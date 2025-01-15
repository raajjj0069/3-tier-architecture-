# Base image
FROM openjdk:8-jdk-alpine

# Set environment variables
ENV CATALINA_HOME=/usr/local/tomcat

# Copy and extract Apache Tomcat
COPY apache-tomcat.zip /tmp/
RUN mkdir -p $CATALINA_HOME && \
    unzip /tmp/apache-tomcat.zip -d /usr/local && \
    mv /usr/local/apache-tomcat* $CATALINA_HOME && \
    rm /tmp/apache-tomcat.zip

# Copy student.war and mysql.jar
COPY student.war $CATALINA_HOME/webapps/
COPY mysql.jar $CATALINA_HOME/lib/

# Set permissions and start Tomcat
RUN chmod 777 $CATALINA_HOME/bin/catalina.sh
CMD ["sh", "-c", "$CATALINA_HOME/bin/catalina.sh run"]
