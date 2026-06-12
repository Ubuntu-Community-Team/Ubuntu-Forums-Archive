---
title: "Need Help with flashing bios on acer s3-391 laptop"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by Traxster on 2013-08-19
Hello to all,

First of all, I found another thread on this topic, unfortunately, I lost track of it, and could not find it again. However, before I did loose the thread, I managed to be able to follow all of the instructions on how to create a Dos disk so I could load my upgrade files from acer to upgrade the bios.The 2 files I downloaded on to my roomates windows machine were HPflash1.zip and Win 98 Boot zip. Basically, Hpflash1 created the start up disk with the win 98 boot zip files. After start up disk was created, I copied the upgrade bios file from acer to usb drive. when I restarted the machine it booted into Dos  mode(shell) leaving a C:/>    (<--something like that).  I typed 'dir' to confirm that my file was there. then entered the name of the file to execute the file but I get a message saying "you cant run this file from dos" ? Am I doing something wrong? is there a command that goes in front of the file name??  By the way, the bios upgrade file ends in exe. 
 

Any help would be greatly appreciated...


Traxster

---

### Post by Mark Phelps on 2013-08-19
What it's telling you is that booting into DOS will not work to run the HP flash utility; instead, you have to boot into Windows.

Sorry, but nearly all the BIOS flash utilities require Windows.

In some cases, the machines provide their own flash utility that is accessed by pressing some key combination.  You should check the documentation on your Acer to see if it has that.

Also, WHY are you flashing your BIOS?  I strongly recommend AGAINST doing this unless the BIOS upgrade is needed to fix a specific problem.

BEFORE you flash the BIOS, you need to confirm that BOTH of the following are true:
1) You have a way to save off the current working BIOS to media
2) You have a way to restore the saved BIOS from that media

If you don't have both, flashing the BIOS risks turning your laptop into an "electric brick".

---

### Post by Traxster on 2013-08-19
> **Mark Phelps said:**
> What it's telling you is that booting into DOS will not work to run the HP flash utility; instead, you have to boot into Windows.

Sorry, but nearly all the BIOS flash utilities require Windows.

In some cases, the machines provide their own flash utility that is accessed by pressing some key combination.  You should check the documentation on your Acer to see if it has that.

Also, WHY are you flashing your BIOS?  I strongly recommend AGAINST doing this unless the BIOS upgrade is needed to fix a specific problem.

BEFORE you flash the BIOS, you need to confirm that BOTH of the following are true:
1) You have a way to save off the current working BIOS to media
2) You have a way to restore the saved BIOS from that media

If you don't have both, flashing the BIOS risks turning your laptop into an "electric brick". 

[[IMG]http://s6.postimg.org/xmqd5lr0t/20130819_125721.jpg[/IMG]]("http://postimg.org/image/xmqd5lr0t/")
this is what the screen looks like and the response i received.

Is there any Linux based Boot Disk that will allow me to back up my current bios(as a bin fiile) and then copy it back if I need it? 

This computer also has a 20gb solid state drive.

---

### Post by Traxster on 2013-08-19
Success!!

O.k. guys, I know this topic has come up a lot in this forum. How do you upgrade your BIOS on a desktop/laptop that originally came with windows without touching your Ubuntu installation? Some have suggested to, make  dos boot disk or usb flash drive, which is what I tried, however, it would not load the file. (see previous post). After searching around for a while on the internet I found a Windows 7 PE SE LIVE CD ISO. I simply booted into Windows 7 live, loaded the file, ran it, and presto. BIOS upgrade success without any issues at all, and I did not have to touch my Ubuntu install. A friend said the disk is legal since you cannot install the software. I hope this helps someone in the same situation. The reason for the BIOS upgrade is, some options in the menu intermittently gray out.


I highly recommend, like a previous poster said,  to have a way to back up and reinstall your current BIOS before attempting this.

  
Traxster

---

