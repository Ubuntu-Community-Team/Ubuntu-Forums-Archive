---
title: "ubuntu 12.04 boot to tty1"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Exar Kun on 2012-04-27
I have recently do a fresh install of ubuntu 12.04 and all went all right but in my first boot it goes directly to tty1 and no gui.

---

### Post by BicyclerBoy on 2012-04-27
Login with username & password..

sudo Xorg -configure
sudo service lightdm start

Does X come to life ?

No:
post as attachments:
/var/log/lightdm/lightdm.log
/var/log/Xorg.0.log

---

### Post by Exar Kun on 2012-04-27
I did that and this is what I get
[IMG][[IMG]http://img835.imageshack.us/img835/8974/dsc0641dv.jpg[/IMG]](http://imageshack.us/photo/my-images/835/dsc0641dv.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]

---

### Post by BicyclerBoy on 2012-04-27
Do you have any idea what the h/w is ?
Sandybridge, atom2600, AMD A E cpu ?

Can you post the log files?
Copy them on to a USB stick (from console login)..

You can switch between the console screens with <ctrl>+<alt>+<Fn> where Fn are the function keys..your console screen is likely to be F1 & your dead X server is on F7.

---

### Post by Exar Kun on 2012-04-27
I have an AMD Phenom II x4 945, nvidia GeForce GTX 460 and I can switch betwen the tty but everything is the same.

---

### Post by BicyclerBoy on 2012-04-27
Post the log file
/var/log/Xorg.0.log

The nVidia 460 is quite new so likely needs the 275 version..
Maybe the std nouveau driver has no support for 460..

sudo apt-get install nvidia-current-updates

---

### Post by Exar Kun on 2012-04-27
```
[     9.767] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[     9.767] X Protocol Version 11, Revision 0
[     9.767] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     9.767] Current Operating System: Linux ignacio-desktop 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
[     9.767] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=e467e1c2-6d2b-4300-82c9-00e4164b7638 ro quiet splash vt.handoff=7
[     9.767] Build Date: 05 April 2012  04:32:37AM
[     9.767] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[     9.767] Current version of pixman: 0.24.4
[     9.767] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     9.767] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.767] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 27 19:08:55 2012
[     9.767] (==) Using config file: "/etc/X11/xorg.conf"
[     9.767] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.767] (==) No Layout section.  Using the first Screen section.
[     9.767] (==) No screen section available. Using defaults.
[     9.767] (**) |-->Screen "Default Screen Section" (0)
[     9.767] (**) |   |-->Monitor "<default monitor>"
[     9.767] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[     9.767] (**) |   |-->Device "Default Device"
[     9.767] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     9.767] (==) Automatically adding devices
[     9.767] (==) Automatically enabling devices
[     9.767] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.767] 	Entry deleted from font path.
[     9.767] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.767] 	Entry deleted from font path.
[     9.767] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.767] 	Entry deleted from font path.
[     9.767] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.767] 	Entry deleted from font path.
[     9.767] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.767] 	Entry deleted from font path.
[     9.767] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     9.767] 	Entry deleted from font path.
[     9.767] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     9.767] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.767] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.767] (II) Loader magic: 0x7fd96432cb00
[     9.767] (II) Module ABI versions:
[     9.767] 	X.Org ANSI C Emulation: 0.4
[     9.767] 	X.Org Video Driver: 11.0
[     9.767] 	X.Org XInput driver : 16.0
[     9.767] 	X.Org Server Extension : 6.0
[     9.768] (--) PCI:*(0:1:0:0) 10de:0e22:1458:34fa rev 161, Mem @ 0xfc000000/33554432, 0xd0000000/134217728, 0xd8000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     9.768] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.768] (II) LoadModule: "extmod"
[     9.799] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.799] (II) Module extmod: vendor="X.Org Foundation"
[     9.799] 	compiled for 1.11.3, module version = 1.0.0
[     9.799] 	Module class: X.Org Server Extension
[     9.799] 	ABI class: X.Org Server Extension, version 6.0
[     9.799] (II) Loading extension MIT-SCREEN-SAVER
[     9.799] (II) Loading extension XFree86-VidModeExtension
[     9.799] (II) Loading extension XFree86-DGA
[     9.799] (II) Loading extension DPMS
[     9.799] (II) Loading extension XVideo
[     9.799] (II) Loading extension XVideo-MotionCompensation
[     9.799] (II) Loading extension X-Resource
[     9.799] (II) LoadModule: "dbe"
[     9.799] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.799] (II) Module dbe: vendor="X.Org Foundation"
[     9.799] 	compiled for 1.11.3, module version = 1.0.0
[     9.799] 	Module class: X.Org Server Extension
[     9.799] 	ABI class: X.Org Server Extension, version 6.0
[     9.799] (II) Loading extension DOUBLE-BUFFER
[     9.799] (II) LoadModule: "glx"
[     9.799] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     9.808] (II) Module glx: vendor="NVIDIA Corporation"
[     9.808] 	compiled for 4.0.2, module version = 1.0.0
[     9.808] 	Module class: X.Org Server Extension
[     9.808] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[     9.808] (II) Loading extension GLX
[     9.808] (II) LoadModule: "record"
[     9.808] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.808] (II) Module record: vendor="X.Org Foundation"
[     9.808] 	compiled for 1.11.3, module version = 1.13.0
[     9.808] 	Module class: X.Org Server Extension
[     9.808] 	ABI class: X.Org Server Extension, version 6.0
[     9.808] (II) Loading extension RECORD
[     9.808] (II) LoadModule: "dri"
[     9.808] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.809] (II) Module dri: vendor="X.Org Foundation"
[     9.809] 	compiled for 1.11.3, module version = 1.0.0
[     9.809] 	ABI class: X.Org Server Extension, version 6.0
[     9.809] (II) Loading extension XFree86-DRI
[     9.809] (II) LoadModule: "dri2"
[     9.809] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.809] (II) Module dri2: vendor="X.Org Foundation"
[     9.809] 	compiled for 1.11.3, module version = 1.2.0
[     9.809] 	ABI class: X.Org Server Extension, version 6.0
[     9.809] (II) Loading extension DRI2
[     9.809] (==) Matched nvidia as autoconfigured driver 0
[     9.809] (==) Matched nouveau as autoconfigured driver 1
[     9.809] (==) Matched nv as autoconfigured driver 2
[     9.809] (==) Matched vesa as autoconfigured driver 3
[     9.809] (==) Matched fbdev as autoconfigured driver 4
[     9.809] (==) Assigned the driver to the xf86ConfigLayout
[     9.809] (II) LoadModule: "nvidia"
[     9.809] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     9.809] (II) Module nvidia: vendor="NVIDIA Corporation"
[     9.809] 	compiled for 4.0.2, module version = 1.0.0
[     9.809] 	Module class: X.Org Video Driver
[     9.809] (II) LoadModule: "nouveau"
[     9.809] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.809] (II) Module nouveau: vendor="X.Org Foundation"
[     9.809] 	compiled for 1.11.3, module version = 0.0.16
[     9.809] 	Module class: X.Org Video Driver
[     9.809] 	ABI class: X.Org Video Driver, version 11.0
[     9.809] (II) LoadModule: "nv"
[     9.852] (WW) Warning, couldn't open module nv
[     9.852] (II) UnloadModule: "nv"
[     9.852] (II) Unloading nv
[     9.852] (EE) Failed to load module "nv" (module does not exist, 0)
[     9.852] (II) LoadModule: "vesa"
[     9.853] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.853] (II) Module vesa: vendor="X.Org Foundation"
[     9.853] 	compiled for 1.11.3, module version = 2.3.0
[     9.853] 	Module class: X.Org Video Driver
[     9.853] 	ABI class: X.Org Video Driver, version 11.0
[     9.853] (II) LoadModule: "fbdev"
[     9.853] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.853] (II) Module fbdev: vendor="X.Org Foundation"
[     9.853] 	compiled for 1.11.3, module version = 0.4.2
[     9.853] 	ABI class: X.Org Video Driver, version 11.0
[     9.853] (==) Matched nvidia as autoconfigured driver 0
[     9.853] (==) Matched nouveau as autoconfigured driver 1
[     9.853] (==) Matched nv as autoconfigured driver 2
[     9.853] (==) Matched vesa as autoconfigured driver 3
[     9.853] (==) Matched fbdev as autoconfigured driver 4
[     9.853] (==) Assigned the driver to the xf86ConfigLayout
[     9.853] (II) LoadModule: "nvidia"
[     9.853] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     9.853] (II) Module nvidia: vendor="NVIDIA Corporation"
[     9.853] 	compiled for 4.0.2, module version = 1.0.0
[     9.853] 	Module class: X.Org Video Driver
[     9.853] (II) UnloadModule: "nvidia"
[     9.853] (II) Unloading nvidia
[     9.853] (II) Failed to load module "nvidia" (already loaded, 32729)
[     9.853] (II) LoadModule: "nouveau"
[     9.853] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.853] (II) Module nouveau: vendor="X.Org Foundation"
[     9.853] 	compiled for 1.11.3, module version = 0.0.16
[     9.853] 	Module class: X.Org Video Driver
[     9.853] 	ABI class: X.Org Video Driver, version 11.0
[     9.853] (II) UnloadModule: "nouveau"
[     9.853] (II) Unloading nouveau
[     9.853] (II) Failed to load module "nouveau" (already loaded, 32729)
[     9.853] (II) LoadModule: "nv"
[     9.853] (WW) Warning, couldn't open module nv
[     9.853] (II) UnloadModule: "nv"
[     9.853] (II) Unloading nv
[     9.853] (EE) Failed to load module "nv" (module does not exist, 0)
[     9.853] (II) LoadModule: "vesa"
[     9.853] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.853] (II) Module vesa: vendor="X.Org Foundation"
[     9.853] 	compiled for 1.11.3, module version = 2.3.0
[     9.853] 	Module class: X.Org Video Driver
[     9.853] 	ABI class: X.Org Video Driver, version 11.0
[     9.853] (II) UnloadModule: "vesa"
[     9.853] (II) Unloading vesa
[     9.853] (II) Failed to load module "vesa" (already loaded, 0)
[     9.853] (II) LoadModule: "fbdev"
[     9.853] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.853] (II) Module fbdev: vendor="X.Org Foundation"
[     9.854] 	compiled for 1.11.3, module version = 0.4.2
[     9.854] 	ABI class: X.Org Video Driver, version 11.0
[     9.854] (II) UnloadModule: "fbdev"
[     9.854] (II) Unloading fbdev
[     9.854] (II) Failed to load module "fbdev" (already loaded, 0)
[     9.854] (II) NVIDIA dlloader X Driver  295.40  Thu Apr  5 21:38:35 PDT 2012
[     9.854] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     9.854] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[     9.854] (II) NOUVEAU driver for NVIDIA chipset families :
[     9.854] 	RIVA TNT        (NV04)
[     9.854] 	RIVA TNT2       (NV05)
[     9.854] 	GeForce 256     (NV10)
[     9.854] 	GeForce 2       (NV11, NV15)
[     9.854] 	GeForce 4MX     (NV17, NV18)
[     9.854] 	GeForce 3       (NV20)
[     9.854] 	GeForce 4Ti     (NV25, NV28)
[     9.854] 	GeForce FX      (NV3x)
[     9.854] 	GeForce 6       (NV4x)
[     9.854] 	GeForce 7       (G7x)
[     9.854] 	GeForce 8       (G8x)
[     9.854] 	GeForce GTX 200 (NVA0)
[     9.854] 	GeForce GTX 400 (NVC0)
[     9.854] (II) VESA: driver for VESA chipsets: vesa
[     9.854] (II) FBDEV: driver for framebuffer: fbdev
[     9.854] (++) using VT number 7

[     9.854] (II) Loading sub module "fb"
[     9.854] (II) LoadModule: "fb"
[     9.854] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.854] (II) Module fb: vendor="X.Org Foundation"
[     9.854] 	compiled for 1.11.3, module version = 1.0.0
[     9.854] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.854] (II) Loading sub module "wfb"
[     9.854] (II) LoadModule: "wfb"
[     9.854] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     9.854] (II) Module wfb: vendor="X.Org Foundation"
[     9.854] 	compiled for 1.11.3, module version = 1.0.0
[     9.854] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     9.854] (II) Loading sub module "ramdac"
[     9.854] (II) LoadModule: "ramdac"
[     9.854] (II) Module "ramdac" already built-in
[     9.854] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     9.854] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     9.854] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.854] (WW) Falling back to old probe method for vesa
[     9.854] (WW) Falling back to old probe method for fbdev
[     9.854] (II) Loading sub module "fbdevhw"
[     9.854] (II) LoadModule: "fbdevhw"
[     9.854] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     9.854] (II) Module fbdevhw: vendor="X.Org Foundation"
[     9.854] 	compiled for 1.11.3, module version = 0.0.2
[     9.854] 	ABI class: X.Org Video Driver, version 11.0
[     9.854] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     9.854] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     9.854] (==) NVIDIA(0): RGB weight 888
[     9.854] (==) NVIDIA(0): Default visual is TrueColor
[     9.854] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     9.854] (**) NVIDIA(0): Option "NoLogo" "True"
[     9.854] (**) NVIDIA(0): Enabling 2D acceleration
[    18.850] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[    18.850] (EE) NVIDIA(0):     check your system's kernel log for additional error
[    18.850] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[    18.850] (EE) NVIDIA(0):     README for additional information.
[    18.850] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    18.850] (II) UnloadModule: "nvidia"
[    18.850] (II) Unloading nvidia
[    18.850] (II) UnloadModule: "wfb"
[    18.850] (II) Unloading wfb
[    18.850] (II) UnloadModule: "fb"
[    18.850] (II) Unloading fb
[    18.850] (EE) Screen(s) found, but none have a usable configuration.
[    18.850] 
Fatal server error:
[    18.850] no screens found
[    18.850] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    18.850] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    18.850] 
[    18.869]  ddxSigGiveUp: Closing log
[    18.869] Server terminated with error (1). Closing log file.
```

That's my Xorg.0.log. I have previously install ubuntu 11.10 and 11.04 in the same machine without problems.

---

### Post by BicyclerBoy on 2012-04-27
Look to me the nouveau driver is being loaded & interfering with nVidia driver..

The nVidia driver install is meant to blacklist the nouveau driver.

You could just purge all nvidia packages & reinstall
apt-get -s purge nvidia*
check nothing really bad is going to happen..
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current

You could try searching in /etc/modprobe.d/*.conf files for
blacklist nouveau.

If you can not find this string just make a file 
/etc/modprobe.d/nvidia.conf
and add
blacklist nouveau

---

### Post by Exar Kun on 2012-04-27
I did all that and nothing

---

### Post by BicyclerBoy on 2012-04-27
Can you please elaborate ?

The purge did remove stuff ?
The install nvidia-current did work?

Did you have to add a blacklist entry ?

Run:
sudo nvidia-xconfig

Reboot & repost /var/log/Xorg.0.log

---

### Post by d4m1r on 2013-02-27
> **Exar Kun said:**
> I have an AMD Phenom II x4 945, nvidia GeForce GTX 460 and I can switch betwen the tty but everything is the same.

Very interesting....I also have the X4 945 + a GTX card (260) and I am having this problem. Occasionally, 12.04 will boot to TTY1 instead of LightDM :(

---

### Post by MAFoElffen on 2013-02-27
Please post your /var/log/Xorg.0.log file, and also do 
```

sudo cat /var/log/lightdm/lightdm.log > lightdm.log.txt

```
and post that file.

Then from console (already logged in), do
```

startx

```
If it locks up, use hot keys <cntrl><alt><F2> log in and do 
```

dmesg | tail -n 50 > ~/snapshot.log.txt

```
And post that file.

If it starts an X session, it's in the graphical loggin. If it doesn't it may be the video driver, which should also show in the xorg log and the syslog snapshot.

---

### Post by d4m1r on 2013-02-27
Thanks for the reply, find all 3 files attached.

Let me know whats next :)

Edit: Xorg log file too big for attachment so find it [HERE]("http://paste2.org/p/3005049").

---

### Post by MAFoElffen on 2013-02-27
> **d4m1r said:**
> Thanks for the reply, find all 3 files attached.

Let me know whats next :)

Edit: Xorg log file too big for attachment so find it [HERE]("http://paste2.org/p/3005049").

Please post your /etc/X11/xorg.conf (I editted name) file in a code box. What you do to do that is select the "#" icon in the post tools bar. Paste the text within the code tags.

I'll edit it for you.

Where yours is failing... "Your" error shows up in both your Xorg.0.log and the syslog snapshot, then passing that fail flag on to LightDM. It loads your nVidia driver successfully, then when it tries modes in your monitor, somehow the translation from EDID for the horizontal and vertical refresh rates are not synching. I can set that manually for you, by editing your xorg.conf file.

Note- It's trying 50hz on verticle refresh, where it should be vetical 56-75, horizontal range 30-81...

---

### Post by d4m1r on 2013-02-28
Weird....I already posted a response but it looks like it was deleted/never went through?

Thanks for the reply MAF. Few things;

1) Yes, I even saw that 50hz in my nvidia settings UI and tried to change it, but it was the only option. The normal for this monitor (new 22" Samsung) is 60hz and that is what I have always run it at. I remember trying to set it manually in a file but that did not work so I've left it @ 50hz ever since as I thought it wasn't causing me any issues, but maybe it has?

2) After running those commands last night, I was not able to login to my Ubuntu desktop today. I think they managed to screw up LightDM enough, but I eventually fixed the problem as I posted [HERE]("http://ubuntuforums.org/showthread.php?t=1999552&p=12535258&viewfull=1#post12535258").

3) Find my Xorg.conf below. Note that I have already fixed it up according to your comments but let me know how it looks now or if any other changes are needed.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 295.33  (buildd@allspice)  Fri Mar 30 13:37:33 UTC 2012

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    # HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "nvidia-auto-select +0+0"
    # Removed Option "metamodes" "nvidia-auto-select +0+0"
    # Removed Option "metamodes" "1920x1080_50 +0+0; nvidia-auto-select +0+0"
    SubSection "Display"
        Depth       24
    EndSubSection
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    # generated from default
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
    Option "Coolbits" "4"
    Option    "NoLogo"    "True"
EndSection


```

---

### Post by MAFoElffen on 2013-02-28
That looks good. Did it work?

If not, there's another way... More work... But I have nVidia w/ Samsung also...

Here's what worked for mine to get all my resolutions:
```

# nvidia-xconfig: X configuration file modifed by MAFoElffen 2013.02.02
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Thu Apr  5 22:40:54 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.0 - 67.0
    VertRefresh     59.0 - 61.0
    ModeLine       "640x480_60" 23.86 640 656 720 800 480 481 484 497 -hsync +vsync
    ModeLine       "800x600_60" 38.22 800 832 912 1024 600 601 604 622 -hsync +vsync
    ModeLine       "1024x768_60" 64.11 1024 1080 1184 1344 768 769 772 795 -hsync +vsync
    ModeLine       "1280x800_60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1280x960_60" 102.10 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024_60" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1440x900_60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1200_60" 160.96 1600 1704 1880 2160 1200 1201 1204 1242 -hsync +vsync
    ModeLine       "1680x1050_60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1080_60" 172.80 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync
    Option         "DPMS"
    ## Valid Monitor Modes
    Option         "PreferredMode" "1920x1080_60"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
 # Option         "NoLogo" "False"
    Option         "UseEDID" "False"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by d4m1r on 2013-03-01
I would know if it works or not if I never experience the "boot to TTY1 instead of LightDM" issue again and while I haven't, I've only booted 1-2 times but so far so good. Hoping we've solved it for good but I'll only be able to tell after a few more boots :)

---

### Post by MAFoElffen on 2013-03-01
k... Waiting then.

---

### Post by d4m1r on 2013-03-04
Thanks MAF! It's been several days now and I haven't hit it again so I'm going to assume it is fixed :)

Never would have thought an Xorg resolution issue was the cause of my lightdm issues.....

---

### Post by d4m1r on 2013-03-05
Nooooo, it just happened again! xorg.conf:

```
Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Samsung SyncMaster"
        HorizSync       30.0 - 81.0
        VertRefresh     56.0 - 75.0

```

So it hasn't changed but occasionally Ubuntu will still boot to TTY1 instead of into LightDM :confused: Although it looks like less occasionally with your partial fix MAF...

---

