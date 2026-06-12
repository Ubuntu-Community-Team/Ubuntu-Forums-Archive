---
title: "ubutnu wont detect my screen"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Slapino on 2010-03-30
Ubuntu wont detect my screen (mag bf22) correctly..that causes poor resolution (1152*864 max) 
my screen is able to at least a 1600*1200 resolution (witch i use in my windows boot ) 
is there anything i can do in order to fix or increase the resolution ?.. i have already installed the drivers correctly  


asus p7p55d 
intel core i5 750 
nvidia geforce 9500gt 
wd640GB black caviar 


thanks in advance to all the helpers:wink:

---

### Post by realzippy on 2010-03-30
Install the NVIDIA graphics driver...

---

### Post by ..::| Dave89 |::.. on 2010-03-30
To do that go to the System menu at the top of the screen, then to Administration and click on Hardware Drivers, It should automatically pick up what drivers are needed.resrtar

---

### Post by Slapino on 2010-03-30
hmm .. i already installed the nvidia drivers 
im dealing a harder problem
is there any way i can force ubuntu to increase screen resolution?

---

### Post by realzippy on 2010-03-30
nvidia-settings does not give the choice?

---

### Post by Slapino on 2010-03-30
no... 
the same choises as the built in resolution settings

---

### Post by Slapino on 2010-03-30
someone?

---

### Post by realzippy on 2010-03-31
AH,so you used the display-settings from gnome also?Open
nautilus and search for a file "monitors.xml" and delete this file if exists,then reboot.(Or log out/in)...
(file is in /home/yourusername/.config)
Does this change resolution-options in nvidia-settings?
If not you could try to add resolutions by the use of *xrandr*,but:
In former similar resolution-threads it sometimes happened that the lack of resolutions was due to the VGA cable,there are differences with the EDID pins,so,can you try (a few) different cables first before starting to mess around with *xrandr*?

---

### Post by realzippy on 2010-03-31
If a different cable does not work,we need the outputs of:

```
xrandr
```

and


```
cvt 1600 1200 60
```

---

### Post by Slapino on 2010-03-31
> **realzippy said:**
> AH,so you used the display-settings from gnome also?Open
nautilus and search for a file "monitors.xml" and delete this file if exists,then reboot.(Or log out/in)...
(file is in /home/yourusername/.config)
Does this change resolution-options in nvidia-settings?
If not you could try to add resolutions by the use of *xrandr*,but:
In former similar resolution-threads it sometimes happened that the lack of resolutions was due to the VGA cable,there are differences with the EDID pins,so,can you try (a few) different cables first before starting to mess around with *xrandr*?

hmm.. i can try connecting it through a hdmi - dvi cable (one side hdmi witch connects to the screen and the other way around , dvi to the computer
but would it make a difference? 


the output of xrandr :

```
Screen 0: minimum 320 x 240, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1024x768       50.0     60.0  
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
   1152x864       60.0* 
```

the output of 
cvt 1600 1200 60```
# 1600x1200 59.87 Hz (CVT 1.92M3) hsync: 74.54 kHz; pclk: 161.00 MHz
Modeline "1600x1200_60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync

```

it may look od because i tried to make a few changes ... im not sure how but it might affected this commands output 


take you for your time..

---

### Post by realzippy on 2010-04-01
[I]hmm.. i can try connecting it through a hdmi - dvi cable (one side hdmi witch connects to the screen and the other way around , dvi to the computer
but would it make a difference?[/I] 

Yes,please try that before going on with xrandr.
I'll be back in a few hours..

---

