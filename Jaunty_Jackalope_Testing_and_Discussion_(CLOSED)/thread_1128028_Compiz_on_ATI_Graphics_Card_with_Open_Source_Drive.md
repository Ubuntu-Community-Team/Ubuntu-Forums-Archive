---
title: "Compiz on ATI Graphics Card with Open Source Drivers"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Akkifokkusu on 2009-04-17
So, I decided to update to Jaunty from Intrepid, seeing as it's the RC and all. Update goes fine, computer restarts. Ubuntu loads, and then... WTF? The display crashes. So, I reboot, go to the diagnostic, try to run xfix or whatever. Same thing happens. So I see somewhere that it might be fglrx. Well, that's fine. So, I remove that and install the open source drivers. Works, but when it loads, no Desktop Effects, no Compiz. After going through some more trial and error, I enabled Compiz, only to get... well, nothing. No 3D effect, not even the widget layer, without which Screenlets are useless to me.

So, I've been reading that my card isn't supported by the fglrx version that the new version of Xorg supports or something. So is there any workaround for me, or should I just go back to Intrepid (and how would I downgrade, anyway)?

---

### Post by alphacrucis2 on 2009-04-17
> **Akkifokkusu said:**
> So, I decided to update to Jaunty from Intrepid, seeing as it's the RC and all. Update goes fine, computer restarts. Ubuntu loads, and then... WTF? The display crashes. So, I reboot, go to the diagnostic, try to run xfix or whatever. Same thing happens. So I see somewhere that it might be fglrx. Well, that's fine. So, I remove that and install the open source drivers. Works, but when it loads, no Desktop Effects, no Compiz. After going through some more trial and error, I enabled Compiz, only to get... well, nothing. No 3D effect, not even the widget layer, without which Screenlets are useless to me.

So, I've been reading that my card isn't supported by the fglrx version that the new version of Xorg supports or something. So is there any workaround for me, or should I just go back to Intrepid (and how would I downgrade, anyway)?

I believe that the older fglrx driver that supported your card doesn't work with xorg 1.6 (which is what Jaunty uses). The new proprietary driver that works with the new xorg doesn't support older cards - a bit of a catch 22. I don't know of any solution for you other than stay with Intrepid for now.

---

### Post by Akkifokkusu on 2009-04-17
So, how would I roll back to Intrepid, then?

---

### Post by alphacrucis2 on 2009-04-17
> **Akkifokkusu said:**
> So, how would I roll back to Intrepid, then?

I don't think you can. It would require a reinstall as far as I know but you should wait for someone with more knowledge than me to advise.

---

### Post by Martje_001 on 2009-04-17
alphacrucis2 is right, you can't rollback. Reinstall Intrepid and wait for the open-source drivers to be ready (end-of-year).

---

### Post by Akkifokkusu on 2009-04-17
Wow. So I pretty much got the shaft there.

I've read people saying the got Compiz working fine with the open-source drivers, though. Anyone have any help with that?

---

### Post by vlovich on 2009-04-17
Well your sig says you have a 2600 which is supported by Fglrx

---

### Post by CarpKing on 2009-04-17
Have you tried reinstalling the open-source drivers? Fglrx messes up some files they need in order to enable 3d, so if you switch without reinstalling (IIRC that's usually all that's needed to fix this) you won't get any 3d acceleration.

---

### Post by danwood76 on 2009-04-17
The open source drivers support compiz up to the x1xx series.
3d for later models is in development but it will take time.

The ATI 2600 is supported by version 9.3 of fglrx which works on jaunty?

How have you installed the drivers?
You might try installing them manually to see if that helps.

---

### Post by markbuntu on 2009-04-17
9.3 fglrx does not work on Jaunty. The restricted driver available in jaunty is a pre-release of 9.4. Your best bet for the 2600 is the radeonhd driver which is in the repos.

---

### Post by vlovich on 2009-04-17
I have a 2600 & have had fewer issues with the pre-release of 9.4 on jaunty than 9.3/9.2/9.1 on hardy.

Also, the official 9.4 is now out anyways with working support for redirected indirect rendering.  Basically, allows you to run opengl apps in windowed or full-screen mode within compiz properly (no flickering, window behaves properly etc).  This is useful for things like games & opengl full-screen video (no need to use xVideo or the unredirect full screen option in compiz).

Using 9.4 right now.

radeonhd is fine, but it's really slow because there's no 3d acceleration right now (not even sure if 2d acceleration is in there), so compiz is really slow.  3d acceleration should be coming soon though apparently.  Can't wait for it to be in a useable enough state that I can finally drop fglrx.

---

### Post by Akkifokkusu on 2009-04-18
> **vlovich said:**
> I have a 2600 & have had fewer issues with the pre-release of 9.4 on jaunty than 9.3/9.2/9.1 on hardy.

Also, the official 9.4 is now out anyways with working support for redirected indirect rendering.  Basically, allows you to run opengl apps in windowed or full-screen mode within compiz properly (no flickering, window behaves properly etc).  This is useful for things like games & opengl full-screen video (no need to use xVideo or the unredirect full screen option in compiz).

Using 9.4 right now.

9.4 works for you? Did you have to tweak it in any way or do a manual install?

I tried a manual install of 9.3, and that didn't go so well... Haven't tried 9.4 yet, but I will and see what happens.

---

### Post by vlovich on 2009-04-18
Why?  First of all 9.3 will not work with Jaunty because the xserver has been updated to 1.6 - but Jaunty came with a prerelease of 9.4 in the distro anyways which you should have been using.

---

### Post by Akkifokkusu on 2009-04-18
Yeah, 9.4 manually didn't work, either.

I'm wondering, if my only option to get back to Intrepid is reinstall, then is there a way to simply roll back Xorg? I guess maybe I'm just wishing that.

But I have seen people say Compiz works great with the open-source drivers for them, and that fglrx actually makes it run worse. Any way I could get it to work with the open-source drivers?

---

### Post by vlovich on 2009-04-18
What exactly doesn't work?

Try running ```
sudo aticonfig --initial
```

If it still doesn't work, post the output of ```
dmesg
``` & attach /var/log/Xorg.0.log

Oh as for rolling back X within Jaunty, keep dreaming.  You'd first have to build the package which will probably be a hassle & take a while & then likely nothing would work any ways.

Depends for whom, but if your card is supported with fglrx under Jaunty, then there's no way the open source drivers will be better - they don't even have 3d acceleration.  I've tried them on my 2600 - it's really really bad.

Also, have you installed the open source drivers?  They conflict with fglrx & you need to clean them from your system.  

Try putting the following in a script (i.e. fglrx.sh) & execute it with root priveleges (i.e. sudo).  Make sure you put the fglrx driver in the same directory or pass it the path to where you downloaded it.  This only supports fglrx 9.4.

```

#!/bin/bash

if ! test xroot = x`whoami`; then
	echo "Please run as root" >&2
	exit 1
fi

WORKDIR=`mktemp -dt`
DRIVER="${1:-ati-driver-installer-9-4-x86.x86_64.run}"

if ! test -e "$DRIVER"; then
	echo "Please place $DRIVER in this directory or pass the location as the first argument" >&2
	exit 1
fi

function cleanup() {
	popd || return 1
	rm -rf "$WORKDIR" || return 1
}

function fail_and_cleanup() {
	cleanup || echo "Failed to cleanup on failure" >& 2
	exit 1
}

function fail() {
	echo $1 >& 2
	exit 1
}

if test -x /usr/share/fglrx/ati-uninstall.sh; then
	/usr/share/fglrx/ati-uninstall.sh # if it exists
fi

apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xserver-xorg-video-radeonhd xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle fglrx-modaliases || fail "Unable to purge old packages"
apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx || fail "Unable to re-install clean mesa"
cp "$DRIVER" "$WORKDIR"
pushd "$WORKDIR" > /dev/null
sh ./"$DRIVER" --buildpkg Ubuntu/9.04 || cleanup
dpkg -i xorg-driver-fglrx_8.602-0ubuntu1_amd64.deb fglrx-amdcccle_8.602-0ubuntu1_amd64.deb fglrx-kernel-source_8.602-0ubuntu1_amd64.deb fglrx-modaliases_8.602-0ubuntu1_amd64.deb || fail_and_cleanup
cleanup || echo "Unable to cleanup $WORKDIR" >&2
printf "Save your work.  Hit enter to restart X with fglrx..."
aticonfig --initial
/etc/init.d/gdm restart

