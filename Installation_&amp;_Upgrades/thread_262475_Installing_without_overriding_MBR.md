---
title: "Installing without overriding MBR"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by facugaich on 2006-09-21
I was wondering if there's any way to install Dapper and not making it dual boot with XP or anything. If I start my computer I want it to boot directly to windows, keeping the current MBR. When I want to boot ubuntu I do it thourgh a boot floppy. Pretty much like that option during breezy install, that let's you choose between booting from the disk or from a floppy.

I have the ShipIt CD... the install program never asks anything about boot method... ant ideas?

---

### Post by facugaich on 2006-09-21
Damn, that features comes with the alternative CD... Does anyone know if I can do it with the shipped CD? I have no burner right now so downloading the Alternative CD ISO can't be of much help...

---

### Post by orb9220 on 2006-09-21
Why don't you just have xp as the first entry in grub so that it will boot  xp by default. Then you don't have to worry about losing or bad floppies.

[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by facugaich on 2006-09-22
I'd much rather install ubuntu with the least possible impact in my current system... This is the only computer I've got and my mom uses it for work, so I don't want to do risky stuff...

---

### Post by facugaich on 2006-09-23
Ok, how about this: I install GRUB on the MBR, then boot into ubuntu make a GRUB boot floppy, and then I boot with windows install CD and /fixmbr ? How would that work?

---

### Post by K.Mandla on 2006-09-23
Probably ... it's a little unorthodox, but I guess it could work. Are you sure it's not easier just to change the default boot option? You could even crank down the timeout so there's almost no pause.

---

