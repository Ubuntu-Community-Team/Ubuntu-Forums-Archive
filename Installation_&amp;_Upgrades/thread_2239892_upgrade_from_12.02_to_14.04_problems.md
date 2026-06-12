---
title: "upgrade from 12.02 to 14.04 problems"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2014-08-16
I upgraded to 14.04 and my netboot won't boot right.
It is an older Acer Aspire One (Atom CPU).
The normal boot doesn't work but the advanced boot into text mode (no graphics) sort of works.
I can get to the read-only disks and a root prompt where I can remount the disk as r/w.
I think grub and the kernel weren't updated.

From here:
GNU GRUB version 2.02~beta2-9ubuntu1
I select recovery
I see another grub menu (same version) and
I select Advanced options for Ubuntu.
I then see an recovery menu (white background)
I select root - drop to a root shell.

My /boot directory has:
abi-3.2.0-35-generic
config-3.2.0-35-generic
grub/
initrd.img-3.2.0-35-generic
memtest86+bin
memtest86+elf
memtest86+_multiboot.b*
System.map-3.2.0-35-generic
vmlinuz-3.2.0-35-generic

Only the initrd has a new date, everything else is old.

---

### Post by bjlockie on 2014-08-16
I was able to reinstall grub (it still has the beta version) and boot in text mode.
The screen is blank in graphics mode.
The kernel is still an old version too.

---

### Post by kansasnoob on 2014-08-16
Can you try what I posted here:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)

---

