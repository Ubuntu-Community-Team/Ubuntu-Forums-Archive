---
title: "Setting up to use only VGA Monitor on a laptop with broken LCD"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by aravind_svu on 2013-01-06
I am posting this just so people like me could find the solution (even my self after sometime) for a problem similar to mine.

Problem:
========
I have a laptop for which LCD/TFT display is broken (nothink can be seen except for weird bakclight and borken patterns). When Ubuntu starts it only uses up the LCD/TFT monitor and I had no way to switch as I can't see what's going on. However the text terminal is shown on a VGA connected display (don't know how and why, but am glad.

Solutions:
==========

Since my LCD/TFT display is broken, I had to either replace the display (can't bother investing more money on this old laptop) or Use an external monitor connected over VGA (I preferred this). Windows seem to work seemlessly on my ACER ASPIRE 4530. With Ubuntu the key that is supposed to switch the displays didn't work. But luckily the text terminal CTRL-ALT-[F1 through to F6] did provide a text terminal on the external VGA Monitor.


The following is only applicable if you have an NVidia GPU with nvidia driver. For example see my configuration below 

```

$sudo lspci
<removed>
**02:00.0** VGA compatible controller: NVIDIA Corporation C77 [GeForce 9100M G] (rev a2)
<removed>

$sudo lspci -s **02:00.0** -v

02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 9100M G] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 014a
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at c9000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=128M]
	Memory at cc000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	[virtual] Expansion ROM at ce000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: nvidia
	Kernel modules: **nvidia_173_updates, nvidia_current, nouveau, nvidiafb**

```

Note the bold faced text above.

If your configuration is similar to above, you could try the below. Note that this solution requires you to have **nvidia-xconfig** which is (at the time of writing this) part of the package **nvidia-173-updates**.

So the steps I followed to enable VGA Monitor (For Graphical display) and disable LCD/TFT monitor are as below:

1) After laptop is booted press CTRL-ALT-F1 to switch to text terminal and if you are lucky it will be shown on external VGA monitor.

2) If you got the terminal on external VGA, follow subsequent steps, otherwise get help.

3) Get the names of the displays connected as shown below

```

$ nvidia-xconfig --query-gpu-info
Number of GPUs: 1

GPU #0:
  Name      : GeForce 9100M G
  PCI BusID : PCI:2:0:0

  Number of Display Devices: 2

  Display Device 0 (**CRT-0**):
     EDID Name             : LG Electronics W2243
     Minimum HorizSync     : 30.000 kHz
     Maximum HorizSync     : 83.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 75 Hz
     Maximum PixelClock    : 150.000 MHz
     Maximum Width         : 1920 pixels
     Maximum Height        : 1080 pixels
     Preferred Width       : 1920 pixels
     Preferred Height      : 1080 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 480 mm
     Physical Height       : 270 mm

  Display Device 1 (**DFP-0**):
     EDID Name             : LPL
     Minimum HorizSync     : 49.323 kHz
     Maximum HorizSync     : 49.323 kHz
     Minimum VertRefresh   : 60 Hz
     Maximum VertRefresh   : 60 Hz
     Maximum PixelClock    : 69.300 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 800 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 800 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 300 mm
     Physical Height       : 190 mm

```

Note the display device names are the ones in the bold faced text above. My laptop desiplay is DFP-0 and the VGA display is CRT-0 (don't get alarmed, even though my external display is LCD panel, it stll uses the name CRT-0, I guess it didn't get that information over VGA port.). You results may vary depending on whether you have connected your display via VGA/Display Port/HDMI/DVI/etc.

4) In my case I wanted the display to be permanently set to CRT-0. So I did as below:

```

$ sudo nvidia-xconfig --use-display-device="CRT-0" --no-twinview

```

the option --no-twinview is optional. I just wanted no power to be wasted on my laptop's display by disabling it. Hence any twinview previously configured has to be gone and GPU should only use CRT-0.

The above would state that it has updated the xorg.conf with the actual lines added.


Now restart the PC or restart the xserver. It should work.

DISCLAIMER: I am not responsble for any damages/misconfigurations as this help is purely based on my experience. I cannot guarantee that it works for your system. Use the above guide at your own risk.

---

