---
title: "Can't get ubuntu to install on my laptop"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by newbie123errrr5 on 2012-11-22
I can't find the answer anywhere but apologies if it is somewhere in this forum!

I downloaded the following: 

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

I clicked everything has it said to do and when it asked to reboot I did so. The two options - ubuntu and windows boot where both there. I hit ubuntu and get the following:

BusyBox v1.18.5 (Ubuntu 1:1.18.5-lubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.


.... and a black screen.
eventually i tried 
exit

To get:
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell!


That's the error I got the first time I downloaded last week which i completely uninstalled and tried again. My laptop has the requirements to run it so I have no idea what the problem is...

---

### Post by darkod on 2012-11-22
I can't help with this error with wubi, but I would recommend you consider a proper installation on its own partition.
That's the way it's supposed to work, and also it makes troubleshooting much easier.

Wubi is like virtual machine inside windows, and not really how you should use an OS. Just for a quick try. But you can do the same running from the ubuntu cd in live mode, if you only want a quick try.

---

