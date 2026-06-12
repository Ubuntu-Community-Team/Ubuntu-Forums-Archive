---
title: "OpenOffice and MySQL and JDBC"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2007-04-14
Hi,

I got some problems with my "specialized" Ubuntu notebook. I try to access a MySQL database through OpenOffice Base. Shouldn't be a problem? Well, there are some pitfalls to it. ;-)

I installed OpenOffice 2.2 from [http://www.openoffice.org](http://www.openoffice.org) into /opt/openoffice2.2

And, I have LAMPP install at /opt/lampp, where there is also my MySQL server located. The MySQL package runs, as I can access all the databases and tables through PHPMyAdmin.

Through Synaptic I have installed libmysql-java, sun-java5-jre, and sun-java6-jre.

When I want to open a MySQL database in OpenOffice 2.2, it tells me that it cannot find the classes for JDBC.

Is it possible to access MySQL in a Lampp installation through OpenOffice / JDBC?

Thanks for your help!

Bye,
Timo

---

### Post by Timokl on 2007-04-14
What I forgot: I already added 

```
CLASSPATH=$CLASSPATH:/usr/share/java/mysql.jar
export CLASSPATH
```

to my .bashrc, logged out and in, and the CLASSPATH is recognized by Ubuntu:

```
timo@aristoteles:~$ echo $CLASSPATH
:/usr/share/java/mysql.jar
```

But still no connectivity from OO to MySQL. :(

---

### Post by davarino on 2007-04-15
Be advised that there is a flaw lurking in an .xml file that loaded with your Java when you did your OO.o upgrade: (I suspect this has been around since at least Java 5)

<http://www.clasohm.com/blog/one-entry?entry%5fid=40367>

Maybe you should fix this first and then let's see what happens.

---

### Post by Timokl on 2007-04-16
Hi,

thanks for the reply. The page you advised me says that the broken xml file is /usr/share/mime/packages/x-java-archive.xml. However, on my machine this file does not exist. As the page you mentioned is written for Fedora, it might be something distro-specific?

Bye,
Timo

---

### Post by davarino on 2007-05-02
> **Timokl said:**
> Hi,

thanks for the reply. The page you advised me says that the broken xml file is /usr/share/mime/packages/x-java-archive.xml. However, on my machine this file does not exist. As the page you mentioned is written for Fedora, it might be something distro-specific?

Possibly. The way that I loaded OO.o 2.2 to Dapper was from the RPM using Alien (because 2.2 is not available in the Dapper repository). If you can't get it to work the way you're doing it, this may be your best option... and then checking to make sure that the file I noted gets fixed.

Good luck!

---

