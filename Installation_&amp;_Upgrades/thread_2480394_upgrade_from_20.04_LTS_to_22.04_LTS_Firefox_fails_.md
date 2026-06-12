---
title: "upgrade from 20.04 LTS to 22.04 LTS Firefox fails on NVidia machine"
date: 2022-10-28
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2022-10-28
I'm running an old Dell Vostro 1700 (with NVIDIA GeForce 8600M GT[COLOR=#4D5156][FONT=arial])[/FONT][/COLOR], and using Lubuntu.

I just upgrade, with no great difficulty. Took about an hour.

But on logging in and starting Firefox (my usual and preferred browser), I got a top window bar and nothing else.

It appears I've hit the NVidia/Wayland/Xorg/Ubuntu bug which is much discussed.

The normal cure (for the moment) is to downgrade from Wayland to Xorg, but this is "normally" done in a Gnome config file.

Lubuntu doesn't have Gnome - my install certainly doesn't have "/etc/gdm3/custom.conf", which is where the Wayland/Xorg config is.

So - how do I switch down to Xorg, to resolve my (hopefully temporary) NVidia/Firefox problem?

   BugBear (posting from freshly installed Chrome, yech)

---

### Post by bugbear6502 on 2022-10-28
Ah. I get:

```
echo $XDG_SESSION_TYPE
x11

```

So it looks like Wayland isn't my issue?

---

### Post by bugbear6502 on 2022-10-28
Hardware/driver

```
  *-display                 
       description: VGA compatible controller
       product: G86M [GeForce 8400M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: /dev/fb0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=nouveau latency=0 resolution=1440,900
       resources: irq:25 memory:fd000000-fdffffff memory:f4000000-f7ffffff memory:fa000000-fbffffff ioport:ef00(size=128) memory:c0000-dffff



```

---

### Post by bugbear6502 on 2022-10-28
OK, I'm going down a bad rabbit hole here.

Is there a base-mode graphic driver (or option) I can use (I'd settle for VGA with no acceleration) so I can un-brick my machine?

---

### Post by bugbear6502 on 2022-10-29
I have re-installed 20.04 LTS. 

This video thing wasn't working.

(I also noticed that the new Firefox snap was using 10.7 Gb on my 4Gb machine, which was never going to end well; my current version is 3.8gB, which is still crazy, but less)

---

