---
title: "Display corrupt and hangs"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by RedCokeBottle on 2005-06-09
Hi all

I've just tried to install Ubuntu for the first time on the following hardware:

Asus K8V-SE
AMD64 3200+
1.5GB PC3200
Sata WD Raptor
Ati 9250 AGP

The installation went well until it tried to load any high resolution UI. It showed me a corrupted screen with the Gnome cursor, which I could move around, but everything was corrupt and nothing changed. 

What can I do to fix it?

---

### Post by zAo on 2005-06-09
[QUOTE=RedCokeBottle]Hi all

I've just tried to install Ubuntu for the first time on the following hardware:

Asus K8V-SE
AMD64 3200+
1.5GB PC3200
Sata WD Raptor
Ati 9250 AGP

The installation went well until it tried to load any high resolution UI. It showed me a corrupted screen with the Gnome cursor, which I could move around, but everything was corrupt and nothing changed. 

What can I do to fix it?[/QUOTE]
How did you load that high resolution? Have you got DRI enabled? Without DRI (so you use VESA) you cant get higher resolutions than 1280x1024@60hz.
To solve this: edit your /etc/X11/xorg.conf (search for 'modes') and get DRI working.

---

### Post by RedCokeBottle on 2005-06-09
I just ran the standard 386 installation and then rebooted when it ejected the CD, the system started to boot up but then when it tried to go into Gnome the display, but not pointer, was corrupted. 

I'm using a Viewsonic 20" lcd at 1600x1200 on DVI. The corrupted picture was being shown at 1600x1200 resolution.

---

