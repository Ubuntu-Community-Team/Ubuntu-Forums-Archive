---
title: "GRUB won't recognize my keyboard"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by Ruke47 on 2007-07-02
Excuse me if I ask/say anything stupid, but I'm reasonably unexperienced at this.  I've installed Ubuntu off of the liveCD, using default settings on everything except install location. (I installed to hdd, as hda and hdb are windows drives, and hdc is my DVD-RW.) When I boot my system, and the bootloader pops up, my keyboard goes dead. I can't select which OS to boot, type anything, hit F1, etc. I know that the keyboard works **before** this point, because I've got a BIOS password set up. As soon as the count-down expires and I boot into Ubuntu, the keyboard becomes functional again.

If it helps, I'm using a Microsoft USB ComfortCurve keyboard, an nForce2 motherboard, and an AMD 2500+ processor. Anyone have any idea how I can solve my problem?

---

### Post by rillip on 2007-07-03
I had this happen with me as well. It would work in the bios area, it would work in Windows, but not at grub.  I found that my bios had a setting for where USB keybaord was provided, by the OS or the Bios.  It was set to OS.  I switched it to bios and it worked fine.

---

### Post by Ruke47 on 2007-07-03
Thanks! The "USB Legacy Keyboard" option in my BIOS settings fixed the problem.

---

