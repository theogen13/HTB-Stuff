<img width="2054" height="324" alt="Screenshot 2026-07-25 112106" src="https://github.com/user-attachments/assets/bb8249dc-36b1-441a-92e6-16a1cc03fa5c" />

# HTB Starting Point Boxes - Tier 0 - Redeemer (Redis)

Target IP - 10.129.189.111

## **Task 1 - Which TCP Port is open on the machine?**

First, I decided to go with using HTB's Virtual Machine Pwnbox.

<img width="2554" height="1424" alt="Screenshot 2026-07-25 102845" src="https://github.com/user-attachments/assets/fa141977-7074-49c1-a123-a434f34bb189" />

Let's open the terminal and get Task 1 in progress!
Since we are given an IP address, let's go for an **nmap** scan of the open ports. 

```
nmap -sV -p- 10.129.189.111
```
*Note: Had to add the flag -p- because nothing showed up in the initial scan.*

<img width="1628" height="532" alt="Screenshot 2026-07-25 103759" src="https://github.com/user-attachments/assets/75411e32-48f7-44bf-8488-70ba3ef15fd2" />

Task 1 Complete! The port is 6379.

## **Task 2 - Which service is running on the port that is open on the machine?**

From our nmap scan you can see the service is called 'redis'. 

## **Task 3 - What type of database is Redis? Choose from the following options: (i) In-memory Database, (ii) Traditional Database**

Welp, after a quick little Google search- **Redis is an open-source, in-memory NoSQL key-value database.** Safe to say option i is correct.

## **Task 4 - Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments.**

```
redis-cli
```
## **Task 5 - Which flag is used in the Redis command-line utility to specify the hostname?**

```
redis-cli --help
```
This will display a list of flags and at the top is -h for server hostname.

## **Task 6 - Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?**

```
info
```

## **Task 7 - What is the version of the Redis server being used on the target machine?**

<img width="2250" height="1148" alt="Screenshot 2026-07-25 110026" src="https://github.com/user-attachments/assets/a278cc41-ff9b-4fca-94a2-8c2b23bef324" />

Using the 'info' command, scroll up to find the version at the top of the output!

## **Task 8  - Which command is used to select the desired database in Redis?**

```
select
```

## **Task 9 - How many keys are present inside the database with index 0?**

Using the 'info' command under the section **#Keyspace** you can find the number of keys present.

<img width="702" height="164" alt="Screenshot 2026-07-25 110821" src="https://github.com/user-attachments/assets/9cedc445-769a-43ec-a2aa-f4ad15cd1d9f" />

## **Task 10 - Which command is used to obtain all the keys in the database?**

```
keys *
```

## **Submit the FLAG located in the database.**

Using the keys * command we can see the 4 keys in the database. “flag” looks interesting! Let’s use ‘get flag’ to see what the array holds. 

<img width="922" height="362" alt="Screenshot 2026-07-25 111757" src="https://github.com/user-attachments/assets/c3098ee0-13b2-4fd7-97f2-e9d72b528039" />

### BOX COMPLETE!
