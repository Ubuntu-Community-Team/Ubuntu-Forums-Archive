---
title: "Two problems with new installation"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by JoshBissey on 2010-07-17
My computer has two physical hard drives.  Up till now, the first hard  drive was for Windows XP and Windows 7, the second was used for file  storage. I just installed Lucid Lynx on the second drive.  The two  problems are as follows.

<s>1. When I boot into Windows 7, the clock  is set ahead by five hours, even as the time zone remains the same. </s>  Terribly sorry.  Found the answer in another thread. Should have searched.

2.  I have kept the Windows 7 boot loader (choice of 7 or XP) on the first hard drive, and put Ubuntu and grub  on the second hard drive.  That way, if I want to load Ubuntu, I press  F9 for the hp boot menu and select the second hard drive. From there, I would like  this to boot straight into Ubuntu.  How do I keep the grub boot menu  from appearing?  Should I just edit grub.cfg, so it has a timeout value  of 0?  

The hardware is an hp dx2300.

Thanks,

Josh

---

### Post by quixote on 2010-07-19
Hey, share your time zone solution, or link to the other thread.  I've had the same problem, and I'm curious. :D

The way to deal with grub is to edit the /etc/default/grub:```
gksudo gedit /etc/default/grub
```Find the lines that look like this:```
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```
Remove the # from the first line.  I believe it then takes precedence.  If not, comment out the last line (i.e. put a # in front of it).

Save.  Then in a terminal run ```
sudo update-grub
```

---

### Post by celldweller1591 on 2010-07-19
> Hey, share your time zone solution, or link to the other thread.  I've had the same problem, and I'm curious.

Here, Try this one :- 
1) open the teminal
2) Type** : gksu gedit /etc/default/rcS**
   3) Search for UTC and set UTC=yes or UTC=no (or accordingly how you wish)
4) Reboot !

[source ]("http://www.linoob.com/2009/06/whats-the-time/")

---

### Post by JoshBissey on 2010-07-19
> **celldweller1591 said:**
> Here, Try this one :- 
1) open the teminal
2) Type** : gksu gedit /etc/default/rcS**
   3) Search for UTC and set UTC=yes or UTC=no (or accordingly how you wish)
4) Reboot !

[source ]("http://www.linoob.com/2009/06/whats-the-time/")

That was it.  Thanks for the help.

---

### Post by quixote on 2010-07-22
Thanks for the tz solution!

---

### Post by JoshBissey on 2010-07-24
I changed the timeout to 0.  Thanks.

---

