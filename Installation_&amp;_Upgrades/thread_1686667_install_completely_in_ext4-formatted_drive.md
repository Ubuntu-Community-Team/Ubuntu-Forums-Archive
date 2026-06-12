---
title: "install completely in ext4-formatted drive"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by ak4allz on 2011-02-12
here is my problem. i want to completely install kubuntu on a 8gb pendrive. i want to install in it completely, using the ext4 and i dont want the installation bring harm to my hdd (eg: the grub boot)..

once i boot the pendrive, i can use the linux and when i eject the drive, i can simply enter into windows without grub

i've done this before, but the grub is there and i cannot enter windows in my hdd. thanks :D

---

### Post by oldfred on 2011-02-12
Not sure if I understand. Have you installed it and grub went into your hard drive not the flash drive?

Or are you worried about it doing the above and you want to be sure that it does not happen.

If already installed you have to reinstall grub to the external flash drive and install a windows boot loader to the internal drive.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


If installing, many recommend disconnecting the internal drive so grub will not even see it. Others suggest using the manual partitioning/manual install.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

See post by C.S.Cameron to answer same question:
[http://ubuntuforums.org/showthread.php?t=1686528](http://ubuntuforums.org/showthread.php?t=1686528)

---

### Post by jerrrys on 2011-02-12
you want a 100% guarantee not to effect your HDD?   just unplug it

---

### Post by ak4allz on 2011-02-13
thanks mate, looks like i only have to remove the HDD if i don't want any further skill to be executed... :D

---

