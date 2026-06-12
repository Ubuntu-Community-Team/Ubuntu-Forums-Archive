---
title: "How to convert ext4 to JFS"
date: 2014-10-09
forum: Installation &amp; Upgrades
---

### Post by Nguyen_Phi_Long on 2014-10-09
Dear supporters.
I already installed ubuntu 12.04.3 on my machine.
/dev/sda1  /boot/efi      EFI     200MB
/dev/sda2  /                 ext4    2Tb
/dev/sda3  not mount    JFS     1Tb
now, system operate well.
I would like to convert ext4 to JFS file sytem. it's mean /dev/sda2 is converted to JFS format.
I searched on google but I cannot see clear info for this.
Anybody please help me.
please give me your suggestion how to do that.

thank you so much.

---

### Post by kc1di on 2014-10-09
[Here's a page to a scrip]("http://www.linux-magazine.com/Online/Features/Converting-Filesystems-with-Fstransform")t that will transform the file system for you. (I've never used it so can't say how well it works)
only other way I know of to do what you want would be to do a complete new install. 
good Luck ;)
You may also want to read[ this page]("https://help.ubuntu.com/community/LinuxFilesystemsExplained") before deciding to convert.

---

### Post by oldfred on 2014-10-09
Generally ext4 is better for most uses.

[http://www.phoronix.com/scan.php?page=article&item=9way_linux317_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=9way_linux317_fs&num=1)

---

