---
title: "Xorg Problem"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by eyedol on 2006-03-27
I just did a fresh install of  Ubuntu Breezy Badger installation went on successfuly, not it boots up and my xorg never start but rather spits out error 

this is the error
```

Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbol found

Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbol found
Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform": No symbol found

Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:fbmmx.o": No symbol found
(EE) RADEON:[dri] DRIScreenInit failed. Disabling DRI.

  ***** If unresolved symbols were reported above, they might not 
  ***** be the reason for the server aborting.

Fatal server error:
Caught signal 4. Server aborting

Please consult the The X.Org Fundation support at http://wiki.X.Org for help

Please also check log file at "/var/log/Xorg.0.log" for additional information.

XIO: fata IO error 104 ( Connection reset by peer ) on X server ":0.0" 
xauth: error in locking authority file /home/james/.Xauthority 

```

that is what i get when i boot to console and then i startx 

My video Card is ATI Radeon Xpress 200M. Please what are the possible resolutions to this problem. A newbie needs help. :(

---

### Post by Xian on 2006-03-27
[QUOTE=eyedol]
xauth: error in locking authority file /home/james/.Xauthority 
[/QUOTE]

Try renaming or removing that file and try to start X again.

---

### Post by eyedol on 2006-03-27
i did what you said but still got that error. I found out that after starting x and it echoing the error it recreates the file .Xauthority even if i delete it. Is an empty file.

---

### Post by eyedol on 2006-03-27
googling around i managed to get it running with this xorg configuration

```

xorg.conf
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "ddc"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Input device"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        ndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
        Driver          "vesa"
        BusID           "PCI:1:5:0"
        VideoRam        200
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-121
        VertRefresh     48-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
         SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

#Section "DRI"
#       Mode    0666
#EndSection

```

Hope it helps somebody some day

---

### Post by lukemh on 2006-04-01
ok im a real newbie, but i really wanna get kubuntu working... i really want to learn linux and the best way to do it is to get it working and playing with it.

but i cant get any gui working i have installed kubuntu properly xserver or xorg or kde or whatever just doesnt load.. i can log into ubuntu with my username and password but if i type xserver it comes up with errors. i have attached the log files i think the errors are in.

this may not be the correct place to ask for help but this is the closest answer to my question cos i have compaq v2000 with a ati radeon 200m. 

i want to use the config file that eyedol posted but how do i use linux commands to replace the text of that file... especially cos right now im in windows xp (i have dual booting working) can i save the text file into a ext2 partition..

i know this is a big pain question but if someone can help... i will try and put back into the community when i get more experienced in ubuntu.

thanks in advance... luke.

ok it wont let my put the log file attached cos its too big

here is the link on my web server

[http://www.permelsing.com/Xorg.0.log1.renamed.txt](http://www.permelsing.com/Xorg.0.log1.renamed.txt)

---

