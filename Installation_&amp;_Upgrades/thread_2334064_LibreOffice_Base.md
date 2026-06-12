---
title: "LibreOffice Base"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by kabuckin on 2016-08-16
I upgraded to 16.04 LTS from 14.04 LTS. The upgrade includes LibreOffice 5.1.4.2. I attempted to open tables of an existing database and receive error:

    The connection to the data source "invest" could not be established.
    Error code: 1000

    The driver class 'org.hsqldb.jdbcDriver' could not be loaded.The additional driver class path is 'file:///usr/share/java/hsqldb1.8.0.jar
    vnd.sun.star.expand:$LO_JAVA_DIR/sdbc_hsqldb.jar'.
    Error code: -1

    org.hsqldb.jdbcDriver

I tried to create a database and it creates successfully, but get same error when attempting to open the database.
I searched for this situation, but I don't find any posts that are relating to these latest release levels.
Can anyone please help with this?

---

### Post by howefield on 2016-08-16
Not sure if it will help but this thread looks similar, might give you a pointer.

[http://en.libreofficeforum.org/node/6526](http://en.libreofficeforum.org/node/6526)

---

### Post by kabuckin on 2016-08-16
Thanks for the reply. I found that post. The  libhsqldb-java in the solution is not the currently installed, libhsqldb1.8.0-java

---