```

If it has syntax errors, let me know (I haven't tested it - I just built it from the steps you need to do).

---

### Post by Akkifokkusu on 2009-04-18
What doesn't work is that when I boot into Ubuntu, it shows me a terminal-like prompt, then I guess tries to load X, which crashes and leaves me with a bunch of colorful static-looking stuff on my screen, which I can't do anything with. I ran aticonfig. Here are the instructions I followed (with both 9.3 and 9.4): [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

And that was only after trying it with Aptitude and Jockey.

I can't post the output of dmesg because it's too long to see. Also can't attach Xorg, but at least I can post that.

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux igor-laptop 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:39:23 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 17 22:58:39 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series] rev 0, Mem @ 0xe0000000/268435456, 0xdfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeonhd from file name radeonhd.ids
(==) Matched radeonhd for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.5.99.902, module version = 1.2.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
	M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.
	RS740 : RS740, RS740M.
	RS780 : Radeon HD 3100/3200/3300 Series.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	R700  : Radeon R700.
	M98   : Radeon M98 Mobility.
	RV730 : Radeon HD4670, HD4650.
	M96   : Radeon M96 Mobility.
	RV710 : Radeon HD4570, HD4350.

(II) RADEONHD: version 1.2.4, built from dist of git branch master, commit 4e897263

(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(EE) RADEONHD(0): The fglrx kernel module is loaded. This can have obvious
     or subtle side effects. See radeonhd(4) for details.
(II) RADEONHD(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Selected ShadowFB.
(II) RADEONHD(0): Unknown card detected: 0x9581:0x10CF:0x1432.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9581:0x10CF:0x1432: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an M76 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xdfef0000 to 0x7fe96dfad000 (size 0x00010000)
(II) RADEONHD(0): PCIE Card Detected
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x10cf SubsystemID: 0x1432
	IOBaseAddress: 0x2000
	Filename: br25637.003 
	BIOS Bootup Message: 

Fujitsu Baikal M76M A15 GDDR3 500e/600m                                     


(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 19
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0xfffb400
(II) RADEONHD(0): AtomBIOS requests 19kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0xfffb400
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0xffff401 VRAM End: 0x10000000
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 500000
(II) RADEONHD(0): Default Memory Clock: 600000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): Direct rendering turned off by default. Use Option "DRI" to enable.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f80
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f80
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_VGA, "VGA CRT1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_PANEL, "LVDS LCD1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_LVTMA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI_SINGLE, "HDMI_TYPE_A DFP1", RHD_DDC_1, RHD_HPD_0, { RHD_OUTPUT_TMDSA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[3] {RHD_CONNECTOR_TV, "7PIN_DIN TV1 CV", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(--) RADEONHD(0): Attaching Output DAC A to Connector VGA 1
(II) RADEONHD(0): LVDS SEQ Dig onto DE: 0
(II) RADEONHD(0): LVDS SEQ DE to BL: 20
(II) RADEONHD(0): LVDS Off Delay: 500
(II) RADEONHD(0): LVDS Duallink: 0x1
(II) RADEONHD(0): LVDS 24Bit: 0x0
(II) RADEONHD(0): LVDS FPDI: 0x0
(II) RADEONHD(0): LVDS Temporal Dither : 0x1
(II) RADEONHD(0): LVDS Spatial Dither : 0x0
(II) RADEONHD(0): LVDS Grey Level: 0x3
(II) RADEONHD(0): AtomBIOS returned 3 Grey Levels
(--) RADEONHD(0): Detected a 18bit dual link panel.
(--) RADEONHD(0): Attaching Output LVDS to Connector PANEL
(==) RADEONHD(0): Setting TMDS A to incoherent
(--) RADEONHD(0): Attaching Output TMDS A to Connector DVI-D 1
(--) RADEONHD(0): Attaching Output DAC B to Connector TV 7PIN_DIN
(II) RADEONHD(0): RandR: Adding RRoutput VGA_1 for Output DAC A
(II) RADEONHD(0): RandR: Adding RRoutput PANEL for Output LVDS
(II) RADEONHD(0): RandR: Adding RRoutput DVI-D_1 for Output TMDS A
(II) RADEONHD(0): RandR: Adding RRoutput TV_7PIN_DIN for Output DAC B
(II) RADEONHD(0): Output VGA_1 using monitor section Configured Monitor
(II) RADEONHD(0): Output PANEL has no monitor section
(II) RADEONHD(0): Output DVI-D_1 has no monitor section
(II) RADEONHD(0): Output TV_7PIN_DIN has no monitor section
(II) RADEONHD(0): I2C device "RHD I2C line 0:E-EDID segment register" registered at address 0x60.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Output VGA_1 disconnected
(II) RADEONHD(0): Output PANEL connected
(II) RADEONHD(0): Output DVI-D_1 disconnected
(II) RADEONHD(0): Output TV_7PIN_DIN disconnected
(II) RADEONHD(0): Using exact sizes for initial modes
(II) RADEONHD(0): Output PANEL using initial mode 1440x900
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2560x2560 Framebuffer with 2560 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x01900000)
(==) RADEONHD(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEONHD(0): Using ShadowFB
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEONHD(0): Mapped IO @ 0xdfef0000 to 0x7fe96dfad000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xe0000000 to 0x7fe95991c000 (size 0x10000000)
(WW) RADEONHD(0): RHDCSInit: No CS for R600 and up yet.
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEONHD(0): On Crtc 0 Setting 59.9 Hz Mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
None
(II) RADEONHD(0): LVDSSetBacklight: trying to set BL_MOD_LEVEL to: 255
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): DPMS enabled
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 381 x 238
(II) config/hal: Adding input device Fujitsu FUJ02B1
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Fujitsu FUJ02B1: always reports core events
(**) Fujitsu FUJ02B1: Device: "/dev/input/event6"
(II) Fujitsu FUJ02B1: Found keys
(II) Fujitsu FUJ02B1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02B1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02B1: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02B1: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02B1: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Fujitsu FUJ02E3
(**) Fujitsu FUJ02E3: always reports core events
(**) Fujitsu FUJ02E3: Device: "/dev/input/event7"
(II) Fujitsu FUJ02E3: Found keys
(II) Fujitsu FUJ02E3: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02E3" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02E3: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02E3: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02E3: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event9"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(**) Option "SHMConfig" "On"
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(**) Option "EmulateTwoFingerMinZ" "90"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stoped with 1 channels, 48000 Hz sampling rate, 8 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x00 IEC60958 status bits and 0x00 category code
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): In rhdRROutputGetProperty
```

---

### Post by vlovich on 2009-04-18
You're definitely trying to load the radeon drivers - not fglrx.  Use my script above.

---

### Post by Akkifokkusu on 2009-04-18
You might get that impression because I'm using the radeon drivers right now cause... fglrx doesn't work. I haven't been able to get ANYWHERE using it, so...

---

### Post by vlovich on 2009-04-18
Use my script.  I'm 90% confident that it'll fix your issue with fglrx.  

Also, what would be the point of posting your X log for radeonhd if your trying to install fglrx?

Also, for dmesg, something like dmesg > log.txt or dmesg | tail -n 100.

But first try the script.

---

### Post by MALEADt on 2009-04-18
If you'd google it a bit, you'd see your HD 2600 has an R600 chipset. R600 is supported by open-source drivers, but without 3D acceleration (ergo, no compiz). If you want Compiz, as the topic title might suggest, you definitely need fglrx, which should work out-of-the-box, without any hacky shell scripts.
Does jockey-gtk (restricted drivers wizard, or however it's called) detect your gpu? Does it suggest fglrx to install? You might try removing and purging all fglrx and -ati related packages and try again. If it still doesn't work after that, you might however need to reinstall Jaunty, as I couldn't get fglrx installed properly either after upgrading from Intrepid (ATi HD4870, R700). Reinstalling Jaunty fixed this, jockey-gtk successfully detected my GPU and installed fglrx automagically.

Bottom line: no need to revert to Intrepid, as your GPU is supported by Catalyst 9.4.

---

### Post by carrozza on 2009-04-18
Thank Akkifokkusu and all other for this helpful thread; I have the same graphics card and was stuck to 8.10 because of no 3D support on 9.04.

Now I read that official 9.04 drivers are out and working of the new X.org server in Jaunty.

Will definately try this stuff out and report back soon.
Thank guys! ;)

---

### Post by Akkifokkusu on 2009-04-18
Well, the script didn't work. Thanks anyway though. On the other hand, I did manage to get the log file and dmesg from the recovery console, so if that's any help:

