---
title: "Screen resolution is wrong after fresh ubuntu 19.10 installation"
date: 2019-11-09
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2019-11-09
I have done a fresh ubuntu 19.10 installation, since that no screen resolution feet 
none of the resolution bellow feet my screen
xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 16384 x 16384
HDMI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050     59.95 +
   1280x1024     75.02    60.02* 
   1440x900      74.98    59.89  
   1280x960      60.00  
   1360x768      59.95  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.9
-----------------------------------------------------------------------------
then I checked on software update/Additional Drivers
it show no additional drivers available
-----------------------------------------------------------------------------
lsmod | grep nvidia
give zero hit
--------------------------------------------------------------------------
Then I install 
  sudo apt install nvidia-driver-435
still no drivers

---

### Post by yaminb on 2019-11-14
I'm having trouble with the monitor resolution and after the latest 19.10 update.
I'm haven't solved it, but I've tried a whole bunch of stuff.

[https://ubuntuforums.org/showthread.php?t=2431254](https://ubuntuforums.org/showthread.php?t=2431254)

Maybe see if any of that helps

---

