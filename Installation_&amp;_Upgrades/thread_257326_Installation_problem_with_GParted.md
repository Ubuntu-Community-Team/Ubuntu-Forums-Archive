---
title: "Installation problem with GParted"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by nana-chan on 2006-09-14
Hi,
I tried to install Dapper Drake 6.06 on my new Laptop. I already got the Partitions set up, and a WinXP running. But GParted won't recognize my partitions.
On the Live-CD I can access all the Partitions on /dev/hda.
When I start GParted (or the setup runs it) it tells me that there are no partitions set up on hda. I already tried to rewrite the MBR with the Windows Recovery Console. No success.
I hope someone can help me.

---

### Post by ciscosurfer on 2006-09-14
Read this page for info on writing to the MBR, etc.  Then reattempt to install Ubuntu: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by nana-chan on 2006-09-14
Thanks for the hint, but I think this goes the wrong direction. To clear things up: I got no Ubuntu installed yet on this machine.
I booted the new computer with the Ubuntu Live-CD and used GParted to make my Windows, Linux and Data-Partitions. Then I installed WinXP. After that, I tried to install Ubuntu and get the display in GParted that the whole disk is unallocated.
btw... I wrote this after reading the page you linked to. Maybe I just didn't get what you meant.

---

### Post by dooblem on 2006-09-14
I have exactly the same problem !

I can't install ubuntu dapper drake because gparted doesn't see any partition in my partition table.

It behaves like if the drive was totaly empty with no partitions at all.

when I launch gparted manually, it displays some errors (see bellow)..

```
# fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2714    20517808+   7  HPFS/NTFS
/dev/hda2            2715        4245    11574360    c  W95 FAT32 (LBA)
/dev/hda3            4246        4752     3827250    5  Extended
/dev/hda5            4246        4310      481918+  82  Linux swap / Solaris
/dev/hda6            4310        4826     3903763+  83  Linux
root@ubuntu:~# gparted
Error: Can't have overlapping partitions.
Warning: Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
Error: Unable to open /dev/hdc - unrecognised disk label.

```

---

### Post by nana-chan on 2006-09-14
I just checked, if I got that problem too. Everything seems fine for me in fdisk. I just noticed in the code you provided, that the error is on hdc and not on hda.

---

### Post by ciscosurfer on 2006-09-14
The Install-to-HardDisk icon on your desktop (when running the LiveCD) will setup your partition table for you (uses a form of gparted), which will setup your /etc/fstab the correct way.

XP likes to be installed first (issues with the MBR, etc.)

You should install XP first, like you normally would, then use the LiveCD to install Ubuntu.  XP doesn't play nicely if you try to install it "over" an Ubuntu install without seriously messing around with your MBR.  My advice, and the advice of many out here, is to install XP first, and then install Ubuntu.

---

### Post by nana-chan on 2006-09-14
@dooblem:
It seems, that I forgot to try to run gparted form terminal the first time. Now I did, and it gives me the same error as you mentioned.

@ciscosurfer:
I'm not really sure, if you read what I wrote, for this is exactly I what I did. The only difference is, that I used GParted to set up the disk, because I don't like the windows-partitioner.
But I tell you again: I installed WinXP and now I'm trying to install Ubuntu.
And...btw, this is not the first time for me to do this, it's just the first time to get this error.

---

