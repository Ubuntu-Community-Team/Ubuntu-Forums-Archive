---
title: "Boot Problem"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Joka999 on 2007-04-04
HI, I have a Sony laptop with dual boot ; WIndows XP and Linux Ubuntu. I restored both my drives as I had problems with Ubuntu. So when i restored both drives c: and d: when i turn on my laptop instead of having the boot options it says "Grub loading, error 15". I found out this is a problem caused by a file missing or something but i need a solution where i can keep my WIndows XP (Not completely wiping my hard drive). Any help appreciated.

---

### Post by zvacet on 2007-04-05
Try to restore grub.Bot up your CD and select **Recover broken system**
It will seems like you are doing instalation,but continue until you are asked to choose root device.Because you are dual booting probably it is second one.Good thing is if you choose wrong one never mind.Proces will procede only if you pick right one.Cd will mount it and go to the next dialogue.You will see several options but you pick Reinstall GRUB boot loader.After that it will ask where you want to install it.Type hd0.
When it is finished choose reboot.

---

