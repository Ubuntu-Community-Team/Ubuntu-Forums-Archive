---
title: "Wine problems after upgrade to Feisty"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by jrogers360 on 2007-06-12
Ever since I upgraded to Feisty, I've been experiencing some grief with wine.  I think I can blow up my fake_c and fix most of it, but there is one problem I'm not sure about:

```
err:wgl:has_opengl  glx_version is 1.4 and GLX_SGIX_fbconfig extension is unsupported. Expect problems.

```

I see this error over and over.  Any ideas what is causing it?  Any ideas on how to resolve/solve it?

---

### Post by BoeroBoy on 2007-06-14
Hi.  I notice the same problem on an install of Sabayon.  I'm actually trying to make use of an old 2xPII-400 HP Kayak XAs with a geForce 2ti.  Using wine over a FreeNX session, I get the same error.  I know that's pushing a legacy system like the Kayak to its limits, but I'm just doing a test.  ;)

My guess is your video card isn't very new.  Am I right?  Maybe it's not compatible with the latest OpenGL.  I'm trying to tweak my xorg.conf to work around it.

---

### Post by jrogers360 on 2007-06-14
Interesting, I too only see it on NX.  When local, it runs w/out errors.  In fact, the program I'm running crashes while connected via NX with a memory error, but runs fine locally (consistently)

I have some old hardware too:

```
jrogers@rafiki:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:09.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
jrogers@rafiki:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 1
model name      : Intel(R) Pentium(R) 4 CPU 1.70GHz
stepping        : 2
cpu MHz         : 1694.635
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
bogomips        : 3392.22
clflush size    : 64

```

---

