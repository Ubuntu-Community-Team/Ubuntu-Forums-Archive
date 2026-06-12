---
title: "Ubuntu 8.04 Alpha 6"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by bloodandsoil on 2008-03-08
I downloaded alpha 6 and it will not work on one of my computers.  The computer that it does not work on has the following parts:

GeForce 8800GTX
Intel Core 2 Duo E6600 2.4GHz
Asus P5B Deluxe motherboard
NEC 20WMGX2 20.1" widescreen monitor
4GB Crucial Ballistix memory

I can actually boot from the CD and get to the screen where I choose my language (English) and then I choose to boot from the Live CD.  The screen goes black and there is some white text that says some stuff about the kernel mapping (I think this is normal) and after that it just goes totally black and never loads Ubuntu.

I tried the same CD on my wife's Dell computer and it works fine.  Can anyone help please?

---

### Post by David_1cog on 2008-03-08
That sounds similar to the problem I have, and your h/w specs are similar to mine.  Are you connecting DVD / HDD with SATA?  I think that could be the cause.

Adding 'irqpoll' to the end of the boot string fixed this for me.  F6 will provide the option to add this parameter during install.

If that solves the problem, you will also need to add 'irqpoll' to grub:

```
gksudo gedit /boot/grub/menu.lst
```

More reading at:
   [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)
   [http://www.google.com/search?aq=f&hl=en&q=irqpoll+sata+hang+boot+OR+install+site%3Aubuntuforums.org&btnG=Search](http://www.google.com/search?aq=f&hl=en&q=irqpoll+sata+hang+boot+OR+install+site%3Aubuntuforums.org&btnG=Search)

Good luck.

---

