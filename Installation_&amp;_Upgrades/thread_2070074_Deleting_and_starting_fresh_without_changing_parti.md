---
title: "Deleting and starting fresh without changing partitions?"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by Roger-H on 2012-10-11
So my system is set up like this:

/dev/sda1/ Windows XP Partition
/dev/sda2/ FAT32 Compaq Recovery Partition
/dev/sda3/ Container for Logical Partitions sda5 and sda6
/dev/sda4/ (can't find this one in Disk Utility)
/dev/sda5/ Linux file system running Lubuntu 12.04
/dev/sda6/ Linux swap space

Is there a way to just delete sda5 and sda6, boot with a Ubuntu 12.04 USB key and do a completely clean install of it to sda3? I'd like to check before I start deleting things.

---

### Post by Wim Sturkenboom on 2012-10-12
Can you post the output of _df -h_?
```

wim@wim-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              24G  2.6G   21G  12% /
none                  1.9G  284K  1.9G   1% /dev
none                  1.9G  200K  1.9G   1% /dev/shm
none                  1.9G   92K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda5             119G  111G  2.5G  98% /home

```

And of _sudo fdisk -l_ (that's lowercase L at the end)
```

wim@wim-desktop:~$ sudo fdisk -l
[sudo] password for wim: 

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a0bfe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3162    25390080   83  Linux
/dev/sda2            3162        3680     4160512   82  Linux swap / Solaris
/dev/sda3            3680       19453   126696449    5  Extended
/dev/sda5            3680       19453   126696448   83  Linux

```

> 
Is there a way to just delete sda5 and sda6, boot with a Ubuntu 12.04 USB key and do a completely clean install of it to sda3?

As you can't install in an extended partition (sda3), you need to delete sda4, sda5 and sda6 and sda3. And next allow Ubuntu to do its thing in the freespace. It would however not be my approach as you more than likely will be limited to 4 primary partitions and therefore either no swap or no partition wor the home directories. Rather have the extended partition and install ubuntu in logical partitions (more or less as it's now).

---

### Post by darkod on 2012-10-12
1. There is no need to delete sda4 what ever that is, only sda5, sda6 and sda3. That is, if you decide deleting at all.

2. The auto install process of ubuntu installs in logical partitions, so it's not tru that if you have two exisitng primary partitions ubuntu will install with two more and reach the limit of primary partitions. It will install in logical partition leaving the posibility to have one more primary later.

If you are happy with your partition sizes, you don't have to delete anything. Just use the manual method to install (Something Else). It will list existing partitions.

Select sda5, click the Change button below. Change the Use As to ext4, tick the format box, select mount point /.
Then select sda6 and in Use As put swap area. There is no mount point for swap and no format tick box.

Below the partition list, for the destination of the bootloder use /dev/sda (without any number in it).

That's it. That is how you install manually with more control of the process.

If you are not happy with the current partition sizes then you do need to delete them and create new ones but that would also involve planning of the other partition if you want to use more space for ubuntu this time. You would need to shrink something else so that you have more unallocated space.

---

### Post by Roger-H on 2012-10-12
Here is df -h

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        29G  8.5G   19G  32% /
udev            965M  4.0K  965M   1% /dev
tmpfs           389M  856K  388M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            972M  264K  972M   1% /run/shm
```

Here is sudo fdisk -l

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    80448622    40224280    7  HPFS/NTFS/exFAT
/dev/sda2       144160768   156299263     6069248   12  Compaq diagnostics
/dev/sda3        80449534   144160767    31855617    5  Extended
/dev/sda5        80449536   140111871    29831168   83  Linux
/dev/sda6       140113920   144160767     2023424   82  Linux swap / Solaris

Partition table entries are not in disk order
```

So my understanding is that I can do the following:

1) In Lubuntu, run Disk Manager and delete sda5 and sda6.
2) Reboot with a Ubuntu USB key and during the install, process, choose to put it on sda3.

I don't have to do anything to fix the master boot record? Will it reinstall grub?

---

### Post by darkod on 2012-10-12
Read my previous post.

---

### Post by Wim Sturkenboom on 2012-10-12
> **Roger-H said:**
> 
So my understanding is that I can do the following:

1) In Lubuntu, run Disk Manager and delete sda5 and sda6.
2) Reboot with a Ubuntu USB key and during the install, process, choose to put it on sda3.
If Lubuntu is your current OS, step 1 will not work as those partitions are in use (you can still get around the swap but not around root partition). So you need to use a liveCD to do so ;)

Go for darkod's advise, it will give you a clean install.

---

### Post by Roger-H on 2012-10-12
Ah, okay, I don't think I followed what was being recommended but after rereading it I understand. I'll let you know how it goes.

---

### Post by jbowen7 on 2012-10-12
For a clean install of Ubuntu, and the retaining your Windows partitions, all you need to do is:

1) Boot a live-cd
2) when you get to the partitioning page, select the manual option.
3) Select partition 4 and make the mount point "/" && set the bootable flag on.
4) for /dev/sda5 , select it, then find in the mount point drop down something like, do no mount partition use for swap...

That'll do you fine.

---

### Post by Roger-H on 2012-10-12
I used a USB key, but that worked. Thanks, everyone.

---

