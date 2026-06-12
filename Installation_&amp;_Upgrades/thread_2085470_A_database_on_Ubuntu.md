---
title: "A database on Ubuntu"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by georingo on 2012-11-18
I have Ubuntu on my notebook at home, and I can make queries in SQL (DB2 9), but that's where my computer-knowledge stops...

Now I want to write queries in a program like "SQuirreL" and have my own database to use them on. That way, I won't need to learn to use "OpenOffice Base" which (in my opinion) is way to difficult, graphical and slow. 

Is there a simple way to "make" your own database on a notebook and is there a program like "SQuirreL" that I can use in Ubuntu, to make the queries. Any help is usefull!

---

### Post by darkod on 2012-11-18
I don't know about squirrel but people usually use MySQL and PostgreSQL on ubuntu.

Both of them are easy to install but I don't know if they are squirrel compatible if that's what you want to use for queries. I would say any sql database should be compatible.

Here is the official documentation to get you started, and I'm sure there are plenty of tutorials online too:
[https://help.ubuntu.com/12.04/serverguide/databases.html](https://help.ubuntu.com/12.04/serverguide/databases.html)

Note: The link is for the Ubuntu Server version but you can install mysql or postgresql on the Desktop version too. It's just that the documentation is inside the server docs.

---

### Post by coldraven on 2012-11-18
According to their web-site SQuirrel **does** run on Linux.
There also are two SQL clients in the Ubuntu software centre, one is GUI and the other CLI.

---

### Post by georingo on 2012-11-18
Using SQuirreL on Ubuntu or finding a program like it, will not be the problem I think. But making a database where I can "copy/paste" my data in, will be. If I look at the documentation about MySQL, I drop out at "configuration"...

Is there a program where you can import data (from a .csv file) into tables and make SQL queries?

---

### Post by steeldriver on 2012-11-18
> **georingo said:**
> Is there a program where you can import data (from a .csv file) into tables and make SQL queries?

To suck in the data, there's mysqlimport

[http://dev.mysql.com/doc/refman/5.0/en/mysqlimport.html](http://dev.mysql.com/doc/refman/5.0/en/mysqlimport.html)

You will need to create the tables first (either using the mysql command line client or the GUI client of your choice - fwiw I have used squirrel on Xubuntu in the past, I found it a bit confusing to set up the java driver bits but that may have been because I was using it with MS SQL Server rather than mysql)

---

### Post by georingo on 2012-11-18
Thank you for the advice. I'll first try "Sqliteman" (SQLite databases made easy). Maybe this is just what I need (simple table making and querying?).

---

### Post by oldfred on 2012-11-18
I am using sqlite as my database. It is just one file and in the repository. But I use python to do a lot of things, but to develop & test my sql queries I use sqliteman and sqlite data base browser. Both are in the repository.

With sqliteman you have to create a database and a table, then you can import files.

With python I can create scripts that read a csv table with headers, create table and add data automatically.

SQLite is a C library that implements an SQL database engine.
Programs that link with the SQLite library can have SQL database
access without running a separate RDBMS process.

sqliteman
Contains the most complete feature set of all SQLite GUI available. Tune
SQL statements, manage tables, views or triggers, administrate the database
space and index statistics with SQLiteman.

SQLite Database Browser is a visual tool used to create, design and edit
database files compatible with SQLite.

---

