---
title: "Problem after PostgreSQL 7.4 installation"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by loonger on 2006-10-11
Hallo! I have some problem:  I have kubuntu 6.06.1 LTS and after install (without any errors) and after login form console to Postgres: 

Code: 
[COLOR="Red"]*su postgres* [/COLOR]

and after trying to create new database (command): 

Code: 
[COLOR="Red"]*psql template1 *[/COLOR]

give back some error: 

Code: 
[COLOR="Red"][I]psql: could not connect to server: There is no any file or folder 
        Is the server running locally and accepting 
        connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"? [/I][/COLOR]

Folder from error is empty. In my opinion PostgreSQL server works correct, I think it's only in some other place. How can I find him? Please give me a corrent solution because  I need PostgreSQL to my project.

---

