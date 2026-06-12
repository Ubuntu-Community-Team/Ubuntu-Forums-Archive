---
title: "nvidia GLX not working after upgrade"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by mpooley on 2007-04-21
Hi
I upgraded using update manager and had to re- install nvidia drivers just to get the x server running but now any desktop effects dont work and in my Nvidia server settings on the glx tab i get this message

GLX not available: either the GLX extension is not
available on this X server, or there was a problem
retrieving GLX information from the X server.

i have googled around and notice that this was a problem also on the last upgrade to edgy!  i have tried editing the xorg.conf using info from these old posts but they dont work,

any ideas anyone so far i'm wishing i hadn't UPgraded?

---

### Post by bulldog on 2007-04-21
Did you install the restricted modules for your kernel?
Did you check if the driver in xorg.conf is listed as nvidia or nv?

---

### Post by d58e7 on 2007-04-21
I'm having a similar problem with GTS. I got around it by uninstalling all of the GLX stuff under the desktop then I installed the driver from Nvidia.com . It works but after a reboot the nvidia.com driver needs to be installed again for me to get into the GDM.

---

### Post by mpooley on 2007-04-21
> **bulldog said:**
> Did you install the restricted modules for your kernel?
Did you check if the driver in xorg.conf is listed as nvidia or nv?
yes and yes:)

---

### Post by mpooley on 2007-04-21
> **d58e7 said:**
> I'm having a similar problem with GTS. I got around it by uninstalling all of the GLX stuff under the desktop then I installed the driver from Nvidia.com . It works but after a reboot the nvidia.com driver needs to be installed again for me to get into the GDM.
Not really sure what you mean there - it sounds like you are having to re-install on every boot???  i must be reading you wrong?

also how do you uninstall the drivers?

---

### Post by d58e7 on 2007-04-21
Well you need to set the video driver to nv or vesa using: sudo dpkg-reconfigure -phigh xserver-xorg . Then you go into synaptic package manager and remove the GLX drivers. Then you just download the nvidia website drivers and install it through the terminal. For me it's not saving the information and I have to install the nvidia website drivers after each boot.

---

### Post by bulldog on 2007-04-21
Does your xorg.conf look like this one from the device section?
```
Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"  ** <----- Pay attention to this one**
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
```

---

### Post by d58e7 on 2007-04-21
Not sure if you were talking to me, but my xorg.conf file has all that information exactly the same

---

### Post by mpooley on 2007-04-22
> **bulldog said:**
> Does your xorg.conf look like this one from the device section?
```
Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV40 [GeForce 6800 Ultra]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"  ** <----- Pay attention to this one**
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1440x900" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
```


thos is how mine looks
Section "Device"
	Identifier	"Nvidai 6600"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia 6600"
	Monitor		"Relisys"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

---

### Post by autocrosser on 2007-04-22
Double-check the Nvidia-GLX you have installed--There was a "new" split with Feisty, Nvidia-GLX is for the "old" cards & Nvidia-GLX-New is for the "new" cards:). As I have heard it, this still falls along the Legacy & newer card lines (just the names have changed).

---

### Post by pinan on 2007-04-22
> **d58e7 said:**
> Well you need to set the video driver to nv or vesa using: sudo dpkg-reconfigure -phigh xserver-xorg . Then you go into synaptic package manager and remove the GLX drivers. Then you just download the nvidia website drivers and install it through the terminal. For me it's not saving the information and I have to install the nvidia website drivers after each boot.

Had the same type of thing
editted the file /etc/default/linux-restricted-modules-common 
and add the line 

DISABLED_MODULES="nv"

---

### Post by mpooley on 2007-04-22
> **autocrosser said:**
> Double-check the Nvidia-GLX you have installed--There was a "new" split with Feisty, Nvidia-GLX is for the "old" cards & Nvidia-GLX-New is for the "new" cards:). As I have heard it, this still falls along the Legacy & newer card lines (just the names have changed).
Thanks for your reply.
I have a geoforce 6600 is that considered new?
How do i check which glx i have?

