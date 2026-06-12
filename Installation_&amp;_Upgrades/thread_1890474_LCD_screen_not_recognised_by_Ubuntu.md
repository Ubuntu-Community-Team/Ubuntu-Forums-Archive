---
title: "LCD screen not recognised by Ubuntu"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by titi79 on 2011-12-03
Hello,
Since several months, I have bought a new LCD screen (LG Flatron IPS226).
After several attempts, I am still not able to set up the suitable resolution under Ubuntu (1920x1080).
I am stick with 800x600 using DVI, or 1024*768 using VGA with standard screen preferences tool, or up to 1360x768 using VGA and nvidia X server settings.
I am not a Linux expert. I have alread read forums, reinstall Ubuntu several times, modify xorg, try modelines or edid customization according to various pages found on the Internet.

Screen seems OK. Everything is fine with Windows (VGA and DVI).
I am lost and discouraged.
Could you help me, or should I go back to windows to be able to fully use my LCD screen ?

Thank you.

---

### Post by bluexrider on 2011-12-03
with all due respect. LG doesn't have Linux drivers for the monitor in question.

---

### Post by titi79 on 2011-12-03
> **bluexrider said:**
> with all due respect. LG doesn't have Linux drivers for the monitor in question.
Does it mean that Ubuntu is not able to display with full resolution with some monitors ?
I did not know that drivers were needed for monitors...
Nobody is using Linux with this LG monitor ??

---

### Post by darkod on 2011-12-03
You never mentioned the model of the video card? Did you install the correct drivers for linux?

Otherwise it would probably give you some "standard" low resolution, like in your case.

---

### Post by fantab on 2011-12-03
Monitors are OS independent just like your HDD or ODD. However the Graphics Card NEEDS OS dependent drivers. If you have installed any proprietary Drivers then I suggest you reinstall them. 

What resolution did your previous Monitor use?

---

### Post by MAFoElffen on 2011-12-04
> **fantab said:**
> Monitors are OS independent just like your HDD or ODD. However the Graphics Card NEEDS OS dependent drivers. If you have installed any proprietary Drivers then I suggest you reinstall them. 

What resolution did your previous Monitor use?
+3, since 2 other people have hinted at this.
```

lspci -vnn | grep VGA

```
and if you posted the  /var/log/Xorg.0.log file would show us what video card, what video drivers and modules are being used. how Linux is seeing your Display and the EDID data it's returning.

If you have NVidia or ATI, good prespect. If new Intel... all depends.

---

### Post by MAFoElffen on 2011-12-04
Also, if you installed hwinfo
```

sudo apt-get install hwinfo

```
Then posted the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q

```
That would show the modes that your video cards and monitor is reporting back to Linux.

---

### Post by titi79 on 2012-01-22
Hello,
Thanks for your interest to help me. Sorry for my late answer, I did not see that I have to follow-up my own thread (I though it was automatic).
Since I have still the same problem, find below requested logs.
I hope it will help.

Result of "lspci -vnn | grep VGA"

01:00.0 VGA compatible controller [0300]: nVidia Corporation G96 
[GeForce 9500 GT] [10de:0640] (rev a1) (prog-if 00 [VGA controller]

/var/log/Xorg.0.log => See attachament

Result of "sudo hwinfo --framebuffer"

02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.Iu3tbmp2o4F
  Hardware Class: framebuffer
  Model: "NVIDIA G96 Board - 07290000"
  Vendor: "NVIDIA Corporation"
  Device: "G96 Board - 07290000"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf9000000-0xf9dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown 

Result of "sudo hwinfo --monitor"

48: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 1024x768@76Hz
  Driver Info #0:
    Max. Resolution: 1024x768
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-61 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown 
 
Result of "xrandr -q"

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 0mm x 0mm
   1360x768       50.0*    51.0     53.0  
   1024x768       52.0  
   800x600        54.0     55.0     56.0  
   680x384        57.0     58.0  
   640x480        59.0  
   512x384        60.0  
   400x300        61.0  
   320x240        62.0

---

### Post by titi79 on 2012-02-19
Hi,
Nobody able to help me ??

---

