---
title: "Compiling kernel for Jaunty"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by applemacmad on 2009-03-23
I tend to compile my own kernels for my Acer Aspire One netbook - it generally makes some hardware work better and the system works better. 
However, I've hit a brick wall with Jaunty - neither my kernels compiled from the ubuntu source, the vanilla source or from git are working, using either the generic config or my optimised one.
The kernels compile and install fine, however, when I boot, I see the errors:
```
intelfb: cannot remap FB region
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-custom1/modules.dep No such file or directory
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-custom1/modules.dep No such file or directory
```
It then gives up waiting for root device and drops to busybox and won't boot.
I use the 'old fashioned' method detailed here:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Has the method changed for Jaunty or something?

---

### Post by danwood76 on 2009-03-23
Sounds like its not doing the modpost after installing the kernel deb package.
I compiled a 2.6.29-rt kernel on my laptop the other day using that method and have had no problems.

Make sure the modules directory exists, the busybox prompt is usually caused by an incorrect initramfs.

So you can also try doing 
```

sudo update-initramfs -u -k all

```
This will rebuild an initramfs for each of the available kernels.

---

### Post by applemacmad on 2009-03-24
hmmm, still no luck.
update-initramfs says that it has worked, but still the same error

---

### Post by applemacmad on 2009-03-24
I have a feeling the problem could have been down to my partition map - I was using GPT (don't ask)
Reformatted the system on bog standard MBR and it's still not working, but it;s at a point where I know what's wrong ;)

---

### Post by danirolo7 on 2009-03-31
I have the same problem but booting from a LiveUsb with the default kernel and official iso.

---

### Post by MacUntu on 2009-03-31
Try```
sudo update-initramfs -c -k all
```instead of```
sudo update-initramfs -u -k all
```

---

