---
title: "GRUB does not load after warm boot"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by njhepler on 2007-12-10
Hello:
I am running dual boot machine (Windows XP SP2 & Ubuntu 7.04 Feisty Fawn). I have noticed that after running Ubuntu and attempting a restart or "warm boot" my system freezes after BIOS runs and before GRUB starts. Anyone know why this would happen?

---

### Post by PmDematagoda on 2007-12-10
Does GRUB still load?

If so then your problem may be that the BIOS is looking at the other devices to see if it can boot from it, such a thing as a CD in the CD-ROM can slow down the PC's starting up process if the CD-ROM is the first in the Boot Device Priority in the BIOS.

---

### Post by petterth on 2007-12-10
HellO, I'm running a quite old Asus p4b 1,6 Ghz and had the same problems caused by too high cpu temperature, i know i should probably buy a new fan but instead i settup bios to ignore the temperature and it's working.

Don't know if this helps, but anyways.

Cheers.

---

### Post by njhepler on 2007-12-11
> **PmDematagoda said:**
> Does GRUB still load?

If so then your problem may be that the BIOS is looking at the other devices to see if it can boot from it, such a thing as a CD in the CD-ROM can slow down the PC's starting up process if the CD-ROM is the first in the Boot Device Priority in the BIOS.

No GRUB does not load, there is no CD mounted

---

