---
title: "Hub sub is grub flub?"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by retrosteve on 2008-03-17
My desktop has two hard drives -- the C: drive is a 40gb IDE
the Y: and Z: drives are partitions on a 250GB SCSI.

When I installed Ubuntu over Windows, I decided to go with Ubuntu single boot, no Windows.

So I told the installer to use the 40GB disk (formerly C:) to install to, and use the whole thing.  I left the 250GB disk untouched, hoping to keep the data on it.

But now it can't boot.  It complains at boot time that it can't boot from this partition.

If I use the "e" command in GRUB menu (still at boot time) to temporarily alter the root command, I note that it's trying to boot from hd(1,0), which is the 250GB drive. According to grub anyway.

If I alter the command to root hd(0,0), it boots.  Temporarily.  Changing that command in the /boot/grub/menu.lst doesn't seem to fix it.

Something is screwy here but I don't know how to fix it.

Any ideas?  I promise to thank anyone who helps...

---

### Post by logos34 on 2008-03-18
Odd.  Are you opening menu.lst as root and saving changes?

gksudo gedit /boot/grub/menu.lst

You could try editing /boot/grub/device.map too:

(hd0) /dev/<yourIDEdrive>
(hd1) /dev/<yourscsi/satadrive>

---

### Post by retrosteve on 2008-03-18
I tried to edit that file once more (the first time the changes apparently didn't stick) and the second time it worked -- the disk hd(0,0) turns out to be correct.  Thank you.

The strange thing I still don't understand is why GRUB insists that the disk I boot from (40GB IDE) is hd(1,0) when it's not.

---

