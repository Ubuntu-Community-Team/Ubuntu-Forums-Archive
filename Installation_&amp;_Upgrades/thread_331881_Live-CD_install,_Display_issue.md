---
title: "Live-CD install, Display issue"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Uta on 2007-01-05
I have a Dell C800 with a ATI Rage Mobility M4 graphic's card. When I boot from the live CD the screen splits into 3 sections. I have tried this in the "Safe Graphics" mode and also with the boot option of vga=771 and using vesa, nothing stops the screen from being split. This didn't happen with Dapper. I know there are those who went ahead and install via these screwy graphic conditions and then fixed the issue afterwards but that seems too visually challenging when tring to reformat a drive and you can't really see what's going on. Is there a way to actually boot the Live-CD with readable graphics? Thanks!

---

### Post by Uta on 2007-01-05
I solved my own issue. I booted the live-cd, I got the 3 way split screen. As root I opened gedit and edited xorg.conf, changed "ati" to "vesa" saved the file. Created a new user in the terminal. Logged out and then logged back in, the screen display was now correct. I installed Edgy, rebooted and the screen display with the new install was fine.
With a stable install of Edgy I have gone back to the xorg.conf and edited, "vesa"  back to "ati" and added this:
HorizSync  28-70 and VertRefresh 43-60 in the Section called "Monitor" reads as this:

Identifier  "Generic Monitor"
Option      "DPMS"
HorizSync  28-70
VertRefresh 43-60

Additionally I downloaded and installed "Easy Ubuntu" which installed the ATI drivers I needed and things look great!

---

