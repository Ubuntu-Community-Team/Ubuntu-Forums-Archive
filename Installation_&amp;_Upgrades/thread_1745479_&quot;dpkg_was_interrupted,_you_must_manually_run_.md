---
title: "&quot;dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct&quot;"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by barnskybeat on 2011-05-01
Dear all,

Just upgraded tu Ubuntu 11, spent hours to fix my broken grub and compiz/metacity settings.....a bit frustrated to say the least.

Now I am getting the following error message in synaptic. When I run the code in terminal it gets stuck. Please help!


Synaptic message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

In terminal (gets stuck here):
dirk@dirk-laptop:~$ sudo dpkg --configure -a
[sudo] password for dirk: 
Setting up xulrunner-1.9.1 (1.9.1.18~hg20110309r27352+nobinonly-0ubuntu1~umd1) ...


how can I fix this???? :confused:

I am getting another error:
dirk@dirk-laptop:~$ sudo apt-get install -f
[sudo] password for dirk: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dirk@dirk-laptop:~$

---

### Post by Dutch70 on 2011-05-01
Well the 2nd one is usually caused by having more than one synaptic open. Such as software center or synaptic package manager.

The first one though, I'm not sure. I did find that one person has a similar bug report.
[[COLOR="RoyalBlue"]https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.1/+bug/774027[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.1/+bug/774027")

---

### Post by barnskybeat on 2011-05-01
no others processes synaptic processes open, cross checked a few times.
So what to do?
The bug report is exactly what I am facing..

---

### Post by barnskybeat on 2011-05-02
anyone available to help me with this???
cannot run synaptic any more and always get stuck with above message in terminal after running sudo dpkg --configure -a

---

### Post by Jerodkdunn on 2012-04-23
I am getting this issue as well and I do not have anything else running.

---

### Post by oldos2er on 2012-04-23
Old thread closed.

Jerodkdunn, please start a new thread.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

