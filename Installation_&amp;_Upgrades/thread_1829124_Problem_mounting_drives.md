---
title: "Problem mounting drives"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by Bewe on 2011-08-20
Hi!

I have a problem with mounting which seams kind of random, during bootup i get the following error included below (it always occurs when i do a "cold" boot, but only randomly when I do a reboot)

boot.log:

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 196990/19456000 files, 2176757/77815040 blocks
mount: /dev/sda1 already mounted or /media/Public busy
mount: according to mtab, /dev/sda1 is mounted on /
mountall: mount /media/Public [605] terminated with status 32
mountall: Filesystem could not be mounted: /media/Public
init: ureadahead-other main process (771) terminated with status 4

fstab:

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
/dev/sdb1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
/dev/sdb5 none            swap    sw              0       0
/dev/sda1 /media/Public ext3 defaults 0 0
/dev/sde1 /media/Private ext3 defaults 0 0
/dev/md0 /media/raid320 auto defaults 0 0

Also, when running fdisk -l i can see that the bootdrive has changed during reboot from sda to sdb (or sdb to sda), without any apparant reason..

Anybody got a suggestion?

---

### Post by Bewe on 2011-08-20
Fixed it by using UUID in fstab!

---

### Post by _nedR on 2011-08-20
edit: Woopsie, didn't see that you already fixed it; :o
Am a noob myself so my suggestion may not be the solution to the problem, but I'll give it a shot:

According to your boot.log, It seems that your partition at /media/Public is no longer /dev/sda1 (which is actually root). So you have to find the new path for your partition and **update your fstab with the correct identifier of /media/Public**. According to the man page of fstab, it is always better to use UUID or **Label** to identify the drive you want to mount. So we'll use your device label to identify your partition.

**1. **To verify the label of /media/Public is 'Public' itself, (which it probably is)  type
> ls -l /dev/disk/by-label/PublicIf it returns your device name (/dev/sd*), Then we're good to go.

**2. **Now that you have verified the label of your partition, edit your** /etc/fstab** using the following command :
>  gksudo gedit /etc/fstabReplace the line
> /dev/sda1 /media/Public ext3 defaults 0 0with
> LABEL=Public /media/Public ext3 defaults 0 0Hopefully this should solve the problem.

I hope my explanation is understandable. If not, please ask.

_nedR

---

