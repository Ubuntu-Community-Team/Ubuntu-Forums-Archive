---
title: "Wrong Kernel Module Loading"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yellow Pasque on 2009-08-29
I don't know how much help I'll get here, but if someone could at least give me an idea of where to begin troubleshooting this issue, it would be appreciated.

The issue: I have an AMD/ATI 770 chipset with a RadeonHD 4550 PCI-E card. Ubuntu is loading intel driver modules (i915 and intel_agp) that prevent the radeon kernel module from loading.

I don't think I can report this as a bug because I'm using Alex Deucher's DRM (compiled a special git branch) of that allows accelerated 3D with open-source drivers.

```
lsmod
Module                  Size  Used by
...
**i915 **                 244008  0 
drm                   193856  1 i915
i2c_algo_bit            7076  1 i915
video                  23388  1 i915
output                  3680  1 video
**intel_agp**              31664  0
```

I know I can workaround the issue by blacklisting the appropriate intel modules and manually loading the radeon module in /etc/modules, but I would rather troubleshoot the problem and learn how i915 is getting loaded.

---

### Post by taavikko on 2009-08-29
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/404496](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/404496)
Basically the same bug.

---

### Post by Regenweald on 2009-08-29
Following Dinxters instructions, I stop gdm, then rmmod drm and i915 then modprobe nouveau at boot. Works :)

---

### Post by prshah on 2009-08-29
> **Temüjin said:**
> 
The issue: I have an AMD/ATI 770 chipset with a RadeonHD 4550 PCI-E card. Ubuntu is loading intel driver modules (i915 and intel_agp) that prevent the radeon kernel module from loading.

..or you can turn off onboard video support in the BIOS, if you are not using the onboard video (eg, multi-head).

---

### Post by Yellow Pasque on 2009-08-29
> **taavikko said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/404496](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/404496)
Basically the same bug.
Thanks for the link. It confirms that it's an Ubuntu issue and not an issue with the drm I installed.

---

### Post by Regenweald on 2009-08-29
Seems to have been fixed.

---

### Post by taavikko on 2009-08-29
> **Regenweald said:**
> Seems to have been fixed.

hmm, not seeing the fix?
```
i915                  244008  0 
drm                   193856  3 radeon,ttm,i915
i2c_algo_bit            7076  2 radeon,i915
video                  23388  1 i915
output                  3680  1 video
intel_agp              31664  0 
```
Part of lsmod, and running radeon.

---

### Post by Regenweald on 2009-08-29
> **taavikko said:**
> hmm, not seeing the fix?
```
i915                  244008  0 
drm                   193856  3 radeon,ttm,i915
i2c_algo_bit            7076  2 radeon,i915
video                  23388  1 i915
output                  3680  1 video
intel_agp              31664  0 
```
Part of lsmod, and running radeon.

Running nvidia here, booted straight to desktop after recent updates. 
```

**nouveau**               643940  1 
snd                    77096  22 
**ttm**                    50032  1 nouveau
k8temp                  5504  0 
serio_raw               6596  0 
soundcore               9088  1 snd
gspca_sonixj           24160  0 
edac_core              48876  1 amd64_edac_mod
gspca_main             26816  1 gspca_sonixj
btusb                  14260  0 
sn9c102               148708  0 
videodev               43360  2 gspca_main,sn9c102
v4l1_compat            16804  1 videodev
v4l2_compat_ioctl32    13344  1 videodev
dell_wmi                3216  0 
dcdbas                  9136  0 
joydev                 12960  0 
usb_storage            65888  0 
usbhid                 44000  0 
forcedeth              61260  0 
fbcon                  41248  0 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6656  1 fbcon
softcursor              2336  1 bitblit
**drm **                  197632  3 nouveau,ttm
**i2c_algo_bit**            7076  1 nouveau
video  

```

Not fixed ati yet ?

---

