FROM maven as build
WORKDIR /app
COPY . .
RUN mvn install
# till above we got jar file, now java is needed to run this jar
FROM openjdk:11.0.10-jre
WORKDIR /app
# here we give stage which is input
# target will be /app/target/appname as we see in eclipse project structure
# to find the appname, we chek pom.xml=> artifactId+version tag .jar
COPY --from=build /app/target/zuul-0.0.1-SNAPSHOT.jar /app
EXPOSE 9999
CMD ["java","jar","zuul-0.0.1-SNAPSHOT.jar"]