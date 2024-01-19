# Build spring boot application
FROM gradle:8.5.0-jdk17-alpine AS build
WORKDIR /home/app
COPY . /home/app
RUN ./gradlew bootJar

# Build docker image
FROM openjdk:17-jdk-slim
COPY --from=build /home/app/build/libs/*.jar /usr/local/lib/app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/app.jar"]