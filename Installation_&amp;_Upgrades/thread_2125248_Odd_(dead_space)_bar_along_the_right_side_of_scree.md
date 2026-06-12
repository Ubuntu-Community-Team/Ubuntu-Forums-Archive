---
title: "Odd (dead space) bar along the right side of screen after installation"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by sevykor on 2013-03-13
I installed Ubuntu 12.04LTS as dual boot with Windows 7 on a Sony Vaio all-in-one model VGC-JS410.  During installation, as well as now, there is a vertical bar to the right of the screen that is not part of the background, will not allow the cursor, different color (sometimes changes color after each boot).  How do I get rid of it?  I hope the attached photo sheds more light on the issue.  When  I do a print-screen, it doesn't acknowledge the dead space in teh picture.  Currently doing post-install updates. Thanks all!!!

---

### Post by TK999 on 2013-03-13
Hey, please run
```

xrandr -q

```
from a terminal & post the results here.

---

### Post by sevykor on 2013-03-13
Here are the results:
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
sony@sony-VGC-JS410F:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 8192 x 8192
VGA1 connected (normal left inverted right x axis y axis)
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
LVDS1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9

---

### Post by TK999 on 2013-03-13
First, run:
```

cvt 1680 1050

```
and copy its output to the clipboard. Then run
```

xrandr --newmode *paste the second line of the previous output here, omitting "ModeLine"*

```
Then run this command, where the mode's name is from the previous two outputs. It looks like "1680x1050_60.00":
```

xrandr --addmode LVDS1 *mode's name* *with quotation marks omitted*
xrandr --output LVDS1 --mode *mode's name* *with quotation marks omitted*

```
Examples: [https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions](https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions)

---

### Post by grahammechanical on 2013-03-13
> [COLOR=#000000]there is a vertical bar to the right of the screen that is not part of the background,[/COLOR]

I do not see anything to the RIGHT of the screen in your screen shot. I do see the Launcher on the LEFT of the screen. That is part of the Ubuntu Unity User Interface. It is not dead space, thank you very much. You may not like it. If so you can read this thread and may be it will help you to get the look that you do like.[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)


On my system I have set the Launcher to hide until I put the mouse on to the left side of the screen. Then it reveals and I can load an application. There is way to do this and to also set the top panel to be transparent so that you only see the notification  icons on the right. It give a nice clear look to the desktop that I like.

Regards.

---

### Post by papibe on 2013-03-13
Hi sevykor.

That smells like a corrupt EDID problem.

Could you please post the content of these files:
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the links to them.

Regards.

---

### Post by sevykor on 2013-03-13
> **TK999 said:**
> First, run:
```

cvt 1680 1050

```
and copy its output to the clipboard. Then run
```

xrandr --newmode *paste the second line of the previous output here, omitting "ModeLine"*

```
Then run this command, where the mode's name is from the previous two outputs. It looks like "1680x1050_60.00":
```

xrandr --addmode LVDS1 *mode's name* *with quotation marks omitted*
xrandr --output LVDS1 --mode *mode's name* *with quotation marks omitted*

```
Examples: [https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions](https://wiki.archlinux.org/index.php/Xrandr#Adding_undetected_resolutions)

This one didn't do it, It instead moved part of the screeen behind the dead zone (see photo).  BTW, the dead zone does not appear in teh screen shot.  Thank you for the effort.

---

### Post by sevykor on 2013-03-13
I do not have the first file, but I do have the second one (/var/log/Xorg.0.log).  Here is the link:

[http://paste.ubuntu.com/5611405/](http://paste.ubuntu.com/5611405/)

---

### Post by sevykor on 2013-03-13
Attached is how the screen looks now.  I took a photo (pay attention to the top right).   Part of the menu is now under the dead space after running the before mentioned commands.  Hope the photo helps..

---

### Post by sevykor on 2013-03-13
> **papibe said:**
> Hi sevykor.

That smells like a corrupt EDID problem.

Could you please post the content of these files:
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Paste them separately here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/), and post back the links to them.

Regards.


Under "/etc/X11/" I found the files as shown in the photo attached,

---

### Post by sevykor on 2013-03-13
I restarted the computer and it reverted back to the orginal configuration with the full top menu visible.  Attached photo...

---

### Post by papibe on 2013-03-13
```
[    30.043] (II) intel(0): Allocated new frame buffer **1600x1200** stride 6656, tiled
[    32.486] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   710.765] (II) intel(0): Allocated new frame buffer **1728x1200** stride 7168, tiled
```
I think your are trying to get a 1600x1200 resolution, isn't it?

Could you post the result of this command?
```
xvidtune -show
```
Regards.

---

### Post by TK999 on 2013-03-13
Hey papibe - I Googled for some info about the computer and Sony's official description ([https://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?productId=8198552921666002207&storeId=10151#specifications](https://store.sony.com/webapp/wcs/stores/servlet/ProductDisplay?productId=8198552921666002207&storeId=10151#specifications)) says the supported resolution is 1680 × 1050, so 1600 × 1200 might be an overshot here.

---

### Post by papibe on 2013-03-13
I see.

Let's try to get the EDID information:
```
sudo apt-get install read-edid
```
Then post the result of this command:
```
sudo get-edid | parse-edid
```
Regards.

---

### Post by sevykor on 2013-03-15
Thanks to everyone for the help, but I ended up using this computer for only Windows 7 rather than dual boot.

---

### Post by MAFoElffen on 2013-03-15
This is just what I see on this.
```

[COLOR=#000000][    28.610] (II) intel(0): Using fuzzy aspect match for initial modes
[/COLOR][COLOR=#000000][    28.610] (II) intel(0): Output VGA1 using initial mode 1024x768
[/COLOR][COLOR=#000000][    28.610] (II) intel(0): Output LVDS1 using initial mode 1024x768
[/COLOR]
```[COLOR=#000000]
[/COLOR]EDID seemed fine from "both" attached monitor devices in the xorg.0.log... but there was something there no-one saw. There is an intel GPU so it doesn't need an an Xorg.conf file by default to get xorg to use the intel driver. There is 2 monitors attached. There is no Xorg.conf file to tell it that the monitors are different- having different "aspect ratios" and the max res on one of the monitors is 1024x768.... so it is defaulting both displays to 1024x768. That mode in the widescreen typed aspect ratio on of the monitor pictured... set at 0,0 fills the screen as far as it can at that aspect ratio...  from the upper left corner 1024 right and 768 down... ending up with the blank portion to the right.

He seems to be gone now. If the OP kept at it... Hint- Separate screens at different resolutions and aspect ratios. Set the aspect rations in the monitor section. Map the monitors & resolutions directly to the ports in the screen section.

This same thing happens from time to time on ATI and nVidia GPU's, when mixing normal and "wide" aspect monitors. You can see from the native resolutions that one he pictured was that format. But he didn't take a picture nor mention that there was another attached. It just shows up in the log.

---

