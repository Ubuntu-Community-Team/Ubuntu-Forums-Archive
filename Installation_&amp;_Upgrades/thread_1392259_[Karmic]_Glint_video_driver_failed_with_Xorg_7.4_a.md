---
title: "[Karmic] Glint video driver failed with Xorg 7.4 at X startup: Segmentation fault"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by JohanPirlouit on 2010-01-27
Hi everyone,

(First, I apologize for my english which is a bit limited...)


](*,) I've searched the forum (and also on G..gle) for an answer but I didn't find any that could solve my problem:

I try to use my good old 3D Labs Oxygen VX1 AGP graphic board (Glint R3 GPU, 32MB RAM) with Ubuntu 9.10 Karmic and Xorg 7.4 (Xorg-core 1.6.4) and the glint driver (1.2.3) failed at X startup ("**Segmentation fault**"). By the way, default Xorg driver works, but only in a basic mode: 640x480px, 60Hz and 256 colors!

For those who think that it could be a problem only with the Glint R3 GPU: I've got the exact same problem with an old Diamond FireGL 1000 Pro AGP (Permedia 2 GPU, 8MB RAM).


My config:
- AMD Duron 1GHz
- Abit KT7A mainboard (chipset VIA KT133A)
- 512 MB SDRAM PC-133
- 3D Labs Oxygen VX1 graphic board (Glint R3 GPU, AGP, 32MB RAM)
- Ubuntu 9.10 Karmic Koala (fresh install using Alternate CD and up-to-date)
- Xorg 7.4 (Xorg-core 1.6.4)
- Glint video driver 1.2.3 manually installed with Synaptic Package Manager


-------------

1. **lspci -vv** (here focused on the VGA controller) returns this:
```
01:00.0 VGA compatible controller: 3DLabs GLINT R3 (rev 01)
	Subsystem: 3DLabs Device 0125
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (48000ns min, 48000ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at ed000000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Region 2: Memory at e8000000 (32-bit, prefetchable) [size=64M]
	[virtual] Expansion ROM at ec000000 [disabled] [size=64K]
	Capabilities: [4c] Power Management version 1
		Flags: PMEClk- DSI+ D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [40] AGP version 2.0
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel driver in use: pm3fb
	Kernel modules: pm3fb
```


-------------

2. **dpkg-reconfigure -phigh xserver-xorg** did solve nothing!


-------------

3. **X -configure** makes this *xorg.conf.new* (I removed modules, fonts, keyboard and mouse sections):
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "RGBbits"            	# <i>
        #Option     "NoAccel"            	# [<bool>]
        #Option     "BlockWrite"         	# [<bool>]
        #Option     "FireGL3000"         	# [<bool>]
        #Option     "Overlay"            	# [<str>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "UseFlatPanel"       	# [<bool>]
        #Option     "VideoKey"           	# [<bool>]
	Identifier  "Card0"
	Driver      "glint"
	VendorName  "3DLabs"
	BoardName   "GLINT R3"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```


-------------

4. Starting X by the command **X -config /root/xorg.conf.new** failed with the message "**Segmentation fault**":
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Test 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=517020c7-3b23-44f8-b4d5-b39c155fc6a9 ro single
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan 25 19:20:42 2010
(++) Using config file: "/root/xorg.conf.new"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 2

(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
	compiled for 1.6.4, module version = 1.0.0
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
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "glint"
(II) Loading /usr/lib/xorg/modules/drivers//glint_drv.so
(II) Module glint: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) GLINT: driver for 3Dlabs chipsets: gamma, gamma2, ti_pm2, ti_pm, r4,
	pm4, pm3, pm2v, pm2, pm, 300sx, 500tx, mx, delta
(WW) Falling back to old probe method for glint
(--) Chipset pm3 found
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
(==) GLINT(0): Depth 24, (--) framebuffer bpp 32
(==) GLINT(0): RGB weight 888
(==) GLINT(0): Default visual is TrueColor
(==) GLINT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) GLINT(0): Using HW cursor
(--) GLINT(0): Not using Linux framebuffer device
(--) GLINT(0): Chipset: "pm3"

Backtrace:
0: X(xorg_backtrace+0x3b) [0x8133d6b]
1: X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xdb8400]
3: X(InitOutput+0x4e9) [0x80b05b9]
4: X(main+0x1cb) [0x807234b]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1c8b56]
6: X [0x80719c1]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
```


