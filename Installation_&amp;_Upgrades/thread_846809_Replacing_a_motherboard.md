---
title: "Replacing a motherboard"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by tobiasly on 2008-07-01
I'm planning to install Hardy on an Epox Socket-939 based AMD board and Athlon-64 I have but may upgrade it to an AM2 based board (and Athlon-64x2 or Phenom) in the near future. If I do upgrade, will Ubuntu figure it out and adjust the drivers as necessary? Is there anything I should do now to make the possible upgrade easier?

Also, new motherboards usually come with CDs containing drivers for Windows XP that supposedly help the OS get better performance from the board; are these already included in Ubuntu or do I need to look for a motherboard that has Linux drivers available?

---

### Post by Pumalite on 2008-07-01
You can upgrade, but a clean install is better. If you do upgrade; remove all third parties from your /etc/apt/sources.list, including the Medibuntu folder if you have added that repo. Make sure your OS is fully updated before you attempt the upgrade.

---

