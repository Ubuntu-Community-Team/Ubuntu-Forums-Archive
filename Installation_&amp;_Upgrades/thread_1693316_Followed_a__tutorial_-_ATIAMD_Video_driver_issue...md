---
title: "Followed a  tutorial - ATI/AMD Video driver issue...fglrx ?"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by telestrial on 2011-02-22
Hello...I'm at my wits end.

I was trying to (I guess) reinstall a set of drivers.  However, I end up screwing everything up in one command:

```
sudo apt-get remove --purge fglrx*
```

Fglrx is now highlighted red in synaptic.  Fix broken packages does not work. Synaptic chooses to remove it..and when it tries I get:

```
E: fglrx: subprocess installed post-removal script returned error exit status 2
```

System>Admin>hardwaredrivers says that the ATI/AMD driver is enabled. No hardware acceleration.  Will the world ever be right again?

O open source wizards...please have mercy on me...

---

### Post by Old_Grey_Wolf on 2011-02-22
Try entering these commands in the terminal ```
sudo /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install fglrx-modaliases
```

---

