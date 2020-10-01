# schatterjee
Welcome to Learning with Astra


Explain your use case
Creating an application for users who are loyalty customers to online grocery app.

Listing below the tables that would represent the same. [Work In Progress]

Requirement:
1. Users table to store user info once they register to the app
2. Purchases table to store user purchases done 

Snapshots:

Users table: 'users_info'

Create Table::

KVUser@cqlsh:killrvideo> CREATE TABLE IF NOT EXISTS users_info (
              ...     userid uuid,
              ...     username text,
              ...     address text,
              ...     contact_number text,
              ...     insert_date timeuuid,
              ...     inserted_by text,
              ...     PRIMARY KEY ((userid), insert_date)
              ... ) WITH CLUSTERING ORDER BY (insert_date DESC);
KVUser@cqlsh:killrvideo>
KVUser@cqlsh:killrvideo>
KVUser@cqlsh:killrvideo> desc tables;

user_info  comments_by_video  comments_by_user  users_info  users_by_city

KVUser@cqlsh:killrvideo> select * from users_info;

 userid | insert_date | address | contact_number | inserted_by | username
--------+-------------+---------+----------------+-------------+----------

(0 rows)

Insert Data::

KVUser@cqlsh:killrvideo> INSERT INTO users_info (userid, username, address, contact_number, insert_date, inserted_by)
              ... VALUES (UUID(), 'John','Mountain View', '655-103-5211',NOW(),'grocery_app');
              
Read from Table::
 
 KVUser@cqlsh:killrvideo> select * from users_info;

 userid                               | insert_date                          | address       | contact_number | inserted_by | username
--------------------------------------+--------------------------------------+---------------+----------------+-------------+----------
 67ae9317-d730-4aa1-b937-59d76bca400e | 6d066670-03fc-11eb-80a6-6b3556455fe8 | Mountain View |   655-103-5211 | grocery_app |     John

(1 rows)
KVUser@cqlsh:killrvideo> select dateOf(insert_date) from users_info;

 system.dateof(insert_date)
---------------------------------
 2020-10-01 15:40:26.071000+0000

(1 rows)



