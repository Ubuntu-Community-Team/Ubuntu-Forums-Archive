---
title: "Partitioning questions"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by cddot on 2007-09-03
I have a Windows XP NTFS partition, plus an unused partition.
On the unused partition, I installed 7.04 which went OK. This created an Ubuntu partition and a swap partition, and installed GRUB and the boot menu.  So now I have a choice of booting Windows or Ubuntu. In fact, I have 3 menu choices: Windows, CD installed Ubuntu, and updated version of Ubuntu.
Now, I want to install another distro, say SUSE. Unfortunately, I made the Ubuntu partition too large, and left no unused space.
Questions: 
1) Can I resize (downsize)  the Ubuntu partition? (the swap partition is fine). What is the recommended tool?
2) Will another distro update GRUB, and the menu.lst or will I have to do something else first? (I understand that will depend on the distro, but a "in-general" answer will do).
3) If I decide to install further distros, is there a practical limit I should be aware of? (I'm thinking the MBR doesn't sound like it's that big)
I have read GRUB documentation, but I seem to pick documents that are far too technical, and does not address the simple questions I have, plus I prefer to keep my Win partition intact. So I thought I'd ask first. Thank you for listening.

---

### Post by merlinus on 2007-09-03
1.  gparted live cd: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

2.  you will probably have to do sopme editing of menu.lst and perhaps even reinstall grub.  not difficult.  

supergrub is an excellent tool for the latter.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

3.  I think it would primarily depend upon how much free hd space.

-merlin

---

