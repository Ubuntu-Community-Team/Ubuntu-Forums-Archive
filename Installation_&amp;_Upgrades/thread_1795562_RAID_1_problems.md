---
title: "RAID 1 problems"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by etiennenoel on 2011-07-02
HI,

I'm trying to install 10.04 on a software RAID 1. I followed this tutorial : [http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html](http://blog.foobaria.com/2010/05/installing-ubuntu-1004-desktop-with.html)

Everything went fine, except at the reboot when I got the initramfs page with the following error message : 

error: fd0 read error

mount: mounting /dev/disk/by-uuid/ca5ebe7f-e126-4f80-a0d3-55d77c3a94d8 on /root failed invalid argument
mount: mounting /dev on /root/dev failed : no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg

Busybox

(initramfs)

Thanks in advance,

ETienne NOEL

---

### Post by dino99 on 2011-07-03
fd0 is the floppy reader, and that error is known

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554700](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554700)

as you might not need that floppy reader very often, try either: unset it into bios, unplug it, add --no-floppy on boot line (/etc/default/grub, then sudo update-grub), but you still should have it (default), and finally, check that floppy is not loaded by /etc/fstab

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

