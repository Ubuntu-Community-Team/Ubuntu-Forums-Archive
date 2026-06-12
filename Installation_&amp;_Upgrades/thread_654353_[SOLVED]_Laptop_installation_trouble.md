---
title: "[SOLVED] Laptop installation trouble"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by jbblue1 on 2007-12-31
Fetal server error: no screens found 


My laptop (toshiba tecra 2100), the disk drive stopped reading cds and would only read dvds, so i had trouble installing. I decided to take the harddrive out of the laptop and put it into a different laptop of similar age, hoping for some compatibility. (Dell Inspiron 2200). the instilation went fine, so i put the hdd back into the the toshiba, and unsurprising no screen can be found.

I ask, is there an easy way to fix this; If so, help please?

or should the ubuntu.iso work fine burned to a dvd?

---

### Post by erfahren on 2007-12-31
the ubuntu CD .iso wouldn't work on a DVD

when you boot it up go into recovery mode or otherwise get to the command line and type in
```

dpkg-reconfigure xserver-xorg

```

go through the steps, you can just accept the defaults for most. that will reconfigure the xorg.conf for the other laptop.

---

### Post by jbblue1 on 2007-12-31
> **erfahren said:**
> the ubuntu CD .iso wouldn't work on a DVD

when you boot it up go into recovery mode or otherwise get to the command line and type in
```

dpkg-reconfigure xserver-xorg

```

go through the steps, you can just accept the defaults for most. that will reconfigure the xorg.conf for the other laptop.

Thank you :)

I knew there was some easy way to do this. I was just unaware of the commands.

but now, after messing with the cd drive quite a bit. it's working again. soo hopefully I can just do a fresh install. 

but thank you.

---

### Post by erfahren on 2007-12-31
oh, when you get to the display driver part you don't really want the "vesa" driver, that's the basic generic driver. you want to start off with whatever open-source driver that's available for your card.

I can't really recall how all that goes, but it automatically make a backup of your /etc/X11/xorg.conf before it starts

---

### Post by erfahren on 2007-12-31
> **jbblue1 said:**
> Thank you :)

I knew there was some easy way to do this. I was just unaware of the commands.

but now, after messing with the cd drive quite a bit. it's working again. soo hopefully I can just do a fresh install. 

but thank you.
ok --  (you posted as I was)

good luck

---

