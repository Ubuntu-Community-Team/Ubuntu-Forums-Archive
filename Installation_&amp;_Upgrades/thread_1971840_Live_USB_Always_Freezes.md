---
title: "Live USB Always Freezes"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by cg2916 on 2012-05-02
I have tried unetbootin, LiLi, and Universal USB Installer, but they all freeze on the SYSLINUX "intro" screen. How do I make the Live USB actually work?

---

### Post by DemonSharkKisame on 2012-05-03
Do you have a Broadcom wireless chip? That's what was causing my live USB to freeze... I had to blacklist it by adding "blacklist.b43=yes" to my boot options (accessed by either F6 or TAB at the boot screen), and everything loaded fine after that.

---

### Post by cg2916 on 2012-05-03
> **DemonSharkKisame said:**
> Do you have a Broadcom wireless chip? That's what was causing my live USB to freeze... I had to blacklist it by adding "blacklist.b43=yes" to my boot options (accessed by either F6 or TAB at the boot screen), and everything loaded fine after that.

Atheros wireless, Broadcom ethernet. Would that make a difference?

---

### Post by DemonSharkKisame on 2012-05-03
> **cg2916 said:**
> Atheros wireless, Broadcom ethernet. Would that make a difference?
*Possibly,* though I'm not entirely sure since Atheros is supposed to have excellent Linux support. I wouldn't doubt that your Broadcom ethernet card would be the culprit though; I would suggest tapping either your up or down-arrow key while Ubuntu is loading (before it freezes) to see if you get a missing firmware message.

---

### Post by bohemian9485 on 2012-05-03
> **DemonSharkKisame said:**
> Do you have a Broadcom wireless chip? That's what was causing my live USB to freeze... I had to blacklist it by adding "blacklist.b43=yes" to my boot options (accessed by either F6 or TAB at the boot screen), and everything loaded fine after that.

That's strange. My netbook comes with Broadcom BCM4313 wireless chip. Since it has no DVD-ROM drive, all OS installations were done using live USB. I've tried all Ubuntu versions starting from 10.04 Lucid. Even when the lower versions could not detect my wireless chip properly, it has no trouble booting into live session.

IMHO, it could be the USB drive that has some defects.

---

### Post by DemonSharkKisame on 2012-05-03
> **bohemian9485 said:**
> That's strange. My netbook comes with Broadcom BCM4313 wireless chip. Since it has no DVD-ROM drive, all OS installations were done using live USB. I've tried all Ubuntu versions starting from 10.04 Lucid. Even when the lower versions could not detect my wireless chip properly, it has no trouble booting into live session.

IMHO, it could be the USB drive that has some defects.
You sure? Were you able to boot into a 12.04 live session even without firmware? I've found that 12.04 is the first version of Ubuntu to just flat-out refuse to boot thanks to my desktop's wireless chip (a Broadcom B4318 ); previous Ubuntu versions would detect missing firmware, but boot anyway. I'd suggest trying to blacklist your wireless chip upon boot to see if your live USB will boot before assuming it's defective.

---

