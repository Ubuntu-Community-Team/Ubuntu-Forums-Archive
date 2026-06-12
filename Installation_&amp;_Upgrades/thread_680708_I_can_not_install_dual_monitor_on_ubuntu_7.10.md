---
title: "I can not install dual monitor on ubuntu 7.10"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by rtsask on 2008-01-28
Hi , I have ATI video card and installes ubuntu 7.10 but computer doesn't recognize dual monitor , I did dpkg-reconfigure xserver-xorg and no success can anyone help me out please , it is very urgent.

---

### Post by neilbuntu on 2008-01-29
Go to the command line and type this in:

xrandr

You will see some output that looks like this:

```
Screen 0: minimum 320 x 200, current 1280 x 768, maximum 1280 x 1280
VGA connected 1280x1024+0+0
LVDS connected 1280x768+0+0 (normal left inverted right) 305mm x 183mm
   1280x768       60.0*+   60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)
```

Then try this command:

xrandr --output LVDS --auto
xrandr --output VGA --right-of-LVDS

Just read up more on **xrandr** and you'll see how easy it is.  There's no crazy xorg.conf stuff, other than adding the following line in the Display SubSection of the Screen Section: 

```
Virtual 2560 1024
```

That creates a larger possible screen resolution for both screens combined (2560 in my case because I have two 1280 wide monitors, but may be different for you).

---

### Post by Horza on 2008-01-29
If the above method fails, as it did for me, with the complaint:

  xrandr: screen cannot be larger than 1600x1200 (desired size 2304x768)
 
(too bad, xrandr seems very nice), a possible next step would be to read up on the basics of the xorg.conf file [here]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html") (there's also a rundown somewhere in the ubuntu docs, but I can't remember where), then look at **[ Ziox's dual monitor howto ]("http://ubuntuforums.com/showthread.php?t=221174") ** and work through the methods till you find one that works for you (the one that worked for me (Radeon 9600 PRO) was xinerama with flgrx (proprietary) drivers).

Finally, don't use the GUI "Screens and Graphics", because it seems to be quite buggy, and will mess up your xorg.conf file (in /etc/X11) where the graphics config info is stored.

---

