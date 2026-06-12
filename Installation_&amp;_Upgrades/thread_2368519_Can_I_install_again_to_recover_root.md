---
title: "Can I install again to recover root ??"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by oygle on 2017-08-11
Have had a problem for several days now, see [https://ubuntuforums.org/showthread.php?t=2368270](https://ubuntuforums.org/showthread.php?t=2368270)

I can boot okay to a Live USB and browse the data hard drives. Can I install again to recover root, and **NOT** overwrite the data ??

HDD#1 - Root is one partition, 20 Gb, then data is another partition about 450 Gb

HDD#2 - All data - 250 Gb

---

### Post by vocx on 2017-08-11
> **oygle said:**
> Have had a problem for several days now, see [https://ubuntuforums.org/showthread.php?t=2368270](https://ubuntuforums.org/showthread.php?t=2368270)

I can boot okay to a Live USB and browse the data hard drives. Can I install again to recover root, and **NOT** overwrite the data ??

HDD#1 - Root is one partition, 20 Gb, then data is another partition about 450 Gb

HDD#2 - All data - 250 Gb

Reinstalling will erase the root partition, but does not need to touch the data partitions. The installer will only overwrite what you tell it to overwrite, nothing more.

You can check the partition numbers with
```

sudo fdisk -l

```

Say, if your system is
```

/dev/sda1      /           20 GB
/dev/sda2      /data      450 GB

/dev/sdb1      /data2     250 GB

```

When you reinstall, tell the installer to reformat "/dev/sda1" only. Do not reformat "sda2" nor "sdb1". Be very careful and double check before proceeding.

---

### Post by oygle on 2017-08-11
Thanks for your reply. I would have liked to be able to backup to an external first, but not sure how to manually mount the external drive. It has usb/sata , but the usb will take a very long time (about 500 Gb to backup). Here is the /etc/fstab details ...

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda1 during installation
UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca / ext4 errors=remount-ro 0 1
# /home was on /dev/sda3 during installation
UUID=4925dcbd-b2a1-4db6-adc0-69a9f05ad473 /home ext4 defaults 0 2
# swap was on /dev/sda2 during installation
UUID=82e48eb2-0c33-4696-9154-d921da42bbd2 none swap sw 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
# / Kubuntu2 - secondary HDD - 250 Gb
UUID=79731916-952b-4d88-b6d4-40e81b15731d /media/kubuntu2 ext4 noauto,errors=remount-ro 0 1
# / external hard drive - 500Gb
UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk ext4 noauto,errors=remount-ro 0 1

```

I did start going down this path - [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) , the 'Update Failure' section and was able to do those commands, but it started failing on missing files. So, I copy one file, it wants another. That will take too long.

So if I can back up to the external drive first, I can wipe the whole disk and do a fresh install.

edit: Here is some extra info from the bootinfo script ..

```

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________ ___________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sda1 * 63 41,945,714 41,945,652 83 Linux
/dev/sda2 41,945,715 50,347,709 8,401,995 82 Linux swap / Solaris
/dev/sda3 50,347,710 976,768,064 926,420,355 83 Linux


Drive: sdb __________________________________________________ ___________________
Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdb1 * 63 488,392,064 488,392,002 83 Linux


Drive: sdc __________________________________________________ ___________________
Disk /dev/sdc: 3.7 GiB, 4005560320 bytes, 7823360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdc1 * 0 3,002,879 3,002,880 0 Empty
/dev/sdc2 2,982,352 2,987,087 4,736 ef EFI (FAT-12/16/32)

/dev/sdc1 overlaps with /dev/sdc2

GUID Partition Table detected, but does not seem to be used.

Partition Start Sector End Sector # of Sectors System
/dev/sdc1 0 3,002,823 3,002,824 Data partition (Windows/Linux)
/dev/sdc2 2,982,352 2,987,087 4,736 Data partition (Windows/Linux)

Drive: sdd __________________________________________________ ___________________
Disk /dev/sdd: 29 GiB, 31104958464 bytes, 60751872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition Boot Start Sector End Sector # of Sectors Id System

/dev/sdd1 21,920 60,751,871 60,729,952 c W95 FAT32 (LBA)


"blkid" output: __________________________________________________ ______________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ext4
/dev/sda2 82e48eb2-0c33-4696-9154-d921da42bbd2 swap
/dev/sda3 4925dcbd-b2a1-4db6-adc0-69a9f05ad473 ext4
/dev/sdb1 79731916-952b-4d88-b6d4-40e81b15731d ext4 kubuntu2
/dev/sdc1 2016-07-19-21-08-55-00 iso9660 Kubuntu 16.04.1 LTS amd64
/dev/sdc2 0F7B-9366 vfat
/dev/sdd1 4E49-ECAD vfat

================================ Mount points: =================================

Device Mount_Point Type Options

/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sda1 /media/kubuntu/855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udi sks2)
/dev/sda3 /media/kubuntu/4925dcbd-b2a1-4db6-adc0-69a9f05ad473 ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udi sks2)
/dev/sdc /cdrom iso9660 (ro,noatime)
/dev/sdd1 /media/kubuntu/4E49-ECAD vfat (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=00 22,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remou nt-ro,uhelper=udisks2)


