---
title: "Installed 10.04 now can't boot XP"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by mtdave on 2010-05-02
I fixed my problem with Grub2 by reinstalling to the MBR. I also ran update-grub and can now boot to Ubuntu 10.04. XP shows up in my Grub2 boot list but when I select it won't boot. I get the following grub error.

error: the symbol 'grub_getcharacterwidth' not found.
grub rescue>

I have a feeling I wiped out my XP boot stuff in the MBR. I've seen some stuff on how to fix that but not entirely convinced thats the problem. Any ideas?

Here is my sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xad1bad1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13083   105089166    7  HPFS/NTFS
/dev/sda2           13084       19457    51199155    5  Extended
/dev/sda5           13084       19191    49062478+  83  Linux
/dev/sda6           19192       19457     2136613+  82  Linux swap / Solaris

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc6c9524

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601    7  HPFS/NTFS

XP is on /dev/sda1

boot.ini, ntldr and NTDETECT.COM are all there.

I have my Gateway System Recovery DVD but all it wants to do is reformat and reinstall XP. I'd really rather not do that!

Thanks

---

### Post by Morganman on 2010-05-02
Hi 
I had a similar problem and was sent this link on the forum.
It worked for me.

[http://sourceforge.net/apps/mediawik...ms:Boot_Sector](http://sourceforge.net/apps/mediawik...ms:Boot_Sector)

---

### Post by kooia on 2010-05-02
I doubt it wiped it out.  Check it from Ubuntu

I'm having the same problem...  I can't boot to Windows

---

