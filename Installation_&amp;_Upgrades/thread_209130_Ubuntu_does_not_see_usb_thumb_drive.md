---
title: "Ubuntu does not see usb thumb drive"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2006-07-04
Linux Newbie here, so your patience appreciated. Have installed Ubuntu on one of our office computers.

It found the CD Drive OK and was able to install a USB printer and scanner OK, but I put a USB memory device into the USB port and nothing came up on the desktop. My computer doesn't show it, but I can see it in Device Manager.

What do I need to do to be able to access it please? TIA

---

### Post by aysiu on 2006-07-04
It's sad that your automounting doesn't appear to be working, but you can force it to mount using these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Odyssey1942 on 2006-07-05
For clarification, I do not have Windoze on this computer and since the URL you kindly provided talks about "mounting Windows partitions..", thought I had better confirm that these instructions still apply. Your further advice much appreciated.

---

### Post by aysiu on 2006-07-05
If your USB memory device is a typical one, it's probably formatted as FAT16 or FAT32, in which case the link would apply.

Just make sure it's physically plugged into your computer before you issue the *sudo fdisk -l* command.

---

