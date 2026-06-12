---
title: "Help! Ubuntu upgrade to 15.04 broke pc!"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by noah31 on 2015-11-15
Hi all, I was upgrading my rig ( Intel core2quad 760, 4 GB ram, Intel dh55tc mobo, MSI Radeon r9 270x) from 14.10 to 15.04 and everything downloaded and installed fine, but after a reboot the system stuck on the purple Ubuntu loading screen (does respond to alt/printsc/b though ) :). I have no idea why it has done this. I tried using the upstart option, same thing. I also used the recovery option, which I can get into. The last thing I've tried is running aticonfig --initial to see if the graphics driver was causing issues. Nothing. Can you please help me, I want to get back to Minecraft!

UPDATE: I was poking around in the logs and I noticed in lightdm.log says it started x server, then the server stopped and returned 127. Dunno if that's helpful or not.

UPDATE: NEW PROBLEM! I got back into the system by deleting fglrx, but now that I'm at the login screen, I put in my password, but it takes me back to the login screen. GRRRRRR!

---

### Post by Vladlenin5000 on 2015-11-15
Hi and welcome.

15.04 will be out of support in a couple of months therefore no point in upgrading to that release.
You should do your backups if you haven already - use a live session if you must - and then do a fresh install from scratch with 15.10. Do NOT install fglrx yet. There's a specific problem with the AMD drivers and the current release but it should be solved quickly. There's a workaround using the proposed repository that apparently works but that's a matter for another thread.

---

### Post by noah31 on 2015-11-15
I've figured out that Unity is the issue here, now to fix it...

---

### Post by Vladlenin5000 on 2015-11-15
Nothing else to add.... Backup, reinstall, done.

---

### Post by noah31 on 2015-11-17
Yeah, after fiddling with it to see if I could fix it, I decided to do a clean install of Ubuntu 15.10 and I am regretting it. Minecraft glitches out when I go fullscreen. I know that's caused by the radeon display driver, but I can't install fglrx! I think I am going back to the LTS since they have broken a lot of stuff here, and I don't feel like cleaning up their mess. More gaming, less bashing the keyboard against the wall trying to get Ubuntu to behave!

---

### Post by Vladlenin5000 on 2015-11-17
The stability of a LTS is a plus indeed.
However, the issue with fglrx in 15.10 isn't that bad:

1. It'll be fixed sooner than later and
2. There's a workaround already.

I'm posting right now from a dirty cheap all AMD laptop running 15.10 with AMD 15.20 drivers and Catalyst Control Center 2.21.

---

