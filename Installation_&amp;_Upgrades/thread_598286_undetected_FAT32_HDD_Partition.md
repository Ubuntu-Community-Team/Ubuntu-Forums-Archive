---
title: "undetected FAT32 HDD Partition"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by user0182 on 2007-10-31
Hey Guys,

I have a Sony Vaio laptop with a 200 GB HDD, which is divided into 5 partitions 2 ntfs partitions for Windows Vista, 2 ext3 partitions for Ubuntu Linux and 1 empty FAT32 partition.

I set up the FAT32 partition to act as a shared partition, between MS Windows and Ubuntu. My problem is the when I look in Places>>Computer, I can view the ntfs partitions but not the FAT32 partition, that I really want :-( .

Any help that anyone can give me would be greatly appreciated. Thanks in advance.


Regards,

user0182

---

### Post by bw44 on 2007-10-31
> **user0182 said:**
> Hey Guys,

I have a Sony Vaio laptop with a 200 GB HDD, which is divided into 5 partitions 2 ntfs partitions for Windows Vista, 2 ext3 partitions for Ubuntu Linux and 1 empty FAT32 partition.

I set up the FAT32 partition to act as a shared partition, between MS Windows and Ubuntu. My problem is the when I look in Places>>Computer, I can view the ntfs partitions but not the FAT32 partition, that I really want :-( .

Any help that anyone can give me would be greatly appreciated. Thanks in advance.


Regards,

user0182

I had a similar problem and it turned out to be that the Fat32 partition was not being automatically mounted at system start-up.  In my (Feisty Fawn) system, the file systems (devices) that are automatically  mounted are listed in the /media directory, shown with the terminal command:

```

$ ls -l /media

```

To see if the device (partition) you are concerned about is recognized at all, enter 

```

$ sudo fdisk -l

```

If the partition is recognized with fdisk but isn't in /media you need to create a subdirectory (folder) in /media and change an entry in the file system table, to give the Fat32 partition an "automatic" mount point.  Please post the output from these two commands and I think I will be able to describe how to do this.

I'm not sure what your level of Linux knowledge is (I"m a rank amateur!), but if you are unclear about the concept of file mount points have a look at the page at this site: 

[http://users.bigpond.net.au/hermanzone/p10.htm#top10](http://users.bigpond.net.au/hermanzone/p10.htm#top10)

There, the author recommends writing a script to mount the partition rather than modifying the file system table.  You might prefer to do it as he/she recommends.

Good luck, and post a follow up if you can't get it sorted.

---

### Post by user0182 on 2007-11-05
The output of the 2 commands was as follows:

:~$ ls -l /media
total 32
lrwxrwxrwx 1 root root        6 2007-09-27 18:30 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2007-09-27 18:30 cdrom0
dr-xr-x--- 1 root plugdev  8192 2007-09-11 21:07 sda1
dr-xr-x--- 1 root plugdev 20480 2007-11-02 18:53 sda2

:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1277    10253312   27  Unknown
/dev/sda2   *        1277        9787    68359168    7  HPFS/NTFS
/dev/sda3            9788       18297    68356575   83  Linux
/dev/sda4           18298       24321    48387780    5  Extended
/dev/sda5           18298       19574    10257471   82  Linux swap / Solaris
/dev/sda6           19575       24321    38130246    b  W95 FAT32


Therefore, it would appear that my FAT32 partition is being detected but not automatically mounted. Thus, if you could instruct me how to give my FAT32 partition an automatic mount point I would be very greatful.

btw - I was just wondering, I think I know what all the partitions are for:
sda1 - MS Windows Recovery
sda2 - MS Windows Vista
sda3 - Ubuntu Linux
sda5 - Linux swap partition
sda6 - FAT32 partition
except sda4, could someone tell me what this partition is for. As I don't believe that I set up that partition, myself, so it must have been set up automatically. I am just curious!


Regards,

- user0182

---

### Post by Fire_Chief on 2007-11-05
On any hard disk, you can have what are called primary and extended partitions. All hard disks can have up to 4 primary partitions. If you want more than 4 you have to create some as extended partitions. What actually happens is a fake primary partition is setup and then the extended partitions are created within it. So /dev/sda4 is a fake partition marker that is automatically created when you add extended partitions.
You really don't have to worry about it but certainly don't try to delete it (you'll lose all of the extended partitions within it).

For another perspective on it, try running gparted from the desktop and you'll see the logical layout I'm talking about.

To have your FAT partition automount at startup, first create a folder (mount point) that you'll want to use to access the data (I have mine set as /store) so ```
sudo mkdir /store
```Then add an entry to your /etc/fstab file to mount it.```
sudo gedit /etc/fstab
```For example, if you want everybody to be able to read, write, and execute every file in your /store, you should specify the mask 0000:

/dev/sda6   /store   vfat   umask=0000    0 0

If you want only users from group 610 to be able to read, write, and execute:

/dev/sda6   /store   vfat   gid=610,umask=0707    0 0

If you want only users from group 610 to be able to read, and execute (not write):

/dev/sda6   /store   vfat   gid=610,umask=0727    0 0

Add one of these lines to the end of your /etc/fstab file and save. Reboot and it should be mounted.

You can also follow the guide [here]("http://www.psychocats.net/ubuntu/mountwindows") for more info on Windows partition mounting.

---

### Post by bw44 on 2007-11-05
> **user0182 said:**
> The output of the 2 commands was as follows:

:~$ ls -l /media
total 32
lrwxrwxrwx 1 root root        6 2007-09-27 18:30 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2007-09-27 18:30 cdrom0
dr-xr-x--- 1 root plugdev  8192 2007-09-11 21:07 sda1
dr-xr-x--- 1 root plugdev 20480 2007-11-02 18:53 sda2

:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1277    10253312   27  Unknown
/dev/sda2   *        1277        9787    68359168    7  HPFS/NTFS
/dev/sda3            9788       18297    68356575   83  Linux
/dev/sda4           18298       24321    48387780    5  Extended
/dev/sda5           18298       19574    10257471   82  Linux swap / Solaris
/dev/sda6           19575       24321    38130246    b  W95 FAT32


Therefore, it would appear that my FAT32 partition is being detected but not automatically mounted. Thus, if you could instruct me how to give my FAT32 partition an automatic mount point I would be very greatful.

btw - I was just wondering, I think I know what all the partitions are for:
sda1 - MS Windows Recovery
sda2 - MS Windows Vista
sda3 - Ubuntu Linux
sda5 - Linux swap partition
sda6 - FAT32 partition
except sda4, could someone tell me what this partition is for. As I don't believe that I set up that partition, myself, so it must have been set up automatically. I am just curious!


That's good. We're almost there.  Could you now post the output from the following command:
```

$  cat /etc/fstab 

```
where we should find the current entry/mount point for your FAT32 partition. If it looks OK you will be able to change the current mount point to a new directory in /media.

(I *think* the sda4 "Extended" partition is the one  within which the "logical" -- as opposed to "primary" -- partitions, "Linux swap" and "FAT32" were created by whatever utility was used to partition your dula boot system. Maybe someone else could confirm or dis-confirm this.  I have a very similar set-up to yours and there's an "Extended" partition on my system as well.)

---

### Post by bw44 on 2007-11-05
> **Fire_Chief said:**
> On any hard disk, you can have what are called primary and extended partitions. All hard disks can have up to 4 primary partitions. If you want more than 4 you have to create some as extended partitions. What actually happens is a fake primary partition is setup and then the extended partitions are created within it. So /dev/sda4 is a fake partition marker that is automatically created when you add extended partitions.
You really don't have to worry about it but certainly don't try to delete it (you'll lose all of the extended partitions within it).

For another perspective on it, try running gparted from the desktop and you'll see the logical layout I'm talking about.

To have your FAT partition automount at startup, first create a folder (mount point) that you'll want to use to access the data (I have mine set as /store) so ```
sudo mkdir /store
```Then add an entry to your /etc/fstab file to mount it.```
sudo gedit /etc/fstab
```For example, if you want everybody to be able to read, write, and execute every file in your /store, you should specify the mask 0000:

/dev/sda6   /store   vfat   umask=0000    0 0

If you want only users from group 610 to be able to read, write, and execute:

/dev/sda6   /store   vfat   gid=610,umask=0707    0 0

If you want only users from group 610 to be able to read, and execute (not write):

/dev/sda6   /store   vfat   gid=610,umask=0727    0 0

Add one of these lines to the end of your /etc/fstab file and save. Reboot and it should be mounted.

You can also follow the guide [here]("http://www.psychocats.net/ubuntu/mountwindows") for more info on Windows partition mounting.

This is more knowledgeable advice than I could offer.  On my system I did not have to create an entirely new entry in fstab;  there was already a mount point for my FAT32 "data sharing" partition in the table. So all I did was change the mount point from what the install procedure had set up (it was /windows), to a new (empty) directory in /media.  What I also learned from this exercise is that Ubuntu will automatically mount and put an icon for hard disk partitions on the Desktop if the mount point is in /media (which is something I also wanted.)  From what you are saying, the partition will be mounted automatically as long as there is a valid mount point in fstab, but I thought it had to be a mount point under /media to be automatically mounted, Thanks for correcting my understanding.

---

### Post by Fire_Chief on 2007-11-05
Actually I was not aware of the /media automounting ability. Probably explains why I used to see my shared partition appearing twice on the desktop. Once for my manual fstab entry and once for the automount detection (showed up as /dev/sda3 instead of folder name).

---

### Post by bw44 on 2007-11-05
> **Fire_Chief said:**
> Actually I was not aware of the /media automounting ability. Probably explains why I used to see my shared partition appearing twice on the desktop. Once for my manual fstab entry and once for the automount detection (showed up as /dev/sda3 instead of folder name).

Hmm.  After reading your previous post I concluded that the automatic **mounting** occurred if there was **any** mount point entry for the partition in fstab.  Whether it appeared automatically on the desktop was determined by whether the mount point was in /media.  (So the presence of the mount point in /media just caused the "auto-desktop-display" to occur, and this was consistent with what happened when I put the Fat32 partition mount point there.)  The names of the device/partition icons on the desktop seem inconsistent to me.  There's a DOS maintenance partition created by Dell as the first primary partition:  it appears on the Desktop as "Dell Utility",  I haven't got a clue where that name is coming from.  Two others appear to be named after the mount point folder in /media: sda2 for the XP NTFS partition, and Fat32 for my data sharing partition.  But I also have a  Kingston USB flash disk for which there is **no** entry in the fstab. Yet it seems to get automatically mounted anyway and appears on the Desktop as "KINGSTON." Go figure!

---

### Post by Fire_Chief on 2007-11-05
The drive names you are seeing are probably being pulled from the volume names assigned to the partitions. (Typically seen in Windows). I think you can change it though I've never needed to or bothered. I know it's changeable in Windows (Properties on the drive or edit in Drive Management).

---

### Post by vanadium on 2007-11-06
Removable drives are mounted automatically in /media when they are inserted. Permanent drives are configured to mount automatically through /etc/fstab during the installation of Ubuntu. Apparently, only your ntfs volumes were configured this way, so you need to add your FAT volume yourself.

An icon appears on the desktop for anything that is mounted under /mount. There is no icon of the mount point is elsewhere.

If available, a volume label is used as the name to mount the device during automatic mounting (i.e. not through fstab). How to set the volume label depends on the file system. You can find information on that in this forum.

---

### Post by user0182 on 2007-11-14
Thanks, for all of your replies. The output to the command: "cat /etc/fstab" is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5e4e44bf-8bc7-4375-b2d6-bf4e4203d415 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9886B80B86B7E840 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=EC341B3A341B06EC /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=073B-9E71  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2daea1a2-9094-4f16-8640-e9b0e9696bab none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Could someone please explain to me what all of the lines mean, as I would really like to learn and understand what I am doing. Although I think I understand a lot of it, obviously lines starting with a '#' are comments. In particular I would like to know what the last two lines do, regarding the Linux swap partition and the cdrom drive.

As I think I am coming to understand, does this output mean that my FAT32 partition has been mounted, but under "/windows". Therefore if I edited this file so that the mount point read "/media/windows", would this create a desktop icon for that partition with the label "windows"?

Also, I was wondering if I were to edit the file, and to comment out a line, such as the line beginning "UUID=9886B80B86B7E840 /media/sda1..." so that it would become "#UUID=9886B80B86B7E840 /media/sda1...". Would this stop that partition from automatically mounting at boot and if I then uncommented that same line would this restore the auto-mount at boot? And also could someone tell me how to change the labels, for the partitions?

Anyway, my basic problem is how do I get my sda6, FAT32 partition, to auto-mount at boot, so that it appears on my desktop?

I also wanted to again thank you, for all your help, I am incredibly grateful to you all.


Regards,

- user0182

---

### Post by bw44 on 2007-11-14
> **user0182 said:**
> Thanks, for all of your replies. The output to the command: "cat /etc/fstab" is as follows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=5e4e44bf-8bc7-4375-b2d6-bf4e4203d415 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=9886B80B86B7E840 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=EC341B3A341B06EC /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=073B-9E71  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=2daea1a2-9094-4f16-8640-e9b0e9696bab none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Could someone please explain to me what all of the lines mean, as I would really like to learn and understand what I am doing. Although I think I understand a lot of it, obviously lines starting with a '#' are comments. In particular I would like to know what the last two lines do, regarding the Linux swap partition and the cdrom drive.

As I think I am coming to understand, does this output mean that my FAT32 partition has been mounted, but under "/windows". Therefore if I edited this file so that the mount point read "/media/windows", would this create a desktop icon for that partition with the label "windows"?

Also, I was wondering if I were to edit the file, and to comment out a line, such as the line beginning "UUID=9886B80B86B7E840 /media/sda1..." so that it would become "#UUID=9886B80B86B7E840 /media/sda1...". Would this stop that partition from automatically mounting at boot and if I then uncommented that same line would this restore the auto-mount at boot? And also could someone tell me how to change the labels, for the partitions?

Anyway, my basic problem is how do I get my sda6, FAT32 partition, to auto-mount at boot, so that it appears on my desktop?

I also wanted to again thank you, for all your help, I am incredibly grateful to you all.


Regards,

- user0182

The lines beginning with # are comment lines (just to confirm your understanding).  Be careful about commenting things out: for example the next to last line in your fstab represents the Linux paging (swap) file!  The last line represents the mount point for a CD when you insert one.

You can confirm that your FAT32 partition has been mounted on /windows by using the file manager to navigate to that folder.  You should see the files/folders on the partition there.

If your FAT32 partition **is** there, then use the mkdir command to create a new (empty) folder under /media called, say for example, /windows:
```
$sudo mkdir /media/windows
```

Then follow  your own suggestion and edit fstab 
```
$sudo gedit /etc/fstab
```
and change the line
```
UUID=073B-9E71  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
```
to
```
UUID=073B-9E71  /media/windows        vfat    defaults,utf8,umask=007,gid=46 0       1
```

That should do it the next time you re-boot.  (Fire_Chief gave you instructions for setting up an entirely new entry, not under /media, which would work, but not cause your FAT32 partion to be displayed on the Desktop automatically.)

As for changing the partition names, have a look at Fire_Chief's earlier postings.  I haven't quite figured out myself how to change the names of the partitions.  I have one called "DellUtility" and it doesn't seem to be known even to Windows XP by that name. Maybe with gparted ... ?

Hope this helps -- you seem to be understanding it quite well.

---

