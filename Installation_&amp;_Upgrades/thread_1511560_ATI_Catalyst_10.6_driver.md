---
title: "ATI Catalyst 10.6 driver"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by mikerobinson on 2010-06-17
I am running kubuntu 10.04 32 bit with ATI Radeon HD 4800 series video card. I had the Catalyst 10.3 driver installed and working, but I wanted to upgrade to 10.6 today. After installation, kdm doesn't even come up if I use the radeon driver and when I switch to the vesa driver, kdm comes up, but logging in brings me right back to the login screen. The only way I've been able to log back in is by doing ```
sudo apt-get remove --purge fglrx-kernel-source xorg-driver-fglrx fglrx-modaliases libamdxvba1
```Has anyone else been able to install the catalyst 10.6 driver? I'll give it a go with 10.5 when I get time tomorrow.

---

### Post by nicke85 on 2010-06-17
I always install nVidia and ATI driver on the same way :)
Steps are.
> 1. Press Alt+Ctrl+F2 to quit desktop
2. Enter your user and pass
3. type "sudo /etc/init.d/gdm stop" to stop GFX driver
4. go to folder where is driver and type "sudo sh `full name of driver file'"
5.install driver ATI or nVidia
6.type "sudo reboot"I hope it will help you :)

So I use Gnome and you can try type "sudo /etc/init.d/kdm stop" if use KDE..

---

### Post by mikerobinson on 2010-06-17
> **nicke85 said:**
> I always install nVidia and ATI driver on the same way :)
Steps are.
I hope it will help you :)

So I use Gnome and you can try type "sudo /etc/init.d/kdm stop" if use KDE..

Hi nicke85,

I was able to get the package installed just fine. It just didn't work, even after reboot. I'm now using the 'radeon' driver since fglrx and vesa are no longer working. I'll try installing 10.5 instead when I get a chance later today. I just wanted to know if anyone else is having issues with the Catalyst 10.6 drivers.

---

### Post by mikerobinson on 2010-06-17
OK I got it to work now with the 10.6 driver. I was missing the BusID in the Device section of my xorg.conf file and Ubuntu couldn't figure out where my card was I guess.

---

### Post by Zireth ZH on 2010-06-17
hows the performance of the card for you? how did u did it? im sure mines will encounter a problem once i upgrade too i own the same card running kubuntu

---

### Post by mikerobinson on 2010-06-17
> **Zireth ZH said:**
> hows the performance of the card for you? how did u did it? im sure mines will encounter a problem once i upgrade too i own the same card running kubuntu

Performance seems pretty decent. Getting around 50000 frames per 5 sec in glxgears. World of warcraft with wine in opengl mode I get around 30 fps with 1776x1000 resolution and all settings maxed out.

To upgrade this is roughly what I did:

1) backup your /etc/X11/xorg.conf file (just in case):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
2) Run the installer:
```
sudo ./ati-driver-installer-10-6-x86.x86_64.run --buildpkg Ubuntu/lucid
```
3) Uninstall current driver:
```
sudo apt-get remove --purge fglrx-kernel-source xorg-driver-fglrx fglrx-modaliases libamdxvba1
```
4) Install the new driver (must be in the same directory as step 2):
```
sudo dpkg -i ./fglrx*.deb
```
5) Cross your fingers
6) Reboot

---

### Post by hegomir on 2010-07-20
Used the solution posted above, but it says that drivers are not installed. Please help.

---

### Post by mikerobinson on 2010-07-20
> **hegomir said:**
> Used the solution posted above, but it says that drivers are not installed. Please help.

Are there any errors in your /var/log/Xorg.0.log file? Is your /etc/X11/xorg.conf file configured correctly to use the fglrx driver? What is the output of executing fglrxinfo?

---

### Post by hegomir on 2010-07-22
Reinstalled ubuntu... i will give it another go... fingers crossed.:) I'm using this tutorial: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by hegomir on 2010-07-22
The instructions say that there should be 6 .deb files after creating them. I only get 4... did I do something wrong?

These are the debs:
 fglrx     - Video driver for the ATI graphics accelerators
 fglrx-amdcccle - Catalyst Control Center for the ATI graphics accelerators
 fglrx-dev  - Video driver for the ATI graphics accelerators (devel files)
 fglrx-modaliases - Identifiers supported by the ATI graphics driver

so i'm missing 3 debs:
 xorg-driver-fglrx - Video driver for the ATI graphics accelerators
 xorg-driver-fglrx-dev - Video driver for the ATI graphics accelerators (devel files)
 fglrx-kernel-source - Kernel module source for the ATI graphics accelerators 

what now?

---

### Post by hegomir on 2010-07-22
Pushed on anyway... nothing happened... rebooted... everything seemed fine, no problem, just docky saying i have to have compoziting enabled, which ment the drivers didn't installed (properly?), looked around abit and no driver, no fglrxinfo, no anything,... so i reinstalled the driver Hardware drivers offered... reboot... run ubuntu in low graphics mode...oh fuuu... now i'm back at post 1.

