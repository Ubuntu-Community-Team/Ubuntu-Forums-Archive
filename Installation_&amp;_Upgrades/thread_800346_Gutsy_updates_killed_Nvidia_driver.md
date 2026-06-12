---
title: "Gutsy updates killed Nvidia driver"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Magsec on 2008-05-19
installed Ubuntu Gutsy Gibbon 7.10```

```

working perfectly fine :) installed the Nvidia Linux Driver from nvidia.com (pressed Ctrl + Alt + F1, stopped X and then used the install package x86 169.12) 

GPU: nvidia 8800GT 

Drivers installed fine, installed compiz fusion which also installed fine.

Then used the update manager to update Ubuntu, re-booted and Ubuntu starts up in safe graphics mode in a very low resolution, checked the Nvidia X settings which gave me this error message :

```
you do not appear to be using the nvidia x driver, please edit your X configuration file (Just run nvidia-xconfig as root and restart X server)
```

I then did that: sudo nvidia-xconfig

and restarted X, sudo /etc/init.d/gdm restart

However it boots up much the same (in safe mode)at a very low resolution.

I doubt its due to the installation as that went fine and worked perfectly fine for many sessions before installing and re-booting after the updates.

Im new to using linux, ubuntu and commands... and Ubuntu is currently un-usuable at that resolution (i cant even setup evolution mail and had to use Windows just to register with this forum. :(

---

### Post by jrusso2 on 2008-05-19
Sounds like you did a nvidia driver install from a non-repository driver so when you did an upgrade and it must have done a kernel upgrade and since you used an nvidia driver not in the repository it didn't know how to reinstall it.

Its best to use the restricted driver manager to install nvidia drivers or else each time the kernel updates it will break it unless you uninstall it first and then reinstall it after the upgrade.

---

### Post by Magsec on 2008-05-19
re-installed nvidia driver problem solved. Thanks :)

---

