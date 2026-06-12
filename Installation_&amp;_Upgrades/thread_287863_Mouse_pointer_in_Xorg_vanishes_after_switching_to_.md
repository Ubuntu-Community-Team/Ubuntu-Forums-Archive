---
title: "Mouse pointer in Xorg vanishes after switching to console and back"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by jrial on 2006-10-29
After the upgrade to edgy some stuff broke. Fixed most of it myself, but this one eludes me: the mouse pointer works flawlessly when I boot the machine, but once I switch to the console (tty) and back to Xorg/Gnome, my mouse pointer becomes invisible. It's still there; I see the tooltips when I hover it over items in the panel. It's just invisible...

The only warnings/errors in my Xorg.0.log file are the following (pasted them all, even the obviously irrelevant ones, for completeness' sake):

```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): config file hsync range 43.8857-48.5053kHz not within DDC hsync ranges.
(WW) I810(0): Bad V_BIOS checksum
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
        (Cannot allocate memory)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
        (Cannot allocate memory)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
        (Cannot allocate memory)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
        (Cannot allocate memory)
(WW) I810(0): xf86AllocateGARTMemory: allocation of 14593 pages failed
        (Cannot allocate memory)
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019023l.pfb: 1
(last one repeated multiple times)
```

none of which seem to impact my xorg in any way.


Any ideas?

---

### Post by jrial on 2006-10-29
Update: while this isn't a real fix to the problem, I now found a way to at least mitigate the damage by closing the lid and opening it again. Somehow, something must get reinitialized during the process, because after I close the lid and open it again (or manually manipulate the lid switch), the mouse pointer appears again.

Sucks having to log in again every time I switch to the console and back, but at least my running X session isn't ruined anymore...

---

### Post by psyke83 on 2006-11-03
jrial,

Do you have an Inspiron 510m laptop, and/or an Intel 855GM chipset? I have the same problem as you, but the workaround doesn't work. I'm more concerned about the Xorg warnings, as 3D performance is worse on Edgy than on Dapper (~1300fps in Dapper 1024x768@16bit, ~800fps in Edgy 1024x768@16bit).

---

