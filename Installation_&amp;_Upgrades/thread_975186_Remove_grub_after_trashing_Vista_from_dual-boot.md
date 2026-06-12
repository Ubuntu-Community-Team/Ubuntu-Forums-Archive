---
title: "Remove grub after trashing Vista from dual-boot"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by vizualbod on 2008-11-08
I used to have dual-boot Ubuntu and Vista, although I formatted the Vista partition as I don't need it anymore.
I guess now I don't need grub loader either? How do I remove it?
I  tried sudo apt-get remove grub and also with --purge, but it's still there.

---

### Post by vizualbod on 2008-11-08
My question was a bit wrong, I found that every operating system needs a boot loader, for Linux it's Grub or Lilo, for Windows it's NTLDR. You can not remove boot-loader of the operating system.

Solution was to configure Grub like so:

```
sudo gedit /boot/grub/menu.lst
```

Change line ```
timeout 10
``` to ```
timeout 0
``` so Grub have no time to ask.

And delete on the bottom of the file following lines:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1
```

Done!

---

### Post by meierfra. on 2008-11-08
> timeout 0

I recommend to use 

```
timeout 1 
```

and 

```
hiddenmenu
```
(in place of "#hiddenmenu")


This way you will be able to boot into recovery mode, if you ever need to. (Press "Esc" during boot up to get to the grub menu)

---

