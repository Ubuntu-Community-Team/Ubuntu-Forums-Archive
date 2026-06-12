---
title: "livecd installer doesn't see old partitions after windows install"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by tedrampart on 2007-06-22
so heres the deal..

I needed to install winblows xp on my laptop to be able to use my recording studio hardware/software.  

I had a solid version of feisty setup already, with a seperate swap and home partition, also had previously setup a partition for winxp.  

I ran the xp installer, and it said I couldn't use the alloted partition because of MBR, so I deleted my feisty root partition, and the winxp partition, formatted them into 1 ntfs partition.

windows installed la la la.. reboot into livecd...

this is where I go nuts...

I clicked the install icon, went through til I got to the partition setup.  now all it sees is /dev/sda, and all I can do is write over the whole drive.

going into the terminal running fdisk -l, I see this:
root@ubuntu:~# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         498     4000153+   7  HPFS/NTFS
/dev/sda2             872        9730    71154374+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3            9360        9730     2972412   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/sda5            1370        9359    64179643+  83  Linux

so I know my partitions are still there, but the installer, or gparted can't see them.  I'm completely at a lose as to where to go from here.. I've searched the forums, but haven't been successful at finding anything to help.  I'm tired, frustrated, and almost threw my laptop already.. 

please help me I don't want to lose all my data because windows has control issues...

basically I want to have my windows partition (sda1), linux root partition, swap, and /home partition working all together happily..I believe swap is sda3, and /home is sda5. the rest is empty space I was going to use as root.

edit - here's a screenshot, I also went back into the windows installer, and tried to make the free space 1 partition, but it wouldn't let me either.

---

### Post by tedrampart on 2007-06-22
okay, so I solved it.

went into parted, then saw that some of the partitions were overlapping.  went back into windows installer, and removed all the partitions except the home partition.

then reinstalled windows.. then went back into the livecd, and I could then use gparted to set up the remaining partitions.  

I've never seen overlapping partitions before.  

everything seems to be fine, linux and windows are now both operational, with all my info still intact.

---