In this Xorg log, **Glint module** claimes to be **compiled for 1.6.1.901** though **X.Org X Server is 1.6.4**.


-------------

5. I saw that a new release of the Glint driver (1.2.4; [the web page / download page is here]("http://cgit.freedesktop.org/xorg/driver/xf86-video-glint")) is out since a few times and can be found on the X.org website, but I could not compile it to install and test it.

From the sources, compile logs are these ones:

Autogen-sh:
```
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1966080
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XV is defined... yes
checking if DPMSExtension is defined... yes
checking if XFreeXDGA is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for XEXT... no
checking whether XSERVER_LIBPCIACCESS is declared... yes
checking cfb8_32.h usability... no
checking cfb8_32.h presence... no
checking for cfb8_32.h... no
checking for ANSI C header files... (cached) yes
checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for DRI... yes
checking for PCIACCESS... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
```

Configure:
```
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1966080
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XV is defined... yes
checking if DPMSExtension is defined... yes
checking if XFreeXDGA is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... yes
checking for XEXT... no
checking whether XSERVER_LIBPCIACCESS is declared... yes
checking cfb8_32.h usability... no
checking cfb8_32.h presence... no
checking for cfb8_32.h... no
checking for ANSI C header files... (cached) yes
checking for /usr/include/xorg/dri.h... yes
checking for /usr/include/xorg/sarea.h... yes
checking for /usr/include/xorg/dristruct.h... yes
checking whether to include DRI support... yes
checking for DRI... yes
checking for PCIACCESS... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating man/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
```

Make:
```
make  all-recursive
make[1]: Entering directory `/home/johan/Public/xf86-video-glint-1.2.4'
Making all in src
make[2]: Entering directory `/home/johan/Public/xf86-video-glint-1.2.4/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -I/usr/include/xorg -I/usr/include/pixman-1     -I/usr/include/drm -I/usr/include/X11/dri   -DPPC_MMIO_IS_BE -DSPARC_MMIO_IS_BE -g -O2 -MT glint_driver.lo -MD -MP -MF .deps/glint_driver.Tpo -c -o glint_driver.lo glint_driver.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/include/xorg -I/usr/include/pixman-1 -I/usr/include/drm -I/usr/include/X11/dri -DPPC_MMIO_IS_BE -DSPARC_MMIO_IS_BE -g -O2 -MT glint_driver.lo -MD -MP -MF .deps/glint_driver.Tpo -c glint_driver.c  -fPIC -DPIC -o .libs/glint_driver.o
glint_driver.c:250: error: 'PACKAGE_VERSION_MAJOR' undeclared here (not in a function)
glint_driver.c:250: error: 'PACKAGE_VERSION_MINOR' undeclared here (not in a function)
glint_driver.c:250: error: 'PACKAGE_VERSION_PATCHLEVEL' undeclared here (not in a function)
glint_driver.c: In function 'GLINTPreInit':
glint_driver.c:1227: warning: format '%lx' expects type 'long unsigned int', but argument 4 has type 'pciaddr_t'
make[2]: *** [glint_driver.lo] Error 1
make[2]: Leaving directory `/home/johan/Public/xf86-video-glint-1.2.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/johan/Public/xf86-video-glint-1.2.4'
make: *** [all] Error 2
```


-------------

So, my questions:

A. Is there any fix or any update or any other way to make Glint driver to be functional with my 3D Labs board and current Xorg release?

B. Did anybody compile the last release of the Glint driver (1.2.4; [the web page / download page is here]("http://cgit.freedesktop.org/xorg/driver/xf86-video-glint")) and build it as a Deb package that I could test on my config?

Any help, any idea, any suggestions will be appreciated ;)...

Regards,
Johan

---

### Post by JohanPirlouit on 2010-02-01
Up......

---

