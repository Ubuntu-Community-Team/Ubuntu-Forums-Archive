---
title: "Grub failed to install after upgrade"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by Daremo_06 on 2011-05-07
Ok I started the upgrade and the system is nearly completed but I there is a problem with GRUB.  Most likely since I am dual boot with win7.  So right now I have a pop-up message that says...

[I]GRUB failed to install to the following devices:

/dev/sdb

Do you want to continue anyway? ect ect ect...[/I]



I have not rebooted and completed the installation yet as I figure its probably easier to fix this now while I have the full system up and running vs having to fix it via live cd.

Any BTDT for this?

---

### Post by kansasnoob on 2011-05-07
Please post the output of:

```
sudo parted -l
```

BTW that's a lower case L.

---

### Post by dino99 on 2011-05-07
no worry till you reboot, you still can open synaptic to:

- remove/purge then reinstall grub-pc & grub-common
( be sure that grub1 & menu.lst are no more installed as they conflict with grub2, before installing grub2)

install grub2 on the hdd where ubuntu is installed: is it /dev/sdb ?
on which hdd is win7 ?

---

### Post by oldfred on 2011-05-07
But to be on the safe side you should download and create a Natty liveCD/liveUSB in case you have to make repairs either now or in the future. 

We are finding the grub 1.99 has enough changes that you can only reinstall its grub easily with the same version liveCD.

---

### Post by Daremo_06 on 2011-05-08
> **kansasnoob said:**
> Please post the output of:

```
sudo parted -l
```

BTW that's a lower case L.

Ok here is parted -l

> Model: ATA HDS728080PLA380 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  38.4GB  38.4GB  primary   ext4
 2      38.4GB  76.7GB  38.4GB  primary   ntfs            boot
 3      76.7GB  80.0GB  3307MB  extended
 5      76.7GB  80.0GB  3307MB  logical   linux-swap(v1)


Model: ATA ST32000542AS (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  2000GB  2000GB  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 

I'll also make the rescue cd.

So next step should be what?

---

### Post by kansasnoob on 2011-05-08
From that I can see that /dev/sda is an 80GB "msdos" drive and /dev/sdb is a 2TB "gpt" drive. By appearances the 2TB drive is data only ,eh?

I would think you'd want the 80GB drive set to boot first in the BIOS so there'd be no need to have grub installed to the 2TB drive which is /dev/sdb.

Do you know how to check the hard disc boot priority in BIOS?

To be certain that grub did get installed to the MBR of the 80GB drive you may wish to run:

```
sudo grub-install /dev/sda
```

---

### Post by Daremo_06 on 2011-05-08
> **kansasnoob said:**
> From that I can see that /dev/sda is an 80GB "msdos" drive and /dev/sdb is a 2TB "gpt" drive. By appearances the 2TB drive is data only ,eh?

I would think you'd want the 80GB drive set to boot first in the BIOS so there'd be no need to have grub installed to the 2TB drive which is /dev/sdb.

Do you know how to check the hard disc boot priority in BIOS?

To be certain that grub did get installed to the MBR of the 80GB drive you may wish to run:

```
sudo grub-install /dev/sda
```

Actually your right, the 80GB is my OS drive for both Ubuntu and Win7.  I have partioned it roughly 50/50 for Ubuntu and Win.  I used EasyBCD to setup the dual boot and that works fine.  Should I just run this as previously suggested?

```
-remove/purge then reinstall grub-pc & grub-common
```

---

### Post by Daremo_06 on 2011-05-16
Anyone?

At this point, I think I am just going to fix the grub and then run the windows cd and fix the MBR.

Unless someone points out why that might not work?

---

### Post by oldfred on 2011-05-17
Most of us do not know much about EasyBCD and how it works. Also do not know if some of the changes to Natty change how well EasyBCD works.

Many are like you and like to have all operating systems on one drive and data on another. I prefer to have an operating system on every drive and have versions of Ubuntu on all my drives except my old windows drive.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate most current from drive to drive.

---

