---
title: "Where should I place GRUB 2?"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by cat2005 on 2011-05-15
Hi All,

I have the following setup
a) 1st sata hdd - Ubuntu 9.04 (32 bit)
b) 2nd sata hdd - Win7 (64 bit)

I am on GRUB legacy.  I am going to do a clean install and replace Ubuntu 9.04 with Ubuntu 10.10.  I plan to leave my Win7 install alone.

When I am installing Ubuntu 10.10 over Ubuntu 9.04, where should I place GRUB 2?

The choices I've always seen:  i)  MBR or ii) boot sector of Ubuntu

I do not recall which setup I have now but I can confirm that when I start the computer, I get a GRUB menu that lets me choose Ubuntu or Windows.  Ubuntu is the default if no choice is made within 20 seconds.

I like that setup and want to replicate it with GRUB 2, if possible. 

***If that is what I want, then I should place GRUB 2 on the MBR, correct or not?***

Note, I do not intend to install any other OSes.  In other words, my 1st sata hdd will only have ubuntu and my 2nd sata hdd will only have windows.

Thanks.

---

### Post by MAFoElffen on 2011-05-15
> **cat2005 said:**
> Hi All,

I have the following setup
a) 1st sata hdd - Ubuntu 9.04 (32 bit)
b) 2nd sata hdd - Win7 (64 bit)

I am on GRUB legacy.  I am going to do a clean install and replace Ubuntu 9.04 with Ubuntu 10.10.  I plan to leave my Win7 install alone.

When I am installing Ubuntu 10.10 over Ubuntu 9.04, where should I place GRUB 2?

The choices I've always seen:  i)  MBR or ii) boot sector of Ubuntu

I do not recall which setup I have now but I can confirm that when I start the computer, I get a GRUB menu that lets me choose Ubuntu or Windows.  Ubuntu is the default if no choice is made within 20 seconds.

I like that setup and want to replicate it with GRUB 2, if possible. 

***If that is what I want, then I should place GRUB 2 on the MBR, correct or not?***

Note, I do not intend to install any other OSes.  In other words, my 1st sata hdd will only have ubuntu and my 2nd sata hdd will only have windows.

Thanks.
The install for 10.10 will ask if you want to install grub to /dev/sdx or /dev/sdaxy, where x=the drive number and y=the partition number.

You want "/dev/sda", which as you refrered, would be the MBR of the first drive (sda or HD0), and NOT to a particular partition.  There are exceptions for that, but I don't see that you fall into one of those exceptions.

If you "don't" want Windows to be found and effected by Grub and it's menu-> Unplug that drive during the install, otherwise...  It will run osprober and find it.

---

### Post by cat2005 on 2011-05-16
> **MAFoElffen said:**
> 
If you "don't" want Windows to be found and effected by Grub and it's menu-> Unplug that drive during the install, otherwise...  It will run osprober and find it.

Sorry, I don't understand your statement.  Are you saying that I should follow your suggestion (in quotes above) if I do NOT want GRUB to find Windows? 

Is that correct?

What happens if GRUB does not find Windows?

---

### Post by Quackers on 2011-05-17
Install grub to the MBR of your Ubuntu hard drive (whether that be /dev/sda or /dev/sdb, whatever - you can check with gparted on the live cd).
Grub2 is not normally installed to a partition (like /dev/sda5, for instance).
If your Ubuntu hard drive is set as the first HDD to boot in your bios you should be good.

---

