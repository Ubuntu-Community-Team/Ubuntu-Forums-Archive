---
title: "&quot;Hardware Drivers&quot; missing in System-&gt;Administration"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Beren Sanders on 2010-05-19
I have upgraded a previous partial installation of karmic up to lucid. When I go to System->Administration there is no "Hardware Drivers" link. What should I apt-get install to get the Hardware Drivers link.

---

### Post by utnubuuser on 2010-05-19
jockey-gtk

If it's already installed, take a look in System>>MainMenu to see if you can add it to the menu.

---

### Post by zomorodkar on 2010-11-23
> **utnubuuser said:**
> jockey-gtk

If it's already installed, take a look in System>>MainMenu to see if you can add it to the menu.

hi,
im fairly new to ubuntu and i have the same problem considering installing jockey-gtk i still cant locate the hardware drivers under the system administration menu , its not even located under main menu when i edit the menu to add it.
plz advise !?!?
btw im running 10.10

thx
Moe

---

### Post by tommcd on 2010-11-23
> **zomorodkar said:**
> ... i have the same problem considering installing jockey-gtk i still cant locate the hardware drivers under the system administration menu , its not even located under main menu when i edit the menu to add it.

Do you have jockey-gtk installed? Open a terminal (applications > accessories > terminal) and post the output of:
```
aptitude search jockey
```
If jockey-gtk is installed there will be an "i" in front of it. If jockey-gtk is not installed there will be a "p" before it.
What video card do you have? You can install the correct driver from the Ubuntu repos using apt-get via the terminal.

And welcome to the Ubuntu forums!

---

### Post by Quackers on 2010-11-24
Is System > Admin > Additional Drivers there - it has been renamed.

---

### Post by comperocean on 2011-06-21
use "jockey-gtk" in terminal to check jockey-gtk installed or not;
use "sudo apt[I]-get install jockey-gtk" to install jockey-gtk;
finished.
the additional drivers can be found.
[/I]

---

### Post by lottes70 on 2011-08-29
> **utnubuuser said:**
> jockey-gtk

If it's already installed, take a look in System>>MainMenu to see if you can add it to the menu.

thanks for the info, my problem was that it wasn't installed.

---

