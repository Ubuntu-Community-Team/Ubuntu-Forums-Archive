---
title: "xorg.conf missing"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by noxified on 2012-03-04
Hello everyone.I need to edit xorg.conf and it's missing!
i googled it up a bit,and i found X -configure (from the recovery root console)
it's says:
Fatal server error:
Could not create lock file in /tmp/.tX0 -lock
(not 100% sure that i copyed the destination very well)
How can i get xorg.conf to edit it?
```

fabbs@smurf:~$ lspci 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX 00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge) 00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01) 00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01) 00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) 00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge 00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge 00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller 00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge 01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10) 02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```
i use kernel 3.2.0-17-generic-pae
I need to edit xorg,to set the resolution right(1200x800).many thanks,and sorry for my english.

---

### Post by raja.genupula on 2012-03-04
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by noxified on 2012-03-04
yes i forgot to mention.i'm talking about xubuntu 12.04(same issue as 11.10)

---

### Post by MAFoElffen on 2012-03-04
```

sudo dexconf 

```
Writes a generic xconfig file as default to /etc/X11/Xorg.conf

---

### Post by noxified on 2012-03-05
```

root@smurf:/home/fabbs# sudo dexconf
sudo: dexconf: command not found

```
```

root@smurf:/home/fabbs# dexconf
No command 'dexconf' found, did you mean:
 Command 'debconf' from package 'debconf' (main)
dexconf: command not found
root@smurf:/home/fabbs# apt-get install dbconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dbconf

```
Not working..

---

### Post by MAFoElffen on 2012-03-05
> **noxified said:**
> ```

root@smurf:/home/fabbs# sudo dexconf
sudo: dexconf: command not found

``````

root@smurf:/home/fabbs# dexconf
No command 'dexconf' found, did you mean:
 Command '[COLOR=Green]debconf[/COLOR]' from package '[COLOR=Green]debconf[/COLOR]' (main)
dexconf: command not found
root@smurf:/home/fabbs# apt-get install [COLOR=Red]dbconf[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dbconf

```Not working..
mistyped / syntax error on your install.  What video do you have? 
```

lspci -vn | grep VGA

```And what are you trying to do? ATI and NVidia GPU's require an Xorg.conf file and drivers. Intel and Nouveau don't normally use an Xorg.conf file unless you are tryinf to tweak it on your own. Just asking to be able to assist you...

Also, if you have NVidia and have drivers installed already, it would be
```

sudo nvidia-xconfig

```

---

