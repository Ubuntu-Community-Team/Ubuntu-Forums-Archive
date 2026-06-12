---
title: "Install hangs on Time Zone Selection (VirtualBox on Win7 Host)"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by kadaan on 2011-06-06
I'm having trouble installing Ubuntu 11.04 in a VirtualBox VM on my Win7 host machine. I gave the VM 1024M RAM and an 8G drive. I have ubuntu-11.04-desktop-i386.iso as my install image.

Each time I try to install it, it hangs on the "Where are you?" timezone selector. The last entry in the log is "ubuntu ubiquity[2818]: switch to page timezone".

I can move the install pane around, but no mouse clicks register inside the window. The network/sound/system menu items in the top right all work fine (although the icon remains the waiting icon and no a pointer/hand.) There is no disk/cd/network activity on the indicators.

Any ideas?

---

### Post by collisionystm on 2011-06-06
> **kadaan said:**
> I'm having trouble installing Ubuntu 11.04 in a VirtualBox VM on my Win7 host machine. I gave the VM 1024M RAM and an 8G drive. I have ubuntu-11.04-desktop-i386.iso as my install image.

Each time I try to install it, it hangs on the "Where are you?" timezone selector. The last entry in the log is "ubuntu ubiquity[2818]: switch to page timezone".

I can move the install pane around, but no mouse clicks register inside the window. The network/sound/system menu items in the top right all work fine (although the icon remains the waiting icon and no a pointer/hand.) There is no disk/cd/network activity on the indicators.

Any ideas?

The first thought that comes to my mind is, ditch virtualbox. Yes, I know, its magical. I swore by it for a long time. UNTIL I discovered VMware player. You can do everything that Virtualbox does and more. It even lets you go so far as drag and dropping files from host to guest and vice-versa. And, did I mention, its free with better support? Oracle is a plague to sun microsystems. What was once a great product is being destroyed.

---

### Post by linuxinstalledfromhdd on 2011-06-06
VMware is what you want to use in Windows too.. I confirm that.

---

### Post by kadaan on 2011-06-06
VMWare worked perfectly, thanks :).

---

### Post by Ratzian on 2011-06-21
Thanks a bunch, guys :) Had the same problem today.

---

