---
title: "Blanck screen - Ubuntu 11.10 64bit Intel i5 Sandy-bridge"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by stumbleUpon on 2011-12-25
I am trying to install ubuntu 11.10 64bit on an Intel i5 with sandy-bridge architecture and integrated graphics card. I was not at all able to use the desktop CD to install. I used the alternate CD and managed to install the OS. But i cant boot into the system. The system hangs just after the GRUB screen. I tried editing the boot options with the 'nomodeset' flag. But it does not help. I just get a blank screen and the system hangs. I have had to force poweroff several time to restart the system.

Any help is greatly appreciated.

---

### Post by MAFoElffen on 2011-12-25
> **stumbleUpon said:**
> I am trying to install ubuntu 11.10 64bit on an Intel i5 with sandy-bridge architecture and integrated graphics card. I was not at all able to use the desktop CD to install. I used the alternate CD and managed to install the OS. But i cant boot into the system. The system hangs just after the GRUB screen. I tried editing the boot options with the 'nomodeset' flag. But it does not help. I just get a blank screen and the system hangs. I have had to force poweroff several time to restart the system.

Any help is greatly appreciated.
And the graphics is seen as Intel?

---

### Post by JCoop on 2011-12-26
My computer is almost identical to yours. I will post a link below to my installation solution. Let me know if this helps or if you have any more questions. Good Luck!

[http://ubuntuforums.org/showthread.php?t=1863125](http://ubuntuforums.org/showthread.php?t=1863125)

---

### Post by stumbleUpon on 2011-12-26
@MAFoElffen and JCoop: Thanks for your replies.

@MAFoElffen: Yes it had recognized the intel graphics.

I ended up using installing 10.04. That works cleanly. But then there is the problem of lower screen resolution due to the older kernel -- 2.6.32 that comes with lucid does not detect higher screen resolutions on machines with sandy-bridge architecture. I solved that by installing a newer kernel following the ppa from here

[http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa)

But there is another problem now. Wireless is not working. I have a broadcom 4313 card. The wireless does not even show up.

---

### Post by MAFoElffen on 2011-12-26
> **stumbleUpon said:**
> @MAFoElffen and JCoop: Thanks for your replies.

@MAFoElffen: Yes it had recognized the intel graphics.

I ended up using installing 10.04. That works cleanly. But then there is the problem of lower screen resolution due to the older kernel -- 2.6.32 that comes with lucid does not detect higher screen resolutions on machines with sandy-bridge architecture. I solved that by installing a newer kernel following the ppa from here

[http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa)

But there is another problem now. Wireless is not working. I have a broadcom 4313 card. The wireless does not even show up.
Yes, the Sandy Bridge/Intel Graphics have some of the same problems with resolutions even with Oneiric. (It an upstream problem)

But "newer" covers more wireless cards. They started supporting more graphics cards with 10.10... 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Even though Intel gets recognized by xserver-xorg-video-intel... Create an xorg.conf file pointing to intel as a driver,. Then create the resolutions you want to try... 

What's your skill level on Linux?  If it's low, if you can post your /var/log/Xorg.).log file, I'll create an xorg.cong file for you. If you'd like to learn how to do it yourself, I'll give you instructions and examples.

---

### Post by stumbleUpon on 2011-12-27
@MAFoElffen

Thanks for the response. 

Though i have been using ubuntu from the days of Dapper, I only have moderate experience playing with system files. I am a scientist by profession and do all my scientific stuff with ubuntu. It has never let me down. This is the first time i have had so much trouble. But i dont want to give up either...!


I have 10.04 running well as of now on my laptop. I will install 11.10 using the alternate CD (well i'll actually be using a USB stick to install) in a separate partition. If all goes well, then i can switch over to 11.10 completely. I'll post the contents of '/var/log/Xorg' as soon as i get the install done.

In the link you gave about wireless cards, it is mentioned that 10.04 supports the broadcom 4313 card. I tried to install the bcmwl-kernel-source package. It fails to install with the kernel i am using (2.6.38-13). I dont know why. Here is what i get

```

vijay@advaitha:~$ sudo apt-get install bcmwl-kernel-source 
[sudo] password for vijay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/967kB of archives.
After this operation, 3,342kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package dkms.
(Reading database ... 301313 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2ubuntu1_all.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2ubuntu1) ...

Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-13-generic
Building for architecture x86_64
Building initial module for 2.6.38-13-generic

Error! Bad return status for module build on kernel: 2.6.38-13-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by MAFoElffen on 2011-12-28
> **stumbleUpon said:**
> @MAFoElffen

Thanks for the response. 

Though i have been using ubuntu from the days of Dapper, I only have moderate experience playing with system files. I am a scientist by profession and do all my scientific stuff with ubuntu. It has never let me down. This is the first time i have had so much trouble. But i dont want to give up either...!


I have 10.04 running well as of now on my laptop. I will install 11.10 using the alternate CD (well i'll actually be using a USB stick to install) in a separate partition. If all goes well, then i can switch over to 11.10 completely. I'll post the contents of '/var/log/Xorg' as soon as i get the install done.

In the link you gave about wireless cards, it is mentioned that 10.04 supports the broadcom 4313 card. I tried to install the bcmwl-kernel-source package. It fails to install with the kernel i am using (2.6.38-13). I dont know why. Here is what i get

```

vijay@advaitha:~$ sudo apt-get install bcmwl-kernel-source 
[sudo] password for vijay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  bcmwl-kernel-source dkms
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/967kB of archives.
After this operation, 3,342kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package dkms.
(Reading database ... 301313 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2ubuntu1_all.deb) ...
Selecting previously deselected package bcmwl-kernel-source.
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2ubuntu1) ...

Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-13-generic
Building for architecture x86_64
Building initial module for 2.6.38-13-generic

Error! Bad return status for module build on kernel: 2.6.38-13-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Drivers, no matter what for (graphics, wireles, etc.)... My rule of thumb is to remove any old drivers before installing a new driver--> Especially if the new driver is from a different code base or "style".  What usually happens is that it ends upd with fragments of both that confilct or don't work together.

---

### Post by stumbleUpon on 2011-12-28
@MAFoElffen

I have installed 11.10 using the alternate install method. As before, I get a blank screen on booting to the desktop. I am using the recovery mode to login and extract info. I have a wired internet connection available. 

Here are the contents of the /var/log/Xorg.0.log file in my system.

