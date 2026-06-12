---
title: "[SOLVED] Xubuntu 8.10 rc :Recommneded downloaded Nvida driver won't install"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by slaabrockband on 2008-10-28
I haved installed Xunbuntu on a old computer with a geforce 3 graphic
card.

I can download the Nvidia proprietary diver but it won't install.
I have tried nvidia-xconfig in terminal, it did'nt work.

Any hint about attacking this problem ?

---

### Post by Elfy on 2008-10-28
It won't work yet, it was in the release notes. You might be ok with the nouveau drivers - [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

If that doesn't work for you then you'll have ti use the nv or vesa driver
> 
The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

---

### Post by dabl on 2008-10-28
Assuming the default Intrepid repositories are enabled, in the CLI do this:

```
sudo /etc/init.d/gdm stop
```

```
sudo apt-get update
```

```
sudo apt-get install envyng-core
```

and following installation,
```

sudo envyng -t
```

then choose #1 "Install Nvidia Driver", followed by #5 "Restart X Server".

:)

---

### Post by Elfy on 2008-10-28
I've tried that - although not this week - it just gets a driver from nvidia that doesn't work either.

WE're wwaiting for nvidia to release a new legacy driver to work with the new xorg - fedora have been waiting longer ;)

---

### Post by slaabrockband on 2008-10-28
Thank you for your answers

I'll downgrade to xubuntu 8.04 and stay there for a while

---