### Post by ciscosurfer on 2006-09-14
@nana-chan:
Okay.  I understand now, sorry, I misread your post.  I would then suggest you download the [GParted image from here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828"), burn it to a disc, and use it this way...if you don't care about losing info (if you don't have anything new on your drives, backing up important files is probably irrelevant...but if you do have important files, then backup obviously back them up), boot from your newly-created GParted disc, delete all partitions on all drives, create new one's to your liking for Windows using the correct filesystem type, restart, install Windows, restart, load up Windows to make sure everything is ok and load necessary files for Windows, shutdown, reboot with Ubuntu LiveCD, install Ubuntu via the Install-to-HardDisk option, it will partition Ubuntu for you, or you can create your own partitions via its partition editor (could be messy if you don't know what you're doing...you need a root partition ( / ) and swap partition at the very least), let it install everything it needs, reboot, click the orange icon in the upper-right to start the update-manager, download and install all updates, reboot, and then enjoy two systems.  Grub will install to the MBR of the first disk unless you tell it otherwise.

---

### Post by nana-chan on 2006-09-14
I'm glad to have cleared the misunderstanding, but still there seems to be something unclear.
First of all I have to tell you: I'm no linux-novice. I'm a System-Administrator on professional level. I know that I always have the option of a complete reinstallation. But this is currently only the last option for me.
I already set up the partitions:
[LIST]
[*]15GB NTFS for WinXP [And already installed]
[*]15GB Ext3 for Ubuntu
[*]one extended Partition containing:
[LIST]
[*]512MB Linux SWAP
[*]60GB NTFS for Data [Loaded with data...hard to back-up]
[*]5GB FAT32 for Cross-Platform-Data
[/LIST]
[/LIST]
Maybe I should have mentioned that earlier, but I saw no need for that.

---

### Post by ciscosurfer on 2006-09-14
Please post the output of sudo fdisk -l

---

### Post by nana-chan on 2006-09-14
Due to the late time (1 AM) and the fact that I currently connect to internet via WirelessLAN, I'll post the output tomorrow, when I got LAN-access to internet and so also from the Live-CD.

---

### Post by nana-chan on 2006-09-15
Here is the requested code:
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/hda2            1959        3916    15727635   83  Linux
/dev/hda3            3917       12161    66227962+   5  Extended
/dev/hda4           11509       12161     5245222+   b  W95 FAT32
/dev/hda5            3917        3982      530082   82  Linux swap / Solaris
/dev/hda6            3983       11508    60452563+   7  HPFS/NTFS

```

---

### Post by ciscosurfer on 2006-09-15
Try out the Live GParted CD and see if you can access/repartition/setup that way.  See how that goes.  Otherwise, you've got me.

You can also try using parted, sfdisk, or cfdisk.  Check the man pages for additional info on these.

---

### Post by nana-chan on 2006-09-15
Well, it didn't work with the GParted LiveCD either. I managed to get an external HDD for backup and deleted all Partitions except the one Windows is installed in with the Windows Partitionmanager. After that, I retried to run GParted and create the partitions. This time everything went fine, and Ubuntu is already up and running in a base config.
Anyways, thanks for the help, even if I still don't really know how the problem came up.

---

### Post by ciscosurfer on 2006-09-15
Do you think it had anything to do with trying to rewrite your MBR using Windows utils and/or the fact that you used a Windows partitioner?  That's why I suggested you look at the my original link on how to recover Ubuntu after a windows install (had to do with resituating your GRUB, etc....even though your Ubuntu wasn't up yet, the information on that page proves useful for many when they hit the same problem you were having...but anyway....glad all is well now!)

---

### Post by nana-chan on 2006-09-15
Actually I think I used the word "rewrite" a bit wrong. I didn't do any HEX-editing or anything. I just started the recovery console and used the command "fixmbr".
In my opinion, this wasn't the reason. Actually I didn't really expect that to work.
I think I recall some strange problem during the Windows-setup. Even though I had deleted all partition and made new ones with GParted before that, the setup recognized the first partition as some recovery partition, and didn't assign a letter to the drive. I just deleted it inside Windows-setup and remade the partition. This problem never appeared again, but it may have been the source.

---

### Post by ciscosurfer on 2006-09-15
No, I believe you used "rewrite" correctly: anytime you mess with an area (via a GUI or command line, even in Windows or DOS) you are essentially rewriting what was there previously.  If you continued with the operation of issuing "fixmbr," then you rewrote your MBR.

But yes, I do believe that your problem may have been how Windows initially setup your partitions (creating a recovery partition first...usually it's created second, no?) and why GParted recognized your first partition as a recovery partiton.  But you didn't tell me about this fact until now and I probably would've have said something to you then about this fact.  But hey, it really doesn't matter now does it...you've got everything back up and running and that's great!

---

