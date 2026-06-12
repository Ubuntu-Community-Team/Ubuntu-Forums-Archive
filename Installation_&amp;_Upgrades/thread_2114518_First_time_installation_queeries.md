---
title: "First time installation queeries"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by Gedgehog not Hedgehog on 2013-02-10
Can anyone help me with an installation issue? I have three hard-drives, two of which are being used, (one for installation of games / music, the other for Windows) and I want to put the unused drive to use as an Ubuntu distro. When it comes to installing Ubuntu via USB, it fails to recognise the third drive. 
It's formatted and recognised by my system BIOS and the filesystem of both Ubuntu's installation disk and Windows - Indeed I can use it for anything I like on Windows! 
The only thing that is different about this drive is the fact that it is an IDE drive, but I can't see why that issue alone is preventing me from using it as a target for Ubuntu. Any ideas?

Attached are pictures to help illustrate what I mean.

---

### Post by darkod on 2013-02-10
First, linux doesn't install on ntfs. So, you need to copy any data you might have on that disk to another location, and if you want to use the whole disk for ubuntu delete the ntfs partition. There are few ways to do it, we can discuss it later.

Before that lets see if tools like parted show it. In the ubuntu live mode, open terminal and post the output of:
sudo parted -l (small L)

---

### Post by Gedgehog not Hedgehog on 2013-02-10
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? Yes                                                               
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? ok                                                             
Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      17.4kB  134MB  134MB               Microsoft reserved partition  msftres


Model: ATA WDC WD8000AARS-0 (scsi)
Disk /dev/sdb: 800GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   800GB  800GB  primary  ntfs


Model: ATA Maxtor 6L160P0 (scsi)
Disk /dev/sdc: 164GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  164GB  164GB  primary


Model: UFD 2.0 Silicon-Power2G (scsi)
Disk /dev/sdd: 2013MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2013MB  2013MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label    

Reading this is giving me a colossal headache!

---

### Post by darkod on 2013-02-10
So, the disk is seen as /dev/sdc. One option for the installer ignoring it might be raid meta data if it was ever used in raid before. You can try removing any left overs from live mode with:
sudo dmraid -Er /dev/sdc

Also, if you don't need anything on that disk, write a new msdos partition table with:
```
sudo parted /dev/sdc
mklabel msdos
quit
```

After that see if the installer can see it now.

On another note, I don't think you should have answered Yes to that question asking you if you have gpt table on /dev/sda. I think it was gpt earlier and you converted to msdos using windows. But windows doesn't do that properly and leaves the backup gpt table which confuses linux. I think you have msdos table on /dev/sda.

---

### Post by Gedgehog not Hedgehog on 2013-02-10
It worked and I could see the drive, however the installer crashed when I was installing the operating system, and now I can't seem to do anything with it! :(

---

### Post by darkod on 2013-02-10
If it crashed during repartitioning, just write a new table again and try again. I guess it doesn't show correctly now if the partitioning didn't have time to finish.

---

