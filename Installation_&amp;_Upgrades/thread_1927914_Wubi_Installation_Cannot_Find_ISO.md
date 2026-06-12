---
title: "Wubi Installation Cannot Find ISO"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by Jeremini on 2012-02-19
Hello,

I am trying to install Ubuntu from Wubi for the first time.

When I used the regular installer, I got a message saying 

Gave up waiting for root device - Common problems are
-Boot args (cat/proc/cmdline)
 -Check rootdelay=(did the system wait long enough?)
 -Check root=(did the system wait for the right device?)
-Missing modules (cat/proc/modules; is/dev)
ALERT! /dev/disk/by-uuid/8c44-4dba does not exist. Dropping to a shell.

so I used the advice on the thread [http://ubuntuforums.org/showthread.php?t=1880031](http://ubuntuforums.org/showthread.php?t=1880031)

and put the installation ISO and the Wubi.exe file on my desktop before installing.

The installation works, but whenever I try to boot up Ubuntu I get the error:

[I]Could not find the iso /ubuntu/install/installation.iso  This could happen if the file system is not clean because of an  operating system crash, an interrupted boot process, an improper  shutdown, or unplugging of a removable device without first unmounting  or ejecting it. To fix this, simply reboot into windows, let it fully  start, log in, run 'chkdsk /r', then gracefully shut down and reboot  back into windows. After this you should be able to reboot again and  resume installation.

[/I]I tried using chkdsk /r but this did not cause any changes. There is a ~700 MB file called installation.iso at /ubuntu/install.

Reinstalling hasn't helped.


If you have any ideas, I would really appreciate it.  Also, please keep in mind that I'm new to this and have a low level of technical skill.

I'm trying to install Ubuntu version 11.10 off of Windows 7.   

Thanks again

---

### Post by Paddy Landau on 2012-02-19
Hello Jeremini,

First things first, uninstall WUBI to clear yourself back to a clean situation. Reboot.

I am not a great fan of WUBI because it does come with some restrictions and a greater level of instability than a native installation of Ubuntu.

Here's my recommendation: download the normal Ubuntu, burn it to CD or USB, and boot from that. Choose "Try Ubuntu" when prompted. Play around; does it work all right? If so, consider doing a native installation rather than WUBI.

However, if you really want to stick with WUBI, check that the ISO is valid ([check the MD5 sum]("https://help.ubuntu.com/community/UbuntuHashes")). If invalid, download it again. Then try to reinstall. See what happens.

---

### Post by Jeremini on 2012-02-19
I tried your advice.

I got Ubuntu to run off of my USB drive, but I cannot get it to install onto my hard drive.

The installation guide shows a step where the user gets to choose between "Install Ubuntu alongside Windows", "Replace Windows with Ubuntu", or "Something else".

I don't get that option.  Instead I am just pushed into the partition table, except all of the buttons, "New Partition Table", "New Partition", "Edit Partition", "Delete Partition" are grayed out.

If I try to continue, I get the error "No root file system defined"

I got the same problem with Ubuntu 11.10 and 10.04 LTS.

Another guy posted a video of the same problem on youtube if you want to know what I'm looking at.

[http://www.youtube.com/watch?v=l5cTNg0gs7A](http://www.youtube.com/watch?v=l5cTNg0gs7A)

Any ideas?

Thanks in advance

---

### Post by Paddy Landau on 2012-02-20
I have never seen that before. The comments mention RAID; do you use RAID?

If you can boot from your Live CD or USB, open a terminal, and enter the following command:
```
sudo parted --list
```Post the results here (between [noparse]```
[/noparse] and [noparse]
```[/noparse] please).

---

### Post by ottosykora on 2012-02-20
could it be that there are already 4 primary partitions on that machine?

Or more bad: they have already been changed to dynamic?

---

### Post by Jeremini on 2012-02-20
Here is the output from sudo parted --list

```

ubuntu@ubuntu:~$ sudo parted --list
Model: PNY USB 2.0 FD (scsi)
Disk /dev/sda: 8075MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  8075MB  8075MB  fat32


ubuntu@ubuntu:~$ 

```I built this computer about 6 months ago and installed windows 7 on it.  It should not have any partitions on it.  I am not using RAID (Had to look up what that is).

My computer has a single Seagate Barracuda ST31000524AS 1TB hard drive.

Thanks for your help

*Edit:  I just realized this looks like my USB Key, not my Hard Drive (8 GB).  How do I perform this command on my Hard Drive when Ubuntu is running off the USB Key?

---

### Post by Paddy Landau on 2012-02-20
Thank you for the listing.
> **Jeremini said:**
> It should not have any partitions on it.
Actually, it should have a partition. A drive must always have a partition. I know that very old operating systems would accept a partition-less drive, but that was many years ago.

If you installed Windows 7 from DVD, it would have created a partition when it loaded.

I see that it is showing your USB drive (because it shows FAT32). I am puzzled that it is not showing your main drive. Another puzzling item is that it shows the USB as /dev/sda. On my computer, when I boot off the USB, it is /dev/sdb; the built-in drive is /dev/sda.

I wonder if, for some reason, Ubuntu is not able to see the physical drive (in which case that would explain your errors).

Booting from your Live CD again, please try GParted (I think it will have the same result). Select your device from the top-right corner of GParted.

Having tried GParted, also try Disk Utility. Again, I think it will have the same result, but I'm really clutching at straws here.

> **ottosykora said:**
> Or more bad: they have already been changed to dynamic?
This is the new system that will take over partitioning, isn't it? Unfortunately, I know nothing about how this would work. Would that affect the results from parted? Could that explain the results that Jeremini had?

---

### Post by Jeremini on 2012-02-21
Neither GParted nor Disk Utility could "See" my Hard Drive.

I'm gonna see if I can get my hands on another hard drive.  Maybe that will solve my problem

Thanks for all your help

---

