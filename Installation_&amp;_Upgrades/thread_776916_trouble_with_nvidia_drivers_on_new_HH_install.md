---
title: "trouble with nvidia drivers on new HH install"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by gilim on 2008-05-01
hey,

I installed hardy heron on to a dual booted ide driver.  I previously had  gutsy and feisty working on this setup before.  The hardware is old, amd 1500ghz etc, with a 5700 nvidia graphics card.  I previously had compiz and other 3d graphics working.

I did a fresh reinstall for hardy, fixed a few of the problems, but I cant get my video drivers to work.  I have just bought a new 7300 nvidia card, but it didnt help.  I have read through the forums and tried every solution I can find in as many variations as I can think of.

things I have tried so far include:
using restricted drivers on a fresh install.
dpkg-reconfigure xserver-xorg
nvidia-xconfig
envy
editing xorg.conf for correct monitor specs.

I can get ok screen resolution if I only boot with 'nv' drivers but then I cant get compiz working.  If I use nvidia drivers I get locked in safe graphics mode at 640x480.

my current xorg.conf is:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1024x768@43"	"1152x864@75"	"1024x768@60"	"1280x1024@75"	"1024x768@70"	"1280x960@60"	"1024x768@75"	"1280x960@85"	"1024x768@85"	"1280x1024@85"	"832x624@75"	"1280x1024@60"	"800x600@60"	"1280x960@75"	"800x600@85"	"1400x1050@60"	"800x600@75"	"1400x1050@75"	"800x600@72"	"1600x1200@65"	"800x600@56"	"1600x1200@60"	"640x480@85"	"1600x1200@75"	"640x480@75"	"1600x1200@70"	"640x480@72"	"1792x1344@60"	"640x480@60"	"1856x1392@60"	"1920x1440@60"	"2048x1536@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"BenQ"
	Modelname	"BenQ P992"
	Horizsync	30.0-98.0
	Vertrefresh	50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

if anyone has any advice it would be good.
Please make it step by step, its been two days and im a psych student not a cs student.

thanks
-gilim

---

### Post by martrn on 2008-05-01
OK, I have come up with this. I think this works....

Back up your X11 file and remove all trace of your nvidia drivers....
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
sudo apt-get remove --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
```

Then visit this site and look at the nvidia manual.
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

Then download the nvidia drivers again from nvidia : [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")
Make sure you save it to /home/yourusername where your username is your user name that you use to log on.

Now we reconfigure your X11 file as looking at yours I have no idea weather yours it is shot or not....
```
sudo dpkg-reconfigure xserver-xorg
```
Make sure you only enter the configuration with respect to the monitor resolution you monitor can handle, one or two mode you know it is capable of displaying is fine, two low or too higher resolution and your in safe mode, or no mode at all....

Find out your kernel, you are using, download the kernel header files, build tools and disable.

```
uname -r
sudo apt-get update
sudo apt-get install build-essential gcc
sudo apt-get build-dep
sudo apt-get install linux-image-$(uname -r)
sudo apt-get install linux-headers-`uname -r`
sudo apt-get upgrade
```

Then try :-
```
kdesu kate /etc/default/linux-restricted-modules-common
kdesu kate /etc/X11/xorg.conf
```

with the first file remove any reference to
> Load    "dri"

with the second file find the line:

> DISABLED_MODULES=""

replace it with:

> DISABLED_MODULES="nv nvidia_new"

then change Section/Device/Driver
```
sudo /etc/init.d/gdm stop
```

Then run the shell script downloaded from nvidia
```
cd ~
cd /home/username
sudo sh NVIDIA*
```

*** NOTE ***** note that "....Could not get lock /var/lib/dpkg/loc..." means you didn't sudo it (run it as root) and that ..."....No such file or directory...."... means the file is not in the current directory or you didn't save the file to /home/username  so go back to downloading the nvidia drivers again..... Or just make sure you know the directory where you saved the nvidia shell script / drivers......

then
```
sudo /etc/init.d/gdm start
```
or 
```
sudo reboot
```


___________________________________________________________________
___________________________________________________________________

[**NOTE**] : This is not the recommended way to install nvidia drivers I found it works every time, but if you do get stuck in the shell type ```
sudo dpkg-reconfigure xserver-xorg
``` and set it to reconfigure X11 to use the nv driver, and you are back into graphical mode.  Envy does a very simular routine to this but you need to remove all traces of your nvidia driver before you run, envy.

---

### Post by gilim on 2008-05-01
hey martrn,

Thanks for your reply.

I followed your instructions and it didnt work.  I had several errors that might have caused it.  I will write them in the order they happened.

>>  sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings

This line didnt work.  The remove one that followed did.  The error was that uninstall is an invalid operation.

>>  sudo dpkg-reconfigure xserver-xorg

When I run dpkg-reconfigure I am not asked any questions about my video card or monitor.  I recall giving details in gutsy etc but not in Hardy.  My final xorg output after following the instructions is:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

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
    Option         "ZAxisMapping" "4 5"
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


I think thats the problem, but I cant work out why its not configuring for my specs.  I tried doing it manually previously and that didnt help either.

>>  uname -r
>>  sudo apt-get update
>>  sudo apt-get install build-essential gcc
>>  sudo apt-get build-dep
>>  sudo apt-get install linux-image-$(uname -r)
>>  sudo apt-get install linux-headers-`uname -r`
>>  sudo apt-get upgrade

The build-dep one came up with an error and the two installs after it came up wierd.  I tried them as printed and with 'uname -r' substituted for my uname-r output.  Which of these should I be trying?

>>  kdesu kate /etc/default/linux-restricted-modules-common
>>  kdesu kate /etc/X11/xorg.conf

command not found, I think this is just a text editor tho?  So I used sudo gedit.  There was no linux-restricted-modules-common file and the xorg.conf contained no references to 'diabled modules'.

Then tried to run the nvidia file with shell, that seemed to work, but didnt result in a working video driver.  The xorg was edited by that process to produce the one above.

Still not sure why this isnt happening....
What do you think?
Thanks in advance,
-gilim

---

### Post by martrn on 2008-05-01
If you can read the comments in this bit marked by a hash #
and change your /etc/X11/xorg.conf file temporarily to look like this.

```
kdesu gedit /etc/X11/xorg.conf
```

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
#    RgbPath         "/usr/X11R6/lib/X11/rgb"
#    Try commenting this bit out tempoary with a hash
EndSection

Section "Module"
#    Load           "dbe"
#    Load           "extmod"
#    Load           "type1"
#    Load           "freetype"
# and comment these out tempoarly 
    Load           "glx"
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
        Modes      "1280x960" "1024x768" "800x600" "640x480"
# add this line above here temporarily...
    EndSubSection
EndSection

```

