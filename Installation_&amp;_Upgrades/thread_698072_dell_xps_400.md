---
title: "dell xps 400"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by jamfix on 2008-02-15
i have only really used live disks b4 is there anything that can help me out on installing to a dell xps 400?

---

### Post by Partyboi2 on 2008-02-15
Hi
Can you give some more info about what you are wanting or what the problem is. eg. error messages, details of what is happening. etc :)

---

### Post by stevescripts on 2008-02-15
> **jamfix said:**
> i have only really used live disks b4 is there anything that can help me out on installing to a dell xps 400?

Start here, maybe?

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

Hope this helps.

Steve

---

### Post by jamfix on 2008-02-19
i was looking for any info on installing on xps 400 is there anything diffrent then a basic install?
how do i find/installing drivers for my system?
right now havent done anything with the system im using a live disk some how the windows xp files have been cruped im trying to save what files i can but i dont have anything i can back up to

---

### Post by Partyboi2 on 2008-02-19
[This]("https://help.ubuntu.com/community/GraphicalInstall") explains how to install ubuntu with the live cd. If you are wanting to do more  like encrypting your partitions you can use the [alternate]("http://releases.ubuntu.com/releases/7.10/") cd.
If you do not have anywhere to back up your files to from windows you could do a dual boot setup to start with. Ubuntu can reaed/write to ntfs which allows you to access all your files on windows. You could copy them over to ubuntu once its installed and then delete windows and resize ubuntu into the space windows was using or reinstall windows again so that you have dual boot setup.

---

### Post by jamfix on 2008-02-21
well i have installed but it seams i have installed to the whole drive 
i can across this software thats spose to suport data recovery 

[http://www.zmanda.com/](http://www.zmanda.com/)

is it worth the try? how would i go about installing it?

---

### Post by Partyboi2 on 2008-02-21
can you open a terminal (Applications>Accessories>Terminal)
and post the output to
```
fdisk -l
```
that is with a small L

---

### Post by jamfix on 2008-02-21
say what?

im lost

---

### Post by Partyboi2 on 2008-02-21
Are you sure you have deleted windows? You can check by booting into ubuntu and when you get to the desktop click on "Applications" then "Accessories" then select "Terminal" then when the terminal opens type```
 fdisk -l
``` this will show you a list of your current partitions.

---

### Post by jamfix on 2008-02-22
this is what i get but it doesnt mean anything to me

james@james-desktop:~$ fdisk -l

Disk /dev/sdb: 1026 MB, 1026555904 bytes
16 heads, 32 sectors/track, 3916 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3916     1002480    6  FAT16
james@james-desktop:~$

---

