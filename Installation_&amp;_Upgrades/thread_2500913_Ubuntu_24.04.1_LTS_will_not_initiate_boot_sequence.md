---
title: "Ubuntu 24.04.1 LTS will not initiate boot sequence unless I connect the secondary mon"
date: 2024-09-15
forum: Installation &amp; Upgrades
---

### Post by neo1477 on 2024-09-15
[h=2]Hardware Information:[/h] 
[LIST]
[*]**Hardware Model:**                              Gigabyte Technology Co., Ltd. B550I AORUS PRO AX
[*]**Memory:**                                      16.0 GiB
[*]**Processor:**                                   AMD Ryzen™ 5 5600G with Radeon™ Graphics × 12
[*]**Graphics:**                                    AMD Radeon™ Graphics
[*]**Disk Capacity:**                               5.0 TB
[/LIST]
 [h=2]Software Information:[/h] 
[LIST]
[*]**Firmware Version:**                            F20c
[*]**OS Name:**                                     Ubuntu 24.04.1 LTS
[*]**OS Build:**                                    (null)
[*]**OS Type:**                                     64-bit
[*]**GNOME Version:**                               46
[*]**Windowing System:**                            Wayland
[*]**Kernel Version:**                              Linux 6.8.0-44-generic
[/LIST]
 neo1@neo1pvtcld:~$ xrandr Screen 0: minimum 16 x 16, current 4640 x 2160, maximum 32767 x 32767 HDMI-1 connected primary 800x1280+0+0 (normal left inverted right x axis y axis) 170mm x 100mm 800x1280      59.93*+ 800x600       59.86
640x480       59.38
320x240       59.52
800x500       59.50
768x480       59.90
720x480       59.71
640x400       59.20
320x200       58.96
720x400       59.55
640x350       59.77
HDMI-2 connected 3840x2160+800+0 (normal left inverted right x axis y axis) 630mm x 360mm 3840x2160     59.98*+ 2048x1536     59.95
1920x1440     59.97
1600x1200     59.87
1440x1080     59.99
1400x1050     59.98
1280x1024     59.89
1280x960      59.94
1152x864      59.96
1024x768      59.92
800x600       59.86
640x480       59.38
320x240       59.52
2560x1600     59.99
1920x1200     59.88
1680x1050     59.95
1440x900      59.89
1280x800      59.81
1152x720      59.97
960x600       59.63
928x580       59.88
800x500       59.50
768x480       59.90
720x480       59.71
640x400       59.95
320x200       58.96
3200x1800     59.96
2880x1620     59.96
2560x1440     59.96
2048x1152     59.90
1920x1080     59.96
1600x900      59.95
1368x768      59.88
1280x720      59.86
1024x576      59.90
864x486       59.92
720x400       59.55
640x350       59.77
 Primary display : Shenzhen Soogeen Electronics Ltd. 8" Secondary display : Viewsonic Corporation 29"
 [Display][1] [Primary][2] [Secondary][3] [1]: [https://i.sstatic.net/pzl52Lkf.png](https://i.sstatic.net/pzl52Lkf.png) [2]: [https://i.sstatic.net/jLH6dGFd.png](https://i.sstatic.net/jLH6dGFd.png) [3]: [https://i.sstatic.net/2cAHtKM6.png](https://i.sstatic.net/2cAHtKM6.png)
 The issue is that unless I don't connect the Secondary display, Ubuntu will not start the boot sequence.
 I've tried multiple things but none seem to work.

---

