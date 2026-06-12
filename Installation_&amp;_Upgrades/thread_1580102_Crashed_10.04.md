---
title: "Crashed 10.04"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by tock on 2010-09-22
It doesn't matter if I use recovery mode or normal boot.  It tries to mount the system and says failed then runs BusyBox v1.13.3 and gets to usbhid 2-4.3:1.1: couldn't find an input interrupt endpoint.  It just sits there after that with the cursor blinking but no prompt.  I used a live cd and can see the partitions so the drive is at least accessible.  I used test disk and it didn't find any issues other then no primary boot partition.  I assume thats because I'm using grub and dual booting?  The windows partition is working but its also on a different drive.  Its finding the usb mouse and keyboard.  Thats the only 2 usb devices I have plugged in at this point.  Any way to recover my system?

Thank you in advance

---

### Post by mikewhatever on 2010-09-22
No primary partition is a problem, as you must have at least one. You should provide more info on what exactly happened, and post the output of **sudo fdisk -l** .

---

### Post by tock on 2010-09-23
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57c757c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       60801   457667752+   f  W95 Ext'd (LBA)
/dev/sda5            3825       60801   457667721    7  HPFS/NTFS

Disk /dev/sdb: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e044e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1275    10241406    7  HPFS/NTFS
/dev/sdb2            1276        9421    65432745    5  Extended
/dev/sdb5            1276        8570    58597056   83  Linux
/dev/sdb6            8571        9421     6835626   82  Linux swap / Solaris

```

I've been working on getting mts files from my hd camcorder to play /convert.  I've installed the svn version of mplayer and ffmeg using the instructions off of the forum.  Also tried installing the latest Kdenlive from their  repositories.  Started having problems with firefox crashing then it got where it wouldn't start at all.  I did a reinstall of firefox and it started working again.  That was the last time I have been able to load ubuntu.  It shut down ok but now it stops at the above screen.  It will give me a prompt if I hit the enter key but it is very limited on the amount of commands I can use.  The drive seems to be working, I have a separate partition on that drive that is accessible in windows.  

Thanks for taking the time to help!

---

### Post by mikewhatever on 2010-09-24
Have you tried checking the Linnux partition for errors?

```
sudo fsck -yv /dev/sdb5
```

Run that from the live cd and post the output.

---

### Post by tock on 2010-09-24
```
/dev/sdb5: recovering journal
Clearing orphaned inode 917 (uid=1000, gid=1000, mode=0100600, size=464)
Clearing orphaned inode 916 (uid=1000, gid=1000, mode=0100600, size=88)
Clearing orphaned inode 915 (uid=1000, gid=1000, mode=0100600, size=597)
Clearing orphaned inode 149140 (uid=0, gid=0, mode=0100644, size=109344)
Clearing orphaned inode 864 (uid=0, gid=0, mode=0100600, size=960)
Clearing orphaned inode 863 (uid=0, gid=0, mode=0100600, size=5552)
Clearing orphaned inode 1177560 (uid=0, gid=0, mode=0100644, size=722636)
Clearing orphaned inode 131627 (uid=0, gid=0, mode=0100644, size=6502252)
Clearing orphaned inode 858 (uid=0, gid=0, mode=0100600, size=16)
Clearing orphaned inode 857 (uid=0, gid=0, mode=0100600, size=95)
Clearing orphaned inode 198421 (uid=0, gid=0, mode=0100644, size=109872)
Clearing orphaned inode 262049 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 262042 (uid=1000, gid=1000, mode=0100600, size=312)
Clearing orphaned inode 262066 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 262065 (uid=1000, gid=1000, mode=0100600, size=6724)
Clearing orphaned inode 111 (uid=113, gid=121, mode=0100600, size=0)
Clearing orphaned inode 586 (uid=113, gid=121, mode=0100600, size=0)
Clearing orphaned inode 557 (uid=113, gid=121, mode=0100600, size=0)
Clearing orphaned inode 536 (uid=113, gid=121, mode=0100600, size=0)
Clearing orphaned inode 120 (uid=113, gid=121, mode=0100600, size=0)
/dev/sdb5: clean, 266932/3662848 files, 5614758/14649264 blocks

```

---

### Post by tock on 2010-09-24
That got it working again.  Anything I should do from here to make sure the system is healthy?

---

