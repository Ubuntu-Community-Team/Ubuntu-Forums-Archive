---
title: "[bug] Feisty und LVM"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by TurboPascal on 2007-05-30
Hi together,

Some days we installed´a new kernel:

The following NEW packages will be installed:
  linux-image-2.6.20-16-server
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

Our hard disk configuration is:
a (software) raid 1 each holding
5GB SWAP and
245GB LVM

After restart the kernel hangs after "md: bind</dev/hda2>" and "md: bind </dev/hdd2>".
with:
"raid1: raid set md0 active with 2 out of 2 mirrors."

Some minutes later the busybox of initramfs has a timeout and provides a shell.
("ALERT! /dev/mapper/vg-root does not exist. Dropping to a shell!"
Unfortunately the busybox in the lvm seems to lack any lvm commands. Thus we cannot continue or fix the bug.

Any suggestions? (We went back to the old kernel and initramfs, that at least works).

Greetings,

Lorenz Kolb

---

### Post by Rotzooi on 2007-05-30
Seems that libdevmapper is not compatible with the new kernel.

---

### Post by kubug on 2007-06-01
I have a computer at home and a computer at work (one with RAID 0 and one with RAID 1) that didn't initialized the raid properly after the latest kernel upgrade.

All I saw was:

* /dev/md1 no found on medium.*

on the computer at home.

I had to restart the computer at work 5 times before I realized it was a problem with the Kernel (we had a thunderstorm right above us at the time, so I blamed some of the interference on that). On this one I could boot into the Desktop but it then froze after a couple of minutes. I checked the log files (I am not so good at that) and couldn't find anything regarding the new kernel or md devices.

I then remembered that we just upgraded to the new kernel, and once booted to the old kernel, it was running fine again.

I guess there was not enough testing done before this one was released.

---

