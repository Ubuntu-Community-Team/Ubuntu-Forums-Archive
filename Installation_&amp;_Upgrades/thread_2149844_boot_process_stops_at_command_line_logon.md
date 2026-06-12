---
title: "boot process stops at command line logon"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2013-05-30
I've just installed 13.04 on a new asus ux32a and for the most part it works very well.  Recently, when I boot it up, it stops at command line asking for username and password, where it hangs for a few seconds before continuing on to the graphical logon screen.  Its not a big issue, just wastes time, any suggestions how to remove the request to login via the command line?  Might be something in the GRUB settings?

Also for some reason it seems to boot to tty1?  I'm no expert at this but I thought the graphical boot booted via tty7?

Thanks

Jim

---

### Post by 2F4U on 2013-05-30
How does your /etc/default/grub look like? Do you have a line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

in it? It is supposed to suppress boot messages and show the purple Ubuntu splash screen.

---

### Post by jamaas on 2013-05-30
It does have that already.  Any other suggestions?

Thanks

J

---

