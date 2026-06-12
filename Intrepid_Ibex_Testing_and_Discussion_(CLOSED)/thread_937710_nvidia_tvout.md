---
title: "nvidia tvout"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Odisej on 2008-10-04
Ok, I hope this isn't being discussed in some other thread but if it is I wasn't able to find it. 

Here is my problem. Installed 8.10 to see how things are coming along and it seems they are progressing just nicely. But I did encounter one problem which may prove quite annoying to new users.

Until now TV-OUT worked nicely as long as one would use nvidia drivers and use nvidia-settings to set things up. Well, it seems xorg 7.4 does not allow this. I tried to find some answers on the net but so far was unable too. If I understand it correctly xorg.conf has a different role now making it impossible to set tv-out the way it used to be.

Nvidia-settings does not work as it is unable to save xorg.conf with the new settings to use. 

Am I doing something wrong or is it rally impossible to currently set tv-out with nvidia drivers? I am using nvidia 6600 if this is at all important.

If I am right this may prove troublesome to some new users who would try Ubuntu. I find it rather problematic that development sometimes goes a step back instead of forward making some things harder to use in newer versions. 

I hope I am wrong about this but would be glad if somebody would be able to help with this.

Regards,

Odisej

---

### Post by roberthr on 2008-10-04
I also have problems. Screen resolution utility is completely useless. Nvidia-settings also. So I managed to fix this with adding following lines to xorg.conf:
```

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        Screen          0
        Busid           "PCI:2:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "NoLogo"        "True"
        Option          "UseDisplayDevice"      "Monitor[0]"
EndSection

Section "Device"
        Identifier      "Device[1]"
        Driver          "nvidia"
        Screen          1
        BusID           "PCI:2:0:0"
        Option          "UseDisplayDevice"      "Monitor[1]"
EndSection

Section "Monitor"
        Identifier      "Monitor[0]"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Monitor[1]"
EndSection

Section "Screen"
        Identifier      "Screen[0]"
        Device          "Device[0]"
        Monitor         "Monitor[0]"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1680x1050"     "1280x1024"     "1280x960"      "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen[1]"
        Device          "Device[1]"
        Monitor         "Monitor[1]"
        DefaultDepth    24
        Option "ConnectedMonitor" "TV"
        Option "TVOutFormat" "Component"
        Option "TVStandard" "HD720p"
        Option "MetaModes" "1280x720"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Screen[0]"
        Screen 1        "Screen[1]" Above "Screen[0]"
EndSection

```

I have nVidia 8400GS with LCD monitor on DVI head nad LCD TV on VGA-Composite RGB head.

---

### Post by Odisej on 2008-10-04
I came up with a sort of solution by using my TV in xinerama (extended desktop) mode. I managed to do it by manually copying settings from nvidia-settings' xorg.conf version and disabling some options in the default file. I think your settings might just work as well although i've tried something similar but always encountered an error. I didn't try to find the reason but it might have been an option misspelled or something similar. 

I will wait for a final release and try some things after that.

Here is a copy of my working xorg.conf. Note that I am using a CRT connected with an s-video cable.

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

# Section "Screen"
#	Identifier	"Default Screen"
#	Monitor		"Configured Monitor"
#	Device		"Configured Video Device"
#	DefaultDepth	24
# EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

# Section "Device"
#	Identifier	"Configured Video Device"
#	Driver	"nvidia"
#	Option	"NoLogo"	"True"
# EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: 800x600 +1280+0"
    SubSection     "Display"
        Depth       24
	Option  "TVOutFormat" "SVIDEO"
	Option "TVStandard" "HD480i"
    EndSubSection
EndSection
```

---

