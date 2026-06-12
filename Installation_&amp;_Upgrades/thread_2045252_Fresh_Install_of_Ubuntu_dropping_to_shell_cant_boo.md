---
title: "Fresh Install of Ubuntu dropping to shell cant boot"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by paichkash on 2012-08-20
hi
i downloaded and installed the ubuntu 10.04 .  after it was installed it asked me to restart my pc which i did.. and the desktop came ok.. then i shut it down and re assembled my pc as i removed the windows disk to avoid any unwanted issue.. 
 then i started my pc but as it was to boot light went off ( here are frequent blackouts. unanounced ) so after 1 hour the light comes back and i start it and get this black screen saying some error like uuid changed (?) and there is a prompt with initramfs and it says droping to shell..


the very first line says
```
 /scripts/init-top/udev: line 24: /sbin/udevd: not found
```it also says like
> Gave up waiting for root device. Common problems: -Boot args (cat /proc/cmdline)  -Check root delay = (did buy acomplia the system wait long enough?)  -Check root=(did the system wait for the right device?)  -Missing modules (cat /proc/modules;  ls /dev) ALERT! /dev/disk/by-uuid/7e729b99-xxxxxxxxxxxxx does not exist. Dropping to shell!  Busybox v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built-in shell (ash) Enter 'help' for a list of built-in commands
please help

---

### Post by mastablasta on 2012-08-21
did you update grub after removing windows disk?
 
try to use boot repair tool from live CD: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by darkod on 2012-08-21
Boot your computer with the ubuntu cd in live mode, open terminal and check the UUIDs with:
sudo blkid

See if that UUID exists or not.

The partitions on the disk might have gotten messed up by the power cut.

---

### Post by PyroSamurai on 2012-10-10
You might also try just reinstalling (minus the power glitch of course).

---

