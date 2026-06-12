---
title: "Triple booting Vista, XP, Ubuntu"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by antoin_celtic on 2008-08-19
Am a new boy to this really.  Had Ubuntu before dual booting alongside Vista.  Now I have Xp thrown in the mix as well.  Thought I had it, but I get the dreaded 'Unable to install GRUB in (hd0)'
'Executing 'grub install (hd0)' failed'
'This is a fatal error'.
This happens at about 94% into the installation.
Have a partition for EXT3 and for swap.
Here's what it looks like when I type sudo fdisk -l into the terminal:-
**************************************************************************
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c2cba63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21992   176644769    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           21992       26215    33923072    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           26684       30401    29864835    7  HPFS/NTFS
/dev/sda4           26216       26683     3759210   82  Linux swap / Solaris

Partition table entries are not in disk order
**************************************************************************

Need help, I need Vista and Xp for various reasons but also want linux.  Tried all different combinations of using the advanced button and installing into different devices and so forth, even tried using EasyBCD in vista and adding linux as an entry but it doesn't work either.  Any help would be great.
Cheers

---

### Post by dstew on 2008-08-19
Apparently this is a bug in the grub-install program that one sees occasionally. It seems that, in some systems, grub-install has difficulty accessing grub stage1 and stage2 files that were placed on the (new) Ubuntu installation. One workaround is to re-install, but format the root partition as ext2 instead of ext3. Then, after the installation is finished, you can convert the ext2 partition to ext3 using tune2fs (see [this]("http://www.troubleshooters.com/linux/ext2toext3.htm")).

Another way to get around this is not to use grub-install at all. You would install Ubuntu the regular way, but at the boot loader step click the Advanced tab, and tell the installer not to install grub. The installation should finish OK. Then, you can install grub from a Live CD using the grub shell program, as described [here]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by antoin_celtic on 2008-08-19
Thanks for the advice I'll give this a try.
Cheers:)

---

### Post by antoin_celtic on 2008-08-19
Installed Ubuntu without GRUB and the installation went without any problems.  Tried that tutorial you posted but when i get the terminal to try and find GRUB it is understandably not there because I never installed it so that doesn't really work in my case ::confused:

---

### Post by SuperSonic4 on 2008-08-19
If you can boot into vista you can use easybcd I believe

---

### Post by dstew on 2008-08-19
> when i get the terminal to try and find GRUB it is understandably not there because I never installed it If you installed the Ubuntu desktop system, the /boot/grub directory is created, and the stage1 and stage2 files are put into it, but the boot loader is not placed in the MBR (if you chose not to install the boot loader using the Advanced tab).

To install the boot loader into the MBR (which is what grub-install tries to do) you have to first boot an Ubuntu Live CD. Open the Live CD terminal, and on the terminal command line enter```
sudo grub
```That should get you the grub shell command line, with the **grub>** prompt. Did you get this far?

---

