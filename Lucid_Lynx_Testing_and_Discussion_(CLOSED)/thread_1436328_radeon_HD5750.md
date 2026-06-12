---
title: "radeon HD5750"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tanari on 2010-03-22
no desktop effects :(

---

### Post by WishMaster on 2010-04-03
lucky you, mine doesn't even boot !

---

### Post by forcecore on 2010-04-03
> **WishMaster said:**
> lucky you, mine doesn't even boot !

even in safe graphics mode (vesa)?

---

### Post by Reiger on 2010-04-03
Assuming that it is only the graphics subsystems that cause the problems (and not other broken stuff), then I suppose that you would get a better result from installing fglrx from the archives than from the opensource radeon driver. For the time being.

If you can boot to a tty that is.

---

### Post by Evzen on 2010-04-06
Same here.

Initially i had some problems with radeon driver. The picture was slightly corrupted - missing vertical stripes in the picture about every 10 pixels (even during the instalation). After some tweaking and updating, radeon driver works, of course, no desktop effect nor 3D acceleration.

After some update (about week ago), Gtk Jockey offered to instal fglrx. So I installed that, rebooted and i got** working 3D and desktop effects**! Sadly, the next day, after update, ubuntu started with xorg configuration error due to the graphic driver. No tweaking helped. So, I had to revert to the radeon driver (radeonhd driver does not work either).

---

### Post by Scott82 on 2010-04-06
have you guys tried installing from beta, then installing fgrlx then reboot then do sudo aticonfig --initial then reboot then install updates? (for me it doesn't work unless i install the driver and do the config before doing updates.)

---

### Post by Evzen on 2010-04-06
> **Scott82 said:**
> have you guys tried installing from beta, then installing fgrlx then reboot then do sudo aticonfig --initial then reboot then install updates? (for me it doesn't work unless i install the driver and do the config before doing updates.)

Not sure that I have tried it that way. But only thing **aticonfig --initial** does (AFAIK) is that it sets up **xorg.conf** file to use fglrx instead of default and automatically used radeon driver. I checked xorg.conf as it is produced during fglrx package installation and it looks fine and correct.

---

### Post by Evzen on 2010-04-15
Since last monday I have full 3D accel using fglrx. The driver was installed simply through jockey-gtk interface.

---

