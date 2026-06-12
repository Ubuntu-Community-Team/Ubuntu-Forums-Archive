---
title: "problem with ubuntu software center"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by vinxtreme on 2010-12-18
Hi all ,

I've just installed ubuntu 10.4 LTS  . I use a proxy server with authentication so had a problem with update center it used to say 407 authentication required ... so searched threads and changed the apt.conf file in /etc/apt  with the following ..
Acquire::http:proxy "http://MYUSERNAMEpASSWD@pROXYSERVERpORT/";

after that 
$ sudo apt-get clean 

then tried sudo apt-get update , but it throws the following .....
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory


Plz help ....(also tried sudo kill all apt etc      but it persists.    ...)      

thanks in advance ..

---

### Post by Rubi1200 on 2010-12-18
Hi and welcome to the forums :)

An error like that often indicates that you have more than one package manager open.

In other words, you cannot run apt-get and Synaptic or Synaptic and the Software Center at the same time.

Close all instances of package management and then try again (logging out and back in again might also help).

---