```


[  1525.573] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  1525.573] X Protocol Version 11, Revision 0
[  1525.573] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[  1525.573] Current Operating System: Linux advaitha 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[  1525.573] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=c135a5a2-a1d3-487d-a00f-798e17c27107 ro recovery nomodeset
[  1525.573] Build Date: 19 October 2011  05:21:26AM
[  1525.573] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[  1525.573] Current version of pixman: 0.22.2
[  1525.573] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  1525.573] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1525.573] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 28 11:40:40 2011
[  1525.573] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1525.774] (==) No Layout section.  Using the first Screen section.
[  1525.774] (==) No screen section available. Using defaults.
[  1525.774] (**) |-->Screen "Default Screen Section" (0)
[  1525.774] (**) |   |-->Monitor "<default monitor>"
[  1525.774] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1525.774] (==) Automatically adding devices
[  1525.774] (==) Automatically enabling devices
[  1525.774] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1525.774] 	Entry deleted from font path.
[  1525.774] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  1525.774] 	Entry deleted from font path.
[  1525.774] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  1525.774] 	Entry deleted from font path.
[  1525.774] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  1525.774] 	Entry deleted from font path.
[  1525.774] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  1525.774] 	Entry deleted from font path.
[  1525.774] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1525.774] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1525.774] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1525.774] (II) Loader magic: 0x7e0220
[  1525.774] (II) Module ABI versions:
[  1525.774] 	X.Org ANSI C Emulation: 0.4
[  1525.774] 	X.Org Video Driver: 10.0
[  1525.774] 	X.Org XInput driver : 12.3
[  1525.774] 	X.Org Server Extension : 5.0
[  1525.774] (--) PCI:*(0:0:2:0) 8086:0116:1028:0504 rev 9, Mem @ 0xf6800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[  1525.775] (II) Open ACPI successful (/var/run/acpid.socket)
[  1525.775] (II) LoadModule: "extmod"
[  1525.775] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1525.775] (II) Module extmod: vendor="X.Org Foundation"
[  1525.775] 	compiled for 1.10.4, module version = 1.0.0
[  1525.775] 	Module class: X.Org Server Extension
[  1525.775] 	ABI class: X.Org Server Extension, version 5.0
[  1525.775] (II) Loading extension MIT-SCREEN-SAVER
[  1525.775] (II) Loading extension XFree86-VidModeExtension
[  1525.775] (II) Loading extension XFree86-DGA
[  1525.775] (II) Loading extension DPMS
[  1525.775] (II) Loading extension XVideo
[  1525.775] (II) Loading extension XVideo-MotionCompensation
[  1525.775] (II) Loading extension X-Resource
[  1525.775] (II) LoadModule: "dbe"
[  1525.775] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1525.775] (II) Module dbe: vendor="X.Org Foundation"
[  1525.775] 	compiled for 1.10.4, module version = 1.0.0
[  1525.775] 	Module class: X.Org Server Extension
[  1525.775] 	ABI class: X.Org Server Extension, version 5.0
[  1525.775] (II) Loading extension DOUBLE-BUFFER
[  1525.775] (II) LoadModule: "glx"
[  1525.775] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1525.776] (II) Module glx: vendor="X.Org Foundation"
[  1525.776] 	compiled for 1.10.4, module version = 1.0.0
[  1525.776] 	ABI class: X.Org Server Extension, version 5.0
[  1525.776] (==) AIGLX enabled
[  1525.776] (II) Loading extension GLX
[  1525.776] (II) LoadModule: "record"
[  1525.776] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1525.776] (II) Module record: vendor="X.Org Foundation"
[  1525.776] 	compiled for 1.10.4, module version = 1.13.0
[  1525.776] 	Module class: X.Org Server Extension
[  1525.776] 	ABI class: X.Org Server Extension, version 5.0
[  1525.776] (II) Loading extension RECORD
[  1525.776] (II) LoadModule: "dri"
[  1525.776] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1525.776] (II) Module dri: vendor="X.Org Foundation"
[  1525.776] 	compiled for 1.10.4, module version = 1.0.0
[  1525.776] 	ABI class: X.Org Server Extension, version 5.0
[  1525.776] (II) Loading extension XFree86-DRI
[  1525.776] (II) LoadModule: "dri2"
[  1525.776] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1525.776] (II) Module dri2: vendor="X.Org Foundation"
[  1525.776] 	compiled for 1.10.4, module version = 1.2.0
[  1525.776] 	ABI class: X.Org Server Extension, version 5.0
[  1525.776] (II) Loading extension DRI2
[  1525.776] (==) Matched intel as autoconfigured driver 0
[  1525.776] (==) Matched vesa as autoconfigured driver 1
[  1525.776] (==) Matched fbdev as autoconfigured driver 2
[  1525.776] (==) Assigned the driver to the xf86ConfigLayout
[  1525.776] (II) LoadModule: "intel"
[  1525.776] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1525.777] (II) Module intel: vendor="X.Org Foundation"
[  1525.777] 	compiled for 1.10.4, module version = 2.15.901
[  1525.777] 	Module class: X.Org Video Driver
[  1525.777] 	ABI class: X.Org Video Driver, version 10.0
[  1525.777] (II) LoadModule: "vesa"
[  1525.777] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1525.825] (II) Module vesa: vendor="X.Org Foundation"
[  1525.825] 	compiled for 1.10.2, module version = 2.3.0
[  1525.825] 	Module class: X.Org Video Driver
[  1525.825] 	ABI class: X.Org Video Driver, version 10.0
[  1525.825] (II) LoadModule: "fbdev"
[  1525.825] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1525.874] (II) Module fbdev: vendor="X.Org Foundation"
[  1525.874] 	compiled for 1.10.0, module version = 0.4.2
[  1525.874] 	ABI class: X.Org Video Driver, version 10.0
[  1525.874] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[  1525.875] (II) VESA: driver for VESA chipsets: vesa
[  1525.875] (II) FBDEV: driver for framebuffer: fbdev
[  1525.875] (++) using VT number 7

[  1525.875] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[  1526.160] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1526.161] (WW) Falling back to old probe method for fbdev
[  1526.161] (II) Loading sub module "fbdevhw"
[  1526.161] (II) LoadModule: "fbdevhw"
[  1526.161] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1526.161] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1526.161] 	compiled for 1.10.4, module version = 0.0.2
[  1526.161] 	ABI class: X.Org Video Driver, version 10.0
[  1526.161] (EE) open /dev/fb0: No such file or directory
[  1526.161] (II) Loading sub module "vbe"
[  1526.161] (II) LoadModule: "vbe"
[  1526.161] (II) Loading /usr/lib/xorg/modules/libvbe.so
[  1526.161] (II) Module vbe: vendor="X.Org Foundation"
[  1526.161] 	compiled for 1.10.4, module version = 1.1.0
[  1526.161] 	ABI class: X.Org Video Driver, version 10.0
[  1526.161] (II) Loading sub module "int10"
[  1526.161] (II) LoadModule: "int10"
[  1526.161] (II) Loading /usr/lib/xorg/modules/libint10.so
[  1526.161] (II) Module int10: vendor="X.Org Foundation"
[  1526.161] 	compiled for 1.10.4, module version = 1.0.0
[  1526.161] 	ABI class: X.Org Video Driver, version 10.0
[  1526.161] (II) VESA(0): initializing int10
[  1526.161] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[  1526.161] (II) VESA(0): VESA BIOS detected
[  1526.161] (II) VESA(0): VESA VBE Version 3.0
[  1526.161] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[  1526.161] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
[  1526.161] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[  1526.161] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[  1526.161] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
[  1526.161] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[  1526.166] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1526.166] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[  1526.166] (==) VESA(0): RGB weight 888
[  1526.166] (==) VESA(0): Default visual is TrueColor
[  1526.166] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[  1526.166] (II) Loading sub module "ddc"
[  1526.166] (II) LoadModule: "ddc"
[  1526.166] (II) Module "ddc" already built-in
[  1526.166] (II) VESA(0): VESA VBE DDC supported
[  1526.166] (II) VESA(0): VESA VBE DDC Level 2
[  1526.166] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[  1526.178] (II) VESA(0): VESA VBE DDC read successfully
[  1526.178] (II) VESA(0): Manufacturer: SEC  Model: 5441  Serial#: 0
[  1526.178] (II) VESA(0): Year: 2010  Week: 0
[  1526.178] (II) VESA(0): EDID Version: 1.4
[  1526.178] (II) VESA(0): Digital Display Input
[  1526.178] (II) VESA(0): 6 bits per channel
[  1526.178] (II) VESA(0): Digital interface is undefined
[  1526.178] (II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[  1526.178] (II) VESA(0): Gamma: 2.20
[  1526.178] (II) VESA(0): No DPMS capabilities specified
[  1526.178] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  1526.178] (II) VESA(0): First detailed timing is preferred mode
[  1526.178] (II) VESA(0): Preferred mode is native pixel format and refresh rate
[  1526.178] (II) VESA(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[  1526.178] (II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[  1526.178] (II) VESA(0): Manufacturer's mask: 0
[  1526.178] (II) VESA(0): Supported detailed timing:
[  1526.178] (II) VESA(0): clock: 76.7 MHz   Image Size:  344 x 194 mm
[  1526.178] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1618 h_border: 0
[  1526.178] (II) VESA(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[  1526.178] (II) VESA(0): Supported detailed timing:
[  1526.178] (II) VESA(0): clock: 48.2 MHz   Image Size:  344 x 194 mm
[  1526.178] (II) VESA(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
[  1526.178] (II) VESA(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
[  1526.178] (II) VESA(0):  4Y4GM€156AT
[  1526.178] (II) VESA(0): Unknown vendor-specific block 0
[  1526.178] (II) VESA(0): EDID (in hex):
[  1526.178] (II) VESA(0): 	00ffffffffffff004ca3415400000000
[  1526.178] (II) VESA(0): 	00140104902213780ac8959e57549226
[  1526.178] (II) VESA(0): 	0f505400000001010101010101010101
[  1526.178] (II) VESA(0): 	010101010101f51d56fc500016303020
[  1526.178] (II) VESA(0): 	250058c21000001ad61256a050001630
[  1526.178] (II) VESA(0): 	3020250058c21000001a000000fe0034
[  1526.178] (II) VESA(0): 	5934474d8031353641540a2000000000
[  1526.178] (II) VESA(0): 	00004101960000000001010a202000cf
[  1526.178] (II) VESA(0): EDID vendor "SEC", prod id 21569
[  1526.178] (II) VESA(0): Printing DDC gathered Modelines:
[  1526.178] (II) VESA(0): Modeline "1366x768"x0.0   76.69  1366 1414 1446 1618  768 770 775 790 +hsync -vsync (47.4 kHz)
[  1526.178] (II) VESA(0): Modeline "1366x768"x0.0   48.22  1366 1414 1446 1526  768 770 775 790 +hsync -vsync (31.6 kHz)
[  1526.178] (II) VESA(0): Searching for matching VESA mode(s):
[  1526.179] Mode: 160 (0x0)
[  1526.179] 	ModeAttributes: 0x0
[  1526.179] 	WinAAttributes: 0x0
[  1526.179] 	WinBAttributes: 0x0
[  1526.179] 	WinGranularity: 0
[  1526.179] 	WinSize: 0
[  1526.179] 	WinASegment: 0x0
[  1526.179] 	WinBSegment: 0x0
[  1526.179] 	WinFuncPtr: 0x0
[  1526.179] 	BytesPerScanline: 0
[  1526.179] 	XResolution: 0
[  1526.179] 	YResolution: 0
[  1526.179] 	XCharSize: 0
[  1526.179] 	YCharSize: 0
[  1526.179] 	NumberOfPlanes: 0
[  1526.179] 	BitsPerPixel: 0
[  1526.179] 	NumberOfBanks: 0
[  1526.179] 	MemoryModel: 0
[  1526.179] 	BankSize: 0
[  1526.179] 	NumberOfImages: 0
[  1526.179] 	RedMaskSize: 0
[  1526.179] 	RedFieldPosition: 0
[  1526.179] 	GreenMaskSize: 0
[  1526.179] 	GreenFieldPosition: 0
[  1526.179] 	BlueMaskSize: 0
[  1526.179] 	BlueFieldPosition: 0
[  1526.179] 	RsvdMaskSize: 0
[  1526.179] 	RsvdFieldPosition: 0
[  1526.179] 	DirectColorModeInfo: 0
[  1526.179] 	PhysBasePtr: 0x0
[  1526.179] 	LinBytesPerScanLine: 0
[  1526.179] 	BnkNumberOfImagePages: 0
[  1526.179] 	LinNumberOfImagePages: 0
[  1526.179] 	LinRedMaskSize: 0
[  1526.179] 	LinRedFieldPosition: 0
[  1526.179] 	LinGreenMaskSize: 0
[  1526.179] 	LinGreenFieldPosition: 0
[  1526.179] 	LinBlueMaskSize: 0
[  1526.179] 	LinBlueFieldPosition: 0
[  1526.179] 	LinRsvdMaskSize: 0
[  1526.179] 	LinRsvdFieldPosition: 0
[  1526.179] 	MaxPixelClock: 0
[  1526.179] Mode: 161 (0x0)
[  1526.179] 	ModeAttributes: 0x0
[  1526.179] 	WinAAttributes: 0x0
[  1526.179] 	WinBAttributes: 0x0
[  1526.179] 	WinGranularity: 0
[  1526.179] 	WinSize: 0
[  1526.179] 	WinASegment: 0x0
[  1526.179] 	WinBSegment: 0x0
[  1526.179] 	WinFuncPtr: 0x0
[  1526.179] 	BytesPerScanline: 0
[  1526.179] 	XResolution: 0
[  1526.179] 	YResolution: 0
[  1526.179] 	XCharSize: 0
[  1526.179] 	YCharSize: 0
[  1526.179] 	NumberOfPlanes: 0
[  1526.179] 	BitsPerPixel: 0
[  1526.179] 	NumberOfBanks: 0
[  1526.179] 	MemoryModel: 0
[  1526.179] 	BankSize: 0
[  1526.179] 	NumberOfImages: 0
[  1526.179] 	RedMaskSize: 0
[  1526.179] 	RedFieldPosition: 0
[  1526.179] 	GreenMaskSize: 0
[  1526.179] 	GreenFieldPosition: 0
[  1526.179] 	BlueMaskSize: 0
[  1526.179] 	BlueFieldPosition: 0
[  1526.179] 	RsvdMaskSize: 0
[  1526.179] 	RsvdFieldPosition: 0
[  1526.179] 	DirectColorModeInfo: 0
[  1526.179] 	PhysBasePtr: 0x0
[  1526.179] 	LinBytesPerScanLine: 0
[  1526.179] 	BnkNumberOfImagePages: 0
[  1526.179] 	LinNumberOfImagePages: 0
[  1526.179] 	LinRedMaskSize: 0
[  1526.179] 	LinRedFieldPosition: 0
[  1526.179] 	LinGreenMaskSize: 0
[  1526.179] 	LinGreenFieldPosition: 0
[  1526.179] 	LinBlueMaskSize: 0
[  1526.179] 	LinBlueFieldPosition: 0
[  1526.179] 	LinRsvdMaskSize: 0
[  1526.179] 	LinRsvdFieldPosition: 0
[  1526.179] 	MaxPixelClock: 0
[  1526.179] Mode: 162 (0x0)
[  1526.179] 	ModeAttributes: 0x0
[  1526.179] 	WinAAttributes: 0x0
[  1526.179] 	WinBAttributes: 0x0
[  1526.179] 	WinGranularity: 0
[  1526.179] 	WinSize: 0
[  1526.179] 	WinASegment: 0x0
[  1526.179] 	WinBSegment: 0x0
[  1526.179] 	WinFuncPtr: 0x0
[  1526.179] 	BytesPerScanline: 0
[  1526.179] 	XResolution: 0
[  1526.179] 	YResolution: 0
[  1526.179] 	XCharSize: 0
[  1526.179] 	YCharSize: 0
[  1526.179] 	NumberOfPlanes: 0
[  1526.179] 	BitsPerPixel: 0
[  1526.179] 	NumberOfBanks: 0
[  1526.179] 	MemoryModel: 0
[  1526.179] 	BankSize: 0
[  1526.179] 	NumberOfImages: 0
[  1526.179] 	RedMaskSize: 0
[  1526.179] 	RedFieldPosition: 0
[  1526.179] 	GreenMaskSize: 0
[  1526.179] 	GreenFieldPosition: 0
[  1526.179] 	BlueMaskSize: 0
[  1526.179] 	BlueFieldPosition: 0
[  1526.179] 	RsvdMaskSize: 0
[  1526.179] 	RsvdFieldPosition: 0
[  1526.179] 	DirectColorModeInfo: 0
[  1526.179] 	PhysBasePtr: 0x0
[  1526.179] 	LinBytesPerScanLine: 0
[  1526.179] 	BnkNumberOfImagePages: 0
[  1526.179] 	LinNumberOfImagePages: 0
[  1526.179] 	LinRedMaskSize: 0
[  1526.179] 	LinRedFieldPosition: 0
[  1526.179] 	LinGreenMaskSize: 0
[  1526.179] 	LinGreenFieldPosition: 0
[  1526.179] 	LinBlueMaskSize: 0
[  1526.179] 	LinBlueFieldPosition: 0
[  1526.179] 	LinRsvdMaskSize: 0
[  1526.179] 	LinRsvdFieldPosition: 0
[  1526.179] 	MaxPixelClock: 0
[  1526.179] Mode: 163 (0x0)
[  1526.179] 	ModeAttributes: 0x0
[  1526.179] 	WinAAttributes: 0x0
[  1526.179] 	WinBAttributes: 0x0
[  1526.179] 	WinGranularity: 0
[  1526.179] 	WinSize: 0
[  1526.179] 	WinASegment: 0x0
[  1526.179] 	WinBSegment: 0x0
[  1526.179] 	WinFuncPtr: 0x0
[  1526.179] 	BytesPerScanline: 0
[  1526.179] 	XResolution: 0
[  1526.179] 	YResolution: 0
[  1526.179] 	XCharSize: 0
[  1526.179] 	YCharSize: 0
[  1526.179] 	NumberOfPlanes: 0
[  1526.179] 	BitsPerPixel: 0
[  1526.179] 	NumberOfBanks: 0
[  1526.179] 	MemoryModel: 0
[  1526.179] 	BankSize: 0
[  1526.179] 	NumberOfImages: 0
[  1526.179] 	RedMaskSize: 0
[  1526.179] 	RedFieldPosition: 0
[  1526.179] 	GreenMaskSize: 0
[  1526.179] 	GreenFieldPosition: 0
[  1526.179] 	BlueMaskSize: 0
[  1526.179] 	BlueFieldPosition: 0
[  1526.179] 	RsvdMaskSize: 0
[  1526.179] 	RsvdFieldPosition: 0
[  1526.179] 	DirectColorModeInfo: 0
[  1526.179] 	PhysBasePtr: 0x0
[  1526.179] 	LinBytesPerScanLine: 0
[  1526.179] 	BnkNumberOfImagePages: 0
[  1526.179] 	LinNumberOfImagePages: 0
[  1526.179] 	LinRedMaskSize: 0
[  1526.179] 	LinRedFieldPosition: 0
[  1526.179] 	LinGreenMaskSize: 0
[  1526.179] 	LinGreenFieldPosition: 0
[  1526.179] 	LinBlueMaskSize: 0
[  1526.179] 	LinBlueFieldPosition: 0
[  1526.179] 	LinRsvdMaskSize: 0
[  1526.179] 	LinRsvdFieldPosition: 0
[  1526.179] 	MaxPixelClock: 0
[  1526.179] Mode: 164 (0x0)
[  1526.179] 	ModeAttributes: 0x0
[  1526.179] 	WinAAttributes: 0x0
[  1526.179] 	WinBAttributes: 0x0
[  1526.179] 	WinGranularity: 0
[  1526.179] 	WinSize: 0
[  1526.179] 	WinASegment: 0x0
[  1526.180] 	WinBSegment: 0x0
[  1526.180] 	WinFuncPtr: 0x0
[  1526.180] 	BytesPerScanline: 0
[  1526.180] 	XResolution: 0
[  1526.180] 	YResolution: 0
[  1526.180] 	XCharSize: 0
[  1526.180] 	YCharSize: 0
[  1526.180] 	NumberOfPlanes: 0
[  1526.180] 	BitsPerPixel: 0
[  1526.180] 	NumberOfBanks: 0
[  1526.180] 	MemoryModel: 0
[  1526.180] 	BankSize: 0
[  1526.180] 	NumberOfImages: 0
[  1526.180] 	RedMaskSize: 0
[  1526.180] 	RedFieldPosition: 0
[  1526.180] 	GreenMaskSize: 0
[  1526.180] 	GreenFieldPosition: 0
[  1526.180] 	BlueMaskSize: 0
[  1526.180] 	BlueFieldPosition: 0
[  1526.180] 	RsvdMaskSize: 0
[  1526.180] 	RsvdFieldPosition: 0
[  1526.180] 	DirectColorModeInfo: 0
[  1526.180] 	PhysBasePtr: 0x0
[  1526.180] 	LinBytesPerScanLine: 0
[  1526.180] 	BnkNumberOfImagePages: 0
[  1526.180] 	LinNumberOfImagePages: 0
[  1526.180] 	LinRedMaskSize: 0
[  1526.180] 	LinRedFieldPosition: 0
[  1526.180] 	LinGreenMaskSize: 0
[  1526.180] 	LinGreenFieldPosition: 0
[  1526.180] 	LinBlueMaskSize: 0
[  1526.180] 	LinBlueFieldPosition: 0
[  1526.180] 	LinRsvdMaskSize: 0
[  1526.180] 	LinRsvdFieldPosition: 0
[  1526.180] 	MaxPixelClock: 0
[  1526.180] Mode: 165 (0x0)
[  1526.180] 	ModeAttributes: 0x0
[  1526.180] 	WinAAttributes: 0x0
[  1526.180] 	WinBAttributes: 0x0
[  1526.180] 	WinGranularity: 0
[  1526.180] 	WinSize: 0
[  1526.180] 	WinASegment: 0x0
[  1526.180] 	WinBSegment: 0x0
[  1526.180] 	WinFuncPtr: 0x0
[  1526.180] 	BytesPerScanline: 0
[  1526.180] 	XResolution: 0
[  1526.180] 	YResolution: 0
[  1526.180] 	XCharSize: 0
[  1526.180] 	YCharSize: 0
[  1526.180] 	NumberOfPlanes: 0
[  1526.180] 	BitsPerPixel: 0
[  1526.180] 	NumberOfBanks: 0
[  1526.180] 	MemoryModel: 0
[  1526.180] 	BankSize: 0
[  1526.180] 	NumberOfImages: 0
[  1526.180] 	RedMaskSize: 0
[  1526.180] 	RedFieldPosition: 0
[  1526.180] 	GreenMaskSize: 0
[  1526.180] 	GreenFieldPosition: 0
[  1526.180] 	BlueMaskSize: 0
[  1526.180] 	BlueFieldPosition: 0
[  1526.180] 	RsvdMaskSize: 0
[  1526.180] 	RsvdFieldPosition: 0
[  1526.180] 	DirectColorModeInfo: 0
[  1526.180] 	PhysBasePtr: 0x0
[  1526.180] 	LinBytesPerScanLine: 0
[  1526.180] 	BnkNumberOfImagePages: 0
[  1526.180] 	LinNumberOfImagePages: 0
[  1526.180] 	LinRedMaskSize: 0
[  1526.180] 	LinRedFieldPosition: 0
[  1526.180] 	LinGreenMaskSize: 0
[  1526.180] 	LinGreenFieldPosition: 0
[  1526.180] 	LinBlueMaskSize: 0
[  1526.180] 	LinBlueFieldPosition: 0
[  1526.180] 	LinRsvdMaskSize: 0
[  1526.180] 	LinRsvdFieldPosition: 0
[  1526.180] 	MaxPixelClock: 0
[  1526.180] Mode: 166 (0x0)
[  1526.180] 	ModeAttributes: 0x0
[  1526.180] 	WinAAttributes: 0x0
[  1526.180] 	WinBAttributes: 0x0
[  1526.180] 	WinGranularity: 0
[  1526.180] 	WinSize: 0
[  1526.180] 	WinASegment: 0x0
[  1526.180] 	WinBSegment: 0x0
[  1526.180] 	WinFuncPtr: 0x0
[  1526.180] 	BytesPerScanline: 0
[  1526.180] 	XResolution: 0
[  1526.180] 	YResolution: 0
[  1526.180] 	XCharSize: 0
[  1526.180] 	YCharSize: 0
[  1526.180] 	NumberOfPlanes: 0
[  1526.180] 	BitsPerPixel: 0
[  1526.180] 	NumberOfBanks: 0
[  1526.180] 	MemoryModel: 0
[  1526.180] 	BankSize: 0
[  1526.180] 	NumberOfImages: 0
[  1526.180] 	RedMaskSize: 0
[  1526.180] 	RedFieldPosition: 0
[  1526.180] 	GreenMaskSize: 0
[  1526.180] 	GreenFieldPosition: 0
[  1526.180] 	BlueMaskSize: 0
[  1526.180] 	BlueFieldPosition: 0
[  1526.180] 	RsvdMaskSize: 0
[  1526.180] 	RsvdFieldPosition: 0
[  1526.180] 	DirectColorModeInfo: 0
[  1526.180] 	PhysBasePtr: 0x0
[  1526.180] 	LinBytesPerScanLine: 0
[  1526.180] 	BnkNumberOfImagePages: 0
[  1526.180] 	LinNumberOfImagePages: 0
[  1526.180] 	LinRedMaskSize: 0
[  1526.180] 	LinRedFieldPosition: 0
[  1526.180] 	LinGreenMaskSize: 0
[  1526.180] 	LinGreenFieldPosition: 0
[  1526.180] 	LinBlueMaskSize: 0
[  1526.180] 	LinBlueFieldPosition: 0
[  1526.180] 	LinRsvdMaskSize: 0
[  1526.180] 	LinRsvdFieldPosition: 0
[  1526.180] 	MaxPixelClock: 0
[  1526.180] Mode: 167 (0x0)
[  1526.180] 	ModeAttributes: 0x0
[  1526.180] 	WinAAttributes: 0x0
[  1526.180] 	WinBAttributes: 0x0
[  1526.180] 	WinGranularity: 0
[  1526.180] 	WinSize: 0
[  1526.180] 	WinASegment: 0x0
[  1526.180] 	WinBSegment: 0x0
[  1526.180] 	WinFuncPtr: 0x0
[  1526.180] 	BytesPerScanline: 0
[  1526.180] 	XResolution: 0
[  1526.180] 	YResolution: 0
[  1526.180] 	XCharSize: 0
[  1526.180] 	YCharSize: 0
[  1526.180] 	NumberOfPlanes: 0
[  1526.180] 	BitsPerPixel: 0
[  1526.180] 	NumberOfBanks: 0
[  1526.180] 	MemoryModel: 0
[  1526.180] 	BankSize: 0
[  1526.180] 	NumberOfImages: 0
[  1526.180] 	RedMaskSize: 0
[  1526.180] 	RedFieldPosition: 0
[  1526.180] 	GreenMaskSize: 0
[  1526.180] 	GreenFieldPosition: 0
[  1526.180] 	BlueMaskSize: 0
[  1526.180] 	BlueFieldPosition: 0
[  1526.180] 	RsvdMaskSize: 0
[  1526.180] 	RsvdFieldPosition: 0
[  1526.180] 	DirectColorModeInfo: 0
[  1526.180] 	PhysBasePtr: 0x0
[  1526.180] 	LinBytesPerScanLine: 0
[  1526.180] 	BnkNumberOfImagePages: 0
[  1526.180] 	LinNumberOfImagePages: 0
[  1526.180] 	LinRedMaskSize: 0
[  1526.180] 	LinRedFieldPosition: 0
[  1526.180] 	LinGreenMaskSize: 0
[  1526.180] 	LinGreenFieldPosition: 0
[  1526.180] 	LinBlueMaskSize: 0
[  1526.180] 	LinBlueFieldPosition: 0
[  1526.180] 	LinRsvdMaskSize: 0
[  1526.180] 	LinRsvdFieldPosition: 0
[  1526.180] 	MaxPixelClock: 0
[  1526.180] Mode: 168 (0x0)
[  1526.180] 	ModeAttributes: 0x0
[  1526.180] 	WinAAttributes: 0x0
[  1526.180] 	WinBAttributes: 0x0
[  1526.180] 	WinGranularity: 0
[  1526.180] 	WinSize: 0
[  1526.180] 	WinASegment: 0x0
[  1526.180] 	WinBSegment: 0x0
[  1526.180] 	WinFuncPtr: 0x0
[  1526.180] 	BytesPerScanline: 0
[  1526.180] 	XResolution: 0
[  1526.180] 	YResolution: 0
[  1526.180] 	XCharSize: 0
[  1526.180] 	YCharSize: 0
[  1526.180] 	NumberOfPlanes: 0
[  1526.180] 	BitsPerPixel: 0
[  1526.180] 	NumberOfBanks: 0
[  1526.180] 	MemoryModel: 0
[  1526.180] 	BankSize: 0
[  1526.180] 	NumberOfImages: 0
[  1526.180] 	RedMaskSize: 0
[  1526.180] 	RedFieldPosition: 0
[  1526.180] 	GreenMaskSize: 0
[  1526.180] 	GreenFieldPosition: 0
[  1526.180] 	BlueMaskSize: 0
[  1526.180] 	BlueFieldPosition: 0
[  1526.180] 	RsvdMaskSize: 0
[  1526.181] 	RsvdFieldPosition: 0
[  1526.181] 	DirectColorModeInfo: 0
[  1526.181] 	PhysBasePtr: 0x0
[  1526.181] 	LinBytesPerScanLine: 0
[  1526.181] 	BnkNumberOfImagePages: 0
[  1526.181] 	LinNumberOfImagePages: 0
[  1526.181] 	LinRedMaskSize: 0
[  1526.181] 	LinRedFieldPosition: 0
[  1526.181] 	LinGreenMaskSize: 0
[  1526.181] 	LinGreenFieldPosition: 0
[  1526.181] 	LinBlueMaskSize: 0
[  1526.181] 	LinBlueFieldPosition: 0
[  1526.181] 	LinRsvdMaskSize: 0
[  1526.181] 	LinRsvdFieldPosition: 0
[  1526.181] 	MaxPixelClock: 0
[  1526.181] Mode: 169 (0x0)
[  1526.181] 	ModeAttributes: 0x0
[  1526.181] 	WinAAttributes: 0x0
[  1526.181] 	WinBAttributes: 0x0
[  1526.181] 	WinGranularity: 0
[  1526.181] 	WinSize: 0
[  1526.181] 	WinASegment: 0x0
[  1526.181] 	WinBSegment: 0x0
[  1526.181] 	WinFuncPtr: 0x0
[  1526.181] 	BytesPerScanline: 0
[  1526.181] 	XResolution: 0
[  1526.181] 	YResolution: 0
[  1526.181] 	XCharSize: 0
[  1526.181] 	YCharSize: 0
[  1526.181] 	NumberOfPlanes: 0
[  1526.181] 	BitsPerPixel: 0
[  1526.181] 	NumberOfBanks: 0
[  1526.181] 	MemoryModel: 0
[  1526.181] 	BankSize: 0
[  1526.181] 	NumberOfImages: 0
[  1526.181] 	RedMaskSize: 0
[  1526.181] 	RedFieldPosition: 0
[  1526.181] 	GreenMaskSize: 0
[  1526.181] 	GreenFieldPosition: 0
[  1526.181] 	BlueMaskSize: 0
[  1526.181] 	BlueFieldPosition: 0
[  1526.181] 	RsvdMaskSize: 0
[  1526.181] 	RsvdFieldPosition: 0
[  1526.181] 	DirectColorModeInfo: 0
[  1526.181] 	PhysBasePtr: 0x0
[  1526.181] 	LinBytesPerScanLine: 0
[  1526.181] 	BnkNumberOfImagePages: 0
[  1526.181] 	LinNumberOfImagePages: 0
[  1526.181] 	LinRedMaskSize: 0
[  1526.181] 	LinRedFieldPosition: 0
[  1526.181] 	LinGreenMaskSize: 0
[  1526.181] 	LinGreenFieldPosition: 0
[  1526.181] 	LinBlueMaskSize: 0
[  1526.181] 	LinBlueFieldPosition: 0
[  1526.181] 	LinRsvdMaskSize: 0
[  1526.181] 	LinRsvdFieldPosition: 0
[  1526.181] 	MaxPixelClock: 0
[  1526.181] Mode: 16a (0x0)
[  1526.181] 	ModeAttributes: 0x0
[  1526.181] 	WinAAttributes: 0x0
[  1526.181] 	WinBAttributes: 0x0
[  1526.181] 	WinGranularity: 0
[  1526.181] 	WinSize: 0
[  1526.181] 	WinASegment: 0x0
[  1526.181] 	WinBSegment: 0x0
[  1526.181] 	WinFuncPtr: 0x0
[  1526.181] 	BytesPerScanline: 0
[  1526.181] 	XResolution: 0
[  1526.181] 	YResolution: 0
[  1526.181] 	XCharSize: 0
[  1526.181] 	YCharSize: 0
[  1526.181] 	NumberOfPlanes: 0
[  1526.181] 	BitsPerPixel: 0
[  1526.181] 	NumberOfBanks: 0
[  1526.181] 	MemoryModel: 0
[  1526.181] 	BankSize: 0
[  1526.181] 	NumberOfImages: 0
[  1526.181] 	RedMaskSize: 0
[  1526.181] 	RedFieldPosition: 0
[  1526.181] 	GreenMaskSize: 0
[  1526.181] 	GreenFieldPosition: 0
[  1526.181] 	BlueMaskSize: 0
[  1526.181] 	BlueFieldPosition: 0
[  1526.181] 	RsvdMaskSize: 0
[  1526.181] 	RsvdFieldPosition: 0
[  1526.181] 	DirectColorModeInfo: 0
[  1526.181] 	PhysBasePtr: 0x0
[  1526.181] 	LinBytesPerScanLine: 0
[  1526.181] 	BnkNumberOfImagePages: 0
[  1526.181] 	LinNumberOfImagePages: 0
[  1526.181] 	LinRedMaskSize: 0
[  1526.181] 	LinRedFieldPosition: 0
[  1526.181] 	LinGreenMaskSize: 0
[  1526.181] 	LinGreenFieldPosition: 0
[  1526.181] 	LinBlueMaskSize: 0
[  1526.181] 	LinBlueFieldPosition: 0
[  1526.181] 	LinRsvdMaskSize: 0
[  1526.181] 	LinRsvdFieldPosition: 0
[  1526.181] 	MaxPixelClock: 0
[  1526.181] Mode: 16b (0x0)
[  1526.181] 	ModeAttributes: 0x0
[  1526.181] 	WinAAttributes: 0x0
[  1526.181] 	WinBAttributes: 0x0
[  1526.181] 	WinGranularity: 0
[  1526.181] 	WinSize: 0
[  1526.181] 	WinASegment: 0x0
[  1526.181] 	WinBSegment: 0x0
[  1526.181] 	WinFuncPtr: 0x0
[  1526.181] 	BytesPerScanline: 0
[  1526.181] 	XResolution: 0
[  1526.181] 	YResolution: 0
[  1526.181] 	XCharSize: 0
[  1526.181] 	YCharSize: 0
[  1526.181] 	NumberOfPlanes: 0
[  1526.181] 	BitsPerPixel: 0
[  1526.181] 	NumberOfBanks: 0
[  1526.181] 	MemoryModel: 0
[  1526.181] 	BankSize: 0
[  1526.181] 	NumberOfImages: 0
[  1526.181] 	RedMaskSize: 0
[  1526.181] 	RedFieldPosition: 0
[  1526.181] 	GreenMaskSize: 0
[  1526.181] 	GreenFieldPosition: 0
[  1526.181] 	BlueMaskSize: 0
[  1526.181] 	BlueFieldPosition: 0
[  1526.181] 	RsvdMaskSize: 0
[  1526.181] 	RsvdFieldPosition: 0
[  1526.181] 	DirectColorModeInfo: 0
[  1526.181] 	PhysBasePtr: 0x0
[  1526.181] 	LinBytesPerScanLine: 0
[  1526.181] 	BnkNumberOfImagePages: 0
[  1526.181] 	LinNumberOfImagePages: 0
[  1526.181] 	LinRedMaskSize: 0
[  1526.181] 	LinRedFieldPosition: 0
[  1526.181] 	LinGreenMaskSize: 0
[  1526.181] 	LinGreenFieldPosition: 0
[  1526.181] 	LinBlueMaskSize: 0
[  1526.181] 	LinBlueFieldPosition: 0
[  1526.181] 	LinRsvdMaskSize: 0
[  1526.181] 	LinRsvdFieldPosition: 0
[  1526.181] 	MaxPixelClock: 0
[  1526.181] Mode: 16c (0x0)
[  1526.181] 	ModeAttributes: 0x0
[  1526.181] 	WinAAttributes: 0x0
[  1526.181] 	WinBAttributes: 0x0
[  1526.181] 	WinGranularity: 0
[  1526.181] 	WinSize: 0
[  1526.181] 	WinASegment: 0x0
[  1526.181] 	WinBSegment: 0x0
[  1526.181] 	WinFuncPtr: 0x0
[  1526.181] 	BytesPerScanline: 0
[  1526.181] 	XResolution: 0
[  1526.181] 	YResolution: 0
[  1526.181] 	XCharSize: 0
[  1526.181] 	YCharSize: 0
[  1526.181] 	NumberOfPlanes: 0
[  1526.181] 	BitsPerPixel: 0
[  1526.181] 	NumberOfBanks: 0
[  1526.181] 	MemoryModel: 0
[  1526.181] 	BankSize: 0
[  1526.181] 	NumberOfImages: 0
[  1526.181] 	RedMaskSize: 0
[  1526.181] 	RedFieldPosition: 0
[  1526.181] 	GreenMaskSize: 0
[  1526.181] 	GreenFieldPosition: 0
[  1526.181] 	BlueMaskSize: 0
[  1526.181] 	BlueFieldPosition: 0
[  1526.181] 	RsvdMaskSize: 0
[  1526.181] 	RsvdFieldPosition: 0
[  1526.181] 	DirectColorModeInfo: 0
[  1526.181] 	PhysBasePtr: 0x0
[  1526.181] 	LinBytesPerScanLine: 0
[  1526.181] 	BnkNumberOfImagePages: 0
[  1526.181] 	LinNumberOfImagePages: 0
[  1526.181] 	LinRedMaskSize: 0
[  1526.181] 	LinRedFieldPosition: 0
[  1526.181] 	LinGreenMaskSize: 0
[  1526.181] 	LinGreenFieldPosition: 0
[  1526.181] 	LinBlueMaskSize: 0
[  1526.181] 	LinBlueFieldPosition: 0
[  1526.181] 	LinRsvdMaskSize: 0
[  1526.181] 	LinRsvdFieldPosition: 0
[  1526.181] 	MaxPixelClock: 0
[  1526.182] Mode: 16d (0x0)
[  1526.182] 	ModeAttributes: 0x0
[  1526.182] 	WinAAttributes: 0x0
[  1526.182] 	WinBAttributes: 0x0
[  1526.182] 	WinGranularity: 0
[  1526.182] 	WinSize: 0
[  1526.182] 	WinASegment: 0x0
[  1526.182] 	WinBSegment: 0x0
[  1526.182] 	WinFuncPtr: 0x0
[  1526.182] 	BytesPerScanline: 0
[  1526.182] 	XResolution: 0
[  1526.182] 	YResolution: 0
[  1526.182] 	XCharSize: 0
[  1526.182] 	YCharSize: 0
[  1526.182] 	NumberOfPlanes: 0
[  1526.182] 	BitsPerPixel: 0
[  1526.182] 	NumberOfBanks: 0
[  1526.182] 	MemoryModel: 0
[  1526.182] 	BankSize: 0
[  1526.182] 	NumberOfImages: 0
[  1526.182] 	RedMaskSize: 0
[  1526.182] 	RedFieldPosition: 0
[  1526.182] 	GreenMaskSize: 0
[  1526.182] 	GreenFieldPosition: 0
[  1526.182] 	BlueMaskSize: 0
[  1526.182] 	BlueFieldPosition: 0
[  1526.182] 	RsvdMaskSize: 0
[  1526.182] 	RsvdFieldPosition: 0
[  1526.182] 	DirectColorModeInfo: 0
[  1526.182] 	PhysBasePtr: 0x0
[  1526.182] 	LinBytesPerScanLine: 0
[  1526.182] 	BnkNumberOfImagePages: 0
[  1526.182] 	LinNumberOfImagePages: 0
[  1526.182] 	LinRedMaskSize: 0
[  1526.182] 	LinRedFieldPosition: 0
[  1526.182] 	LinGreenMaskSize: 0
[  1526.182] 	LinGreenFieldPosition: 0
[  1526.182] 	LinBlueMaskSize: 0
[  1526.182] 	LinBlueFieldPosition: 0
[  1526.182] 	LinRsvdMaskSize: 0
[  1526.182] 	LinRsvdFieldPosition: 0
[  1526.182] 	MaxPixelClock: 0
[  1526.182] Mode: 16e (0x0)
[  1526.182] 	ModeAttributes: 0x0
[  1526.182] 	WinAAttributes: 0x0
[  1526.182] 	WinBAttributes: 0x0
[  1526.182] 	WinGranularity: 0
[  1526.182] 	WinSize: 0
[  1526.182] 	WinASegment: 0x0
[  1526.182] 	WinBSegment: 0x0
[  1526.182] 	WinFuncPtr: 0x0
[  1526.182] 	BytesPerScanline: 0
[  1526.182] 	XResolution: 0
[  1526.182] 	YResolution: 0
[  1526.182] 	XCharSize: 0
[  1526.182] 	YCharSize: 0
[  1526.182] 	NumberOfPlanes: 0
[  1526.182] 	BitsPerPixel: 0
[  1526.182] 	NumberOfBanks: 0
[  1526.182] 	MemoryModel: 0
[  1526.182] 	BankSize: 0
[  1526.182] 	NumberOfImages: 0
[  1526.182] 	RedMaskSize: 0
[  1526.182] 	RedFieldPosition: 0
[  1526.182] 	GreenMaskSize: 0
[  1526.182] 	GreenFieldPosition: 0
[  1526.182] 	BlueMaskSize: 0
[  1526.182] 	BlueFieldPosition: 0
[  1526.182] 	RsvdMaskSize: 0
[  1526.182] 	RsvdFieldPosition: 0
[  1526.182] 	DirectColorModeInfo: 0
[  1526.182] 	PhysBasePtr: 0x0
[  1526.182] 	LinBytesPerScanLine: 0
[  1526.182] 	BnkNumberOfImagePages: 0
[  1526.182] 	LinNumberOfImagePages: 0
[  1526.182] 	LinRedMaskSize: 0
[  1526.182] 	LinRedFieldPosition: 0
[  1526.182] 	LinGreenMaskSize: 0
[  1526.182] 	LinGreenFieldPosition: 0
[  1526.182] 	LinBlueMaskSize: 0
[  1526.182] 	LinBlueFieldPosition: 0
[  1526.182] 	LinRsvdMaskSize: 0
[  1526.182] 	LinRsvdFieldPosition: 0
[  1526.182] 	MaxPixelClock: 0
[  1526.182] Mode: 16f (0x0)
[  1526.182] 	ModeAttributes: 0x0
[  1526.182] 	WinAAttributes: 0x0
[  1526.182] 	WinBAttributes: 0x0
[  1526.182] 	WinGranularity: 0
[  1526.182] 	WinSize: 0
[  1526.182] 	WinASegment: 0x0
[  1526.182] 	WinBSegment: 0x0
[  1526.182] 	WinFuncPtr: 0x0
[  1526.182] 	BytesPerScanline: 0
[  1526.182] 	XResolution: 0
[  1526.182] 	YResolution: 0
[  1526.182] 	XCharSize: 0
[  1526.182] 	YCharSize: 0
[  1526.182] 	NumberOfPlanes: 0
[  1526.182] 	BitsPerPixel: 0
[  1526.182] 	NumberOfBanks: 0
[  1526.182] 	MemoryModel: 0
[  1526.182] 	BankSize: 0
[  1526.182] 	NumberOfImages: 0
[  1526.182] 	RedMaskSize: 0
[  1526.182] 	RedFieldPosition: 0
[  1526.182] 	GreenMaskSize: 0
[  1526.182] 	GreenFieldPosition: 0
[  1526.182] 	BlueMaskSize: 0
[  1526.182] 	BlueFieldPosition: 0
[  1526.182] 	RsvdMaskSize: 0
[  1526.182] 	RsvdFieldPosition: 0
[  1526.182] 	DirectColorModeInfo: 0
[  1526.182] 	PhysBasePtr: 0x0
[  1526.182] 	LinBytesPerScanLine: 0
[  1526.182] 	BnkNumberOfImagePages: 0
[  1526.182] 	LinNumberOfImagePages: 0
[  1526.182] 	LinRedMaskSize: 0
[  1526.182] 	LinRedFieldPosition: 0
[  1526.182] 	LinGreenMaskSize: 0
[  1526.182] 	LinGreenFieldPosition: 0
[  1526.182] 	LinBlueMaskSize: 0
[  1526.182] 	LinBlueFieldPosition: 0
[  1526.182] 	LinRsvdMaskSize: 0
[  1526.182] 	LinRsvdFieldPosition: 0
[  1526.182] 	MaxPixelClock: 0
[  1526.182] Mode: 170 (0x0)
[  1526.182] 	ModeAttributes: 0x0
[  1526.182] 	WinAAttributes: 0x0
[  1526.182] 	WinBAttributes: 0x0
[  1526.182] 	WinGranularity: 0
[  1526.182] 	WinSize: 0
[  1526.182] 	WinASegment: 0x0
[  1526.182] 	WinBSegment: 0x0
[  1526.182] 	WinFuncPtr: 0x0
[  1526.182] 	BytesPerScanline: 0
[  1526.182] 	XResolution: 0
[  1526.182] 	YResolution: 0
[  1526.182] 	XCharSize: 0
[  1526.182] 	YCharSize: 0
[  1526.182] 	NumberOfPlanes: 0
[  1526.182] 	BitsPerPixel: 0
[  1526.182] 	NumberOfBanks: 0
[  1526.182] 	MemoryModel: 0
[  1526.182] 	BankSize: 0
[  1526.182] 	NumberOfImages: 0
[  1526.182] 	RedMaskSize: 0
[  1526.182] 	RedFieldPosition: 0
[  1526.182] 	GreenMaskSize: 0
[  1526.182] 	GreenFieldPosition: 0
[  1526.182] 	BlueMaskSize: 0
[  1526.182] 	BlueFieldPosition: 0
[  1526.182] 	RsvdMaskSize: 0
[  1526.182] 	RsvdFieldPosition: 0
[  1526.182] 	DirectColorModeInfo: 0
[  1526.182] 	PhysBasePtr: 0x0
[  1526.182] 	LinBytesPerScanLine: 0
[  1526.182] 	BnkNumberOfImagePages: 0
[  1526.182] 	LinNumberOfImagePages: 0
[  1526.182] 	LinRedMaskSize: 0
[  1526.182] 	LinRedFieldPosition: 0
[  1526.182] 	LinGreenMaskSize: 0
[  1526.182] 	LinGreenFieldPosition: 0
[  1526.182] 	LinBlueMaskSize: 0
[  1526.182] 	LinBlueFieldPosition: 0
[  1526.182] 	LinRsvdMaskSize: 0
[  1526.182] 	LinRsvdFieldPosition: 0
[  1526.182] 	MaxPixelClock: 0
[  1526.183] Mode: 171 (0x0)
[  1526.183] 	ModeAttributes: 0x0
[  1526.183] 	WinAAttributes: 0x0
[  1526.183] 	WinBAttributes: 0x0
[  1526.183] 	WinGranularity: 0
[  1526.183] 	WinSize: 0
[  1526.183] 	WinASegment: 0x0
[  1526.183] 	WinBSegment: 0x0
[  1526.183] 	WinFuncPtr: 0x0
[  1526.183] 	BytesPerScanline: 0
[  1526.183] 	XResolution: 0
[  1526.183] 	YResolution: 0
[  1526.183] 	XCharSize: 0
[  1526.183] 	YCharSize: 0
[  1526.183] 	NumberOfPlanes: 0
[  1526.183] 	BitsPerPixel: 0
[  1526.183] 	NumberOfBanks: 0
[  1526.183] 	MemoryModel: 0
[  1526.183] 	BankSize: 0
[  1526.183] 	NumberOfImages: 0
[  1526.183] 	RedMaskSize: 0
[  1526.183] 	RedFieldPosition: 0
[  1526.183] 	GreenMaskSize: 0
[  1526.183] 	GreenFieldPosition: 0
[  1526.183] 	BlueMaskSize: 0
[  1526.183] 	BlueFieldPosition: 0
[  1526.183] 	RsvdMaskSize: 0
[  1526.183] 	RsvdFieldPosition: 0
[  1526.183] 	DirectColorModeInfo: 0
[  1526.183] 	PhysBasePtr: 0x0
[  1526.183] 	LinBytesPerScanLine: 0
[  1526.183] 	BnkNumberOfImagePages: 0
[  1526.183] 	LinNumberOfImagePages: 0
[  1526.183] 	LinRedMaskSize: 0
[  1526.183] 	LinRedFieldPosition: 0
[  1526.183] 	LinGreenMaskSize: 0
[  1526.183] 	LinGreenFieldPosition: 0
[  1526.183] 	LinBlueMaskSize: 0
[  1526.183] 	LinBlueFieldPosition: 0
[  1526.183] 	LinRsvdMaskSize: 0
[  1526.183] 	LinRsvdFieldPosition: 0
[  1526.183] 	MaxPixelClock: 0
[  1526.183] Mode: 13c (0x0)
[  1526.183] 	ModeAttributes: 0x0
[  1526.183] 	WinAAttributes: 0x0
[  1526.183] 	WinBAttributes: 0x0
[  1526.183] 	WinGranularity: 0
[  1526.183] 	WinSize: 0
[  1526.183] 	WinASegment: 0x0
[  1526.183] 	WinBSegment: 0x0
[  1526.183] 	WinFuncPtr: 0x0
[  1526.183] 	BytesPerScanline: 0
[  1526.183] 	XResolution: 0
[  1526.183] 	YResolution: 0
[  1526.183] 	XCharSize: 0
[  1526.183] 	YCharSize: 0
[  1526.183] 	NumberOfPlanes: 0
[  1526.183] 	BitsPerPixel: 0
[  1526.183] 	NumberOfBanks: 0
[  1526.183] 	MemoryModel: 0
[  1526.183] 	BankSize: 0
[  1526.183] 	NumberOfImages: 0
[  1526.183] 	RedMaskSize: 0
[  1526.183] 	RedFieldPosition: 0
[  1526.183] 	GreenMaskSize: 0
[  1526.183] 	GreenFieldPosition: 0
[  1526.183] 	BlueMaskSize: 0
[  1526.183] 	BlueFieldPosition: 0
[  1526.183] 	RsvdMaskSize: 0
[  1526.183] 	RsvdFieldPosition: 0
[  1526.183] 	DirectColorModeInfo: 0
[  1526.183] 	PhysBasePtr: 0x0
[  1526.183] 	LinBytesPerScanLine: 0
[  1526.183] 	BnkNumberOfImagePages: 0
[  1526.183] 	LinNumberOfImagePages: 0
[  1526.183] 	LinRedMaskSize: 0
[  1526.183] 	LinRedFieldPosition: 0
[  1526.183] 	LinGreenMaskSize: 0
[  1526.183] 	LinGreenFieldPosition: 0
[  1526.183] 	LinBlueMaskSize: 0
[  1526.183] 	LinBlueFieldPosition: 0
[  1526.183] 	LinRsvdMaskSize: 0
[  1526.183] 	LinRsvdFieldPosition: 0
[  1526.183] 	MaxPixelClock: 0
[  1526.183] Mode: 14d (0x0)
[  1526.183] 	ModeAttributes: 0x0
[  1526.183] 	WinAAttributes: 0x0
[  1526.183] 	WinBAttributes: 0x0
[  1526.183] 	WinGranularity: 0
[  1526.183] 	WinSize: 0
[  1526.183] 	WinASegment: 0x0
[  1526.183] 	WinBSegment: 0x0
[  1526.183] 	WinFuncPtr: 0x0
[  1526.183] 	BytesPerScanline: 0
[  1526.183] 	XResolution: 0
[  1526.183] 	YResolution: 0
[  1526.183] 	XCharSize: 0
[  1526.183] 	YCharSize: 0
[  1526.183] 	NumberOfPlanes: 0
[  1526.183] 	BitsPerPixel: 0
[  1526.183] 	NumberOfBanks: 0
[  1526.183] 	MemoryModel: 0
[  1526.183] 	BankSize: 0
[  1526.183] 	NumberOfImages: 0
[  1526.183] 	RedMaskSize: 0
[  1526.183] 	RedFieldPosition: 0
[  1526.183] 	GreenMaskSize: 0
[  1526.183] 	GreenFieldPosition: 0
[  1526.183] 	BlueMaskSize: 0
[  1526.183] 	BlueFieldPosition: 0
[  1526.183] 	RsvdMaskSize: 0
[  1526.183] 	RsvdFieldPosition: 0
[  1526.183] 	DirectColorModeInfo: 0
[  1526.183] 	PhysBasePtr: 0x0
[  1526.183] 	LinBytesPerScanLine: 0
[  1526.183] 	BnkNumberOfImagePages: 0
[  1526.183] 	LinNumberOfImagePages: 0
[  1526.183] 	LinRedMaskSize: 0
[  1526.183] 	LinRedFieldPosition: 0
[  1526.183] 	LinGreenMaskSize: 0
[  1526.183] 	LinGreenFieldPosition: 0
[  1526.183] 	LinBlueMaskSize: 0
[  1526.183] 	LinBlueFieldPosition: 0
[  1526.183] 	LinRsvdMaskSize: 0
[  1526.183] 	LinRsvdFieldPosition: 0
[  1526.183] 	MaxPixelClock: 0
[  1526.183] Mode: 15c (0x0)
[  1526.183] 	ModeAttributes: 0x0
[  1526.183] 	WinAAttributes: 0x0
[  1526.183] 	WinBAttributes: 0x0
[  1526.183] 	WinGranularity: 0
[  1526.183] 	WinSize: 0
[  1526.183] 	WinASegment: 0x0
[  1526.183] 	WinBSegment: 0x0
[  1526.183] 	WinFuncPtr: 0x0
[  1526.183] 	BytesPerScanline: 0
[  1526.183] 	XResolution: 0
[  1526.183] 	YResolution: 0
[  1526.183] 	XCharSize: 0
[  1526.183] 	YCharSize: 0
[  1526.183] 	NumberOfPlanes: 0
[  1526.183] 	BitsPerPixel: 0
[  1526.183] 	NumberOfBanks: 0
[  1526.183] 	MemoryModel: 0
[  1526.183] 	BankSize: 0
[  1526.183] 	NumberOfImages: 0
[  1526.183] 	RedMaskSize: 0
[  1526.183] 	RedFieldPosition: 0
[  1526.183] 	GreenMaskSize: 0
[  1526.183] 	GreenFieldPosition: 0
[  1526.183] 	BlueMaskSize: 0
[  1526.183] 	BlueFieldPosition: 0
[  1526.183] 	RsvdMaskSize: 0
[  1526.183] 	RsvdFieldPosition: 0
[  1526.183] 	DirectColorModeInfo: 0
[  1526.183] 	PhysBasePtr: 0x0
[  1526.183] 	LinBytesPerScanLine: 0
[  1526.183] 	BnkNumberOfImagePages: 0
[  1526.183] 	LinNumberOfImagePages: 0
[  1526.183] 	LinRedMaskSize: 0
[  1526.184] 	LinRedFieldPosition: 0
[  1526.184] 	LinGreenMaskSize: 0
[  1526.184] 	LinGreenFieldPosition: 0
[  1526.184] 	LinBlueMaskSize: 0
[  1526.184] 	LinBlueFieldPosition: 0
[  1526.184] 	LinRsvdMaskSize: 0
[  1526.184] 	LinRsvdFieldPosition: 0
[  1526.184] 	MaxPixelClock: 0
[  1526.184] Mode: 13a (0x0)
[  1526.184] 	ModeAttributes: 0x0
[  1526.184] 	WinAAttributes: 0x0
[  1526.184] 	WinBAttributes: 0x0
[  1526.184] 	WinGranularity: 0
[  1526.184] 	WinSize: 0
[  1526.184] 	WinASegment: 0x0
[  1526.184] 	WinBSegment: 0x0
[  1526.184] 	WinFuncPtr: 0x0
[  1526.184] 	BytesPerScanline: 0
[  1526.184] 	XResolution: 0
[  1526.184] 	YResolution: 0
[  1526.184] 	XCharSize: 0
[  1526.184] 	YCharSize: 0
[  1526.184] 	NumberOfPlanes: 0
[  1526.184] 	BitsPerPixel: 0
[  1526.184] 	NumberOfBanks: 0
[  1526.184] 	MemoryModel: 0
[  1526.184] 	BankSize: 0
[  1526.184] 	NumberOfImages: 0
[  1526.184] 	RedMaskSize: 0
[  1526.184] 	RedFieldPosition: 0
[  1526.184] 	GreenMaskSize: 0
[  1526.184] 	GreenFieldPosition: 0
[  1526.184] 	BlueMaskSize: 0
[  1526.184] 	BlueFieldPosition: 0
[  1526.184] 	RsvdMaskSize: 0
[  1526.184] 	RsvdFieldPosition: 0
[  1526.184] 	DirectColorModeInfo: 0
[  1526.184] 	PhysBasePtr: 0x0
[  1526.184] 	LinBytesPerScanLine: 0
[  1526.184] 	BnkNumberOfImagePages: 0
[  1526.184] 	LinNumberOfImagePages: 0
[  1526.184] 	LinRedMaskSize: 0
[  1526.184] 	LinRedFieldPosition: 0
[  1526.184] 	LinGreenMaskSize: 0
[  1526.184] 	LinGreenFieldPosition: 0
[  1526.184] 	LinBlueMaskSize: 0
[  1526.184] 	LinBlueFieldPosition: 0
[  1526.184] 	LinRsvdMaskSize: 0
[  1526.184] 	LinRsvdFieldPosition: 0
[  1526.184] 	MaxPixelClock: 0
[  1526.184] Mode: 14b (0x0)
[  1526.184] 	ModeAttributes: 0x0
[  1526.184] 	WinAAttributes: 0x0
[  1526.184] 	WinBAttributes: 0x0
[  1526.184] 	WinGranularity: 0
[  1526.184] 	WinSize: 0
[  1526.184] 	WinASegment: 0x0
[  1526.184] 	WinBSegment: 0x0
[  1526.184] 	WinFuncPtr: 0x0
[  1526.184] 	BytesPerScanline: 0
[  1526.184] 	XResolution: 0
[  1526.184] 	YResolution: 0
[  1526.184] 	XCharSize: 0
[  1526.184] 	YCharSize: 0
[  1526.184] 	NumberOfPlanes: 0
[  1526.184] 	BitsPerPixel: 0
[  1526.184] 	NumberOfBanks: 0
[  1526.184] 	MemoryModel: 0
[  1526.184] 	BankSize: 0
[  1526.184] 	NumberOfImages: 0
[  1526.184] 	RedMaskSize: 0
[  1526.184] 	RedFieldPosition: 0
[  1526.184] 	GreenMaskSize: 0
[  1526.184] 	GreenFieldPosition: 0
[  1526.184] 	BlueMaskSize: 0
[  1526.184] 	BlueFieldPosition: 0
[  1526.184] 	RsvdMaskSize: 0
[  1526.184] 	RsvdFieldPosition: 0
[  1526.184] 	DirectColorModeInfo: 0
[  1526.184] 	PhysBasePtr: 0x0
[  1526.184] 	LinBytesPerScanLine: 0
[  1526.184] 	BnkNumberOfImagePages: 0
[  1526.184] 	LinNumberOfImagePages: 0
[  1526.184] 	LinRedMaskSize: 0
[  1526.184] 	LinRedFieldPosition: 0
[  1526.184] 	LinGreenMaskSize: 0
[  1526.184] 	LinGreenFieldPosition: 0
[  1526.184] 	LinBlueMaskSize: 0
[  1526.184] 	LinBlueFieldPosition: 0
[  1526.184] 	LinRsvdMaskSize: 0
[  1526.184] 	LinRsvdFieldPosition: 0
[  1526.184] 	MaxPixelClock: 0
[  1526.184] Mode: 15a (0x0)
[  1526.184] 	ModeAttributes: 0x0
[  1526.184] 	WinAAttributes: 0x0
[  1526.184] 	WinBAttributes: 0x0
[  1526.184] 	WinGranularity: 0
[  1526.184] 	WinSize: 0
[  1526.184] 	WinASegment: 0x0
[  1526.184] 	WinBSegment: 0x0
[  1526.184] 	WinFuncPtr: 0x0
[  1526.184] 	BytesPerScanline: 0
[  1526.184] 	XResolution: 0
[  1526.184] 	YResolution: 0
[  1526.184] 	XCharSize: 0
[  1526.184] 	YCharSize: 0
[  1526.184] 	NumberOfPlanes: 0
[  1526.184] 	BitsPerPixel: 0
[  1526.184] 	NumberOfBanks: 0
[  1526.184] 	MemoryModel: 0
[  1526.184] 	BankSize: 0
[  1526.184] 	NumberOfImages: 0
[  1526.184] 	RedMaskSize: 0
[  1526.184] 	RedFieldPosition: 0
[  1526.184] 	GreenMaskSize: 0
[  1526.184] 	GreenFieldPosition: 0
[  1526.184] 	BlueMaskSize: 0
[  1526.184] 	BlueFieldPosition: 0
[  1526.184] 	RsvdMaskSize: 0
[  1526.184] 	RsvdFieldPosition: 0
[  1526.184] 	DirectColorModeInfo: 0
[  1526.184] 	PhysBasePtr: 0x0
[  1526.184] 	LinBytesPerScanLine: 0
[  1526.184] 	BnkNumberOfImagePages: 0
[  1526.184] 	LinNumberOfImagePages: 0
[  1526.184] 	LinRedMaskSize: 0
[  1526.184] 	LinRedFieldPosition: 0
[  1526.184] 	LinGreenMaskSize: 0
[  1526.184] 	LinGreenFieldPosition: 0
[  1526.184] 	LinBlueMaskSize: 0
[  1526.184] 	LinBlueFieldPosition: 0
[  1526.184] 	LinRsvdMaskSize: 0
[  1526.184] 	LinRsvdFieldPosition: 0
[  1526.184] 	MaxPixelClock: 0
[  1526.184] Mode: 107 (0x0)
[  1526.184] 	ModeAttributes: 0x0
[  1526.184] 	WinAAttributes: 0x0
[  1526.184] 	WinBAttributes: 0x0
[  1526.184] 	WinGranularity: 0
[  1526.184] 	WinSize: 0
[  1526.184] 	WinASegment: 0x0
[  1526.184] 	WinBSegment: 0x0
[  1526.184] 	WinFuncPtr: 0x0
[  1526.184] 	BytesPerScanline: 0
[  1526.185] 	XResolution: 0
[  1526.185] 	YResolution: 0
[  1526.185] 	XCharSize: 0
[  1526.185] 	YCharSize: 0
[  1526.185] 	NumberOfPlanes: 0
[  1526.185] 	BitsPerPixel: 0
[  1526.185] 	NumberOfBanks: 0
[  1526.185] 	MemoryModel: 0
[  1526.185] 	BankSize: 0
[  1526.185] 	NumberOfImages: 0
[  1526.185] 	RedMaskSize: 0
[  1526.185] 	RedFieldPosition: 0
[  1526.185] 	GreenMaskSize: 0
[  1526.185] 	GreenFieldPosition: 0
[  1526.185] 	BlueMaskSize: 0
[  1526.185] 	BlueFieldPosition: 0
[  1526.185] 	RsvdMaskSize: 0
[  1526.185] 	RsvdFieldPosition: 0
[  1526.185] 	DirectColorModeInfo: 0
[  1526.185] 	PhysBasePtr: 0x0
[  1526.185] 	LinBytesPerScanLine: 0
[  1526.185] 	BnkNumberOfImagePages: 0
[  1526.185] 	LinNumberOfImagePages: 0
[  1526.185] 	LinRedMaskSize: 0
[  1526.185] 	LinRedFieldPosition: 0
[  1526.185] 	LinGreenMaskSize: 0
[  1526.185] 	LinGreenFieldPosition: 0
[  1526.185] 	LinBlueMaskSize: 0
[  1526.185] 	LinBlueFieldPosition: 0
[  1526.185] 	LinRsvdMaskSize: 0
[  1526.185] 	LinRsvdFieldPosition: 0
[  1526.185] 	MaxPixelClock: 0
[  1526.185] Mode: 11a (0x0)
[  1526.185] 	ModeAttributes: 0x0
[  1526.185] 	WinAAttributes: 0x0
[  1526.185] 	WinBAttributes: 0x0
[  1526.185] 	WinGranularity: 0
[  1526.185] 	WinSize: 0
[  1526.185] 	WinASegment: 0x0
[  1526.185] 	WinBSegment: 0x0
[  1526.185] 	WinFuncPtr: 0x0
[  1526.185] 	BytesPerScanline: 0
[  1526.185] 	XResolution: 0
[  1526.185] 	YResolution: 0
[  1526.185] 	XCharSize: 0
[  1526.185] 	YCharSize: 0
[  1526.185] 	NumberOfPlanes: 0
[  1526.185] 	BitsPerPixel: 0
[  1526.185] 	NumberOfBanks: 0
[  1526.185] 	MemoryModel: 0
[  1526.185] 	BankSize: 0
[  1526.185] 	NumberOfImages: 0
[  1526.185] 	RedMaskSize: 0
[  1526.185] 	RedFieldPosition: 0
[  1526.185] 	GreenMaskSize: 0
[  1526.185] 	GreenFieldPosition: 0
[  1526.185] 	BlueMaskSize: 0
[  1526.185] 	BlueFieldPosition: 0
[  1526.185] 	RsvdMaskSize: 0
[  1526.185] 	RsvdFieldPosition: 0
[  1526.185] 	DirectColorModeInfo: 0
[  1526.185] 	PhysBasePtr: 0x0
[  1526.185] 	LinBytesPerScanLine: 0
[  1526.185] 	BnkNumberOfImagePages: 0
[  1526.185] 	LinNumberOfImagePages: 0
[  1526.185] 	LinRedMaskSize: 0
[  1526.185] 	LinRedFieldPosition: 0
[  1526.185] 	LinGreenMaskSize: 0
[  1526.185] 	LinGreenFieldPosition: 0
[  1526.185] 	LinBlueMaskSize: 0
[  1526.185] 	LinBlueFieldPosition: 0
[  1526.185] 	LinRsvdMaskSize: 0
[  1526.185] 	LinRsvdFieldPosition: 0
[  1526.185] 	MaxPixelClock: 0
[  1526.185] Mode: 11b (0x0)
[  1526.185] 	ModeAttributes: 0x0
[  1526.185] 	WinAAttributes: 0x0
[  1526.185] 	WinBAttributes: 0x0
[  1526.185] 	WinGranularity: 0
[  1526.185] 	WinSize: 0
[  1526.185] 	WinASegment: 0x0
[  1526.185] 	WinBSegment: 0x0
[  1526.185] 	WinFuncPtr: 0x0
[  1526.185] 	BytesPerScanline: 0
[  1526.185] 	XResolution: 0
[  1526.185] 	YResolution: 0
[  1526.185] 	XCharSize: 0
[  1526.185] 	YCharSize: 0
[  1526.185] 	NumberOfPlanes: 0
[  1526.185] 	BitsPerPixel: 0
[  1526.185] 	NumberOfBanks: 0
[  1526.185] 	MemoryModel: 0
[  1526.185] 	BankSize: 0
[  1526.185] 	NumberOfImages: 0
[  1526.185] 	RedMaskSize: 0
[  1526.185] 	RedFieldPosition: 0
[  1526.185] 	GreenMaskSize: 0
[  1526.185] 	GreenFieldPosition: 0
[  1526.185] 	BlueMaskSize: 0
[  1526.185] 	BlueFieldPosition: 0
[  1526.185] 	RsvdMaskSize: 0
[  1526.185] 	RsvdFieldPosition: 0
[  1526.185] 	DirectColorModeInfo: 0
[  1526.185] 	PhysBasePtr: 0x0
[  1526.185] 	LinBytesPerScanLine: 0
[  1526.185] 	BnkNumberOfImagePages: 0
[  1526.185] 	LinNumberOfImagePages: 0
[  1526.185] 	LinRedMaskSize: 0
[  1526.185] 	LinRedFieldPosition: 0
[  1526.185] 	LinGreenMaskSize: 0
[  1526.185] 	LinGreenFieldPosition: 0
[  1526.185] 	LinBlueMaskSize: 0
[  1526.185] 	LinBlueFieldPosition: 0
[  1526.185] 	LinRsvdMaskSize: 0
[  1526.185] 	LinRsvdFieldPosition: 0
[  1526.185] 	MaxPixelClock: 0
[  1526.185] Mode: 105 (1024x768)
[  1526.185] 	ModeAttributes: 0x9b
[  1526.185] 	WinAAttributes: 0x7
[  1526.185] 	WinBAttributes: 0x0
[  1526.185] 	WinGranularity: 64
[  1526.185] 	WinSize: 64
[  1526.185] 	WinASegment: 0xa000
[  1526.185] 	WinBSegment: 0x0
[  1526.185] 	WinFuncPtr: 0xc0008657
[  1526.185] 	BytesPerScanline: 1024
[  1526.185] 	XResolution: 1024
[  1526.185] 	YResolution: 768
[  1526.185] 	XCharSize: 8
[  1526.185] 	YCharSize: 16
[  1526.185] 	NumberOfPlanes: 1
[  1526.185] 	BitsPerPixel: 8
[  1526.185] 	NumberOfBanks: 1
[  1526.185] 	MemoryModel: 4
[  1526.185] 	BankSize: 0
[  1526.185] 	NumberOfImages: 84
[  1526.185] 	RedMaskSize: 0
[  1526.185] 	RedFieldPosition: 0
[  1526.185] 	GreenMaskSize: 0
[  1526.185] 	GreenFieldPosition: 0
[  1526.185] 	BlueMaskSize: 0
[  1526.185] 	BlueFieldPosition: 0
[  1526.185] 	RsvdMaskSize: 0
[  1526.185] 	RsvdFieldPosition: 0
[  1526.185] 	DirectColorModeInfo: 0
[  1526.185] 	PhysBasePtr: 0xe0000000
[  1526.185] 	LinBytesPerScanLine: 1024
[  1526.185] 	BnkNumberOfImagePages: 84
[  1526.185] 	LinNumberOfImagePages: 84
[  1526.185] 	LinRedMaskSize: 0
[  1526.185] 	LinRedFieldPosition: 0
[  1526.185] 	LinGreenMaskSize: 0
[  1526.186] 	LinGreenFieldPosition: 0
[  1526.186] 	LinBlueMaskSize: 0
[  1526.186] 	LinBlueFieldPosition: 0
[  1526.186] 	LinRsvdMaskSize: 0
[  1526.186] 	LinRsvdFieldPosition: 0
[  1526.186] 	MaxPixelClock: 230000000
[  1526.186] Mode: 117 (1024x768)
[  1526.186] 	ModeAttributes: 0x9b
[  1526.186] 	WinAAttributes: 0x7
[  1526.186] 	WinBAttributes: 0x0
[  1526.186] 	WinGranularity: 64
[  1526.186] 	WinSize: 64
[  1526.186] 	WinASegment: 0xa000
[  1526.186] 	WinBSegment: 0x0
[  1526.186] 	WinFuncPtr: 0xc0008657
[  1526.186] 	BytesPerScanline: 2048
[  1526.186] 	XResolution: 1024
[  1526.186] 	YResolution: 768
[  1526.186] 	XCharSize: 8
[  1526.186] 	YCharSize: 16
[  1526.186] 	NumberOfPlanes: 1
[  1526.186] 	BitsPerPixel: 16
[  1526.186] 	NumberOfBanks: 1
[  1526.186] 	MemoryModel: 6
[  1526.186] 	BankSize: 0
[  1526.186] 	NumberOfImages: 41
[  1526.186] 	RedMaskSize: 5
[  1526.186] 	RedFieldPosition: 11
[  1526.186] 	GreenMaskSize: 6
[  1526.186] 	GreenFieldPosition: 5
[  1526.186] 	BlueMaskSize: 5
[  1526.186] 	BlueFieldPosition: 0
[  1526.186] 	RsvdMaskSize: 0
[  1526.186] 	RsvdFieldPosition: 0
[  1526.186] 	DirectColorModeInfo: 0
[  1526.186] 	PhysBasePtr: 0xe0000000
[  1526.186] 	LinBytesPerScanLine: 2048
[  1526.186] 	BnkNumberOfImagePages: 41
[  1526.186] 	LinNumberOfImagePages: 41
[  1526.186] 	LinRedMaskSize: 5
[  1526.186] 	LinRedFieldPosition: 11
[  1526.186] 	LinGreenMaskSize: 6
[  1526.186] 	LinGreenFieldPosition: 5
[  1526.186] 	LinBlueMaskSize: 5
[  1526.186] 	LinBlueFieldPosition: 0
[  1526.186] 	LinRsvdMaskSize: 0
[  1526.186] 	LinRsvdFieldPosition: 0
[  1526.186] 	MaxPixelClock: 230000000
[  1526.186] *Mode: 118 (1024x768)
[  1526.186] 	ModeAttributes: 0x9b
[  1526.186] 	WinAAttributes: 0x7
[  1526.186] 	WinBAttributes: 0x0
[  1526.186] 	WinGranularity: 64
[  1526.186] 	WinSize: 64
[  1526.186] 	WinASegment: 0xa000
[  1526.186] 	WinBSegment: 0x0
[  1526.186] 	WinFuncPtr: 0xc0008657
[  1526.186] 	BytesPerScanline: 4096
[  1526.186] 	XResolution: 1024
[  1526.186] 	YResolution: 768
[  1526.186] 	XCharSize: 8
[  1526.186] 	YCharSize: 16
[  1526.186] 	NumberOfPlanes: 1
[  1526.186] 	BitsPerPixel: 32
[  1526.186] 	NumberOfBanks: 1
[  1526.186] 	MemoryModel: 6
[  1526.186] 	BankSize: 0
[  1526.186] 	NumberOfImages: 20
[  1526.186] 	RedMaskSize: 8
[  1526.186] 	RedFieldPosition: 16
[  1526.186] 	GreenMaskSize: 8
[  1526.186] 	GreenFieldPosition: 8
[  1526.186] 	BlueMaskSize: 8
[  1526.186] 	BlueFieldPosition: 0
[  1526.186] 	RsvdMaskSize: 8
[  1526.186] 	RsvdFieldPosition: 24
[  1526.186] 	DirectColorModeInfo: 0
[  1526.186] 	PhysBasePtr: 0xe0000000
[  1526.186] 	LinBytesPerScanLine: 4096
[  1526.186] 	BnkNumberOfImagePages: 20
[  1526.186] 	LinNumberOfImagePages: 20
[  1526.186] 	LinRedMaskSize: 8
[  1526.186] 	LinRedFieldPosition: 16
[  1526.186] 	LinGreenMaskSize: 8
[  1526.186] 	LinGreenFieldPosition: 8
[  1526.186] 	LinBlueMaskSize: 8
[  1526.186] 	LinBlueFieldPosition: 0
[  1526.186] 	LinRsvdMaskSize: 8
[  1526.186] 	LinRsvdFieldPosition: 24
[  1526.186] 	MaxPixelClock: 230000000
[  1526.187] *Mode: 112 (640x480)
[  1526.187] 	ModeAttributes: 0x9b
[  1526.187] 	WinAAttributes: 0x7
[  1526.187] 	WinBAttributes: 0x0
[  1526.187] 	WinGranularity: 64
[  1526.187] 	WinSize: 64
[  1526.187] 	WinASegment: 0xa000
[  1526.187] 	WinBSegment: 0x0
[  1526.187] 	WinFuncPtr: 0xc0008657
[  1526.187] 	BytesPerScanline: 2560
[  1526.187] 	XResolution: 640
[  1526.187] 	YResolution: 480
[  1526.187] 	XCharSize: 8
[  1526.187] 	YCharSize: 16
[  1526.187] 	NumberOfPlanes: 1
[  1526.187] 	BitsPerPixel: 32
[  1526.187] 	NumberOfBanks: 1
[  1526.187] 	MemoryModel: 6
[  1526.187] 	BankSize: 0
[  1526.187] 	NumberOfImages: 52
[  1526.187] 	RedMaskSize: 8
[  1526.187] 	RedFieldPosition: 16
[  1526.187] 	GreenMaskSize: 8
[  1526.187] 	GreenFieldPosition: 8
[  1526.187] 	BlueMaskSize: 8
[  1526.187] 	BlueFieldPosition: 0
[  1526.187] 	RsvdMaskSize: 8
[  1526.187] 	RsvdFieldPosition: 24
[  1526.187] 	DirectColorModeInfo: 0
[  1526.187] 	PhysBasePtr: 0xe0000000
[  1526.187] 	LinBytesPerScanLine: 2560
[  1526.187] 	BnkNumberOfImagePages: 52
[  1526.187] 	LinNumberOfImagePages: 52
[  1526.187] 	LinRedMaskSize: 8
[  1526.187] 	LinRedFieldPosition: 16
[  1526.187] 	LinGreenMaskSize: 8
[  1526.187] 	LinGreenFieldPosition: 8
[  1526.187] 	LinBlueMaskSize: 8
[  1526.187] 	LinBlueFieldPosition: 0
[  1526.187] 	LinRsvdMaskSize: 8
[  1526.187] 	LinRsvdFieldPosition: 24
[  1526.187] 	MaxPixelClock: 230000000
[  1526.187] Mode: 114 (800x600)
[  1526.187] 	ModeAttributes: 0x9b
[  1526.187] 	WinAAttributes: 0x7
[  1526.187] 	WinBAttributes: 0x0
[  1526.187] 	WinGranularity: 64
[  1526.187] 	WinSize: 64
[  1526.187] 	WinASegment: 0xa000
[  1526.187] 	WinBSegment: 0x0
[  1526.187] 	WinFuncPtr: 0xc0008657
[  1526.187] 	BytesPerScanline: 1600
[  1526.187] 	XResolution: 800
[  1526.187] 	YResolution: 600
[  1526.187] 	XCharSize: 8
[  1526.187] 	YCharSize: 16
[  1526.187] 	NumberOfPlanes: 1
[  1526.187] 	BitsPerPixel: 16
[  1526.187] 	NumberOfBanks: 1
[  1526.187] 	MemoryModel: 6
[  1526.187] 	BankSize: 0
[  1526.187] 	NumberOfImages: 67
[  1526.187] 	RedMaskSize: 5
[  1526.187] 	RedFieldPosition: 11
[  1526.187] 	GreenMaskSize: 6
[  1526.187] 	GreenFieldPosition: 5
[  1526.187] 	BlueMaskSize: 5
[  1526.187] 	BlueFieldPosition: 0
[  1526.187] 	RsvdMaskSize: 0
[  1526.187] 	RsvdFieldPosition: 0
[  1526.187] 	DirectColorModeInfo: 0
[  1526.187] 	PhysBasePtr: 0xe0000000
[  1526.187] 	LinBytesPerScanLine: 1600
[  1526.187] 	BnkNumberOfImagePages: 67
[  1526.187] 	LinNumberOfImagePages: 67
[  1526.187] 	LinRedMaskSize: 5
[  1526.187] 	LinRedFieldPosition: 11
[  1526.187] 	LinGreenMaskSize: 6
[  1526.187] 	LinGreenFieldPosition: 5
[  1526.187] 	LinBlueMaskSize: 5
[  1526.187] 	LinBlueFieldPosition: 0
[  1526.187] 	LinRsvdMaskSize: 0
[  1526.187] 	LinRsvdFieldPosition: 0
[  1526.187] 	MaxPixelClock: 230000000
[  1526.187] *Mode: 115 (800x600)
[  1526.187] 	ModeAttributes: 0x9b
[  1526.187] 	WinAAttributes: 0x7
[  1526.187] 	WinBAttributes: 0x0
[  1526.187] 	WinGranularity: 64
[  1526.187] 	WinSize: 64
[  1526.187] 	WinASegment: 0xa000
[  1526.187] 	WinBSegment: 0x0
[  1526.187] 	WinFuncPtr: 0xc0008657
[  1526.187] 	BytesPerScanline: 3200
[  1526.187] 	XResolution: 800
[  1526.187] 	YResolution: 600
[  1526.187] 	XCharSize: 8
[  1526.187] 	YCharSize: 16
[  1526.187] 	NumberOfPlanes: 1
[  1526.187] 	BitsPerPixel: 32
[  1526.187] 	NumberOfBanks: 1
[  1526.187] 	MemoryModel: 6
[  1526.187] 	BankSize: 0
[  1526.187] 	NumberOfImages: 33
[  1526.187] 	RedMaskSize: 8
[  1526.187] 	RedFieldPosition: 16
[  1526.187] 	GreenMaskSize: 8
[  1526.187] 	GreenFieldPosition: 8
[  1526.187] 	BlueMaskSize: 8
[  1526.187] 	BlueFieldPosition: 0
[  1526.187] 	RsvdMaskSize: 8
[  1526.188] 	RsvdFieldPosition: 24
[  1526.188] 	DirectColorModeInfo: 0
[  1526.188] 	PhysBasePtr: 0xe0000000
[  1526.188] 	LinBytesPerScanLine: 3200
[  1526.188] 	BnkNumberOfImagePages: 33
[  1526.188] 	LinNumberOfImagePages: 33
[  1526.188] 	LinRedMaskSize: 8
[  1526.188] 	LinRedFieldPosition: 16
[  1526.188] 	LinGreenMaskSize: 8
[  1526.188] 	LinGreenFieldPosition: 8
[  1526.188] 	LinBlueMaskSize: 8
[  1526.188] 	LinBlueFieldPosition: 0
[  1526.188] 	LinRsvdMaskSize: 8
[  1526.188] 	LinRsvdFieldPosition: 24
[  1526.188] 	MaxPixelClock: 230000000
[  1526.188] Mode: 101 (640x480)
[  1526.188] 	ModeAttributes: 0x9b
[  1526.188] 	WinAAttributes: 0x7
[  1526.188] 	WinBAttributes: 0x0
[  1526.188] 	WinGranularity: 64
[  1526.188] 	WinSize: 64
[  1526.188] 	WinASegment: 0xa000
[  1526.188] 	WinBSegment: 0x0
[  1526.188] 	WinFuncPtr: 0xc0008657
[  1526.188] 	BytesPerScanline: 640
[  1526.188] 	XResolution: 640
[  1526.188] 	YResolution: 480
[  1526.188] 	XCharSize: 8
[  1526.188] 	YCharSize: 16
[  1526.188] 	NumberOfPlanes: 1
[  1526.188] 	BitsPerPixel: 8
[  1526.188] 	NumberOfBanks: 1
[  1526.188] 	MemoryModel: 4
[  1526.188] 	BankSize: 0
[  1526.188] 	NumberOfImages: 203
[  1526.188] 	RedMaskSize: 0
[  1526.188] 	RedFieldPosition: 0
[  1526.188] 	GreenMaskSize: 0
[  1526.188] 	GreenFieldPosition: 0
[  1526.188] 	BlueMaskSize: 0
[  1526.188] 	BlueFieldPosition: 0
[  1526.188] 	RsvdMaskSize: 0
[  1526.188] 	RsvdFieldPosition: 0
[  1526.188] 	DirectColorModeInfo: 0
[  1526.188] 	PhysBasePtr: 0xe0000000
[  1526.188] 	LinBytesPerScanLine: 640
[  1526.188] 	BnkNumberOfImagePages: 203
[  1526.188] 	LinNumberOfImagePages: 203
[  1526.188] 	LinRedMaskSize: 0
[  1526.188] 	LinRedFieldPosition: 0
[  1526.188] 	LinGreenMaskSize: 0
[  1526.188] 	LinGreenFieldPosition: 0
[  1526.188] 	LinBlueMaskSize: 0
[  1526.188] 	LinBlueFieldPosition: 0
[  1526.188] 	LinRsvdMaskSize: 0
[  1526.188] 	LinRsvdFieldPosition: 0
[  1526.188] 	MaxPixelClock: 230000000
[  1526.188] Mode: 103 (800x600)
[  1526.188] 	ModeAttributes: 0x9b
[  1526.188] 	WinAAttributes: 0x7
[  1526.188] 	WinBAttributes: 0x0
[  1526.188] 	WinGranularity: 64
[  1526.188] 	WinSize: 64
[  1526.188] 	WinASegment: 0xa000
[  1526.188] 	WinBSegment: 0x0
[  1526.188] 	WinFuncPtr: 0xc0008657
[  1526.188] 	BytesPerScanline: 832
[  1526.188] 	XResolution: 800
[  1526.188] 	YResolution: 600
[  1526.188] 	XCharSize: 8
[  1526.188] 	YCharSize: 16
[  1526.188] 	NumberOfPlanes: 1
[  1526.188] 	BitsPerPixel: 8
[  1526.188] 	NumberOfBanks: 1
[  1526.188] 	MemoryModel: 4
[  1526.188] 	BankSize: 0
[  1526.188] 	NumberOfImages: 126
[  1526.188] 	RedMaskSize: 0
[  1526.188] 	RedFieldPosition: 0
[  1526.188] 	GreenMaskSize: 0
[  1526.188] 	GreenFieldPosition: 0
[  1526.188] 	BlueMaskSize: 0
[  1526.188] 	BlueFieldPosition: 0
[  1526.188] 	RsvdMaskSize: 0
[  1526.188] 	RsvdFieldPosition: 0
[  1526.188] 	DirectColorModeInfo: 0
[  1526.188] 	PhysBasePtr: 0xe0000000
[  1526.188] 	LinBytesPerScanLine: 832
[  1526.188] 	BnkNumberOfImagePages: 126
[  1526.188] 	LinNumberOfImagePages: 126
[  1526.188] 	LinRedMaskSize: 0
[  1526.188] 	LinRedFieldPosition: 0
[  1526.188] 	LinGreenMaskSize: 0
[  1526.188] 	LinGreenFieldPosition: 0
[  1526.188] 	LinBlueMaskSize: 0
[  1526.188] 	LinBlueFieldPosition: 0
[  1526.188] 	LinRsvdMaskSize: 0
[  1526.188] 	LinRsvdFieldPosition: 0
[  1526.188] 	MaxPixelClock: 230000000
[  1526.188] Mode: 111 (640x480)
[  1526.188] 	ModeAttributes: 0x9b
[  1526.188] 	WinAAttributes: 0x7
[  1526.188] 	WinBAttributes: 0x0
[  1526.188] 	WinGranularity: 64
[  1526.188] 	WinSize: 64
[  1526.188] 	WinASegment: 0xa000
[  1526.189] 	WinBSegment: 0x0
[  1526.189] 	WinFuncPtr: 0xc0008657
[  1526.189] 	BytesPerScanline: 1280
[  1526.189] 	XResolution: 640
[  1526.189] 	YResolution: 480
[  1526.189] 	XCharSize: 8
[  1526.189] 	YCharSize: 16
[  1526.189] 	NumberOfPlanes: 1
[  1526.189] 	BitsPerPixel: 16
[  1526.189] 	NumberOfBanks: 1
[  1526.189] 	MemoryModel: 6
[  1526.189] 	BankSize: 0
[  1526.189] 	NumberOfImages: 101
[  1526.189] 	RedMaskSize: 5
[  1526.189] 	RedFieldPosition: 11
[  1526.189] 	GreenMaskSize: 6
[  1526.189] 	GreenFieldPosition: 5
[  1526.189] 	BlueMaskSize: 5
[  1526.189] 	BlueFieldPosition: 0
[  1526.189] 	RsvdMaskSize: 0
[  1526.189] 	RsvdFieldPosition: 0
[  1526.189] 	DirectColorModeInfo: 0
[  1526.189] 	PhysBasePtr: 0xe0000000
[  1526.189] 	LinBytesPerScanLine: 1280
[  1526.189] 	BnkNumberOfImagePages: 101
[  1526.189] 	LinNumberOfImagePages: 101
[  1526.189] 	LinRedMaskSize: 5
[  1526.189] 	LinRedFieldPosition: 11
[  1526.189] 	LinGreenMaskSize: 6
[  1526.189] 	LinGreenFieldPosition: 5
[  1526.189] 	LinBlueMaskSize: 5
[  1526.189] 	LinBlueFieldPosition: 0
[  1526.189] 	LinRsvdMaskSize: 0
[  1526.189] 	LinRsvdFieldPosition: 0
[  1526.189] 	MaxPixelClock: 230000000
[  1526.189] 
[  1526.189] (II) VESA(0): Total Memory: 1023 64KB banks (65472kB)
[  1526.189] (II) VESA(0): <default monitor>: Using hsync range of 31.60-47.40 kHz
[  1526.189] (II) VESA(0): <default monitor>: Using vrefresh range of 40.00-60.00 Hz
[  1526.189] (WW) VESA(0): Unable to estimate virtual size
[  1526.189] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[  1526.189] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[  1526.189] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[  1526.189] (WW) VESA(0): No valid modes left. Trying less strict filter...
[  1526.189] (II) VESA(0): <default monitor>: Using hsync range of 31.60-47.40 kHz
[  1526.189] (II) VESA(0): <default monitor>: Using vrefresh range of 40.00-60.00 Hz
[  1526.189] (WW) VESA(0): Unable to estimate virtual size
[  1526.189] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[  1526.189] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[  1526.189] (**) VESA(0): *Built-in mode "1024x768"
[  1526.189] (**) VESA(0): *Built-in mode "800x600"
[  1526.189] (**) VESA(0): Display dimensions: (340, 190) mm
[  1526.189] (**) VESA(0): DPI set to (76, 102)
[  1526.189] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[  1526.189] (**) VESA(0): Using "Shadow Framebuffer"
[  1526.189] (II) Loading sub module "shadow"
[  1526.189] (II) LoadModule: "shadow"
[  1526.189] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  1526.189] (II) Module shadow: vendor="X.Org Foundation"
[  1526.189] 	compiled for 1.10.4, module version = 1.1.0
[  1526.189] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1526.189] (II) Loading sub module "fb"
[  1526.189] (II) LoadModule: "fb"
[  1526.189] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1526.189] (II) Module fb: vendor="X.Org Foundation"
[  1526.189] 	compiled for 1.10.4, module version = 1.0.0
[  1526.189] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1526.189] (II) UnloadModule: "fbdev"
[  1526.189] (II) Unloading fbdev
[  1526.189] (II) UnloadModule: "fbdevhw"
[  1526.189] (II) Unloading fbdevhw
[  1526.189] (==) Depth 24 pixmap format is 32 bpp
[  1526.189] (II) Loading sub module "int10"
[  1526.189] (II) LoadModule: "int10"
[  1526.189] (II) Loading /usr/lib/xorg/modules/libint10.so
[  1526.190] (II) Module int10: vendor="X.Org Foundation"
[  1526.190] 	compiled for 1.10.4, module version = 1.0.0
[  1526.190] 	ABI class: X.Org Video Driver, version 10.0
[  1526.190] (II) VESA(0): initializing int10
[  1526.190] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[  1526.190] (II) VESA(0): VESA BIOS detected
[  1526.190] (II) VESA(0): VESA VBE Version 3.0
[  1526.190] (II) VESA(0): VESA VBE Total Mem: 65472 kB
[  1526.190] (II) VESA(0): VESA VBE OEM: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
[  1526.190] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[  1526.190] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[  1526.190] (II) VESA(0): VESA VBE OEM Product: Intel(R)Sandybridge Mobile Graphics Controller
[  1526.190] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[  1526.203] (II) VESA(0): virtual address = 0x7fee8df59000,
	physical address = 0xe0000000, size = 67043328
[  1526.210] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[  1526.282] (==) VESA(0): Default visual is TrueColor
[  1526.282] (==) VESA(0): Backing store disabled
[  1526.282] (==) VESA(0): DPMS enabled
[  1526.282] (==) RandR enabled
[  1526.282] (II) Initializing built-in extension Generic Event Extension
[  1526.282] (II) Initializing built-in extension SHAPE
[  1526.282] (II) Initializing built-in extension MIT-SHM
[  1526.282] (II) Initializing built-in extension XInputExtension
[  1526.282] (II) Initializing built-in extension XTEST
[  1526.282] (II) Initializing built-in extension BIG-REQUESTS
[  1526.282] (II) Initializing built-in extension SYNC
[  1526.282] (II) Initializing built-in extension XKEYBOARD
[  1526.282] (II) Initializing built-in extension XC-MISC
[  1526.282] (II) Initializing built-in extension SECURITY
[  1526.282] (II) Initializing built-in extension XINERAMA
[  1526.282] (II) Initializing built-in extension XFIXES
[  1526.282] (II) Initializing built-in extension RENDER
[  1526.282] (II) Initializing built-in extension RANDR
[  1526.282] (II) Initializing built-in extension COMPOSITE
[  1526.282] (II) Initializing built-in extension DAMAGE
[  1526.282] (II) Initializing built-in extension GESTURE
[  1526.286] (II) AIGLX: Screen 0 is not DRI2 capable
[  1526.286] (II) AIGLX: Screen 0 is not DRI capable
[  1526.286] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
[  1526.731] (II) AIGLX: Loaded and initialized swrast
[  1526.731] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  1526.909] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1570.088]  ddxSigGiveUp: Closing log


```

---

### Post by MAFoElffen on 2012-01-01
> **stumbleUpon said:**
> @MAFoElffen

I have installed 11.10 using the alternate install method. As before, I get a blank screen on booting to the desktop. I am using the recovery mode to login and extract info. I have a wired internet connection available. 

Here are the contents of the /var/log/Xorg.0.log file in my system.
Could you please post your ~/.xsession-errors file?

---

### Post by stumbleUpon on 2012-01-02
> **MAFoElffen said:**
> Could you please post your ~/.xsession-errors file?

@MAFoElffen

I have given up on 11.10 as of now. Ubuntu 10.04 is working fine and i am happy with that.

Thanks a lot for your responses. And sorry for giving up. But i have to get my work done and need to have a system for production us. 11.10 as troubling a lot.

---

