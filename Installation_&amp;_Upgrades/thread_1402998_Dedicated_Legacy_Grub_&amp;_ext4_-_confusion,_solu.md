---
title: "Dedicated Legacy Grub &amp; ext4 - confusion, solutions"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by recluce on 2010-02-09
I run a machine that quadruple boots Ubuntu 9.04, Ubuntu 10.04, Windows XP and (every blue moon) a diagnostic partition. I found it a bit tiresome to reinstall grub every ten minutes while playing around with Lucid Alpha, so I decided that I wanted a dedicated GRUB boot partition.

My situation before setting up the dedicated GRUB partition:

/dev/sda1 (Dell Diagnostics, FAT16, bootable (chainloader)
/dev/sda2 (FAT32, Windows drive C, Windows boot files, no OS)
/dev/sda3 (extended)
/dev/sda5 (NTFS, Windows Drive D, Win XP)
/dev/sda6 (NTFS, Windows Drive E) 
/dev/sda7 (NTFS, Windows Drive F)
/dev/sda8 (reiserfs, Ubuntu 9.04 root)
/dev/sda9 (Linux Swap)
/dev/sda10 (ext3, /home)
/dev/sda11 (ext4, Ubuntu 10.04 root, Legacy grub boot files)

At one point (after having issues with GRUB2) I installed Legacy Grub to the Lucid root partition (from a Jaunty live CD). The system booted correctly into all installed operating systems.

Now I followed this excellent guide to set up a dedicated GRUB boot partition (using legacy GRUB):

[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

My layout after the changes: 

/dev/sda1 (FAT16, Dell Diagnostics, bootable (chainloader)
/dev/sda2 (FAT32, Windows drive C, Windows boot files, no OS)
/dev/sda4 (reiserfs, GRUB 0.97 dedicated boot partition)
/dev/sda3 (extended)
/dev/sda5 (NTFS, Windows Drive D, Win XP)
/dev/sda6 (NTFS, Windows Drive E) 
/dev/sda7 (NTFS, Windows Drive F)
/dev/sda8 (reiserfs, Ubuntu 9.04 root)
/dev/sda9 (Linux Swap)
/dev/sda10 (ext3, /home)
/dev/sda11 (ext4, Ubuntu 10.04 root)

The menu.lst file was transfered form the 10.04 installation, the other grub files were transferred from the 9.04 installation, because the grub folder there did not contain any GRUB2 junk and was easier to read and copy.

Booting with the new setup into Diagnostics, Win XP and Jaunty worked as expected. Trying to boot into Lucid produced a GRUB error 15 (file not found). Chainloading into the Lucid partition was not possible either.

At this point I was really scratching my head. Both the grub files on the Lucid partition and the Jaunty partition came from a Jaunty CD, so what was the difference? I did a side-by-side comparison anyway - and found that there was indeed a difference in file size for two files.

stage2 (orignally installed to reiserfs): 121460 bytes
stage2 (originally installed to ext4): 121740 bytes

e2fs_stage1_5 (originally installed to reiserfs): 8108 bytes
e2fs_stage1_5 (originally installed to ext4): 8288 bytes

All other grub files (excluding menu.lst) were identical between both installations. 

My reaction was "WTF..." - and I copied stage2 and e2fs_stage1_5 from the Lucid partition to the GRUB dedicated partition. To my surprise, Lucid booted fine after that.

Conclusion: it appears that legacy GRUB, at least as distributed with Jaunty, does some "black magic" and writes slightly different versions of stage2 and e2fs_stage1_5 to ext4 partitions than to other partition types, only these modified files seem to be able to handle ext4 partitions. This would explain conflicting reports here and in other forums, where some people say "Legacy GRUB can't handle ext4" and some say: "Legacy GRUB will handle ext4 just fine".

What I cannot understand is the reasoning for installing two different versions of the above mentioned files, as the "modified" version that can boot ext4 obviously boots anything else just fine. Any ideas?

Comments welcome...

---

### Post by recluce on 2010-02-12
*** bump ***

---

### Post by meierfra. on 2010-02-12
Was your Ubuntu 9.04 a fresh install or an upgrade  from an earlier version?
Upgrades do not replace the stage files in /boot/grub. So maybe your Ubuntu 9.04 was still using older stage files.

---

### Post by recluce on 2010-02-12
> **meierfra. said:**
> Was your Ubuntu 9.04 a fresh install or an upgrade  from an earlier version?
Upgrades do not replace the stage files in /boot/grub. So maybe your Ubuntu 9.04 was still using older stage files.

That would explain it, my 9.04 was an upgrade from 8.10. I am surprised that the upgrade to Jaunty would leave the old stage files from Intrepid behind - but live in and learn... ;)

Thank you for the explanation!

---

### Post by meierfra. on 2010-02-13
> I am surprised that the upgrade to Jaunty would leave the old stage files from Intrepid behind 
Any update has the chance to break something. And people somehow don't like it if you break their  working boot loader.

---

