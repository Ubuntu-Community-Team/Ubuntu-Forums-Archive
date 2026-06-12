---
title: "Blender  segmentation fault"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by ownsuall on 2010-06-15
When i try to run Blender in Ubuntu 10.04 it dosen't run. When i run in command line i get
```

Compiled with Python version 2.6.5.
Checking for installed Python... got it!
Segmentation fault

```
I get the same error while trying to run an application im making in opengl so i'm not sure if the 2 are related.

---

### Post by ZephyrXero on 2010-07-08
I'm getting the exact same problem with Kubuntu 10.04 (64-bit)

CPU: AthlonII 440
GPU: Radeon 4200

***UPDATE:***
Looks like it's a driver issue, as GLXGears seg faults as well (Blender was just the first 3D app I tried...new install).

---

### Post by syva on 2010-07-08
I'm getting the exact same problem with Ubuntu 10.04 (32-bit) 
(Blender's working fine under Windows on a similar Computer)

CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz
GPU: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]

If this is a grafic card problem :
I think I'm using the "Video driver for the ATI Radeon and FireGL graphics accelerators" fglrx.
I tried to install ATI Catalyst without getting it to work.

---

### Post by zachboy82 on 2011-10-21
I am having this problem as well... has anyone figured out the solution yet?  Anything that tries to use my graphics card like blender or desktop effects does not work.  seg fault.  I tried different drivers.

I'm frustrated!

---

