---
title: "[SOLVED] Move GRUB to Bootsector"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by rob150588 on 2008-11-18
Evening all.

Been buiding up a triple boot machine XP/Vista/Ubuntu. Loaded XP on first, followed by Vista and finally Ubuntu went on. Loaded up Vista and used EasyBCD to configure the Vista bootloader (because I prefer the Vista loader to GRUB). Added the entries in for the three OS's, but Ubuntu won't load because GRUB is not installed on the Bootsector, it was on the MBR.

I would like to put GRUB on the bootsector so the Vista bootloader runs GRUB when I select the Linux option.

Does anyone know how to do this without reinstalling Ubuntu (because like an idiot I've set Ubuntu up how I want and put my software on it, so it'd be a pain to have to do all that again).

I'm not too clued up about Linux, so please speak slowly and loudly to me. Cheers.

---

### Post by confused57 on 2008-11-18
You can use the Ubuntu live cd to do this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Instead of setup (hd0), you would install to root partition:
root (hdx,y)
setup (hdx,y)

---

### Post by rob150588 on 2008-11-18
You're a saint. Owe you a pint. Many thanks :)

---

