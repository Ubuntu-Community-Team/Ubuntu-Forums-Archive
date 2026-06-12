---
title: "My Ubuntu minimal installation!"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by RJARRRPCGP on 2010-02-19
```
sudo apt-get install hal
``` 

```
sudo apt-get install xserver-xorg-core xinit menu menu-xdg jwm fluxbox alsa-utils mrxvt gdebi-core synaptic logrotate localepurge
```

Now reboot:

```
sudo reboot
```

Then after logging in, type ```
startx
```

I'm running with this configuration as I'm typing! 

(I was worried that X was gonna ignore my mouse and keyboard, that occurred before, when trying to use another desktop.)

Looks like you must do ```
sudo apt-get install hal
``` to make sure you have a working mouse and keyboard!

Psychocats don't have this mentioned! IIRC, when I once followed a Psychocats tutorial, I ended up with no working mouse and keyboard! 

All I could do was watch helplessly and go for the power button!

---

### Post by mkvnmtr on 2010-02-19
I have just finished a couple of minimal ijnstalls. One in Ubuntu and one in Debian. Rather than local purge why not choose no language in the installer. That way they never get downloaded. Another thing I like to do is choose a targeted kernel install. Saves downloading a lot of drivers you do not need.

---

