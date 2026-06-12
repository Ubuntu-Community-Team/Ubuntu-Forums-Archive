---
title: "Please help.. cant run Ubuntu on Nforce4 with PCIe?"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by Zillion on 2005-09-09
Ok, I am n00b but I sure read the forums and have now tried to install Ubuntu Hoary 5 times.. it just wont work on my main pc, on my old pc it runs well.

My config :

MSI K8N Neo4 Platinum Nforce 4 mobo
AMD64 3000 proc
Nvidia 6800 GTO pcie vga
Audigy2 sb
2 x 512 mb ddr
Nec DvD player
Pioneer DVD writer
1 hdd 160gb maxtor with WinXp

no other devices connected!

nothing special I would think.. in fact there must be a lot of people in the world with a likewise configuration

but Ubuntu doesnt like it : the installation on Hoary seems to go well, but after it install all things and it boots it hangs 2 out of 3 times on "Starting Hotplug subsystem".. But the main problem is that if it boots further to the point Ubuntu should really start it just gives a black screen cuz the monitor doesnt get a signal no more...

Is anyone else running on Nforce4 /PCIe?

Any help would be appreciated!

---

### Post by amohanty on 2005-09-09
I have an Asus A8N SLI with PCIe, nForce4 chipset and audigy 2zs and everything been fine for the last 6 months. I would suggest first trying the Live CD. If it does not work , try taking out the DVD player and writer and boot off the live cd.

If that works, add each one back and do the same. Ubuntu repos have nvidia drivers, so that should not be a problem. If any one of the dvd drives causes a problem search the forums, I think I saw some posts regarding the poineer dvd writer, one of them being:
[http://ubuntuforums.org/showthread.php?t=34516&highlight=pioneer+dvd+writer](http://ubuntuforums.org/showthread.php?t=34516&highlight=pioneer+dvd+writer)

HTH
AM

---

### Post by Zillion on 2005-09-10
I disconnected both dvd players and connected a cd-player which I used on other pc with Ubuntu. Still same problem. I found out I can do ctrl alt f1 to get console, what can I type there to check or start gnome?

tx

---

### Post by Zillion on 2005-09-10
[QUOTE=amohanty]I have an Asus A8N SLI with PCIe, nForce4 chipset and audigy 2zs and everything been fine for the last 6 months. I would suggest first trying the Live CD. If it does not work , try taking out the DVD player and writer and boot off the live cd.

If that works, add each one back and do the same. Ubuntu repos have nvidia drivers, so that should not be a problem. If any one of the dvd drives causes a problem search the forums, I think I saw some posts regarding the poineer dvd writer, one of them being:
[http://ubuntuforums.org/showthread.php?t=34516&highlight=pioneer+dvd+writer](http://ubuntuforums.org/showthread.php?t=34516&highlight=pioneer+dvd+writer)

HTH
AM[/QUOTE]

allright I tried that all. boot cd also gives black screen, though I can come in console. I have no clue what to do :(
Knoppix and Mepis work allright, but I want Ubuntu  ](*,)

---

### Post by krusbjorn on 2005-09-10
The reason your screen recieves no signal might be cause if X is using a higher resolution than your screen can handle. Try editing your /etc/X11/xorg.conf and remove the high resolution modes, to make X start with, say 1024x768, and see if it works.

---

### Post by Zillion on 2005-09-11
[QUOTE=krusbjorn]The reason your screen recieves no signal might be cause if X is using a higher resolution than your screen can handle. Try editing your /etc/X11/xorg.conf and remove the high resolution modes, to make X start with, say 1024x768, and see if it works.[/QUOTE]

tx but pff took me some time to figure out how to do that with vi and recoverymode, I am a noob remember ;)

but guess what, it didnt work.. and Ubuntu now also hangs on login (after I press ctrl alt f1)

:(

---

### Post by Zillion on 2005-09-11
Ok I changed driver from NV to vesa in xorg.conf and now I finally see X start :D dang that took long time to figure that out. next thing I gonna try is install latest Nvidia driver..

---

