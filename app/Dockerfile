FROM maven:3.6.3-openjdk-11 AS build
WORKDIR /tmp
COPY ./src ./src
COPY ./pom.xml .
RUN mvn clean install
RUN mvn package
FROM openjdk:11-jdk
COPY --from=build /tmp/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
