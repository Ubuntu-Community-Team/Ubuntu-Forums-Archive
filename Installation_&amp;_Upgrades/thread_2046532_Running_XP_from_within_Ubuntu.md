---
title: "Running XP from within Ubuntu"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by Prboz on 2012-08-23
Hi Newbie here.

I have both Windows XP and Ubuntu 12.01 up and running as a dual boot system on 2 seperate HDD's.  Is it possible to make the xp run inside of the Linux OS?

:popcorn:Prboz

---

### Post by bohemian9485 on 2012-08-23
You can use VirtualBox/VMWare to run a different OS inside your Linux system.

---

### Post by coldraven on 2012-08-23
If you want USB support you need to download VirtualBox from their website

You can migrate an existing XP installation but I have not tried this method.
[https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows)
I think that this method can cause problems.

I deleted my XP partition and did a fresh install directly into a virtual machine.
This works easily if you have a XP disc with the activation code on it but is trickier if you have an OEM version like I have.
The VirtualBox forum has instructions for that or search some of my old posts.

---

### Post by Mark Phelps on 2012-08-23
What you may not know, is that if you have an existing installation of XP on a PC, you can NOT install VirtualBox in Ubuntu and then run that same instance of XP in VB.  You have to migrate it first -- and as you can see from the linked info, that is a LOT of work.

---

### Post by Bucky Ball on 2012-08-23
Forget the migrating. Never heard of a successful one and as far as I know rarely tried because of that.

Point to remember: When using Virtualbox your RAM is split between Host and Guest; e.g. if you have 4Gb of RAM you need to allocate some to Ubuntu (host) and some to XP (guest). That can be 2Gb each or 3Gb for host and 1Gb for guest. Whatever. But it is a limitation.

In other words, if you have 1Gb of RAM all up that is giving you 512Mb per install. That could get sluggish. ;)

---

### Post by Prboz on 2012-08-24
Thanks Guys,

Just thought I would ask the question.

Regards

Prboz

---

