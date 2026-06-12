---
title: "deleted /lib/modules/2.6.17-10-generic/"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by kebajonathan on 2007-07-18
Hi,

I was installing some modem driver when I hit "rm -rf *" inside of /lib/modules/2.6.17-10-generic/
The computer still starts up, but the mouse, usb, ethernet, ... don't work. what works is X11 (without mouse) and the keyboard. Even for example CD filesystems don't work any more. What works is what couldn't be deleted inside of "volatile" because it was being used. How can I repair this? Can someone help me? Thanks

---

### Post by 5-HT on 2007-07-18
Reinstalling your  2.6.17-10-generic kernel will bring back the modules (either remove the kernel and reinstall, or force a reinstall). If you have another kernel installed, it would be a good idea to boot into that one while you're fixing the issue.
cheers,

---

