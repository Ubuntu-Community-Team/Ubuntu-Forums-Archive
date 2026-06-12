---
title: "Dual boot: beware 7.10!"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by OwenWatson on 2007-10-26
Just installed 7.10 over 7.0 and suddenly Windows disappeared as a boot option.

I've checked and it looks as though the menu.lst file in grub gets overwritten between the automagic parts.

Just a heads-up to those who only occasionally use ubuntu. . .

Now to work out how to put Windows (XP) back before the family kills me. . .

---

### Post by ldesilva on 2007-10-26
open a console and modify the menu.lst in the /boot/grub
and paste this contents to the end of the file: (i pressume that you want to dual-boot between XP and Gutsy)

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by thelocust on 2007-10-26
Always backup. :)

---

### Post by OwenWatson on 2007-10-26
Many thanks: it now works!

Domestic harmony now reigns. . .

---

