---
title: "graphic driver update"
date: 2024-01-19
forum: Installation &amp; Upgrades
---

### Post by ubontik22 on 2024-01-19
Hello,
I tried to use Blender 4.0.2, but it crashes while loading. I did research and found out that problem is graphic driver.
```
# lshw -c video  
*-display                 
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1600,900
       resources: irq:35 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) memory:c0000-dffff
```
How to update the driver?

Thank you

---

### Post by deadflowr on 2024-01-20
I highly doubt it's a driver issue since the card is over 12 years old now and blender's minimum requirements are for cards under 10 years old.
[https://www.blender.org/download/requirements/](https://www.blender.org/download/requirements/)
Ubuntu should already have the latest possible drivers installed.

Where did you install version 4.0.2 from anyway?
From blender directly or through Ubuntu's Software store?

---

### Post by MAFoElffen on 2024-01-20
Well, it not a problem with Blender and it's Linux dependencies:
```

 Linux distributions using glibc 2.28 or newer

```
What release of Ubuntu are you running? If Jammy, then these packages are all built from glibc source and are all dependent on each other:
```

mafoelffen@msi-ubuntu:~$ apt list libc-bin libc6 locales --installed
Listing... Done
libc-bin/jammy-updates,jammy-security,now 2.35-0ubuntu3.6 amd64 [installed,automatic]
libc6/jammy-updates,jammy-security,now 2.35-0ubuntu3.6 amd64 [installed,automatic]
libc6/jammy-updates,jammy-security,now 2.35-0ubuntu3.6 i386 [installed,automatic]
locales/jammy-updates,jammy-updates,jammy-security,jammy-security,now 2.35-0ubuntu3.6 all [installed,automatic]

```
Those are all >=2.28.

Your iGpu is Crystalwell, which is Iris Pro P6300 (GT3e)... which uses the in-kernel opensource i915 driver...

Please post the output from these, posted within CODE Tags:
```

sudo dmidecode -t 4 | grep -E 'Family:|Version:|ID:|Signature:'
sudo lspic -nnnk | grep -A3 -E 'VGA|Display|3D'
modinfo -p i915
glxinfo | grep -E 'OpenGL version string'
apt list mesa-*-drivers --installed
apt list linux-firmware* intel-media* --installed

```
Please post your link to reference this comment:
> **ubontik22 said:**
> I did research and found out that problem is graphic driver.


---

### Post by ubontik22 on 2024-01-20
From Ubuntu Software
It crashes when I try to run it.
> $ blender
Writing: /tmp/blender.crash.txt
Segmentation fault (core dumped)

---

### Post by MAFoElffen on 2024-01-20
So, besides posting what I asked for... attach the file /tmp/blender.crash.txt to the post as an attachment. If larger than 19.5kb, then paste the contents to a pastebin at paste.ubuntu.com and post he URL.

We are not clairvoyant and cannot see what the errors are until you give us clues on those. That information is needed. Help us to help you.

---

### Post by MAFoElffen on 2024-01-20
Digging deeper, there were different versions of that processor that were released...

I updated the queries in Post #3 to get that information. Still waiting on that information.

---

### Post by ubontik22 on 2024-01-21
[COLOR=#000000]/tmp/blender.crash.txt[/COLOR]
> # Blender 4.0.2, Commit date: 2023-12-05 07:41, Hash 9be62e85b727

# backtrace
/snap/blender/4300/blender() [0xf3a7b0]
/snap/blender/4300/blender() [0x8c42ec]
/lib/x86_64-linux-gnu/libc.so.6(+0x42520) [0x7f2d26242520]
/snap/blender/4300/blender() [0xf7c36d]
/snap/blender/4300/blender() [0xf7c3cd]
/snap/blender/4300/blender() [0xf484b4]
/snap/blender/4300/blender() [0xf5cf01]
/snap/blender/4300/blender() [0xf62414]
/snap/blender/4300/blender() [0x725166]
/lib/x86_64-linux-gnu/libc.so.6(+0x29d90) [0x7f2d26229d90]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0x80) [0x7f2d26229e40]
/snap/blender/4300/blender() [0x8c022e]


# Python backtrace

---

### Post by MAFoElffen on 2024-01-22
You did post the mentioned crash, but nothing else that was requested. I've asked (nicely) twice already. I am not going to beg.

You can't seem to follow instructions on providing that information. Instead you ignore those requests. That would have helped me, to be able to help you.

I will now just ignore you until you provide that. Good luck.

---

### Post by ubontik22 on 2024-01-22
Sorry, I missunderstood.

> $ lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy
> $ apt list libc-bin libc6 locales --installed
Listing... Done
libc-bin/jammy-updates,jammy-security,now 2.35-0ubuntu3.6 amd64 [installed,automatic]
libc6/jammy-updates,jammy-security,now 2.35-0ubuntu3.6 amd64 [installed,automatic]
locales/jammy-updates,jammy-updates,jammy-security,jammy-security,now 2.35-0ubuntu3.6 all [installed,automatic]
> $ sudo dmidecode -t 4 | grep -E 'Family Version ID Signature:' 
    Family: Core i5
    ID: A9 06 03 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 58, Stepping 9
    Version: Intel(R) Core(TM) i5-3330 CPU @ 3.00GHz
> $  sudo lspci -nnk | grep -A3 -E 'VGA|Display|3D'
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
    DeviceName:  Onboard IGD
    Subsystem: Hewlett-Packard Company Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [103c:2ada]
    Kernel driver in use: i915
> $ modinfo -p i915
modeset:Use kernel modesetting [KMS] (0=disable, 1=on, -1=force vga console preference [default]) (int)
enable_dc:Enable power-saving display C-states. (-1=auto [default]; 0=disable; 1=up to DC5; 2=up to DC6; 3=up to DC5 with DC3CO; 4=up to DC6 with DC3CO) (int)
enable_fbc:Enable frame buffer compression for power savings (default: -1 (use per-chip default)) (int)
lvds_channel_mode:Specify LVDS channel mode (0=probe BIOS [default], 1=single-channel, 2=dual-channel) (int)
panel_use_ssc:Use Spread Spectrum Clock with panels [LVDS/eDP] (default: auto from VBT) (int)
vbt_sdvo_panel_type:Override/Ignore selection of SDVO panel mode in the VBT (-2=ignore, -1=auto [default], index in VBT BIOS table) (int)
reset:Attempt GPU resets (0=disabled, 1=full gpu reset, 2=engine reset [default]) (uint)
vbt_firmware:Load VBT from specified file under /lib/firmware (charp)
error_capture:Record the GPU state following a hang. This information in /sys/class/drm/card<N>/error is vital for triaging and debugging hangs. (bool)
enable_hangcheck periodically check GPU activity for detecting hangs. WARNING: Disabling this can cause system wide hangs. (default: true) (bool)
enable_psr:Enable PSR (0=disabled, 1=enable up to PSR1, 2=enable up to PSR2) Default: -1 (use per-chip default) (int)
psr_safest_params:Replace PSR VBT parameters by the safest and not optimal ones. This is helpful to detect if PSR issues are related to bad values set in  VBT. (0=use VBT parameters, 1=use safest parameters) (bool)
enable_psr2_sel_fetch:Enable PSR2 selective fetch (0=disabled, 1=enabled) Default: 0 (bool)
enable_sagv:Enable system agent voltage/frequency scaling (SAGV) (default: true) (bool)
force_probe:Force probe options for specified supported devices. See CONFIG_DRM_I915_FORCE_PROBE for details. (charp)
disable_power_power_well:Disable display power wells when possible (-1=auto [default], 0=power wells always on, 1=power wells disabled when possible) (int)
enable_ips:Enable IPS (default: true) (int)
enable_dpt:Enable display page table (DPT) (default: true) (bool)
fastboot:Try to skip unnecessary mode sets at boot time (0=disabled, 1=enabled) Default: -1 (use per-chip default) (int)
load_detect_test:Force-enable the VGA load detect code for testing (default:false). For developers only. (bool)
force_reset_modeset_test:Force a modeset during gpu reset for testing (default:false). For developers only. (bool)
invert_brightness:Invert backlight brightness (-1 force normal, 0 machine defaults, 1 force inversion), please report PCI device ID, subsystem vendor and subsystem device ID to dri-devel@lists.freedesktop.org, if your machine needs it. It will then be included in an upcoming module version. (int)
disable_display:Disable display (default: false) (bool)
memtest:Perform a read/write test of all device memory on module load (default: off) (bool)
mmio_debug:Enable the MMIO debug code for the first N failures (default: off). This may negatively affect performance. (int)
verbose_state_checks:Enable verbose logs (ie. WARN_ON()) in case of unexpected hw state conditions. (bool)
nuclear_pageflip:Force enable atomic functionality on platforms that don't have full support yet. (bool)
edp_vswing:Ignore/Override vswing pre-emph table selection from VBT (0=use value from vbt [default], 1=low power swing(200mV),2=default swing(400mV)) (int)
enable_guc:Enable GuC load for GuC submission and/or HuC load. Required functionality can be selected using bitmask values. (-1=auto [default], 0=disable, 1=GuC submission, 2=HuC load) (int)
guc_log_level:GuC firmware logging level. Requires GuC to be loaded. (-1=auto [default], 0=disable, 1..4=enable with verbosity min..max) (int)
guc_firmware_path:GuC firmware path to use instead of the default one (charp)
huc_firmware_path:HuC firmware path to use instead of the default one (charp)
dmc_firmware_path:DMC firmware path to use instead of the default one (charp)
gsc_firmware_path:GSC firmware path to use instead of the default one (charp)
enable_dp_mst:Enable multi-stream transport (MST) for new DisplayPort sinks. (default: true) (bool)
enable_dpcd_backlight:Enable support for DPCD backlight control(-1=use per-VBT LFP backlight type setting [default], 0=disabled, 1=enable, 2=force VESA interface, 3=force Intel interface) (int)
enable_gvt:Enable support for Intel GVT-g graphics virtualization host support(default:false) (bool)
request_timeout_ms:Default request/fence/batch buffer expiration timeout. (uint)
lmem_size:Set the lmem size(in MiB) for each region. (default: 0, all memory) (uint)
lmem_bar_size:Set the lmem bar size(in MiB). (uint)
mitigations:Selectively enable security mitigations for all Intel® GPUs in the system.


  auto -- enables all mitigations required for the platform [default]
  off  -- disables all mitigations


Individual mitigations can be enabled by passing a comma-separated string,
e.g. mitigations=residuals to enable only clearing residuals or
mitigations=auto,noresiduals to disable only the clear residual mitigation.
Either '!' or 'no' may be used to switch from enabling the mitigation to
disabling it.


Active mitigations for Ivybridge, Baytrail, Haswell:
  residuals -- clear all thread-local registers between contexts
I was not able to figure out what is the output of modinfo -p i915
> $ glxinfo | grep -E 'OpenGL version string'
OpenGL version string: 4.2 (Compatibility Profile) Mesa 24.1~git2401210600.c3a64f~oibaf~j (git-c3a64f8 2024-01-21 jammy-oi
> $ apt list mesa-*-drivers --installed
Listing... Done
mesa-va-drivers/jammy,now 24.1~git2401210600.c3a64f~oibaf~j amd64 [installed,automatic]
mesa-vdpau-drivers/jammy,now 24.1~git2401210600.c3a64f~oibaf~j amd64 [installed,automatic]
mesa-vulkan-drivers/jammy,now 24.1~git2401210600.c3a64f~oibaf~j amd64 [installed,automatic]
> $ apt list linux-firmware* intel-media* --installed
Listing... Done
intel-media-va-driver/jammy,now 23.2.4+dfsg1-0ubuntu1~22.04.sav0 amd64 [installed,automatic]
linux-firmware/jammy-updates,jammy-updates,now 20220329.git681281e4-0ubuntu3.24 all [installed,automatic]

---

### Post by deadflowr on 2024-01-23
Edit your post and change all the [QUOTE] brackets to [CODE].
Code tags retain the proper formatting and make it easier to read.
Quote does not and adds the bonus of italicizing the output just to make reading it even worse.
On top of that code tags also remove any inadvertent emojis.

---

### Post by MAFoElffen on 2024-01-23
It the iGPU and not meeting te minumum system requirements for that.

Yours is Ivy Bridge
```

8086:0152     Ivy Bridge GT1     Intel HD Graphics 2500

```
Blender's minimum for Intel Graphics is Broadwell..

---

### Post by ubontik22 on 2024-01-23
Thanks for your help.
So, I'll stay with older Blender.

---

