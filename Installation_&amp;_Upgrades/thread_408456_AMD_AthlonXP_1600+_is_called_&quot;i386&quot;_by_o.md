---
title: "AMD AthlonXP 1600+ is called &quot;i386&quot; by operating system"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by dave71 on 2007-04-13
I am running ubuntu 7.04 on a system using an AMD AthlonXP 1600+ with 1GB mem and 40G hard disk space.  The "Add/Remove Applications" program previous to a few days ago let me add whatever I wished, but now on some applications states: 
 
[INDENT]"[The application] cannot be installed on your computer type (i386).  Either the application requires special hardware features or the vendor decided to not support your computer type."[/INDENT]

Please note that this started to occur while running ubuntu 6.10.  I have since updated to 7.04.
I should also note that, for example, the application XaraXtreme now says it is not supported, but, it is running very nicely.

Does anyone have a clue why ubuntu now thinks that my machine is an i386?  Should I just ignore the warning and try to install anyway?

Any help would be appreciated.

---

### Post by bulldog on 2007-04-13
Wel your machine is probably an i386?
You have to understand there is an i386 version of ubuntu which is called '32bit' as well,and a 64bit version,for the AMD64 bit processors.
You have an AMD1600 which is basically an i386 processor [based on this architecture] and not an 64bit processor.

So,nothing to worry about.
Installing applications which are not base on the i386 architecture,is not a wise thing to do.
The 64 bit version is backwords compatible with some 32 bit applications but not the other way around.

---

### Post by dave71 on 2007-04-14
Thank you.
I guess that I somehow got a 32bit version of Xara.

---

