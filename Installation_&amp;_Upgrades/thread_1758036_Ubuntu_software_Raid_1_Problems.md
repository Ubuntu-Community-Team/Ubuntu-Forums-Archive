---
title: "Ubuntu software Raid 1 Problems"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Thraxarious on 2011-05-14
I too am having this trouble. Doesn't seem to matter which version, every time I try to install Software raid on an Ubuntu server system, it blows up with this error. Seems I've had trouble for several versions.

```
mount: mounting /dev/disk/by-uuid/f35415ee-4c14-4eb1-995f-f19fbcd760c7 on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```


I've done it on Centos Fine, and followed the many different instructions I've seen for Ubuntu.
The only luck I've had was with bios raid, but I would much rather let Mdadm handle things.


My build:
ubuntu-10.04.2-server-amd64 CD install
AMD 1055T 6Core
4GB ram
Asus M4A88TD-M\USB3
2x 500gb SATA HDDs in AHCI mode.
2x ~475GB bootable Raid 1 Primary Ext4 Partitions for /
2x ~16GB Raid 1 for Swap (tried both primary and logical)

I install both as letting Ubuntu decide partitions for one drive, do the same for the other, and create a raid, and do them from scratch.

No dice, same problem. I've tried that one as logical and as primary too. No difference.

Something just doesn't like booting from a raid 1 Mirror. I've tried installing grub on both HDDs (sda1 + sdb1) 

I've tried several CDs, burned from several machines. Re-downloaded from Torrent and from the website. The DVD drives work since I purchased new DVD drives for both one workstation and the server. Things install fine under CentOS, software raid comes up.

I am able to install on a single drive in non raid mode, but...soon as I start putting K-raid partitions up, and /dev/md0... nope.

I'm really not sure why I have so much trouble with Ubuntu server.

---

### Post by Thraxarious on 2011-05-14
Okay, a bit more info.

I tried installing with a partition group that was split up a bit.

35G to /boot
25G to swap
the rest to /

That and letting it finish sync on /md0 and /md1 seemed to work. Does Grub have trouble booting to raid devices if they are too far down the drive in size or too large?

---

