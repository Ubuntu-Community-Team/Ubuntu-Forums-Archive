---
title: "Clean install 12.04 FSCK runs for 10 minutes every boot."
date: 2012-09-24
forum: Installation &amp; Upgrades
---

### Post by saphil on 2012-09-24
This is not what I was used to before.  It used to be fsck did a disk check every 30 boots, which is usual.  /var/log/bootlog:

```
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda1: clean, 453820/2445984 files, 2995189/9764864 blocks
found 132432056320 bytes used err is 0
total csum bytes: 128195324
total tree bytes: 1144139776
total fs tree bytes: 855859200
btree space waste bytes: 310435099
file data blocks allocated: 711485284352
 referenced 119848607744
Btrfs Btrfs v0.19
 * Starting mDNS/DNS-SD daemonESC[154G[ OK ]
 * Starting network connection managerESC[154G[ OK ]

```

My filesystems are as follows from /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=97a64352-ab34-48a7-8557-2484252e4ef3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=ace16697-dc8f-45eb-a7be-cd2a4d8ad8e2 /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda2 during installation
UUID=bec66462-da69-4c55-8d76-15579dcfef43 none            swap    sw              0       0

```

It is not checking the larger btrfs /home partition, for which I am thankful, but I do not know why it has to check every time it starts.  Does this mean it is finding a bad partition it just doesn't want to tell me about, or if it does really want to tell me, then where is it logging the info?

---

