---
title: "Install on an old machine"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by sdb2028 on 2006-03-01
How old of a machine can you install ubuntu on?
I try'd to install it on a machine which has a 6 gig HD, 200mhz Pentium, 64mg mem. Gets all the way to through starting the partitioner, then hangs at a blue screen.
Any help would be appreciated.

---

### Post by az on 2006-03-01
[QUOTE=sdb2028]How old of a machine can you install ubuntu on?
I try'd to install it on a machine which has a 6 gig HD, 200mhz Pentium, 64mg mem. Gets all the way to through starting the partitioner, then hangs at a blue screen.
Any help would be appreciated.[/QUOTE]
The installer needs more than 64 megs of ram to work.  You need 128 megs of ram to run ubuntu.

---

### Post by rfruth on 2006-03-01
64 MB RAM won't do it, 128 MB would if ya didn't use a GUI and enjoyed watching paint dry - hey wait only Windows blue screens ... :rolleyes:

---

### Post by funkydan2 on 2006-03-01
You probably can install Ubuntu on that machine, but a full featured desktop environment is going to struggle with only 64 megs of RAM.

Maybe you should start with a server install and then try to install xubuntu-desktop ("sudo apt-get install xubuntu-desktop") once you've got a basic command line and network stuff up and running.

Xubuntu will install XFCE which is a much lighter desktop environment and may even give acceptable performance on your machine.

---

### Post by sdb2028 on 2006-03-01
Thanks, thats all I needed to know.

---

### Post by Ozitraveller on 2006-03-01
There are some links below that you might also find useful.

---

### Post by sdb2028 on 2006-03-01
try'd the server install--- still hngs at prtition

---

### Post by odysseus.lost on 2006-06-15
OK, since this thread seems applicable to my problem let me reopen it, but this time I am referrinhg to 6.06 version. I am trying to install XUbuntu 6.06 on a pentium 266 mmx with 128 MB RAM. I am getting the same problem described... a blue screen just after trying to start the partitioner... According to the requirements this xubuntu alternative should be able to install in machines with RAM less or equal to 128MB...

Anyone any clues??

---

### Post by Ozitraveller on 2006-06-25
Are you doing a desktop or an alternate install? I think the desktop will require more memory to do.

I read yesterday that fluxbox is being considered as the second lightweight desktop, Xfce would be the default, and fluxbox would be an alternative. Fluxbox is even more lightweight than Xfce There are a number of distros that use Fluxbox DSL (Damn Small Linux) [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) around 50mb all up, VectorLinux [http://www.vectorlinux.com/](http://www.vectorlinux.com/). Puppy Linux uses Xfce [http://www.puppylinux.org/](http://www.puppylinux.org/)

I hope this helps...

---

### Post by Lonney on 2006-06-25
I'm having the same problem on a Compaq EVO D51S SFF (Celeron 1.7, 512mb, 20gb IDE) with Ubuntu Server 6.06.

>> update: I have solved my issue with this, resetting the CMOS seems to have cleared the problem.

---

