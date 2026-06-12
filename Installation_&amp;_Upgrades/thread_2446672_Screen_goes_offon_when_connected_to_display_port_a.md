---
title: "Screen goes off/on when connected to display port after upgrade to 20.04"
date: 2020-07-04
forum: Installation &amp; Upgrades
---

### Post by papadolinux on 2020-07-04
Hello there!

As the titles briefly says, I have upgraded to Kubuntu 20.04 from 19.10. Session went ok but after rebooting i noticed one or two instances where my screen (external monitor connected via display port to my laptop) went on and off for 1-2 seconds. After the recent update to Kernel 5.4.0-40 these on and off instances are more frequent. System and sound etc works (doesn't hang) , only the screen goes black and shows again, which is very annoying. This does not happen with HDMI cable connected, but instead there are some minor screen glitches, not very often though. I did not have any of those with 19.10...my system is details is shown below:

```
Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-40-generic
OS Type: 64-bit
Processors: 8 × Intel® Core&#8482; i5-10210U CPU @ 1.60GHz
Memory: 15,5 GiB of RAM


```

lspci

```
00:00.0 Host bridge: Intel Corporation Device 9b61 (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics (rev 02)
00:12.0 Signal processing controller: Intel Corporation Comet Lake Thermal Subsytem
00:14.0 USB controller: Intel Corporation Device 02ed
00:14.2 RAM memory: Intel Corporation Device 02ef
00:15.0 Serial bus controller [0c80]: Intel Corporation Serial IO I2C Host Controller
00:16.0 Communication controller: Intel Corporation Comet Lake Management Engine Interface
00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller
00:1c.0 PCI bridge: Intel Corporation Device 02bc (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device 02b0 (rev f0)
00:1d.1 PCI bridge: Intel Corporation Device 02b1 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Device 02b4 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0284
00:1f.3 Audio device: Intel Corporation Device 02c8
00:1f.4 SMBus: Intel Corporation Device 02a3
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake SPI (flash) Controller
01:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:00.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:01.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
02:02.0 PCI bridge: Intel Corporation JHL7540 Thunderbolt 3 Bridge [Titan Ridge 2C 2018] (rev 06)
03:00.0 System peripheral: Intel Corporation JHL7540 Thunderbolt 3 NHI [Titan Ridge 2C 2018] (rev 06)
3a:00.0 USB controller: Intel Corporation JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 2C 2018] (rev 06)
3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader (rev 01)
3b:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)
40:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
45:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981
```

inxi -G

```
Graphics:  Device-1: Intel UHD Graphics driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa resolution: 2560x1440~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2) v: 4.6 Mesa 20.0.8
```

vainfo

```
libva info: VA-API version 1.7.0
libva info: User environment variable requested driver 'iHD'
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 20.1.1 ()
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            : VAEntrypointVLD
      VAProfileMPEG2Main              : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointVLD
      VAProfileH264Main               : VAEntrypointEncSliceLP
      VAProfileH264High               : VAEntrypointVLD
      VAProfileH264High               : VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           : VAEntrypointVLD
      VAProfileJPEGBaseline           : VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline: VAEntrypointVLD
      VAProfileH264ConstrainedBaseline: VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          : VAEntrypointVLD
      VAProfileHEVCMain               : VAEntrypointVLD
      VAProfileHEVCMain10             : VAEntrypointVLD
      VAProfileVP9Profile0            : VAEntrypointVLD
      VAProfileVP9Profile2            : VAEntrypointVLD
```

glxinfo | grep -i opengl

```
OpenGL vendor string: Intel
OpenGL renderer string: Mesa Intel(R) UHD Graphics (CML GT2)
OpenGL core profile version string: 4.6 (Core Profile) Mesa 20.0.8
OpenGL core profile shading language version string: 4.60
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.6 (Compatibility Profile) Mesa 20.0.8
OpenGL shading language version string: 4.60
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.0.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:


```

dmesg | grep -i i915 (here is where i get some errors)

```
[    1.867750] i915 0000:00:02.0: VT-d active for gfx access
[    1.867792] i915 0000:00:02.0: vgaarb: deactivate vga console
[    1.869955] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.870380] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_04.bin (v1.4)
[    1.901537] [drm] Initialized i915 1.6.0 20190822 for 0000:00:02.0 on minor 0
[    1.942047] fbcon: i915drmfb (fb0) is primary device
[    1.942050] i915 0000:00:02.0: fb0: i915drmfb frame buffer device
[    4.475863] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[  343.832335] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[ 1533.852245] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[ 7999.870873] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[10325.714958] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[11963.761144] [drm:intel_dp_link_training_clock_recovery [i915]] *ERROR* failed to enable link training
[11966.525181] [drm:intel_dp_link_training_clock_recovery [i915]] *ERROR* failed to enable link training
[11966.808691] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun
[12009.683387] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
[12078.020618] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe A FIFO underrun
```

Can anyone please detect what is wrong and help me resolve it?

Many thanks in advance!

---

### Post by papadolinux on 2020-07-05
OK so quick update: I switched to the previous kernel ie 5.4.0-39 and now everything works perfectly. I will keep this thread open for now until there is a fix after the new kernel which i will load and revert back here with my feedback.

---

### Post by papadolinux on 2020-07-22
Coming back to this and after the recent kernel upgrade to 5.4.0-42, the issue persists. I am having even more screen flickering on/offs. Reverted back to 5.4.0-39.
I don't know what to do with this issue. Should I keep upgrading hoping that this will stop eventually or stick with 5.4.0-39 for ever...?

---

### Post by mastablasta on 2020-07-23
i would say open bug report on launchpad if it is not there yet. 

looks like some sort of regression. for now lock the kernel. it used to be possible in Muon, but maybe Synaptics will be needed for that.

---

### Post by papadolinux on 2020-09-08
I am coming back once again since i cannot find any solution to the problem. I have found a similar open issue in Launchpad, which is still unresolved ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1550779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1550779) ). I have added my issue there too but no one is dealing with it.

Could anyone here offer some assistance? In the recent kernel update ( .47) i am still getting the same problems ie 

[FONT=arial] [drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun  
[/FONT]
  
drm:intel_cpu_fifo_underrun_irq_handler [i915]] *ERROR* CPU pipe B FIFO underrun

  
Cheers!

---

