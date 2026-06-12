---
title: "cannot fix grub after win reinstall"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by vangop on 2011-08-07
Hi!
I've reinstalled win 7 (dualboot). Then booted with rescuecd and tried to fix grub.
```
$mount /dev/sda3 /tmp/b/boot
$grub-install --root-dir=/tmp/b /dev/sda
```
This gave ma a grub shell on boot. The prbm was that this was grub1 - v0.97
I ran a proper 2nd time
```
$mount /dev/sda3 /tmp/b/boot
$grub2-install --root-dir=/tmp/b /dev/sda
```
Now on boot I can spot grub loading and black screen with blinking cursos on top.
Plz help )
ubuntu 10.10, separate /boot, uncrypted /root (which is probably the cause)
Also I have deleted the 2 win partitions (sda1, sda2) and made a new one (sda1). The /boot is still sda3, can this be the cause?

---

### Post by haresear on 2011-08-07
This thread might help:
[http://ubuntuforums.org/showthread.php?t=1814053](http://ubuntuforums.org/showthread.php?t=1814053)

---

### Post by vangop on 2011-08-07
Thanks a lot, that gave me a hint. I needed to chroot and update-grub, since my partitions numbers changed.
I tried to chroot but it failed, the error reveled the architecture mismatch: i had a x86 liveCD, while x64 system to repair. Just booted the x64 liveCD and it worked!
As expected, if anyone has GRUB problems, try [howto]("https://help.ubuntu.com/community/GrubHowto") first.
Most of the tutorials are copy/pastes of it.

---

