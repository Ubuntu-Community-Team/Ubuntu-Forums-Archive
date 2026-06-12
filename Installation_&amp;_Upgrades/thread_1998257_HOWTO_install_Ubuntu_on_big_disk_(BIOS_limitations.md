---
title: "HOWTO: install Ubuntu on big disk (BIOS limitations)"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2012-06-06
[size=3][COLOR="Red"][B]This HOWTO has been moved to the Wiki - [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
This thread is now in use for discussion about the HOWTO only!![/B][/COLOR][/size]


When you reboot after installing **Ubuntu on a big disk**, you may get a **boot error (eg "GRUB rescue>" prompt). **

This situation may be the result of various problems.

Most can be easily solved by reinstalling GRUB (via [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") for example).
Some other may be linked to BIOS limits on **big disks (>100GB)**. In this case you may need to:
1) either **use the "ata disk" option of GRUB** (in Boot-Repair this option is in Advanced options -> "GRUB options" tab)
[IMG]http://img4.hostingpics.net/pics/421549outofdisk.png[/IMG]
2) **or (if the "ata disk" option was not enough) create/move the /boot partition** (or the / partition which contains the /boot partition) at the start of the disk (generally **inside the first 137GB of the disk**).
To perform this, you will need to:
- first repartition your disk in order to create a 1Go free disk space in the first 137GB of the disk. I recommend you reduce/move Windows partitions via Windows tools; other partitions can be handled perfectly via [gParted]("https://sourceforge.net/projects/gparted/files/gparted-live-stable/").
- then simply run Boot-Repair, update it, click "Advanced options" -> "GRUB location" tab, select the "Separate /boot partition: sdaX" option (sdaX must be your new 1Go partition) to setup your Ubuntu so that it uses this new partition.

This thread's aim is to guide users, and group informations and experiences about the last case: **BIOS reading limits.**


Here is a **user case:**
- a user who could not boot because his system (/) partition'end was too far from the beginning of the disk: [http://paste.ubuntu.com/1007972](http://paste.ubuntu.com/1007972)
- he fixed the problem by creating a /boot partition as close as possible from the beginning of the disk: [http://paste.ubuntu.com/1026868](http://paste.ubuntu.com/1026868)

In this example, the BIOS could not read partitions that are not included in the first 174GB of the disk.

There may be other kind of limitations depending of the BIOSes. Any feedback is welcome! :)

---

### Post by oldfred on 2012-06-06
Some old BIOS had a limit of booting from the first 137GB, so a separate boot or the entire / (root) had to be inside the 137GB limit. The rest of a drive could be used for /home or data. Most often where users add a newer large hard drive to an old system.

We are seeing similar issues with some new systems. I think it is a BIOS setting or settings, but cannot confirm. Generally with new drives LBA, large or other setting should be used in BIOS not IDE or RAID. Often the new AHCI is suggested and works with Linux, but will not work with XP. Windows 7 needs a driver installed before changing BIOS to AHCI.

There was (is?) a bug in grub2 where very large (1TB or more) / (root) partitions had issues also. So a default install to a 1 or 2TB drive often would not boot. Either smaller / (root) and separate /home or data partitions or a separate /boot work. I normally suggest smaller / of 25GB (boot files closer together on drive but still room as install will use 5 to 7GB) and separate /home and/or  additional data partitions.

---

### Post by YannBuntu on 2012-06-06
Hi Fred, thanks for your comment. (remark: instead of "1GB or more" you meant "1TB or more" i suppose)
I wanted to show you this new user-case (post#1) because:
- the limit of this BIOS is not the usual 137GB, but more (the /boot is located from 152GB to 154GB)
- the /boot is logical (in another thread we were wondering if the /boot had to be primary or not)

---

### Post by oldfred on 2012-06-06
Fixed 1GB entry incase someone does not read rest of thread.

I would not think /boot has to be primary. Linux has always worked from logicals. 

Some systems seem to have this issue and I have not seen one easy fix. Sometimes BIOS, sometimes just location on drive or / or /boot partition size.

---

### Post by YannBuntu on 2012-06-12
added the "ata disk" suggestion in the 1st post. It doesn't always work, but i think it's worth trying it before moving the /boot.

---

### Post by YannBuntu on 2012-06-13
Added details on **how to create & use a separate /boot** in post#1.
Also removed "dualboot" from the title because this problem can also happen with single OS on big disk.

Here are also details about the **"ATA option"** (which i gave to Drs but i think it can be useful for you Fred too ;) ):
this option in Boot-Repair adds the --disk-module=ata parameter to grub-install.
Eg it will do:
sudo grub-install **--disk-module=ata** /dev/sda

To reverse it, you just need to reinstall GRUB without ticking this option.
Eg this will do:
sudo grub-install /dev/sda

I don't know:
- how to see in the BootInfoSummary if GRUB has been installed with or without this module.
- what this module does exactly

I know:
- in the BootInfo created by Boot-Repair you can see if the user has activated the option or not.
- that this option generally solves "GRUB rescue" or "out-of-memory" errors on big disks, generally ATA disks but not necessarily ATA disks. Here is an example when it worked on a non-ATA disk: [http://paste.ubuntu.com/1024025/](http://paste.ubuntu.com/1024025/)

---

### Post by oldfred on 2012-06-13
I think on newer systems it is the IDE setting in BIOS, but have not had consistency in suggesting changing to LBA, large or whatever BIOS offers. Also changing to AHCI if not using XP seems to work. Several users have reported the BIOS change from IDE worked. 

But I have had exceptions where someone said changing to IDE fixed boot issue, but may have been something else.

But it also just may be buggy BIOS.

History of BIOS and IDE limits
[http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html](http://tldp.org/HOWTO/Large-Disk-HOWTO-4.html)

Some quotes from old threads:

> It was in the BIOS. Under Onboard Devices Settings, the SATA Mode was set to SATA. I changed it to AHCI. Then another  showed up in the BIOS that stated "Change the AHCI DID for Linux to Enabled. I booted to win7 and it loaded some new drivers. I booted to Gpart and glory be there were my hard drives.

Change SATA controller mode from AHCI to Compatibility (AHCI should be ok for Vista/7 & Linux), XP may not have AHCI driver.
[http://ubuntuforums.org/showthread.php?t=1694750&page=8](http://ubuntuforums.org/showthread.php?t=1694750&page=8) post #79
Standard BIOS Settings -> [drive you want to change] -> IDE Access -> “Large”, did the trick. 

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

Oldfred was right on, it was the SATA Native IDE setting that hosed Grub. I had to set the OnChip SATA Type to AHCI in order to boot using Grub. As for the OnChip SATA Port 4/5 Type setting it doesn't have any affect on Grub, it can be set to IDE or as SATA Type. My MB BIOS doesn't have a Compatibility or LBA setting so I have to find the AHCI XP drivers if I want to Multi-Boot XP and Ubuntu.


---

### Post by YannBuntu on 2012-06-13
Thanks for the links!

Please could you change the title of this thread to:
**HOWTO: install Ubuntu on big disk (BIOS limitations)**
(because the BIOS limit problem mostly happen with dualboot, but can also happen with single OS on big disk)

---

### Post by YannBuntu on 2012-07-05
Memo:
for such BIOS limit problem, error message at reboot can be:

**"Error: unknown file system"**

or

**error: Out of disk.**

or

**Grub rescue>**


grub-install reports no error.

---

### Post by Malswon on 2012-07-05
AHH! D*** it! I found this tread after trying all sorts of /mnt grub-installs and even the boot repair disc... but the ata option went unchecked. I just started a re-installation, and now have to wait.  I will probably encounter the same error, and will have to try this fix.. but it makes sense, I think it will work. thank you.

---

### Post by Malswon on 2012-07-05
> **YannBuntu said:**
> Memo:
for such BIOS limit problem, error message at reboot can be:
**"Error: unknown file system"**
or
**error: Out of disk.**
or
**Grub rescue>**
grub-install reports no error.

I Did the boot repair, ATA thing.
[http://paste.ubuntu.com/1077144/]("http://http://paste.ubuntu.com/1077144/")

Now I get this:

error: no device connected.
error: no device connected.
error: no such device: bpd18ca2-bdca-4991-9725-61449940e46c.
grub rescue>

I don't know what to do..


EDIT: Please help.

---

### Post by YannBuntu on 2012-07-06
Now please try creating a /boot partition as described in [post#1]("http://ubuntuforums.org/showpost.php?p=12003697&postcount=1").

---

### Post by YannBuntu on 2012-07-06
Just added an automatic detection of this problem in Boot-Repair:
[http://ubuntuforums.org/showpost.php?p=12080780&postcount=482](http://ubuntuforums.org/showpost.php?p=12080780&postcount=482)

---

### Post by YannBuntu on 2012-07-07
Here is a case where the BIOS can't read partitions ending after **119GB** only:
[http://ubuntuforums.org/showpost.php?p=12082298&postcount=487](http://ubuntuforums.org/showpost.php?p=12082298&postcount=487)

---

### Post by YannBuntu on 2012-07-11
I have just seen a case where this problem appeared when switching from GRUB Legacy to GRUB2. (in French: [http://forum.ubuntu-fr.org/viewtopic.php?id=958511](http://forum.ubuntu-fr.org/viewtopic.php?id=958511) )

So there may be a problem with GRUB2.

---

### Post by YannBuntu on 2012-07-16
Hello
I just moved this tutorial on the WIKI: [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)

And created another tutorial dedicated to the creation of a separate /boot partition: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

---

