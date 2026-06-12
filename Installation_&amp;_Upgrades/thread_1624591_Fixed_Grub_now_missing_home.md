---
title: "Fixed Grub now missing /home"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Anomally on 2010-11-17
I had Ubuntu installed.  I partitioned my drive and installed Windows 7.  After that grub was missing. Following the directions I was able to fix that problem.

Now when Ubunutu 10.10 loads up it says failed to find /home wait or press S/M to skip or fix.

I went ahead and hit M... I'm not sure how to fix the /home problem. I know /home is on it's own partition, but I'm not sure how to fix it. Thanks.

---

### Post by mikewhatever on 2010-11-18
Run **sudo fdisk -l** from the live cd/usb just to make sure the home partition is still there. If it is, its UUID (id number) could have changed, especially if you resized it.
If you need help with that, post th outputs of the following from the live cd:

sudo fdisk -l

sudo blkid

the contents of fstab

---

### Post by Anomally on 2010-11-18
> **mikewhatever said:**
> Run **sudo fdisk -l** from the live cd/usb just to make sure the home partition is still there. If it is, its UUID (id number) could have changed, especially if you resized it.
If you need help with that, post th outputs of the following from the live cd:

sudo fdisk -l

sudo blkid

the contents of fstab

The thing is ubuntu loads, but it says "Can't find disk /home. Wait or push m to manually fix it." I waited for about 30 minutes before I hit M. It takes you straight to the terminal. I pushed 'startx' to load the gui, but it's not 100% functional

As for FDISK -l:

[sudo fdisk -l]
*********************************************Disk /dev/sda: 4016 MB, 4016045568 bytes
65 heads, 36 sectors/track, 3352 cylinders
Units = cylinders of 2340 * 512 = 1198080 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b75f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3353     3921875    b  W95 FAT32

Disk /dev/sdd: 507 MB, 507379712 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df239

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         983      495313+   6  FAT16

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0dbc0dbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1           1         992+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdf2   *           1       48053   385984698+   7  HPFS/NTFS
/dev/sdf3           48054       60802   102399035    5  Extended
/dev/sdf5           48054       48661     4881408   82  Linux swap / Solaris
/dev/sdf6           48661       60802    97516602   83  Linux 
***********************************************************

[sudo blkid]

/dev/sda1: LABEL="^YM-^FM-/lM-BM-^[^ZM-^MM-fM-yQ" UUID="F0AB-1875" TYPE="vfat"
/dev/sdd1: SEC_TYPE="msdos" UUID="3534-3237" TYPE="vfat"
/dev/sdf2: LABEL="DRIVE_C" UUID="56F0F23BF0F22143" TYPE="ntfs"
/dev/sdf5: UUID="0e991406-759d-43b1-a6e9-c9945e86b1b2" TYPE="swap"
/dev/sdf6: UUID="3ea3e6d7-e7af-4a2c-8ba1-9356f954f8c2" TYPE="ext4"
root@Anomally:~#

*******************************************************

---

### Post by tommcd on 2010-11-18
```

Device Boot Start End Blocks Id System
/dev/sdf1 1 1 992+ 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sdf2 * 1 48053 385984698+ 7 HPFS/NTFS
/dev/sdf3 48054 60802 102399035 5 Extended
/dev/sdf5 48054 48661 4881408 82 Linux swap / Solaris
/dev/sdf6 48661 60802 97516602 83 Linux 

```
=======================================================
This indicates that you only have 1 linux partition, which is /dev/sdf6. You also have a swap partition.
Since your posts provide almost no useful info, how did you install Ubuntu 10.10??? It looks like you have obliterated the /home partition that you allegedly used to have.

---

### Post by Anomally on 2010-11-18
I had Ubuntu 10.10 installed on my system... I had partitioned one part for NTFS, another for SWAP, a small one for /home(On Sda3) and then I did sda6 for Ubuntu. I then installed windows 7... Windows 7's MBR messed up GRUB2, so I went to the tutorial on how to fix the Grub fix.. I used the CD for a live boot of UBUNTU and reinstalled the grub from the terminal. 

After that I am now able to go to the boot menu and select linux or windows, but when I go to load Ubuntu it says /home drive can not be found wait or press M for manual repair (which takes me to the Terminal)

---

### Post by kansasnoob on 2010-11-18
It sounds like grub is just trying to boot the wrong device, that is the device designation may have changed when you installed Windows, so we'll try to update grub.

So boot the live CD again and then copy-n-paste the following commands:

```
sudo mount /dev/sdf6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo chroot /mnt
```

```
update-grub
```

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot and see if you can now boot your installed Ubuntu from the grub menu. If not we'll need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oldfred on 2010-11-18
Did you plug in a multi card reader with a flash card? Your sda is a 4GB device and your hard drive has become sdf? That can confuse grub if there is a large gap between drives even though it searches by UUID, if often stops looking if no drives are found in order.

---

### Post by mcduck on 2010-11-18
> **tommcd said:**
> ```

Device Boot Start End Blocks Id System
/dev/sdf1 1 1 992+ 83 Linux
Partition 1 does not end on cylinder boundary.
/dev/sdf2 * 1 48053 385984698+ 7 HPFS/NTFS
/dev/sdf3 48054 60802 102399035 5 Extended
/dev/sdf5 48054 48661 4881408 82 Linux swap / Solaris
/dev/sdf6 48661 60802 97516602 83 Linux 

```
=======================================================
This indicates that you only have 1 linux partition, which is /dev/sdf6. You also have a swap partition.
Since your posts provide almost no useful info, how did you install Ubuntu 10.10??? It looks like you have obliterated the /home partition that you allegedly used to have.

Actually there is (see sdf1), but the partitions are definitely messed up, sdf1 and sdf2 are overlapping, both start at block 1.

---

