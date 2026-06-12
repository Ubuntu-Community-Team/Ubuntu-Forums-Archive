---
title: "Nvidia drivers broken since package upgrade"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by sosasami on 2013-03-18
My system was working perfectly until yesterday I upgrdaded some packages, and today when I rebooted the Nvidia drivers fail to load and I am unable to launch xbmc.


looking at the packages that were upgraded yesterday the most likely ones to cause the breakage are
xserver-xorg-core 2:1.11.4-0ubuntu10.12
xserver-common 2:1.11.4-0ubuntu10.12


but even though I tried to downgrade them in synaptic to xserver-xorg-core 2:1.11.4-0ubuntu10.6 and xserver-common 2:1.11.4-0ubuntu10.6, the nvidia drivers still fail to load.


"sudo modprobe nvidia" results in:
WARNING: Module nvidia_current not found.


xorg log shows following:
199.925] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 199.925] compiled for 4.0.2, module version = 1.0.0
[ 199.925] Module class: X.Org Video Driver
[ 199.934] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[ 199.934] (EE) NVIDIA: system's kernel log for additional error messages.
[ 199.934] (II) UnloadModule: "nvidia"
[ 199.934] (II) Unloading nvidia


Any help would be appreciated.

---

### Post by dino99 on 2013-03-18
you should accept the xserver upgrade, then purge nvidia* packages
then be sure that : dkms, linux-headers are installed, then be sure that no ppa conflict (if some are installed, desactivate them and update again), and then:

sudo apt-get install nvidia-current nvidia-common

and logout/in

---

### Post by sosasami on 2013-03-18
Thanks Dino,

I tried that already but it didn't work.

Turned out I had the wrong version of linux headers installed (mismatch with linux-image). Once I fixes that it fixed the Nvidia drivers too.

Cheers.

---

### Post by MAFoElffen on 2013-03-18
> **sosasami said:**
> Thanks Dino,

I tried that already but it didn't work.

Turned out I had the wrong version of linux headers installed (mismatch with linux-image). Once I fixes that it fixed the Nvidia drivers too.

Cheers.
Sort of... Once you get the linux-head-xxxxxx er to match the kernel you are running on... then after you purge the nvidia driver that was installl... then install the new nvidia driver (even if the same driver) THEN the driver can install. You see, it is a binary driver that needs to "compile" on the new kernel. To compile, it needs the kernel header source to do that.

After a few years of this, all this will be "Expected" as something that just occasionally happens.

---

