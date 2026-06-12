---
title: "resolution problem with Intel integrated graphics"
date: 2019-03-26
forum: Installation &amp; Upgrades
---

### Post by b_e_e_k on 2019-03-26
Integrated graphics on a Coffee Lake i3-8100 with a B360 chipset does not recognize the native resolution of my monitor. My LG W3000H has a native resolution of 2560x1600, but only one single resolution (1280x800) is shown by xrandr. The same monitor worked fine on an older Linux build with Nvidia card. Below the 2 attempts at fixes I tried so far, some diagnostic output and specs.

Any ideas how I can get 2560x1600 to work?

Attempt 1: I have added the resolution using xrandr:
```
sudo xrandr --newmode "2560x1600_60.00"  348.50  2560 2760 3032 3504  1600
 1603 1609 1658 -hsync +vsync
sudo xrandr --addmode HDMI-2 "2560x1600_60.00"
```
but that only grows the logical desktop to the right and down, while displaying only the top left quadrant, without changing the resolution.

Attempt 2: I have tried to update the drivers as outlined [here]("https://ubuntuforums.org/showthread.php?t=2377324&p=13710326#post13710326"), but nothing changes.

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 connected primary 1280x800+0+0 (normal left inverted right x axis y axis)
 641mm x 401mm
   1280x800      59.91*
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-3 disconnected (normal left inverted right x axis y axis)
```

Note: When using another monitor (Dell 19") on the same system, xrandr displays many resolutions, and i can switch between them.

No obvious errors with the i915 driver:
```
$ dmesg |grep i915
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-16-generic root=UUI
D=21424809-547e-4f35-9844-d192dec81d67 ro quiet splash i915.alpha_support=1 vt.h
andoff=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-16-generic r
oot=UUID=21424809-547e-4f35-9844-d192dec81d67 ro quiet splash i915.alpha_support
=1 vt.handoff=1
[    1.158753] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem
,decodes=io+mem:owns=io+mem
[    1.159039] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.
4)
[    1.433188] [drm] Initialized i915 1.6.0 20180514 for 0000:00:02.0 on minor 0
[    1.468306] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.395296] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_co
mponent_bind_ops [i915])
```


Specs:
i3-8100
MoBo MSI B360M Mortar (using the DVI port; DVI port worked on the older Ubuntu build I mentioned above)
```
inxi -v 1
System:    Host: nifty Kernel: 4.18.0-16-generic x86_64 bits: 64
           Desktop: Gnome 3.28.3 Distro: Ubuntu 18.04.2 LTS
CPU:       Quad core Intel Core i3-8100 (-MCP-) speed/max: 800/3600 MHz
Graphics:  Card: Intel 8th Gen Core Processor Gaussian Mixture Model
           Display Server: x11 (X.Org 1.20.1 ) driver: i915
           Resolution: 1280x800@59.91hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 630 (Coffeelake 3x8 GT2
)
           version: 4.5 Mesa 18.2.2
Drives:    HDD Total Size: 1024.2GB (0.8% used)
Info:      Processes: 272 Uptime: 22 min Memory: 1277.0/15911.6MB
           Client: Shell (bash) inxi: 2.3.56 
```

---

### Post by CatKiller on 2019-03-26
That monitor doesn't seem to provide accurate EDID information. There are reports on all platforms of it not being autoconfigured properly.

You could put proper frequency ranges in your xorg.conf, and you may even need to explicitly use the IgnoreEDID option.

---

### Post by b_e_e_k on 2019-03-26
> **CatKiller said:**
> That monitor doesn't seem to provide accurate EDID information. There are reports on all platforms of it not being autoconfigured properly.

You could put proper frequency ranges in your xorg.conf, and you may even need to explicitly use the IgnoreEDID option.

I'll try that. Is there a way how I can retrieve these frequency ranges from the old Ubuntu 14 rig, where the same monitor worked fine with an Nvidia card?

---

### Post by CatKiller on 2019-03-26
> **b_e_e_k said:**
> I'll try that. Is there a way how I can retrieve these frequency ranges from the old Ubuntu 14 rig, where the same monitor worked fine with an Nvidia card?

Probably. I can't remember if it's dmesg or /var/log/Xorg.0.log where the Nvidia driver puts the configuration information that it's discovered. Maybe both. There's the get-edid tool, too, although the EDID information could well be inaccurate - given that's it's not working automatically.

The manual only gives a HorizSync value of 98.71 kHz rather than a range. Specifying a small range that includes that value might work. Specifying a modeline and using IgnoreEDID might work, too. It's been a while, but I think you can ignore specific parts of the EDID (the bits that you know are wrong) and still use the rest. It includes things  - like size, and DPI, and whether it can use power saving modes - that are still useful, provided they're accurate.

There are a few things you can poke it with. Essentially you want the end result to be that it's automatically picking the correct resolution from good information and not using bad information.

---

### Post by b_e_e_k on 2019-03-27
That worked! I found the correct Modeline in the Xorg.0.log of hte old rig, and also with 
```
xvidtune -show
```

I can now set the resolution with xrandr commands. How can that be done at start-up?

```
xrandr --newmode "2560x1600" 268.00   2560 2608 2640 2720   1600 1603 1609 1646 +hsync -vsync
xrandr --addmode HDMI-2 "2560x1600"
xrandr --output HDMI-2 --mode 2560x1600
```

---

### Post by CatKiller on 2019-03-27
> **b_e_e_k said:**
> I can now set the resolution with xrandr commands. How can that be done at start-up?

You can add the modeline to xorg.conf. It's not there by default any more, but it will be used if it's there. You might even get away with having just a Monitor snippet in xorg.conf.d rather than having a full xorg.conf.

---

### Post by smillien on 2020-03-25
Same issue with same monitor: LG Flatron W300H :-)
And the problem was the cable DVI.
You have to use a cable DUAL DVI.
Works perfectly in mode 2560x1600 with the right cable.

---

