---
title: "Dual boot, from xp and dapper to xp and edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by brian.leroux on 2006-10-30
Hey folks, I'm sorry if this seems painfully obvious or has been answered in the past. I've done a little searching but my question is probably so obvious its probably not quite ever directly answered. 

So, I'm just about to pull the trigger on a fresh edgy install (I've made a mess of dapper getting to know it). 

I currently have dapper on one partition and xp on another. I still use xp daily for my work and dual boot w/ grub.

Question is, when using the iso graphical installer it appears edgy will install a new instance of grub. [COLOR="Blue"]Will I still have the xp options when all is said and done?[/COLOR]


Thanking you all in advance --- Ubuntu rawks!

Cheers,
Brian

---

### Post by Neobuntu on 2006-10-30
Yep.

Later when you learn to edit your GRUB "menu.lst" file, you can even set it to (timeout) and default boot to the LAST (XP or Linux) OS started. Windows seems to need this because it likes to reboot a lot. This way Windows reboots to Windows and Kubuntu reboots to Kubuntu (Unless you choose differently on boot, of course).

---

### Post by brian.leroux on 2006-10-30
Rawkin, thx for the grub.lst tip too. Install was smooth, windows and edgy playing nice side by side. Thanks very much!

---

