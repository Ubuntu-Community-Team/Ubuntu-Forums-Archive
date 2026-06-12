---
title: "nvidia FATAL error plz help"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by bward1 on 2007-01-27
I just bought a new nvidia to relieve my ATI troubles, and now I am having just as many problems with nvidia, which I thought would be far easier.  I am trying to get the nvidia driver instead of the nv driver to work and I am not getting anywhere.  I have installed nvidia-glx and done all of the nvidia-xconfig things I can find and still no luck.  The xserver error explains that the nvidia kernel module doesn't load, so obviously I need to do that, but I can't for the life of me figure out how.  I try and I get this error: ```
root@Conroe:~# modprobe nvidia
FATAL: Error running install command for nvidia

```  I have read that this happens due to having the wrong restricted kernel modules installed, but I have installed and reinstalled the different kernel modules so many times and it hasn't ever worked.

```
root@Conroe:~# uname -r
2.6.17-10-server-bigiron
root@Conroe:~# apt-get install linux-restricted-modules-2.6.17-10-generic linux-generic linux-restricted-modules-common nvidia-kernel-common nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.17-10-generic is already the newest version.
linux-generic is already the newest version.
linux-restricted-modules-common is already the newest version.
nvidia-kernel-common is already the newest version.
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any help would be greatly appreciated.

---

### Post by taurus on 2007-01-27
Maybe this guide helps.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

