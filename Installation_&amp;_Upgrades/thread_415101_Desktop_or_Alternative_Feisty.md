---
title: "Desktop or Alternative Feisty"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by jchstevens on 2007-04-20
I want to dual boot Feisty on an Inspiron 6400 laptop and I'm wondering whether to use Desktop Feisty or the Alternative one.  Although I have plenty of RAM (2GB), I don't want grub installed on the MBR because I don't want it to overwirte the Dell Media app.
Does anyone know if there is much difference between these 2 installations?
e.g. If I go with the alternative CD will I be missing out on anything?
Julian.

---

### Post by pepsi_max2k on 2007-04-20
having just tried the live cd and not wanting to install a bootloader either, i wasn't too impressed that it gave very few bootloader options. it *will* be installed with the live cd, don't know yet if you have much choice over where. i'm currently downloading the alt cd to see if it's any better, though from what i've read there's still no option not to install any at all with it.

---

### Post by jchstevens on 2007-04-20
> **pepsi_max2k said:**
> having just tried the live cd and not wanting to install a bootloader either, i wasn't too impressed that it gave very few bootloader options. it *will* be installed with the live cd, don't know yet if you have much choice over where. i'm currently downloading the alt cd to see if it's any better, though from what i've read there's still no option not to install any at all with it.
I thought, I'd seen on the ubuntu website a comment about the Alternative CD giving an option to install the bootloader on the ubuntu partition - can't find it now, though!
I think I'll give the Alternative CD a go anyway.

---

### Post by pepsi_max2k on 2007-04-20
Just installed with the alt cd. It's virtually identicle to the live cd (albeit a text mode interface) and you only get grub options after you've installed to hd. Then it pops up and asks if you want to intall as is, or configure it yourself. I hit configure and it just asks where you want to install it, no option not to install or to install lilo instead...

In the end I just chose fdo (floppy) which is as good as no install at all. From what I can tell the live cd is probably identicle in it's options, the only difference being whether it actually ignores what you put in the boot loader device box or actually installs where you say.

---

