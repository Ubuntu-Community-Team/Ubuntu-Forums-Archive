---
title: "How to install the new mesa version 7.0"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by nbabs on 2007-06-29
Would you please help me in installing the new MESA version 7.0? Is this version available in synaptic? If not how to install it?

---

### Post by nbabs on 2007-07-01
Have you got any idea to install mesa 7.0?

---

### Post by Leptom on 2007-07-04
**[COLOR="Red"]WORKS WITH MESA 7.0.1[/COLOR]**

Download from [http://sourceforge.net/project/showfiles.php?group_id=3](http://sourceforge.net/project/showfiles.php?group_id=3)  MesaLib.tar.gz file

Install libdrm-dev (needed for compilation):

	$ sudo aptitude install libdrm-dev libdrm-dev build-essential xorg-dev

Nota: DRM is Direct Rendering Manager, it is not Digitals Rights Management.

Decompress it, I save it in  ~/misc

	$ tar xzvf MesaLib-7.0.tar.gz

It make Mesa-7.0 folder, enter in:
	
	$ cd Mesa-7.0

Begin compile. For 32bits:

	$ make linux-dri-x86

For 64bits:

	$ make linux-dri-x86-64

... wait compile ... paciencia ... más paciencia... :D

Tips: In config/linux-dri-* files can write compile optimizations. For example I used: 
ARCH_FLAGS = -m32 -O2 -march=pentium-m

If all was ok then you can see this files on lib/ :

	$ ls lib/

ffb_dri.so   i915_dri.so     i965_dri.so  libGL.so.1    libGLU.so    libGLU.so.1.3.070100  libGLw.so.1      mach64_dri.so  r128_dri.so  r300_dri.so    s3v_dri.so     sis_dri.so   trident_dri.so
i810_dri.so  i915tex_dri.so  libGL.so     libGL.so.1.2  libGLU.so.1  libGLw.so             libGLw.so.1.0.0  mga_dri.so     r200_dri.so  radeon_dri.so  savage_dri.so  tdfx_dri.so  unichrome_dri.so


The libraries are installed in /usr/local/lib and drivers in /usr/X11R6/lib/modules/dri. We need libraries in /usr/lib and drivers in /usr/lib/dri. We must edit configs/default (line 81 and 82):

# Installation directories (for make install)
INSTALL_DIR = /usr/local
DRI_DRIVER_INSTALL_DIR = /usr/X11R6/lib/modules/dri

Change to:

# Installation directories (for make install)
INSTALL_DIR = /usr/
DRI_DRIVER_INSTALL_DIR = /usr/lib/dri

Now we can install:

$ sudo make install

Restart and voila!!

---

### Post by Meister_Eder on 2007-07-06
Thanks!

---

### Post by kilroo on 2007-09-05
In order for this to get me direct rendering, I had to make install again WITHOUT the changes to the installation directories suggested here. glxinfo | grep direct now gets

libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

Radeon 9800 Pro, incidentally.

---

### Post by runemaste644 on 2007-10-07
> **Leptom said:**
> 

Nota: DRM is Direct Rendering Manager, it is not Digitals Rights Management.



Thank goodness!

---

### Post by runemaste644 on 2007-10-07
it is now planetpenguin-racer in the universe repo.

---

