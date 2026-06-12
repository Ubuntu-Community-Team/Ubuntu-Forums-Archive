---
title: "[SOLVED] Post-upgrade dual-monitor failure"
date: 2018-10-27
forum: Installation &amp; Upgrades
---

### Post by JackD on 2018-10-27
Upgraded to 18.04.1 from 16.04, and my dual-monitor failed, the second monitor (via HDMI) was never recognized). Never had a problem with 16.04. 

Here's what I tried, to no avail, [https://askubuntu.com/questions/908764/display-manager-gdm3-not-working-under-ubuntu-17-04/1066697#1066697](https://askubuntu.com/questions/908764/display-manager-gdm3-not-working-under-ubuntu-17-04/1066697#1066697)

I've updated to 18.10, without any improvement.

Symptoms:
[LIST]
The 2nd monitor will actually work as the sole monitor, for the login page. After a login, then only the 1st laptop monitor screen will be used.
I've spend a lot of time trying different configurations (w/ and w/o wayland, xorg, lightdm vs gdm3) and I haven't been able to get a working dual-monitor environment.
[/LIST]

---

### Post by him610 on 2018-10-27
I am using (freshly installed) Xubuntu 18.04.1, and I can assure you that dual monitors, properly configured (Settings>Display) work as one would expect. Primary is connected HDMI>HDMI; secondary is connected DVI-I>Adapter>HDMI>HDMI. The displays can be configured to mirror or extend. 
```

xrandr
Screen 0: minimum 320 x 200, current 4480 x 1080, maximum 16384 x 16384
DVI-I-1 connected 1920x1080+2560+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1440x576      50.00  
   1024x768      75.03    70.07    60.00  
   1440x480      60.00    59.94  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    66.67    60.00    59.94  
   720x400       70.08  
DVI-D-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected primary 2560x1080+0+0 (normal left inverted right x axis y axis) 673mm x 284mm
   2560x1080     59.98*+
   1920x1080     60.00    50.00    59.94    30.00    29.97  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1080     59.98  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by JackD on 2018-10-28
Yep. "Properly configured" is not what we have. Here's the xrandr comparison between (1)  my post-upgrade laptop and (2) if I use the boot ISO USB drive on the same laptop. Please note that simply doing a re-install isn't going to fix anything, because that's how I got to my present state.

1. Post-Upgrade xrandr. Not a lot to show. And this is --verbose.
> Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
XWAYLAND0 connected 1600x900+0+0 (0x22) normal (normal left inverted right x axis y axis) 310mm x 170mm
	Identifier: 0x21
	Timestamp:  79713
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	non-desktop: 0 
		supported: 0, 1
  1600x900 (0x22) 118.250MHz -HSync +VSync *current +preferred
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock  55.99KHz
        v: height  900 start  903 end  908 total  934           clock  59.95Hz

Here is a (2) the xrandr on the same laptop, using the 18.10 Live Boot ISO USB drive (and I concated some of the output):
> ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 3520 x 1080, maximum 8192 x 8192
LVDS-1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1600x900      60.04*+  59.99    59.94    59.95    40.00    59.82  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1440x810      60.00    59.97  
//FURTHER RESOLUTION EXCISED//
 VGA-1 disconnected (normal left inverted right x axis y axis)
LVDS-1-2 disconnected (normal left inverted right x axis y axis)
DP-1-1 disconnected (normal left inverted right x axis y axis)
DP-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080     60.00*+  59.96    59.93  
   1680x1050     69.88    59.95    59.88  
   1600x1024     60.17  
   1400x1050     74.76    70.00    59.98  
   1600x900      59.95    59.82  
   1280x1024     75.02    60.02  
 //FURTHER RESOLUTION EXCISED//
VGA-1-2 disconnected (normal left inverted right x axis y axis)
  1600x900 (0x51) 118.250MHz -HSync +VSync
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock  55.99KHz
        v: height  900 start  903 end  908 total  934           clock  59.95Hz
  1600x900 (0x52) 97.500MHz +HSync -VSync
        h: width  1600 start 1648 end 1680 total 1760 skew    0 clock  55.40KHz
        v: height  900 start  903 end  908 total  926           clock  59.82Hz
//FURTHER RESOLUTION EXCISED//


---

### Post by JackD on 2018-10-29
And we have a winner.

I restored the default configuration:

> sudo apt-get purge nvidia-* sudo rm /etc/X11/xorg.conf
sudo apt-get install ubuntu-desktop
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo reboot

So *nice* to everything working correctly.

---

