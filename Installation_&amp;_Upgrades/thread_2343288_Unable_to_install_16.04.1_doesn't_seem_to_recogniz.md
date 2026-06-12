---
title: "Unable to install 16.04.1 doesn't seem to recognize hard drives"
date: 2016-11-15
forum: Installation &amp; Upgrades
---

### Post by r0ckst4r on 2016-11-15
I'm trying to load 16.04 LTS from a USB stick and I'm having some difficulty.  The computer in question is an HP desktop with a 2TB SATA hard drive and Legacy BIOS.  It originally had windows 7 which was upgraded to windows 10.  I used the windows shrink utility to create a large unallocated partition and I disabled fast startup which was recommended in other threads I have searched.

The issue is that when I get the "Installation Type" screen (3rd screen in the install process) it will not give any options of "install along side windows" or "erase disk" or anything like that.  All it gives me is a screen that used to be in older installers where you would create partitions yourself however it does not list any drives or partitions.  Hitting any of the buttons on the screen will instantly freeze everything or crash the installer (if I am running it from the "try without installing" GRUB option.  I have tried both installing right from the GRUB menu and from the runtime environment with the same results.  In the runtime environment the hard drive is mounted on the left hand side bar and is able to be opened and explored.  As soon as I click the install Ubuntu icon the mounted drives disappear.  This has been getting frustrating as Ubuntu installations in the past have not been this difficult.  I also attempted to install a previous version (14) but to no avail.  Does anyone have any ideas what I can try next?

---

### Post by ajgreeny on 2016-11-15
Can you try the "Something Else" option when you get to the third or fourth screen in the installation and see if the installer now sees the disk.

Also tell us more about the hardware, particularly the graphic card which may need you to boot with the **nomodeset** option by using F6 at the first screen, to get to a GUI.

---

### Post by oldfred on 2016-11-15
Most Windows 7 systems used all 4 primary partitions. Is that your issue?
Or is it the Windows 10 always on hibernation or fast start up? That prevents the Linux NTFS driver from seeing that you have anything on that partition.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[URL="http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360"]http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360

[/URL]
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

[URL="http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360"]
[/URL]

---

### Post by r0ckst4r on 2016-11-15
> **ajgreeny said:**
> Can you try the "Something Else" option when you get to the third or fourth screen in the installation and see if the installer now sees the disk.

Also tell us more about the hardware, particularly the graphic card which may need you to boot with the **nomodeset** option by using F6 at the first screen, to get to a GUI.

As I mentioned it does not even give me these options, this screen seems to be bypassed all together.  Here are more hardware details.

AMD FX-8120, 970 chipset 3.1 Ghz
10 GB RAM
Radeon HD 7570 graphics card

Do I need to use the nomodeset option you mentioned?  How would I go about doing this?


[QUOTE=oldfred]
Re: Unable to install 16.04.1 doesn't seem to recognize hard drives
                          Most Windows 7 systems used all 4 primary partitions. Is that your issue?
Or is it the Windows 10 always on hibernation or fast start up? That  prevents the Linux NTFS driver from seeing that you have anything on  that partition.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/14982...install-ubuntu]("http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu")
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[URL="http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360"]http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360

