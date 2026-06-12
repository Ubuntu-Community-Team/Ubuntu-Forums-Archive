---
title: "No 3D acceleration/glitchy video on Athlon 5350 APU (kabibi) / Ubuntu 18.10+"
date: 2019-02-02
forum: Installation &amp; Upgrades
---

### Post by bkbrd on 2019-02-02
I was happily running ubuntu 18.04 on my little HTPC box built on Athlon 5350 APU. 
This APU is a bit dated, but  my TV is not that high resolution and it runs Super Tux Kart my kids are playing quite smoothly. After upgrading to 18.10 the graphics is completely dead though and so far I could not reanimate it. 

my hardware is
AMD Athlon(tm) 5350 APU with Radeon(tm) R3
video being detected as 
VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series]
ASRock AM1B-ITX motherboard

I&#8217;ve tryied lot&#8217;s of things (installing/uninstalling drivers/ reinstalling xorg, trying different desktop environments) and as the last crazy measure I updated to 19.04 development, which is probably not good idea. But anyways, pretty much all current symptoms were same on 18.10, please wait with blaming it on unstable brunch :)

What are the symptoms:
Login screen is relatively smooth, but as soon as I log in to gnome-shell session or xfce - can&#8217;t use the system anymore. 
It is not just slow, which would have been understandable assuming software rendering, but, say, desktops start switching back and forth.

One thing to add about my system: my TV is pretty non-standard resolution and I was having hard times adding it to x configs. Basically only LXDE I managed to get working properly. Not sure if it is related to the current problem. 
My TV is Sharp AQUOS LC-32DX1&#12288;supporting 1366×768 resolution. 

Radeon driver seems to be loaded:
```

dmesg | grep radeon
[    3.721992] [drm] radeon kernel modesetting enabled.
[    3.722059] fb: switching to radeondrmfb from VESA VGA
[    3.723148] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    3.723151] radeon 0000:00:01.0: GTT: 2048M 0x0000000020000000 - 0x000000009FFFFFFF
[    3.723324] [drm] radeon: 512M of VRAM memory ready
[    3.723326] [drm] radeon: 2048M of GTT memory ready.
[    3.724329] [drm] radeon: dpm initialized
[    3.753145] radeon 0000:00:01.0: WB enabled
[    3.753167] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0x(____ptrval____)
[    3.753170] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0x(____ptrval____)
[    3.753173] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0x(____ptrval____)
[    3.753175] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0x(____ptrval____)
[    3.753177] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000020000c10 and cpu addr 0x(____ptrval____)
[    3.754057] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000078d30 and cpu addr 0x(____ptrval____)
[    3.754393] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000020000c18 and cpu addr 0x(____ptrval____)
[    3.754395] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000020000c1c and cpu addr 0x(____ptrval____)
[    3.754477] radeon 0000:00:01.0: radeon: using MSI.
[    3.754524] [drm] radeon: irq initialized.
[    4.582053] fbcon: radeondrmfb (fb0) is primary device
[    4.582198] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    4.604151] [drm] Initialized radeon 2.50.0 20080528 for 0000:00:01.0 on minor 0

```

```

lsmod | egrep "amdgpu|amd"
amd_freq_sensitivity    16384  0
edac_mce_amd           28672  0
kvm_amd                94208  0
ccp                    90112  1 kvm_amd
kvm                   622592  1 kvm_amd
amdgpu               2945024  0
chash                  16384  1 amdgpu
gpu_sched              24576  1 amdgpu
i2c_algo_bit           16384  2 amdgpu,radeon
ttm                   106496  2 amdgpu,radeon
drm_kms_helper        172032  2 amdgpu,radeon
drm                   458752  16 gpu_sched,drm_kms_helper,amdgpu,radeon,ttm

```

Not sure why amdgpu is there, but blacklisting it does not change much 


I&#8217;ve tried to uninstall/purge and re-install basically all graphics stack to no avail. 
I&#8217;ve tried installing newer drivers from ppa:oibaf/graphics-drivers to no avail as well.

Live CD with 19.10 is pretty much not responsive too, so it does not look like something was broken upon release-upgrade.

If nothing works I'll install 18.04 again but I'll have to upgrade it later anyways, so I'd give myself a couple of days to fix the new one now...
Any suggestions about where to look further are much appreciated.

UPD:
with 4.15 kernel it seems to work somegow

```

glxinfo | grep "renderer string"
OpenGL renderer string: AMD KABINI (DRM 2.50.0, 4.15.0-44-generic, LLVM 7.0.1)

```

yet
```

glxinfo -i
name of display: localhost:10.0

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  152 (GLX)
  Minor opcode of failed request:  6 (X_GLXIsDirect)
  Serial number of failed request:  53
  Current serial number in output stream:  52

```
but sill working


wit 4.18 I can't use GUI at all, and with ssh session it seems hard to get glxinfo, always gives me only LLVm string even with X forwarding

---

