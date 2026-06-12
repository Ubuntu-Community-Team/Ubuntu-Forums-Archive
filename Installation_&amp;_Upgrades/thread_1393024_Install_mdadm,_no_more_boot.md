---
title: "Install mdadm, no more boot"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Smeghead on 2010-01-28
I'm setting up a new machine that has a pair of drives in it and have ran into a rather serious problem with mdadm.

The intent was to take two 1.5TB drives, create a small 20GB partition at the start of each so that the person using the system can juggle Ubuntu installations as he sees fit (this is the way he wants it, so I'm not going to argue) and then partition the remainder of the disks as type fd to be software RAIDed together for data.

It was a nice plan. It's too bad it didn't survive the first step.

After running into problems the first time around, I played around with reinstalling a couple of times and managed to distill the problem down two basic steps:

[list=1]
[*]Install the 32-bit version of 9.10 from the CD.
[*]Boot the new install and install mdadm (apt-get install mdadm).
[/list]
The result is a system that no longer boots. It gets through the grub menu, shows the initial splash screen which then stretches out off the screen and then goes black. It dies in initramfs after trying to mount the UUID equivalent to /dev/sda1, complaining that the device is busy.

Any idea what gives? I literally have installed nothing and tweaked nothing other than the above two steps - install 9.10, then install mdadm. It's not like I'm trying to boot the system off the RAID array - the little partition at the start of the disk is completely standalone.

Booting the liveCD, I can mount /dev/sda1 and poke around in its contents, so nothing fatal appears to have happened to it. I did notice that the ramfs image has been touched today, presumably by apt installing mdadm.

Various searches haven't found anything interesting, but that's not to say there isn't a thread where this has already been discussed and solved.

---