[/URL]
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.p...2#post13488472]("http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472")
[http://www.tenforums.com/tutorials/4...dows-10-a.html]("http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html")
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2...dows-10-a.html

[/URL][/QUOTE]

I did already mention this that I had already disabled fast start up as well as had an unallocated partition ready to go using the windows 10 shrink partition tool.

---

### Post by r0ckst4r on 2016-11-15
Maybe it will help to show the screens that I see.  Please pardon the crude phone images.  The first screen is of course the language selection.  The second is the check box for installing wifi updates and proprietary drivers.  The third screen is the one that is the problem and that will then crash the system.  It should give me a different screen with options but it does not.  This is the only screen I see and all buttons crash the installation.

---

### Post by oldfred on 2016-11-16
If you used Windows to create unallocated, but still have 4 primary partitions the space cannot be used.
If you used Windows to create more than 4 primary partitions it converts to proprietary dynamic partitions not the usual primary, extended & logical partitions. 

Post this:
sudo parted -l

---

### Post by r0ckst4r on 2016-11-16
You are correct, I did not realize that there was a 4 partition limit.  I deleted the recovery partition but I still am having the same issue.  Here is the output you requested.


```
Model: ATA Hitachi HDS72302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size   Type     File system  Flags
 1      1049kB  106MB   105MB  primary  ntfs         boot
 2      106MB   933GB   932GB  primary  ntfs
 3      1981GB  1982GB  472MB  primary  ntfs         diag


Model: Sony Storage Media (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4006MB  4006MB  primary  fat32        boot, lba


```

---

### Post by r0ckst4r on 2016-11-16
I went back to the windows partition tool and created a partition instead of just having unallocated space.  Unfortunately the same problem remains.  Here is the updated information.

```
Model: ATA Hitachi HDS72302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   933GB   932GB   primary   ntfs
 3      933GB   1981GB  1049GB  extended               lba
 4      1981GB  1982GB  472MB   primary   ntfs         diag


```

---

### Post by oldfred on 2016-11-17
Ubuntu cannot install to a NTFS partition.
You need unallocated or partition in advance with gparted.

But did you turn off Windows fast start. That prevents installer from seeing the NTFS partitions as they are hibernated and cannot be mounted to know what they are other than from partition table we know they are NTFS.

 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by r0ckst4r on 2016-11-17
> **oldfred said:**
> Ubuntu cannot install to a NTFS partition.
You need unallocated or partition in advance with gparted.

But did you turn off Windows fast start. That prevents installer from seeing the NTFS partitions as they are hibernated and cannot be mounted to know what they are other than from partition table we know they are NTFS.

 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

The first data set I posted (that listed only 3 partitions) was when there was no partition and just unallocated space.  That did not work.  Yes, Windows fast start is disabled.  It was one of the first things I tried.  I still seem to be back at square one with this install.  Anything else that I am missing?

---

### Post by oldfred on 2016-11-17
Have you tried creating an ext4 partition and a swap partition with gparted and then use Something else to install and choose/change ext4 partition as /?

---

### Post by r0ckst4r on 2016-11-17
I just tried to create the partition ahead of time with gparted which was successful however it still gives me the same problem.  I can access all the partitions just fine in the live environment but it seems like all the partitions unmount every time I start the installer.

---

### Post by r0ckst4r on 2016-11-17
> **oldfred said:**
> Have you tried creating an ext4 partition and a swap partition with gparted and then use Something else to install and choose/change ext4 partition as /?

Also just to reiterate the main problem is that I never have a chance to get to "something else" as that option screen is never presented to me.  The only three screens I get are the ones I posted previously.

---

### Post by oldfred on 2016-11-18
Was drive ever RAID? That has RAID meta-data that causes problems.

Was drive ever gpt as mixed gpt & MBR can cause problems.
Usually gparted would also have complained and it would be one or the other.

Post this, do not expect to see anything:
sudo parted -l

---

### Post by r0ckst4r on 2016-11-18
> **oldfred said:**
> Was drive ever RAID? That has RAID meta-data that causes problems.

Was drive ever gpt as mixed gpt & MBR can cause problems.
Usually gparted would also have complained and it would be one or the other.

Post this, do not expect to see anything:
sudo parted -l

There is a RAID utility on start up so that may have been a possibility.  When I enter the utility it says the drive is RAID ready but nothing else.  It is MBR only as far as I know.  Here is what the drive looks like after using gparted

```
Model: ATA Hitachi HDS72302 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   933GB   932GB   primary   ntfs
 4      933GB   1981GB  1049GB  extended
 5      933GB   1970GB  1038GB  logical   ext4
 6      1970GB  1981GB  10.7GB  logical   linux-swap(v1)
 3      1981GB  1982GB  472MB   primary   ntfs            diag


```

---

### Post by r0ckst4r on 2016-11-18
Also, just to be thorough I tried making a primary partition and also no such luck.  The installer should be recognizing SOMETHING by this point and not pretending like there isn't a hard drive.  To reiterate the live environment recognizes the hard drives and partitions perfectly and I can navigate them.  This is a problem with the installer.  I know its been a long time but when I first started using Ubuntu there were "alternate" CDs which used an older text only installer when i had trouble with the GUI installer.  Do these still exist?

---

### Post by oldfred on 2016-11-18
You have used all 4 primary partitions, so you cannot create another primary. Only logical inside the extended.

Make sure drives are set to AHCI, not IDE nor RAID in BIOS.

The last alternative installer was 12.04.
But you can use the server installer and not install any server software and then install desktop of your choice. Server installer is not a live installer.

You can run this, it will not hurt if not using RAID.
 sudo dmraid -E -r /dev/sda 

Does Disks utility show anything special about drive? Also in upper right icon is Smart Status.

---

### Post by r0ckst4r on 2016-11-19
> **oldfred said:**
> 

You can run this, it will not hurt if not using RAID.
 sudo dmraid -E -r /dev/sda 



Thank you my kind sir, that one line solved my problem.  Just for future searchers I will outline some of the settings that I had to change to get this to work correctly outside of making sure that all 4 partitions are not in use which was already outlined.  Since Windows 10 booted from Legacy BIOS on my system (and my system has the ability to boot UEFI)  I had to make sure that UEFI booting was disabled because this was the default boot choice for a USB drive.  Also, I made sure that the "storage emulation" was set to AHCI and not RAID or IDE.  This was all done in BIOS, more specifically the HP's version of BIOS .  After this is done you can boot to the live environment open terminal and put in your magical command which fixed everything.  The installer worked as it should after this.  Thank you again for solving this frustrating problem.

---

