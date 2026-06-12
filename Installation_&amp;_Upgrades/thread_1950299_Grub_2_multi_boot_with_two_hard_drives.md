---
title: "Grub 2 multi boot with two hard drives?"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by cgb223 on 2012-03-31
Hey all, I have this laptop that I want to install Ubuntu on as well as Windows 8 Beta and maybe backtrack or openBSD. Not sure exactly how many its gonna be but the point is it will more than two OSes.

I want to setup Grub 2 in Ubuntu because its stable and I want it to load all of these OSes. 

Now my computer has two hard drives, and I was wondering if there was an issue with using Grub 2 to load OSes from different hard drives?

ALso, Im coming from using the original GRUB. Is there much of a difference? can somebody point me to a website to help me setup the necessary boot files?

---

### Post by darkod on 2012-03-31
There is no issue loading from different disks.

Also, usually most OSs would be located automatically so you shouldn't need to do anything manually with grub2.

The only thing, if you are installing another linux distro after ubuntu, watch out for advanced options during the install and tell it not to install a bootloader, so that it doesn't overwrite your ubuntu grub2 on the MBR.

After you finish the new install, simply boot ubuntu (the new OS won't exist the first time) and in terminal run:
sudo update-grub

That makes grub2 search for OSs and add an entry in the boot menu for all it finds.

If you need more info, you can google ubuntu grub2, I don't have many links ready at hand.

---

### Post by oldfred on 2012-03-31
If you are only used to grub legacy, it is a big change. 

I resisted at first, but that was partially because there was little documentation on how to do more than just boot. I was chainloading from a grub only partition to installs of legacy in each partitions boot sector -PBR. Now I only use grub2 and use it to boot everything including ISO on hard drives to install to another drive, flash drives formated to FAT, NTFS or ext4 (with journal turned off) and anything else I can find.

Grub2 does not like to install to a partition and can directly boot most other systems. It also finds those systems well with its os-prober that is run as part of sudo update-grub.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

The old menu.lst actually had three sectons. Settings (first part of menu.lst), an area that was automatically generated (in automagic) and an area to write custom entries (before or after auto magic). The new grub2 had each of those in separate places and combines them into grub.cfg (not editable) with the sudo udpate-grub. It helps prevent errors but many think it is more difficult. The os-prober is greatly improved. Grub legacy often would not find or not create a valid Windows 7 boot entry, but now with grub2 it finds just about everything.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
And look in drs305 signature for many links to other grub2 guides.

---

