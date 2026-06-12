---
title: "Partition problem (sort of)"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by DMBryant on 2007-02-08
After reading about using VMWare to run an existing windows installation ([http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")) I went home last night with the intention of getting it working.  I installed VMPlayer, downloaded copies of the VM files that need to be altered and tried to run Parted to get the relevant disk information.

This is where the problem is.  Parted returns an 'Partitions cannot overlap' error and wont do anything else.

I have two drives installed in my machine hda and hdb.  Ubuntu is installed on hdb in one partition.  Hda contains my Windows partition, Linux swap partition, NTFS data partition and Ext3 data partition.

Both OS's work perfectly and I use Acronis Disk Director to manage the boot options (seemed like the easiest option at the time).  I also used Disk Director to create and resize the partitions on hda.

I ran fdisk -l /dev/hda which returned the following:

hda1    0002    9728    - Extended
hda2    5109    6530    - NTFS
hda3    6531    6995    - Linux Swap
hda5    0002    5108    - NTFS
hda6    6996    9728    - Linux

I think the problem is that Disk Director (or me by mistake) has created an extended partition the entire size of the disk and put all the other partitions inside it (including the primary XP partition).  Can this be resolved without losing any of the data?

The only thing I can think of at the moment is to delete hda6 (which is pretty much empty) shrink the extended partition (hda1) to be the same size as the 3 remaining partitions and then try and move the XP partition out of the extended partition into the free space.

Would this work?

Otherwise I just need some other way of finding out the information required to get VMPlayer working with the XP partition.

Cheers for any help.

---

### Post by DMBryant on 2007-02-09
Well, it seems that no one knows much about partitioning so I'll just have to try some things and hope I don't lose my data...

Cheers anyway.

---

