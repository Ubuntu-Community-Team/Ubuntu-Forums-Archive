---
title: "Can't run Live disk on Athlon Dual core"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by whistlerspa on 2008-07-04
My AMD Athlon 64 X2 Dual core with GeForce 7300 GS NVidea won't allow the live disk to boot into the GUI and halts half way through boot.

This happens whether I use the 64 or 32 bit Ububtu 8.04 disks. Consequently I'm unable to try Hardy on this box. Is there any fix for this or is this box simply Ubuntu incompatible I'm wondering?

---

### Post by Partyboi2 on 2008-07-04
What part halfway through boot is it stopping? Maybe removing the splash screen will provide some more info on where it is halting. Have you tried starting in "safe graphics" mode? Have you tried using some [[COLOR=Blue]boot options[/COLOR]]("https://help.ubuntu.com/community/BootOptions")? Another option if you are wanting to install it is to try the [[COLOR=Blue]alternate cd[/COLOR]]("http://releases.ubuntu.com/hardy/")

---

### Post by whistlerspa on 2008-07-08
Thanks the F6 option got the disk to work. But only to 800X600 mode. This has been the subject of many posts already. It seems to be a Nvidea issue with this distro

---

### Post by Rocket2DMn on 2008-07-08
Ubuntu should be compatible, but the LiveCD has limited support for some video cards and monitors.  If you were to install with the altnerate install cd, you would most likely be good to go when you boot up normally.

---