### Post by noxified on 2012-03-05
```

fabbs@smurf:~$ lspci -vn | grep VGA
01:00.0 0300: 1039:6351 (rev 10) (prog-if 00 [VGA controller])

```
```

fabbs@smurf:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```
I want to use an xorg.conf config to have a 1200x800 resolution.
to an older ubuntu distro(or another linux) i used to gedit /etc/X11/xorg.conf( if i do remember well the destination)
if you want i can post the xorg conf here...
dosn't matter here it is:
```

Section "Extensions"  Option "Composite"  EndSection  # **********************************************************************  # Refer to the xorg.conf man page for details about the format of  # this file.  # **********************************************************************   Section "ServerFlags"  #DontZap # disable <Ctrl><Alt><BS> (server abort)  AllowMouseOpenFail # allows the server to start up even if the mouse does not work  #DontZoom # disable <Ctrl><Alt><KP_+>/<KP_-> (resolution switching)  EndSection   Section "Module"  Load "dbe" # Double-Buffering Extension  Load "v4l" # Video for Linux  Load "extmod"  Load "type1"  Load "freetype"  Load "glx" # 3D layer  EndSection   Section "InputDevice"  Identifier "Keyboard1"  Driver "kbd"  Option "XkbModel" "pc105"  Option "XkbLayout" "pt"  Option "XkbOptions" "compose:rwin"  EndSection   Section "InputDevice"  Identifier "Mouse1"  Driver "mouse"  Option "Protocol" "ExplorerPS/2"  Option "Device" "/dev/mouse"  EndSection   Section "InputDevice"  Identifier "Mouse2"  Driver "evdev"  Option "bustype" "0x0003"  Option "product" "0xc521"  Option "relBits" "+0+1+2"  Option "HWheelRelativeAxisButtons" "7 6"  Option "vendor" "0x046d"  EndSection   Section "InputDevice"  Identifier "SynapticsMouse1"  Driver "synaptics"  Option "SHMConfig" "on"  EndSection   Section "Monitor"  Option "PreferredMode" "1280x768"  Identifier "monitor1"  VendorName "Generic"  ModelName "Flat Panel 1280x800"  HorizSync 31.5-90  VertRefresh 60   # TV fullscreen mode or DVD fullscreen output.  # 768x576 @ 79 Hz, 50 kHz hsync  ModeLine "768x576" 50.00 768 832 846 1000 576 590 595 630   # 768x576 @ 100 Hz, 61.6 kHz hsync  ModeLine "768x576" 63.07 768 800 960 1024 576 578 590 616   # modeline generated by gtf(1) [handled by XFdrake]  ModeLine "1280x800_120" 181.21 1280 1376 1520 1760 800 801 804 858 -HSync +Vsync   # modeline generated by gtf(1) [handled by XFdrake]  ModeLine "1280x800_100" 147.89 1280 1376 1512 1744 800 801 804 848 -HSync +Vsync   # modeline generated by gtf(1) [handled by XFdrake]  ModeLine "1280x800_85" 123.38 1280 1368 1504 1728 800 801 804 840 -HSync +Vsync   # modeline generated by gtf(1) [handled by XFdrake]  ModeLine "1280x800_75" 107.21 1280 1360 1496 1712 800 801 804 835 -HSync +Vsync   # modeline generated by gtf(1) [handled by XFdrake]  ModeLine "1280x800_60" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync   # modeline generated by gtf(1) [handled by XFdrake]  ModeLine "1280x800_50" 68.56 1280 1336 1472 1664 800 801 804 824 -HSync +Vsync  EndSection   Section "Device"  Identifier "device1"  BoardName "VESA driver (generic)"  Driver "vesa"  Option "DPMS"  EndSection   Section "Screen"  Identifier "screen1"  Device "device1"  Monitor "monitor1"  DefaultColorDepth 24   Subsection "Display"  Depth 8  Modes "1280x800"  EndSubsection   Subsection "Display"  Depth 15  Modes "1280x800"  EndSubsection   Subsection "Display"  Depth 16  Modes "1280x800"  EndSubsection   Subsection "Display"  Depth 24  Modes "1280x800"  EndSubsection  EndSection   Section "ServerLayout"  Identifier "layout1"  InputDevice "Keyboard1" "CoreKeyboard"  InputDevice "Mouse1" "CorePointer"  InputDevice "Mouse2" "SendCoreEvents"  InputDevice "SynapticsMouse1" "AlwaysCore"  Screen "screen1"  EndSection

```
as far as i know this is a vesa config..

---

