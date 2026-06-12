---
title: "NV Geforce 560GTX Ti driver install help"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by Spikey123 on 2013-02-20
I have been all day trying to get the video card driver to work and not to use default. I to were the os goes from standard to accelerated. I tried all the solutions that I can google and it still will not change to the nvidia driver. If there is any more suggestions that would be helpful.

I have tried the opensource drivers and non opensource driver.

---

### Post by dino99 on 2013-02-20
install the xorg-edgers ppa to get the latest 313 driver
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

then purge the actual installed video driver(s)
install nvidia-graphics-drivers-313

be sure to remove xorg.conf
(sudo rm /etc/X11/xorg.conf)

and reboot

---

### Post by Spikey123 on 2013-02-20
I did what I can understand about those step and still nothing I don't know if I am not understanding it because I don't know all the commands in the terminal that is needed or if it from this headache I have right now. But it still didn't work and the Driver is not kicking on.

---

