---
title: "Can not enter KDE after install Kubuntu  on Laptop"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by amarin on 2006-06-06
I install on my laptop that have 14.1 Wxga 
ATI display card Radeon 700


I can enter text mode, I try to set the correct resolution
1280 * 800

Please guide me

---

### Post by aysiu on 2006-06-06
Try ```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/kdm start
```

---