---

### Post by tommcd on 2007-04-22
> **autocrosser said:**
> Double-check the Nvidia-GLX you have installed--There was a "new" split with Feisty, Nvidia-GLX is for the "old" cards & Nvidia-GLX-New is for the "new" cards:). As I have heard it, this still falls along the Legacy & newer card lines (just the names have changed).

I was wondering about that nvidia-glx-new, versus the nvidia-glx. I installed the nvidia-glx for my nvidia 6200 since that is what I was used to, and it is still listed here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29)
Is nvidia-glx now the legacy driver, and should I be using nvidia-glx-new?
Nvidia-glx seems to be working ok.
EDIT: found this thread that explains the nvidia-glx-new stuff:
[http://ubuntuforums.org/showthread.php?t=406845&highlight=nvidia+glx+new](http://ubuntuforums.org/showthread.php?t=406845&highlight=nvidia+glx+new)
I'll try switching to nvidia-glx-new when I get home from work.

---

### Post by mpooley on 2007-04-22
> **pinan said:**
> Had the same type of thing
editted the file /etc/default/linux-restricted-modules-common 
and add the line 

DISABLED_MODULES="nv"
Thanks - tried that but it booted to command line!

---

### Post by shirsch on 2007-04-22
Fought with this myself.  The package manager / updater seems to get very confused about compatible versions of glx package vs. kernel module.  There are (3) versions of glx (legacy, "std" and new) with (3) versions of the kernel support to go with them.  These are all under the umbrella of 'nvidia-kernel-common', but aptitude shows virtual packages with three corresponding levels of the module.  I'll never understand the virtual package business as long as I live...

Anyway, if you check both /var/log/Xorg.0.log and /var/log/syslog, I'm betting you'll see a complaint about mismatched versions of glx and module. I couldn't find any obvious way to install one virtual package over the other, so I purged both (you must use the '--force-all' switch to remove the module, since it claims to be part of a larger package).  Then, reinstall glx-new and the highest revision of kernel module.

NOTE: This is probably a horrifyingly incorrect way to fix things, so don't be upset with me if it hoses your system!

---

### Post by mpooley on 2007-04-22
I get
(II) Loading /usr/lib/xorg/modules//libglx.so
dlopen: /usr/lib/libGLcore.so.1: undefined symbol: _nv000043gl
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)

and 
Apr 22 17:25:25 mike-desktop kernel: [   79.463682] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Apr 22 17:25:25 mike-desktop kernel: [   79.463696] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Apr 22 17:25:25 mike-desktop kernel: [   79.463742] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Apr 22 17:25:26 mike-desktop hpiod: 1.7.3 accepting connections at 2208... 
Apr 22 17:25:26 mike-desktop kernel: [   80.117320] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
Apr 22 17:25:26 mike-desktop kernel: [   80.118087] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
Apr 22 17:25:26 mike-desktop kernel: [   80.118575] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!


IVE NO IDEA WHAT ALL THAT MEANS!

---

### Post by poekie on 2007-04-22
I had trouble getting GLX to work as well...
I installed nvidia-glx-new and changed xorg.conf with these lines (of course: driver should be nvidia not nv)  
```

#changed to ON because Xlog gave error about GLX and Composite not working together properly, this #was solution to that:
    Option         "AllowGLXWithComposite" "On" 
#added because glx wasn't working and this was supposed to work
   Option         "AddARGBGLXVisuals" "True"

```

And now it works! :D

---

### Post by mpooley on 2007-04-23
do you mean the -Linux-x86-1.0-9755 driver?
I tried to install this last night and it recompiled my kernal.
Trouble is there was an error and my screen is now just bands of bluecream stripes!

i then tried to re-install the old driver nut it said there was a kernal mismatch and it wouldnt do it.
so i have had to revert to nv driver and i am seriously thinking of dumping the whole system and re- installing edgy !!

---

