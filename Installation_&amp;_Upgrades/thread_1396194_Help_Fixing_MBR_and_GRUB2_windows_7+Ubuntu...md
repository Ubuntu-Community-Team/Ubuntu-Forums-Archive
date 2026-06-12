---
title: "Help Fixing MBR and GRUB2 windows 7+Ubuntu.."
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by xccrev on 2010-02-01
Hello I have two hard drives one with ubuntu and one with windows 7.

I first was running ubuntu then added a larger hard drive and installed windows 7 on it.

I am wondering how to fix this. I tried using this tutorial [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

but it didn't work.

Here is my fdisk -l printout

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fc83750

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d2867a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       77826   625027072    7  HPFS/NTFS


Please try to give me some useful help I have tried numerous howtos and tutorials on the internet.

I am fairly new to linux but I do understand commandline and such.

Thanks

---

### Post by Leppie on 2010-02-01
could you please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by oldfred on 2010-02-02
Please run the script leppie suggested so we can better tell what is where.

Often when physically installing a new drive the grub device map is not updated. This may work, but script likely will tell more.

You could try:
```
sudo grub-mkdevicemap
sudo update-grub
```

---

