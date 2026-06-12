---
title: "Brightness Controls Still Don't Work"
date: 2010-03-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-03-12
Hello,

I am using a Sony Vaio with an nVidia GeForce 8400M GT graphics card. It is a couple of years old now. The current situation is this:

- Fn keys are detected properly (and show brightness indicator on screen when pressed).
- NVClock and smartdimmer change the brightness successfully.
- /sys/class/backlight has two folders: nv_backlight and sony.

```
/sys/class/backlight$ ls -r *
sony:
uevent     power           brightness  actual_brightness
subsystem  max_brightness  bl_power

nv_backlight:
uevent     power           device      bl_power
subsystem  max_brightness  brightness  actual_brightness
```

The problem is, the brightness applet on gnome-panel AND the Fn keys (though detected properly) *do not actually change the brightness*!

Does anybody know *anything* about this issue? I can't find any specifics on it at all. Some people claim it's because of HAL being removed (but it didn't work with HAL either).

Whenever I want to change my brightness, I have to *sudo* on a terminal. It would be great if I could rectify that situation, or at least, get a news update about it:P

```
xrandr --prop
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS-1 connected 1440x900+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
	dithering:	Off
		supported: Off          On          
	scaling mode:	Full
		supported: None         Full         Center       Full aspect 
   1440x900       59.9*+
   1152x864       60.0  
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
	scaling mode:	None
		supported: None         Full         Center       Full aspect 
DVI-D-1 disconnected (normal left inverted right x axis y axis)
	dithering:	Off
		supported: Off          On          
	scaling mode:	Full
		supported: None         Full         Center       Full aspect
```

---

### Post by cyberkilla on 2010-03-13
Bump.

---

### Post by sirkeith on 2010-03-14
On my system I found a switch in my bios that had 2 settings. Changing the setting allowed me to make the screen brighter using the panel applet and I assume it affects the FN brightness key as well.

keith

---

### Post by chrisccoulson on 2010-03-14
If you're using the proprietary NVIDIA driver, then you will need HAL installed for brightness control anyway (unless the brightness is controlled in hardware). NVIDIA does not support brightness control via the XRANDR extension. Installing HAL if it is not installed already would be a good start

---

### Post by cyberkilla on 2010-03-16
> **chrisccoulson said:**
> If you're using the proprietary NVIDIA driver, then you will need HAL installed for brightness control anyway (unless the brightness is controlled in hardware). NVIDIA does not support brightness control via the XRANDR extension. Installing HAL if it is not installed already would be a good start

Hello,

HAL is already installed. It does not work with any driver, from VESA upwards. There must be other people with the same problem.

It's just rather annoying that it works if I use nvclock on the commandline, and the actual Fn keys are detected properly, yet nobody has figured out a way to connect the two.:P

> **sirkeith said:**
> On my system I found a switch in my bios that had 2 settings. Changing the setting allowed me to make the screen brighter using the panel applet and I assume it affects the FN brightness key as well.

keith

I can barely change the Date & Time in this stupid locked-down proprietary Sony-crippled BIOS:)

---

### Post by peepingtom on 2010-03-17
Try running the proprietary nVidia drivers, and add the following the "Device" section of xorg.conf
Option "RegistryDwords" "EnableBrightnessControl=1"

---

### Post by cyberkilla on 2010-03-18
> **peepingtom said:**
> Try running the proprietary nVidia drivers, and add the following the "Device" section of xorg.conf
Option "RegistryDwords" "EnableBrightnessControl=1"

Interesting. Thanks for posting - I'll reinstall the nVidia drivers over the weekend and see if it fixes the problem.

---

