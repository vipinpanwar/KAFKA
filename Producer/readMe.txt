KAFKA TOPICS COMMAND************* 1.) create topic : (replication-factor can not be greater than the brokers(aka connected servers.) kafka-topics --bootstrap-server localhost:9092 --topic first_topic --create --partitions 3 --replication-factor 1 2.) Describe topics kafka-topics --bootstrap-server localhost:9092 --topic first_topic --describe. 3.)Delete Topics kafka-topics --bootstrap-server localhost:9092 --topic first_topic --delete. 4.) List topics kafka-topics --bootstrap-server localhost:9092 --list

Kafka Producer 1.) kafka-console-producer --broker-list localhost:9092 --topic first_topic Kafka Consumer 1.) kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic library-events

**********Sending Message without key

Kafka Producer ---[Send to test-topic] --- Partitioner ---

let say we have four patition. Now Before sending the message to consumer, message goes to different layer of producer one of which is "Partitioner".

1.) "Partitioner" check if there is no key then it randomly assign the value by round robin approach to all partition. 2.) Now there is no gurantee consumer will read the message in order because order is guranted only with in a partition.

**********Sending Message with key

Kafka Producer ---[Send to test-topic] --- Partitioner --- 1.) "Partitioner" check if there is a key then it perform some hashing on that key and resolve it to one of the partition(leyt say partition 0), now if we get the same key again it will resolve to partition 0 only in this way we can guratee the ordering.

Coinsumer Groups*** https://www.udemy.com/course/apache-kafka-for-developers-using-springboot/learn/lecture/17343856#questions consumer groups are fundamentally the basis for a scalable message consumption. how to generate the groupID : when you use a console consumer, the group I.D. is automatically generated for you behind the scenes.

Commmit and retention Log 1.) When producer produce any thing that gets logged in the Hdd. log dir : /tmp/kafka-logs 2.) Retention policy : Determined how longs meesage should retained

Configured in server.properties (log.retention.hours) Default is 168hours 7 days.

Distributed Streaming Platform 1.)Apache kafka is a Distributed Streaming Platform. 2.) For better understanding go through the pdf.

Kafka Clusters****** 1.) Set of Kafka Brokers. 2.) At a time how many brokers works? 3.) For each broker we need seprate server.properties file, and we need to change atleast 3 properties mentioned below a.) Broker id b.) Port c.) Logs path 4.) we have multiple broker but only one zookeepar do this create a single point of failure for zookeepar, what happends if zookeepar failed?

*********Data LOss IN Kafka(imp)