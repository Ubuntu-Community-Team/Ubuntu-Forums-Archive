---
title: "Fifth try installing 12.04"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by christopherbrown03 on 2013-12-12
Okay, I have been working on this all day and cant seem to get anywhere.  I am a newbie to linux, so please dumb it down for me.  I had a dual-boot system with windows 8 and 13.10 installed.  After not using windows for 6 months, I have decided to go all linux.  I had some issues getting 13.10 installed, but eventually got it working.  I have not had the same success with 12.10.  I tried installing it the first time over windows, so my hard drive got wiped, which was what I wanted, I think.  The first time I did the install, I let the installer set everything up and before it installed I got this message: The gtub-efi-amd64-signed package failed to install into /target/.  After getting this, I went ahead and tried to boot into ubuntu and got an error upon startup saying that my hard drive could not be found.  I then tried installing it again, this time with manual partitions. Here are screen shots of my partitions from gparted.
[ATTACH=CONFIG]248548[/ATTACH][ATTACH=CONFIG]248549[/ATTACH]

The first shot is from my 32 gb solid-state drive, the second of my 500 gb regular hard drive.  I tried it with all the partitions on the 500 gb drive, but that didnt change anything.  When I put the partitions on the SSD I could run boot-repair and get grub installed, but now all I get is a grub command line propmt when I boot.  Also, before putting the partitions on to the SSD, Ubuntu did not appear in my bios boot menu, but now there are two instances.  I have run boot repair several times, but the last time I ran it was the most successful.  Here is the URL:

[http://paste.ubuntu.com/6563199/](http://paste.ubuntu.com/6563199/)

Also I should mention that I am booting with UEFI secure boot on.  If I turn secure boot off, I cannot even boot from the live-usb I am using currently.  Also, I changed the SSD from intel smart response to ACHI, though I am not sure what that even means.  I am just trying to get my comupter to work again!  I have searched the forums and tried a number of things and can not figure this out.  Any help would be appreciated.  Thank you.

---

### Post by Bashing-om on 2013-12-12
christopherbrown03; Hi !

Bear in mind I am not knowledgeable in respect to UEFI or secure boot.
What I do not see is the hard disk SDA ! .. Why ?
That drive should be the 1st drive found by bios, Is the 1st sata buss connector not being used ?
Is bios set to boot from the drive you intend to use as the primary operating system install ? ( I would think the SSD drive)
Is grub installed onto that primary booting drive ?

In this instance perhaps terminal commands will yield more useful information.
As you are presently not able to boot the install;
From the liveDCD:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print #just to see if there is any result
sudo parted /dev/sdb
sudo parted /dev/sdc

```'#' represents a comment, not to be entered !
Maybe then we can tell more of what is not going on.


[INDENT][INDENT]just food for thought
[/INDENT][/INDENT]

---

### Post by christopherbrown03 on 2013-12-12
Bashing,
   Thank you for the reply. Here is the output from the commands you wanted entered.

ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xc8c2ff1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e8c4ec5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1    62533295    31266647+  ee  GPT

Disk /dev/sda: 7876 MB, 7876902912 bytes
256 heads, 39 sectors/track, 1540 cylinders, total 15384576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087372

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          32    15384575     7692272    b  W95 FAT32

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2a0b3f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63   488392064   244196001    c  W95 FAT32 (LBA)


ubuntu@ubuntu:~$ sudo parted -l

Model: Lexar USB Flash Drive (scsi)
Disk /dev/sda: 7877MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  7877MB  7877MB  primary  fat32        boot


Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  500GB  500GB  ext4


Model: ATA Micron C400 Real (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  200MB   199MB   fat32                 boot
 2      200MB   450MB   250MB   ext4
 3      450MB   15.4GB  15.0GB  ext4
 4      15.4GB  19.5GB  4096MB  linux-swap(v1)


Model: Toshiba External USB HDD (scsi)
Disk /dev/sde: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  fat32        lba

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print



Model: Lexar USB Flash Drive (scsi)
Disk /dev/sda: 15384576s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      32s    15384575s  15384544s  primary  fat32        boot

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print

Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sdb: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End         Size        File system  Name  Flags
 1      2048s  976771071s  976769024s  ext4



ubuntu@ubuntu:~$ sudo parted /dev/sdc unit s print


Model: ATA Micron C400 Real (scsi)
Disk /dev/sdc: 62533296s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End        Size       File system     Name  Flags
 1      2048s      391167s    389120s    fat32                 boot
 2      391168s    878591s    487424s    ext4
 3      878592s    30175231s  29296640s  ext4
 4      30175232s  38174719s  7999488s   linux-swap(v1)


I dont know what half of this stuff means, I am a beginner and am just trying to escape the surly grips of Windows.  I thought that my SSD was installed to be the boot disk so that the computer started up faster.  When I had the boot partitions on the 500 gb hard drive, I couldnt get anything to work.  With it on the SSD I have been able to at least get a gryb command prompt. I believe that SDA is the USB drive that I am using for my live boot.

---

### Post by Bashing-om on 2013-12-12
christopherbrown03; Hey,

Maybe things are not a bleak as they appear.
I do not understand why the flash drive is recognized as the 1st drive sda, but I can accept that it is.
Drive sdb is a single partition .. recon it is going to be a "data" storage drive.

Now the biggy -> sdc the SSD drive that you are installed on (?).
Partition sdc1 is the boot partition for the GPT partitioned hard disk, looks proper.
Partition sdc2 is very small. what in the world are you using it for, almost at capacity now ?
Partition sdc3 is that '/' (root) ? to be the only operating system partition (not counting the swap partition) ?
Partition sdc4 is the swap partition, good !

SDE hard drive .. Windows' data disk, I would for now remove it (external ?) Simplify as much as possible.

OK ! 
So what is set in bios as the primary boot device ? Make doubly sure for now that you have it set to boot from the SSD ( not sda, the USB flash drive !). I can not tell you how to make bios differentiate that the 2nd hard disk is what you want to boot from.

Pull the flash drive anyway - done with it for the time being -, bios set to boot from the SSD, REboot.
What exactly do you see then ? Where to you get to in the boot process ?

Bear in mind I still do not understand how the USB flash drive is recognized as 1st device !


But, hey, one way or another, 
[INDENT][INDENT]we will get through this
[/INDENT][/INDENT]

---

### Post by christopherbrown03 on 2013-12-12
I actually just got 13.10 to work.  I think that it had something to do with the EUFI boot since it was a windows 8 machine.  I wanted 12.10 because it was an LTS, but I will just keep working on 13.10 until the new LTS comes out I guess.  Now I'm off to try to get a printer to work, still havent been able to figure that one out.  Just for the record the bios was set to boot from the SSD installed on the machine, I figured that out.  I think that sdc2 was a second boot partition, I was thinking I needed a seperate EFI boot and a "normal" boot partition.  All well, we got it working now!  Thanks again for the help, I really do appreciate you taking the time out to work on this with me!

---

### Post by Bashing-om on 2013-12-12
christopherbrown03; Not a problem at all ,

We are here to help.

As you are up and running, you do good work. Please mark this thread solved; 1st post thread tools.

If I may, do your homework on using a SSD, the consensus is to limit the writes to the SSD, a limited lifetime to that surface - move swap off the SSD !

Problems with installing the printer, by all means post another thread.

[INDENT][INDENT]and hey
[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT]

---

