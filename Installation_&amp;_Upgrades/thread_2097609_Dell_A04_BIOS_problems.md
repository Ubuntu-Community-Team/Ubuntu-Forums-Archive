---
title: "Dell A04 BIOS problems"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by korgoth28 on 2012-12-23
I bought an old Dell DV051 computer to dual boot windows XP and lubuntu. Both worked, however it was in some weird RAID mode, which kept grub2 from detecting windows. So I ran dmraid -rE. The BIOS couldn't find any hard drives at all, so I reset it (the BIOS). Grub didn't come up, and windows had a blue screen of death that said STOP: 0x0000007B

When I physically switched which cord (both are SATA) connected to which hard drive, grub came up, and lubuntu works fine, and can access windows. Booting windows from grub still gives me STOP: 0x0000007B.

I backed up my important stuff, but I don't have the windows xp install disk. How can I get windows to boot again?

Sorry if this is in the wrong place; could you direct me to a good place to ask, if that's the case?

Thanks in advance

EDIT: I should mention that there's some weird metadata stuff going on with the boot sequence. It detects the secondary hd in the list of hardware, but doesn't show it in the boot sequence. It only wants to boot the "internal" hard drive (they're both internal) which is why I physically switched the cords. Also it's windows xp media center. I didn't touch the hard drive at all, and there's no reason to think it would have coincidentally been damaged. So I'm totally baffled as to why windows suddenly forgot how to boot.

---

### Post by korgoth28 on 2012-12-23
Just turning raid back on let windows boot. Can't use grub, but oh well.

---

