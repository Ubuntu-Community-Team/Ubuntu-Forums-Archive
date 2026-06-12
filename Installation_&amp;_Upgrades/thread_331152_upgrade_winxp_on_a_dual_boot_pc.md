---
title: "upgrade winxp on a dual boot pc"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by mavromilos on 2007-01-04
goodmorning to everyone,
I have a - already running - dual boot PC with the following partitions:
partition name    pri/log        system    capacity (GB)      comments
sda1                  primary      ntfs         9                        WinXP (sp2)
sda5                  logical        ntfs         4.5                      for restore (image of sda1)
sda6                  logical        ext3        10                       Ubuntu 6.10
sda7                  logical        swap       1.2
sda8                  logical        ext3        10                       for future use of 2nd linux distro
sda9                  logical        xfs          50                       for mythtv recordings
sda10                logical        fat32       70                       for movies storage
sda11                logical        fat32       84                       for music storage

my pc specs are:
processor: P4 2.8 ht , motherboard: asrock P4S55FX+ , 512MB RAM, HDD seagate 250GB SATA2, graphics card: asus R9250, skystar 2 pci, hauppauge pvr 150

I read a lot before chosing and installing Ubuntu as a newcomer in linux. 
Now I want to upgrade my first partition from winxp to win mce.
Before attempting that I want to ask if this will affect my dual boot.
What will happen to the bootloader? Will I be able to see Ubuntu again? 
Please keep in mind that I am not so familiar with Linux yet so forgive my ignorance.

Thank you all in advance.

V.M.
Milos, Greece

---

### Post by goatflyer on 2007-01-04
I haven't played with windows mce, but there is a strong possibility that upgrading your windows will overwrite grub.  Grub is the program that lets you choose which OS you want to boot from at startup.

You'll want to familiarize yourself with the instructions in this thread in order to repair the damage that the windows upgrade may or will cause:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by mavromilos on 2007-01-05
Thank you for your prompt reply.
Sorry for having been dissappeared.
I have to deal first with my SiSRaid conroller then with a missing hal.dll file and then I'll be able to upgrade.
As soon I have any news I'll post reply
Thanks

---

### Post by mavromilos on 2007-01-05
@ goatflyer
Finally my MBR was messed up.
Thanks to your link I managed to put back again GRUB into the MBR (though I used the "rescue a broken system" option of the installation cd).
I haven't yet been able to install winxp mce because of my sata2 hdd.
Thanks anyway for the kind response.
V.M.

---

