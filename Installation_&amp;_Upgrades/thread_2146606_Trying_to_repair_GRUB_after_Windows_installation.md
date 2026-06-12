---
title: "Trying to repair GRUB after Windows installation"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by Ianman on 2013-05-19
Hi everyone,

Here is my situation. I had a working dual boot setup. Windows 7 was installed first following by Ubuntu 13.04. Everything was working fine until I had to use the Windows 7 installation disc to perform an upgrade. This of course over-wrote my MBR thereby removing Grub. Searching with google I found a number of solutions none of which work because for some reason when I boot with a live USB stick and run:

sudo fdisk -l

I don't see my partitions. If I start GParted it hangs with the message "Scanning all devices". It doesn't seem to be able to find my partitions.

If possible I would like to refrain from re-installing Ubuntu. Does anyone have any ideas?

Thanks!

---

### Post by sudodus on 2013-05-19
Please describe some details of your system!

- Are you using old time BIOS or UEFI?

- Please specify the basic hardware, at least the cpu and ram.

- Which version of Ubuntu 13.04 is it (32-bit or 64-bit)?

- What output do you get from

```
sudo parted -l
```

Maybe a good solution would be YannBuntu's ***Boot-Repair*** script, but before getting it we should find out which version you need.

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by Ianman on 2013-05-19
Here is the output from the terminal:

```
Model: ATA WDC WD10EAVS-00D (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 2057MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  2056MB  2056MB  primary  fat32        boot, lba


Model: ATA WDC WD1001FALS-0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  500GB   500GB   primary   ntfs
 2      500GB   1000GB  500GB   extended
 5      500GB   994GB   494GB   logical   ext4
 6      994GB   1000GB  6431MB  logical   linux-swap(v1)

```

This is showing me something weird though. I see that the boot is on what I thought was my secondary disk?

Some other information about my system:

CPU: core i7 920
RAM: 6 GB tripple channel DDR
2 physical hard disks both 1 TB. 
I think I am using a BIOS but not too sure. Its an ASUS P6T from 2009 so probably not using the UEFI standard. If I look on the asus site it would indicate a regular BIOS.

Any other information needed?

(Thanks for helping!)

---

### Post by fantab on 2013-05-19
Yes, you are using Legacy BIOS. You have to reinstall Grub. You can do it easily from LiveCD/USB with [**Boot-Repair**]("https://help.ubuntu.com/community/Boot-Repair").

Also 494GB for Ubuntu is way too much. Consider splitting into two partitions 30GB for "/" (system files) and the remaining GB for your DATA or /home. I would like to addititonally suggest that you consider installing one OS per HDD. It will help you a lot, especially with kind of issues you are having now.

---

### Post by sudodus on 2013-05-19
> **Ianman said:**
> Here is the output from the terminal:

```
Model: ATA WDC WD10EAVS-00D (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 2057MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  2056MB  2056MB  primary  fat32        boot, lba


Model: ATA WDC WD1001FALS-0 (scsi)
[COLOR=#ff0000]Disk /dev/sdc[/COLOR]: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  500GB   500GB   primary   ntfs
 2      500GB   1000GB  500GB   extended
 [COLOR=#ff0000]5      500GB   994GB   494GB   logical   ext4[/COLOR]
 6      994GB   1000GB  6431MB  logical   linux-swap(v1)

```

This is showing me something weird though. I see that the boot is on what I thought was my secondary disk?

Some other information about my system:

CPU: core i7 920
RAM: 6 GB tripple channel DDR
2 physical hard disks both 1 TB. 
I think I am using a BIOS but not too sure. Its an ASUS P6T from 2009 so probably not using the UEFI standard. If I look on the asus site it would indicate a regular BIOS.

Any other information needed?

(Thanks for helping!)

Your Ubuntu is installed on the third (sdc) drive's partition number 5, [COLOR=#ff0000]/dev/sdc5[/COLOR]

Where is Windows installed? I guess on /dev/sda1 (or is it on /dev/sdc1 or both?)

I think you have a choice either the use the instructions in the following link

[URL="https://help.ubuntu.com/community/Grub2/Installing"]https://help.ubuntu.com/community/Grub2/Installing
[/URL]or more specifically
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

or to use the Boot-Repair script, which is more automatic.
[URL="http://ubuntuforums.org/showthread.php?t=1769482"]http://ubuntuforums.org/showthread.php?t=1769482
[/URL][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Good luck :-)

---

### Post by Ianman on 2013-05-19
I tried to use the boot-repair script but it doesn't detect my partitions/disks so that isn't an option for me I am afraid. I don't understand why they are not detected?

I had also considered installing the OS's each on a separate disk but one of the disks is a caviar green which is terrible slow. The reason I gave Ubuntu so much space is because I do a lot of video editing. 

Thanks so far guys!

---

### Post by sudodus on 2013-05-19
> **Ianman said:**
> I tried to use the boot-repair script but it doesn't detect my partitions/disks so that isn't an option for me I am afraid. I don't understand why they are not detected?

I had also considered installing the OS's each on a separate disk but one of the disks is a caviar green which is terrible slow. The reason I gave Ubuntu so much space is because I do a lot of video editing. 

Thanks so far guys!

This makes me confused. Obviously ***parted*** finds your partitions. But you write that the GUI version, ***gparted*** won't. Are you running them from the same operating system? I would think you run them from the USB drive

```
Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 2057MB
``` 

Anyway, if not, I suggest that you run gparted from the system, where parted works. Otherwise I think it is possible to run the commands described in

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

from the system where parted can find the partitions.

---

### Post by jamesisin on 2013-05-19
When you are using GParted, are you using the drop-down menu to select between your different drives?  First you select the drive using that drop-down (upper-right of GParted) and *then* you will see the partitions *on that drive*.

---

### Post by oldfred on 2013-05-19
Parted is showing partition table, but gparted and Boot-Repair are trying to mount partition and that seems like the issue. I might drive fsck from a liveCD.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdc5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc5
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdc5

Check that drive is still sdc, it looks like flash drive became sdb, but that may change depending on what you have plugged in and in what order. If it changes, then change above command to correct drive & partition.

---

