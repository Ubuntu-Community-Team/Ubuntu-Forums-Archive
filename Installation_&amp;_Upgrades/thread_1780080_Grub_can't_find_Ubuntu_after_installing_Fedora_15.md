---
title: "Grub can't find Ubuntu after installing Fedora 15"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Terad on 2011-06-11
Hi,

after I've installed Fedora 15, Ubuntu is no longer visible in my Grub menu, which is 0.99 (and in "fedora-blue") instead of 1.99 now.
I tried some HOWTOs, like

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but I can't get my old Grub and Ubuntu back.


"sudo fdisk -l" gives me ```
Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06050604

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   115779583    57889760+  83  Linux
/dev/sdb2       146496796   156296384     4899794+   5  Extended
/dev/sdb3       115779584   146495487    15357952   83  Linux
/dev/sdb5       146496798   156296384     4899793+  82  Linux swap / Solaris
```

Sdb1 is where Ubuntu is installed, and sdb3 is where Fedora is installed.

Any ideas?

---

### Post by drs305 on 2011-06-11
Your Grub2 files should still be intact - you just have to 'correct' the MBR info. If you boot a Natty LiveCD and run grub-install it should point the MBR back to your Natty Grub files. At that point, it should boot Natty's Grub files. You'll have to see if it picks up Fedora, but there have been some posts within the past week about this.

From the Natty LiveCD:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdb
```

---

### Post by Terad on 2011-06-13
Worked, thanks a lot!

---