and reboot ..... what do you get then ?????

---

### Post by gilim on 2008-05-01
Gave that a try, still in low graphics mode. 

Im freely willing to admit I might have missed something very basic in the normal setup, but I cant see what it would be.

I read somewhere that in hardy they are trying to streamline the xorg.conf...  Do you know anything about that?  Why arent I getting prompts in dpkg-reconfigure to enter my monitor or graphics card specs....

still trying
-gilim

---

### Post by martrn on 2008-05-01
> **gilim said:**
> hey martrn, Thanks for your reply.

err no probs.

> **gilim said:**
>  I followed your instructions and it didn't work.  I had several errors that might have caused it.  I will write them in the order they happened.

It appear to me they did work, more or less.  Error messages are good.

> **gilim said:**
> >>  sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings

This line didnt work.  The remove one that followed did.  The error was that uninstall is an invalid operation.

err thats good the remove is apptitute / remove.

> **gilim said:**
> 
>>  sudo dpkg-reconfigure xserver-xorg

When I run dpkg-reconfigure I am not asked any questions about my video card or monitor.  I recall giving details in gutsy etc but not in Hardy.  My final xorg output after following the instructions is:


I have my settings left from gusty.  I have no idea why on earth it would have changed.  But at long as it produces a valid X configuration file, it shouldn't matter.

> **gilim said:**
> 
I think thats the problem, but I cant work out why its not configuring for my specs.  I tried doing it manually previously and that didnt help either.


Manually add the modes your monitor is capable of displaying.

> **gilim said:**
> 
>>  uname -r
>>  sudo apt-get update
>>  sudo apt-get install build-essential gcc
>>  sudo apt-get build-dep
>>  sudo apt-get install linux-image-$(uname -r)
>>  sudo apt-get install linux-headers-`uname -r`
>>  sudo apt-get upgrade

The build-dep one came up with an error and the two installs after it came up wierd.  I tried them as printed and with 'uname -r' substituted for my uname-r output.  Which of these should I be trying?


ignore the build-dep, it should be build-deb, I think they are a part of build essestials anyway (or hope).  The `uname -r` are supposed to be back-ticks not qoutes.  You should have back-tick on your keyboard as well as qoutes but replaceing it `uname -r` with the output of uname -r should be one and the same thing.

