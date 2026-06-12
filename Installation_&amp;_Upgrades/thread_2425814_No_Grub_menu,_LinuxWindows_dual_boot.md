---
title: "No Grub menu, Linux/Windows dual boot"
date: 2019-08-30
forum: Installation &amp; Upgrades
---

### Post by colony11 on 2019-08-30
I can't see to boot into Linux anymore.

Summary: I accidentaly ran window recovery, restarted and when rebooting it went to grub rescue.
Used a live USB and ran boot-repair, now my machine boots straight to windows without a grub menu.
Here is the boot repair log.

[http://paste.ubuntu.com/p/HGrW7vmYzQ/](http://paste.ubuntu.com/p/HGrW7vmYzQ/)

---

### Post by Skaperen on 2019-08-30
did you have some other Linux on your 2nd hard drive?

---

### Post by oldfred on 2019-08-30
Classic Windows "bug". Windows since Windows 7 in BIOS mode rewrites partition table & conviently forgets to include your Linux partition. It probably was sda5, but it also renumbered swap to sda5. That is not important, but your data is still there & you just need to add partition table entry back again.

You show large gap in extended partition. Your Linux partition started a few sectors after the beginning of the extended & ended a few sectors before the start of swap. After restore you also need to reinstall grub.
```
/dev/sda3         210,554,878   475,406,335   264,851,458   5 Extended
/dev/sda5         435,165,184   475,406,335    40,241,152  82 Linux swap / Solaris
```

Just in case, you make a mistake keep a copy of current partitions on another drive.
       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt 

Many threads with details, either  testdisk or parted rescue should work.
      
 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

Use Boot-Repair's advanced mode to reinstall grub. Choose install after restored & drive.
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

