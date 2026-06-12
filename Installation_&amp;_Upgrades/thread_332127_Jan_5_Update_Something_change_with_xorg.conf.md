---
title: "Jan 5 Update: Something change with xorg.conf?"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by SFDD on 2007-01-05
I just performed the few updates that came down the pipe this morning. It required a restart, which I did. But now I don't see the higher display resolutions I had before.

So I looked into my  xorg.conf file, but it looks no different. The higher resolutions are listed in there, but they no longer appear in the Screen Resolution Preferences dialog.

Has something changed with regard to the xorg.conf file?

I have an nVidia TI 4600 card. Here are the relevant sections from my xorg file:

```
Section "Device"
    Identifier     "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV25 [GeForce4 Ti 4600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1400×1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1400×1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1400×1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1400×1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1400×1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1400×1050" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Thanks for any help!

---

### Post by taurus on 2007-01-05
Did you happen to upgrade your kernel?

---

### Post by SFDD on 2007-01-05
Actually, no. The updates included one to Thunderbird and another two to some messaging service that I should have paid closer attention to the name of. ;)

---

### Post by taurus on 2007-01-05
Try to install nVidia driver over again (you probably have to remove the current one first though)...

---

### Post by SFDD on 2007-01-05
Well, I tried that, but I get the same result. I also tried executing:

```
whereis xorg.conf
```

which returns:

```
xorg: /usr/lib/xorg
```

But an ls of that directory shows only a directory called ```
modules
```.

I think it's odd that after a removal and reinstall of my nVidia driver that I would see the same xorg.conf file I had in there before. No?

It makes me wonder whether the system is looking for xorg.conf in some new location.

---

### Post by taurus on 2007-01-05
You did

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

---

### Post by SFDD on 2007-01-05
I actually did the removal/reinstall via Automatix. But I just tried the way you suggsted too and I see no difference. 

Is there a way to see for certain where the X Server is finding its xorg.conf file?

(Thanks for all your help, by the way!)

---

### Post by taurus on 2007-01-05
As far as I know, it is looking in /etc/X11 for xorg.conf!!!  What happens if you edit /etc/X11/xorg.conf and change the **Driver** from "nvidia" to "nv" and see if you can get X running!

Applications -> Accessories -> Terminal
```
sudo nano -w /etc/X11/xorg.conf
```
<Ctrl>x to save and exit (with a yes and a return)...

---

### Post by SFDD on 2007-01-05
Okay, I've done that and it did boot me into the NV driver. Or, at least I think it did. The nVidia configuration control panel no longer shows any options, so I'm guessing this means the driver isn't loaded.

I still see only those three resolution options though:

1024 x 768
800 x 600
640 x 480

So I guess this means I am edited the correct file, but for whatever reason it's no longer acknowledging the higher resolutions. :(

---

### Post by taurus on 2007-01-05
Now that you have X working again, why don't you use this guide to install nvidia for your graphic card then!!!

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by SFDD on 2007-01-05
X was never not working for me. I was just unable  to get the higher resolutions I had right before an update that seemed to have nothing whatsoever to do with my video card.

To be honest, I hesitate to start down the road of someone else's installation advice because I've gotten burned on that before with Ubuntu. I have no doubts about Alberto's expertise in this area. His "envy" script was a saving grace for me with Dapper in getting an nVidia driver installed on my other computer. But this (Edgy) driver was not installed by his script and I'm quite frankly afraid to start installing one method on top of another. It reminds me of the Broadcom wireless fiasco where I was installing and removing drivers, blacklisting things, unblacklisting things, and before I knew it I had to reinstall Ubuntu because the "experts" told me I was stupid for trying so many things, which of course i tried only because nothing was working.

Anyway, thanks for the help. Perhaps some future update will magically "fix" what this update today magically broke.

---

### Post by bulldog on 2007-01-05
If you install nvidia drivers for the second or even the third time,it will remove the 'old' drivers first,so no harm done.
You can use automatix instead if you prefer.

---

