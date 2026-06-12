---
title: "Dual Boot issues (issue with BIOS!)"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by tkstock on 2007-02-23
Hi,

I wanted to pass along this tidbit - it may belong in a sticky, but I don't know where.

I installed Edgy Eft (Ubuntu 6.10) on an extended partition with XP on my primary partition so that I could dual boot to both.

After working with the GRUB, I was able to get Ubuntu to boot fine, but Windows never would.  I went around this for hours.

Finally, I discovered that if your BIOS is set to autodetect drive access, this can screw that up!  I changed mine to Large, and suddenly Windows would boot!  Yay!

Now, how can I specify that windows will be the default OS to load instead of Ubuntu?

---

### Post by taurus on 2007-02-24
You need to edit /boot/grub/menu.lst and change the default value from 0 (currently) to whatever the entry for XP.  Remember, the first entry counts as 0, not 1.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