Xorg.0.log
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux igor-laptop 2.6.28-11-generic #41-Ubuntu SMP Wed Apr 8 04:39:23 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 17 22:58:39 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series] rev 0, Mem @ 0xe0000000/268435456, 0xdfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeonhd from file name radeonhd.ids
(==) Matched radeonhd for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeonhd"
(II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
(II) Module radeonhd: vendor="AMD GPG"
	compiled for 1.5.99.902, module version = 1.2.4
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
	RV505 : Radeon X1550, X1550 64bit.
	RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
	RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
	R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
	RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
	RV535 : Radeon X1300, X1650.
	RV550 : Radeon X2300 HD.
	RV560 : Radeon X1650.
	RV570 : Radeon X1950, X1950 GT; FireGL V7400.
	R580  : Radeon X1900, X1950; AMD Stream Processor.
	R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
	RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
	RV620 : Radeon HD 3450, HD 3470.
	RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
		FireGL V3600/V5600.
	RV635 : Radeon HD 3650, HD 3670.
	RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
	R680  : Radeon HD 3870 X2.
	M52   : Mobility Radeon X1300.
	M54   : Mobility Radeon X1400; M54-GL.
	M56   : Mobility Radeon X1600; Mobility FireGL V5200.
	M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
	M62   : Mobility Radeon X1350.
	M64   : Mobility Radeon X1450, X2300.
	M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
	M68   : Mobility Radeon X1900.
	M71   : Mobility Radeon HD 2300.
	M72   : Mobility Radeon HD 2400; Radeon E2400.
	M74   : Mobility Radeon HD 2400 XT.
	M76   : Mobility Radeon HD 2600;
		(Gemini ATI) Mobility Radeon HD 2600 XT.
	M82   : Mobility Radeon HD 3400.
	M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
	M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
	RS600 : Radeon Xpress 1200, Xpress 1250.
	RS690 : Radeon X1200, X1250, X1270.
	RS740 : RS740, RS740M.
	RS780 : Radeon HD 3100/3200/3300 Series.
	RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
	R700  : Radeon R700.
	M98   : Radeon M98 Mobility.
	RV730 : Radeon HD4670, HD4650.
	M96   : Radeon M96 Mobility.
	RV710 : Radeon HD4570, HD4350.

(II) RADEONHD: version 1.2.4, built from dist of git branch master, commit 4e897263

(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(EE) RADEONHD(0): The fglrx kernel module is loaded. This can have obvious
     or subtle side effects. See radeonhd(4) for details.
(II) RADEONHD(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Selected ShadowFB.
(II) RADEONHD(0): Unknown card detected: 0x9581:0x10CF:0x1432.
	If - and only if - your card does not work or does not work optimally
	please contact radeonhd@opensuse.org to help rectify this.
	Use the subject: 0x9581:0x10CF:0x1432: <name of board>
	and *please* describe the problems you are seeing
	in your message.
(--) RADEONHD(0): Detected an M76 on an unidentified card
(II) RADEONHD(0): Mapped IO @ 0xdfef0000 to 0x7fe96dfad000 (size 0x00010000)
(II) RADEONHD(0): PCIE Card Detected
(II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
(II) RADEONHD(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x10cf SubsystemID: 0x1432
	IOBaseAddress: 0x2000
	Filename: br25637.003 
	BIOS Bootup Message: 

Fujitsu Baikal M76M A15 GDDR3 500e/600m                                     


(II) RADEONHD(0): Analog TV Default Mode: 1
(II) RADEONHD(0): Found default TV Mode NTSC
(--) RADEONHD(0): VideoRAM: 262144 kByte
(II) RADEONHD(0): Framebuffer space used by Firmware (kb): 19
(II) RADEONHD(0): Start of VRAM area used by Firmware: 0xfffb400
(II) RADEONHD(0): AtomBIOS requests 19kB of VRAM scratch space
(II) RADEONHD(0): AtomBIOS VRAM scratch base: 0xfffb400
(WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area not located at the end of VRAM. Scratch End: 0xffff401 VRAM End: 0x10000000
(II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEONHD(0): Default Engine Clock: 500000
(II) RADEONHD(0): Default Memory Clock: 600000
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): Direct rendering turned off by default. Use Option "DRI" to enable.
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
(II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f80
(II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
(II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f80
(II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
(II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) RADEONHD(0): Detected VGA mode.
(II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEONHD(0): Maximum Pixel Clock: 400000
(II) RADEONHD(0): Reference Clock: 27000
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
(II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
(II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_VGA, "VGA CRT1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_PANEL, "LVDS LCD1", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_LVTMA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI_SINGLE, "HDMI_TYPE_A DFP1", RHD_DDC_1, RHD_HPD_0, { RHD_OUTPUT_TMDSA, RHD_OUTPUT_NONE } }
(II) RADEONHD(0): Connector[3] {RHD_CONNECTOR_TV, "7PIN_DIN TV1 CV", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
(--) RADEONHD(0): Attaching Output DAC A to Connector VGA 1
(II) RADEONHD(0): LVDS SEQ Dig onto DE: 0
(II) RADEONHD(0): LVDS SEQ DE to BL: 20
(II) RADEONHD(0): LVDS Off Delay: 500
(II) RADEONHD(0): LVDS Duallink: 0x1
(II) RADEONHD(0): LVDS 24Bit: 0x0
(II) RADEONHD(0): LVDS FPDI: 0x0
(II) RADEONHD(0): LVDS Temporal Dither : 0x1
(II) RADEONHD(0): LVDS Spatial Dither : 0x0
(II) RADEONHD(0): LVDS Grey Level: 0x3
(II) RADEONHD(0): AtomBIOS returned 3 Grey Levels
(--) RADEONHD(0): Detected a 18bit dual link panel.
(--) RADEONHD(0): Attaching Output LVDS to Connector PANEL
(==) RADEONHD(0): Setting TMDS A to incoherent
(--) RADEONHD(0): Attaching Output TMDS A to Connector DVI-D 1
(--) RADEONHD(0): Attaching Output DAC B to Connector TV 7PIN_DIN
(II) RADEONHD(0): RandR: Adding RRoutput VGA_1 for Output DAC A
(II) RADEONHD(0): RandR: Adding RRoutput PANEL for Output LVDS
(II) RADEONHD(0): RandR: Adding RRoutput DVI-D_1 for Output TMDS A
(II) RADEONHD(0): RandR: Adding RRoutput TV_7PIN_DIN for Output DAC B
(II) RADEONHD(0): Output VGA_1 using monitor section Configured Monitor
(II) RADEONHD(0): Output PANEL has no monitor section
(II) RADEONHD(0): Output DVI-D_1 has no monitor section
(II) RADEONHD(0): Output TV_7PIN_DIN has no monitor section
(II) RADEONHD(0): I2C device "RHD I2C line 0:E-EDID segment register" registered at address 0x60.
(II) RADEONHD(0): I2C device "RHD I2C line 0:ddc2" registered at address 0xA0.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Output VGA_1 disconnected
(II) RADEONHD(0): Output PANEL connected
(II) RADEONHD(0): Output DVI-D_1 disconnected
(II) RADEONHD(0): Output TV_7PIN_DIN disconnected
(II) RADEONHD(0): Using exact sizes for initial modes
(II) RADEONHD(0): Output PANEL using initial mode 1440x900
(II) RADEONHD(0): RandR 1.2 support enabled
(==) RADEONHD(0): RGB weight 888
(==) RADEONHD(0): Default visual is TrueColor
(==) RADEONHD(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEONHD(0): Using 2560x2560 Framebuffer with 2560 pitch
(II) RADEONHD(0): FB: Allocated ScanoutBuffer at offset 0x00008000 (size = 0x01900000)
(==) RADEONHD(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEONHD(0): Using ShadowFB
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEONHD(0): Mapped IO @ 0xdfef0000 to 0x7fe96dfad000 (size 0x00010000)
(II) RADEONHD(0): Mapped FB @ 0xe0000000 to 0x7fe95991c000 (size 0x10000000)
(WW) RADEONHD(0): RHDCSInit: No CS for R600 and up yet.
(==) RADEONHD(0): Backing store disabled
(==) RADEONHD(0): Silken mouse enabled
(II) RADEONHD(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) RADEONHD(0): On Crtc 0 Setting 59.9 Hz Mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
None
(II) RADEONHD(0): LVDSSetBacklight: trying to set BL_MOD_LEVEL to: 255
(II) RADEONHD(0): RHDAudioSetSupported: config 0x60040 codec 0x1
(II) RADEONHD(0): DPMS enabled
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) RADEONHD(0): Setting screen physical size to 381 x 238
(II) config/hal: Adding input device Fujitsu FUJ02B1
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Fujitsu FUJ02B1: always reports core events
(**) Fujitsu FUJ02B1: Device: "/dev/input/event6"
(II) Fujitsu FUJ02B1: Found keys
(II) Fujitsu FUJ02B1: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02B1" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02B1: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02B1: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02B1: xkb_layout: "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Fujitsu FUJ02E3
(**) Fujitsu FUJ02E3: always reports core events
(**) Fujitsu FUJ02E3: Device: "/dev/input/event7"
(II) Fujitsu FUJ02E3: Found keys
(II) Fujitsu FUJ02E3: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu FUJ02E3" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Fujitsu FUJ02E3: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Fujitsu FUJ02E3: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Fujitsu FUJ02E3: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event9"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event10"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(**) Option "SHMConfig" "On"
(II) ALPS touchpad detected: AlpsPS/2 ALPS GlidePoint. Applying customised settings...
(**) Option "EmulateTwoFingerMinZ" "90"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
(**) Option "TapButton1" "1"
(**) Option "TapButton2" "3"
(**) Option "TapButton3" "2"
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint touchpad found
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: stoped with 1 channels, 48000 Hz sampling rate, 8 bits per sample,
(II) RADEONHD(0): RHDHdmiUpdateAudioSettings: 0x00 IEC60958 status bits and 0x00 category code
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): Query for AtomBIOS Get Panel EDID: failed
(II) RADEONHD(0): Found native mode: Modeline "1440x900"   96.20  1440 1488 1520 1760  900 903 909 912
(WW) RADEONHD(0): No monitor size info, assuming 96dpi.
(II) RADEONHD(0): In rhdRROutputGetProperty
```

dmesg
```
[    0.000000] BIOS EBDA/lowmem at: 0009e000/0009e000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] Command line: root=UUID=17ea7057-8f8a-470a-ab7d-4cb463d9e5ac ro  single
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
[    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe60000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe60000 - 00000000cfe72000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe72000 - 00000000cfe74000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfe74000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcfe60 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009e000 (usable)
[    0.000000]  modified: 000000000009e000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfe60000 (usable)
[    0.000000]  modified: 00000000cfe60000 - 00000000cfe72000 (ACPI data)
[    0.000000]  modified: 00000000cfe72000 - 00000000cfe74000 (ACPI NVS)
[    0.000000]  modified: 00000000cfe74000 - 00000000d0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfe60000
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfe60000 page 4k
[    0.000000] kernel direct mapping tables up to cfe60000 @ 10000-16000
[    0.000000] last_map_addr: cfe60000 end: cfe60000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000
[    0.000000] last_map_addr: 130000000 end: 130000000
[    0.000000] RAMDISK: 3785a000 - 37fef503
[    0.000000] ACPI: RSDP 000F69A0, 0024 (r2 FUJ   )
[    0.000000] ACPI: XSDT CFE6A37E, 006C (r1 FUJ    PC        1030000 FUJ       100)
[    0.000000] ACPI: FACP CFE70956, 00F4 (r3 FUJ    PC        1030000 FUJ       100)
[    0.000000] ACPI: DSDT CFE6A3EA, 656C (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: FACS CFE73FC0, 0040
[    0.000000] ACPI: HPET CFE70A4A, 0038 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: MCFG CFE70A82, 003C (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: SSDT CFE70ABE, 04EF (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: SSDT CFE70FAD, 01CA (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: SSDT CFE71177, 0C0F (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: APIC CFE71D86, 0068 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: BOOT CFE71DEE, 0028 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.000000] ACPI: SLIC CFE71E16, 0176 (r1 FUJ    PC        1030000 FUJ       100)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [003785a000 - 0037fef503]          RAMDISK ==> [003785a000 - 0037fef503]
[    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]
[    0.000000]   #6 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]
[    0.000000]  [ffffe20000000000-ffffe200043fffff] PMD -> [ffff880028200000-ffff88002c5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cfe60
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048046
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2543 pages reserved
[    0.000000]   DMA zone: 1383 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833176 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfe60000 - 00000000cfe72000
[    0.000000] PM: Registered nosave memory: 00000000cfe72000 - 00000000cfe74000
[    0.000000] PM: Registered nosave memory: 00000000cfe74000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:28000000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1028479
[    0.000000] Kernel command line: root=UUID=17ea7057-8f8a-470a-ab7d-4cb463d9e5ac ro  single
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.392 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] allocated 49807360 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3982968k/4980736k available (4760k kernel code, 788552k absent, 208252k reserved, 2540k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.78 BogoMIPS (lpj=5985568)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004018] ACPI: Core revision 20080926
[    0.006514] ACPI: Checking initramfs for custom DSDT
[    0.452061] Setting APIC routing to flat
[    0.452543] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.494468] CPU0: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz stepping 0d
[    0.496001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 2992.44 BogoMIPS (lpj=5984891)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.580547] CPU1: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz stepping 0d
[    0.581081] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.584049] Brought up 2 CPUs
[    0.584109] Total of 2 processors activated (5985.22 BogoMIPS).
[    0.584222] CPU0 attaching sched-domain:
[    0.584225]  domain 0: span 0-1 level MC
[    0.584228]   groups: 0 1
[    0.584234] CPU1 attaching sched-domain:
[    0.584236]  domain 0: span 0-1 level MC
[    0.584238]   groups: 1 0
[    0.584317] net_namespace: 1400 bytes
[    0.584317] Booting paravirtualized kernel on bare hardware
[    0.585090] Time:  1:59:33  Date: 04/18/09
[    0.585090] regulator: core version 0.5
[    0.585090] NET: Registered protocol family 16
[    0.585090] ACPI: bus type pci registered
[    0.585090] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.585090] PCI: MCFG area at f8000000 reserved in E820
[    0.591145] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.591220] PCI: Using configuration type 1 for base access
[    0.593142] ACPI: EC: Look up EC in DSDT
[    0.597459] ACPI: SSDT CFE73A93, 03C3 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    0.600760] ACPI: Interpreter enabled
[    0.600820] ACPI: (supports S0 S3 S4 S5)
[    0.601083] ACPI: Using IOAPIC for interrupt routing
[    0.608898] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.608962] ACPI: EC: driver started in poll mode
[    0.609250] ACPI: No dock devices found.
[    0.609317] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.609487] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.609549] pci 0000:00:01.0: PME# disabled
[    0.609704] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.609776] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.609857] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe504800-0xfe504bff]
[    0.609910] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.609974] pci 0000:00:1a.7: PME# disabled
[    0.610091] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe500000-0xfe503fff]
[    0.610138] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.610218] pci 0000:00:1b.0: PME# disabled
[    0.610350] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.610413] pci 0000:00:1c.0: PME# disabled
[    0.610551] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.610613] pci 0000:00:1c.2: PME# disabled
[    0.610747] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.610810] pci 0000:00:1c.3: PME# disabled
[    0.610940] pci 0000:00:1d.0: reg 20 io port: [0x1840-0x185f]
[    0.611011] pci 0000:00:1d.1: reg 20 io port: [0x1860-0x187f]
[    0.611081] pci 0000:00:1d.2: reg 20 io port: [0x1880-0x189f]
[    0.611167] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe504c00-0xfe504fff]
[    0.611240] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.611305] pci 0000:00:1d.7: PME# disabled
[    0.611530] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.611603] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.611701] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.611710] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.611719] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.611727] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.611736] pci 0000:00:1f.1: reg 20 io port: [0x18a0-0x18af]
[    0.611817] pci 0000:00:1f.2: reg 10 io port: [0x18d8-0x18df]
[    0.611826] pci 0000:00:1f.2: reg 14 io port: [0x18cc-0x18cf]
[    0.611835] pci 0000:00:1f.2: reg 18 io port: [0x18d0-0x18d7]
[    0.611843] pci 0000:00:1f.2: reg 1c io port: [0x18c8-0x18cb]
[    0.611852] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.611860] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe504000-0xfe5047ff]
[    0.611884] pci 0000:00:1f.2: PME# supported from D3hot
[    0.611947] pci 0000:00:1f.2: PME# disabled
[    0.612039] pci 0000:00:1f.3: reg 10 32bit mmio: [0x000000-0x0000ff]
[    0.612068] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.612139] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xefffffff]
[    0.612148] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.612157] pci 0000:01:00.0: reg 18 32bit mmio: [0xdfef0000-0xdfefffff]
[    0.612186] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.612199] pci 0000:01:00.0: supports D1 D2
[    0.612252] pci 0000:01:00.1: reg 10 32bit mmio: [0xdfeec000-0xdfeeffff]
[    0.612305] pci 0000:01:00.1: supports D1 D2
[    0.612385] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.612389] pci 0000:00:01.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.612394] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.612487] pci 0000:04:00.0: reg 10 64bit mmio: [0xfe000000-0xfe003fff]
[    0.612500] pci 0000:04:00.0: reg 18 io port: [0x3000-0x30ff]
[    0.612540] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.612558] pci 0000:04:00.0: supports D1 D2
[    0.612560] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.612624] pci 0000:04:00.0: PME# disabled
[    0.612753] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.612759] pci 0000:00:1c.0: bridge 32bit mmio: [0xfe000000-0xfe0fffff]
[    0.612951] pci 0000:0c:00.0: reg 10 64bit mmio: [0xfe100000-0xfe101fff]
[    0.613101] pci 0000:0c:00.0: PME# supported from D0 D3hot D3cold
[    0.613203] pci 0000:0c:00.0: PME# disabled
[    0.613390] pci 0000:00:1c.2: bridge 32bit mmio: [0xfe100000-0xfe1fffff]
[    0.613463] pci 0000:00:1c.3: bridge io port: [0x00-0xfff]
[    0.613469] pci 0000:00:1c.3: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.613478] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.613535] pci 0000:1c:03.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.613549] pci 0000:1c:03.0: supports D1 D2
[    0.613551] pci 0000:1c:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613616] pci 0000:1c:03.0: PME# disabled
[    0.613724] pci 0000:1c:03.2: reg 10 32bit mmio: [0xfe202800-0xfe2028ff]
[    0.613782] pci 0000:1c:03.2: supports D1 D2
[    0.613784] pci 0000:1c:03.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.613845] pci 0000:1c:03.2: PME# disabled
[    0.613952] pci 0000:1c:03.3: reg 10 32bit mmio: [0xfe200000-0xfe200fff]
[    0.614011] pci 0000:1c:03.3: supports D1 D2
[    0.614013] pci 0000:1c:03.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.614076] pci 0000:1c:03.3: PME# disabled
[    0.614196] pci 0000:1c:03.4: reg 10 32bit mmio: [0xfe201000-0xfe201fff]
[    0.614205] pci 0000:1c:03.4: reg 14 32bit mmio: [0xfe202000-0xfe2027ff]
[    0.614251] pci 0000:1c:03.4: supports D1 D2
[    0.614253] pci 0000:1c:03.4: PME# supported from D0 D1 D2 D3hot
[    0.614317] pci 0000:1c:03.4: PME# disabled
[    0.614439] pci 0000:00:1e.0: transparent bridge
[    0.614505] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe200000-0xfe2fffff]
[    0.614571] bus 00 -> node 0
[    0.614581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.615049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.615255] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.615448] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.615637] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.615857] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.620322] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.621152] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.621939] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.622774] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.623564] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.624373] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.625141] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.625974] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.626795] ACPI: WMI: Mapper loaded
[    0.626903] SCSI subsystem initialized
[    0.626903] libata version 3.00 loaded.
[    0.626903] usbcore: registered new interface driver usbfs
[    0.626903] usbcore: registered new interface driver hub
[    0.626903] usbcore: registered new device driver usb
[    0.626903] PCI: Using ACPI for IRQ routing
[    0.626903] pci 0000:00:1c.3: BAR 7: can't allocate resource
[    0.626903] pci 0000:00:1c.3: BAR 8: can't allocate resource
[    0.626903] pci 0000:00:1c.3: BAR 9: can't allocate resource
[    0.640012] Bluetooth: Core ver 2.13
[    0.640081] NET: Registered protocol family 31
[    0.640086] Bluetooth: HCI device and connection manager initialized
[    0.640152] Bluetooth: HCI socket layer initialized
[    0.640213] NET: Registered protocol family 8
[    0.640272] NET: Registered protocol family 20
[    0.640342] NetLabel: Initializing
[    0.640400] NetLabel:  domain hash size = 128
[    0.640459] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.640533] NetLabel:  unlabeled traffic allowed by default
[    0.640629] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.640873] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.644072] AppArmor: AppArmor Filesystem Enabled
[    0.648010] Switched to high resolution mode on CPU 0
[    0.649244] Switched to high resolution mode on CPU 1
[    0.656011] pnp: PnP ACPI init
[    0.656076] ACPI: bus type pnp registered
[    0.660019] pnp: PnP ACPI: found 9 devices
[    0.660080] ACPI: ACPI bus type pnp unregistered
[    0.660153] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.660229] system 00:01: ioport range 0x680-0x69f has been reserved
[    0.660289] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.660350] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.660410] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.660472] system 00:01: ioport range 0x1100-0x111f has been reserved
[    0.660533] system 00:01: ioport range 0x1180-0x11bf has been reserved
[    0.660599] system 00:01: ioport range 0x1640-0x164f has been reserved
[    0.660661] system 00:01: ioport range 0xf800-0xf87f has been reserved
[    0.660723] system 00:01: ioport range 0xf880-0xf8ff has been reserved
[    0.660785] system 00:01: ioport range 0xfc00-0xfc7f has been reserved
[    0.660845] system 00:01: ioport range 0xfc80-0xfcff has been reserved
[    0.660906] system 00:01: ioport range 0xfd00-0xfd7f has been reserved
[    0.660966] system 00:01: ioport range 0xfe00-0xfe03 has been reserved
[    0.661031] system 00:02: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.661093] system 00:02: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.661155] system 00:02: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.661229] system 00:02: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.661291] system 00:02: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.661354] system 00:02: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.661417] system 00:02: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.661479] system 00:02: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.661542] system 00:02: iomem range 0xfef00000-0xfeffffff has been reserved
[    0.666379] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.666442] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.666504] pci 0000:00:01.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.666566] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.666639] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.666702] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.666767] pci 0000:00:1c.0:   MEM window: 0xfe000000-0xfe0fffff
[    0.666831] pci 0000:00:1c.0:   PREFETCH window: 0x000000d8000000-0x000000d80fffff
[    0.666907] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:0c
[    0.666965] pci 0000:00:1c.2:   IO window: disabled
[    0.667029] pci 0000:00:1c.2:   MEM window: 0xfe100000-0xfe1fffff
[    0.667092] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.667165] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:10
[    0.667236] pci 0000:00:1c.3:   IO window: disabled
[    0.667300] pci 0000:00:1c.3:   MEM window: disabled
[    0.667362] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.667436] pci 0000:1c:03.0: CardBus bridge, secondary bus 0000:1d
[    0.667495] pci 0000:1c:03.0:   IO window: 0x004000-0x0040ff
[    0.667559] pci 0000:1c:03.0:   IO window: 0x004400-0x0044ff
[    0.667622] pci 0000:1c:03.0:   PREFETCH window: 0xd4000000-0xd7ffffff
[    0.667686] pci 0000:1c:03.0:   MEM window: 0xf0000000-0xf3ffffff
[    0.667752] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:1c
[    0.667815] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.667878] pci 0000:00:1e.0:   MEM window: 0xfe200000-0xfe2fffff
[    0.667941] pci 0000:00:1e.0:   PREFETCH window: 0x000000d4000000-0x000000d7ffffff
[    0.668032] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.668095] pci 0000:00:01.0: setting latency timer to 64
[    0.668104] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.668183] pci 0000:00:1c.0: setting latency timer to 64
[    0.668198] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.668265] pci 0000:00:1c.2: setting latency timer to 64
[    0.668275] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.668340] pci 0000:00:1c.3: setting latency timer to 64
[    0.668348] pci 0000:00:1e.0: setting latency timer to 64
[    0.668360] pci 0000:1c:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.668427] bus: 00 index 0 io port: [0x00-0xffff]
[    0.668487] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.668547] bus: 01 index 0 io port: [0x2000-0x2fff]
[    0.668606] bus: 01 index 1 mmio: [0xdfe00000-0xdfefffff]
[    0.668665] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.668725] bus: 01 index 3 mmio: [0x0-0x0]
[    0.668786] bus: 04 index 0 io port: [0x3000-0x3fff]
[    0.668847] bus: 04 index 1 mmio: [0xfe000000-0xfe0fffff]
[    0.668907] bus: 04 index 2 mmio: [0xd8000000-0xd80fffff]
[    0.668966] bus: 04 index 3 mmio: [0x0-0x0]
[    0.669026] bus: 0c index 0 mmio: [0x0-0x0]
[    0.669085] bus: 0c index 1 mmio: [0xfe100000-0xfe1fffff]
[    0.669144] bus: 0c index 2 mmio: [0x0-0x0]
[    0.669222] bus: 0c index 3 mmio: [0x0-0x0]
[    0.669281] bus: 10 index 0 mmio: [0x0-0xfff]
[    0.669338] bus: 10 index 1 mmio: [0x0-0xfffff]
[    0.669396] bus: 10 index 2 mmio: [0x0-0xfffff]
[    0.669455] bus: 10 index 3 mmio: [0x0-0x0]
[    0.669511] bus: 1c index 0 io port: [0x4000-0x4fff]
[    0.669570] bus: 1c index 1 mmio: [0xfe200000-0xfe2fffff]
[    0.669629] bus: 1c index 2 mmio: [0xd4000000-0xd7ffffff]
[    0.669689] bus: 1c index 3 io port: [0x00-0xffff]
[    0.669750] bus: 1c index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.669810] bus: 1d index 0 io port: [0x4000-0x40ff]
[    0.669869] bus: 1d index 1 io port: [0x4400-0x44ff]
[    0.669930] bus: 1d index 2 mmio: [0xd4000000-0xd7ffffff]
[    0.669989] bus: 1d index 3 mmio: [0xf0000000-0xf3ffffff]
[    0.670057] NET: Registered protocol family 2
[    0.704065] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.704745] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.707130] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.707911] TCP: Hash tables configured (established 262144 bind 65536)
[    0.707974] TCP reno registered
[    0.720128] NET: Registered protocol family 1
[    0.720356] checking if image is initramfs... it is
[    1.615531] Freeing initrd memory: 7765k freed
[    1.619983] Simple Boot Flag at 0x7b set to 0x1
[    1.620454] audit: initializing netlink socket (disabled)
[    1.620541] type=2000 audit(1240019973.620:1): initialized
[    1.631607] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.633205] VFS: Disk quotas dquot_6.5.1
[    1.633325] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.634075] fuse init (API version 7.10)
[    1.634235] msgmni has been set to 7796
[    1.634485] alg: No test for stdrng (krng)
[    1.634557] io scheduler noop registered
[    1.634619] io scheduler anticipatory registered
[    1.634679] io scheduler deadline registered
[    1.634782] io scheduler cfq registered (default)
[    1.635043] pci 0000:01:00.0: Boot video device
[    1.639866] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.639909] pcieport-driver 0000:00:01.0: found MSI capability
[    1.640021] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.640032] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.640049] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.640063] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.640136] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.640237] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.640389] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.640422] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.640439] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.640453] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.640602] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.640702] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.640851] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.640884] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.640899] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.640912] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.641065] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.641160] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.641318] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.641351] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.641366] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.641382] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.641515] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.642095] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.642424] ACPI: AC Adapter [AC] (on-line)
[    1.643667] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.646399] ACPI: Battery Slot [CMB1] (battery present)
[    1.646561] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.646647] ACPI: Power Button (FF) [PWRF]
[    1.646786] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.646956] ACPI: Lid Switch [LID]
[    1.647082] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.647171] ACPI: Power Button (CM) [PWRB]
[    1.648279] ACPI: SSDT CFE72DD9, 01B4 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    1.649064] ACPI: SSDT CFE732D9, 046E (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    1.649807] Monitor-Mwait will be used to enter C-1 state
[    1.649811] Monitor-Mwait will be used to enter C-2 state
[    1.649813] Monitor-Mwait will be used to enter C-3 state
[    1.649830] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.650169] processor ACPI_CPU:00: registered as cooling_device0
[    1.650700] ACPI: SSDT CFE73221, 00B8 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    1.651369] ACPI: SSDT CFE73747, 0047 (r1 FUJ    FJNB1D2   1030000 FUJ       100)
[    1.652179] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.652517] processor ACPI_CPU:01: registered as cooling_device1
[    1.656502] thermal LNXTHERM:01: registered as thermal_zone0
[    1.656700] ACPI: Thermal Zone [TZ00] (27 C)
[    1.657246] thermal LNXTHERM:02: registered as thermal_zone1
[    1.657459] ACPI: Thermal Zone [TZ01] (27 C)
[    1.685147] Linux agpgart interface v0.103
[    1.685233] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.686398] brd: module loaded
[    1.686844] loop: module loaded
[    1.686990] Fixed MDIO Bus: probed
[    1.687073] PPP generic driver version 2.4.2
[    1.687218] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.687332] Driver 'sd' needs updating - please use bus_type methods
[    1.687422] Driver 'sr' needs updating - please use bus_type methods
[    1.687548] ahci 0000:00:1f.2: version 3.0
[    1.687572] ahci 0000:00:1f.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.687702] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.687787] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.687875] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    1.687962] ahci 0000:00:1f.2: setting latency timer to 64
[    1.688242] scsi0 : ahci
[    1.688423] scsi1 : ahci
[    1.688560] scsi2 : ahci
[    1.688729] ata1: SATA max UDMA/133 abar m2048@0xfe504000 port 0xfe504100 irq 2299
[    1.688817] ata2: SATA max UDMA/133 abar m2048@0xfe504000 port 0xfe504180 irq 2299
[    1.688908] ata3: SATA max UDMA/133 abar m2048@0xfe504000 port 0xfe504200 irq 2299
[    2.008028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.008686] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.008764] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.008956] ata1.00: ATA-7: FUJITSU MHV2200BT PL, 0000004F, max UDMA/100
[    2.009040] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.009808] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.009891] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.010100] ata1.00: configured for UDMA/100
[    2.344022] ata2: SATA link down (SStatus 0 SControl 300)
[    3.084024] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.085517] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.085600] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.085969] ata3.00: ATA-8: ST9500325AS, 0001SDM1, max UDMA/133
[    3.086051] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.087902] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.087977] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.088348] ata3.00: configured for UDMA/133
[    3.104130] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2200B 0000 PQ: 0 ANSI: 5
[    3.104324] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    3.104429] sd 0:0:0:0: [sda] Write Protect is off
[    3.104507] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.104539] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.104700] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    3.104803] sd 0:0:0:0: [sda] Write Protect is off
[    3.104878] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.104910] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.104999]  sda: sda1 sda2 sda3
[    3.146653] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.146780] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.146934] scsi 2:0:0:0: Direct-Access     ATA      ST9500325AS      0001 PQ: 0 ANSI: 5
[    3.147115] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.147214] sd 2:0:0:0: [sdb] Write Protect is off
[    3.147296] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.147328] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.147475] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.147577] sd 2:0:0:0: [sdb] Write Protect is off
[    3.147656] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.147687] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.147775]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[    3.223169] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.223286] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.223427] ata_piix 0000:00:1f.1: version 2.12
[    3.223439] ata_piix 0000:00:1f.1: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.223569] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.223668] scsi3 : ata_piix
[    3.223807] scsi4 : ata_piix
[    3.224580] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    3.224657] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    3.388449] ata4.00: ATAPI: HL-DT-ST DVDRAM_GSA-T20N, WF08, max UDMA/33
[    3.404315] ata4.00: configured for UDMA/33
[    3.576784] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM_GSA-T20N  WF08 PQ: 0 ANSI: 5
[    3.587831] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.587919] Uniform CD-ROM driver Revision: 3.20
[    3.588106] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.588153] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    3.588968] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.589075] ehci_hcd 0000:00:1a.7: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    3.589174] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.589180] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.589320] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.593341] ehci_hcd 0000:00:1a.7: debug port 1
[    3.593427] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.593444] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfe504800
[    3.608011] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.608159] usb usb1: configuration #1 chosen from 1 choice
[    3.608275] hub 1-0:1.0: USB hub found
[    3.608366] hub 1-0:1.0: 4 ports detected
[    3.608591] ehci_hcd 0000:00:1d.7: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    3.608686] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.608690] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.608828] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.612842] ehci_hcd 0000:00:1d.7: debug port 1
[    3.612934] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.612940] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe504c00
[    3.624012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.624153] usb usb2: configuration #1 chosen from 1 choice
[    3.624268] hub 2-0:1.0: USB hub found
[    3.624355] hub 2-0:1.0: 6 ports detected
[    3.624555] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.624657] uhci_hcd: USB Universal Host Controller Interface driver
[    3.624774] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.624870] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.624875] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.625009] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.625148] uhci_hcd 0000:00:1a.0: irq 22, io base 0x00001800
[    3.625322] usb usb3: configuration #1 chosen from 1 choice
[    3.625437] hub 3-0:1.0: USB hub found
[    3.625525] hub 3-0:1.0: 2 ports detected
[    3.625707] uhci_hcd 0000:00:1a.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.625807] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.625813] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.625948] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.626076] uhci_hcd 0000:00:1a.1: irq 22, io base 0x00001820
[    3.626250] usb usb4: configuration #1 chosen from 1 choice
[    3.626361] hub 4-0:1.0: USB hub found
[    3.626448] hub 4-0:1.0: 2 ports detected
[    3.626631] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.626723] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.626729] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.626871] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.626997] uhci_hcd 0000:00:1d.0: irq 22, io base 0x00001840
[    3.627168] usb usb5: configuration #1 chosen from 1 choice
[    3.627279] hub 5-0:1.0: USB hub found
[    3.627367] hub 5-0:1.0: 2 ports detected
[    3.628108] uhci_hcd 0000:00:1d.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.628203] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.628207] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.628335] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.628461] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00001860
[    3.628637] usb usb6: configuration #1 chosen from 1 choice
[    3.628746] hub 6-0:1.0: USB hub found
[    3.628833] hub 6-0:1.0: 2 ports detected
[    3.629025] uhci_hcd 0000:00:1d.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.629118] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.629124] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.629252] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.629377] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001880
[    3.629552] usb usb7: configuration #1 chosen from 1 choice
[    3.629661] hub 7-0:1.0: USB hub found
[    3.629750] hub 7-0:1.0: 2 ports detected
[    3.629987] usbcore: registered new interface driver libusual
[    3.630117] usbcore: registered new interface driver usbserial
[    3.630209] USB Serial support registered for generic
[    3.630308] usbcore: registered new interface driver usbserial_generic
[    3.630392] usbserial: USB Serial Driver core
[    3.630521] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.632889] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.635374] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.635464] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.635549] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.635632] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.635719] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.645044] mice: PS/2 mouse device common for all mice
[    3.693075] rtc_cmos 00:07: RTC can wake from S4
[    3.693197] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.693315] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.693470] device-mapper: uevent: version 1.0.3
[    3.693648] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.693831] device-mapper: multipath: version 1.0.5 loaded
[    3.693919] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.694183] cpuidle: using governor ladder
[    3.694387] cpuidle: using governor menu
[    3.694951] TCP cubic registered
[    3.695114] NET: Registered protocol family 10
[    3.695651] lo: Disabled Privacy Extensions
[    3.696074] NET: Registered protocol family 17
[    3.696193] Bluetooth: L2CAP ver 2.11
[    3.696279] Bluetooth: L2CAP socket layer initialized
[    3.696365] Bluetooth: SCO (Voice Link) ver 0.6
[    3.696451] Bluetooth: SCO socket layer initialized
[    3.696543] Marking TSC unstable due to TSC halts in idle
[    3.696697] Bluetooth: RFCOMM socket layer initialized
[    3.696787] Bluetooth: RFCOMM TTY layer initialized
[    3.696871] Bluetooth: RFCOMM ver 1.10
[    3.697948] registered taskstats version 1
[    3.698184]   Magic number: 5:883:963
[    3.698389] rtc_cmos 00:07: setting system clock to 2009-04-18 01:59:36 UTC (1240019976)
[    3.698486] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.698565] EDD information not available.
[    3.698711] Freeing unused kernel memory: 536k freed
[    3.699033] Write protecting the kernel read-only data: 6708k
[    3.735242] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.933108] sky2 driver version 1.22
[    3.933261] sky2 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.933357] sky2 0000:04:00.0: setting latency timer to 64
[    3.933411] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 3
[    3.937322] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.965565] sky2 0000:04:00.0: Marvell Yukon 88E8055 Gigabit Ethernet Controller
[    3.965658]  Part Number: Yukon 88E8055
[    3.965660]  Engineering Level: Rev. 1.2
[    3.965662]  Manufacturer: Marvell
[    3.965759] sky2 0000:04:00.0: irq 2298 for MSI/MSI-X
[    3.967876] sky2 eth0: addr 00:17:42:65:e9:16
[    3.981298] ohci1394 0000:1c:03.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.032754] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fe201000-fe2017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.134122] usb 1-2: configuration #1 chosen from 1 choice
[    4.143368] Initializing USB Mass Storage driver...
[    4.145450] scsi5 : SCSI emulation for USB Mass Storage devices
[    4.145666] usbcore: registered new interface driver usb-storage
[    4.145744] USB Mass Storage support registered.
[    4.145947] usb-storage: device found at 2
[    4.145949] usb-storage: waiting for device to settle before scanning
[    4.416327] PM: Starting manual resume from disk
[    4.416404] PM: Resume from partition 8:21
[    4.416406] PM: Checking hibernation image.
[    4.416666] PM: Resume from disk failed.
[    4.474018] kjournald starting.  Commit interval 5 seconds
[    4.474109] EXT3-fs: mounted filesystem with ordered data mode.
[    4.608072] usb 4-2: new full speed USB device using uhci_hcd and address 2
[    4.769342] usb 4-2: configuration #1 chosen from 1 choice
[    5.305537] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000e1003c65cc9]
[    9.147633] usb-storage: device scan complete
[    9.151397] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[    9.166608] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    9.166748] sd 5:0:0:0: Attached scsi generic sg3 type 0
[   12.684492] udev: starting version 141
[   13.801503] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.827054] [fglrx] Maximum main memory to use for locked dma buffers: 3737 MBytes.
[   13.827478] [fglrx]   vendor: 1002 device: 9581 count: 1
[   13.828072] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   13.828166] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.828249] pci 0000:01:00.0: setting latency timer to 64
[   13.829648] [fglrx] Driver built-in PAT support is enabled successfully
[   13.829771] [fglrx] module loaded - fglrx 8.60.3 [Apr  1 2009] with 1 minors
[   13.861105] cfg80211: Calling CRDA to update world regulatory domain
[   13.915576] input: Fujitsu FUJ02B1 as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:2b/FUJ02B1:00/input/input5
[   13.940198] ACPI: Fujitsu FUJ02B1 [FJEX] (on)
[   13.941149] input: Fujitsu FUJ02E3 as /devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input6
[   13.968102] ACPI: Fujitsu FUJ02E3 [FEXT] (on)
[   13.968418] fujitsu-laptop: driver 0.4.3 successfully loaded.
[   14.024459] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   14.077297] iTCO_vendor_support: vendor-support=0
[   14.088632] cfg80211: World regulatory domain updated:
[   14.088716] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.088799] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.088873] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.088948] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.089051] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.089132] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.101747] sdhci: Secure Digital Host Controller Interface driver
[   14.101834] sdhci: Copyright(c) Pierre Ossman
[   14.109229] sdhci-pci 0000:1c:03.2: SDHCI controller found [1217:7120] (rev 2)
[   14.109352] sdhci-pci 0000:1c:03.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.109494] mmc0: Unknown controller version (2). You may experience problems.
[   14.109676] mmc0: SDHCI controller on PCI [0000:1c:03.2] using PIO
[   14.133593] yenta_cardbus 0000:1c:03.0: CardBus bridge found [10cf:13c6]
[   14.133714] yenta_cardbus 0000:1c:03.0: O2: res at 0x94/0xD4: 00/ea
[   14.133790] yenta_cardbus 0000:1c:03.0: O2: enabling read prefetch/write burst
[   14.188977] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.189272] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   14.189464] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.233407] acpi device:05: registered as cooling_device2
[   14.233993] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input8
[   14.261501] yenta_cardbus 0000:1c:03.0: ISA IRQ mask 0x0cb8, PCI irq 17
[   14.261597] yenta_cardbus 0000:1c:03.0: Socket status: 30000006
[   14.261684] pci_bus 0000:1c: Raising subordinate bus# of parent bus (#1c) from #1d to #20
[   14.261788] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   14.261873] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge Memory window: 0xfe200000 - 0xfe2fffff
[   14.261946] yenta_cardbus 0000:1c:03.0: pcmcia: parent PCI bridge Memory window: 0xd4000000 - 0xd7ffffff
[   14.265150] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.337075] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.469407] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.469511] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.470326] iwlagn 0000:0c:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.470450] iwlagn 0000:0c:00.0: setting latency timer to 64
[   14.470581] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   14.509806] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.509949] iwlagn 0000:0c:00.0: irq 2297 for MSI/MSI-X
[   14.511027] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.642773] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   14.642851] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.643009] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.745786] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.745932] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.941577] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   14.985584] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   15.026721] lp: driver loaded but no devices found
[   15.247273] Adding 1437776k swap on /dev/sdb5.  Priority:-1 extents:1 across:1437776k
[   15.624396] EXT3 FS on sdb3, internal journal
[   17.652836] type=1505 audit(1240045190.453:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2269
[   17.729179] type=1505 audit(1240045190.529:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2273
[   17.729320] type=1505 audit(1240045190.529:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2273
[   17.729369] type=1505 audit(1240045190.529:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2273
[   17.729413] type=1505 audit(1240045190.529:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2273
[   17.868335] type=1505 audit(1240045190.669:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2278
[   17.868522] type=1505 audit(1240045190.669:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2278
[   17.921622] type=1505 audit(1240045190.722:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2282
[   19.000081] Clocksource tsc unstable (delta = -178437311 ns)
```

Unless that brings anything to light (hoping against hope here), I guess what I'll do (most likely Sunday) is create a new partition, do a clean install of Jaunty there, and see if that solves the problem. If it does, great. It not, well, most of the stuff that I really want from Compiz is stuff that I shouldn't really miss a great deal as I've really only been using Ubuntu actively since January (but actively pretty much accounts for 90% of the time I spend on my computer). I didn't (and don't) really have it in Vista, so I won't die without it in Ubuntu.

---

### Post by vlovich on 2009-04-18
Are you sure the script ran ok?  I haven't tested it so it might not work.  Clearly either it doesn't work or you didn't run it properly because you still have radeonhd on your system.

Try just running these commands manually

```

sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon xserver-xorg-video-radeonhd xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle fglrx-modaliases || echo "problem"
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx || echo "problem"
sh ./ati-driver-installer-9-4-x86.x86_64.run --buildpkg Ubuntu/9.04
sudo dpkg -i xorg-driver-fglrx_8.602-0ubuntu1_amd64.deb fglrx-amdcccle_8.602-0ubuntu1_amd64.deb fglrx-kernel-source_8.602-0ubuntu1_amd64.deb fglrx-modaliases_8.602-0ubuntu1_amd64.deb

```

I think I found a potential reason the script didn't work (updating again - you don't need to use it, just for posterity).

---

### Post by vlovich on 2009-04-18
Also, don't forget ```
sudo aticonfig --initial
```

---

### Post by vlovich on 2009-04-18
And am I safe in assuming that you reboot after installing the ati drivers?  Cause otherwise the radeonhd ones are still loaded.

---

### Post by carrozza on 2009-04-18
Well, today I installed Ubuntu Jaunty RC and enabled ATI hardware drivers.

All went well without any hack, I enabled Compiz effects and they just started.

Unfortunately my experience with Linux OS is still not totally good, and I have to stick with Windows a little more.

This time the only problem was Flash: after watching a few videos over internet the system become unstable, and 3 over 4 times it crash.

So, good news for ATI owners, bad news for Flash watchers.

---

### Post by danwood76 on 2009-04-18
Are you running 64 bit?
There is a native 64 bit version out but its still in alpha, the one in the repos uses the 32 bit version and is pretty unstable.

(This is to do with flash btw)

---

### Post by Akkifokkusu on 2009-04-18
> **vlovich said:**
> And am I safe in assuming that you reboot after installing the ati drivers?  Cause otherwise the radeonhd ones are still loaded.

Yeah, of course... I tried it manually through the terminal... no change. But here's an Xorg.0.log file that definetely doesn't reference radeonhd.

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux igor-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 18 10:42:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series] rev 0, Mem @ 0xe0000000/268435456, 0xdfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension XFree86-DRI
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.3
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.60.3
	Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.60.3
(II) ATI Proprietary Linux Driver Release Identifier: 8.602                                
(II) ATI Proprietary Linux Driver Build Date: Apr  1 2009 15:01:03
(II) Loading PCS database from /etc/ati/amdpcsdb
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 5.0
(--) Chipset Supported AMD Graphics Processor (0x9581) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x1ef2430
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(II) fglrx(0): 10BitPixelFormat disabled by default
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(--) fglrx(0): Chipset: "ATI Mobility Radeon HD 2600" (Chipset = 0x9581)
(--) fglrx(0): (PciSubVendor = 0x10cf, PciSubDevice = 0x1432)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xdfef0000
(--) fglrx(0): I/O port at 0x00002000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitConfig failed
(EE) fglrx(0): PreInit failed
(II) fglrx(0): === [atiddxPreInit] === end

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/X11R6/bin/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7fe8f0a02040]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlDalHelperClose+0x87) [0x7fe8eec2be57]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxFreeScreen+0x13f) [0x7fe8eec029df]
5: /usr/X11R6/bin/X(xf86DeleteScreen+0x7e) [0x49209e]
6: /usr/X11R6/bin/X(InitOutput+0xe1d) [0x46f9fd]
7: /usr/X11R6/bin/X(main+0x20e) [0x433bde]
8: /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8f09ed5a6]
9: /usr/X11R6/bin/X [0x433219]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
```

I guess maybe my issue is in the way the BIOS handles the video card or something? I looked up the error and saw a post from someone somewhere who managed to change some setting in the BIOS, and it worked. I, unfortunately, don't have that setting to change, so I'm stuck there.

---

### Post by growled on 2009-04-18
Makes me glad for once that I have a x1300 and use 32 bit.

---

### Post by vlovich on 2009-04-18
I'm having no problem with my 2600 on 64-bit.  The issue was him trying 9.3 which doesn't work with Jaunty.  Then switching to radeonhd which doesn't work if you have the binary drivers installed.  Then trying to go to 9.4 which conflicts because he now has the radeonhd drivers.

And to top it all off, his xorg.conf was messed up - set to use radeonhd instead of fglrx.

So yes - you can shoot yourself in the foot with any operating system.  I tried to help him - a reinstall was completely unnecessary.

---

### Post by Akkifokkusu on 2009-04-18
> **vlovich said:**
> I'm having no problem with my 2600 on 64-bit.  The issue was him trying 9.3 which doesn't work with Jaunty.  Then switching to radeonhd which doesn't work if you have the binary drivers installed.  Then trying to go to 9.4 which conflicts because he now has the radeonhd drivers.

And to top it all off, his xorg.conf was messed up - set to use radeonhd instead of fglrx.

So yes - you can shoot yourself in the foot with any operating system.  I tried to help him - a reinstall was completely unnecessary.

You're making it seem like I did something wrong. I upgraded. It should've just worked. It doesn't. I've removed the other drivers whenever I try to get the other stuff to work, with a new xorg.conf. It just doesn't work. Is yours a Mobility 2600? Maybe that's it? I don't know. If I didn't have a laptop, I'd probably just buy a new video card, but I do so there's really nothing I can do besides trying the clean install option.

---

### Post by vlovich on 2009-04-18
I have a desktop card.  However, that is most likely not the issue.  When you upgraded, did you have fglrx drivers or radeonhd?  Cause I had fglrx & had no problems upgrading - automatically upgraded my 9.3 drivers to the pre-release 9.4 (there was a problem with Qt apps due to a bug with vertical sub-pixel anti-aliasing, but that's not what you experienced).

---

### Post by Akkifokkusu on 2009-04-18
Had frglrx... Which should be obvious given that I was able to use Compiz (as well as games and other stuff) before. When I upgraded, it did the same thing. Upgraded my drivers to 9.4. But 9.4 causes X to crash on launch. If I just had a bug with Qt apps I'd be OK since I barely use them. But I wasn't that lucky.

---

### Post by vlovich on 2009-04-18
But you never posted the log of your X crashing like I asked - you posted the one where you had radeonhd running (intentionally or unintentionally) which obviously wouldn't work because you did it wrong (you still had fglrx installed & as I mentioned nothing will work if both of those are installed at the same time).

Also, Jaunty hasn't yet been released, so a smooth upgrade (while somewhat reasonable given it's going to be released in a few days) isn't necessarily to be expected.

That being said, did you actually try the manual steps I told you for removing the old drivers & reinstalling fglrx?

---

### Post by vlovich on 2009-04-18
Also, as for flash, mine works fine here without issue.

---

### Post by Akkifokkusu on 2009-04-18
I did try the manual way. Before and after you told me to. I'll post my Xorg.conf next time I try to do it all. I'm on Vista right now though, for the simple reason that I can actually use my graphics card for stuff like... games.

---

### Post by Akkifokkusu on 2009-04-18
And yeah, Flash also works for me, and has worked for me since the first day that I downloaded the 64-bit version from Adobe and placed in the Firefox plugins folder... Nothing to do with the graphics card, I think, cause very little of Flash is too intensive for even intergrated cards.

---

### Post by carrozza on 2009-04-19
Thanks for replies on Flash, I'm on a 32 bit laptop, but had issues with Flash and streaming videos in each and every Linux distribution I tried out there.

Even Intrepid 8.10, or OpenSuse... none seems to be completely free from issues with my use of web browsing.

Not a big deal, I'm happy to see Linux progress and will come back from time to time to see improvements!

---

### Post by vlovich on 2009-04-19
Pre-Jaunty, make sure you have flashplugin-nonfree installed for Adobe's flash which works on 32-bit.  For 64-bit, you need to manually install Adobe's beta Flash 10 build for 64-bit Linux.

Jaunty seems to come with Flash 10 both for 64 & 32 bit.  ```
sudo apt-get install flashplugin-installer
```

---

