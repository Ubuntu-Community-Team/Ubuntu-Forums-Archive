---
title: "Epic RAID installation problems"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by iandotcom on 2008-04-11
Hey,

I was hoping if I could get a few pointers on getting a copy of gutsy gibbon installed on my computer.

Its a Dell Dimension 9150 with 2 x 250 GB hard drives in a RAID 0 array. Its got Windows XP already installed on the array, and I was hoping if I could make another partition on this drive to install Ubuntu on.

I did this on my laptop, but this was just a single hard drive. I booted into Ubuntu on a USB memory stick and used the partition manager to do the partitioning. Managed to successfully install everything fine, partitions working properly too :D

I tried to do this on my RAID array computer, but the partition editor shows the two 250 GB drives as individual devices which are unformatted. I read around and found this app called dmraid which is supposed to allow Ubuntu to recognise RAID arrays.

In Windows, the RAID array appears as three partitions. There is a small partition at the beginning of the array, an FAT16 EISA configuration, a large NTFS partition where Windows and all my files are stored, and a FAT32 partition which I think is a utility partition installed by the manufacturer. I looked in the Windows device manager for the RAID controller, and it was listed as a "Intel 82801GR/GH SATA RAID controller."
 
So I installed dmraid and 4 additional devices appear alongside the two original devices which appeared in the app. These are:
 
[LIST]
**/dev/mapper/isw_cgcihaaba_ARRAY (465.65 GB)**
This disk has a similar configuration to the partitions layout from Windows.
 
The two smaller partitions have the error:
*Unable to read the contents of this filesystem! Because of this some operations may not be available.*
 
The bigger NTFS partition has the error:
[I]Failed to startup volume : Invalid argument
Couldn't mount device '/dev/mapper/isw)cgcihaaba_ARRAY' : Invalid argument
 
ntfsresize v1.13.1 (libntfs 9:0:0)
Failed to startup volume : Invalid argument
ERROR(22): Opening '/dev/mapper/isw_cgcihaaba_ARRAY' as NTFS failed: Invalid argument/dev/mapper/isw_cgcihaaba_ARRAY4 (4.64 GB)
NTFS failed: Invalid argument
The device '/dev/mapper/isw_cgcihaaba_ARRAY' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda)? This error might also occur if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
 
Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.[/I]

**[*]/dev/mapper/isw_cgcihaaba_ARRAY1 (47.07 MB)**
This is a single FAT16 partition. Similar to the EISA configuration found in Windows.
 
**[*]/dev/mapper/isw_cgcihaaba_ARRAY3 (460.96 GB)**
This appears to have totally unallocated space.

**[*]/dev/mapper/isw_cgcihaaba_ARRAY4 (4.64 GB)**
This has a single FAT32 partition, looks a lot like the utilities partition found in Windows.
[/LIST]

I assumed that the first array was my hard drive, but I was unable to make any changes to this because of the errors which prevented me from working with the disk in Gparted. Does anyone have any pointers for me on how to get this to work on my computer. I've been looking around for a good few days about this and this is as far as i've got :(

Thanks,

Ian =)

---

### Post by jaymode on 2008-04-15
Well I don't personally have any experience with Ubuntu and dmraid but I figured this could help out:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

