---
title: "Support for SIS 671/672 in Ubuntu 8.10?,"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by salamaza on 2008-10-23
hi, 
This might be late for 8.10 but today i tried ubuntu and there is still no sis support at all, no 2d/3d acceleration and i got wrong resolution in my laptop.

Today I was looking at mandriva 2009, and it had this [SIS Media]("http://www.linuxconsulting.ro/xorg-drivers/") 2d driver with Xvideo Acceleration and it gave me the right resolution and that what i actually needed(its ok with no 3d, its slow anyway).

it seems this "sis media" driver is not merged with xorg for somereason

so please ubuntu team, could u include it in Ubuntu 8.10 ?

Thanks,

---

### Post by amano on 2008-10-23
The correct way is to file a bug on launchpad. Begging in the forums will not help because the developers don't read here.

---

### Post by salamaza on 2008-10-23
oh sorry but its not a bug, should i still report it as a bug ?

---

### Post by amano on 2008-10-23
Yes. All undesired behaviour is a "bug". And missing drivers are rather big ones.

Please search launchpad if this bug was reported before to not create any unnecessary duplicates though.

---

### Post by prshah on 2008-10-23
> **salamaza said:**
> 
it seems this "sis media" driver is not merged with xorg for somereason
so please ubuntu team, could u include it in Ubuntu 8.10 ?


You can install the [sis driver package]("apt://xserver-xorg-video-sis") to enable this.

If you want to do this manually (rather than just clicking the link above), open a Terminal (Applications-Accessories-Terminal) and give the command```
sudo apt-get install xserver-xorg-video-sis
```

Once installed, activate it by pressing Alt+F2 and giving the command```
gksudo displayconfig-gtk
```, then click on the "Graphics Card" tab, and selected a suitable SiS driver from the choices.

Post back if you run into difficulties.

---

