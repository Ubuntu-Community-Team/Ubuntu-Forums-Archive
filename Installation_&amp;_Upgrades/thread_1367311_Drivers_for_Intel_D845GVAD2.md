---
title: "Drivers for Intel D845GVAD2"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by mfainter on 2009-12-29
I'm running Ubuntu 9.04 (newest version).  I have an Intel D845GVAD2 all integrated MOBO.  Ubuntu found all the drivers i needed except for the Video driver.  My display is horribly large, and i'm having trouble finding a video driver for this board.  I've got my board disc, but it's only got Windows drivers on it.  Any ideas?

---

### Post by avtolle on 2009-12-29
Take a look at [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) and see if this helps.

---

### Post by mfainter on 2009-12-29
i can't edit the /etc/apt/source.list file.  I'm logged in as power user.

---

### Post by Mark Phelps on 2009-12-29
When you open a terminal, look at the prompt character.  If it's a "#", you're logged in as root; if it's a "$", you're logged in as a normal user.

To edit a file as root, enter "gksudo gedit <filename>", substituting the full name of the file for "<filename>".

---

### Post by avtolle on 2009-12-29
> **Mark Phelps said:**
> When you open a terminal, look at the prompt character.  If it's a "#", you're logged in as root; if it's a "$", you're logged in as a normal user.

To edit a file as root, enter "gksudo gedit <filename>", substituting the full name of the file for "<filename>".
To amplify, if needed, using your example mfainter:```
gksudo gedit /etc/apt/sources.list
```Good luck.

---

### Post by mfainter on 2009-12-29
Ok, i went through the steps and restarted the system, but still no luck.  I still only have 640X480 resolution setting.  Sorry for the bash questions, i'm more used to using Fedora and the enable commands rather than sudo.

---

