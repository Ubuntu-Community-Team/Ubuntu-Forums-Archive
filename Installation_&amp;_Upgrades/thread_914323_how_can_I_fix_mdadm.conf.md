---
title: "how can I fix mdadm.conf??"
date: 2008-09-08
forum: Installation &amp; Upgrades
---

### Post by sholdowa on 2008-09-08
OK, I run a server which boots off /dev/md0, a soft raid partition. I also use an initramfs when booting. Every time that a new kernel is installed and the initramfs image is rebult, the etc/mdadm/mdadm.conf file is corrupted and I have to replace it before the array is found.

A working mdadm.conf under the image looks like

[INDENT]ARRAY /dev/md1 level=raid5 num-devices=4 UUID=e60fd168:e0b840b9:74e89b5b:db916dde
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=1936d17e:0c90680f:aa0bb4fa:0c32cc87
[/INDENT]

which is replaced every time with

[INDENT]UUID=e60fd168:e0b840b9:74e89b5b:db916dde
UUID=1936d17e:0c90680f:aa0bb4fa:0c32cc87
[/INDENT]

The latter hangs. To fix this requires me to a) remember to fix it, and b) to have to use gzip / cpio to unpack and repack the image.

How do I stop mkinitramfs screwing this up every time I boot??

---

