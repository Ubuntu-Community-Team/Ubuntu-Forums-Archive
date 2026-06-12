---
title: "Oh dear- installation hangs after reboot"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by white_tiger_daniel on 2006-04-16
Well I stuffed up my computer a while ago and it was completely wrecked so I tried installing again. After the install when you reboot and it cofigures your packages, it hangs on configuring xserver-xorg. I have tried heaps with different cds and it still doesnt work. Any help?

---

### Post by Kapre on 2006-04-16
[QUOTE=white_tiger_daniel]Well I stuffed up my computer a while ago and it was completely wrecked so I tried installing again. After the install when you reboot and it cofigures your packages, it hangs on configuring xserver-xorg. I have tried heaps with different cds and it still doesnt work. Any help?[/QUOTE]

The error on "configuring xserver-xorg" means its having a problem with the grfx card (simply cannot show you the GUI). Try installing only the base or "server" then follow this [link]("http://doc.gwos.org/index.php/Minimal_Install") from the Ubuntu Docs only up to the "sudo apt-get update".

Then after that, enter "sudo apt-get install kubuntu-desktop" (if you like Kubuntu) or "sudo apt-get install ubuntu-desktop" (for GNOME or Ubuntu Desktop). After if finishes d/l and to change your resolution enter "dpkg-reconfigure xserver-xorg" to change the screen's resolution.

Hope it helps.

K

---

### Post by white_tiger_daniel on 2006-04-17
I think I have found out what is the problem. I installed anew grfx card a while ago. I'll try installing without the grfx card in and try and use integrated grfx for a while. If it doesnt work i'll try your solution.

Thanks heaps,

Daniel Marsom
Everyone's favourite nerd

---

### Post by white_tiger_daniel on 2006-04-18
Hi again. I tried installing w/o the grfx card. It didnt make any difference. I wold have tried your solution but the broadband over here is stupid and has a low data cap and I wanted to conserve data.

Thanks heaps.

---

### Post by white_tiger_daniel on 2006-04-24
Aha I have tried you solution K and it still didn't work so I looked at my X logfile and it says "Missing output drivers. Configuration failed." I need a driver for S3 Virge DX.

Thanks in advance

D

---

