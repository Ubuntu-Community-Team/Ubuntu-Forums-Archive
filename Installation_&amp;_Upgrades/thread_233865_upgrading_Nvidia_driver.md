---
title: "upgrading Nvidia driver"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by tsunade on 2006-08-10
I wanted to upgrade my nvidia drivers ->
```

sudo apt-get install nvidia-glx nvidia-kernel-common

```
did a reboot.. 
could not start xserver..
downloaded nvidia drivers from their website and installed them but doesn't work 

I reinstalled the drivers but without success..

plz help!

---

### Post by mlind on 2006-08-10
Do you have linux-restricted-modules package for your architechture installed?

---

### Post by tsunade on 2006-08-10
yep the linux-restricted-modules for my kernel/arch were installed.

here is the error from the log file:
```

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

if you need my xorg.conf, there you go (attached)

i still can't find any solution :(

---

### Post by mlind on 2006-08-10
What kernel are you running? If you've compiled your own kernel, you need to build a kernel module too. For Ubuntu kernel, linux-restricted-modules provides the module.

If you're running Ubuntu kernel and linux-restricted-modules are installed like you said, try modprobing the nvidia kernel module
```

sudo modprobe nvidia

```

Then restart gdm
```

sudo invoke.rc-d gdm restart

```

---

### Post by tsunade on 2006-08-10
thx for your fast response, i'll try it right away ^^

---

### Post by tsunade on 2006-08-10
I've found the solution!

i uninstalled nvidia-glx and nvidia-kernel-common (-> so all the restricted modules of all kernel versions would be removed)

i reinstalled nvidia-glx, but not just nvidia-kernel-common, but nvidia-restricted-modules-<my kernel version>, so nvidia-glx will build a kernel interface of my kernel version =), anyway I think it's like that.

thx for your help anyway ;-)

---

### Post by mlind on 2006-08-10
> **tsunade said:**
> I've found the solution!

i uninstalled nvidia-glx and nvidia-kernel-common (-> so all the restricted modules of all kernel versions would be removed)

i reinstalled nvidia-glx, but not just nvidia-kernel-common, but nvidia-restricted-modules-<my kernel version>, so nvidia-glx will build a kernel interface of my kernel version =), anyway I think it's like that.

thx for your help anyway ;-)

That was the idea since post #2 ;) 
It doesn't build the kernel module for you, linux-restricted-modules just installs pre-built module for your Ubuntu kernel.

---

