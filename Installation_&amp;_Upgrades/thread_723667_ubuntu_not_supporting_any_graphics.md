---
title: "ubuntu not supporting any graphics"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by .ultimate on 2008-03-13
hi all, i have moved from windows to ubuntu and have a big prob with the graphics. the max resolution is 640 by 480. can anyone resolve this problem or find an updated driver that works. there are no restricted drivers. i need a driver for a sis m650 graphics controller.

thanks

---

### Post by zvacet on 2008-03-14
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select** vesa** driver and after reboot you should have basic graphic.Now you can search for your video card driver.

---

