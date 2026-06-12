---
title: "Cannot install grub with my current Raid 0 setup + dualboot."
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by f1zz1ec0ke on 2012-07-28
Hi,
I'm sitting on the live usb at the moment after installing Ubuntu 12.04 64 bit.
The problem I am having is that i cannot install grub, i have 3 hard drives total in my pc, 2 of them are in raid.
I have windows 7 installed on the raid, and partitioned the raid in windows so that there was 58gb of free space.
I know that im supposed to put grub on /dev/sda but i cant, in gparted /dev/sda and /dev/sdb are shown as unallocated.
 /dev/sdc is my 1tb hard drive.
In gparted my raid appears to be listed as /dev/mapper/pdc_cedggeecc
 /dev/mapper/pdc_cedggeecc1/2 are windows system reserved and i guess C: drive.
 /dev/mapper/pdc_cedggeecc5 is where Ubuntu is installed,  /dev/mapper/pdc_cedggeecc6 is where i put the linux swap.
I would prefer not to use wubi.
Thanks in advance.

Edit: So im still trying to figure this out, I've seen on many forums that people need to fdisk -l so that you can get more info, I have done the same:

>  ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c581056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   350064639   174928896    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xefee7072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT

Disk /dev/mapper/pdc_cedggeecc: 238.0 GB, 237999882240 bytes
255 heads, 63 sectors/track, 28935 cylinders, total 464843520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x3c581056

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_cedggeecc1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/mapper/pdc_cedggeecc2          206848   350064639   174928896    7  HPFS/NTFS/exFAT
/dev/mapper/pdc_cedggeecc3       350064894   464841983    57388545    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc5       350064896   447720959    48828032   83  Linux
/dev/mapper/pdc_cedggeecc6       447721216   464841983     8560384   82  Linux swap / Solaris

Disk /dev/sdd: 3990 MB, 3990294528 bytes
123 heads, 62 sectors/track, 1021 cylinders, total 7793544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdd2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sdd3   ?           0           0           0   6f  Unknown
/dev/sdd4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

Disk /dev/mapper/pdc_cedggeecc1: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders, total 204800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_cedggeecc1p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc1p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc1p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc1p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/pdc_cedggeecc2: 179.1 GB, 179127189504 bytes
255 heads, 63 sectors/track, 21777 cylinders, total 349857792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_cedggeecc2p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc2p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc2p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/pdc_cedggeecc2p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/pdc_cedggeecc3: 58.8 GB, 58765870080 bytes
255 heads, 63 sectors/track, 7144 cylinders, total 114777090 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 1024 bytes
Disk identifier: 0x50a857f4

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_cedggeecc3p1               2    97656065    48828032   83  Linux
/dev/mapper/pdc_cedggeecc3p2        97656066   114777089     8560512    5  Extended
/dev/mapper/pdc_cedggeecc3p5        97656322   114777089     8560384   82  Linux swap / Solaris

Disk /dev/mapper/pdc_cedggeecc5: 50.0 GB, 49999904768 bytes
255 heads, 63 sectors/track, 6078 cylinders, total 97656064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_cedggeecc5 doesn't contain a valid partition table

Disk /dev/mapper/pdc_cedggeecc6: 8765 MB, 8765833216 bytes
255 heads, 63 sectors/track, 1065 cylinders, total 17120768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/pdc_cedggeecc6 doesn't contain a valid partition table 

---

### Post by oldfred on 2012-07-28
I do not know if Boot-Repair works with RAID or not. Is sda not part of RAID? I really do not know RAID, but normally you install the boot loader to the root of RAID not a drive, but if you have a separate drive not part of the RAID, I think you can install there. The liveCD does not by default have the RAID drivers which you need for it to work correctly.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.
sudo apt-get install lvm2
sudo apt-get install mdadm
sudo apt-get install gawk
sudo apt-get install xz-utils
# unlzma is equivalent to xz --format=lzma --decompress.

---

### Post by f1zz1ec0ke on 2012-07-28
Thanks, boot-repair fixed my mbr, Now i can boot back into windows, I will try again tomorrow, thanks for the help dude

---

### Post by darkod on 2012-07-28
This probably happened if you used the standard live cd to install. The recommendation is to use the alternate cd for raid installs, exactly for this reason. The live cd will install the system but it often fails to install grub2.

It doesn't go to sda or sdb, it goes to the MBR of the raid device, the /dev/mapper/pdc_blahblah. Note that the MBR of the array DOES NOT have a number in it, the same like /dev/sda has no number in it. If there is a number, that means a partition.

You should be able to add grub2 from live mode. First mount the root partition, partition #5 on the array, and then install grub2 to the MBR of the array (without any number, as we said).

```
sudo mount /dev/mapper/pdc_blahblah[COLOR=Red]5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/pdc_blahblah
```That should sort it out in most cases.

---

### Post by f1zz1ec0ke on 2012-07-29
I tried that but i ended up with a grub page with no options, i used boot repair again and now im able to boot into ubuntu from grub but windows is nowhere to be found?

---

### Post by darkod on 2012-07-29
Looks like windows is not getting detected. Try first to run in ubuntu:
sudo update-grub

If that doesn't detect it, run boot-repair again but only to create the bootinfo results and post the link it gives you.

---

