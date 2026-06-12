---
title: "installing another linux distro with ubuntu already on 2nd drive"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by aBitLater on 2008-02-20
Hello,

I'm looking for advice for partitioning the 1st drive on my computer, which is currently WinXP - for opensuse 10.3 installation.  (I'm going "Windows-Free"!!!)

On the 2nd drive, I currently have Ubuntu 7.10, and I will keep this OS on the 2nd drive for a while, then I will want to remove it and use OpenSuse only.

I like to learn about programming, so I will have all kinds of development software on my system.  And I record TV to my disk (a few shows / week) I will also have a /spare partition for testing other OS's.

Below, I show you fdisk -l output, then I show you my current properties for folders on my Ubuntu drive (has everything I want for the moment), then I show you what I think will be a good setup, and ask for your opinion. 

(Also, many thanks to Scorp123 who gave me some help in a different situation - for my laptop - at [http://ubuntuforums.org/showthread.php?t=684984]("http://ubuntuforums.org/showthread.php?t=684984"))

===============================================================

Here's the current config of my 2 disks.  (Note that "fdisk -l" reports 160GB and 80GB, but Ubuntu sees these as 149 GB and 74 GB for some reason, so not sure I will have full size to use on sda1 for OpenSuse) 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd635d635

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
-----------------------------------------------------------------
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b7c7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap
```
------------------------------------------------------------------- 
===================================================================

My current Ubuntu 2nd drive (sdb) has everything on root, but these are the size of the directories:
```
/boot     =   33 MB
/var      =    1 GB
/usr      =    6 GB
/home     =   26 GB
/tmp      =    1 GB
/         =    4 GB
```
 (my math for calculating root size, subtract directories above from total used space of 37GB, so I think '/' is a little under 4 GB)

===================================================================

So here is what I'm thinking for OPENSUSE (assuming I only get 149 GB from my 160 GB Drive):

```
/boot     =  150 MB
/         =   10 GB
/tmp      =    2 GB
/(swap)   =    2 GB (= RAM, and this ** is on sdb5 already***!!)
/var      =    4 GB 
/usr      =   10 GB
/home     =   71 GB
/spare    =   50 GB
```

So do these look like good ideas?  And, which goes on first primary partition, 2nd partition, 3rd, etc?

If I understand correctly, I can have 3 primary partitions, then the 4 will have to be an extended partition from which I can make other partitions. (?)  

When I am ready to delete Ubuntu, in the future, should I leave swap on the 2nd drive?  Or should I plan now to have it on the first drive with opensuse immediately?  I think I will want to put /tmp on the 2nd drive also, as well as swap, but only at a later time, for now I'll have it on the 1st drive with Opensuse.. good idea ???>

Thank you for your time and consideration.

-- 
Regards,
Brian

---

### Post by Existentialist on 2008-02-21
The partition order shouldn't be too important.  It used to be that BIOS could not read beyond the 1024th cylinder (about 8.5GB) so the boot partition had to be within this space, but on any new machine this wont be an issue.

You are correct on the partitions, you can have, at most, 4 primary partitions on a hard drive.  One of these can be an extended partition, which lets you create whats called logical partitions within the extended partition.

For the swap, I would recommend sharing it between both distros to save space.  Ideally, the swap partition would be on a separate drive from the OS, as this is the fastest when swap must be used.  This shouldn't be a big deal on a machine with 2GB, as you have plenty of RAM for common tasks and shouldn't access swap very often.  But you can plan ahead and keep it on the second drive so that any other distro you install in your spare space will be able to use the swap on the second drive also.

---

