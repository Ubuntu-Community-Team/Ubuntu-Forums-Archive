---
title: "NVIDIA nightmare"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by kippertoffee on 2007-02-21
Hello,

I'm having a nightmare getting my nvidia GEforce6200 card working.

I've tried installing using apt-get and synaptic, and with both when I run 
"sudo nvidia-glx-config enable"
It tells me that the nvidia driver doesn't match my kernel driver.

I've tried setting up manually, changing the
 xorg.conf >[devices] - "nv" to "nvidia"
but that makes my X11 crash on startup.

I have also tried envy, but that just crashes X11 as soon as i click "1-install nvidia".

I guess my next option is to install manually (unless anyone has a better idea), but the NVIDIA installer wants the kernel source files to compile with, and I can't find them for 2.6.17.11.

Also, i know i need to remove nvdia-glx package before installing manually, but what about the restricted packages?

So, as you can see, i'm pretty stuck. 
Thanks for any help, Pete.

---

### Post by kippertoffee on 2007-02-21
p.s. here is the bit from my xorg.conf
most documentation i have seen says "PCI:1:0:0"
Could this be the problem?

CHeers, pete.

Section "Device"
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

---

### Post by kippertoffee on 2007-02-21
After all that, one last try installing nvidia-glx from synaptic, and it worked.

Brilliant, sorry for the waste of time.

Pete

---

