---
title: "Can't boot Xubuntu"
date: 2018-07-16
forum: Installation &amp; Upgrades
---

### Post by zentsugo on 2018-07-16
Hi I can't boot Xubuntu after installing it on my HDD it says an error about unknown file system in grub, I was trying to dual boot Windows 10 and Xubuntu and Windows 10 is already installed in my SSD, so I went into Xubuntu Live USB and installed boot repair but each time I'm repairing it it freezes the whole screen I know it can take time but, I've waited for almost 2 hours and I'm restarting it, also I made a report log file here if anyone can help me thanks.
[http://paste.ubuntu.com/p/2JkcXdX4nG/](http://paste.ubuntu.com/p/2JkcXdX4nG/)

I'm in UEFI, I have a laptop.

---

### Post by ajgreeny on 2018-07-16
I am by no means an expert in this but you appear, according to the info I copied below, to have one main large 1TB disk using the legacy msdos MBR partitioning but you say you installed Xubuntu in UEFI mode.
This is a big problem as Windows 10, if pre-installed, will have been UEFI and that is impossible using MBR partitioning. Both OSs must use the same mode, MBR or UEFI for a successful dual boot.
Can you boot Windows still or is that also a problem for you?
What hardware do you use; saying it is a laptop and you use UEFI is not enough detail.
```

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd9fa2484

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048 1881845759 1881843712 897.3G  7 HPFS/NTFS/exFAT
/dev/sda2       1881845760 1889845247    7999488   3.8G 82 Linux swap / Solaris
/dev/sda3  *    1889845248 1891115007    1269760   620M ef EFI (FAT-12/16/32)
/dev/sda4       1891115008 1953523711   62408704  29.8G 83 Linux


Disk /dev/sdb: 3.8 GiB, 4009754624 bytes, 7831552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AF57C163-9A43-42EE-BC05-BF6755B004D2

Device     Start     End Sectors  Size Type
/dev/sdb1   2048 7831518 7829471  3.8G Microsoft basic data
```
I assume this 4GB sdb is a live disk used for installlation?

---

### Post by zentsugo on 2018-07-17
Hi, yes that 4gb is the Xubuntu Live USB, I got a 1TB HDD that I shrink in 2 parts, the first one is where are my files the second one is where Xubuntu is supposed to be installed so the free space, I got an SSD of 128gb that isn't detected/recognized in Xubuntu Live USB where Windows is installed.
Somehow now the boot repair worked on Xubuntu Live USB but it doens't want to boot on Xubuntu and it says problem with BCD when I boot Xubuntu with Secure Boot enabled uh

---

### Post by zentsugo on 2018-07-17
Here are logs after the boot repair
[http://paste.ubuntu.com/p/P3GNHrHQ6F/](http://paste.ubuntu.com/p/P3GNHrHQ6F/)

---

