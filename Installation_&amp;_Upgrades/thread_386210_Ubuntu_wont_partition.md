---
title: "Ubuntu wont partition??"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-03-16
Ok well after trying many distros on my intel DP965LT mobo with core 2 Duo only 2 would boot...  Those two where OPENsuse and ubuntu feisty fawn herd 5.  But both always fail when they try to partition my hard drive i have windows installed and everything.  but they wont seem to get past it ubuntu says that it just fails to create the partition and i have to close the installer.  When i reboot i haver to manually expand my windows partition again too.  Is there anything that im doing wrong at all or anything that i can do to finally get my ubuntu installation onto myt new computer?

---

### Post by bulldog on 2007-03-16
Download the GParted live cd [30MB] and burn it to a cd-r.
Defrag your windows partition several times before you boot from the GParted live cd.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Resize your windows partition and create a 10GB [or more] of free space.
The best way is to create a 10GB  /  (root) partition
A 1GB swap and a /home as big as your remaining free space.
Format them all and exit the GParted live cd and boot the ubuntu cd.

When you come to the partition part just choose manual partition and mount the partitions you've already created.
Set them all to format again and take a good look if your windows isn't set to format too,because this would destroy your windows.

Go ahead with the install and it should be fine.

---

### Post by Opeth115 on 2007-03-16
I've tried the gparted live cd but it can't boot... It does teh same thing as dapper and edgy in not finding a bootable medium ide. my cd-rom drive...

---

### Post by bulldog on 2007-03-16
Well take a good look at your hardware then,there should be something that malfunctions.

---

### Post by Opeth115 on 2007-03-16
I've been trying to install ubuntu for so long now and it's so frustrating i have the 965 chipset which isn't supported in many distros i've found out due to the kernel.  But feisty boots up it jsut can't partition i have tried using partition magic on windows to do it also but it spits m,e out an error too ill post here in a sec

---

### Post by Opeth115 on 2007-03-16
Ok well here's the message:

Error 1529 while executing batch

Error 1529:  Information mismatch in directory entry

---

### Post by Opeth115 on 2007-03-17
any help you can give me anyone on what might be going wrong with this?

---

