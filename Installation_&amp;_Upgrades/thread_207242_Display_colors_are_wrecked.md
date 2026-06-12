---
title: "Display colors are wrecked"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by ~ Skipper ~ on 2006-07-01
Hi, after installing Ubuntu 6.06 I have a problem with my monitor. The image is displayed with horyzontal lines and the colors look funny, with strange stains.
FC4 & Ubuntu 5.04 worked ok, so i gues it is xorg 7.0 problem.

Please help me!!!

---

### Post by ~ Skipper ~ on 2006-07-02
I'm using an old Mighty Banshee video card (tdfx driver). In xorg.conf i see that 'vesa' driver is used. Shouldn't it be tdfx?

---

### Post by ~ Skipper ~ on 2006-07-05
Mandriva & FC4 use tdfx driver and does well.
Can you post your xorg.conf so i could compare to my?

---

### Post by confused57 on 2006-07-05
[QUOTE=~ Skipper ~]Mandriva & FC4 use tdfx driver and does well.
Can you post your xorg.conf so i could compare to my?[/QUOTE]

I don't know if Ubuntu has tdfx driver support, you could try:
```
sudo dpkg-reconfigure xserver-xorg
```

If you've never used this menu,  at the first screen, select "no" for autodetect your monitor...the remaining options, you could probably just go with the default.  You'll come to a screen with a list of possible video drivers, like I said, I don't know if  "tdfx" is an option, or if there is something comparable.

---

### Post by ~ Skipper ~ on 2006-07-05
Ubuntu has a tdfx support, it is on the list.
Tried what you said but was no difference.

---

### Post by confused57 on 2006-07-05
You could try the sudo dpkg-reconfigure xserver-xorg, again; but when you get to the screen resolutions screen, try taking out the highest resolution with an (*) by pressing the space bar with it highlighted.  I don't think it'll make a difference, but if you know the vertical & horizontal refresh rates for your monitor, you could go into:

```
sudo nano /etc/X11/xorg.conf
```

and make sure that's what the file shows for your monitor.
I believe it's probably a driver issue, but I don't it'll hurt anything to try a lower resolution.

---

### Post by ~ Skipper ~ on 2006-07-05
nothing...

---

