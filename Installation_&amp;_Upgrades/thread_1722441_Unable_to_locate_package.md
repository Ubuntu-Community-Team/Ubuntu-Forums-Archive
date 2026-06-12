---
title: "Unable to locate package"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by kerbyjonsonjr on 2011-04-05
[LEFT]I am trying to install aircrack but when I try to a get an error message that says unable to locate package. The exact messages are:
ubuntu@ubuntu:~$ airmon-ng
The program 'airmon-ng' is currently not installed.  You can install it by typing:
sudo apt-get install aircrack-ng
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install aircrack-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aircrack-ng

I am pretty new to ubuntu so I am not really sure what I am doing. I don't know if I have to enable "universe" or what I should do. I am not sure if it matters but I am also running Ubuntu from my flash drive so maybe that is the problem. Any help would be greatly appreciated. Thanks!
[/LEFT]

---

### Post by zvacet on 2011-04-05
Applications>ubuntu software center>edit>software repositories> check all under ubuntu software ( you can skip source and CD rom) and check first two under updates tab.Reload and try to install again.

---

### Post by kerbyjonsonjr on 2011-04-06
> **zvacet said:**
> Applications>ubuntu software center>edit>software repositories> check all under ubuntu software ( you can skip source and CD rom) and check first two under updates tab.Reload and try to install again.

THANKS! That did the trick. Thanks a lot!!

---

### Post by TinkerAlf on 2012-04-15
I am also new to Ubuntu, unfortunately too new, I don't understand what is ment by the reply to the problem... Could you clearify it? Thanks... TinkerAlf

---

### Post by Elfy on 2012-04-15
Hi rather than bump and old thread try creating a new one.

Link to start a new thread - 
[http://ubuntuforums.org/newthread.php?do=newthread&f=326](http://ubuntuforums.org/newthread.php?do=newthread&f=326)

Read the help people help you link in my sig.

Closed.

---

