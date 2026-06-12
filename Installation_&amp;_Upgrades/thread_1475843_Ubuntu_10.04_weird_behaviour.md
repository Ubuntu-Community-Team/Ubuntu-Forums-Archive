---
title: "Ubuntu 10.04 weird behaviour"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by ubun2warrior on 2010-05-07
I recently installed UBUNTU 10.04 on my desktop(AMD Athlonx64, 2 gb ram, 320gb hd). I have created two user accounts and sometimes when i log out of one account the screen just goes blank(...It should take me to the log in screen actually) and it sorts of hangs there nothing happens i have to switch of the power supply.

---

### Post by sylvester_0 on 2010-05-07
Strange - are you using the best video card drivers? You can see if better drivers can be installed by going to System -> Administration -> Hardware Drivers. Also, you could get some clues as to what's going on by pressing Ctrl - Alt - F1 when you get a black screen, logging in and running ```
tail -n 20 /var/log/Xorg.0.log
```

Worst case scenario you can run ```
sudo service gdm restart
``` and it should get your running again (instead of having to poweroff.) If you can't get to a terminal with the above trick, try sshing from another machine and running those commands.

---

### Post by ubun2warrior on 2010-05-25
I am using nVidia GeForce 6000 series.

---

