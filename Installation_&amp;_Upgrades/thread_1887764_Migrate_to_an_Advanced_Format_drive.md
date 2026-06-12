---
title: "Migrate to an Advanced Format drive"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by charlesshoults on 2011-11-27
I have an Ubuntu Server installation running on an older 400GB Western Digital 3.5" drive and want to change to a notebook drive.  I've done this once before, but didn't run into these particular problems last time.  On my other server, I did later add two 2TB drives that were WD EARS drives so I had to configure them for 4k at that time.  

When I set up this box, I used LVM.  Information about the existing setup is shown here:
```
--- Volume group ---
  VG Name               Griffin
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               372.37 GiB
  PE Size               4.00 MiB
  Total PE              95327
  Alloc PE / Size       95318 / 372.34 GiB
  Free  PE / Size       9 / 36.00 MiB
  VG UUID               vC57mz-g77w-6bVG-T5iw-dWQ9-ca20-JxvwBU
```

```
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8cdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   780919649   390459793+  8e  Linux LVM
/dev/sda2       780919650   781417664      249007+   5  Extended
/dev/sda5       780919713   781417664      248976   83  Linux
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Griffin-root
                      359G  2.8G  338G   1% /
none                  1.8G  320K  1.8G   1% /dev
none                  1.9G   24K  1.9G   1% /dev/shm
none                  1.9G  332K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda5             228M   38M  179M  18% /boot
192.168.0.150:        4.3T  3.4T  703G  84% /home/xbmc/Ryoken
```

So, I picked up a Black Friday 640GB Seagate drive that was in a GoFlex enclosure, $54.00, not thinking that it might be a 4k drive, which it is.  When I first went through fdisk on the notebook drive, it told me that the first partition did not begin on a physical sector boundary, which was my first clue that there was a problem.  After some monkeying around with it, I have the following:

```
Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x43f5b54a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              64   156282965    78141451   8e  Linux LVM
```

How do I go about migrating data from my old drive to my new one?  The first thing I read about was using a Live CD and DD to duplicate the drive, but I don't know if the advanced format drive will cause problems or not.  I thought about adding the new drive to the volume group and then the Live CD to migrate, but I can't unlock the original drive in order to add the new one, most likely because root is on the drive.  The third option I can think of is to do a new install on the new drive, then rsync everything over, but I don't know how to do a clean install on a 4k advanced format drive...


Help!!??  :(

---

### Post by MAFoElffen on 2011-11-28
> **charlesshoults said:**
> I have an Ubuntu Server installation running on an older 400GB Western Digital 3.5" drive and want to change to a notebook drive.  I've done this once before, but didn't run into these particular problems last time.  On my other server, I did later add two 2TB drives that were WD EARS drives so I had to configure them for 4k at that time.  

When I set up this box, I used LVM.  Information about the existing setup is shown here:
```
--- Volume group ---
  VG Name               Griffin
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               372.37 GiB
  PE Size               4.00 MiB
  Total PE              95327
  Alloc PE / Size       95318 / 372.34 GiB
  Free  PE / Size       9 / 36.00 MiB
  VG UUID               vC57mz-g77w-6bVG-T5iw-dWQ9-ca20-JxvwBU
``````
Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8cdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   780919649   390459793+  8e  Linux LVM
/dev/sda2       780919650   781417664      249007+   5  Extended
/dev/sda5       780919713   781417664      248976   83  Linux
``````
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Griffin-root
                      359G  2.8G  338G   1% /
none                  1.8G  320K  1.8G   1% /dev
none                  1.9G   24K  1.9G   1% /dev/shm
none                  1.9G  332K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda5             228M   38M  179M  18% /boot
192.168.0.150:        4.3T  3.4T  703G  84% /home/xbmc/Ryoken
```So, I picked up a Black Friday 640GB Seagate drive that was in a GoFlex enclosure, $54.00, not thinking that it might be a 4k drive, which it is.  When I first went through fdisk on the notebook drive, it told me that the first partition did not begin on a physical sector boundary, which was my first clue that there was a problem.  After some monkeying around with it, I have the following:

```
Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x43f5b54a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              64   156282965    78141451   8e  Linux LVM
```How do I go about migrating data from my old drive to my new one?  The first thing I read about was using a Live CD and DD to duplicate the drive, but I don't know if the advanced format drive will cause problems or not.  I thought about adding the new drive to the volume group and then the Live CD to migrate, but I can't unlock the original drive in order to add the new one, most likely because root is on the drive.  The third option I can think of is to do a new install on the new drive, then rsync everything over, but I don't know how to do a clean install on a 4k advanced format drive...


Help!!??  :(
Boot from a LiveCD, then follow the instruction in this link starting at "Copy." Where it says VMWare, just think LiveCD:
[http://mybookworld.wikidot.com/upgrade-500gb-blue-ring-to-1-5tb-wd15ears](http://mybookworld.wikidot.com/upgrade-500gb-blue-ring-to-1-5tb-wd15ears)

---

