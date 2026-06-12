---
title: "Installed wubi but no prompt for ubuntu when rebooting"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by nomiezvr4 on 2011-01-04
Hey guys, I have windows xp and I installed wubi from their website. It seems simple and easy and I was expecting a prompt when i rebooted but it directly goes into windows.

How can I make the prompt show?

---

### Post by bcbc on 2011-01-05
The line "timeout=#" should have a # > 0
The following line should follow the Windows XP entry, usually at the bottom of the file:
C:\wubildr.mbr = "Ubuntu"

Post the contents of the c:\boot.ini file if you're not sure. IMPORTANT - if you mess up this file you could prevent windows from booting, and you'll get a hal.dll error. So backup beforehand and use Microsoft approved tools...

PS once you get Ubuntu booting, do not update packages grub-pc and grub-common as they are breaking Wubi installs at the moment (look under the "Recommended" updates within the Update Manager and unselect these)

---

