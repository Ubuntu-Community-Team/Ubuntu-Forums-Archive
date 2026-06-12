---
title: "Grub Error 17: Cannot Mount Selected Partition - again!"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by BrianMaskell on 2008-02-06
I have a similar configuration to that described in several other posts - and I have got it to work as required. I just don't understand why!

My Dell 1501 laptop came with Windows XP and for the foreseable future I want it to stay that way. I have an external hard drive connected via USB on which I have installed everything Ubuntu and the BIOS order is CD drive, external drive, internal drive; so if the external drive is present, I get a grub menu with Ubuntu as the default, otherwise it just boots XP. Simple! But getting there initially was a struggle, though I was greatly assisted by this forum; so imagine my deep joy when, having upgraded to 2.6.22-14-generic I once more encountered "Error 17 Cannot mount the selected partition".

The answer was that /boot/grub/menu.lst had been rewritten with "root (hd1,0)", where I need "root (hd0,0)" correctly to address my Ubuntu boot partition (sdb1) - but why the discrepancy? It seems that the installation/upgrade process has a different way of addressing partitions than grub does. So when I look at my two disks with gparted, the internal disk with its Windows bootable partition is sda and the external disk with Ubuntu and grub is sdb; it seems entirely reasonable that this external disk (sdb) be addressed as it was, viz hd1. However grub, when it runs on the external disk, addresses it as hd0.

Grub addresses the internal disk (sda) as hd1, so the menu.lst entry for my Windows bootable partition (sda2) is correct:
title           Microsoft Windows XP Home Edition
root            (hd1,1)
map             (hd1) (hd0)
Presumably the installation process just copied this anyway.

menu.lst also includes the line
# groot=(hd1,0)
and I suspect that it should be (hd0,0), but I don't understand its role. Dare I change it? I don't ever want grub to be written to the 'Windows' disk.

I would be grateful for some illumination about what governs the way these different components address partitions.

---

### Post by confused57 on 2008-02-06
Yes, # groot should be (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by BrianMaskell on 2008-02-06
Thanks for the bare confirmation but it brings me no closer to an understanding.

Your reference says:
"'groot' is short for 'grub root device'. That will be the partition you want your new Linux kernel to be installed in when you get a new one during an update. Your /boot partition is the partition you should specify here."

So if I change to
# groot=(hd0,0)
and this is read, as is implied, by the installation/upgrade process, won't this be interpreted as my Windows drive (sda)? This is definitely not where I want grub installed. But if it just means that the root commands in menu.lst will be written correctly at the next upgrade, that would be fine.

Where is this defined? I did try the manual [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html) but could not find groot in there.

---

### Post by confused57 on 2008-02-06
Here's everything you need to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

> So if I change to
# groot=(hd0,0)
and this is read, as is implied, by the installation/upgrade process, won't this be interpreted as my Windows drive (sda)? This is definitely not where I want grub installed. But if it just means that the root commands in menu.lst will be written correctly at the next upgrade, that would be fine.

Since you're booting first to your external drive, it is recognized as hd0 and your external drive is hd1...(hd0,0) is your root partition...the link above explains grub much better than I can.

---

