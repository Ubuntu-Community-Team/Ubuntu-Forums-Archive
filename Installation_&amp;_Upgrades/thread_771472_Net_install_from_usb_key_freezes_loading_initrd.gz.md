---
title: "Net install from usb key freezes loading initrd.gz"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by fairlyradpossum on 2008-04-27
I'm following the general steps from [http://technowizah.com/2006/11/ubuntu-how-to-ubuntu-edgy-from-usb.html](http://technowizah.com/2006/11/ubuntu-how-to-ubuntu-edgy-from-usb.html) to install Hardy via usb. I get a boot menu, but when loading initrd.gz I see a line and a half of ... and then nothing happens.

I installed edgy on this same machine (thinkpad x60) without trouble. I'm not even sure where to begin troubleshooting; I've md5summed the files on the usb key and everything matches up. Any suggestions?

---

### Post by Rallg on 2008-04-27
Possibilities: (1) The USB thinks it is hd0, and that your hard drive is hd1. (2) Whenever you reformat a partition (such as when installing), its UUID is changed. Does your bootloader menu.lst refer to an obsolete UUID? If so, either find out what the new UUID is (can be discovered via live CD, if necessary), or edit the Grub menu.lst to refer to the boot partition by its standard device path.

I'm not sure, but I believe that Edgy did not rely on UUID, whereas Hardy is very particular about it.

---

### Post by fairlyradpossum on 2008-04-27
For 1, I'm not sure how to diagnose this since I can't get to any sort of prompt. For 2, I haven't formatted anything yet; I should say that initrd isn't freezing on first boot, it's freezing when I'm trying to run the installer. I used lilo to configure the usb key, so grub isn't in the equation yet.

Poking around with boot options, I tried "install break=top", but apparently I'm not even getting far enough for this to make a difference.

---

