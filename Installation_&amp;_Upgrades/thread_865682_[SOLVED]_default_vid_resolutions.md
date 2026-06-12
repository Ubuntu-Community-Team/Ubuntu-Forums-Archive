---
title: "[SOLVED] default vid resolutions?"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2008-07-20
This laptop is working great with Nvidia card, it was set up doing the manual install after all other attempts failed including envy.

I can set about 20 different resolutions but the pc defaults to 1920x1200 on every boot up and i have to manually set it to 1024x768 or other preferred setting.

I had read to do the following to adjust the settings but it failed. 



```
electric@XPS-Laptop:~$ sudo nvidia-settings
[sudo] password for electric: 

ERROR: Cannot open display 'XPS-Laptop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 22 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 23 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 24 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 25 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 26 of configuration
       file '/home/electric/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 27 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 28 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 29 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 30 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 31 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 32 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 33 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 34 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 35 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 36 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 37 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 38 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 39 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 40 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 41 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 42 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 43 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 44 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 45 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 46 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 47 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 48 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       49 of configuration file '/home/electric/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       50 of configuration file '/home/electric/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 51 of
       configuration file '/home/electric/.nvidia-settings-rc' (no Display
       connection).

electric@XPS-Laptop:~$ 
```


this is my xorg, and like I said the driver works very well, but i want to be able to tell it which default resolution to use on start up.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Thu Jun  5 00:10:21 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons"       "7"
    Option         "ZAxisMapping"  "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by upchucky on 2008-10-12
an automatic update solved the problem,soI do not have a clue as to what was wrong.

---

