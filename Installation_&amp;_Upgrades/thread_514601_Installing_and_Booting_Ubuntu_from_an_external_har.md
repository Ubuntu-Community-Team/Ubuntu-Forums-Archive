---
title: "Installing and Booting Ubuntu from an external hard drive"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by programmerxsv on 2007-07-31
Hello, 

                 I have an external hard drive which is connected to my pc (which is running XP pro) via USB 2.0. What I want to do is install Ubuntu on my external hard drive and upon turning on my pc being able to boot from my internal hard drive (XP pro) or my external hard drive (UBuntu). 

                   Could anyone help guide me threw the process of installing ubuntu on the external drive and then installing and configuring a program such as grub so i am able to boot from either drive/ OS upon PC start up!!

Thanks for your time!!!:)

---

### Post by confused57 on 2007-08-01
> **programmerxsv said:**
> Hello, 

                 I have an external hard drive which is connected to my pc (which is running XP pro) via USB 2.0. What I want to do is install Ubuntu on my external hard drive and upon turning on my pc being able to boot from my internal hard drive (XP pro) or my external hard drive (UBuntu). 

                   Could anyone help guide me threw the process of installing ubuntu on the external drive and then installing and configuring a program such as grub so i am able to boot from either drive/ OS upon PC start up!!

Thanks for your time!!!:)
This thread should get you started:
[http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external)

You could try a routine Ubuntu install first, if you prefer not to use the above guide.
Basically, you'll need to set your external hard drive in bios to boot before your internal hard drive...do this before you boot up the live cd to install Feisty.  When you're installing, make a note of how the partitioner/installer recognizes your external hard drive(e.g. /dev/sda, /dev/sdb, etc).  At the step to install grub, press the "Advanced" option to install grub to the external hard drive's mbr...here is where you would type in "/dev/sda" or "/dev/sdb", without quotes.  

The mistake many people make is installing grub to the internal hard drive's mbr and they're not able to boot Windows with the external hard drive disconnected.

---

