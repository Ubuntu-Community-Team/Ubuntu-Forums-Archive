---
title: "how to backup quickly entire ubuntu system"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by srobert on 2007-02-13
hi, every one,

here is newbie question.

after all is done (install, ..), 
do there have any way backup entire ubuntu system?
 
quickly and easy-to-use.

Thanks.

---

### Post by kebes on 2007-02-13
There are many options... depends on your setup and what tools you like best.

One thing you can do is boot into a LiveCD and use a program called "[partimage]("http://www.partimage.org/Main_Page")". This program can create an image of a partition, so that you can later restore your partition back to its previous state. This is great for backing up the OS, since you can restore it and everything will be back to the way it was before (including installed applications, etc.). Of course you need somewhere to store the compressed disk image, so typically you need a spare backup partition on your hard drive. (Although partimage can also do network backups, etc.)

There is a special Linux boot CD called "[System Rescue CD]("http://www.sysresccd.org/Main_Page")" that includes a bunch of default tools, including partimage. (It is a text-only environment, however, so you have to be comfortable with the commandline.)

---

### Post by palmerthegeek on 2007-02-13
srobert,

Good question.  I'm also interested in hearing what solutions existed for backup.

AND... if they are easy.....

:popcorn:

---

### Post by IgnorantGuru on 2007-02-13
In case you missed it I just made a HOWTO Backup a Partition using SystemRescueCD...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

That is actually a very easy method.  It looks longer than it is because I gave various options and examples.  Whittle it down to just what you want and there's not much to it.

Partimage is easy to use and intuitive - you just need to use the keyboard in lieu of the mouse (use Tab and arrow keys to move, spacebar to select, and follow on-screen instructions, such as F5 to proceed).

Let me know how it goes.

---

