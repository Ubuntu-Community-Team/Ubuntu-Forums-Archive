---
title: "Please somebody help"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-11-16
I have installed wubi, I used dual booting with vista, but I have select E:\ drive to install ubuntu insted of c:\ where vista is installed, now I want to uninstall ubuntu then reinstall it but E:\Ubuntu\Uninstall-Ubuntu.exe refuse to launch, is there any other way of uninstalling ubuntu  ?

---

### Post by geoffjay on 2008-11-16
I've never used wubi before so I can't help there, but the common way to dual boot windows/linux is to just install linux normally on a different partition, let the installer put grub on the boot loader and it will add the necessary entry for the windows install you have on your c: drive so that you can still get into it.

When the ubuntu installer comes to the partition section you need to use manual partitioning and think real hard about what you're going to do there. Typically you'll have a drive that comes up as sda and on that drive there will be sda1, sda2, etc... It's likely that the first partition (sda1) is your c: drive for windows. You'll probably want to do some size checks to make sure of this. 

Once you've found the partition that you're going to install to you need to delete the partition that you want to install onto, make a new partition for swap space (usually the same size as the amount of RAM in your machine), and make a partition for the rest of the OS giving it "/" for the mount point and whatever you want for a file system. Make sure not to format your c: partition, that can be a real headache because you'll have to re-install windows and if you install the M$ bootloader it won't recognize the ubuntu installation which means you'll have to figure out how to add an entry for it in windows manually.

---

### Post by mikewhatever on 2008-11-16
How about trying the Windows add/remove programs? I think there should be an entry for Ubuntu.

---

### Post by hoboy on 2008-11-17
> **mikewhatever said:**
> How about trying the Windows add/remove programs? I think there should be an entry for Ubuntu.

This is actually the problem it is not listed their, that is weird.

---

### Post by oilchangeguy on 2008-11-17
> **hoboy said:**
> I have installed wubi, I used dual booting with vista, but I have select E:\ drive to install ubuntu insted of c:\ where vista is installed, now I want to uninstall ubuntu then reinstall it but E:\Ubuntu\Uninstall-Ubuntu.exe refuse to launch, is there any other way of uninstalling ubuntu  ?

you might have better luck if this were posted in main support, wubi.

---

