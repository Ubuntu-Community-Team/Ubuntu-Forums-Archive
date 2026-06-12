---
title: "[GUTSY] Partition problem while &amp; after installing"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by `ixM on 2008-01-19
Hi everyone,

I'm requiring your help for a very annoying problem.

Here's me story :p 

I have bought a new 400 GB HDD and I want to use Ubuntu Gutsy in dual boot with Windows XP.

I've installed XP on a 100 GB NTFS partition.

Then I tried to install Ubuntu.
[LIST]
[*]100 GB - NTFS - Primary (/windows)
[*]100 GB - FAT32 - Primary (/music)
[*]135 GB - FAT32 - Logical (/data)
[*]30 GB - EXT3 - Primary (/)
[*]30 GB - EXT3 - Logical (/home)
[*]5 GB - Swap
[/LIST]
That's what I wanted but it tells me that it was impossible to mount /windows, /music and /data so just set "do not use it" as mount point.

But when the installation is completed and the computer is restarted, if I try to run Ubuntu, I've got an error message, immediately after it begins to start :
"ERROR 17: Cannot mount selected partition
Press any key to continue..._"

I've already tried several times to install it, tried to burn a new cd but it happens every time.

Can someone please tell me what I should to in order to fix that ?

Thank you,
Regards,
ixM`

---

### Post by louieb on 2008-01-19
Do you have internet with the Live CD?
If so please post your partition table. to do that
Open Applications>Accessories>Terminal
```
[FONT=Fixedsys][FONT=Arial]sudo fdisk -l[/FONT] [/FONT]
```(lowercase L)

Copy and paste the output in your next post.

---

### Post by `ixM on 2008-01-20
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       12158    97659103+   7  HPFS/NTFS
/dev/hdc2           12159       44996   263771235    5  Extended
/dev/hdc3           44997       48641    29278462+  83  Linux
/dev/hdc5           12159       24316    97659103+   b  W95 FAT32
/dev/hdc6           24317       27975    29390886   83  Linux
/dev/hdc7           27976       44388   131837391    b  W95 FAT32
/dev/hdc8           44389       44996     4883728+  82  Linux swap / Solaris

And since it took me about 10 minutes to start an old Live-CD, I'll try to use QtParted to set up everything before Installing. If it doesn't work, I'll post fdisk output here again.

What I've noticed is that QtParted tells me that hdc7 has no format and fdisk that it is FAT32 which is quite strange, isn't it ?

Thank you,
See you soon

---

### Post by `ixM on 2008-01-20
Ok, there's no change if I try to format with QtParted prior to install it. The partition table is still the same.

But I've noticed two things. I don't know if they have any interest but who knows ?

First, I can only do 1 change on the partition table with QtParted. After this change, nothing more can be done until I reboot the computer.

Then, when I've applied the change to the fat32 partition (displayed as unknown), it appears as fat32 while QtParted is working on the partition table but immediately afterwards it is displayed as unknown again.

Is this relevant ?

See you

---

### Post by louieb on 2008-01-20
Partition table looks fine. No overlapping partitions  Just wondering if your not running into some BIOS limit.  How old is this PC?
If you put your partitions in disk order   it looks like: 
```

/dev/hdc1 00001 12158 097659103+ 7 HPFS/NTFS
/dev/hdc2 12159 44996 263771235 5 Extended
/dev/hdc5 12159 24316 097659103+ b W95 FAT32
/dev/hdc6 24317 27975 029390886 83 Linux
/dev/hdc7 27976 44388 0131837391 b W95 FAT32
/dev/hdc8 44389 44996 0004883728+ 82 Linux swap / Solaris
/dev/hdc3 44997 48641 0029278462+ 83 Linux

```Which partition did mount as / (root)?   If you haven't tried hda6 already - I would try the install again with hda6 as / (root).

A BIOS limit is all I can think of thats giving you the type of problems you have described.

---

### Post by `ixM on 2008-01-20
Actually the first time I've tried. Both ext3 partition where logical partitions.

The last time I've tried, hdc3 was / (primary) and hdc6 was /home (logical).

But I'll try

---

