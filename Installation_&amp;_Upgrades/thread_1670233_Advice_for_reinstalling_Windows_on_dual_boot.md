---
title: "Advice for reinstalling Windows on dual boot"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by horseatingweeds on 2011-01-18
I'm about to reinstall Windows XP on a system that I also have Ubuntu installed on. I'm a bit confused how the boot loader works in a dual boot system. After reinstalling XP will I have to do something, like reinstalling GRUB somehow? Any advice?

Thanks

---

### Post by oldfred on 2011-01-18
Windows will install its boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If reinstalling to the same partition the old entry may still work, but you probably should run this anyway after you have rebooting into Ubuntu.

sudo update-grub


To understand a little more. Article is detailed but just reviewing pictures is worthwhile.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by horseatingweeds on 2011-01-18
Thanks oldfred. That's a good article. I understand the master boot record subject a lot better.

Would the instructions in the first link be equivalent to running "Reinstall GRUB Boot Loader" from the Rescue Mode menu on a live CD/DVD?

---

### Post by oldfred on 2011-01-19
I have not tried the rescue mode on the liveCD. If would be worth a try. Let us know if that works. And what version of liveCD you have. Older versions did not even have a rescue mode.

---

