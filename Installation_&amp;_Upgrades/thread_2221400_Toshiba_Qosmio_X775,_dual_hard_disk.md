---
title: "Toshiba Qosmio X775, dual hard disk"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by john wagner on 2014-05-01
Not trying to hijack this thread, but...  I just installed 10.04 on my dual hdd (500 gig each) toshiba Qosmio X775 laptop.  I formatted one drive completely for the clean i Any advice?nstall.  Works great.  Except, I no longer have ANY access to the other drive.  It doesn't exist.

---

### Post by sammiev on 2014-05-01
> **john wagner said:**
> Not trying to hijack this thread, but...  I just installed 10.04 on my dual hdd (500 gig each) toshiba Qosmio X775 laptop.  I formatted one drive completely for the clean i Any advice?nstall.  Works great.  Except, I no longer have ANY access to the other drive.  It doesn't exist.

You really do need to start a new thread of your own to get the best results. Remember that 10.04 is history and not updated any more.

---

### Post by john wagner on 2014-05-02
Yeah, new thread for my question...

---

### Post by john wagner on 2014-05-02
I just installed 10.04 on my dual hdd (500 gig each) toshiba Qosmio X775 laptop. I formatted one drive completely for the clean install.  Used to have a dual boot of Windows 7 on one drive and 10.04 on the other.  Then my 10.04 started being buggy, so that's when I did the format and clean install. Works great. Except, I no longer have ANY access to the other drive. It doesn't exist. When I go to Bios (f2) it lists the two drives, but with the same serial number.  Doesn't matter what drive I select, it only goes to the Ubuntu one.

I figure I messed up grub/mbr being stored on the "empty" drive.  I lost Windows (no real loss) but I need to access the drive.  I wanted my dual drive back.  One disk Windows, the other Linux.  Help!!!!!  And yes, I know 10.04 is old but new is not always better!

john

---

### Post by fantab on 2014-05-02
> And yes, I know 10.04 is old but new is not always better!

Neither is sticking to a 'dead' version any wiser.

When reinstalling you must have chosen to 'erase windows or disk' option... then you may have lost the Windows partitions...
The following command should clarify; post its output here:
```
sudo fdisk -l
sudo parted -l
```

Do you want to Recover lost data? If YES then stop using the HDD immediately and boot with Ubuntu Live CD/DVD/USB.
If re-installing Windows is not an issue then perhaps its a good time install latest and supported version of Ubuntu.
Start afresh - set up your partitions and re-install both and dual-boot.

If you don't like the relatively new Unity-desktop interface then you can choose Ubuntu with XFCE desktop aka.. XUbuntu. Try it before you install.
There are other desktops as well that run on Ubuntu:
Gnome-Shell
Cinnamon
Mate
LXDE
Enlightenment
etc...

A lot of folks here on the forum have switched over to XUbuntu since Unity...

---

### Post by bapoumba on 2014-05-02
@ john wagner : moved your other posts in here.

---

### Post by mörgæs on 2014-05-02
> **john wagner said:**
> I know 10.04 is old but new is not always better

Yes, new IS better. First of all it brings you security updates.

---

### Post by john wagner on 2014-05-02
> **fantab said:**
> Neither is sticking to a 'dead' version any wiser.

When reinstalling you must have chosen to 'erase windows or disk' option... then you may have lost the Windows partitions...
The following command should clarify; post its output here:
```
sudo fdisk -l
sudo parted -l
```

Do you want to Recover lost data? If YES then stop using the HDD immediately and boot with Ubuntu Live CD/DVD/USB.
If re-installing Windows is not an issue then perhaps its a good time install latest and supported version of Ubuntu.
Start afresh - set up your partitions and re-install both and dual-boot.

If you don't like the relatively new Unity-desktop interface then you can choose Ubuntu with XFCE desktop aka.. XUbuntu. Try it before you install.
There are other desktops as well that run on Ubuntu:
Gnome-Shell
Cinnamon
Mate
LXDE
Enlightenment
etc...

A lot of folks here on the forum have switched over to XUbuntu since Unity...


results...
sudo fdisk -l

basset@basset-laptop:~$ sudo fdisk -l
[sudo] password for basset: 


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001627a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59706   479584256   83  Linux
/dev/sda2           59706       60802     8799233    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5           59706       60802     8799232   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536    f  W95 Ext'd (LBA)
/dev/sdb5               1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdc: 7803 MB, 7803174912 bytes
122 heads, 58 sectors/track, 2153 cylinders
Units = cylinders of 7076 * 512 = 3622912 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2153     7617285   83  Linux



results for $ sudo parted -l

Model: ATA Seagate ST950042 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  491GB  491GB   primary   ext4            boot
 2      491GB   500GB  9010MB  extended
 5      491GB   500GB  9010MB  logical   linux-swap(v1)


Model: ATA Seagate ST950042 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  500GB  500GB  extended               lba
 5      2097kB  500GB  500GB  logical   ntfs


Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdc: 7803MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      29.7kB  7800MB  7800MB  primary  fat32

---

### Post by fantab on 2014-05-03
You have two HDDs and one USB connected while you took the output.

