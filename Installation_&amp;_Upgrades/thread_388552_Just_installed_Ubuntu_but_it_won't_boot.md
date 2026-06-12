---
title: "Just installed Ubuntu but it won't boot"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by urioli on 2007-03-19
Hi all,

I've just installed Ubuntu 6.10 on a separate hd on my Dell Dimension 5000 PC. It boots fine with the Live-CD, but it won't boot from the hd where I installed it.

I have the following disks on the PC:

IDE hard drive where Ubuntu is installed (/dev/hda I guess)
IDE DVD (/dev/hdb)
SATA hd with Windows XP (/dev/sda)

Both the Keyboard and the Mouse are connected through usb.

I've set up the bios to boot first from the IDE HD, and I get to the grub menu. However, when I select to boot Ubuntu (or Ubuntu in safe mode) from the menu, it stops at the following line:

drivers/usb/input/hid-core.c: v2.6 USB HID core driver

Any ideas on what is happening? Anything I can try?

Thanks in advance,

Oriol

---

### Post by urioli on 2007-03-20
I just corrected it by reinstalling Ubuntu. The problem was that the first time I installed it, the ide hd was slave to a ide dvd and was not recognised by the boot.

---