> **gilim said:**
> 
>>  kdesu kate /etc/default/linux-restricted-modules-common
>>  kdesu kate /etc/X11/xorg.conf

command not found, I think this is just a text editor tho?  So I used sudo gedit.  There was no linux-restricted-modules-common file and the xorg.conf contained no references to 'diabled modules'.


yes sudo gedit / sudo nano / sudo your favorite text editor is all fine.
> **gilim said:**
> 
Then tried to run the nvidia file with shell, that seemed to work, but didnt result in a working video driver.  The xorg was edited by that process to produce the one above.

That is good that the nvidia file ran, it should have built a kernel module (driver) did you notice a green bar and a 100% when it built the kernel module, this is what we wanted it do, this is the important bit, and the rest is window dressing for it.

> **gilim said:**
> 
Still not sure why this isnt happening....
What do you think?
Thanks in advance,
-gilim

you should be able to sudo reboot and boot in graphically with your nvidia drivers I am supprised if you built the kernel module, that it didn't do that.  Edit your your /etc/X11/xorg.conf file to display some modes and you should be fine.

---

### Post by gilim on 2008-05-01
didnt work when I rebooted.
Tried reconfiguring my monitor but not my graphics card at the low grpahics mode screen.

Now I am in the start up error, in  low graphics mode, in 2048x1536 screen resolution.  I have reached this point before.  If I change to a reasonable screen resolution the display screws up.  Also when I try to start desktop effects in compiz, I get told the drivers arent loaded.

Not sure if this is closer to fixed or further away.
-gilim

---

### Post by martrn on 2008-05-01
> **gilim said:**
> didnt work when I rebooted.
Tried reconfiguring my monitor but not my graphics card at the low grpahics mode screen.

Now I am in the start up error, in  low graphics mode, in 2048x1536 screen resolution.  I have reached this point before.  If I change to a reasonable screen resolution the display screws up.  Also when I try to start desktop effects in compiz, I get told the drivers arent loaded.

Not sure if this is closer to fixed or further away.
-gilim

There are two stages of having X11 working properly.

Stage 1 would be configuring X11 to display a reasonable screen size.
Stage 2 would be configuring the kernel to use a kernel module.

Do *** NOT *** regardless of what anyone tells you to do reconfigure install any nvida drivers / kernel modules they appear to be working.

Your /X11/xorg.conf is the only thing that isn't

What does it look like at the moment ?
It should look like the one above,
or rather it should look like the one nvidia created,
with the exeption of the screen section should be modified to look like this....

```
 Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x960" "1024x768" "800x600" "640x480"
# add this line above here temporarily...
    EndSubSection 
```

You need to make sure that the modes, are reasonable for your system to display.

---

### Post by gilim on 2008-05-01
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:2:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"BenQ"
	Modelname	"BenQ P992"
	Horizsync	30.0-98.0
	Vertrefresh	50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2048	1536
		Modes		"1024x768@43"	"1152x864@75"	"1024x768@60"	"1280x1024@75"	"1024x768@70"	"1280x960@60"	"1024x768@75"	"1280x960@85"	"1024x768@85"	"1280x1024@85"	"832x624@75"	"1280x1024@60"	"800x600@60"	"1280x960@75"	"800x600@85"	"1400x1050@60"	"800x600@75"	"1400x1050@75"	"800x600@72"	"1600x1200@65"	"800x600@56"	"1600x1200@60"	"640x480@85"	"1600x1200@75"	"640x480@75"	"1600x1200@70"	"640x480@72"	"1792x1344@60"	"640x480@60"	"1856x1392@60"	"1920x1440@60"	"2048x1536@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by martrn on 2008-05-01
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
........ [..]  ....


It says to try 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

so try it .....

You need an xorg file simular to the one nvidia created, with the settings of your monitor, and what it is cabebel of displaying.

..This xorg.conf is garbage......

I am begining to dislike failsafe x

---

### Post by njparton on 2008-05-01
Install envy and us that to uninstall your current nvidia drivers, then use it to reinstall them along with auto configuring your x server.

---

### Post by gilim on 2008-05-01
ok its working

I dont know how tho.  So I hope it just keeps working.  I have the driver installed and compiz working.  

I connected a power cable to the video card, didnt know I had to...  Uninstalled everything and reinstalled everything again with envy and this time it worked.

Doesnt explain why my previous video card which doesnt need a cable stopped working when I installed Hardy.... But I dont mind so long as it Does work.

Thanks Martrn and njparton

my xorg.conf is : 

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

