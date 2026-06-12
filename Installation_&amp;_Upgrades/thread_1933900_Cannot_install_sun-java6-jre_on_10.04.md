---
title: "Cannot install sun-java6-jre on 10.04"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by kgilmore on 2012-03-01
Hi,

Im trying to install alfresco on my ubuntu server however im stuck on the first step, which is install sun-java6-jre.

I've added the repositories in the sources.list

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
those two . . .

I've also done apt-get update but still get this message 
```
ubuntu@ip-10-58-55-131:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

```

Please help! 
Thanks.

---

### Post by sammiev on 2012-03-01
Read [this]("http://sites.google.com/site/easylinuxtipsproject/java") it will likely help you. :)

---

### Post by kgilmore on 2012-03-01
okay followed the guide, seem to go fine.

However did not fix it still cannot install sun-java6-jre

thanks.

---

### Post by kgilmore on 2012-03-01
Okay got it to work, here's how . . .

1. download and install java se from [http://www.oracle.com/technetwork/java/javase/downloads/jre-6u31-download-1501637.html](http://www.oracle.com/technetwork/java/javase/downloads/jre-6u31-download-1501637.html)

2. follow the guide from sammiev's link to install java se.

3. Type in the following commands in terminal

```
gksudo gedit /etc/apt/sources.list
```

add the following lines in

```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```

then. . .

```
sudo aptitude update
sudo aptitude install sun-java6-jre
sudo update-alternatives --config java
```

PS. Make sure to use the right version i.e. 32 / 64 bit.

---

### Post by sammiev on 2012-03-01
Thanks for posting back and marking the thread as solved.

Also, Welcome to the forums. :)

---

### Post by yacho98 on 2012-03-08
follow to this link and its more easy and worked

[http://www.techytalk.info/latest-oracle-sun-java-jdk-and-jre-6-on-ubuntu-operating-systems/]("http://www.techytalk.info/latest-oracle-sun-java-jdk-and-jre-6-on-ubuntu-operating-systems/")

thanks

---

