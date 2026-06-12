---
title: "Want to install Windows on a LUKS-encrypted laptop"
date: 2024-01-27
forum: Installation &amp; Upgrades
---

### Post by mnealbarrett on 2024-01-27
I have a laptop with Ubuntu installed on it encrypted with LUKS. It is a sizeable SSD drive (about 500GB) with lots of free space. I would like to install Windows on it and dual-boot, but I do NOT want to reinstall my Ubuntu installation. Any ideas?

---

### Post by tea for one on 2024-01-27
> **mnealbarrett said:**
>  I would like to install Windows on it and dual-boot, but I do NOT want to reinstall my Ubuntu installation.
Why do you think that you would have to re-install Ubuntu?

---

### Post by ubfan1 on 2024-01-27
The conventional wisdom is that a Windows install will mess up an existing Ubuntu installation, but the last few times I reinstalled Windows 11 on a dual boot machine (with an existing Windows partition), there was no problem. No encryption was involved though.

---

### Post by tea for one on 2024-01-27
Installing Windows after Ubuntu will probably only affect grub.
Ubuntu will still be intact but the user will, undoubtedly, have to re-install grub via a live session.

All this assumes that we are dealing with UEFI installations rather than old-fashioned Legacy/mbr.

Hopefully, the OP will inform us about the version and status of their Ubuntu OS?

---

### Post by mnealbarrett on 2024-01-27
> **tea for one said:**
> Why do you think that you would have to re-install Ubuntu?

Because the installation is encrypted.  The Ubuntu installer can resize an existing installation, as long as it is not encrypted.The installer can't shrink an encrypted partition because it can't read the partition to shrink it.

---

### Post by MAFoElffen on 2024-01-27
I'm confused by your last statement.

It may help us if you post the output of this, posted withi CODE Tgas:
```

lsblk -e7 -o name,label,size,fstype,mountpoint,mdoel

```
That should show us what is there, and the current layout.

So your goal is to install Windows alongside of Your Ubuntu Install, and that existing install is LUKS, right?

---

### Post by tea for one on 2024-01-28
> **mnealbarrett said:**
> Because the installation is encrypted.  The Ubuntu installer can resize an existing installation, as long as it is not encrypted.The installer can't shrink an encrypted partition because it can't read the partition to shrink it.
Unintentionally, I think that I have misinterpreted your situation.

Reading between the lines, I get the impression that you do not have free space i.e. unallocated (as mentioned in post no. 1).
It appears that you have unused (i.e. potentially available) space within your encrypted volume?
Is that correct?

---

### Post by yancek on 2024-01-28
> The Ubuntu installer can resize an existing installation, as long as it is not encrypted 

You already have Ubuntu installed so how is that relevant since you are trying to install windows?  Do you mean the windows installer is incapable of this?  Not surprising but if what you have is Ubuntu using the entire disk, you can shrink a partition to create unallocated space by using a 'live' Linux system with the proper tools as explained in detail at the link below.

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

### Post by MAFoElffen on 2024-01-28
+1000 with both of you in Posts #7 & #8...

That is the why of the information requested in Post #6. If he had ran the Forums 'system-info' script, all that information would have been provided and there would be none of these 'guesses'. More info would be known. that is why I gave the script to the Forum. As a tool for you Members to use. To help the User, help you to help them.

Get very good backups of the content, that can be restored to newer, smaller partitions if needed.

The way I see that. He needs to shrink the LUKS container to provide room for Windows. That statement implies a lot of things for that to happen. It cannot be done online (needing tto be booted from an installer LiveUSB), and it has many steps to it that have to be done in order by the User, or it will fail. Open the container. Shrink the filesystem. Shrink the partition. Test it to ensure it is okay.

Windows can be installed to a disk that contains Ubuntu, that step doesn't matter that what exists on there is encrypted, by making room (unallocated space) for it to install to. Of course that will mess with the Grub2 boot loader. That will require remounting the drive from an installer LiveUSB (again) and fixing Grub2, after the Windows install is done.

