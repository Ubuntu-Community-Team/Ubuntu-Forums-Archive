---
title: "dual booting xp, redhat and ubuntu 6.06 without installing grub on MBR"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by minesh on 2007-08-28
I have two hard disks, the first one (master) contains windows xp and redhat 9 and they work together well. when installing redhat(a long time back),  i did not installed grub on the MBR, but in the boot partition and then raw copied the file into the windows C:\ and edited the boot.ini file. So far things are perfectly fine.

now, i have a second hard disk and i installed ubuntu on this disk with the alternate cd. i chose guided partitioning in which the complete disk was divded into ext3 and swap filesystems. i chose not to install grub on the MBR and installed it in /dev/hdb1. then i made a  raw copy of it on my usb drive and copied it to the windows C:\ partition. i edited the boot.ini file to look like this,

[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\REDHAT.LNX="RedHat 9 Linux"
c:\ubuntu.lnx="Ubuntu 6.06 Linux"|

When, i restart the machine i get the 3 options, but when i select ubuntu i get a black screen saying 'GRUB' on the upper left corner and thats all .. nothing happens from then on. i have to reset to get into windows again. I can still boot into redhat but not into ubuntu. AM  I missing something here? would appreciate any help to get this thing working. 


regards
minesh

---

### Post by MQMike on 2007-08-28
Just a quick thought . . .
You can try to re-install GRUB (also) to the MBR of the second hard drive, which looks like it will come up as (hd1).  Leave the GRUB you put in sdb1 (= (hd1,0)) as it is.
Doing this will not hurt anything at all, but maybe that's what's missing.

You know, at a terminal you get a GRUB prompt
sudo grub
then
grub> root (hd1,0)
grub> setup (hd1)
quit
$exit
re-boot to test it.

I'm assuming (hd1) is how BIOS (and therefore how GRUB) sees your second hard drive.
You can test it using geometry at the GRUB prompt:
grub> geometry (hd1)
(or geoemrty (hd0), etc.))
to see what is where.

I've never used NTLDR for the dual booting, but can you direct NTLDR to the MBR of the second hard drive (vs the partition-boot sector at sdb1)?

---

