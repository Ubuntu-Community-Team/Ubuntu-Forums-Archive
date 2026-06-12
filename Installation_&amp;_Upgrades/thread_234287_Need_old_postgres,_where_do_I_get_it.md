---
title: "Need old postgres, where do I get it?"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by schurtek on 2006-08-11
I need to install 7.4.7 in order to run ]project-open[. The server is basically being dedicated to run ]project-open[ and nothing else. I have tried with apt-get, and I can only get 8.1... 

Any advice?

---

### Post by apaton on 2006-08-25
I also want to install Postgres 7.4, did you solve the problem?

Andy

---

### Post by apaton on 2006-08-26
Worked out an answer at to get postgres-7.4 from [https://help.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html]("https://help.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html")

To enable the Universe and Multiverse repositories, edit the  /etc/apt/sources.list file and uncomment the appropriate lines:

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntudapper](http://archive.ubuntu.com/ubuntudapper) universe multiverse
```

```
apaton@lamp:/home/apaton# sudo apt-cache search postgresql-7
postgresql-7.4 - object-relational SQL database, version 7.4 server
postgresql-client-7.4 - front-end programs for PostgreSQL 7.4
```

apaton

---

