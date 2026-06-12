---
title: "Error while attempting to run ubuntu"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by Izotz on 2008-06-24
hey guys I'm new so i hoe this is the right section.

i get this re-occuring error when i try and install ubuntu or boot it im not sure, and i get it with the image i downloaded and the image that came with APC magazine free dvd, i also get in when i try the wubi install so here it is hopefully you can help my out guys.

ata3.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata3.01: cmd a0/00:00:00:24:00/00:00:00:00/b0 tag 0 pio 36 in
ata3.01: status : {DRDY}

thanks for your time

Kieran

---

### Post by Pumalite on 2008-06-24
Post your specs. If 512 MB of RAM or more; you can try adding all_generic_ide at the end of the boot line:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Izotz on 2008-06-24
core 2 duo 2.13ghz
foxconn 965 mobo
3 gig ram
320 gig hdd
8800gts 320 mb

also something i forgot to mention, when its booting ie the Ubuntu logo appears with the loading bar, it does its normal backwards and forwards of the progress bar then it starts spitting out this error.

---

### Post by Pumalite on 2008-06-24
Could be a bad burn. Do md5sum and burn at 4x or less. Clean the lens in your burner.
If not; try your luck with these:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788 vga=789 vga=791
To be tried alone or in different combinations.
OTOH; a 32 bit could be having trouble with 3 GB of RAM.

---

### Post by Izotz on 2008-06-26
Thanks for your help trying a slower burn now, and if i get the chance ill try the options. hopefully it will all work out.

---

### Post by Pumalite on 2008-06-26
Good luck.

---

