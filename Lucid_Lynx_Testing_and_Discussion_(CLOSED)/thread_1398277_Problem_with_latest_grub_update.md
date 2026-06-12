---
title: "Problem with latest grub update"
date: 2010-02-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mikeyphi on 2010-02-04
Updated this morning, noticed a new grub update. Then could not reboot into lucy; if lucy selected - system froze on boot page; my other 2 drives with hardy & Karmic were OK.

I had to delete the first 2 lines from the Grub.cfg file before lucy would boot...viz:
record fail
set gfxpayload=keep

Anyone else see this?

---

### Post by dino99 on 2010-02-04
i'm using the grub-ppa package and i have to edit the boot line because a vga=xxx has been inserted and the initrd line end with generi instead of generic.

when i remove vga=xxx which is deprecated and add c to generi then ctrl-x, it boot fine.

running grub-mkconfig insert these deprecated vga things but everything else seems ok, no typo there. Then update-grub2 makes the same typo error in menu.

note: have posted yet today on this forum about this problem but have not reported it.

---

### Post by kansasnoob on 2010-02-04
The only thing I noticed here was a "lag" in the time after I make my selection and press enter. I would guess about 10 seconds added to total boot time.

On the plus side I now have a relatively "quiet" boot.

BTW I'm multi-booting:

```
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.32-12-generic
Found initrd image: /boot/initrd.img-2.6.32-12-generic
Found linux image: /boot/vmlinuz-2.6.32-11-generic
Found initrd image: /boot/initrd.img-2.6.32-11-generic
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda11
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sda13
Found Ubuntu 9.04 (9.04) on /dev/sda5
Found Linux Mint 7 Gloria - Main Edition (7) on /dev/sda7

```

---

