---
title: "Installation issue of Ubuntu 11.10"
date: 2012-01-14
forum: Installation &amp; Upgrades
---

### Post by psisa_filin on 2012-01-14
[FONT="Arial"]Hi there****! I have tryed installing **Ubuntu 11.10** for many times (*any version of dist*), but always got the same result - screen is out, so I can not see any boot menu of the installer. It looks like you have some color stripes on it and after a few seconds a screen is turning off. I've even tryed the alternate install - it work fine, but when I've got to load a first log-in session - the same effect appeared (*screen off*); When I tryed the safe-mode - it just hangs on the select menu of it. Previous Ubuntu versions worked fine, beside the 11.04 - by safe-mode I installed the propriate drivers.
By the way - I have tryed other linuxes (newest) - almost the same result.

Does anyone know some way to install new Ubuntu with workable graphics?

My hardware:
[SIZE="1"]Intel(R) Core(TM) i3 CPU 540
Gigabyte Technology Co., Ltd. H55M-S2V
RAM - 4GB
AMD Radeon HD 6700 Series[/SIZE]
[/FONT]

---

### Post by IPEX-731BA5DD06 on 2012-01-15
Look in the Problems sticky file.

I remember, only because I have NVidia and not ATI, that ATI can cause graphics problems.

There is a list of things to do for ATI Graphics cards.

Apart from that, system seems fine, are you using 32 Bit or 64 bit system?? as well.

---

### Post by 2F4U on 2012-01-15
Here is a troubleshooting guide which may help:

[https://wiki.ubuntu.com/X/Troubleshooting](https://wiki.ubuntu.com/X/Troubleshooting)

Many are successful in loading Ubuntu by adding nomodeset as grub kernel boot parameter.

---

### Post by psisa_filin on 2012-01-15
I have a long win 7 x64; I've tryed both OS types (x86 & x64) - same effect. I can see workable grub (after install), but my problem is that I can not see anything on the installation (after I see keeboard and a man pictures on the purple screen).

---

### Post by dino99 on 2012-01-15
first remove /etc/X11/xorg.conf if it exist, and try nomodeset

---

### Post by psisa_filin on 2012-01-15
dino99, what did you mean by that? Delete it from existing OS?
I have installed Win7 and Ubuntu 10.10 along side (I want to erase 10th and install 11.10).

---

### Post by darkod on 2012-01-15
Can you run a 11.10 lice cd in live mode successfully?

---

### Post by psisa_filin on 2012-01-15
darkod, I can not run live mode successfully - black screen (no signal).

---

### Post by darkod on 2012-01-15
Boot with the live cd and immediately on the first purple screen, hit Esc. That should show you the older type text menu.
With the Try Ubuntu option highlighted, hit 'e' for editing the boot lines.
Move with the arrows keys to position the cursor in the line starting with linux, and before 'quiet splash' add radeon.modeset=0

Press Ctrl + X to boot. If that works and boots you in live mode, let us know.

---

### Post by psisa_filin on 2012-01-15
darkod, it was not successful, but I've install with nomodeset. But when I try to load first OS session (after install) got same problem. I tryed safemod - got menu and turned off keyboard, but active mouse (lighted up). That safemode is hanged up - ctrl+alt+printsrc+b did work. Not sure what to do now...

---

### Post by darkod on 2012-01-15
If you installed with nomodeset did you try booting with it too? Did you enter it into the grub config?

If you don't get the grub menu at boot, press Shift to show the menu.

Once it shows, when the ubuntu entry is highlighted, press 'e' for edit and do the same with nomodeset.

Does that boot correctly?

---

