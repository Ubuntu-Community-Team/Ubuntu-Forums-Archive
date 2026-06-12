---
title: "usb keyboard fails to work in grub"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by meaghann on 2010-05-17
[LEFT]I installed Ubuntu 10.04 LTS to dual boot with Win Xp and everything went fine with the installation untill I went to boot back into Windows. My keyboard fails to respond in the boot loader so I am stuck with the default setting of booting back into Linux. To be clear, the keyboard works when the BIOS loads, I can hit DEL and go to the BIOS menu, etc, it's only when I hit the boot loader. The keyboard also works fine in Linux and Windows.

Any ideas?
[/LEFT]

---

### Post by oldfred on 2010-05-17
I had this issue a year or so ago when I put in a new motherboard. I was able to use a ps/2 adapter while in the grub menu. but it was not easy to quickly add & swap adapters. It turns out to be a setting in BIOS. Older systems ignored BIOS settings and just worked. New one's read the BIOS and may not.

---

### Post by scottwd on 2010-06-15
I have what may be the exact opposite problem.  System is on a boat and we must run without a keyboard.  System halts during boot with keyboard not plugged in, in direct contrast to your problems where boot fails with keyboard attached.

(1) At which system version is the transition from BIOS being ignored (and keyboard existence presumably not known) and same BIOS read for validation of keyboard existence.

(2) Is there a configuration option (my initial guess is kernel configuration) to command system to ignore presence/absence of keyboard?

---