Will look for the thing you pointed out and post it here. Thank you in advance. :S

---

### Post by hegomir on 2010-07-22
xorg.0.log ... i'm sorry... but i can't separate what's an error and what's not.
I only spotted a few warnings: 

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.

(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)

(WW) Falling back to old probe method for fglrx

(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found





X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux valentin-laptop 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-23-generic-pae root=UUID=95f91900-36ce-4c38-a4d0-bb305e620941 ro quiet splash
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jul 22 12:34:52 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:68c1:1179:fd00 ATI Technologies Inc Redwood [Radeon HD 5600 Series] rev 0, Mem @ 0xc0000000/268435456, 0xd2200000/131072, I/O @ 0x00005000/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.74.4
	Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.74.4
(II) ATI Proprietary Linux Driver Version Identifier:8.74.4
(II) ATI Proprietary Linux Driver Release Identifier: 8.741                                
(II) ATI Proprietary Linux Driver Build Date: May 27 2010 12:52:28
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x68C1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb7847410]
3: /usr/bin/X (xf86ParsePciBusString+0x2c) [0x80c6cec]
4: /usr/bin/X (xf86ComparePciBusString+0x32) [0x80c6f92]
5: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (atiddxProbe+0x95b) [0xb6de3dfb]
6: /usr/bin/X (xf86CallDriverProbe+0x182) [0x80b82c2]
7: /usr/bin/X (InitOutput+0x3c2) [0x80b9a82]
8: /usr/bin/X (0x8048000+0x1ebbb) [0x8066bbb]
9: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0xb757dbd6]
10: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by hegomir on 2010-07-22
xorg.conf


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection









fglrxinfo gives me segmentation fault.

---

### Post by chrisinspace on 2010-07-28
I was able to get this installed with no real issues, but with the proprietary driver in place, the system is unusable.  I wish I could easily describe it, but it's just a mess.  The desktop loads up fine, but any thing I interact with (menus, icons, open windows) fragments into a bunch of small horizontal lines and takes forever to come into focus.  This happens whether I used Ubuntu's built-in "Hardware Drivers" utility or download the .sh file from ATI and install using the processes described in this thread.  Any ideas?

---

### Post by mikerobinson on 2010-07-29
> **chrisinspace said:**
> I was able to get this installed with no real issues, but with the proprietary driver in place, the system is unusable.  I wish I could easily describe it, but it's just a mess.  The desktop loads up fine, but any thing I interact with (menus, icons, open windows) fragments into a bunch of small horizontal lines and takes forever to come into focus.  This happens whether I used Ubuntu's built-in "Hardware Drivers" utility or download the .sh file from ATI and install using the processes described in this thread.  Any ideas?

I had a similar issue. When I switched windows, they would often be completely grayed out until I interact with them. I upgraded to 10.7 last night and the problem still persists, but to a much lesser degree. Maybe it wouldn't be such a bad idea trying other driver versions - even older ones - and see if that fixes your problem.

---

### Post by chrisinspace on 2010-07-29
> **mikerobinson said:**
> I had a similar issue. When I switched windows, they would often be completely grayed out until I interact with them. I upgraded to 10.7 last night and the problem still persists, but to a much lesser degree. Maybe it wouldn't be such a bad idea trying other driver versions - even older ones - and see if that fixes your problem.

I'm using 10.7 now and the problem is just as bad as ever.  Does the ATI site have old versions?  I'll go back and check.  

What output port are you using...HDMI, DVI?

---

### Post by mikerobinson on 2010-07-29
> **chrisinspace said:**
> I'm using 10.7 now and the problem is just as bad as ever.  Does the ATI site have old versions?  I'll go back and check.  

What output port are you using...HDMI, DVI?

It's DVI... I never thought about trying it with plain RGB to see if that makes a difference.

---

### Post by alphacrucis2 on 2010-07-29
> **chrisinspace said:**
> I'm using 10.7 now and the problem is just as bad as ever.  Does the ATI site have old versions?  I'll go back and check.  

What output port are you using...HDMI, DVI?

For me the buildpkg method never worked properly with either 10.6 or 10.7. Just run the ATI installer and select the install option as per the ATI instructions. Don't forget ```
sudo aticonfig --initial -f
``` before rebooting.

---

### Post by chrisinspace on 2010-07-30
> **alphacrucis2 said:**
> For me the buildpkg method never worked properly with either 10.6 or 10.7. Just run the ATI installer and select the install option as per the ATI instructions. Don't forget ```
sudo aticonfig --initial -f
``` before rebooting.

Hmmm.  I tried running the ATI installer and I did use aticonfig --initial, but I didn't include the -f switch.  That creates a new Xorg config file instead of modifying the existing one, right?  Does that make a big difference?

---

### Post by Stimpy84 on 2010-10-08
> **mikerobinson said:**
> To upgrade this is roughly what I did:

[...]
Thanks so much, Mike! This worked absolutely flawlessly!

I'm delighted to see that windows resize, maximize and unminimize instantaneously. For those out there with the same problem, I urge you to follow this wise man's instructions!

---

