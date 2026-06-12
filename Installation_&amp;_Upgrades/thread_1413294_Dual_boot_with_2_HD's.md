---
title: "Dual boot with 2 HD's"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Huntly on 2010-02-22
Wondering if anyone has a simple straight forward howto on Dual-booting with 2 HDs.  I have Ubuntu 9.10 installed on one and Windows 7 on the other, right now I just plug in the sata cord for the OS I want to start up but I am sure there is a simpler way.

---

### Post by darkod on 2010-02-22
Just plug in both of them. Go into BIOS and make the ubuntu disk first in the hdd boot order. That will boot ubuntu straight away because it's not yet aware of windows being there. Once ubuntu boots, just execute in terminal:

sudo update-grub

and that will add windows to the grub boot menu which you will now see at each boot.

Note that if you set the windows disk as first option to boot from, it will just load windows straight away. By default it can't recognize linux to boot it. There are ways, but using grub2 bootloader which is already on your ubuntu disk is much better.

---

### Post by Huntly on 2010-02-22
> **darkod said:**
> Just plug in both of them. Go into BIOS and make the ubuntu disk first in the hdd boot order. That will boot ubuntu straight away because it's not yet aware of windows being there. Once ubuntu boots, just execute in terminal:

sudo update-grub

and that will add windows to the grub boot menu which you will now see at each boot.

Note that if you set the windows disk as first option to boot from, it will just load windows straight away. By default it can't recognize linux to boot it. There are ways, but using grub2 bootloader which is already on your ubuntu disk is much better.
Worked like a charm, cheers!

---

