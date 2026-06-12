---
title: "ubuntu does not start anymore after win7 installation (double part.)"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by awayguy on 2010-09-07
i had a double partition. working ubuntu 64bit side by side with vista 64bit partition. i installed win7 64bit on vista partition. now ubuntu doesnt start. i cant see that partition, but there is 50gb of space on which ubuntu is intalled. ho to fix that, so that i can run ubuntu and 7 side by side?

---

### Post by an0dos on 2010-09-07
> **awayguy said:**
> i had a double partition. working ubuntu 64bit side by side with vista 64bit partition. i installed win7 64bit on vista partition. now ubuntu doesnt start. i cant see that partition, but there is 50gb of space on which ubuntu is intalled. ho to fix that, so that i can run ubuntu and 7 side by side?

When you installed windows it wrote over GRUB (the Linux boot loader). You need to reinstall it. See here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202 ]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by awayguy on 2010-09-08
hmm, but i can only start windows. i have reinstall the grub while working in windows, because ubuntu doesnt start, unless i can boot ubuntu from usb drive, and install grub while beeing in ubuntu with usb flash?

---

### Post by Mammut1492 on 2010-09-08
As you can read in the Documentation posted by anOdos, you can reinstall GRUB from Live CD --> see section [COLOR=black]**Reinstalling from LiveCD.**[/COLOR]
 
Good luck** :p**

---

### Post by Mark Phelps on 2010-09-09
> **awayguy said:**
> hmm, but i can only start windows. i have reinstall the grub while working in windows ...


Huh?? You can't reinstall GRUB from inside Windows.

Follow the directions already provided to install GRUB from an Ubuntu LiveCD.

---

