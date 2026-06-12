---
title: "Disk partitioner freezes on installation"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by csenciboy on 2010-12-18
Hi, all.

I'm a complete noob trying to install Ubuntu Server 10.10 on my first build for use as a file/media server.

When I get to the step to partition the drives, the installation freezes.  The screen says "Starting disk partitioner" and the progress bar stops at 45%.  It has done this three times now, and the longest I waited for it before rebooting was over an hour.

I am installing from a flash drive containing the .iso file, and I have the following hardware (in case that matters): asus p7h55-m pro mobo, core i3-540 CPU, 2x4GB ram, WD caviar green 1.5TB, WD caviar green 1TB, and Kingston 8GB SSD.

Has anyone experienced this issue and resolved it?

---

### Post by Quackers on 2010-12-18
Have you checked the MD5SUM of the downloaded iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Have you checked the usb image for errors?
While booting from the usb tap the F6 key and you should get an options screen. Choose "check cd for errors" and see if it runs ok.

---

### Post by sikander3786 on 2010-12-19
Welcome to the forums :-)

Only if **Quackers** advice doesn't solve your problem:

Were there any partitions on the HDD previously? Are you sure the HDD is in good health?

If possible, boot an Ubuntu Live CD (desktop) and from Applications > Accessories > Terminal, post the output of this command.

```
sudo fdisk -l
```

---

### Post by csenciboy on 2010-12-21
Thanks for the info. Ok, I don't think it's a physical hard drive issue because I have tried the install with each drive as the only one connected.  Also, I downloaded and used the WinMD5sum program and the iso that I'm using came back correct.

Background info: I don't have a CD drive installed, and the only way I was even able to get the installation to start was to put the iso file on one flash drive and the installer files on another flash drive, insert both of them, and when the installer fails to find a CD-ROM drive, I select "scan drives for iso file."  It eventually locates the iso on the second flash drive and gets me all the way to the point where the disk partitioner stalls.  Is this even right?  This entire installation process has really been difficult for me.

Thanks again for the help.

---

### Post by GarbloJones on 2010-12-25
Hey guys, 

I don't know if anyone else is still having this problem... it's been harshin my vibe all night. Finally I found a very helpful tip on another board (and this shoulda been completely obvious). 

I tried 3 different ISO burns, tried waiting ... watched a whole movie and it was still stuck at 47%.

So anyway, I would suggest unplugging all of your external media/storage (Flash/External HDs) ... my "starting disk partitioner" literally took less than a second to breeze through this time. 

Hope this helps! 
Merry Christmas.

---

### Post by csenciboy on 2010-12-28
alright, well i broke down and installed a DVD-RW drive.  It was only $20 extra but i was really hoping to avoid putting an optical drive in because it would only be used for OS installation. Oh well.  Ubuntu Server is installed now and the machine is well on its way to being a solid media server.

I still haven't figured out what I was doing wrong trying to boot from flash drive.  Thanks for all your help.

---

### Post by TonyCopping on 2011-02-05
Thanks for posting this I have just had the same initial problem with my HP Compaq D530 failing at 45%, the difference being that it also happend with the CD install untill I noticed that the 45% coincided with a "click" from the old built in floppy drive. I disconnected the floppy drive and removed it from the Bios and the CD installtion flew through !!

---

