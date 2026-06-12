---
title: "GPU Temperature showing as -390C!"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by pookieman123 on 2011-10-27
Hi

Pretty new to this, but I want to see my GPU temp I have a XFX GT 9600 GSO 512mb, been reading a few posts this is what I can show so far:

> 

/usr/local/src/nvclock$ nvclock -i
-- General info --
Card:         nVidia Geforce 9600GSO
Architecture:     G92 A2
PCI id:     0x610
GPU clock:     499.500 MHz
Bustype:     PCI-Express

-- Shader info --
Clock: 1242.000 MHz
Stream units: 96 (11111100b)
ROP units: 8 (0101b)
-- Memory info --
Amount:     512 MB
Type:         128 bit DDR3
Clock:         899.996 MHz

-- PCI-Express info --
Current Rate:     16X
Maximum rate:     16X

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: -390C

-- VideoBios information --
Version: 62.92.42.00.00
Signon message: GeForce 9600 GSO VGA BIOS
Performance level 0: gpu 500MHz/shader 1250MHz/memory 900MHz/1.00V/100%
VID mask: 3
Voltage level 0: 0.95V, VID: 2
Voltage level 1: 1.00V, VID: 1
Voltage level 2: 1.05V, VID: 0


This can't be right! after doing sensors-detect

> 

sensors
coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +30.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +30.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +28.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +29.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +28.0°C  (high = +80.0°C, crit = +98.0°C)

and

> 

nvidia-smi -q -d

Missing value for -d argument. Please run 'nvidia-smi -h' for help.

I am on 11.10 what am I doing wrong, I have installed the recommended drivers

thanks!

---

### Post by garvinrick4 on 2011-10-27
> GPU Temperature showing as -390C!
That is pretty darn hot 390 degrees C!! 

Let's us say 39 degrees C and that is about 120 degrees F so about right isn't it.

---

### Post by pookieman123 on 2011-10-27
You think that's it?

Weird that it has a minus in front of it? Is there anyway I can verify? Also in the NVIDIA X Server Settings I can't see the temperature anyway I can change the fan speed etc but I can't see the temp being shown, just nervous about tinkering with fan speeds without some assurance that I am not damaging the GPU.

---