### Post by MAFoElffen on 2012-03-06
> [FONT=monospace]
[FONT=Verdana]```


```[/FONT][/FONT]```
Section "Extensions"  
       Option "Composite"  
   EndSection  
  # **********************************************************************  
  #    Refer to the xorg.conf man page for details about the format of this file.  #
  # **********************************************************************   
EndSection

Section "ServerFlags"  
       #DontZap 
       # disable <Ctrl><Alt><BS> (server abort)  
       AllowMouseOpenFail 
       # allows the server to start up even if the mouse does not work  
       #DontZoom 
       # disable <Ctrl><Alt><KP_+>/<KP_-> (resolution switching)  
EndSection   

Section "Module"  
       Load "dbe" 
       # Double-Buffering Extension  
       Load "v4l" 
       # Video for Linux  
       Load "extmod"  
       Load "type1"  
       Load "freetype"  
       Load "glx" # 3D layer  
EndSection   

Section "InputDevice"  
        Identifier "Keyboard1"  Driver "kbd"  
       Option "XkbModel" "pc105"  
       Option "XkbLayout" "pt"  
       Option "XkbOptions" "compose:rwin"  
EndSection   

Section "InputDevice"  
       Identifier "Mouse1"  Driver "mouse"  
       Option "Protocol" "ExplorerPS/2"  
       Option "Device" "/dev/mouse"  
EndSection   

Section "InputDevice"  
       Identifier "Mouse2"  Driver "evdev"  
       Option "bustype" "0x0003"  
       Option "product" "0xc521"  
       Option "relBits" "+0+1+2"  
       Option "HWheelRelativeAxisButtons" "7 6"  
       Option "vendor" "0x046d"  
EndSection   

 Section "InputDevice"  
       Identifier "SynapticsMouse1"  
       Driver "synaptics"  
       Option "SHMConfig" "on"  
EndSection   

Section "Monitor"  
  Option "PreferredMode" "1280x768"  
       Identifier "monitor1"  
       VendorName "Generic"  
       ModelName "Flat Panel 1280x800"  
       HorizSync 31.5-90  
       VertRefresh 60   
       # TV fullscreen mode or DVD fullscreen output.  # 768x576 @ 79 Hz, 50 kHz hsync  
       ModeLine "768x576" 50.00 768 832 846 1000 576 590 595 630   # 768x576 @ 100 Hz, 61.6 kHz hsync  
       ModeLine "768x576" 63.07 768 800 960 1024 576 578 590 616   
       # modeline generated by gtf(1) [handled by XFdrake]  
       ModeLine "1280x800_120" 181.21 1280 1376 1520 1760 800 801 804 858 -HSync +Vsync 
       # modeline generated by gtf(1) [handled by XFdrake]  
  ModeLine "1280x800_100"  147.89 1280 1376 1512 1744 800 801 804 848 -HSync +Vsync   
       # modeline generated by gtf(1) [handled by XFdrake]  
       ModeLine "1280x800_85" 123.38 1280 1368 1504 1728 800 801 804 840 -HSync +Vsync   
       # modeline generated by gtf(1) [handled by XFdrake]  
       ModeLine "1280x800_75" 107.21 1280 1360 1496 1712 800 801 804 835 -HSync +Vsync   
       # modeline generated by gtf(1) [handled by XFdrake]  
       ModeLine "1280x800_60" 83.46 1280 1344 1480 1680 800 801 804 828 -HSync +Vsync   
       # modeline generated by gtf(1) [handled by XFdrake]  
       ModeLine "1280x800_50" 68.56 1280 1336 1472 1664 800 801 804 824 -HSync +Vsync  
EndSection   

Section "Device"  
       Identifier "device1"  
       BoardName "VESA driver (generic)"  
       Driver "vesa"  
       Option "DPMS"  
EndSection   

Section "Screen"  
         Identifier "screen1"  
         Device "device1"  
         Monitor "monitor1"  
       DefaultColorDepth 24   
       Subsection "Display"  
             Depth 8  
             Modes "1280x800"  
       EndSubsection   
       Subsection "Display"  
             Depth 15  
             Modes "1280x800"  
       EndSubsection   
       Subsection "Display"  
             Depth 16  
             Modes "1280x800"  
  EndSubsection   
  Subsection "Display"  
             Depth 24  
             Modes "1280x800"  
       EndSubsection  
EndSection   

Section "ServerLayout"  
         Identifier "layout1"  
         InputDevice "Keyboard1" "CoreKeyboard"  
         InputDevice "Mouse1" "CorePointer"  
         InputDevice "Mouse2" "SendCoreEvents"  
         InputDevice "SynapticsMouse1" "AlwaysCore"  
         Screen "screen1"  
EndSection

```That is old. Above (I reformated) uses drivers and xorg methods that don't exist anymore. For example on keyboards and mice, drivers now go through HAL to achieve plug-n-play devices. 

The modelines assume that the edid is broken in your display so use these, but in that file, if used today, because of changes in Xorg, if that is what you want to do, you have to tell it Option UseEDID "false"... So in the above, all those modeline declarations would be ignored.

So without seeing your /var/log/Xorg.0.log to see if your display does return valid data or the result back from hwinfo -- monitor, hwinfo --framebuffer and xrandr... to see if your video gpu displays that mode or that the display is capable to display a mode...

Here you go as a start:
```

# xconfig: X configuration file generated by MAFoElffen (custom)
# Revised As Of: 2012.3.5
# Not generated by XServer
# 

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "default"
    ModelName      "default"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    VendorName     "Silicon Integrated Systems"
    BoardName      "771/671"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Mode       "1200x800"
    EndSubSection
EndSection

```

---

### Post by Grenage on 2012-03-06
> **noxified said:**
> Hello everyone.I need to edit xorg.conf and it's missing!

While xorg.conf isn't required, have you tried using xrandr, before going the xorg route?

> **MAFoElffen said:**
> That is old. Above (I reformated) uses drivers and xorg methods that don't exist anymore. For example on keyboards and mice, drivers now go through HAL to achieve plug-n-play devices.

I thought that hal was deprecated, and that we're on udev?

---

### Post by noxified on 2012-03-06
yes,i tryed xandr,and no use.does not working...
in previous versions of ubuntu,that xorg config worked...so you are saying that there's ...no way,setting 1200x800 rez?

---

### Post by Grenage on 2012-03-06
I'm sure we can work something out, although I've had poor experience with SiS chipsets.  What model/make is your monitor?

---

### Post by noxified on 2012-03-06
it's a laptop.
fujitsu siemens v5515..

