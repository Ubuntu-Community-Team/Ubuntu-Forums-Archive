---
title: "Setting up for Multiple Boot"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by olaboy- on 2005-06-22
I'm using Windows XP and I'm planning on trying out linux, however I want to keep windows as my primary OS. How do I make it so at startup the black screen comes up that displays the two OS's, or does this happen automatically after it's installation. 

Also I have to partition my hard drive, can someone give me an example of how to do it? I want 55gb for Windows and 25 for Linux.

Last, should I download it (I'm on dial-up) or order one of those free CDs (Is it for real?)

---

### Post by Seti on 2005-06-22
Yes, ordering the CD's is a good idea if you're on dial-up; the installer is a 600+ MGb download. 
By the looks of how you want to partition your disc, looks like you have the right idea.  
You'll want to have Windows on a primary partition (this will be called /dev/hda1). You'll then want to Make an extended partition with the remaining free space; the linux installer will guide you through the rest. It will automatically detect windows and set up GRUB for you so that you have a boot menu when you turn on your comp. 
Enjoy!

---

### Post by mingus on 2005-06-23
[QUOTE=olaboy-]I'm using Windows XP and I'm planning on trying out linux, however I want to keep windows as my primary OS. How do I make it so at startup the black screen comes up that displays the two OS's, or does this happen automatically after it's installation. 

Also I have to partition my hard drive, can someone give me an example of how to do it? I want 55gb for Windows and 25 for Linux.

Last, should I download it (I'm on dial-up) or order one of those free CDs (Is it for real?)[/QUOTE]

If you "want to keep windows as your primary OS", does that mean you want Windows to control the boot.?  Here is a HowTo on doing that.

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

In short, there will (a) need to be a file created from Ubuntu that gets put in the Windows C: directory and (b) the Windows file c:\boot.ini needs to have an entry added that points to Ubuntu.

A few guidelines:
* Because you will be changing the disk partitioning, have a reliable Windows backup first.
* Have Windows recovery media in case of a problem, if W2K/XP then preferably an install CD.  At the minimum, a W98/ME/DOS bootable diskette (if you don't, see [www.bootdisk.com)](www.bootdisk.com)).
* Do not use Windows Disk Manager to create any partitions to be used by Linux.

If you decide to use Ubuntu's boot manager (grub or lilo) instead of Window's ntldr, you can still use the above HowTo.

---

