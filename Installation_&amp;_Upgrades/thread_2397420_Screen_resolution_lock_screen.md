---
title: "Screen resolution lock screen"
date: 2018-07-29
forum: Installation &amp; Upgrades
---

### Post by Ofloo on 2018-07-29
I've got 3 screen layout all of them aligned next to each other.

/etc/lightdm/lightdm.conf:
```
[SeatDefaults]
display-setup-script=/usr/share/lightdm/xrandr.sh
session-setup-script=/usr/share/lightdm/xrandr.sh

```
/usr/share/lightdm/xrandr.sh:
```
#!/bin/sh
/usr/bin/xrandr --output DVI-D-0 --auto --panning 1920x1080+3840+0 --output HDMI-0 --auto --panning 1920x1080+0+0 --output DVI-I-1 --auto --primary --panning 1920x1080+1920+0

```

After I've upgraded to 18.04 LTS from 16.04 LTS I ran into this issue where my screen resolution isn't working as it should when it's locked down. The login screen at boot is fine, the session is fine,.. however when the screen locks only 2 of the 3 screens have video the other one is active but black, they are in mirror mode and have a resolution of something like 640x480, not sure about the exact resolution, but that what it looks like.

Is there any way to fix this? Again this issue only arises when the computer went into lockscreen mode. (light-locker is installed.) After I login the screen resolution goes back to normal.

---

### Post by chui2ch on 2018-09-04
Did you have any luck fixing your resolution? I am on Xubuntu 18.04 and mine is doing the same thing. The login screen is correct, but when I lock the computer it is a low resolution.

---

### Post by chui2ch on 2018-09-04
Found a fix [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1757202](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1757202).

---

