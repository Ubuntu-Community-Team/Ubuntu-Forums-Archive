---
title: "Install error - ubuntu can't see hdd"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by tejolote on 2012-12-04
Hi guys, 

I'm trying to install ubuntu on a six-month old Lenovo Ideapad U410.  Until today I've been using Windows 7, the install that came with the machine from the factory.  I have tried to install Ubuntu 12.04 and 12.10, the 64 bit versions, and both give me the same error, which is when I get to partitioning, no drive shows up.  If I continue, I get a generic error about Ubiquity. 

The ideapad doesn't have an optical drive, so at first I tried to install 12.10 from USB, and when it didn't work, I tried 12.04 from a usb stick.  Then I downloaded a completely fresh copy and burned a cd and tried to install using an external usb-connected cd drive.  In all cases I got the same error.

I went in and formatted the drive from the live CD (which boots up just fine, and is how I'm communicating now), using gparted.  Then I rebooted and tried again.  Same error.  I booted into gparted, and pulled out the cd cable and plugged in the USB stick.  It gave me the option to install on the USB stick.  I cancelled out of the install and went into gparted, and it shows two partitions sda1, which looks like the usb media (8 gb) and unallocated, which it shows as only 21.82 GB (I have a 1 TB hdd).

I'm feeling vaguely panicky, because I don't have a windows disk (I know, I know), just an "upgrade" disk from my university, which won't work without a previous install of windows (trust me, I tried it).     I've installed Ubuntu before on different machines, and every time it went smoothly, so I'm kind of flummoxed.   I'm kind of in a time crunch here on finals and...argh.  Any ideas on how I can solve this?

---

### Post by darkod on 2012-12-04
If the installer can't see the hdd but Gparted sees it fine in live mode, usually that means the disk has been used (or is used) in some sort of raid.

Some laptops these days use a combination of hdd+ssd in a raid setup. Since you formatted the disk and deleted all data, it doesn't hurt to try and remove eventual raid meta data with:
sudo dmraid -Er /dev/sda

Try that from live mode. In case you have another smaller disk (ssd) as /dev/sdb, do it for /dev/sdb also.

If that was your issue, it should work just fine after that.

If the command says there is no raid meta data, post the output of this so we can see more details:
sudo parted -l (small L)

---

### Post by tejolote on 2012-12-04
Ok, I ran sudo dmraid -ER on /dev/sda and /deb/sdb. The command executed, but no dice in the installation department.
[INDENT]This is the output I get:  ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary
 2      8733MB  24.5GB  15.7GB  primary  ext2


Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  211MB   210MB   primary  ntfs         boot
 3      952GB   979GB   27.3GB  primary  ntfs
 4      979GB   1000GB  20.8GB  primary  ntfs         diag


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           
[/INDENT]As you can see, it's not seeing my entire 1 TB hdd.

I've never had RAID set up.  Originally this disk had three partitions:  one for windows, and two partitions that had lenovo junk on them.  I bought from the factory and didn't change anything about it until tonight.

---

### Post by Bashing-om on 2012-12-04
Is UEFI booting a factor ? Can you still boot into windows ? Ubuntu install will have to match the windows booting method (dual booting ?).
How is Windows booting, in BIOS mode or in EFI mode? You can find out by typing "bcdedit" in a Windows Administrator Command Prompt window and looking for the "path" line in the "Windows Boot Loader" section. If this line refers to winload.efi, then you're booted in EFI mode; if it refers to winload.exe, then you've booted in BIOS mode.


[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by tejolote on 2012-12-04
Hey, I appreciate the idea, but it's not booting into Windows because I formatted that partition.  Windows no longer exists.   I did wonder if that was the problem at first (before I formatted), so I checked the BIOS and UEFI was enabled, but when I looked at the Ubuntu documention it said it could install with UEFI enabled.  Either way, I no longer have a windows option, so I have to get Ubuntu installed somehow.

---

### Post by darkod on 2012-12-04
UEFI is not an issue here since as we can see from the parted output, the 1TB disk has msdos table. Win7 can work with uefi only on gpt table.

But my guess about Intel SRT was correct. As you can see in parted, you have a 32GB SSD as /dev/sda (maybe you weren't even aware of this), and a 1TB HDD as /dev/sdb.

Congratulations, you just got a free 32GB SSD. :)

I never had Intel SRT, but from seeing posts here, you can try this:
1. Go into BIOS and look very carefully in all screens for Intel SRT. When you find it, disable it.

2. After that boot into live mode again, and in terminal run:
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb

That will remove any traces of meta data from both the ssd and hdd.

If all is good, you should be able to install now. Don't forget that it will run much faster if you install on the ssd, but put the swap partition on the hdd.

---

### Post by tejolote on 2012-12-04
Done!  Brilliant, thank you.   And if you're ever in Copenhagen, drop me a line and I'll treat you to a beer.  

I guess there's no more reason to procrastinate studying, blast it.

---

