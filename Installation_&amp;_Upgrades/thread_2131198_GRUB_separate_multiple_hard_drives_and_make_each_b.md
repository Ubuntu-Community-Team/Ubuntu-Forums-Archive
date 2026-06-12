---
title: "GRUB separate multiple hard drives and make each bootable. Can this be done?"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2013-04-01
I have 2 working hard drives, the first, sda, has Ubuntu 11.10 (Oneiric Ocelot) installed and the other, sdc, has Ultimate Edition 3.5 installed. I have them coexisting wonderfully, but now I wonder if I can separate them, unplug either one, and still have either one boot as a single install?

If there is a way to do this, can it be done without a usb or cd?

---

### Post by fantab on 2013-04-01
Yes it can be done. You will have to install GRUB on Both the HDD. However, you will have to "update-grub" from the existing HDD whenever the other HDD is plugged in to boot the os on the plugged in OS.

Suppose this /dev/sdc is an external HDD, plugged in via USB then you can adjust the BIOS to BOOT "USB devices first". This way whenever the Usb is plugged in your mobo will boot it, otherwise the regular HDD will boot.

---

### Post by darkod on 2013-04-01
Just further clarification. Yes you need to install grub on both, but not the "same" grub. If you put grub from 11.10 on both for example, it won't work after disconnecting sda because there will be no /boot folder with the grub files to use.

I assume the Ultimate edition works like the normal one. What you need to do is boot the 11.10 and install its grub to /dev/sda:
```
sudo grub-install /dev/sda
```

Then boot the Ultimate and install its grub to /dev/sdc:
```
sudo grub-install /dev/sdc
```

After that each disk will have its own separate grub which is from the OS on that disk. If you disconnect one disk, the other OS can keep going.

---

