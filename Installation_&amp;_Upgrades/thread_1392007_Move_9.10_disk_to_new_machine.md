---
title: "Move 9.10 disk to new machine"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by brianmc on 2010-01-27
I've been landed with a disk from a friend whose machine we've never managed to get into the BIOS of and tweak the boot order to include a CD drive.

I pulled the disk from my own system and ran a from-scratch install on this shiny blank disk with numerous of the tweaks I like and he'll need. (Getting pleased with how the time to usable is still dropping doing an install).

What I'm concerned about is sticking this disk in his machine and using it. I've gone with the sort-of generic 32-bit base even though both his machine and mine are Athlons. However, he's a musician and has some rather nice audio kit - as well as, I suspect, different video hardware.

Am I likely to hit noticeable problems? Is there some script I can arm myself with to rescan available hardware and update config, or can someone give a list of packages to completely remove then reinstall via the recovery boot?

I know the latter option may well cause some dependency problems that see stuff I've already installed lost - I can cope with that if I can get the GUI running smoothly.

---

### Post by dabl on 2010-01-27
You probably have already done more than would be advisable -- you want NO drivers at all, in that situation.  Not ethernet, not audio, not video, unless his motherboard is the same as your motherboard.  But, being Linux, if it will boot to the command line, you can probably remove anything that is not wanted, and then install the appropriate drivers for his hardware.

---

