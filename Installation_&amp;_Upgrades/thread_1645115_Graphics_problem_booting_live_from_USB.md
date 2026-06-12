---
title: "Graphics problem booting live from USB"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by mysquad on 2010-12-14
Hi.

Im trying to boot a live USB with Ubuntu 10.10 on it. But when i come to the screen with 5 dots and the Ubuntu logo my screen gets all scrambled and nothing more happens.

The hardware i run is:
[LIST]
[*]AMD Athlon X2 5600+
[*]3GB DDR2 RAM
[*]Nvidia 240 GT
[*]MSI K8N-NeoV2 Motherboard
[/LIST]

And Here follows some pitures of how the screen looks when this occurs:

[[IMG]http://img196.imageshack.us/img196/9397/wp000054.th.jpg[/IMG]](http://img196.imageshack.us/i/wp000054.jpg/)


Would appriciate all help in resolving this matter :)

---

### Post by Rubi1200 on 2010-12-14
Hi and welcome to the forums :)

Have you tried booting with the nomodeset parameter?

As the live medium starts, press F6 then Esc to see the boot line. Move the cursor to get to where it says quiet splash and add nomodeset, then Enter to boot.

---

### Post by searchfgold6789 on 2010-12-14
And maybe on that CD they still have "Safe Graphics Mode". Maybe that is what the other guy just suggested, but they renamed it....

---

### Post by mysquad on 2010-12-14
It worked when i booted the live USB, but then i installed it and the same problem occured! Where do i fix that?

---

### Post by wilee-nilee on 2010-12-14
> **mysquad said:**
> It worked when i booted the live USB, but then i installed it and the same problem occured! Where do i fix that?

Power on hold the shift down, at grub menu hit e=edit, use arrow keys to get to end of first kernel should see quiet splash type in nomodeset before it then use certl-x to boot to safemode and find a driver.

---

