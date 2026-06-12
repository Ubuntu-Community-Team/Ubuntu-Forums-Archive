---
title: "Radeon HD 8400 (AMD A6-5200 APU) - No Graphical Install/Live Boot"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by slooksterpsv on 2014-01-25
I know why this isn't working, in the log files it's looking for a "compatible" module for the Kabini Radeon HD 8400 series graphics (newer, last generation (just before the R2xx series). My question is, is there a way to force this to work? nomodeset doesn't work, I've tried elementary OS, Xubuntu, Linux Mint 16 - I'm considering trying OpenSuSE. There's one last option I'm going to try and that's xforcevesa to see if maybe that'll force a Vesa driver (probably won't).

Any other ideas besides doing a VM, building a live cd with the fglrx drivers already installed?

---

### Post by slooksterpsv on 2014-01-25
Fixed:

In a terminal I ran:
```

Xorg -configure
[/code

Then:
[code]
sudo cp ./xorg.conf.new /etc/X11/xorg.conf
sudo lightdm

```

---

