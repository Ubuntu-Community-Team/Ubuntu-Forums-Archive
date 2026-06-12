---
title: "X problems in custom install when system runs gdm/wdm"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by gasphemer on 2007-12-09
I downloaded the mini.iso of Ubuntu Gutsy to build a custom lightweight Ubuntu on an old Pentium 1 w/MMX 200mhz w/256 mb of ram I had lying around.  I chose the mini.iso because for some reason the CD drive will hang and produce errors if I used it.  So I installed the command-line system, and set LILO as the bootloader.  Personal preference :)

So there I was with the Ubuntu cli.  I log in and follow the directions for installing a minimal system in the Ubuntu wiki.

```
sudo apt-get update
sudo apt-get install menu xterm firefox wdm synaptic icewm xorg
```

after it was all installed, I typed in "startx" to start x and it gave me a bunch of snow and moving lines.  Is this a problem with xorg?  I try hitting Ctrl-Alt-Del and it just blanks then gives me that screen again so I can't edit anything... I'm lost!

---

### Post by PmDematagoda on 2007-12-09
Did you try running:-

```
sudo dpkg-reconfigure xserver-xorg
```

To configure your Xserver?

---

### Post by gasphemer on 2007-12-09
Nope... whoops.  I'll do that.  Is there a keyboard shortcut or something to exit X and get back to the terminal so I can type that? :)

---

### Post by totalnub on 2007-12-09
ctrl-alt-f1

---

### Post by gasphemer on 2007-12-09
Thank you!

---

### Post by PmDematagoda on 2007-12-09
Did it work properly?

---

