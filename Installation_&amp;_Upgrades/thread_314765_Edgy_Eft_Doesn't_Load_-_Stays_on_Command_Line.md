---
title: "Edgy Eft Doesn't Load - Stays on Command Line"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by RyanPower on 2006-12-08
I did a clean netboot install of Edgy Eft on the rest of my hard drive the other day. And it installed successfully, as far as I can tell; I can select it from the GRUB BootLoader menu and it starts initialising.

Though isn't of the Ubuntu logo popping up and loading, it just stops on a black screen with a flashing underscore following this:

<myusername>@ubuntu: $

(Or something along those lines.)
I don't know whether this is suppose to happen, I've only ever installed Badger on this computer, I don't know if Eft is any different.

Thanks!

---

### Post by endersshadow on 2006-12-08
Log into that blinking cursor and then try this:

```
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by RyanPower on 2006-12-08
I type in the first line and it starts installing the required packages.

But after it finishes, it just returns to the command line. Then when I type in the second line you gave me, I get this:

```
Command /etc/init.d/gdm not found
```

(Or something like that.)

---

### Post by endersshadow on 2006-12-08
Oh...that would explain a lot.  Try this at the command line:

```
sudo apt-get install gdm
sudo /etc/init.d/gdm restart
```

It will install GDM and then the second command should get you up and running!

---

### Post by RyanPower on 2006-12-08
Ah, it installs fine and I restarted it, but I get a new screen with this message:

```
Failed to start the X server
```

etc etc. Then when I view the diagnosis this is the message I get:

```
X: cannot stat /etc/X11/X (no such file or directory), aborting
```

---

### Post by endersshadow on 2006-12-08
Okay, you don't have X installed...I would've thought that would've been a depdency, but I guess not.  Try this:

```
sudo apt-get install xserver-xorg
```

If it doesn't take you through a process to configure your monitor:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

To start 'er up:

```
sudo /etc/init.d/gdm restart
```

Good luck!

---

### Post by RyanPower on 2006-12-09
After the screen flashes for a bit, the X Server comes up but I still get an error. The diagonsis this time is

```
...

(EE) No devices detected.

Fatal server error:

No screen found
```

Also, if I have an Intel(r) 82815 Graphics Controller for a graphic device, what chipset type should I be putting into the X Server configuring. (Windows helps me find that the Chip Type is "Intel(R) 82815")

---

### Post by endersshadow on 2006-12-09
Well that's interesting.  I know that you're obviously not using Ubuntu to post this, but would there be any way for you to post the contents of your /etc/X11/xorg.conf file (you can get it by doing "less /etc/X11/xorg.conf" in the command line).

---

### Post by RyanPower on 2006-12-09
To save me some writing, I tried to copy down the relevant information.

```
...

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "chips"
    BusID         "PCI:0:2:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HoriSync      28-51
    VertRefresh   43-60
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor       "Generic Monitor"
    DefaultDepth  24
    SubSection    "Display"
        Depth        1
    [...] (Then follows a lot repitive things about screen resolutions.)

Section "Server Layout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    Input Device  "Generic Keyboard"
    Input Device  "Configured Mouse"
    Input Device  "stylus"    "SendCoreEvent"
    Input Device  "cursor"    "SendCoreEvent"
    Input Device  "eraser"    "SendCoreEvent"
    Input Device  "Synaptics Touchpad"
SectionEnd

Section "DRI"
    Mode    0666
EndSection
```

---

### Post by endersshadow on 2006-12-09
Try changing your Video Card "Device" section to this:

```
Section "Device"
        Identifier      "Intel i810"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection
```

Also, in the "Screen" section, change Device from "Generic Video Card" to "Intel i810".

You'll need to edit it by using this command:
```
sudo nano /etc/X11/xorg.conf
```

Then do the sudo /etc/init.d/gdm restart that has by now become habitual.

---

### Post by RyanPower on 2006-12-09
Okay I edited like you said, but now the X Server gives a longer diagnosis.

I've tried to shorten it as much as possible without omitting vital information, for example the first error has a lot more information, just ask if you need it and I'll go fetch it.

```
(EE) AIGLX: Screen 0 is not DRI capable

(EE) xf86OpenSerial: Cannot open device /dev/wacom
      No such file or directory

(which is then repeated 5 times)

Synaptics DeviceInit called              nt
SynapticsCtrl called.
Synaptics DeviceOn called

Could not init font path element...

(which is repeated for all the font directories shown in xorg.conf)

Fatal server error:
    could not open default font 'fixed'
```

---

### Post by endersshadow on 2006-12-09
Hmm...ubuntu-desktop should have installed those.

My only advice at this point would to be to install the full graphical version of Ubuntu from the get go by using the LiveCD or the Alternate Install CD, and not the server install.  Unless a more experienced/knowledgable person comes around, that's the best I can give you...sorry :-|

---

### Post by RyanPower on 2006-12-10
Interesting, after that I then tried for the helluva it again:

```
sudo apt-get install ubuntu-desktop
```

Then the gdm restart thing and it works! I am posting this inside Edgy! Thank you so much for helping me endershadow!

---

