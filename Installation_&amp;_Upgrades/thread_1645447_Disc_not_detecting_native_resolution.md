---
title: "Disc not detecting native resolution"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by DaymItzJack on 2010-12-14
I am planning on installing Ubuntu on my new laptop with a native resolution of 1920x1080 however the install disc (I booted into the "test") part, sets my resolution to 2048x1536. Keeping it on 2048x1536 cuts off about 50 pixels on the right side of my screen so it must not be right. 

So I tried changing it from the "Monitors" settings back to 1920x1080 and everything is so large and it is stretched horizontally. Is this just because I'm running the "try me" part, or is there something wrong with Ubuntu and my video card?

Product:	US-VPCF1290X-LBOM
Component: 	Standard capacity battery
Component: 	Intel® Core™ i7-740QM processor (1.73GHz) with Turbo Boost up to 2.93GHz
Component: 	16.4" VAIO Full HD Premium Display (1920x1080)
Component: 	NVIDIA® GeForce® 330M GPU (1GB VRAM)
Component: 	Fresh Start
Component: 	LED Backlit Keyboard
Component: 	4GB (2GBx2) DDR3-SDRAM-1333
Component: 	CD/DVD player/burner
Component: 	No Engraving
Component: 	No Adobe Software
Component: 	No additional AntiVirus Software
Component: 	Black
Component: 	No additional Office software
Component: 	Genuine Windows® 7 Professional 64-bit
Component: 	500GB Hard Disk Drive (7200rpm)

---

### Post by sikander3786 on 2010-12-14
Did you check under System > Administration > Additional Drivers/Hardware Drivers if proprietary drivers for your card are available. If yes, activate the current/recommended version. It would require a reboot. Don't reboot! Press Ctrl + Alt + F1 to switch to tty1 and restart gdm.

```
sudo service gdm stop
```

```
sudo service gdm start
```

Nvidia configuration tool should then be available under System Administration menu. See if that lists your desire resolutions now.

---

### Post by DaymItzJack on 2010-12-14
> **sikander3786 said:**
> Did you check under System > Administration > Additional Drivers/Hardware Drivers if proprietary drivers for your card are available. If yes, activate the current/recommended version. It would require a reboot. Don't reboot! Press Ctrl + Alt + F1 to switch to tty1 and restart gdm.

```
sudo service gdm stop
```

```
sudo service gdm start
```

Nvidia configuration tool should then be available under System Administration menu. See if that lists your desire resolutions now.

I haven't tried this yet but the problem isn't that the resolution isn't there, it's that it's way too big and not correctly sized. I use 1920x1080 on Windows 7 and it looks fine (its the native resolution) but on Ubuntu is all messed up.

---

### Post by DaymItzJack on 2010-12-14
While still running from the disc, I cannot get gdm to start up again after stopping it. It'll load but as soon as I hit "Try Ubuntu" it goes back to tty1 and tty7 doesn't work either.

---

### Post by sikander3786 on 2010-12-15
> **DaymItzJack said:**
> While still running from the disc, I cannot get gdm to start up again after stopping it. It'll load but as soon as I hit "Try Ubuntu" it goes back to tty1 and tty7 doesn't work either.
And that is happening after the Nvidia drivers have been installed?

---

