---
title: "Time to get rid of windows 7"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by TimEnid on 2010-08-01
but the boot loader is on the w7 hd. whats the best method to have the boot loader/gub switched to my ubuntu hd? i want to use the w7 hd as extra space.

is it possible to format the w7 hd, while in ubuntu, using gparted. then install the grub/boot loader on the ubuntu hd? will there be any setbacks from this?

---

### Post by anglican on 2010-08-03
> **TimEnid said:**
> but the boot loader is on the w7 hd. whats the best method to have the boot loader/gub switched to my ubuntu hd? i want to use the w7 hd as extra space.

is it possible to format the w7 hd, while in ubuntu, using gparted. then install the grub/boot loader on the ubuntu hd? will there be any setbacks from this?
Yes, I'd expect a re-partition of the w7 hd followed by a "sudo grub-install" to work.

H

---

### Post by TimEnid on 2010-08-03
> **anglican said:**
> Yes, I'd expect a re-partition of the w7 hd followed by a "sudo grub-install" to work.

H

thanks. but when i open gparted and click on the w7 drive, the option to format is greyed-out.

---

### Post by lucasart on 2010-08-03
> **TimEnid said:**
> thanks. but when i open gparted and click on the w7 drive, the option to format is greyed-out.
you have to it from a live CD and start gparted from the liveCD boot. but then before rebooting make sure grub  starts on the other partition, otherwise you'll crash after bios on a grub console and that's really nasty, unless you're grub fluent ;)

---

### Post by Mark Phelps on 2010-08-03
> **TimEnid said:**
> but the boot loader is on the w7 hd. whats the best method to have the boot loader/gub switched to my ubuntu hd? i want to use the w7 hd as extra space.
Don't know of any way to "move" it, but the link below has details on how to install GRUB from a LiveCD:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

After that, I'd switch boot order in the BIOS to boot from the Ubuntu drive and you should be set to go.

> is it possible to format the w7 hd, while in ubuntu, using gparted. then install the grub/boot loader on the ubuntu hd? will there be any setbacks from this?
It's possible the Win7 partition is mounted, in which case, Gparted won't let you do anything with it.  Simply select the partition in GParted and unmount it.  You should then be able to do whatever you want with it.

---

