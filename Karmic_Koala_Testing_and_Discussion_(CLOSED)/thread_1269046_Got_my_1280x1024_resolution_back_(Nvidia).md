---
title: "Got my 1280x1024 resolution back (Nvidia)"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-09-17
I have a GeForce graphic card (Nvidia) and a SyncMaster Monitor. Karmic did not allow me to set higher resolutions. Reading through endless threats advocating downloading and installing special drivers and methods, I did not succeed.

Having to do a new install of Karmic, I tried my luck with just editing /etc/X11/xorg.conf before I fiddled with any drivers.

All I did, I replaced the Sections Monitor and Screen completely with the following.

```
Section "Monitor"
    Identifier     "Samsung SyncMaster 171s"
    Modelname      "Samsung SyncMaster 171s"
    HorizSync       30-81
    VertRefresh     56-76
    Option	   "DPMS"	
EndSection

Section "Screen"
    Identifier     "NV Monitor"
    Device         "Geforce2 MX400/200"
    Monitor        "Samsung SyncMaster 171s"
    DefaultDepth    16
   	 SubSection     "Display"
	        Viewport 0 0 
       	        Depth   16
       		Modes   "1280x1024" "1024x768" "800x600"
   	 EndSubSection
   
	 SubSection     "Display"
       		 Depth  24
       		 Modes  "1024x768" "800x600" "640x480"
   	 EndSubSection
EndSection
```

After restarting the computer, I have my higher resolution back and am happy with my achivement :).

Michael

---

### Post by forumache on 2009-09-18
Interesting. On the other hand, this is my complete xorg.conf.
I see that you use an old nvidia card. I think that you are forced to use nvidia-96 drivers (as nVidia does not support it in newer versions of the drivers)

```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "nvidia"
    Option      "NoLogo"    "True"
    Option      "DynamicTwinview"   "False"
    Option      "RandrRotation" "True"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen "Default Screen"
EndSection
```

---

### Post by Yumi on 2009-09-18
As I wrote, it is working. No need for me to consider old or new drivers.

Michael

---

