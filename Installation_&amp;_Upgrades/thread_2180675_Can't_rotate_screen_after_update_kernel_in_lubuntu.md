---
title: "Can't rotate screen after update kernel in lubuntu13.04?"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by wyatt2 on 2013-10-14
Dear all:
 
It can't rotate screen after update kernel(3.8.1 or 3.11).

it's working fine where first install lubuntu13.04. 
I can rotate from below command:
 A. xrandr --output CRT1 --rotate left
 B. xrandr -o 1

but when update kernel, it's fault. it's given error message:
[COLOR=#1F497D][FONT=Calibri] xrandr: Configure crtc 1 failed

the command xrandr -q message show below:

[/FONT][/COLOR]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1280
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1024x600       60.0  
   800x600        60.0  
   800x480        60.0  
   640x480        60.0  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     70.1     60.0* 
   1024x600       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   800x480        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  

I built kernel step as below:

1. make mrproper
2. make oldconfig
3. make
4. make modules_install
5. make install
6. update-initramfs -k 3.11.0 -c
7. update-grub
8. reboot

It's show right kernel version(uname -a) after reboot.


please help me?

Thanks!

---

### Post by wyatt2 on 2013-10-15
Who can help me???

---

### Post by wyatt2 on 2013-10-16
Up

---

