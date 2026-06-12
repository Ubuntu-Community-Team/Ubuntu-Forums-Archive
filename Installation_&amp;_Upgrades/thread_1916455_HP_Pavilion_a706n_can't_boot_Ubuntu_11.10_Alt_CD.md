---
title: "HP Pavilion a706n can't boot Ubuntu 11.10 Alt CD"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by RedPenguin on 2012-01-28
I have an unmodded HP Pavilion a706n with all original parts except the memory has been upgraded to 784MB.

Now when I try to boot up the Ubuntu 11.10 Alternative CD, it goes to a black screen that just sits there, even eventually Caps Lock and Scroll Lock just blink.

Eventually using "vga=770" and removing "quiet" I was able to see what was going on.

Eventually trying "noapic" and "noacpi" and sometimes trying apm=off, I am able to almost boot.

But I just end up with a flood of udevd: '/sbin/modprobe -bv pci:....." and udevd: '/sbin/modprobe -bc usb:....." and eventually "udevadm settle - timeout of 120 seconds reached the event queue contains" and mentions "sr0" twice.

Then finally "Kernel Panic - not syncing: Attempting to kill init" and "Pid: 1 comm: init Not tainted 3.0.0-12-generic #20-Ubuntu".

---

