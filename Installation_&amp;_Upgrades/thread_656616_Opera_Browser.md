---
title: "Opera Browser"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by ShawnEckhart on 2008-01-02
I have downloaded this file to my desktop. (opera_9.25-20071214.6-shared-qt_en_i386.deb)
But when I try to install it I get this message.  "Error: Dependency is not satisfiable: libqt3-mt".  What does it mean and how can I fix it.

If you respond, and I hope someone will, please keep it simple for this noob. Thanks.

---

### Post by jrusso2 on 2008-01-02
Download the static deb of opera

---

### Post by Partyboi2 on 2008-01-02
>   "Error: Dependency is not satisfiable: libqt3-mt".  What does it mean and how can I fix it.
when you try and install a deb package, and get the error you got it normally means that you need to install the package needed to meet the dependency. In your case you would need to install libqt3-mt

---

### Post by ~LoKe on 2008-01-02
```
sudo apt-get install libqt3-mt
```
In the terminal.

---

### Post by ShawnEckhart on 2008-01-03
This is what I get when I copy and paste the code.


shawn@shawn-laptop:~$ sudo apt-get install libqt3-mt
[sudo] password for shawn:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt3-mt
shawn@shawn-laptop:~$

---

### Post by dannyboy79 on 2008-01-03
if you issue

sudo aptitude search libqt3

you'll see that there are all these with that name:

p   libqt3-compat-headers                                    - Qt 1.x and 2.x compatibility includes
id  libqt3-headers                                           - Qt3 header files
p   libqt3-i18n                                              - i18n files for Qt3 library
p   libqt3-java                                              - Java bindings for Qt
p   libqt3-jni                                               - Java bindings for Qt ( Native libraries )
id  libqt3-mt                                                - Qt GUI Library (Threaded runtime version), Version 3
id  libqt3-mt-dev                                            - Qt development files (Threaded)
id  libqt3-mt-mysql                                          - MySQL database driver for Qt3 (Threaded)
p   libqt3-mt-odbc                                           - ODBC database driver for Qt3 (Threaded)
p   libqt3-mt-psql                                           - PostgreSQL database driver for Qt3 (Threaded)
p   libqt3-mt-sqlite                                         - SQLite database driver for Qt3 (Threaded)

It's there, you just need to enable some repo's. Do you have multiverse and universe repo's enabled. Here's how to do that: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by FosterMX on 2008-03-31
I got the same message "Error: Dependency is not satisfiable: libqt3-mt" but i was trying to install virtualbox.The way i fixed it was.
System>Software Sorces and then i check marked all the boxes under "Ubuntu Software" tab
I went back to the package and clicked on it and it install just fine! =D

---

