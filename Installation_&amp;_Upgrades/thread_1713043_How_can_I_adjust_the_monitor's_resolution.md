---
title: "How can I adjust the monitor's resolution?"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by imaefe on 2011-03-23
Hello,

I'm a new user at "ubuntu forums" and I have a problem with my graphics (exactly this one: [http://ubuntuforums.org/showthread.php?t=1639124&page=2](http://ubuntuforums.org/showthread.php?t=1639124&page=2)).

I've got an Intel 845G  chipset and a LG Flatron F900P monitor. A friend of mine  convinced me to try ubuntu and I installed the 10.10 version. Everything  (except the monitor's resolution) works all right. I don't know how to  fix it and so I thought realzippy could help me.

My computer is: IBM Net Vista 8305-21G
Chipset: FRU PN 49P1599    (Intel 845G)

Thank you very much in advance,

I apologize, I'm not very good at English.

---

### Post by imaefe on 2011-03-23
By the way, I've already tried with everything realzippy posted in the link.

---

### Post by realzippy on 2011-03-23
Here I am.
Hello and welcome to the forum!

*Everything (except the monitor's resolution) works all right. *

..to be honest in the moment I am to lazy to read that old thread,but
the problem (not solved) was that resolution was too high.
Is this also your problem?Usually it is too *low*...

---

### Post by realzippy on 2011-03-23
Let's start with xrandr.

what is the output from:
```
xrandr
```

Btw,I just read the thread.Only 2 pages..

Edit:
[This]("http://www.dealtime.com/LG-Flatron-F900P-19-in/prices") seems to be your monitor,correct?
Which resolution do you want to run?

---

### Post by imaefe on 2011-03-23
Yes that's my problem as well. My current resolution is 2048 x 1536, and the monitor appears as 'unknown'.
And yes, [this]("http://www.dealtime.com/LG-Flatron-F900P-19-in/prices") is my monitor.

For example, I'd like have a 1280 x 1024 resolution (which is supported as far as I know).

The output from ```
xrandr
``` is:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 2048 x 1536, current 2048 x 1536, maximum 2048 x 1536
default connected 2048x1536+0+0 0mm x 0mm
   2048x1536       0.0* 
```

---

### Post by realzippy on 2011-03-24
1.Write this down since you won't be able to paste (mind capital "X"):
sudo service gdm stop
sudo Xorg -configure
sudo service gdm start

2.Press Alt+Ctrl+F2
A shell opens,log in with username&password
Type:

```
sudo service gdm stop
```


```
sudo Xorg -configure
```

a file xorg.conf.new should get created in your user's home folder.

```
sudo service gdm start
```

should bring you back.Post the content of created file,can use gedit:


```
gedit ~/xorg.conf.new
```

---

### Post by imaefe on 2011-03-24
the content of "xorg.conf.new" is:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by realzippy on 2011-03-24
Ok,will reduce it and modify it to your needs,takes a few minutes.
Meanwhile:
Do you know how to start in recovery mode?
(If the xorg.conf we are going to test results to black screen at boot,
you have to delete the file from recovery mode..)

---

### Post by realzippy on 2011-03-24
When system boots press "shift"...you should get a few kernels to choose
and for every kernel a [recovery mode]("https://help.ubuntu.com/community/Grub2").
"*The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. ..bla*"

...when you got this,I 'll give you the 1rst version of the file to test.

---

### Post by imaefe on 2011-03-24
ok I got it now.

now you can give me the 1st version of the file to test

---

### Post by realzippy on 2011-03-24
run

```
gksudo gedit /etc/X11/xorg.conf
```

empty file opens (if not,stop here and post the output !)

paste in:

```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "extmod"
    Load  "record"
    Load  "dbe"
    Load  "dri"
    Load  "dri2"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync       30.0 - 111.0
    VertRefresh     50.0 - 200.0
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```

close file saving changes.
Reboot,fingers crossed.
..if problems boot in recovery mode,log in at shell,run

```
sudo rm /etc/X11/xorg.conf
```

```
sudo reboot

```

or start low graphics session or kind of (have not been there for a while..)
and delete the file with file browser (nautilus):
/etc/X11/xorg.conf
and restart.

---

### Post by imaefe on 2011-03-24
Hi realzippy!!

I can't believe but now everything's all right, even my screen resolution. Now my monitor is detected as "Goldstar Company Ltd 18" and my resolution is set at 1600 x 1200 (I have a wide range of resolutions available)

No I have to go but I'll tell how it is going

Thanks!!!

---

### Post by imaefe on 2011-03-26
Hello Realzippy!!

As I told you on Friday, it worked perfectly and I have not had any problem with my screen since then. I thought it was going to be pretty difficult to fix it. It's been very easy for me with your help, though.

I just wanted to tell you that I'm very grateful.

thank you!!!

---

### Post by realzippy on 2011-03-27
You are welcome..
One more thing:
Note that we set the values for your monitor in the xorg.conf file

HorizSync       30.0 - 111.0
VertRefresh     50.0 - 200.0

If you now would connect a different monitor,especially a TFT panel,
this will work,but you would get resolutions/refresh rates available the different panel could not handle or even damage it.So if you ever change the monitor,disable
(rename) the file or edit the proper H/Vsync values for the new monitor.

Have fun...

..and set thread as "solved" (threadtools)

---