---

### Post by Grenage on 2012-03-06
Make sure you are happy with a text-only login, or have a livecd (Ubuntu CD will do) so that you can undo this if something goes wrong.

Create a new xorg.conf:

```
gksu gedit /etc/X11/xorg.conf
```

Paste the following config, save, and reboot.  If something goes wrong, you need only delete the file.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "fujitsu"
	ModelName "v5515"
	HorizSync 31.5-90
	VertRefresh 60 
EndSection

Section "Device"
	Identifier "Device0"
	Driver "sis"
	VendorName "mirage3"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x800"
	EndSubSection
EndSection
```

I've guessed the monitor ranges as best I can, and I think 'sis' is the correct driver name - if the chipset has current support.  If it still doesn't work, add a modeline, so that it looks like:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "fujitsu"
	ModelName "v5515"
	HorizSync 31.5-90
	VertRefresh 60
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "sis"
	VendorName "mirage3"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x800"
	EndSubSection
EndSection
```

---

### Post by noxified on 2012-03-06
thank you.but,the last version that readed xorg.conf directly was 10.10.after that,the support for xorg.conf was done.the ubuntu team tought that ,ubuntu repository is smart enough to find a driver all by itself,so it wont be needed to read xorg.conf.so it's not gonna read it ...

---

### Post by Grenage on 2012-03-06
It will read the xorg.conf if it exists, it's simply not required or there by default in current versions.

---

### Post by MAFoElffen on 2012-03-06
> **noxified said:**
> yes,[COLOR=Red]i tryed xandr[/COLOR],and no use.does not working...
in previous versions of ubuntu,that xorg config worked...so you are saying that there's ...no way,setting 1200x800 rez?
There is ways. Some of the syntax has just changed in xorg.conf(5) in the past 2 years.

Are you saying that you had to use that specific xorg.conf file on your hardware with older versions of Ubuntu?

Would be first to install hwinfo (very small utility)
```

sudo apt-get hwinfo

```Then post the results of 
```

sudo hwinfo --monitor
sudo hwinfo --framebuffer
xrandr -q

```And posting the file /var/log/Xorg.0.log

---

### Post by noxified on 2012-03-07
```

fabbs@smurf:~$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 2116: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
23: None 00.1: 10002 LCD Monitor                                
  [Created at monitor.95]
  Unique ID: jyhG.La7dBzYeYq2
  Hardware Class: monitor
  Model: "SAMSUNG LCD Monitor"
  Vendor: SEC "SAMSUNG"
  Device: eisa 0x4245 
  Resolution: 1280x800@60Hz
  Size: 331x207 mm
  Detailed Timings #0:
     Resolution: 1280x800
     Horizontal: 1280 1296 1344 1408 (+16 +64 +128) -hsync
       Vertical:  800  801  804  816 (+1 +4 +16) -vsync
    Frequencies: 68.94 MHz, 48.96 kHz, 60.00 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown


fabbs@smurf:~$ sudo hwinfo --framebuffer
> hal.1: read hal dataprocess 2147: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.eC0SacAaAQA
  Hardware Class: framebuffer
  Model: "Silicon Integrated 6330"
  Vendor: "Silicon Integrated Systems Corp."
  Device: "6330"
  SubVendor: "SiS"
  SubDevice: 
  Revision: "3.72.14A"
  Memory Size: 256 MB
  Memory Range: 0xc0000000-0xcfffffff (rw)
  Mode 0x031c: 1280x768 (+1280), 8 bits
  Mode 0x031d: 1280x768 (+2560), 16 bits
  Mode 0x031e: 1280x768 (+5120), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0304: 1024x768 (+128), 4 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x030d: 320x200 (+640), 15 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0327: 320x240 (+320), 8 bits
  Mode 0x0328: 400x300 (+400), 8 bits
  Mode 0x0329: 512x384 (+512), 8 bits
  Mode 0x032a: 320x240 (+640), 16 bits
  Mode 0x032b: 400x300 (+800), 16 bits
  Mode 0x032c: 512x384 (+1024), 16 bits
  Mode 0x032d: 320x200 (+320), 8 bits
  Mode 0x0331: 640x400 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0302: 800x600 (+100), 4 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

fabbs@smurf:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0 



```This is how i fixed:
[http://doc.ubuntu-fr.org/sis_771_671](http://doc.ubuntu-fr.org/sis_771_671)
AND BONUS.... 3D WORKS WITH XUBUNTU 12.04 AND SIS MIRAGE M 672

---

