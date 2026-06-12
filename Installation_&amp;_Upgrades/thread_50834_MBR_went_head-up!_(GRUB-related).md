---
title: "MBR went head-up! (GRUB-related)"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by Monolith on 2005-07-21
Hello all! I've searched the forums for my questions but I couldn't find anything that looked like my problem, so here goes.

When installing Hoary Hedgehog on my laptop (WinXP pre-installed), the first time I rebooted to the GRUB loader, it wouldn't boot anything. The only rescue I thought of, was to re-install Ubuntu and try again. After that, things went smoothly.

Now the time had come for me to install it to my desktop computer (also WinXP installed). (Specs: XP2600+, 1.2Gb, HD0: (pri. master) Maxtor 80Gb w/WinXP, HD2: (sec. slave) Samsung something 4Gb, empty). Installed with all the default options (leave HD0 alone, make /ext3 and swap on HD2:, etc. GRUB then detected WinXP and made me a boot menu.

All went tickety-boo, until the first reboot to GRUB. Rebooting got me nowhere except GRUB yelling "Error 17" at me.

Fine, says I, and re-installed Ubuntu, hoping that it would be the same fluke as on my laptop. Wrong! It keeps getting stuck at "Error 17".

Fine, says I, a bit distressed, and re-installed Ubuntu, now installing GRUB on a floppy disc. Rebooting got me the familiar GRUB-bootloader. But after rebooting, the floppy apparently went head-up, because all I got was "GRUB". Nothing more or less, just "GRUB".

So before I turn to the XP install disc to run fixmbr, what did I do wrong? Is there some sort of enormous, stupid error I'm making?

Any help appreciated,
Robin

---

### Post by Monolith on 2005-07-21
Well, I followed some of the steps in another GRUB-related thread here, entered the rescue-mode on the install CD.

but when entering #fdisk -l all I got was: "couldn't find /proc/partitions"

What's going on here?

---

