---
title: "[SOLVED] Gutsy upgrade kills Nvidai"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by pt123 on 2007-10-19
After installing it asked me to reboot and as usual xserver had problems(on upgrades) but this time it fell back to the graphical failsafe xserver loaded but when choosing the monitors there were no defaults Chimei(CMV) which is absurd, considering they are one of the biggest sellers in the Asia Pacific region. So I chose 1680x1050 LCD but it had problems and was only able to give me 800x600 screen.
It couldn't even pick up my Leadtek Nvidia 6600GT card, and chose VESA drivers, than the nv.

After installing it and enabling the restricted drivers I was able to set 1680x1050 resolution. But then I couldn't enable the Visual effects, it would always fallback to none.
What is the command to get the visual effects applet so I can see the error message.

These restricted drivers have always been hopeless for me, and I have relied on the drivers from the Nvidia site. The ones from Nvidia can also pick up the monitor correctly.

This is so frustrating, now I can't install the drivers from the nvidia,
Using this method which I had used many times before
```

sudo nano /etc/default/linux-restricted-modules-common
Make the last line look like
DISABLED_MODULES="nv"


sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx  nvidia-glx-new nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start


```
Is there an updated version of this script for Gutsy 

After installing it boots up in this failsafe crap.

Oh hopefully my backup of Feisty isn't screwed like this release.

The xorg.conf file is littered with this failsafe settings.

---

### Post by Argus on 2007-10-19
Try ENVY [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . I haven't tried it yet with 7.10 but it has always worked flawlessly for me. I'm mid install and had to come to work.

Sean

---

### Post by pt123 on 2007-10-19
envy hasn't worked for me in 6.10 & 7.04.

The drivers from nvidia worked like a treat. 

Now this annoying failsafe won't even let me chose nv, its defaulting to god damn VESA.

Is there anyway to turnoff or purge this failsafe nonsense & ubuntu res. &  driver utility?

---

### Post by Envirotech on 2007-10-19
I have had the same problems as you. Every time i enable the restricted driver and reboot I end up at the safe boot prompt.  I choose my monitor (plug n play (it has the proper vertical and horizontal sync settings)) and chose the propitary Nvidia driver 7600gs it boots but nvidia-settings shows no nvidia driver.  When I look at my xorg.conf it is full of failsafe info.  I have a backup of my original xorg.conf from before the update and paste that into the new xorg.conf and reboot I still end up at the bulletproof X menu.  Any help would be appreciated. :(

I upgraded from 7.04 to 7.10 using the Alternative CD from within 7.04

system
3800+ 64bit dual core
Nvidia 7600gs
dual booting Ubuntu and XP Pro

---

### Post by m2006h on 2007-10-19
try this:

Modify /etc/default/linux-restricted-modules-common to skip unnecessary kernel modules. 

DISABLED_MODULES="nvidia nvidia_legacy"

---

### Post by pt123 on 2007-10-19
> **m2006h said:**
> try this:

Modify /etc/default/linux-restricted-modules-common to skip unnecessary kernel modules. 

DISABLED_MODULES="nvidia nvidia_legacy"

Thanks this now lets me choose NV as the graphics driver, and I am able use 1680x1050 resolution. 

Then I when I chose to use the restricted drivers everything boots up fine & evens says that its using nvidia in  "Screen & Resolution Applet" but the desktop Visual effects fails as how I mentioned above.

Is there a way to get a terminal output as to why it is failing?


Also another question how is it able to use nvidia restricted drivers when it has been listed in the disabled modules. DISABLED_MODULES="nvidia nvidia_legacy

---

### Post by pt123 on 2007-10-19
I dont have the option of "System > Preferences > GL Desktop"

In the new xorg.conf file all it has is this for device, module & screen
```

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection


```

When I was on Feisty running Compiz perfectly using the drivers from the nvidia site,  device, module  & screen looked like this:
```

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1680x1050_60 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    #Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    #Option         "DisableGLXRootClipping" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Do we need to manually add Option         "AddARGBGLXVisuals" "True"

---

### Post by pt123 on 2007-10-19
when I tried running CompizFusion like inFeisty using this script 
```


#!/bin/sh

# click to start, click to stop

if pidof compiz.real | grep [0-9] > /dev/null
then
 exec metacity --replace
else
 exec compiz --replace -c emerald
fi


```

I am getting this error output in the terminal
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f1 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: Unknown option '-c'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'emerald'
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz: line 378:  6189 Segmentation fault      (core dumped) ${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS
metacity: Unknown option -c


```

Why is it saying **Checking for Xgl: not present. **

Is there another hack to get it make it present.

---

### Post by m2006h on 2007-10-19
> **pt123 said:**
> Thanks this now lets me choose NV as the graphics driver, and I am able use 1680x1050 resolution. 

Then I when I chose to use the restricted drivers everything boots up fine & evens says that its using nvidia in  "Screen & Resolution Applet" but the desktop Visual effects fails as how I mentioned above.

Is there a way to get a terminal output as to why it is failing?


Also another question how is it able to use nvidia restricted drivers when it has been listed in the disabled modules. DISABLED_MODULES="nvidia nvidia_legacy

There are some new designations for nvidia drivers with this release including nvidia_new and nvidia-glx-new. I think you probably also have the nvidia_new driver installed, which is being used. There is a support thread about this issue here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107646](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/107646)

One other thing I did was to delete the hidden nvidia file in the /lib/linux-restricted-modules directory. Go there, ls -la and see if there is a .nvidia_new_installed file.  If so, delete it (or rename it to .hidden or something. This is described here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217) . I had this file even through the upgrade to Gutsy and using the 2.6.22 kernel.

I've got the same Geforce 6600 card and it will work. My xorg.conf has the same Section "Module"  and Section Device" as you (except for the compiz stuff you'll soon have. And mine had Option "AddARGBGLXVisuals" "True" uncommented.)

