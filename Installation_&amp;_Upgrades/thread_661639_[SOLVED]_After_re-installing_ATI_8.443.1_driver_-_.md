---
title: "[SOLVED] After re-installing ATI 8.443.1 driver - 'libGL error' - DRM open failed"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by perixx on 2008-01-08
Hi! Perhaps somebody can bring me on the right track what to look after in this matter; after de-installing a previously well-working latest (!) ATI-driver in my setup in favour to tinkering around with a Geforce 6800XT (which just wouldn't work), I wanted to re-install the ATI card again. 

After de-installing both (restricted drivers) and re-installing ATI, first via Envy (didn't work as like the first time I used it), de-installing again and simply running the installer (which worked in the first good installation for me), I can't get direct rendering to work (though /var/log/Xorg.0.log doesn't give any 'EE' errors on this!), but see this: 

> fglrxinfo
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1950 GT
OpenGL version string: 1.4 (2.1.7170 Release)

perixx

---

### Post by perixx on 2008-01-08
maybe this is linked to a file permission problem? 
I've done > 'sudo depmod -a'
sudo aticonfig --initial
 after installing the driver.

My xorg.conf file's relevant lines:
> Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load	   "dri"
    Load           "drm"       <<<<< not sure if that does anything, added myself for test
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
Section "Device"
    Identifier     "Standardgrafikkarte"
#    Option	   "DynamicTwinView" "false"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
#	Option		"OpenGLOverlay"	"off"
	Option		"UseFastTLS"	"2"
	Option		"XaaNoOffscreenPixmaps"
EndSection
Section "ServerFlags"
    Option         "AIGLX" "on"
EndSection
Section "Extensions"
	Option		"Composite"	"Disable"
EndSection

My card and setup results:
> lspci | grep ATI
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7288 (rev 9a) -- ATI X1950GT
01:00.1 Display controller: ATI Technologies Inc Unknown device 72a8 (rev 9a)

lsmod | grep fglrx
fglrx                1496044  22 
agpgart                35400  2 fglrx,ati_agp

~/.xsession-errors:
/usr/bin/startxfce4: X server already running on display :0
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
** Message: This build doesn't include support for XF86Misc extension

> less /var/log/Xorg.0.log | grep EE returned nothing of interest (only wacom). 

'amdcccle' in terminal:
>  amdcccle
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
X Error: BadMatch (invalid parameter attributes) 8
  Extension:    143 (Uknown extension)
  Minor opcode: 5 (Unknown request)
  Resource id:  0x3600001
X Error: GLXBadContext 155
  Extension:    143 (Uknown extension)
  Minor opcode: 5 (Unknown request)
  Resource id:  0x2e00002

'Information' will tell that driver version 8.44.3 is installed + OpenGL renderer ATI Radeon X1950 GT, version 1.4 (2.1.7170 Release).

Someone got an idea please?

perixx

---

### Post by perixx on 2008-01-08
**[COLOR="Teal"]**PROBLEM SOLVED**[/COLOR]**

After using ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and re-setting the German keyboard layout in the keyboard manager, OpenGL is up and running again! Now I'll just have to downgrade to my former drivers, for with the 8.443.1 driver run less Games than before...

perixx

---

