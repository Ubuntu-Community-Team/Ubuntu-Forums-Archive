---
title: "Live USB , testing Ubuntu + Wubi"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by II Luis II on 2010-07-21
Hey guys, I've decided to try and use a USB to boot Ubuntu just to test it out. I have come across a couple of things I want to check with people who have done this. First, the USB Installer from the downloads page is asking me whether I want to format Drive (F: ) which is my USB drive. Should this be done, and what does it do? I am using Vista BTW. Also is using the USB to test whether Ubuntu will run on my laptop likely to cause any problems that will cause harm/damage to my machine? 

Also I have posted up before about using Wubi on my vista to install into my (D: ) drive which has 111GB free, to run along side my Vista. Some one mention that this 

"As to disk shrinkage, I'm guessing you're using Win7 on the ACER, or maybe Vista? Either way, if you want to install using traditional dual-boot (with each OS in its own partitions), use the built-in Disk Management utility to shrink the "D" drive to make room for Ubuntu. Do NOT allow the Ubuntu installer to shrink the partition. Doing so is asking for trouble later."

Is this person suggesting that installing Wubi into the empty (D: ) drive will cause the space to shrink down to 30GB instead of 111GB and I lose the space in that drive other than what Ubuntu would be taking up? (All that is in the (D: ) Drive is a shortcut to my (C: ) Drive).

If this thread makes sense then what do you think about my problems/questions?

---

### Post by phillw on 2010-07-21
Hi,

if all you want is a live usb to 'play' with, then use unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) There is no need to worry about hard-drive partitions. Ubuntu 10.04 is one of the (many) systems it can install to a USB stick.

Just remember, you must have a computer that can both boot from USB and have your BIOS set to boot from USB ;) A great resource for things like that is [http://www.pendrivelinux.com/category/bios-usb-boot-options/](http://www.pendrivelinux.com/category/bios-usb-boot-options/) (I'm sure some of the things that they do to usb sticks is barely moral, probably fattening - but, there's not a lot they cannot do with a usb stick :D ) Joking aside, it's an excellent site.

Regards,

Phill.

---

### Post by gordintoronto on 2010-07-21
If you are making a bootable flash drive, it is a good idea to format it first, to make sure it is empty. When you are running from the flash drive, you will probably have access to the files on your hard drive, so you could cause problems by deleting files, but Ubuntu itself will not cause problems.

The person who was talking about shrinking a drive, was not talking about Wubi. He was talking about a "dual boot" setup, where Ubuntu has its own partition or partitions.

This site: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) 
tells you how to use Windows to make a Linux boot drive. I think Unetbootin is only for Linux, so it won't help you if all you have is Windows.

---

### Post by C.S.Cameron on 2010-07-21
If you are using the USB installer from the Live CD there is no need to format your flash drive as long as it is FAT32, if it is FAT16 then back up anything valuable on it and let the USB installer format it. Usb-creator will not touch your internal HDD.
I usually let the Ubuntu installer shrink my Windows partition when installing a dual boot system. 
The main thing is to **thoroughly** defrag Windows before proceeding.

---

### Post by II Luis II on 2010-07-22
How do I know if my USB stick is FAT32? And what does the formatting actually do? Thanks for your comments everyone, I think I can nearly actually make this USB live thing work and test Ubuntu at last!

---

### Post by II Luis II on 2010-07-22
Please anyone? I really need to know, I would like to test linux ASAP

---

### Post by C.S.Cameron on 2010-07-22
You can right click on your USB drive in Windows Explorer and select Format or right click it in Nautilus from the Ubuntu Live CD and select Format.
Formatting sets the partition up for the file system that will be used on it.
Most of the Live USB creators will format the flash drive for you also.
If you don't have anything valuable on it there is no big deal.

---

