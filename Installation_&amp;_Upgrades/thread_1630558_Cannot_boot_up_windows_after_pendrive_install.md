---
title: "Cannot boot up windows after pendrive install"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by Chellygel on 2010-11-25
Hello all.

First, i would like to apologize for the noobiness of all of this post. Thanks in advance for your help.

Recently, i was trying to install Linux 10 onto a flash drive in order to install it on a separate computer.  After completing the Linux USB pendrive install i realized that the files has not installed onto my flash drive and had instead installed themselves somewhere onto my machine. At the time of the install, i believed that my attempts had failed and that ubuntu did not install properly. After rebooting my computer i came to discover Ubuntu booting up each and every time without option of going back to windows. I unplugged all USB devices, believing that somehow i may have installed the OS onto a different device, to no avail. I changed, disabled, and moved the boot order around to no avail. I attempted to dual boot install Ubuntu (in order to set the primary boot to windows as o avoid the issue) to which it states i am unable to partition drives. 

I am at a loss for what to do next. I'm afraid i have no idea. If there were a way to simply delete the file and reboot right back into windows that would be great. I'm just clueless!

Any help would be greatly appreciated

---

### Post by Rubi1200 on 2010-11-25
Hi and welcome to the forums :)

There are 2 things you need to do right now please:

1. boot into Ubuntu and run the boot info script linked at the bottom of my post (instructions are there). Post the results back here to the forum

2. find your Windows installation/recovery CD

Thanks.

---

### Post by NickN002 on 2010-11-25
Chellygel,

I had a similar problem a couple of months ago. I managed to get the computer booted into Windows using an external CD and then ran chkdsk and this repaired an error in the Windows partition and then the dual boot worked. I hope that this is helpful. Good luck

---

### Post by psoup1965 on 2010-11-25
I will try to jump in here ....

First Which Windws system are you using?  Windows < Vista will use one boot loader and Vista and newer will use another.

Basically what you will need to do is repair the boot for Windows (for your version). Such as in XP and older Google Fix XP MBR.

In a nutshell you will have to install your Windows install disk and go to advanced (or repair) and restore the boot.  (XP and older fdisk /mbr).

These will restore your boot sector to get back to Windows. Then you will need to download a tool to show your Linux boot... 

I like EasyBCD from Neosmart... it is free and there is a bunch of talk about how to use it.

---

### Post by Mark Phelps on 2010-11-25
If you're now booting into Ubuntu without the USB connected, the most likely explanation is that you overwrote Windows during the install.

If that's true, no boot loader repair, regardless of the version of Windows you HAD, is going to get Windows back.

Run the script that Rubi1200 mentioned -- so we can see what is NOW present on your system.  That info is needed for any further detailed technical advice.

---

