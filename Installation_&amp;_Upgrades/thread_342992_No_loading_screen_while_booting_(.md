---
title: "No loading screen while booting :("
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by Jarn on 2007-01-20
Since I upgraded from Dapper to Edgy a few weeks ago, there is no longer a loading screen while booting. All it is text until it gets to the login screen.

---

### Post by Jarn on 2007-01-20
Bump since I'm on the second page... (wow these forums are active).

---

### Post by taurus on 2007-01-20
Look at the kernel entry in /boot/grub/menu.lst and make sure you have **splash** at the end.

Applications -> Accessories -> Terminal
```
sudo cat /boot/grub/menu.lst
```

---

### Post by Jarn on 2007-01-21
I do.

---

### Post by featherking on 2007-01-21
You could try reinstalling usplash or usplash-theme-ubuntu in synaptic, if that doesnt work i would suggest looking into a program called [[COLOR="Red"]startup manager[/COLOR]]("http://web.telia.com/~u88005282/sum/index.html"). Usplash can be reconfigured through the terminal but it requires multiple long steps and ive found this startup manager to be great and much quicker than typing all the steps out by hand

---

### Post by Jarn on 2007-01-21
Reinstalling usplash and kubuntu-artwork-usplash (I'm on Kubuntu) worked -- thanks much!

---

### Post by featherking on 2007-01-21
no problem!

---

