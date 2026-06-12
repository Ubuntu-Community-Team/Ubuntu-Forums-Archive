---
title: "Installing Windows alongside Ubuntu [no /boot/grub/menu.lst file]"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by AlvitrValkyrie on 2011-12-29
Yes, Windows alongside Ubuntu. I know I know... Just for particular compatability reasons.
I can partition my drive no problem. The only issue is for when GRUB is overwritten by Windows' boot manager. I get you can restore it via a live CD, but my issue is that I lack /boot/grub/menu.lst on my machine, for reasons unknown. [Particular for GRUB 1 or 2?]

Alternatively, I'd image my drive, and then just install that after XP has overwritten my entire drive, but I don't have that much time.



Current: BT5r1-GNOME-x64 [Based on Ubuntu 10.04 LTS]
To be installed: Windows-XP-x32
Idk if this should go in the "other" OS section. I don't see any need, really, as all should work the same (and has thus far).

---

### Post by 2F4U on 2011-12-29
For pretty long Ubuntu uses Grub2, which does no longer have /boot/grub/menu.lst. I would suggest to read through the dual boot guide, which has a section on installing Windows after Ubuntu.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by AlvitrValkyrie on 2011-12-29
Yea. I've been looking into the boot repair package/disk. I'm still partitioning my drive via a live CD. Shrinking about 180 down to two 90s. Been since I posted this thread.

Anyhow. Do you personally know any of the options to work? I've experienced Ubuntu specifically to be very unstable when it comes to booting :l Dont wanna mess anything up

---

