---
title: "upgraging from 20.04 to 22.04"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2022-08-13
Hello fellow Ubunters :D. I am just wondering if this can really be fixed or if I should erase my Ubuntu partition. A few hours ago I tried to upgrade from 20.04 to 22.04. Everything went just fine until restart and I read this:  [1.495568] [ end kernel panic_ not syncing: VFS: unable to mount root fs on unknown block (0,0) ]. Recovery mode does not help. 
Thanks for any tip. 

C. Naud

---

### Post by Impavidus on 2022-08-13
Upgrades that have gone wrong can be very hard to fix. On very rare occasions the first thing you try works, but in most cases it's days work. I wouldn't try.

---

### Post by christon74 on 2022-08-14
Thank you ImpavidusO:). So here is what I have already done. I have deleted the Ubuntu partition (sdb1). I have downloaded the latest version of Ubuntu (22.04 LTS) on a memory stick. Is it possible to use KDE partition manager to reinstall Ubuntu. Prior to the failed upgrade, my Fujitsu-Seimens Esprimo  E 5731 was on dual boot (LinuxMint/ Ubuntu). Thanks;)

---

### Post by Impavidus on 2022-08-14
If you deleted the Ubuntu partition, you can create a new one using kde partition manager or gparted or whatever is included on your live disk. But you don't really have to delete the old partition. Then start the installer. It will ask how you want to install it: wipe the drive and install Ubuntu, alongside an existing system, something else/manual. Go for something else/manual. Tell the installer to use the partition you already have, mountpoint / (root) and select the checkbox for formatting that partition.

---

### Post by christon74 on 2022-08-14
Thanks;)

---

### Post by mIk3_08 on 2022-08-15
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

