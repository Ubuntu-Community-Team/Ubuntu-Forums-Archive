---
title: "Ubuntu 14.04 Server - Unable To Install Grub"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by Asif_Ahmad on 2014-04-26
Hey Everyone,

I'm not new to the Ubuntu world, been using the desktop off and on for the past few years.  But recently, I tried installing Ubuntu server on an old desktop I have, and I got greeted with the following error: "Unable to install GRUB in /dev/sda."

This machine has windows 7 on it currently, and I was hoping I could install it along-side of it.  It seemed to detect Win7 just fine, and said everything is cool to install Grub, but it fails for some reason.  

If anyone could offer any assistance, it would be greatly appreciated.  TIA!

--Asif

---

### Post by TheFu on 2014-04-26
I had an issue with 14.04 Server on my laptop. Never figured out what the problem was, but I think it was the wifi.  Try disabling that in the BIOS and installing again.  BTW, "14.04 Desktop" installed fine, so it is definitely something different between the desktop and server releases.

You got farther than I did on the install ... mine stopped before loading any packages, so it probably is NOT the same root cause.
If you can run the **boot-info** script, we can probably help with the grub-install command. By signature has instructions.

---

