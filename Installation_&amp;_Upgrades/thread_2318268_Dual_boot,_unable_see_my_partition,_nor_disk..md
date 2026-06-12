---
title: "Dual boot, unable see my partition, nor disk."
date: 2016-03-24
forum: Installation &amp; Upgrades
---

### Post by bilout on 2016-03-24
Hi, I have a new shiny Dell XPS 13 2016 laptop, with win10, I am trying to set a Dual boot Win10/Ubuntu.

 I  have created a partition in win10, first in un-allocated, without  success. Then convert it to ext3, then ext4(with Partition Wizard), none  of this allowed me to see my partition when I boot from ubuntu live usb  in UEFI.

I have already disable safe boot  in Bios, and Fast start in win10, gpart, fdisk didn't return anything  about my partition, I just see 1 - sda, which is the usb drive itself.

I spent already a few nights on the problem, even tried with Mint as well, to be sure it wasn't ubuntu, all for the same result. 

A bit of help would be much appreciated...

---

### Post by grahammechanical on 2016-03-24
Are you sure that you are booting the live session in EFI mode & not BIOS/legacy/CSM mode?

The machine will have a UEFI boot system with GPT partitioning. Gparted running from a Live session will have no problem seeing the partitions on a disk with GPT partitioning. Nor will the Disks utility.

But there may be a problem if the Live session is not loaded in EFI mode and the other OS on the drive has been installed in EFI mode. I say "may be" because I do not have a machine with a UEFI boot system and I have never examined this issue myself.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by oldfred on 2016-03-24
This system may have the new NMVe drives.

If not this system, yours should be very similar:
 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)
Uses Intel Wi-Fi adaptors
[http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/](http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)

---

### Post by bilout on 2016-03-24
Thank you Graham,
I am indeed booting in UEFI mode, I get the right boot screen, this is allright I think.

I think Ubuntu should be able to see the volume, even if it was GPT, and formated for Windows, right ?
why is it that nothing shows at all ? could it be because it is a PCi SSD (M2) ? and not a SATA? I was also thinking it could be something Dell related, maybe... 
I am going to try now with Ubuntu 15, this was with 14.04.

---

### Post by bilout on 2016-03-24
I just tried wit Ubuntu 15.10, same same...

---

### Post by bilout on 2016-03-27
Yes, my Dell as a NMVe drive, looking at your first link i find out that I have to switch RAID to AHCI, I did that and this is finally working, Thanks !
now i am running in an other little problem/confusion with the disk management before install, my partition is not viewed as "free space" so i am not able to partition it for swap...

---

### Post by oldfred on 2016-03-27
Are you using newest gparted to partition in advance?
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php) 

Post this:
sudo parted -l

---

### Post by bilout on 2016-03-27
Thanks, I had no idea that NVMe could be the problem,
that probably also explain why fdisk didn't see anything at all, 
and Gparted was probably older, I guess if I go for Ubuntu 16, it will work out of ISO boot, right?

---

### Post by bilout on 2016-03-28
I confirm that last release of ubuntu mate 16 could detect all partitions, with gparted.

---

