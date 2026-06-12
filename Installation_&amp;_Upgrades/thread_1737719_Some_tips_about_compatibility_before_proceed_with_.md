---
title: "Some tips about compatibility before proceed with setup?"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Fred2040 on 2011-04-23
Hi  people, I have an ubuntu instalation ready to fly  and I want a VMware  test. Then, I need to  know something important.. If I make a Windows  Virtual Machine, can this  VM run StarCraft2?
As you can see, it's  about use maximum resources  with graphics card and not at all with CPU,  and no only games, apps like  for example, 3dsmax..
Is VMW fully compatible with OpenGL 2,3 or 4, and/or DirectX 9,10?
Thks alot srs!
Best Regards
:guitar:

---

### Post by earthpigg on 2011-04-23
No, modern 3d games on modern hardware will not run well in a Virtual Machine. 

If you pulled hardware from the future, or were trying to play games from the past - perhaps. (If you do pull some hardware from the future, can you please send me a video card from 2025?)

Wine is what Linux Gamers tend to use. Here is [how well]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882") starcraft 2 is reported to run on Wine. Please be sure to read up on what wine is, and what limitations it has, before setting your expectations to high -- Windows will always be the best and most reliable platform to run Windows games on.

(Also: Most Linux users tend to prefer VirtualBox to VMWare for windows *productivity* applications, though that isn't unanimous.)

---

### Post by earthpigg on 2011-04-23
Er, I forgot to mention:

If you are anything approaching a serious gamer, I suggest dual-booting Windows and Ubuntu. A true dual boot, not a wubi install.

Find documentation on how to fix Ubuntu's bootloader once Windows breaks it (ie: every few Windows updates), print it, and keep it handy. 

One added advantage to a dual-boot approach is that if the *only* thing you use your Windows install for is gaming, security on Windows becomes much less of a concern. Rumor has it that many people with such a setup un-install antivirus software as a result of the decreased level of concern that comes with this.

---

### Post by Fred2040 on 2011-04-23
Whoa indeed 

Thks!

---

