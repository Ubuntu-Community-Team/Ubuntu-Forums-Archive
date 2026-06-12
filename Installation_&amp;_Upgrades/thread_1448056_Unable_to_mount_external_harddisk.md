---
title: "Unable to mount external harddisk"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by peter_kint on 2010-04-06
Hello,
Ubuntu refuses to recognize/mount my external harddisk (Western Digital 500GB).
This happened after installing Ubuntu 10.04lucid (before I was on 9.10 and everything went well).

As a linux-newbie, I searched forums and tried all kinds of things with gparted, parted magic boot-CD, system rescue CD, and so on ...

I formatted the external harddisk to FAT-32 (I want to keep dual-booting with Windows Vista).

No matter what I try: either he **doesn't regognize the disk** or  he **refuses to mount** it (like now: error message after logging in + Disk Utility recognizes but refuses to mount it).

Disk Utility says: **Error mounting: mount: /dev/sdf1 is not a valid block device**

Any ideas (please include code/specifics for this linux-dummy) would be greatly appreciated.
P.

---

### Post by mikewhatever on 2010-04-06
You can try checking its file system with the following command:

sudo fsck.vfat -y -v /dev/sdf1

Fat32 is ok for basic usage, but you'd probably be better off with ntfs.

---

### Post by peter_kint on 2010-04-06
> **mikewhatever said:**
> You can try checking its file system with the following command:

sudo fsck.vfat -y -v /dev/sdf1

Fat32 is ok for basic usage, but you'd probably be better off with ntfs.

Thx for replying. Here is what he says:
[INDENT]```
pepe@pepe-desktop:~$ sudo fsck.vfat -y -v /dev/sdf1
dosfsck 3.0.7 (24 Dec 2009)
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
open: No such device or address
pepe@pepe-desktop:~$ 
```
[/INDENT]**Does this mean he actually recognizes the disk but refuses to mount/open it?**

About NTFS: I'm going to try it but from what I've read I thought it was going to give problems for Linux/Ubuntu to recognize/read/write the disk...

Thx again for ur time.
peter

---

### Post by mikewhatever on 2010-04-06
No, Ubuntu, and other modern Linux distros, have no problem with ntfs. I don't think the command did anything because /dev/sdf1 doesn't seem to exist. Try running *sudo fdisk -l* to find out the device name.

---

### Post by dino99 on 2010-04-06
goto system --admin --mountManager and check that you have rights to mount a device (admin by default, so change with user)

---

### Post by peter_kint on 2010-04-06
> **mikewhatever said:**
> No, Ubuntu, and other modern Linux distros, has no problem with ntfs. I don't think the command did anything because /dev/sdf1 doesn't seem to exist. Try running *sudo fdisk -l* to find out the device name.

Here is the output. The external HD doesn't seem to be listed...
pepe@pepe-desktop:~$ sudo fdisk -l

[INDENT]```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c155a3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8858    71145158+   7  HPFS/NTFS
/dev/sda4            8858       38913   241421153    5  Extended
/dev/sda5            8858       38369   237051472+  83  Linux
/dev/sda6           38370       38913     4369648+  82  Linux swap / Solaris
pepe@pepe-desktop:~$ 

```
[/INDENT]This is what I tried before reading your reply:
_1. Formatting the whole **drive** with disk utility (Master Boot Record)_
Error creating partition table: helper exited with exit code 1: cannot open /dev/sdf: No such device or address

_2. Formatting the** Volume** with disk utility_
Error creating file system: helper exited with exit code 1: cannot open /dev/sdf1: No such device or address

[U]3. GParted doesnt even find/list the HD

4. Log out
[/U]
_5. Boot with _**_SystemRescueCD (_**_with GParted on it_[B]_) _
[/B]He seemingly formats it to NTFS . (says ok)

_6. Log in again_
same error message

Peter.

---

### Post by peter_kint on 2010-04-06
> **dino99 said:**
> goto system --admin --mountManager and check that you have rights to mount a device (admin by default, so change with user)

Hi,
This seems to be a cool program, I wasn't aware of it.


[LIST=1]
[*]I can see the external HD in the display and it's name seems to be 'sdf', but when I     select it, the options (to mount it) are grayed out.
[*]I can't find the menu option to find out if I have the proper rights.
[*]I fiddled around a bit and I got this as Configuration File Preview:
[/LIST]
  p, li { white-space: pre-wrap; }  [INDENT]Device: /dev/sr0
Mount point: [COLOR=#FF0000]Unknown[/COLOR]
File system: udf,iso9660
Options: defaults
Dump flag: 0
Fsck value: 0
Device: /dev/fd0
Mount point: /media/floppy0
File system: vfat
Options: noauto
Dump flag: 0
Fsck value: 0
Device: UUID=ec6dc15a-0099-4e77-b663-def4bcba0fed
Mount point: swap
File system: swap
Options: sw
Dump flag: 0
Fsck value: 0
Device: UUID=b098c7f3-9cb1-4422-81cb-2f6cf2292e00
Mount point: /
File system: ext4
Options: defaults
Dump flag: 0
Fsck value: 1
Device: UUID=3C08E6CB08E682EE
Mount point: [COLOR=#FF0000]Unknown[/COLOR]
File system: ntfs-3g
Options: defaults
Dump flag: 0
Fsck value: 0
[/INDENT]Thanks for replying,
Peter

---

### Post by peter_kint on 2010-04-06
> **dino99 said:**
> goto system --admin --mountManager and check that you have rights to mount a device (admin by default, so change with user)

My* other* partitions on the* internal* HD (Windows + Linux) give the information:[INDENT]**Who can mount the partition? Only Administrator**
[/INDENT]The external HD , however, does not give a similar information-pane.

Peter

---

### Post by peter_kint on 2010-04-07
I installed everything again, from scratch: same problem.
Peter

---

### Post by vanadium on 2010-04-07
The problem is that your external harddisk did not show up in the output of "sudo fdisk -l". Was it plugged in when you ran the command?

Besides, it might be unwise to install, as a linux-newbie, an Ubuntu version that is not yet ready. Leave that to testers.

---

### Post by peter_kint on 2010-04-07
> **vanadium said:**
> The problem is that your external harddisk did not show up in the output of "sudo fdisk -l". Was it plugged in when you ran the command?

Besides, it might be unwise to install, as a linux-newbie, an Ubuntu version that is not yet ready. Leave that to testers.

Just to be sure, I do it again:[INDENT]peter@peter-desktop:~$ sudo fdisk -l
[sudo] password for peter: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c155a3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21096   169445228    7  HPFS/NTFS
/dev/sda2           21096       38914   143123456+   5  Extended
/dev/sda5           21096       38185   137269248   83  Linux
/dev/sda6           38185       38914     5853184   82  Linux swap / Solaris
[/INDENT]It's not there...

About the Ubuntu-version:
1. you are absolutely right of course, but I wanted a distro with texlive2009 included (I need 2009 to integrate tikz features properly). It took me weeks to get texlive2009 working together with Lyx in ubuntu9.
2. maybe my problem is also a test for the new version?

Thx for replying,
Peter

---

### Post by vanadium on 2010-04-07
A drive not showing up in "sudo fdisk -l" indicates the system just does not see it at all. Frequently, this indicates hardware issues, from a loose connection to a broken hard drive. Since yours worked fine with Ubuntu 9.10, it might be an Ubuntu 10.4 issue. You could boot a live session of a 9.10 CD to check whether the drive is still being seen ("sudo fdisk -l") from Ubuntu 9.10.

---

