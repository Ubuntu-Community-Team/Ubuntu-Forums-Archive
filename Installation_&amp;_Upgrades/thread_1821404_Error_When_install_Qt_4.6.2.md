---
title: "Error When install Qt 4.6.2"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by rstanly on 2011-08-09
I am using ubuntu 10.10.When i try to install Qt 4.6.2 installation procedure for FriendlyARM mini 2440 Linux. Followed all the steps.I found errors in make command. When i run make install i got the error like this "No targets specified and no makefile found.  Stop."
Please advice.

---

### Post by piyush.kumar on 2011-08-09
all I can suggest with this information is to read the README, or try to set it up from the repositories... I did it from the repos

---

### Post by mörgæs on 2011-08-09
Yes, in general everything should be set up from repos, if possible. Finding stuff here and there on the web and installing it is a bad habit from Windows.

---

### Post by allwimb on 2011-08-09
You cannot run make install first there should be a configure script that you need to run first after that you compile it using make and finally you install it using make install. The steps are described in the README file. But I suggest you to get Qt from repos it's easier and faster. Compiling Qt takes a lot of time.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

