---
title: "update-initramfs.conf not found"
date: 2017-02-07
forum: Installation &amp; Upgrades
---

### Post by errolflynn on 2017-02-07
[B][SIZE=4]I was hit with the following error after installing Ubuntu Studio:
```
[URL="http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell"]
ALERT! /dev/disk/by-uuid/xxxxxxxxx does not exist. Dropping to a shell[/URL]
```[/SIZE][/B]



[SIZE=4]This led me to the following forum post:
[http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell](http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell)

So I tried to run the commands:
[/SIZE]```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub
reboot

```[SIZE=4]
However, upon running ```
update-initramfs -u
```, I was hit with the following error:
```
/usr/sbin/update-initramfs: 4: /etc/initramfs-tools/update-initramfs.conf: 0: not found
```

I have searched for this file on the mounted system, and it looks like this:
[/SIZE]```
#
# Reserved protocols.
#
0 unspec
1 redirect
...
42 babel

#
# Used by me for gated
#
254 gated/aggr
...
246 gated/default

```
[SIZE=4]
The update-initramfs.conf on the live USB used for install looks like this:
[/SIZE]```
#
# Configuration file for update-initramfs(8)
#

#
# update_initramfs [ yes | all | no ]
#
# Default is yes
# If set to all update-initramfs will update all initramfs
# If set to no disables any update to initramfs beside kernel upgrade

update_initramfs=yes

#
# backup_initramfs [ yes | no ]
# 
# Default is no
# If set to no leaves no .bak backup files.

backup_initramfs=no

```
[SIZE=4]
Unfortunately, I don't have a working knowledge of initramfs. As for the initial alert, the UUID of the hard drive partition is correct as determined by ```
sudo blkid
```[/SIZE]

---