```

---

### Post by vocx on 2017-08-11
When posting code, please use CODE tags, not QUOTE tags. The buttons are next to each other.

> **oygle said:**
> 
I did start going down this path - [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery) , the 'Update Failure' section and was able to do those commands, but it started failing on missing files. So, I copy one file, it wants another. That will take too long.

So if I can back up to the external drive first, I can wipe the whole disk and do a fresh install.

edit: Here is some extra info from the bootinfo script ..
You have to explain more clearly where your problem is exactly.

"Started failing on missing files" where? What was the last command you ran? According to that section that you are linking, the last commands are a couple of
```

sudo apt update
sudo apt upgrade

```
Was it reporting missing files then? What is the terminal output of this part?

If you only want to backup your files, it is simple.
1. Run Live USB session
2. Mount your partitions as you see necessary. As the wiki page that you linked says, "sudo mount /dev/sda3 /mnt/home"
3. Connect the USB drive. It should be automatically mounted in one directory, for example, "/media/USBdrive"
4. Move the files from the mounted partition to the USB drive.
```

rsync -avz /mnt/home /media/USBdrive

```

It will take a long time for sure if you have to transfer the entire 450 GB of the original "/home" partition, but this is normal.

According to the output you post, you have several disks
```

sda  internal disk with 450 GB
sdb  external disk with 250 GB
sdc  internal disk with 4 GB. Is this a DVD?
sdd  internal disk with 30 GB. Is this a USB thumb drive?

```

So, what exactly do you want to back up? I assume you only want to backup your "/home" which seems to be in "sda3".

You don't need to backup "sda1". That is the root file system on top of which you will reinstall.
You don't need to backup "sda2". This is the swap partition.
You don't need to backup "sdb1". This is a completely different drive. You can disconnect it from your system if you want to be sure nothing will be erased there when you reinstall.
And of course, you don't need to back up "sdc1" being the Live DVD. And neither do you need to back up "sdd1". I'm not sure what this is.

> **oygle said:**
> Thanks for your reply. I would have liked to be able to backup to an external first, but not sure how to manually mount the external drive. It has usb/sata , but the usb will take a very long time (about 500 Gb to backup). Here is the /etc/fstab details ...

Now, according to your fstab, you have another 500 GB drive, that is not shown in the "bootinfo" script.

You are mounting it with a line
```

UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk ext4 noauto,errors=remount-ro 0 1

```
What is the problem with this? It looks fine to me. As long as the UUID is correct it should mount. Just make sure the folder where you want to mount it exists, and also mount it actually.
```

sudo mkdir -p /media/externaldisk
sudo mount /media/externaldisk

```

4. Then you can copy your previous "/home" to this drive.
```

rsync -avz /mnt/home /media/externaldisk

```

---

### Post by oygle on 2017-08-11
Thanks for your reply. I use Beyond Compare for copying, as it can also do a binary compare and the interface is 2 windows, source and destination.

Am now able to backup to that external drive, but it is going to take another 5 hours. It is connected via usb 2.0 though. The drive does have an esata connection and that will be much quicker. Can you please advise what command I need to mount the external drive ?

This is the line in /etc/fstab ..

```

UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk ext4 noauto,errors=remount-ro 0 1

```

---

### Post by vocx on 2017-08-11
> **oygle said:**
> Thanks for your reply. I use Beyond Compare for copying, as it can also do a binary compare and the interface is 2 windows, source and destination.

Am now able to backup to that external drive, but it is going to take another 5 hours. It is connected via usb 2.0 though. The drive does have an esata connection and that will be much quicker. Can you please advise what command I need to mount the external drive ?

This is the line in /etc/fstab ..

```

UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk ext4 noauto,errors=remount-ro 0 1

```
Did you not read my post, or did you read it but not understand it?

I already mentioned the "/etc/fstab" entry looks fine. If it is like that, then you just need to use the "mount" command to actually mount it.

Be sure the directory exists
```

sudo mkdir -p /media/externaldisk

```
and mount it
```

sudo mount /media/externaldisk

```

The "/etc/fstab" file basically describes which options are passed to the "mount" command, so you can give the same options in the terminal.
```

sudo mount --types ext4 --uuid bbff7f7d-5db9-467c-b1c4-5831cc6870d6 --target /media/externaldisk

```

---

### Post by oygle on 2017-08-11
Thanks for your advice in regards to mounting. This is a liveboot , so the normal /etc/fstab entries are ignored. :)

---

### Post by oygle on 2017-08-14
Was able to do a clean install of Kubuntu 17.04 from a live usb, and update the backups whilst booted up with the Live usb. Thanks :)

---

