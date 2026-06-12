---
title: "Ubuntu 7.10 64 bit reboots 4 times before starting up"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by jlfqam on 2008-09-27
Hi, I've just started with linux.
I have installed Ubuntu 7.10 64bit on a gigabyte MB with 4GB RAM, 250MB sata disk and Gforce card. The disk is partinioned with 200MB for XP64 and 50GB for Ubuntu.
After the setup was finished the system rebooted at least 4 times automatically until the login window appeared. The system works well but I would preferr it start up normally.
A message appears at the bottom
kernel alive
kernel direct mapping tables up to ....
Any clues?
I intend to run seadas on this system so I have installed the newest Ubuntu version 7.10 recommended in the website. Matlab  2007b has been installed and up to now runs very fast without problems.
I've browsed the web searching for solutions to this "problem" and tried a few of them without success.
Thanks in advance
jlf

---

### Post by Sef on 2008-09-27
> I intend to run seadas on this system so I have installed the newest Ubuntu version 7.10 recommended in the website. Matlab 2007b has been installed and up to now runs very fast without problems.

It does not say recommded, just that it has been tested on Gutys with the 2.6.22 kernel; however, in 7 months updates will stop being sent out.   If I were you, I would install Hardy Heron on another partition and see if it works with that.  Heron is an LTS (Long Term Support), which means that the desktop will be supported for 3 years instead of the normal 18 months.

---

### Post by jlfqam on 2008-09-27
Hi Sef,
thanks very much for your advice. 
I will try to upgrade from 7.10 to 8.04.1. I have just started setting it up and there's not much on that partition.
Greetings
jlf

---

### Post by jlfqam on 2008-09-29
Hi Sef,
the >200 pending upgrades within the same version  7.10 did not but 
the upgrade to 8.04 LTS solved the rebooting loop problems
I have not installed the seadas yet.
Thanks for your support
jlfqam

---

