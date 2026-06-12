---
title: "GRUB_BADRAM , Ubuntu 12.04"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by ariskk on 2012-12-01
I've used memtest to find a bad byte of ram (12 digit hex address around 8100 th MB). I then added that address to /etc/default/grub 's GRUB_BADRAM section. I've uncommented GRUB_BADRAM and then run update-grub. It updated /boot/grub/grub.cfg and I can see the badram entry there. But it doesn't seem to take effect, my box still crashes due to the bad ram byte. 

I've noted GRUB_BADRAM examples are all 8 hex digits but memtest reported the problem using 12 hex digits. How many digits should I use for GRUB_BADRAM ? Any other ideas of what am I doing wrong?

Thanks

---

### Post by Sef on 2012-12-01
Why don't you get another stick of ram?

---

### Post by ariskk on 2012-12-01
Well, I don't mind loosing 1 byte out of 8GB :D

replacing the RAM is the plan B, but badram seems to offer a better alternative that buying and replacing hardware.

> **Sef said:**
> Why don't you get another stick of ram?

---

### Post by ariskk on 2012-12-04
Anyone, knows any more details?

this is the entry at /boot/grub/grub.cfg :

badram 0x00002089d2698

it doesn't work though.

---

