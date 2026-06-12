---
title: "LiveCD wont boot &amp; can't install"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by mightyball on 2005-10-15
I am having trouble with Breezy. I'm trying to boot the LiveCD just try it out before wiping out my working FC4 install, but the booting locks up after the ACPI lines. I've disabled ACPI and it locks up at the same place, just without the ACPI lines. 

System:
DFI AD77 Motherboard
AMD XP2600+
1GB ram
GeForce 4800TI
SBLive!

I've tried to install 5.04 in the past, and had the exact same problem on the initial post-install bootup. 

Any ideas?

---

### Post by se0siris on 2005-10-16
Just Googled your motherboard and found that it has integrated AC97 sound?

Try disabling this in your BIOS if it isn't already. It caused the LiveCD and install to crash on my machine. I disabled the on-board sound and put in a SBLive! card and everything runs fine.

Hope that's of some use to you.

---

### Post by mightyball on 2005-10-19
[QUOTE=se0siris]Just Googled your motherboard and found that it has integrated AC97 sound?

Try disabling this in your BIOS if it isn't already. It caused the LiveCD and install to crash on my machine. I disabled the on-board sound and put in a SBLive! card and everything runs fine.

Hope that's of some use to you.[/QUOTE]

Thanks, but that didnt help either. I went through BIOS and disabled everything i could find that i didnt think i needed, and still nothing. I dont understand why its not booting.

---

