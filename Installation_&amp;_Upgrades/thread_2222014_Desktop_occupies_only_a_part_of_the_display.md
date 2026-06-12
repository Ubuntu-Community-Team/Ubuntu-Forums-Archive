---
title: "Desktop occupies only a part of the display"
date: 2014-05-04
forum: Installation &amp; Upgrades
---

### Post by sumithar on 2014-05-04
I just installed lubuntu 14 on an old Dell Inspiron 1100 laptop with pentium 4 and 1GB RAM.  Installation seemed to go thru fine but when I boot into Lubuntu I find that the desktop occupies only about a quarter of the screen, the top left quadrant as it were.  Which pretty much renders it useless at this point!

Any ideas are welcome.

---

### Post by mörgæs on 2014-05-04
Please run ```
lspci -k | grep -A3 VGA
``` and post the results in CODE tags.

---

### Post by sumithar on 2014-05-04
```
Inspiron-1100:~$ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
	Subsystem: Dell Device 0149
	Kernel driver in use: i915
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
```

Is this what you wanted?  
Thanks

---

### Post by ibjsb4 on 2014-05-04
If I read that right, its good.  Could you post the output of:

```
xrandr
```

---

### Post by sumithar on 2014-05-04
```
Inspiron-1100:~$ xrandr
Screen 0: minimum 320 x 200, current 640 x 480, maximum 32767 x 32767
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

Hi,
Hope that tells you something!
Thanks!

---

### Post by Luke M on 2014-05-05
The problem is that linux thinks your screen is 640x480. You have to create an xorg.conf file with additional resolutions.

Suggest googling "Dell Inspiron 1100 xorg.conf" and see what you can find.

---

### Post by mörgæs on 2014-05-05
[http://superuser.com/questions/347131/xrandr-shows-two-displays-lvds1-but-how-can-i-use-vga1-only](http://superuser.com/questions/347131/xrandr-shows-two-displays-lvds1-but-how-can-i-use-vga1-only)

---

### Post by sumithar on 2014-05-06
Thank you mörgæs  and Luke M and ibjsb4.
I found some instructions to tweak grub to add modeset and tried that.  But apart from now displaying the same small sized desktop in the middle of my display (as opposed to the the top left quadrant) it didn't do anything.
I also followed the instructions on the superuser page but that gave me an error message.

At this time it's not worth my time to pursue this exercise any further.  I guess I'll just have to take that laptop to my local electronics recycling place :-(

Not that it matters, but I also tried to install Mint and Xubuntu.  The former just kept clocking and the latter complained with an illegal video mode, so Lubuntu was the only one that actually installed!  I wish the laptop had a DVD drive, my options would have increased a bit, I could have given my tried and trusted Fuduntu a go- I only have that on DVD.

---

### Post by mörgæs on 2014-05-06
It's a long shot, but you could try to add an xorg.conf as described in the link in my signature.

---

### Post by ibjsb4 on 2014-05-06
> **mörgæs said:**
> It's a long shot, but you could try to add an xorg.conf as described in the link in my signature.

Is Bodhi an option?

---

### Post by mörgæs on 2014-05-06
Asking me? Yes, it's worth a try, especially the 2.4 version.

---

### Post by sumithar on 2014-05-06
I created /etc/X11/xorg.conf as follows
```

Section "Device"
    Identifier "Intel Graphics"
    Driver "intel"
    Option "AccelMethod" "uxa"
EndSection
```

But it didn't make any difference.

---

### Post by sumithar on 2014-05-06
I was holding off on trying bodhi cos I read some reports about its being quirky.  

I can give it a shot.  The process looks rather roundabout, they assume that I am doing it from an existing Linux system and wants me to create a bootable USB drive and so on.  
I will see if I can just bung in the CD with the ISO image and see how far it takes me.

---

### Post by Luke M on 2014-05-07
Try this /etc/X11/xorg.conf:

```

Section "Monitor"
        Identifier "Internal monitor"
        Option "DPMS"
        HorizSync 28-80
        VertRefresh 43-60
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Internal monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 16
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth 24
                Modes "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "Default Screen"
EndSection

```

After rebooting see if you can select 1024x768 as a resolution.

---

### Post by sumithar on 2014-05-07
Hi Luke,
I tried your xorg.conf and rebooted but made no difference.
I don't see 1024x768 as an option when I got into preferences/Monitor. that command xrandr now shows a different result
```

Inspiron-1100:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0* 

```

---

### Post by Luke M on 2014-05-07
Ok, that didn't work. Sorry. Game for another? try editing /etc/default/grub,

GRUB_CMDLINE_LINUX="vga=792"

then run
sudo update-grub

(actually it would be easier to test by using the "e" option of grub, if you know how to do that. Hit "e" and add vga=792 to the end of the linux line...it won't be permenanently saved, but that's fine for testing)

---

### Post by sumithar on 2014-05-07
When  you are willing to take the time to provide me alternatives, it would be dreadfully churlish on my part to not try them out, wouldn't it?  Anyway, that last suggestion of yours did work and I have a lovely desktop that fills up the whole screen.  Thank you, danke, merci, gracias, dhanyavaad- you get the picture

---