But to make a sound recommendation, more information is needed from this User. Just saying.

---

### Post by l3modz on 2024-01-29
[ Do it ] reinstall 

> 
[1] Boot using Ubuntu latest USB Live Bootable.
[2] Save data on Ubuntu Operating system encrypted LUKS. fail ??? Using Login Ubuntu, plug in USB/HDD External.
[3] failed save data from USB Live Ubuntu OR others Distro, it normal. it Encrypted LUKS.
[4] use QParted USB Live USB Bootable. Create Windows Partition on partition 0, Linux Partition on partition 1.
[5] Install first Windows OS, install Antivirus, update antivirus.
[6] Install Ubuntu latest version, it will make selectable Bootable Dual OS that controled by Ubuntu.
[7] Download Boot Rescue Live USB Bootable for help you someday.

cheers. I just have mechine/PC Dual Boot Linux Fedora AND Ubuntu, handle boot by Ubuntu. ^_^ ^_^ ^_^

---

### Post by tea for one on 2024-01-30
Following a bit of research, it transpires that KDE Partition Manager can shrink LUKS encrypted volumes.
Surprisingly, Gparted lacks this option.

To experiment, I installed Ubuntu 23.10 with encryption on a separate disk.
Here we go:-

Boot into a live "Try Ubuntu" session of Ubuntu 23.10 (I did not have a Kubuntu iso)
Backup important data
Install KDE Partition Manager
```
sudo apt install partitionmanager
```
Open partitionmanager
Select disk with encrypted volume
Right click >luks2 > Unlock
Device > Refresh devices 
Right click > ubuntu-vg (visible in left pane)
Deactivate Volume Group
Refresh Devices
Right click > /dev/ubuntu-vg/ubuntu-lv (ext4) (visible in right pane)
Resize/move is now available
Adjust size and Apply

Confirmation details below
```
Command: e2fsck -f -y -v /dev/ubuntu-vg/ubuntu-lv 
Check file system on partition ‘/dev/ubuntu-vg/ubuntu-lv’: Success
Shrink partition ‘/dev/ubuntu-vg/ubuntu-lv’ from 71.46 GiB to 40.00 GiB: Success
```

---

### Post by MAFoElffen on 2024-01-30
So... That worked okay?

I just usually follow this guide: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

### Post by tea for one on 2024-01-30
> **MAFoElffen said:**
> So... That worked okay?
Yes, it did.
Having dipped my toe into the turbulent waters of encryption, I'm going to indulge myself this evening with an second libation of Old Speckled Hen ;)

---

### Post by #&amp;thj^% on 2024-01-30
> **tea for one said:**
> Yes, it did.
Having dipped my toe into the turbulent waters of encryption, I'm going to indulge myself this evening with an second libation of Old Speckled Hen ;)

+1
I think I dumped gparted at least 2 years ago, partitionmanager is just the beez kneez :)
```
apt policy partitionmanager gparted
partitionmanager:
  Installed: 23.08.4-0ubuntu1
  Candidate: 23.08.4-0ubuntu1
  Version table:
 *** 23.08.4-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status
gparted:
  Installed: (none)
  Candidate: 1.5.0-1
  Version table:
     1.5.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages

```

---

### Post by MAFoElffen on 2024-01-30
I'm going to look into that tonight.

Remember to share these things with me... I feel left out. LMAO!

---

### Post by #&amp;thj^% on 2024-01-30
LMAO How would I know you needed a share...

---

### Post by tea for one on 2024-01-30
> **MAFoElffen said:**
> I'm going to look into that tonight.
Remember to share these things with me... I feel left out. LMAO!
I tried this in the terminal:-
```
sudo sharewith -user MAFoElffen
sharewith not granted - Salmon fishing takes priority
```

---

### Post by MAFoElffen on 2024-01-30
> **tea for one said:**
> I tried this in the terminal:-
```
sudo sharewith -user MAFoElffen
sharewith not granted - Salmon fishing takes priority
```
LMFAO!!! Yes during Salmon Season! LOL

---

