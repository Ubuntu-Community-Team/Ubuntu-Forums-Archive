---
title: "Can't install Ubuntu (screen goes black)"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by Chris_Nickel on 2012-01-13
Hi,
I've been trying to install Ubuntu for a few hors now and am getting nowhere.
My system is a Gateway NV55S with a Quad Core A6-3400M AMD processor. The system has 4gb of ram and an AMD Radeon HD 6520G graphics chip with 512mb of graphics system memory. The computer is running a Windows 7 64 bit OS.
 
Basicly when I try to install Ubuntu, either the 32 or 64 bit system, the lnguage choice screen comes up and after I select a language the CD starts spinning and the screen goes black. This happens when I try to install from startup, the live CD or install within Windows. The only thing I have noticed that was different among the three is that when I booted from the LiveCD I heard the startup sound, but still no image.
 
I have managed to get the system to startup from the LiveCD and drop to a command line by using <F6> and then choosing nomode. I have even tried using <F6> <Esc> and then choosing text install to get the install to check the system for the correct video mode.
 
So far nothing has worked.
 
Any suggestions?
 
Thanks
 
-Chris

---

### Post by Rubi1200 on 2012-01-14
Hi,
there are a few things you can check to try and narrow down the issue:

1. is the image corrupt?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. did you burn at the lowest possible speed?

3. do you have RAID, LVM, or any other non-regular setup?

4. in Windows Disk Management utility, are the disks labeled as Basic or Dynamic?

Report back with findings please.

---

### Post by Chris_Nickel on 2012-01-17
Hello and thanks for the response.
Sorry for the delay in answering, I was off over the weekend and yesterday.
Anyway, in response to your questions:
 
1. is the image corrupt? As far as I can tell, the image is correct. We have used these images to install on other computers in the shop.

2. did you burn at the lowest possible speed? These disks were burned by saving them to the CD/DVD drive, so they were burned at the drive's default setting. Sorry, I don't know what that is.

3. do you have RAID, LVM, or any other non-regular setup? No, the setup is pretty much out of the box basic. 

4. in Windows Disk Management utility, are the disks labeled as Basic or Dynamic?
All of my disks read as basic.
 
Thanks
 
-Chris

---

### Post by kamal7725 on 2012-04-26
I also has the same problem with the same system, only difference is my laptop is of HP. I think there is some problem with this system configuration. I am also couldn't install the Ubuntu same version.

---

### Post by DougC on 2012-04-26
I get this as well. Black screen with a blinking cursor at the top left of the screen. No desktop.

I've got a Desktop Intel i5-2500K, 4Gb RAM, nVidia 550Ti graphics. 

I also had this issue with a download of the Beta. Ubuntu 11.10 CD boots fine

---

### Post by DougC on 2012-04-26
I found I can get by it by setting nomodeset at boot. But this drops me into a lower res desktop which I can't change in setting.

I think I'll give installing a go and see what happens.

---

### Post by DougC on 2012-04-26
Ok, install was the same. I ended up having to use nomodeset to get it to boot.

But it would go to a low res Unity 2D desktop. I installed the nVidia drivers and it seems ok now. phew.

---

