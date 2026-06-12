---
title: "Ubuntu OS no longer shows on OS selection page at boot"
date: 2017-05-03
forum: Installation &amp; Upgrades
---

### Post by old.jim on 2017-05-03
Hi, I had both Ubuntu 12.04 and Windows XP on two seperate partitions on my Dell Latitude D-620 hard drive. The XP OS was on a FAT 32 file system, but I wanted it on a NTFS system, so I created a 3rd partition on some unused space, formatted it as NTFS, and installed another copy of XP on that partition. Now, when I boot the computer, it only lists the two XP operating systems on the OS choice page during boot, and not Ubuntu. I think Ubuntu is still on the partition and usable, but I don't know how to access it. Can somebody please tell me how to get it back on the OS choice list. Thank you much.

---

### Post by oldfred on 2017-05-03
May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Impavidus on 2017-05-04
Sounds like Windows took over control over boot. Boot repair, as linked by oldfred, can probably fix this. First create the summary report to confirm.

Please note that both Windows XP and Ubuntu 12.04 are no longer supported. In case of Ubuntu, moving to a supported release is free. So maybe you want to create a live disk of a more recent Ubuntu release, use that to access your hard drive and make backups, then install a recent Ubuntu in the old Ubuntu partition. It should pick up the Windows XP systems automatically and take control over boot.

---

### Post by old.jim on 2017-05-20
Thanks for your help. I ended up upgrading to 16.04, and yes, your right, it did take over boot, and also lists XP for boot.

---

