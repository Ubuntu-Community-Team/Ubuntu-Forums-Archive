---
title: "Problem with Grub"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by Torture on 2007-06-26
I was having a problem with grub and I needed to enter the vga=771 code everytime I wanted to boot with ubuntu, otherwise it would make my monitor go into stand by.

So, after a couple of days I decided to edit /boot/grub/menu.lst and I added vga=771 where I used to put it manually on every restart. Restarted my computer and instead of crashing my monitor after about 10 seconds, it crashed after about 40 seconds.
I tried editing the boot sequence and removing the vga=771, it went back to crashing after about 10 secs.
I tried entering in safe mode, went back to edit the menu.lst and it was still the same.

I am running the following hardware:
DFI Lanparty NF4 Ultra D
AMD Opteron 165
2x1gb OCZ gold ddr500
ATI x850 xt pe
dell 2007fpw

Should I reinstall or is there a way to rescue this?

Thanks!!!

---

### Post by haden9 on 2007-06-27
Did you make a backup of your menu.lst file before editing it? That may be your last hope. If so use the copy command:

sudo cp /boot/grub/menu.lst_bak menu.lst

I used the menu.lst_bak as an example only, you need write what you saved your backup as.

Good luck by the way!!!

---

### Post by Torture on 2007-06-30
I ended up formating and reinstalling an x86 version, it installed right away without the problems I was having with the x64.

---

