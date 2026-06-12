---
title: "Combine 2 drives, 2 OS' into 1 dual boot system?"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by danawr on 2011-06-08
Hello,

Is it possible to create a dual boot system from two separate disk drives each having been created as a single boot computer?

I have an 80gb disk drive with Windows XP installed on it.
I have a 160gb disk drive with Ubuntu 11 installed on it.

I have installed the Windows disk drive as drive 0 and the Ubuntu disk drive as drive 1 in my computer. Each disk drive was set with cable select pin settings.

The computer boots to windows.

If at all possible, how would I go about setting up the system to dual boot to both windows and Ubuntu?

I have attached screen shots of part -l, gparted 80gb disk and gparted 160gb disk.

Thank you for any assistance you can offer.

Dana

---

### Post by jerrrys on 2011-06-08
i would first suggest a little reading

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+two+harddrives+hdd&sa=Search&cof=FORID:9#936](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+two+harddrives+hdd&sa=Search&cof=FORID:9#936)

---

### Post by oldfred on 2011-06-08
First issue is will BIOS let you choose boot drive or not. New BIOS with SATA control boot drive in BIOS. It is easy to set to boot sdb.

Old BIOS and IDE drives only booted primary master as set with jumpers on hard drives and BIOS just knew enough to jump to that drive.

Slightly newer IDE drives use the cable select and may have a BIOS that lets you change.

If BIOS lets you change boot drive just boot Ubuntu from sdb. Then run this to find the windows install.

```
sudo update-grub
```

If BIOS does not let you change boot drive, you have to install grub's boot loader to the sda or hd0 drive and boot with that. You can reinstall the windows boot loader if you ever separate drives.

If you can only boot windows because you can only boot from sda, then use liveCD to install grub's boot loader to sda.

Are you using grub legacy or grub2. Instructions to reinstall boot loader are different and you do not want to mix them up.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by walt.smith1960 on 2011-06-08
It involves $ but I've used this solution for a few years.  This is a newer version; I'm using BootItNG, the older version.  [http://www.terabyteunlimited.com/bootit-bare-metal.htm](http://www.terabyteunlimited.com/bootit-bare-metal.htm)  There is apparently an issue with Ubuntu's installer installing GRUB correctly; I usually have to install twice. Ubuntu's installer is such that after the first few minutes I just go do something else for a few minutes until it finishes.     The problem is manifested as booting to a GRUB rescue prompt.  It might be possible to do some sort of GRUB update but I find it just as easy to simply repeat the install.  Once it boots it will continue to work as expected.  If you choose to go this route, do be sure that GRUB gets installed in the Ubuntu partition, e.g. sda1 not in the MBR of the disk,sda.  If GRUB installs in the MBR-default location-it will disable the boot manager.

I had this boot manager since before I learned about Ubuntu.  I had 2 windows installs.  One partition  for everyday use and one "this needs to work" partition used for very restricted online stuff, nothing from download.com etc.

---

### Post by DinoT1985 on 2011-06-08
i have two hard drives in my laptop with Windows 7 and Ubuntu running on my master drive which has grub2 installed. 

wouldnt it just be the case of making Ubuntu the master drive and then running grub update?

---

