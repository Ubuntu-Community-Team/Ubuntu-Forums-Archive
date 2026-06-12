---
title: "Warning possible to destroy other OS installation"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Ditchy on 2009-11-26
Hello there,
                 Dont know if anyone has come across this yet but I thought I would take the time to warn people.  If you have two identical drives, Ubuntu seems to *assume* you have a striped RAID array when installing.  I had this problem in Mandriva 2009 (its fixed in 2010) and ended up destroying my windows installation so for a newbie its confusing and dangerous. I obviously do not have a striped RAID array and do not have RAID enabled in the BIOS (or anywhere), its two separate drives, one for windows and one for linux.  The solution in Mandriva 2009 was to set the option 'nodmraid' in the kernel options, trying this in ubuntu (9.10) results in the installer showing just a blank page when it gets to the partitioning section, its then impossible to install!  If I had gone ahead and installed as the ubuntu installer suggested I would have been unable to get back into windows.  Someone completely new would have no chance with all this, needs looking at methinks, its put me right off trying ubuntu as well :(.

---

### Post by coffeecat on 2009-11-26
Have you filed a bug report on [Launchpad?](https://bugs.launchpad.net/ubuntu/)

---

### Post by Ditchy on 2009-11-26
Nope, never heard of it, followed your link, registered, could not find any way of actually reporting a bug.  The link leads to a web site focusing on how to file a bug through ubuntu, I dont have ubuntu so thats no use.  It says use launchpad, I hit that link, on the new page theres one link that says report a bug.... it leads to the first web page which was no use :).  I tried, I give up, Im not THAT interested since I aint gonna install it now anyway.

---

### Post by coffeecat on 2009-11-27
You're quite right. Trying to report a bug takes you in a never-ending circle. Must be a bug. I hope someone reports it. :rolleyes:

---