Did you enable the nvidia in System/Restricted Drivers ?

---

### Post by pt123 on 2007-10-19
> **m2006h said:**
> T
One other thing I did was to delete the hidden nvidia file in the /lib/linux-restricted-modules directory. Go there, ls -la and see if there is a .nvidia_new_installed file.  If so, delete it (or rename it to .hidden or something. This is described here: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217) . I had this file even through the upgrade to Gutsy and using the 2.6.22 kernel.

I've got the same Geforce 6600 card and it will work. My xorg.conf has the same Section "Module"  and Section Device" as you (except for the compiz stuff you'll soon have

Did you enable the nvidia in System/Restricted Drivers ?
The file was there I renamed it and rebooted. Still Visual effects fails like previously.
Do I have to reinstall the restricted drivers?

> 
. And mine had Option "AddARGBGLXVisuals" "True" uncommented.)

In which section was this?

> Did you enable the nvidia in System/Restricted Drivers 
Yep

Thanks for your help

---

### Post by pt123 on 2007-10-19
I now uninstalled the restricted modules and re-installed it and it dropped that file .nvidia_new_installed file in the directory again. 

Still no luck with the Visual effects.

Do I need to remove this
DISABLED_MODULES="nvidia nvidia_legacy"
---

Even I enable the restricted drivers its still choosing the new:
```

Selecting previously deselected package nvidia-glx-new.
(Reading database ... 131199 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb) ...
Setting up nvidia-glx-new (100.14.19+2.6.22.4-14.9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

And it is also dropping the 
.nvidia_new_installed in that directory

---

### Post by m2006h on 2007-10-19
I think I would start from a known state.

Go to Screens and Graphics and change the driver to nv, if it's not already, test and save the configuration. Then use Synaptic, search for nvidia, uninstall completely all the nvidia drivers there (but not the nvidia-kernel-common). Reboot just to make sure you're ok so far.

X should start with the nv driver. Back to Admin/Restricted Drivers, click on the reinstall nvidia_new driver and enable it. Back to Screen and Graphic, select nvidia for the driver, make sure the Screen model and resolution are correct, test and make sure it starts, save the configuration. Reboot. Does X start?

---

### Post by m2006h on 2007-10-19
Sorry, it probably should be the nvidia-glx-new driver above.

---

### Post by pt123 on 2007-10-19
^ I pretty much did that

Anyway when I opened gnome-appearance-properties in the terminal to see what could be causing the visual effects not to load this is the error I got:

```

(gnome-appearance-properties:6285): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed

(gnome-appearance-properties:6285): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.

(gnome-appearance-properties:6285): Gtk-WARNING **: Unable to locate theme engine in module_path: "candido",
/home/par/.themes/Murrina Deviant/gtk-2.0/gtkrc:56: Murrine configuration option "squaredstyle" is not supported and will be ignored.

