---
title: "HDD combining w/ LVM. Does it stick?"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by benjio123 on 2011-01-19
So here's the thing..

My home server is running Ubuntu 10.10 (Desktop) with a speedy internal HDD (sda) and 2 slow USB drives, a 2TB (sdb) and a 1TB (sdc).

The OS is installed on the internal, while the 2 large drives are combined using LVM and shared on my network, mounted in /home/<user>/Server.

My question is, how (and where) is the configuration of the combined drive stored? Depending on this, is it possible to do a clean install, completely wiping /dev/sda and still keep the LVM drive, and all data intact? And by extension, will it be preserved when I eventually upgrade to Natty?
If I do completely wipe and reinstall, will I only have to add the entry back into /etc/fstab?

I'm a bit of a linux noob and I can't find a whole lot on LVM management in the forums so help is much appreciated.

Here are a few term outputs, just in case:

sudo pvdisplay
[sudo] password for server: 
  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               fileserver
  PV Size               1.82 TiB / not usable 2.56 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              476931
  Free PE               0
  Allocated PE          476931
  PV UUID               bKHV72-BNHg-VIp8-BVNb-2jxy-PmfT-pIFz9h
   
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               fileserver
  PV Size               931.51 GiB / not usable 3.19 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              238466
  Free PE               6
  Allocated PE          238460
  PV UUID               86GdxL-hYUQ-fqzg-jYE4-v0gQ-BkOM-0XQdE4

sudo vgdisplay
  --- Volume group ---
  VG Name               fileserver
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               2.73 TiB
  PE Size               4.00 MiB
  Total PE              715397
  Alloc PE / Size       715391 / 2.73 TiB
  Free  PE / Size       6 / 24.00 MiB
  VG UUID               ZgVVRH-ucW9-9qYY-OOFj-A8T9-rKPf-KZCCbO


cat /etc/fstab
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=9f44f793-054d-4638-8c35-b02a45ae1fda /               ext4    errors=remount-ro 0       1
UUID=a2c64ac3-b60d-4f44-864f-dffe0212f39c none            swap    sw              0       0
/dev/fileserver/LVMdrive /home/benjio/Server reiserfs nodev,nosuid 0 2

---

### Post by srs5694 on 2011-01-19
The LVM configuration is stored in the LVM partitions themselves. Thus, you can completely wipe your OS installation and use the existing LVM in the next installation -- provided of course that your new installation includes the necessary LVM features (they're missing from a standard desktop Ubuntu install, IIRC, but you can add them in later).

---

### Post by benjio123 on 2011-01-19
Thanks for the reply!! 
Just to make sure before I begin..
1. Unplug external drives, reboot, wipe, and reinstall. (probably xubuntu)
2. apt-get install lvm2 dmsetup mdadm reiserfsprogs xfsprogs
3. Reboot, plug in drives, sdb, then sdc
4. Add entry into /etc/fstab, reboot again, done.

Sorry if these are dumb or redundant questions...The data on these drives is important and I have no way to back up 3TB of data elsewhere!!

---

### Post by psusi on 2011-01-19
> **benjio123 said:**
> 
Sorry if these are dumb or redundant questions...The data on these drives is important and I have no way to back up 3TB of data elsewhere!!

If it is important, then you had better find a way to back it up, because it is not a question of if, but when you will loose it.

---

### Post by srs5694 on 2011-01-20
> **benjio123 said:**
> Thanks for the reply!! 
Just to make sure before I begin..
1. Unplug external drives, reboot, wipe, and reinstall. (probably xubuntu)
2. apt-get install lvm2 dmsetup mdadm reiserfsprogs xfsprogs
3. Reboot, plug in drives, sdb, then sdc
4. Add entry into /etc/fstab, reboot again, done.

Basically, yes, although I'd plug in both external drives when the computer is powered off after installing the necessary LVM packages. Also, the reboot in your step #4 is unnecessary; you can just type "sudo mount -a" after changing your /etc/fstab file.

> Sorry if these are dumb or redundant questions...The data on these drives is important and I have no way to back up 3TB of data elsewhere!!

I agree with psusi's comment on this point. If the files on these drives are important, back them up!

---

