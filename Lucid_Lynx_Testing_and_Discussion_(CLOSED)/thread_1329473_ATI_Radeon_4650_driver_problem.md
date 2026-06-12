---
title: "ATI Radeon 4650 driver problem"
date: 2009-11-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2009-11-17
Anyone else having problems installing the fglrx drivers at the moment?

The hardware Drivers app doesnt even try to get the drivers, so have to do it manually, but the dkms module install fails and says "could not locate fglrx.ko file"

If i try and enable Desktop Effects, it goes to load but says it cant enable them

any ideas?

---

### Post by ranch hand on 2009-11-17
Nope, sounds normal to me from Hardy (where I came in) to Lounge Lizard.  No support so use the generic.

I you like things like compiz you may not like this.

---

### Post by uBeer on 2009-11-17
It's probably the new kernel that isn't yet supported by the fglrx drivers.

There are 2 things you can do: wait for support in a few months time and in the mean while use metacity as compositor (works fine!) OR (more fun) try out the latest open source drivers that should have a little 3D working, enough for compiz!

---

### Post by DoeRayMe on 2009-11-18
> **uBeer said:**
> It's probably the new kernel that isn't yet supported by the fglrx drivers.

There are 2 things you can do: wait for support in a few months time and in the mean while use metacity as compositor (works fine!) OR (more fun) try out the latest open source drivers that should have a little 3D working, enough for compiz!

Where can i get the latest open source drivers?

---

### Post by Woody1987 on 2009-11-18
fglrx doesnt support the kernel and in all certainty wont till lucid is released, AMD are very slow at adopting newer stuff and wont update till the very last minute. The opensource ATI drivers are your best bet. Lucid has them preinstalled but you can get more upto date drivers by adding this ppa [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=lucid) I run these drivers on my 4670 and have full 2d and 3d accleration and no problems.

---

### Post by DoeRayMe on 2009-11-19
well i downloaded compiz-check and ran it, got this output:

```
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV730 PRO [Radeon HD 4650]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

how can i fix that error?

---

### Post by SevenMachines on 2009-11-19
any bug open on this? fglrx-kernel-source dkms build will fail with 2.6.32
the fix is to add
#include <linux/signal.h>to
/usr/src/fglrx-8.660/kcl_io.c

then the driver should build ok
$dpkg-reconfigure fglrx-kernel-source

---

### Post by SevenMachines on 2009-11-20
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/485444](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/485444)

---

### Post by DougieFresh4U on 2009-11-21
Working very nice here 
ATI Radeon HD3200
Thanks

---