(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field


(gnome-appearance-properties:6285): Gtk-WARNING **: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

nvidia_new restricted driver is already enabled
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f1 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
Attaching to program: /usr/bin/compiz.real, process 6371
Reading symbols from /usr/lib/libXcomposite.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcomposite.so.1
Reading symbols from /usr/lib/libXdamage.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdamage.so.1
Reading symbols from /usr/lib/libXfixes.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXfixes.so.3
Reading symbols from /usr/lib/libXrandr.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrandr.so.2
Reading symbols from /usr/lib/libXinerama.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXinerama.so.1
Reading symbols from /usr/lib/libXcursor.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXcursor.so.1
Reading symbols from /usr/lib/libSM.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libSM.so.6
Reading symbols from /usr/lib/libICE.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libICE.so.6
Reading symbols from /usr/lib/libxslt.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxslt.so.1
Reading symbols from /usr/lib/libxml2.so.2...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libxml2.so.2
Reading symbols from /usr/lib/libstartup-notification-1.so.0...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libstartup-notification-1.so.0
Reading symbols from /usr/lib/libGL.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGL.so.1
Reading symbols from /lib/tls/i686/cmov/libm.so.6...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libm.so.6
Reading symbols from /lib/tls/i686/cmov/libc.so.6...(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libc.so.6
Reading symbols from /usr/lib/libX11.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libX11.so.6
Reading symbols from /usr/lib/libXext.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXext.so.6
Reading symbols from /lib/tls/i686/cmov/libdl.so.2...
(no debugging symbols found)...done.
Loaded symbols for /lib/tls/i686/cmov/libdl.so.2
Reading symbols from /usr/lib/libXrender.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXrender.so.1
Reading symbols from /usr/lib/libz.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libz.so.1
Reading symbols from /usr/lib/libGLcore.so.1...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libGLcore.so.1
Reading symbols from /usr/lib/tls/libnvidia-tls.so.1...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/tls/libnvidia-tls.so.1
Reading symbols from /lib/ld-linux.so.2...(no debugging symbols found)...done.
Loaded symbols for /lib/ld-linux.so.2
Reading symbols from /usr/lib/libXau.so.6...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXau.so.6
Reading symbols from /usr/lib/libXdmcp.so.6...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libXdmcp.so.6
Reading symbols from /usr/lib/compiz/libccp.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libccp.so
Reading symbols from /usr/lib/libcompizconfig.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libcompizconfig.so.0
Reading symbols from /usr/lib/compizconfig/backends/libini.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compizconfig/backends/libini.so
Reading symbols from /usr/lib/compiz/libcrashhandler.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libcrashhandler.so
Reading symbols from /usr/lib/compiz/libshift.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libshift.so
Reading symbols from /usr/lib/compiz/libdbus.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libdbus.so
Reading symbols from /usr/lib/libdbus-1.so.3...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libdbus-1.so.3
Reading symbols from /usr/lib/compiz/libresize.so...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libresize.so
Reading symbols from /usr/lib/compiz/libimgjpeg.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libimgjpeg.so
Reading symbols from /usr/lib/libjpeg.so.62...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libjpeg.so.62
Reading symbols from /usr/lib/compiz/libpng.so...
(no debugging symbols found)...done.
Loaded symbols for /usr/lib/compiz/libpng.so
Reading symbols from /usr/lib/libpng12.so.0...(no debugging symbols found)...done.
Loaded symbols for /usr/lib/libpng12.so.0
Reading symbols from /usr/lib/compiz/libsnow.so...done.
Loaded symbols for /usr/lib/compiz/libsnow.so

0xffffe410 in __kernel_vsyscall ()
(gdb) 

#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7bd16b3 in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7b76b8b in ?? () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6564962 in ?? () from /usr/lib/compiz/libcrashhandler.so
#4  0xbf937bd8 in ?? ()
#5  0xb6564a94 in ?? () from /usr/lib/compiz/libcrashhandler.so
#6  0xbf93a8e7 in ?? ()
#7  0x000018e3 in ?? ()
#8  0x000018e3 in ?? ()
#9  0x000018e3 in ?? ()
#10 0x00000017 in ?? ()
#11 0xbf937f7b in ?? ()
#12 0x00000001 in ?? ()
#13 0xb7efe7b0 in ?? () from /lib/ld-linux.so.2
#14 0x6f686365 in ?? ()
#15 0x20652d20 in ?? ()
#16 0x74657322 in ?? ()
#17 0x6f727020 in ?? ()
#18 0x0a74706d in ?? ()
#19 0x65726874 in ?? ()
#20 0x61206461 in ?? ()
#21 0x796c7070 in ?? ()
#22 0x6c6c6120 in ?? ()
#23 0x20746220 in ?? ()
#24 0x6c6c7566 in ?? ()
#25 0x6863650a in ?? ()
#26 0x5c5c206f in ?? ()
#27 0x650a6e5c in ?? ()
#28 0x206f6863 in ?? ()
#29 0x6e5c5c5c in ?? ()
#30 0x0a74620a in ?? ()
#31 0x74697571 in ?? ()
#32 0x203e2022 in ?? ()
#33 0x706d742f in ?? ()
#34 0x6264672f in ?? ()
#35 0x706d742e in ?? ()
#36 0x6264673b in ?? ()
#37 0x20712d20 in ?? ()
#38 0x7273752f in ?? ()
#39 0x6e69622f in ?? ()
#40 0x6d6f632f in ?? ()
#41 0x2e7a6970 in ?? ()
#42 0x6c616572 in ?? ()
#43 0x37333620 in ?? ()
#44 0x203c2031 in ?? ()
#45 0x706d742f in ?? ()
#46 0x6264672f in ?? ()
#47 0x706d742e in ?? ()
#48 0x67207c20 in ?? ()
#49 0x20706572 in ?? ()
#50 0x2220762d in ?? ()
#51 0x73206f4e in ?? ()
#52 0x6f626d79 in ?? ()
#53 0x6174206c in ?? ()
#54 0x22656c62 in ?? ()
#55 0x74207c20 in ?? ()
#56 0x2f206565 in ?? ()
#57 0x2f706d74 in ?? ()
#58 0x706d6f63 in ?? ()
#59 0x635f7a69 in ?? ()
#60 0x68736172 in ?? ()
#61 0x3733362d in ?? ()
#62 0x756f2e31 in ?? ()
#63 0x72203b74 in ?? ()
#64 0x662d206d in ?? ()
#65 0x6d742f20 in ?? ()
#66 0x64672f70 in ?? ()
#67 0x6d742e62 in ?? ()
#68 0x65203b70 in ?? ()
#69 0x206f6863 in ?? ()
#70 0x435b0a22 in ?? ()
#71 0x48534152 in ?? ()
#72 0x4e41485f in ?? ()
#73 0x52454c44 in ?? ()
#74 0x5c203a5d in ?? ()
#75 0x6d742f22 in ?? ()
#76 0x6f632f70 in ?? ()
#77 0x7a69706d in ?? ()
#78 0x6172635f in ?? ()
#79 0x362d6873 in ?? ()
#80 0x2e313733 in ?? ()
#81 0x5c74756f in ?? ()
#82 0x72632022 in ?? ()
#83 0x65746165 in ?? ()
#84 0x220a2164 in ?? ()
#85 0x09691f00 in ?? ()
#86 0x08286900 in ?? ()
#87 0xbf937d34 in ?? ()
#88 0xb7efbc0b in ?? () from /lib/ld-linux.so.2
#89 <signal handler called>
#90 0x00000000 in ?? ()
#91 0x0806cef6 in pushPlugin ()
#92 0x0805500f in eventLoop ()
#93 0x08051bc0 in main ()
The program is running.  Quit anyway (and detach it)? (y or n) [answered Y; input not from terminal]
Detaching from program: /usr/bin/compiz.real, process 6371

[CRASH_HANDLER]: "/tmp/compiz_crash-6371.out" created!

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"




```

XGL error again. 

Also why shouldn't the 6600GT card, use nvidia-glx-new drivers?

---

### Post by m2006h on 2007-10-19
I posted a correction because I made a mistake and said to use nvidia_new instead of nvidia-glx-new. Try uninstalling nvidia_new and installing nvidia-glx-new. That's what I'm using with my Geforce 6600 GT.

---

### Post by PrinceArithon on 2007-10-19
Well the nv driver is working great for me....I just can't get these nvidia drivers to work at all....so it looks like I'm stuck with this nv until one of these nvidia drivers decide to work for me or there is a fix for it...Still I tried everything in this thread and nothing is working at all....

Aaron

---

### Post by Argus on 2007-10-19
After the install was complete X wouldn't start so I used an old xorg.conf this got this going. I figure the nvidia drivers are tied to the kernal and I do believe that gutsy upgraded itl so no wonders it doesn't work.

Once things got started I was asked if I wanted to use the restricted drives, I guess I was feeling lucky so I said yes and rebooted. X would started again, but all I had to was change the driver from "nividia" to "nv" in the xorg.conf. 
 sudo nano /etc/X11/xorg.conf

 After a reboot I was able to login to X then I download the new version ENVY [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (Thanks Alberto). Remember to make sure that all the Ubuntu software repositories are checked before you run Envy or it will fail. Type envy -g at the cmd line, to get the graphical interface and follow the prompts.

Sean

---

### Post by m2006h on 2007-10-19
Sorry it didn't work out. Took me a few days to get it, one of the last things I did was to install the inf driver for my monitor from the windows driver disk. Don't know if that did it or not. It was definitely harder than I thought it should be.

Good luck

---

### Post by Envirotech on 2007-10-19
> **m2006h said:**
> try this:

Modify /etc/default/linux-restricted-modules-common to skip unnecessary kernel modules. 

DISABLED_MODULES="nvidia nvidia_legacy"

Thank you very much this also worked for me.  I hope they fix this though.):P

---

### Post by MDanihy on 2007-10-19
I feel your pain, the upgrade totally choked on nvidia and then crapped out before it could finish.  It then asked me if I wanted to report the error, which was then met with a message stating that I was not using (what I can remember) an official ubuntu (funny, I installed it from their disk).  Then, it stopped.  Left me high and dry, I can't do squat now, it will not complete the update, left everything broken.  I didn't want to do a new install because of all the work I put into getting it running in the first place.

I guess it is my own fault.  I should have waited for the next release after GG.  Its a shame, I liked Ubuntu up until now.

---

### Post by pt123 on 2007-10-20
Good news I managed to get a similar setup to what I had on Feisty.

I uninstalled all the restricted drives fully and went back to nv.

Then installed the drivers from the Nvidia site,


sudo nano /etc/default/linux-restricted-modules-common

Make the last line look like
Code:

DISABLED_MODULES="nv nvidia nvidia_legacy"

ctrl+x and y to save.

Then all this in a Terminal no X


sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

Then after the reboot it was using the nvidia drivers.

Then completely uninstalled compiz & emerald (because on Feisty I was the git rep by Trevino)

Then 
sudo apt-get install compiz

Then started compiz using
this script 

#!/bin/sh

# click to start, click to stop

if pidof compiz.real | grep [0-9] > /dev/null
then
 exec metacity --replace
else
 exec compiz --replace -c emerald
fi

and now everything is working fine... (touches wood)

Since Edgy Ubuntu has been my baby, use it much more than my  Windows installation. Having these upgrade problems caused so much pain & grief. They really need to work on the upgrading 
procedure, because even in Feisty it was a nightmare with the changing of how disks were addressed. 


**Thanks m2006h for all your assistance**


I am going to put the thread as solved.

---

### Post by mocha on 2007-10-20
pt123,

I'm glad I searched for Gutsy upgrade stories before diving in head first!  I have an nvidia 7600 card and booted Gutsy using the LiveCD, then I went into the restricted manager and selected the proprietary driver.  Then I restarted X and experienced exactly the same problems everyone is describing in this thread and numerous others.

Doesn't this qualify as a serious bug????  I'm surprised the Ubuntu team doesn't address this immediately and do a re-release.  I'm very leary of upgrading even with your proposed fix.  I have doubts that it will work for everyone.

---

### Post by pt123 on 2007-10-20
The problem is that sometimes in upgrades bug/errors that didn't do any harm before become a serious issue in the upgrade. 
They should do more testing on upgrades scenarios.

To get the restricted drivers working you need this
DISABLED_MODULES="nvidia nvidia_legacy"
in your 
/etc/default/linux-restricted-modules-common

But I prefer the drivers from the nvidia site. 

If you backup your partitions using the How to thread you can restore your Feisty installation, without too many problems.
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

---

### Post by KozzioU on 2007-10-20
I can't get it to work :/

Restricted driver disabled: Compiz won't start.
Restricted driver enabled: system will run only in low-graphics mode (I have a headache from staring at the low-refresh-rate screen).

I've tried installing drivers from the nvidia site, but to no avail. Running Compiz from terminal doesn't work. Neither does enabling desktop effects.

---

### Post by mocha on 2007-10-20
> **pt123 said:**
> 
To get the restricted drivers working you need this
DISABLED_MODULES="nvidia nvidia_legacy"
in your 
/etc/default/linux-restricted-modules-common


Should I do that before initiating the upgrade?  and then pray?  :lolflag:

Thanks for the link to the system backup how-to.  I was looking for something similar last night.

---

### Post by pt123 on 2007-10-20
> **KozzioU said:**
> I can't get it to work :/
I've tried installing drivers from the nvidia site, but to no avail. Running Compiz from terminal doesn't work. Neither does enabling desktop effects.

what is in your
/etc/default/linux-restricted-modules-common

fille?

-
**mocha**
yes after backing up, because Gutsy runs more smoothly in other areas.

---

### Post by KozzioU on 2007-10-21
My /etc/default/linux-restricted-modules-common:
```
DISABLED_MODULES="nvidia nvidia_legacy"
```

---

### Post by pt123 on 2007-10-21
you are better of creating a new thread explaining your problems & hardware. 

The "Solved" in this thread will make most people to ignore it.

---