```
Model: ATA Seagate ST950042 (scsi)
Disk /dev/sda: 500GB
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  491GB  491GB   primary   ext4            boot
 2      491GB   500GB  9010MB  extended
 5      491GB   500GB  9010MB  logical   linux-swap(v1)
```

This HDD, /dev/sda is where Ubuntu is.


```
Model: ATA Seagate ST950042 (scsi)
Disk /dev/sdb: 500GB
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  500GB  500GB  extended               lba
 5      2097kB  500GB  500GB  logical   ntfs
```

This HDD, /dev/sdb is probably not showing, right?

Did you mount the second HDD? Can you find it listed under "Devices" in the file-browser.

Also download and burn to USB etiher 14.04 or 12.04 Ubuntu or [Xubuntu]("http://xubuntu.org/") and "Try it without installing". Check the file-browser for /dev/sdb.
Let us know whether you find the second HDD...

---

### Post by john wagner on 2014-05-03
> **fantab said:**
> You have two HDDs and one USB connected while you took the output.

```
Model: ATA Seagate ST950042 (scsi)
Disk /dev/sda: 500GB
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  491GB  491GB   primary   ext4            boot
 2      491GB   500GB  9010MB  extended
 5      491GB   500GB  9010MB  logical   linux-swap(v1)
```

This HDD, /dev/sda is where Ubuntu is.


```
Model: ATA Seagate ST950042 (scsi)
Disk /dev/sdb: 500GB
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  500GB  500GB  extended               lba
 5      2097kB  500GB  500GB  logical   ntfs
```

This HDD, /dev/sdb is probably not showing, right?

Did you mount the second HDD? Can you find it listed under "Devices" in the file-browser.

Also download and burn to USB etiher 14.04 or 12.04 Ubuntu or [Xubuntu]("http://xubuntu.org/") and "Try it without installing". Check the file-browser for /dev/sdb.
Let us know whether you find the second HDD...

You're right.  The Windows HDD doesn't show up at all, anywhere.  Not even BIOS.  I have both OS's on disks I'll check the live cd's file-browser for /dev/sdb.  That didn't occur to me...  Sneaky!  I'll let you know!

---

### Post by john wagner on 2014-05-03
Edit:

I tried the Live CD route got nada.  That other HDD doesn't show up at all.  I don't want to, but it's looking like I'm gonna have to yank it, stick it in my dock, clone it then reinstall after formatting.  Maybe the Linux will 'see' it then?  As an empty partition?  I dunno, help!!!!

---

### Post by fantab on 2014-05-05
Its not that your /dev/sdb is not showing; it does turn up in both *'parted -l* and *fdisk-l'*. So the system sees it.
Also the 'outputs' don't show any errors.

If you tried the latest Ubuntu then have you checked in the launcher? if it was xubuntu then they show up on the desktop.
However, if latest Ubuntu did NOT find your HDD then perhaps reinstalling won't help.

Try some Windows software to see if data from /dev/sdb can be retrieved/recovered. if there is any data to be recovered.
[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") can help too but you must prefer a Windows tools to do the job.

From LiveCD open [*Gparted *]("http://www.dedoimedo.com/computers/gparted.html")and check if it shows up there. If it does, then check for any rounded red icon with white exclamation mark. This icon will tell you what the problem is.
We can either fix the problem ordelete the partitions and make two new primary partitions /dev/sdb1 and /dev/sdb2. This will completely erase the disk and the data on it... So try to recover your data first.
If Ubuntu then check the 'Launcher' for two new 'devices', /sdb1 & /sdb2.

Lastly, get in touch with the Toshiba service..

---

### Post by john wagner on 2014-05-05
> **fantab said:**
> Its not that your /dev/sdb is not showing; it does turn up in both *'parted -l* and *fdisk-l'*. So the system sees it.
Also the 'outputs' don't show any errors.

If you tried the latest Ubuntu then have you checked in the launcher? if it was xubuntu then they show up on the desktop.
However, if latest Ubuntu did NOT find your HDD then perhaps reinstalling won't help.

Try some Windows software to see if data from /dev/sdb can be retrieved/recovered. if there is any data to be recovered.
[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec") can help too but you must prefer a Windows tools to do the job.

From LiveCD open [*Gparted *]("http://www.dedoimedo.com/computers/gparted.html")and check if it shows up there. If it does, then check for any rounded red icon with white exclamation mark. This icon will tell you what the problem is.
We can either fix the problem ordelete the partitions and make two new primary partitions /dev/sdb1 and /dev/sdb2. This will completely erase the disk and the data on it... So try to recover your data first.
If Ubuntu then check the 'Launcher' for two new 'devices', /sdb1 & /sdb2.

Lastly, get in touch with the Toshiba service..



A Live CD of 12.04 didn't show it at all, will try a 14.04 Live CD after I burn one.  I know Windows is still there, my keyboard still lights up (it won't with just Linux) it's using the driver on the Windows HDD.  I really appreciate your help so far, after my 14.04 and  [URL="http://www.dedoimedo.com/computers/gparted.html"]*Gparted *[/URL attempt is done I'll post the results!

---

### Post by john wagner on 2014-05-12
Nope.  Nada.  Doesn't show with any live cd, or with windows boot, or with recovery disk, grub installer, nothing.

Very confused.

---

