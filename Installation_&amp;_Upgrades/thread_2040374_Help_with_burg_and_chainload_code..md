---
title: "Help with burg and chainload code."
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by spotzz on 2012-08-10
Hi,

 I'm using ubuntu 12.04 and I'm trying to chainload from burg to other distros, but the code doesn't seem to work.  I get the menu entries at the bootloader menu, but when I press "enter" nothing happens. I dont get any error message and I don't get any type of screen, nothing happens.  The entries are just texts.

The code I'm using:

```

menuentry "PClinuxOS" {
set root=(hd0,6)
chainloader +1
}

```

I'm sure the OS is located at logical drive 6.

What am I doing wrong?

---

