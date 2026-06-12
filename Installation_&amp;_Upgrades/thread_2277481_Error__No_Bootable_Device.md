---
title: "Error:  No Bootable Device"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by Marstig on 2015-05-09
I recently had some issues with Malware on my Windows 8.1 installation and decided to switch over to Ubuntu.  I created a Live USB and installed the system on my laptop without any hiccups, however, when I attempt to boot the computer I get the, "no bootable device error".  I am thinking this has something to do with the filesystem and partitions but I cant be sure (I am a total Noob to LInux).  I have downloaded the boot info tool and have the following link with my info in it:

[http://paste.ubuntu.com/11040866/](http://paste.ubuntu.com/11040866/)

Please note that if I leave the usb stick in I am able to boot directly from it without any issues.  

Could someone please point me in the right direction with this?

Thanks for the help!

---

### Post by grahammechanical on 2015-05-09
On my machine a USB memory stick with an OS on it is seen by the BIOS as an external USB drive. The BIOS boot priority setting are ineffective in this case. I have to go into the BIOS settings for hard drives and set the hard drive to boot from. It could be that your BIOS is looking to a USB port for an operating system and not finding one but it is not looking to the hard drive as an alternative.

In my case I have select which drive to boot from and maybe to need to do that also.

Regards.

---

### Post by ubfan1 on 2015-05-09
From the efibootmgr section of your pasting, your hard disk/ubuntu is not in the boot order.  Try adding it in the UEFI settings(aka BIOS), or your could add it directly yourself by running efibootmgr.  You might also want to consider the disk partitioning -- having a 30G root partition, (or even two, one for testing new releases), and the rest for a /home partition for your release independent files is a usual setup.  What model is your machine?  They each have different install issues, and knowing that might help us give better suggestions.

---

### Post by oldfred on 2015-05-09
It looks like you have your efi partition, a very large /boot partition,  and swap.
But then no / (root) partition?? Script did not show fstab which would be in / and other data seems to be missing?
Most desktops do not need a separate /boot partition unless installing with full disk encryption which uses LVM. LVM is also more advanced logical partitions overlaying the physical partitions.

---

