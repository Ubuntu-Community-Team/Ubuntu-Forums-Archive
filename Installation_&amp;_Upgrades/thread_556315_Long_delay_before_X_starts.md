---
title: "Long delay before X starts"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by jeeves on 2007-09-21
I just installed Xubuntu Feisty on a Gateway MFATXPNT GSX 500S. Everything seems to be working fine except there is a **delay of about 2 minutes between the GRUB menu and the X window system starting.** Anyone know what could be causing this?

Interestingly enough, if I log in as root using the recover option in GRUB and run "startx", the GUI comes up without delay. Weird.

---

### Post by Soybean on 2007-09-21
It's probably some sort of driver thing that's slowing down your booting. The fact that things go faster in recovery mode suggests that maybe the driver in question isn't loading when you go that way. A common cause of this in laptops is the wireless driver -- sometimes it loads up, then searches for an access point before it allows anything else to continue.

There's a tool called "bootchart" that you can install from Synaptic, that can be used to diagnose boot problems. However, actually sorting out what it means, and how to fix it, is kind of tricky. For example, I was able to make my laptop boot faster, but now there's about a 50/50 chance that the wireless card just won't work, and I'll have to reboot to fix it. ;) So... if you're feeling ambitious, you can probably improve your boot speed. Personally, I wish I had just left it alone.

---

