---
title: "Slow intel 945 graphics"
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Cloud79 on 2008-12-19
glxinfo | grep renderer
OpenGL renderer string: Software Rasterizer

Desktop effects are slow! The xorg.conf
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

```
(--) PCI:*(0@0:2:0) Intel Corporation Mobile 945GME Express Integrated Graphics Controller rev 3, Mem @ 0xf0500000/0, 0xd0000000/0, 0xf0600000/0, I/O @ 0x00001800/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xf0580000/0

```

Are there any solution to this. I have searched other posts but haven't found any.

---

### Post by jrusso2 on 2008-12-19
Seems like you don't have a driver for it.  But I am not sure what one that uses?

---

### Post by Cloud79 on 2008-12-19
> **jrusso2 said:**
> Seems like you don't have a driver for it.  But I am not sure what one that uses?

It uses the intel driver. It seems to be broken with this chipset

---

### Post by DougieFresh4U on 2008-12-19
> **Cloud79 said:**
> It uses the intel driver. It seems to be broken with this chipset

Intel has been 'borked' for some time.
I have the 865G chipset. Have been stuck with 'vesa' until they sort this mess

---

### Post by Cloud79 on 2008-12-19
> **DougieFresh4U said:**
> Intel has been 'borked' for some time.
I have the 865G chipset. Have been stuck with 'vesa' unil they sort this mess

I hope it will be soon, i have to use windows on my netbook until then. That sucks *ss!

---

