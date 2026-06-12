---
title: "grub issues"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by tanozfood on 2008-03-06
Hello,
installing ubuntu I have changed from LILO to the grub boot loader
and I have some doubts about its configuration.
I have 2 hard disk, one is sata and one is ide. On BIOS I set up
the boot sequence as cdrom-sata (ide is disabled). On the sata disk
I have 3 logical partitions for ubuntu and, after them, a primary
partition for windows xp.
Looking at /boot/grub/device.map I found:

(hd0)    /dev/hdb
(hd1)    /dev/sda

and this is the first doubt (I think it is wrong).
However, if I set up the root partition for the ubuntu entry as
(hd0, 4), it boots! (even if I do not change device.map)

For the xp entry, I have (automatically generated)

root (hd1,1)
map (hd0)(hd1)
map (hd1)(hd0)
chainloader +1

But if I edit from the grub menu substitute all these line with a unique
line like:

chainloader (hd0,1) +1

it works.
So, what should I do to keep things organized in the right way?
Thanks,
                      tano

---

### Post by dstew on 2008-03-06
> chainloader (hd0,1) +1I did not know you could do that. That is pretty neat. If it works, just leave it alone. You might have to reconfigure your menu.lst after you get a kernel update though. If you want to try to make it update correctly, change the **#groot** value in the upper part of the menu.lst file to (hd0,4) to match the root entries. Do not remove the # from in front of groot, it is not a comment. The comments have ## in front of them.

---

