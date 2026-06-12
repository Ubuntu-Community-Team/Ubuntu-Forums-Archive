---
title: "installing Ubuntu without GRUB"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by alfredlau on 2007-05-19
Is it possible? GRUB is pissing me off. I've managed to get Vista back, and I think I love its bootloader more than that stupid GRUB.

So is it possible to install Ubuntu without GRUB? I can't do a repair using Vista's installation disc (weird I know).

---

### Post by louieb on 2007-05-19
The short answer is no. But you don't have to change the MBR of the hard drive. You just tell the installer to put the GRUB initial program loader (IPL) in the boot sector of you Linux / (root) partition. After you do that then [Booting Using NTloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=351692")

---

