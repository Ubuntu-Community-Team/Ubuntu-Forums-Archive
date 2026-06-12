---
title: "can I chose where APT-GET INSTALL installs software"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by mwall on 2007-11-19
Can I choose what directory I want to install a program when using "apt-get install" command?
What would the command line look like.

much thanks

---

### Post by monktbd on 2007-11-19
why would you want that?

the advantage is that you do not need to care as long as you have sufficient diskspace on the partition holding your programs (usually the partition where /usr is on).
if you do not have enough space then you can always mount another partition as /usr.

---

### Post by mwall on 2007-11-20
I bought a book to learn PHP, MYSQL and APACHE. It refers to MYSQL being installed in /usr/local/mysql-ver.platform and seting a symbolic link to it as mysql. Also on the mysql.com site it refers to it being installed at /usr/local/mysql.... When I install using ubuntu's synaptic package manager it does not install to the referanced location. So I thought it might be possible to change the install location using "apt-get install" some how. Does anyone know if this is possible? How to do it? I have googled and ask searched to no avail.

Thanks

---

### Post by monktbd on 2007-11-20
i dont know why it is important to have the exact same install folder to properly follow the book, i did not do too many things with mysql but the ones that i did never needed the install place that apt-get chose. all commands are in your path and available in the command shell, the usual place for the databases can be configured in the /etc/mysql folder.

[http://dev.mysql.com/downloads/mysql/5.0.html#ubuntu](http://dev.mysql.com/downloads/mysql/5.0.html#ubuntu) even recommends using apt-get to get mysql.

i dont know whether it is possible to change the folder with apt-get - i think it might be dangerous because files are not spread just in one folder but over several folders within in a linux install.

you could download the source and compile it yourself, there you usually have the option to set the base dir yourself (usually /usr or /usr/local).

---

### Post by mwall on 2007-11-21
Thanks I'll give it a try!

---

### Post by monktbd on 2007-11-21
just one more thing: if you install mysql by compiling it yourself you are hopefully aware that you need to check for security updates yourself and apply patches yourself and recompile it. 
using a deb package with apt-get gets rid of that too because it alerts you of updates.

---

