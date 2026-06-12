---
title: "RAID 1 (mirroring) on fresh install"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by kalahari875 on 2005-10-23
I'm trying to install Kubuntu 5.10 on two empty 20GB IDE hard drives and configure them as RAID 1. I know the installer is supposed to handle this, but the options are confusing--I am not experienced with this setup. I've installed various distros many times, but always on a single drive. The drives are both masters on separate IDE controllers.

Can someone help me pick the right options? I'd like the two drives to be mirrored and both bootable. 

I am first presented with the Partition Disks screen. The options are to:
1) Erase entire disk: IDE1 master (hda) 
2) Erase entire disk: IDE2 master (hdc) 
3) Erase entire disk and use LVM: IDE1 master (hda)
4) Erase entire disk and use LVM: IDE2 master (hdc)

I tried choosing option 3, thinking LVM to be a good idea. Is this a mistake? After doing this, it set up the following:

IDE1 master (hda)
  #1 primary 255.0 MB (lighting bolt icon) (light smiley icon) ext3   /boot
  #5 logical 20.3 GB (dark smiley icon) lvm
IDE2 master (hdc)
  pri/log 20.5 GB FREE SPACE
LVM VG Ubuntu, LV root - 19.4 GB Unknown
  #1 19.4 GB (light smiley icon) ext3   /
LVM VG Ubuntu, LV swap_1 - 859.8 MB Unknown
  #1 859.8 MB (light smiley icon) swap     swap

How do I take this to a RAID 1 (mirrored) configuration? Do I need to change the ext3 partitions it created on IDE1 to raid partitions? I am not sure if I needed to do anything with LVM; I tried creating raid partitions to match the partitions it created on IDE1 (255.O MB raid and 20.3 GB raid) and changing the IDE1 partitions to raid partitions, and then setting up the mirrored pairs (pairing off the 255 MB partitions first and then the larger ones). It lets me do this, but the system wouldn't go past the partitioning screen to install in this manner.

Thanks for helping.

---

### Post by mättä on 2005-10-30
You should choose to manually set up your partitions. Only thgrough there can you activate RAID. You don't need LVM.

What you do instead is creating partitions on both harddrives on which you want to create your RAID. The created partitions should be of type RAID (you can set this with the partitioning tool in the installer).

After the partitions are created you can create the RAID by selecting the according option in the partitioning tool. Follow the steps und your RAID 1 should be set up correctly.

---

### Post by kalahari875 on 2005-11-01
Thanks. What do the partitions look like if I want to mirror the entire installation, for example to have only swap partitions and a partition for mounting / ? Do I create one swap and one RAID partition?

---

### Post by kalahari875 on 2005-11-03
Ah! I found out how to do this. Thanks to Patrick at howtoforge for writing such an excellent howto:

[http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

---

