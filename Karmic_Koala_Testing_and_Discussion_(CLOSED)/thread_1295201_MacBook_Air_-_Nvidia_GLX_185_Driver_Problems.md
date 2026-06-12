---
title: "MacBook Air - Nvidia GLX 185 Driver Problems"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubu-for on 2009-10-19
Yesterday I've installed the nvidia-glx-185 drivers for my MacBook Air but now Karmic doesn't boot up any longer and it looks like X11 doesn't start correctly.

Was it wrong to install the nvidia drivers?

---

### Post by mikedep333 on 2009-10-19
Probably not.

If you have a wired ethernet adapter, I would tell you to update your software:
```
sudo apt-get update
sudo apt-get upgrade
```

If you can't do that or that doesn't work, regenerate your X config file to a default not using the "nvidia" driver (nvidia-glx.)
```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

