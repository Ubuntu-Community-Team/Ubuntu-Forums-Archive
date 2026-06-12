---
title: "GRUB2 fails to load after install"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by Tye on 2010-08-31
G'day Everyone,

I am a long time ubuntu user (4.10) and have had a fair bit of experience installing ubuntu and the many mishaps along the way.

So after having no internet for a year I decide to try the new 10.04 flavour by ordering the cd from the site.

Installation went well, no hiccups. But when I restarted the comp
it went straight to Xp, so I thought I'll just use the SGD to boot the partion anyway and fix this small problem later.

Well...

After SGD confused sda with sdb, I figured out that GRUB2 is now the standard boot loader.

So thats where I am lost, I have searched the 
forums quickly (25 pages or so..) and realise that I am not going to fix this easily or by trial and error.

here's some info

Ubuntu 10.04 LTS
WinXP SP3
Intel P4 3.0
1.5 GB RAM
Nvidia 6200 agp
IDE HDD 36 GB     sda1 NTFS, sda2 ext3(/), sda3 swap
SATA HDD 160 GB   sdb1 NTFS, sdb2 ext3(/home)

Cheers in Advance !!

---

### Post by andrewthomas on 2010-08-31
Go to 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
and follow the instructions and post the results in your next post

---

### Post by Tye on 2010-08-31
Thanks for the prompt reply Andrew

---

### Post by andrewthomas on 2010-08-31
Did you switch the boot order in BIOS? Everything seems ok.  Try and reverse the boot order.

---

### Post by Tye on 2010-08-31
I cannot change the boot order 

when I use SGD to boot the partition /slice i get this error:

   Booting '2 hdb2 sdb2 (hd1,1) hd1s2 ext2fs
set out_device=(hd1,1)
set out_hurd_hd=hd1
set out_hd=hd1
set out_linux_letter=b
set out_lide_hd=hdb
set out_lscsi_hd=sdb
set out_part=(hd1,1)
set out_lide_part=hdb2
set out_lscsi_part=sdb2
set out_hurd_part=hd1s2
set out_linux_part=b2
set out_part_n=1
set out_linux_end=b2
back
back
set aux_slice=(hd1,1)
rootnoverify (hd1,1)
chainloader +1

Error 13: Invalid or unsupported execute format

---

### Post by andrewthomas on 2010-08-31
using grub2

(hd1,2) is your /home directory

(hd0,2) should be your /

maybe that super grub disk is using grub

I would use a Live CD to reinstall grub2 to the MBR of whichever drive boots first (which I would assume to be sda) as per: 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Tye on 2010-08-31
from what I've read quickly on GRUB2 
it no longer calls the first hdd 0

i have re installed grub2 twice now
and ubuntu again once

I am almost at the point of just trial and error 

like trying a different hdd
 trying a lone install (no xp)
 trying usb drives
 trying death threats (which works more than you'd think)
 trying #ubuntu on freenode

thanks for giving me a hand andrew

---

### Post by andrewthomas on 2010-08-31
> **Tye said:**
> from what I've read quickly on GRUB2 
it no longer calls the first hdd 0


It does call1st drive 0, but the first partition is 1 as opposed to 0 in grub.

---

### Post by Tye on 2010-08-31
ahh yep ok

this part of the results.txt doesn't seem right to me

============================= Boot Info Summary:=====================


 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #2 for /boot/grub.
 
=> Windows is installed in the MBR of /dev/sdb

=============================================================



should both ntfs partitions have "Boot files/dirs:" on them?

---

### Post by Tye on 2010-08-31
fixed it!

My sdb ntfs partition was flagged as "boot"

which is weird cos I have never installed and operating system on it.

---

