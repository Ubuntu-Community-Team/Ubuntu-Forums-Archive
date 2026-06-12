---
title: "8400m gs driver"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Sergeantfour on 2008-02-14
I installled Ubuntu last night but evidently used the wrong driver because the screen started freezing up in really short spurts and the resolution was WAAAAAY off.  Everything else worked great though.  Does anyone know the correct driver to use?

I'm running a hp dv6675us with 2.0 dual core 4gb RAM dual booting with Vista Ultimate 64 bit.

---

### Post by Partyboi2 on 2008-02-17
try installing the latest driver from nvidia
boot into recovery mode (Select at grub menu) When you get to the terminal
install build-essential
```
 apt-get install build-essential
```grab the driver from nvidia
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```start the installer
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```after installer has finished
```
startx
``` or
```
reboot
``` to boot into the normal kernel

---

### Post by Sergeantfour on 2008-02-18
You rule.

---

