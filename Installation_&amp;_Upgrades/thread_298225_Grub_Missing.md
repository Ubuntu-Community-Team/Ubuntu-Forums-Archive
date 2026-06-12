---
title: "Grub Missing"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by hellraiser_rob on 2006-11-12
Hi all,

Sorry to be a bother, i've just installed edgy and have run into a problem.

Have two drives:
-sata 200gb (windows) 
-hdb 40gb (just put ubuntu on it)

When i restarted its just gone straight into windows, i think i might have chosen the incorrect options with grub.


Does anyone know of a solution, many thanks in advance,

Rob

---

### Post by bulldog on 2006-11-12
Change the boot order in your BIOS and see if GRUB is on the other hdd.

If so leave the boot order that way and map your windows in menu.lst or reinstall GRUB on your windows hdd [not recommended by me]

So you have the opportunity to boot always your windows bootloader by changing the boot device in your BIOS when GRUB is failing for any reason.

BTW,nice avatar

---

### Post by hellraiser_rob on 2006-11-12
many thanks for your quick support, my feeble mind realised about the f8 boot menu and that worked, thanks again

---

