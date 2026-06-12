---
title: "Two partitions with the same stuff"
date: 2012-09-13
forum: Installation &amp; Upgrades
---

### Post by SimpsonTruckDriver on 2012-09-13
When I upgraded to 12.04 LTS, I set one partition as "33Gb File System", where I had 12.04 LTS installed.  Accordingly, it has 31Gb free. But, when I try to install the updates, I get this message:

The upgrade needs a total of 406 M free space on disk '/'. Please free at least an additional 59.4 M of disk space on '/'

It looks like "/" has all the same files as "33 Gb File System". I want to clean out everything in "/", but how can I do it and make sure the system does not crash as a result? Or make sure that, if '/" is where 12.04 boots out of, that I can use the "33Gb File System as the Linux to use. This is a dual boot with Windows Vista, and the boot menu only shows Ubuntu and Windows (and Dell's Media Direct - never use).

TS

---

### Post by darkod on 2012-09-13
Looks like it's not installed where you think it is. If you have 31GB free, no way you can receive that message about not enough space.

Boot your ubuntu and post the output of:
```
df -h
```

Additionally, you can add the output of:
```
sudo parted -l
```

---

### Post by SimpsonTruckDriver on 2012-09-13
simpsontruckdriver@Laptop:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8       4.2G  3.4G  618M  85% /
udev            999M  4.0K  999M   1% /dev
tmpfs           403M  876K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  376K 1006M   1% /run/shm
/dev/sdb1       7.6G  5.0G  2.7G  66% /media/KINGSTON

simpsontruckdriver@Laptop:~$ sudo parted -l
Model: ATA SAMSUNG HM120JI (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  57.6MB  57.5MB  primary   fat16           diag
 2      57.7MB  10.8GB  10.7GB  primary   ntfs
 3      10.8GB  75.0GB  64.2GB  primary   ntfs            boot
 4      75.0GB  120GB   45.1GB  extended                  lba
 6      75.0GB  80.0GB  5000MB  logical  linux-swap(v1)
 7      80.0GB  113GB   33.5GB  logical   ext4
 8      113GB   118GB   4448MB  logical   ext4
 5      118GB   120GB   2146MB  logical   fat32

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  8128MB  8123MB  primary  fat32        boot, lba

Boot menu: both versions of Ubuntu 12.04, Memory Tests, Windows Vista, and Dell Media Direct.

TS

---

### Post by darkod on 2012-09-13
As you can see, your root partition is sda8, not sda7.

sda8 is only 4.2GiB big, and already 85% full. So, there is only 618MiB left free.

---

### Post by SimpsonTruckDriver on 2012-09-13
I see how I can change the "/" mount from sda8 to sda7 using Disk utility. My concern is, how do I move GRUB to sda7 (if not there already)? I don't want to set it to sda7, and not have an MBR/GRUB there.

TS

---

### Post by darkod on 2012-09-14
Hmm, I've never tried copying the root partition. It might work, it might not.

I guess it's best to do it from live mode, because I don't think it can copy root while running from it. There will be open system files.

From live mode, you would need to create two temporary mount points, and copy the content keeping permissions. Grub2 on the MBR will also need to be reinstalled to point to sda7 instead of sda8.

If sda7 is now empty, to do the copy from live mode:
```
sudo mkdir /mnt/oldroot
sudo mkdir /mnt/newroot
sudo mount /dev/sda8 /mnt/oldroot
sudo mount /dev/sda7 /mnt/newroot
cd /mnt/oldroot
sudo cp -ax * /mnt/newroot
```

You will also need to change the UUID value of the root in /etc/fstab. While everything is still mounted after the copy, first check the UUID string for sda7 with:
sudo blkid

Write it down. Then open with the nano editor:
sudo nano /mnt/newroot/etc/fstab

and replace the UUID of sda8 with the UUID of sda7. Press Ctrl + O to save the file, Ctrl + X to exit nano.

After that reboot, when the grub2 boot menu shows press 'c' for command line. Try to boot executing these commands one by one:
```
insmod part_msdos
insmod ext2
set root=(hd0,7)
linux vmlinuz root=/dev/sda7
initrd initrd.img
boot
```If that didn't work, there are other ways to boot it, don't panic and do something you might regret later. :)

---

### Post by SimpsonTruckDriver on 2012-09-14
Just thinking along the lines of Windows/DOS, is it possible to delete sda7, and resize sda8, keeping the UUIDs (so it will still boot into Ubuntu)? Can it be done in Disk Utility  or does it have to be done with another program like Gparted? I'm one who likes the most efficient and easiest route with the least amount of data damage/loss.

TS

---

### Post by darkod on 2012-09-14
Yeah, it could work since the partitions are next to each other. But you will have to boot into live mode for that, you can't expand root while mounted.
You can use Gparted in the live mode. Delete sda7 first, and expand sda8 to the left.

Note that resize of partitions can go wrong sometimes, so it's not like failsafe. It's always best to have a backup before you start.

Also, it might disrupt grub2 sometimes, if it moves the boot files. But this should be easily solved by grub2 reinstall to the MBR, it will pick up the new location during the process.

It's up to you. With the copy to another partition, you will still have sda8 untouched to go back to. But I can't say for 100% whether that will work too.

---

### Post by SimpsonTruckDriver on 2012-09-29
I deleted the rarely used partition, resized (and renamed) the new one, reinstalled GRUB, and now everything is ok. I haven't found any damaged data, but it was backed up just in case.

TS

---

