---
title: "[SOLVED] mythbuntu hijacked grub, how do i switch it back?"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by ahumin on 2008-11-21
i know there are a lot of similar issues out there but i've searched and cannot find the relevant info. the cause was me trying out different linux OSes to find a decent open source alternative to dell's windows-xp-based mediadirect 3.5.

i am trying out mythbuntu but it has hijacked grub (even though i told the installer not to install a boot loader). grub is now using the [FONT="monospace"]/boot/grub/menu.lst[/FONT] on [FONT="monospace"]sda3[/FONT] but i want it to keep using the one on [FONT="monospace"]sda1[/FONT] because i will eventually set the second OS to boot using the mediadirect button on the laptop.

how do i make grub use the [FONT="monospace"]menu.lst[/FONT] on [FONT="monospace"]sda1[/FONT]?

---

### Post by caljohnsmith on 2008-11-21
Fortunately, what you want to do should be easy, just do the following in a terminal:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And then Grub in the MBR will use the sda1 partition for its boot files, including menu.lst. Let me know how it goes. :)

---

### Post by ahumin on 2008-11-22
perfect, that fixed it. i never would have guessed that from the grub man page and clearly i was not googling for the right words.

---

