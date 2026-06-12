---
title: "Couldn't install ubuntu full version from demo"
date: 2015-09-23
forum: Installation &amp; Upgrades
---

### Post by mnamz on 2015-09-23
I recently installed Ubuntu iso into unetbootin. So, it brought me to  demo version of Ubuntu, I don't have optical disk drive / any spare usb  to install it. I've tried installing full version through demo version  but it seems not to be working, can't find user I've created during  installation (still running demo version and stuck at here since I've  change primary OS boot to unetbootin and the keyboard doesn't seems to  be working when I'm about  to boot Window 7(still working as bootable OS  but given option in dual boot as I mentioned at above)).
So, is there any alternative I can do to complete installation of  Ubuntu? I just found out that I can choose partition to install ([http://imgur.com/gCPU9Jm](http://imgur.com/gCPU9Jm)) but I don't continue on that since I think it'll ruin my windows/hard disk. Thank you.

---

### Post by Bashing-om on 2015-09-23
mnamz; Hello;

1st thing is to insure the install medium is good.
Boot the liveUSB and as soon as the bios screen clears, depress and hold the shift key -> language screen, escape key to accept the default -> boot options screen -> choose " check disk for defects" . 
Will take a bit of time to run the check, does it complete with no errors ?

If the check is good, next we want to look at the partitioning on the hard drive(s).
From the liveUSB in "try ubuntu" mode activate a terminal from the desktop ( ctl+alt+t) .
Post back the outputs - Between Code Tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

to show what we have to work with.

[INDENT][INDENT]installing is no step
[INDENT][INDENT][INDENT]for a stepper
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mnamz on 2015-09-23
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6c326b8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   312575999   155928576    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac204

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   968386559   484192256   83  Linux
/dev/sdb2       968388606   976771071     4191233    5  Extended
/dev/sdb5       968388608   976771071     4191232   82  Linux swap / Solaris


```

```
Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  368MB  367MB  primary  ntfs         boot
 2      368MB   160GB  160GB  primary  ntfs


Model: StoreJet Transcend (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4292MB  extended
 5      496GB   500GB  4292MB  logical   linux-swap(v1)


```

Is there any way I can re-install ubuntu through demo version itself? I can't use CD method since my optical disc drive isn't working, and I don't have spare USB stick.

---

### Post by Bashing-om on 2015-09-23
mnamz; Well;

For clarification;
1) ubuntu is installed onto the the 2nd hard drive (sdb) ; Windows is installed onto that 1st hard drive (sda). Good.
2) To boot ubuntu OR Windows set in bios to boot the 2nd hard drive as the 1st boot priority ( with the USB drive disconnected )
      To boot up only Windows; set the bios boot priority to the 1st hard drive.

What results when resetting the boot priorities and attempting to boot ?

And, Yes, if you want or it is required, one can simply (RE-)install ubuntu . In the install live(USB) is the option " erase disk and install ubuntu" make sure it is the second hard drive choosen in the installer and the install wizard will comply. Will (RE-)install .
BUT let's not go there yet. let's instead find the nature of the booting problem and repair .

[INDENT][INDENT]just my 2 pounds worth
[/INDENT][/INDENT]

---

### Post by mnamz on 2015-09-24
Alright, I removed the 2nd drive and now I have reinstall ubuntu using my micro SD card, I stick in onto card reader, using EasyBCD plop. I use them to boot my usb, entering demo version and do clean install. Now it is working. Thanks for your help anyway :)

---

### Post by Bashing-om on 2015-09-24
mnamz; Great !

Pleased you are up and running.
Enjoy.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

