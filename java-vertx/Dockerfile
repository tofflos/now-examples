FROM maven:3-jdk-8-alpine as build
COPY src /usr/src/vertx/src
COPY pom.xml /usr/src/vertx
RUN mvn --batch-mode --file /usr/src/vertx/pom.xml clean package


FROM openjdk:8-jre-alpine
COPY --from=build /usr/src/vertx/target/lib /opt/vertx/lib
COPY --from=build /usr/src/vertx/target/*.jar /opt/vertx
EXPOSE 8080/tcp
ENTRYPOINT ["java", "-jar", "/opt/vertx/java-vertx-1.0-SNAPSHOT.jar"]
