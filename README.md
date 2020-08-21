# Kafka Twitter Producer

Read from twitter stream and write to kafka

## Prerequisites
* Twitter API Keys
* Kafka and zookeeper installation

### Producer Configuration

#### Configure Kafka Broker -

* Open Kafka Configuration file -
```
 vi src/main/java/app/config/KafkaConfiguration.java
```
* Give details of kafka servers and kafka topic name you want to produce into

#### Configure twitter client -

* Open Twitter Configuration file -
```
  vi  src/main/java/app/config/TwitterConfiguration.java
```
* Add the twitter's secrets and tokens to respective places

* The 'HASHTAG' with '#' symbol is used to index keywords or topics on Twitter. You can change the 'HASHTAG' value to some other keyword so that it will produce tweets with the new keyword

After the setup, create a JAR file - 
```
  mvn clean package
```
Now start zookeeper, kafka and create a topic with the name mentioned in code

### Execution

Let’s see the code in action !

Run the JAR. It should start sending data to Kafka -
````
 java -jar target/<JAR file name>
````

Run you kafka consumer to consume the messages


# Kafka Consumer Application
Read data from Kafka and store it in to MongoDB

## Prerequisites
* Kafka and zookeeper installation
* MongoDB setup

### Configuration
* Open config file -
```
  vi src/main/resources/application.conf
```
* Provide Kafka and MongoDB details

### Execution
After the setup, create a JAR file - 
```
  mvn clean package
```
* Now start zookeeper, kafka and create a topic with the name mentioned in application.conf file

Run the JAR to have kafka consumer up and running. We are ready to consume data
````
 java -jar target/kafka-mongo-application-1.0-SNAPSHOT-jar-with-dependencies.jar
````

* Run the producer and produce messages

### Verify
* Login to mongodb and check if we have the data present 

Login - 
```
  mongo -u <username> -p --authenticationDatabase <db_name>
```
It will prompt for password. Enter the password

Lists all the database - 
```
  show dbs
```

Select the database - 
```
  use <dbname>
```

See collections - 
```
  show collections
```
See the stored data - 
```
  db.<collectionname>.find()
```

Check if the new data is getting inserted - 
```
  db.<collectionname>.count()
```
The count will increase with each new data being inserted to mongodb
