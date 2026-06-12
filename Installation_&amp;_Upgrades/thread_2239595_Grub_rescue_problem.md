---
title: "Grub rescue problem"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by Idiens on 2014-08-14
Having attempted an upgrade from 12.04 to 14.04.1 with update manager, which failed,  I tried reinstalling 12.04 from a USB stick. The installation appeared to run smoothly, but on restart I get the following error.

error: unknown file system
Entering rescue mode ...
grub rescue>_

Dell Studio 1737 the machine is working in trial mode of the USB stick, hence this message. It should still be dual boot with Vista.

Any suggestions how to get GRUB moving? It appears to be v0.97 despite loading by 12.04

---

### Post by oldfred on 2014-08-14
Grub rescue is only grub2.

You may be able to manually boot.

       See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

If configfile does not work then grub.cfg is part of issue, but you may be able to directly boot kernel. Again change from hd0,5 and sda5 to your correct partition for install.

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

If that does not work post link from BootInfo report:

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Idiens on 2014-08-14
Boor-repair eventually fixed my problem thanks,

It took a bit of downloading to find a installation that worked and it still complained about Pastebinit files being missing.

Thanks again.

---

