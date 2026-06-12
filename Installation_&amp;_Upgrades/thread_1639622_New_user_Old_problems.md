---
title: "New user Old problems"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by BewilderedStranger on 2010-12-06
Okay so I've attempted to install ubuntu on this machine several times now and failed miserably with every version i've tried all the way back to the 9. ... the one just before 9.10.  Here is one of the old q and as: [http://ubuntuforums.org/showthread.php?t=1408920](http://ubuntuforums.org/showthread.php?t=1408920)  The situation never got resolved and i ran into another problem anyhow so i kinda gave up on it for a while and now here am i trying it again.  After researching the subject on all the forums across the web apparently some computers just don't like the graphical install programs... or trials at that rate. i've seen several threads that offer workarounds but none have worked for me. 
[http://ubuntuforums.org/showthread.php?t=1472054&highlight=stalls+at+black+screen+integrated&page=2](http://ubuntuforums.org/showthread.php?t=1472054&highlight=stalls+at+black+screen+integrated&page=2)

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

  I Cant run the live CD or check disk or much anything from any version from 9.04 up till 10.10 all end with black screen which turns to blue screen saying no signal then TV off.

Is it possible that i may have luck with an alternate install version and if so how can i partition my hd the way i want it.  I can't use gparted off live cd cause i can't boot into live cd and with windows still on the drive i can't move the cursed mft and boot files and all that garbage to shrink the windows partition to less than about 500 gigs.   Anyhow thanks a bunch and i would appreciate any help.


Ubuntu 9.04, 9.10, 10.04, 10.10 Kubuntu 10.10 all 64 bit all same results.  Also i'm very sure of the disk burns i burned several versions in 32 bit for use on other computers and ran into 0 bad ones.

Asus Rampage II Gene 6gb DDR3  ATI radeon HD4850  Monitor is Polaroid Tlx-04240b 42in. LCD TV

---

### Post by wilee-nilee on 2010-12-06
As careful as you were in giving information, it is difficult for me to even follow what you want, and what you have as of now. We only need that information, not much else, can you streamline that request, to this idea.;)

Just trying to get you help here is all. The first text block at the least would be nice to be split into paragraphs so the words are just separated.

Your own stress over loss of data means nothing if not recoverable, although I know it does help to process this by sharing, but it confuses in the help a bit.

---

### Post by PRC09 on 2010-12-06
Have you tried to install using a standard lcd monitor instead of a television???

---

### Post by BewilderedStranger on 2010-12-06
no PRC I haven't tried using another monitor honestly that's the only monitor i have.  Its always worked for me you think ubuntu just doesn't like the tv as a monitor?  You think there would be a way to install with a different monitor then switch back to the tv after installation?

---

### Post by PRC09 on 2010-12-06
Not sure exactly how Ubuntu recognises what monitor you are using but it might be worth a try.I have always set-up using an lcd monitor and then connected to the TV after.Never thought to try tv first.Also if you have tried different versions with the same problem then more then likely something in the hardware that Ubuntu doesnt like.

---

### Post by BewilderedStranger on 2010-12-06
Yeah this I'm sure of.   It has to be a hardware issue if I can locate another monitor I'll see what I can come up with.  I know this thing is real finnicky about the resolutions and refresh rates.  and... you just gave me another idea it seemed happier with different resolutions and refresh rates when connected via hdmi as opposed to vga or dvi input.  If no luck i'll have to find another monitor to try.

---

### Post by BewilderedStranger on 2010-12-12
Okay So I used a different monitor to install and all went well  Yaayyyy!   However when I switched back to my 42" LCD tv again everything works all the way up to the sign in screen then loses signal to my monitor/TV. any ideas?  It does allow me to ctrl +alt F1 into a terminal login though which seems a step in the right direction.  Thanks all.

---

### Post by BewilderedStranger on 2010-12-13
This mess is starting to make me crazy however looking at all the workarounds on the forums and everything I noticed that one was to edit the xorg.conf well the section they say to edit is modeline under monitors section.  My xorg doesn't even seem to have a monitors section in it.  Lost and confused everything worked great on the lcd i borrowed but I cannot figure out what to do here if anyone has any suggestions I would greatly appreciate it.

---

### Post by BewilderedStranger on 2010-12-17
So in a flash of **"**brilliance" I clicked on recovery mode and  found the fail safe Xgraphics and saw the first desktop i've even seen  on my monitor/TV.  Then I also found the troubleshooting options. :razz:   Whenever ubuntu first loads it pops up with an error saying that the  monitor graphics card and the input devices were unable to be auto  detected  sp i needed   to configure those myself.  I made an X logfile  and included it below.  Can you fearless ubuntunites help me to set this  up?  I feel so close now I can taste the ubuntu. haha.  Thank you all  very much here's the logfile:... Actually I kinda lost track and here  are several different logfiles i spotted hopefully the more info the  better you all can help me.  

Logfile from /home folder:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-RmcnL2
GNOME_KEYRING_CONTROL=/tmp/keyring-RmcnL2
SSH_AUTH_SOCK=/tmp/keyring-RmcnL2/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-RmcnL2
** Message: adding killswitch idx 0 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 0 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED

(polkit-gnome-authentication-agent-1:1854): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1854): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
/usr/bin/compiz (core) - Fatal: glXCreateContext failed
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :1.0
Initializing nautilus-gdu extension

(nautilus:1856): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:1856): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

** (gnome-settings-daemon:1826): WARNING **: Got less number of items in credentials hash table than expected!
Unable to find a synaptics device.
** Message: applet now embedded in the notification area
** (update-notifier:2048): DEBUG: aptdaemon on bus: 0
** (update-notifier:2048): DEBUG: Skipping reboot required

(evolution-alarm-notify:1859): evolution-alarm-notify-WARNING **: alarm.c:253: Requested removal of nonexistent alarm!

(nautilus:1856): GdkPixbuf-CRITICAL **: gdk_pixbuf_format_get_name: assertion `format != NULL' failed

(nautilus:1856): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message:  Called "net usershare info" but it failed: 'net usershare' returned  error 255: net usershare: cannot open usershare directory  /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Next logfile:

[    91.814] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    91.814] X Protocol Version 11, Revision 0
[    91.814] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    91.814] Current Operating System: Linux Angel 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 11:55:36 UTC 2010 x86_64
[     91.814] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic  root=UUID=f40b16f8-0abe-4b98-aa05-2f87edda6367 ro single
[    91.814] Build Date: 16 September 2010  06:18:41PM
[    91.814] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    91.814] Current version of pixman: 0.18.4
[    91.814]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    91.814] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    91.814] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Dec 16 23:30:54 2010
[    91.814] (==) Using config file: "/etc/X11/xorg.conf.failsafe"
[    91.814] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    91.814] (==) No Layout section.  Using the first Screen section.
[    91.814] (**) |-->Screen "Default Screen" (0)
[    91.814] (**) |   |-->Monitor "Configured Monitor"
[    91.814] (**) |   |-->Device "Configured Video Device"
[    91.814] (==) Automatically adding devices
[    91.814] (==) Automatically enabling devices
[    91.814] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    91.814]     Entry deleted from font path.
[    91.814] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    91.814] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    91.814] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    91.814] (II) Loader magic: 0x7d0200
[    91.814] (II) Module ABI versions:
[    91.814]     X.Org ANSI C Emulation: 0.4
[    91.814]     X.Org Video Driver: 8.0
[    91.814]     X.Org XInput driver : 11.0
[    91.814]     X.Org Server Extension : 4.0
[     91.815] (--) PCI:*(0:2:0:0) 1002:9442:174b:e810 rev 0, Mem @  0xd0000000/268435456, 0xfbbe0000/65536, I/O @ 0x0000b000/256, BIOS @  0x????????/131072
[    91.815] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    91.815] (II) LoadModule: "extmod"
[    91.816] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    91.816] (II) Module extmod: vendor="X.Org Foundation"
[    91.816]     compiled for 1.9.0, module version = 1.0.0
[    91.816]     Module class: X.Org Server Extension
[    91.816]     ABI class: X.Org Server Extension, version 4.0
[    91.816] (II) Loading extension MIT-SCREEN-SAVER
[    91.816] (II) Loading extension XFree86-VidModeExtension
[    91.816] (II) Loading extension XFree86-DGA
[    91.816] (II) Loading extension DPMS
[    91.816] (II) Loading extension XVideo
[    91.816] (II) Loading extension XVideo-MotionCompensation
[    91.816] (II) Loading extension X-Resource
[    91.816] (II) LoadModule: "dbe"
[    91.816] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    91.816] (II) Module dbe: vendor="X.Org Foundation"
[    91.816]     compiled for 1.9.0, module version = 1.0.0
[    91.816]     Module class: X.Org Server Extension
[    91.816]     ABI class: X.Org Server Extension, version 4.0
[    91.816] (II) Loading extension DOUBLE-BUFFER
[    91.816] (II) LoadModule: "glx"
[    91.816] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    91.816] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    91.816]     compiled for 7.6.0, module version = 1.0.0
[    91.816] (II) Loading extension GLX
[    91.816] (II) LoadModule: "record"
[    91.817] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    91.817] (II) Module record: vendor="X.Org Foundation"
[    91.817]     compiled for 1.9.0, module version = 1.13.0
[    91.817]     Module class: X.Org Server Extension
[    91.817]     ABI class: X.Org Server Extension, version 4.0
[    91.817] (II) Loading extension RECORD
[    91.817] (II) LoadModule: "dri"
[    91.817] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    91.817] (II) Module dri: vendor="X.Org Foundation"
[    91.817]     compiled for 1.9.0, module version = 1.0.0
[    91.817]     ABI class: X.Org Server Extension, version 4.0
[    91.817] (II) Loading extension XFree86-DRI
[    91.817] (II) LoadModule: "dri2"
[    91.817] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    91.817] (II) Module dri2: vendor="X.Org Foundation"
[    91.817]     compiled for 1.9.0, module version = 1.2.0
[    91.817]     ABI class: X.Org Server Extension, version 4.0
[    91.817] (II) Loading extension DRI2
[    91.817] (II) LoadModule: "vesa"
[    91.818] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    91.818] (II) Module vesa: vendor="X.Org Foundation"
[    91.818]     compiled for 1.8.99.905, module version = 2.3.0
[    91.818]     Module class: X.Org Video Driver
[    91.818]     ABI class: X.Org Video Driver, version 8.0
[    91.818] (II) VESA: driver for VESA chipsets: vesa
[    91.818] (--) using VT number 3

[    93.132] (II) Loading sub module "vbe"
[    93.132] (II) LoadModule: "vbe"
[    93.132] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    93.132] (II) Module vbe: vendor="X.Org Foundation"
[    93.132]     compiled for 1.9.0, module version = 1.1.0
[    93.132]     ABI class: X.Org Video Driver, version 8.0
[    93.132] (II) Loading sub module "int10"
[    93.132] (II) LoadModule: "int10"
[    93.132] (II) Loading /usr/lib/xorg/modules/libint10.so
[    93.132] (II) Module int10: vendor="X.Org Foundation"
[    93.132]     compiled for 1.9.0, module version = 1.0.0
[    93.132]     ABI class: X.Org Video Driver, version 8.0
[    93.132] (II) VESA(0): initializing int10
[    93.132] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    93.132] (II) VESA(0): VESA BIOS detected
[    93.132] (II) VESA(0): VESA VBE Version 3.0
[    93.132] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    93.132] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    93.132] (II) VESA(0): VESA VBE OEM Software Rev: 11.10
[    93.132] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    93.132] (II) VESA(0): VESA VBE OEM Product: RV770
[    93.132] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    93.141] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    93.141] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    93.141] (==) VESA(0): RGB weight 888
[    93.141] (==) VESA(0): Default visual is TrueColor
[    93.141] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    93.141] (II) Loading sub module "ddc"
[    93.141] (II) LoadModule: "ddc"
[    93.141] (II) Module "ddc" already built-in
[    93.141] (II) VESA(0): VESA VBE DDC supported
[    93.141] (II) VESA(0): VESA VBE DDC Level 2
[    93.141] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    93.196] (II) VESA(0): VESA VBE DDC read successfully
[    93.196] (II) VESA(0): Manufacturer: PTS  Model: 108f  Serial#: 730002584
[    93.196] (II) VESA(0): Year: 2007  Week: 41
[    93.196] (II) VESA(0): EDID Version: 1.3
[    93.196] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    93.196] (II) VESA(0): Sync:
[    93.196] (II) VESA(0): Max Image Size [cm]: horiz.: 88  vert.: 49
[    93.196] (II) VESA(0): Gamma: 1.00
[    93.196] (II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    93.196] (II) VESA(0): First detailed timing is preferred mode
[    93.196] (II) VESA(0): redX: 0.643 redY: 0.331   greenX: 0.281 greenY: 0.596
[    93.196] (II) VESA(0): blueX: 0.144 blueY: 0.061   whiteX: 0.280 whiteY: 0.290
[    93.196] (II) VESA(0): Supported established timings:
[    93.196] (II) VESA(0): 720x400@70Hz
[    93.196] (II) VESA(0): 640x480@60Hz
[    93.196] (II) VESA(0): 640x480@72Hz
[    93.196] (II) VESA(0): 640x480@75Hz
[    93.196] (II) VESA(0): 800x600@56Hz
[    93.196] (II) VESA(0): 800x600@60Hz
[    93.196] (II) VESA(0): 800x600@72Hz
[    93.196] (II) VESA(0): 800x600@75Hz
[    93.196] (II) VESA(0): 1024x768@60Hz
[    93.196] (II) VESA(0): 1024x768@70Hz
[    93.196] (II) VESA(0): 1024x768@75Hz
[    93.196] (II) VESA(0): Manufacturer's mask: 0
[    93.196] (II) VESA(0): Supported standard timings:
[    93.196] (II) VESA(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[    93.196] (II) VESA(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[    93.196] (II) VESA(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[    93.196] (II) VESA(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    93.196] (II) VESA(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    93.196] (II) VESA(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    93.196] (II) VESA(0): #6: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    93.196] (II) VESA(0): Supported detailed timing:
[    93.196] (II) VESA(0): clock: 80.0 MHz   Image Size:  16 x 9 mm
[    93.196] (II) VESA(0): h_active: 1366  h_sync: 1476  h_sync_end 1516 h_blank_end 1736 h_border: 0
[    93.196] (II) VESA(0): v_active: 768  v_sync: 773  v_sync_end 778 v_blanking: 798 v_border: 0
[    93.196] (II) VESA(0): Ranges: V min: 56 V max: 85 Hz, H min: 31 H max: 70 kHz, PixClock max 145 MHz
[    93.196] (II) VESA(0): Monitor name: TLX-04240B
[    93.196] (II) VESA(0): Serial No: 7186730002584
[    93.196] (II) VESA(0): EDID (in hex):
[    93.196] (II) VESA(0):     00ffffffffffff0042938f1098f4822b
[    93.196] (II) VESA(0):     2911010300583100eab2eda454489824
[    93.196] (II) VESA(0):     0f474aafce00315945596159714f8140
[    93.196] (II) VESA(0):     81808bc00101401f567251001e306e28
[    93.196] (II) VESA(0):     550010090000001e000000fd0038551f
[    93.196] (II) VESA(0):     460e000a202020202020000000fc0054
[    93.196] (II) VESA(0):     4c582d3034323430420a2020000000ff
[    93.196] (II) VESA(0):     00373138363733303030323538340047
[    93.196] (II) VESA(0): EDID vendor "PTS", prod id 4239
[    93.196] (II) VESA(0): Using EDID range info for horizontal sync
[    93.196] (II) VESA(0): Using EDID range info for vertical refresh
[    93.196] (II) VESA(0): Printing DDC gathered Modelines:
[    93.196] (II) VESA(0): Modeline "1366x768"x0.0   80.00  1366 1476 1516 1736  768 773 778 798 +hsync +vsync (46.1 kHz)
[    93.196] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    93.196] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    93.196] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    93.196] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    93.196] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    93.196] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    93.196] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    93.196] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    93.196] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    93.196] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    93.196] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    93.196] (II) VESA(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    93.196] (II) VESA(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    93.196] (II) VESA(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    93.196] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    93.196] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    93.196] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    93.196] (II) VESA(0): Modeline "1366x768"x59.8   84.75  1366 1432 1568 1776  768 770 780 798 -hsync +vsync (47.7 kHz)
[    93.196] (II) VESA(0): Searching for matching VESA mode(s):
[    93.196] Mode: 100 (640x400)
[    93.196]     ModeAttributes: 0xbb
[    93.196]     WinAAttributes: 0x7
[    93.196]     WinBAttributes: 0x0
[    93.196]     WinGranularity: 64
[    93.196]     WinSize: 64
[    93.196]     WinASegment: 0xa000
[    93.196]     WinBSegment: 0x0
[    93.196]     WinFuncPtr: 0xc00050ef
[    93.196]     BytesPerScanline: 640
[    93.196]     XResolution: 640
[    93.196]     YResolution: 400
[    93.196]     XCharSize: 8
[    93.196]     YCharSize: 16
[    93.196]     NumberOfPlanes: 1
[    93.196]     BitsPerPixel: 8
[    93.196]     NumberOfBanks: 1
[    93.196]     MemoryModel: 4
[    93.196]     BankSize: 0
[    93.196]     NumberOfImages: 63
[    93.196]     RedMaskSize: 0
[    93.197]     RedFieldPosition: 0
[    93.197]     GreenMaskSize: 0
[    93.197]     GreenFieldPosition: 0
[    93.197]     BlueMaskSize: 0
[    93.197]     BlueFieldPosition: 0
[    93.197]     RsvdMaskSize: 0
[    93.197]     RsvdFieldPosition: 0
[    93.197]     DirectColorModeInfo: 0
[    93.197]     PhysBasePtr: 0xd0000000
[    93.197]     LinBytesPerScanLine: 640
[    93.197]     BnkNumberOfImagePages: 63
[    93.197]     LinNumberOfImagePages: 63
[    93.197]     LinRedMaskSize: 0
[    93.197]     LinRedFieldPosition: 0
[    93.197]     LinGreenMaskSize: 0
[    93.197]     LinGreenFieldPosition: 0
[    93.197]     LinBlueMaskSize: 0
[    93.197]     LinBlueFieldPosition: 0
[    93.197]     LinRsvdMaskSize: 0
[    93.197]     LinRsvdFieldPosition: 0
[    93.197]     MaxPixelClock: 400000000
[    93.197] Mode: 101 (640x480)
[    93.197]     ModeAttributes: 0xbb
[    93.197]     WinAAttributes: 0x7
[    93.197]     WinBAttributes: 0x0
[    93.197]     WinGranularity: 64
[    93.197]     WinSize: 64
[    93.197]     WinASegment: 0xa000
[    93.197]     WinBSegment: 0x0
[    93.197]     WinFuncPtr: 0xc00050ef
[    93.197]     BytesPerScanline: 640
[    93.197]     XResolution: 640
[    93.197]     YResolution: 480
[    93.197]     XCharSize: 8
[    93.197]     YCharSize: 16
[    93.197]     NumberOfPlanes: 1
[    93.197]     BitsPerPixel: 8
[    93.197]     NumberOfBanks: 1
[    93.197]     MemoryModel: 4
[    93.197]     BankSize: 0
[    93.197]     NumberOfImages: 50
[    93.197]     RedMaskSize: 0
[    93.197]     RedFieldPosition: 0
[    93.197]     GreenMaskSize: 0
[    93.197]     GreenFieldPosition: 0
[    93.197]     BlueMaskSize: 0
[    93.197]     BlueFieldPosition: 0
[    93.197]     RsvdMaskSize: 0
[    93.197]     RsvdFieldPosition: 0
[    93.197]     DirectColorModeInfo: 0
[    93.197]     PhysBasePtr: 0xd0000000
[    93.197]     LinBytesPerScanLine: 640
[    93.197]     BnkNumberOfImagePages: 50
[    93.197]     LinNumberOfImagePages: 50
[    93.197]     LinRedMaskSize: 0
[    93.197]     LinRedFieldPosition: 0
[    93.197]     LinGreenMaskSize: 0
[    93.197]     LinGreenFieldPosition: 0
[    93.197]     LinBlueMaskSize: 0
[    93.197]     LinBlueFieldPosition: 0
[    93.197]     LinRsvdMaskSize: 0
[    93.197]     LinRsvdFieldPosition: 0
[    93.197]     MaxPixelClock: 400000000
[    93.197] Mode: 103 (800x600)
[    93.197]     ModeAttributes: 0xbb
[    93.197]     WinAAttributes: 0x7
[    93.197]     WinBAttributes: 0x0
[    93.197]     WinGranularity: 64
[    93.197]     WinSize: 64
[    93.197]     WinASegment: 0xa000
[    93.197]     WinBSegment: 0x0
[    93.197]     WinFuncPtr: 0xc00050ef
[    93.197]     BytesPerScanline: 832
[    93.197]     XResolution: 800
[    93.197]     YResolution: 600
[    93.197]     XCharSize: 8
[    93.197]     YCharSize: 14
[    93.197]     NumberOfPlanes: 1
[    93.197]     BitsPerPixel: 8
[    93.197]     NumberOfBanks: 1
[    93.197]     MemoryModel: 4
[    93.197]     BankSize: 0
[    93.197]     NumberOfImages: 31
[    93.197]     RedMaskSize: 0
[    93.197]     RedFieldPosition: 0
[    93.197]     GreenMaskSize: 0
[    93.197]     GreenFieldPosition: 0
[    93.197]     BlueMaskSize: 0
[    93.197]     BlueFieldPosition: 0
[    93.197]     RsvdMaskSize: 0
[    93.197]     RsvdFieldPosition: 0
[    93.197]     DirectColorModeInfo: 0
[    93.197]     PhysBasePtr: 0xd0000000
[    93.197]     LinBytesPerScanLine: 832
[    93.197]     BnkNumberOfImagePages: 31
[    93.197]     LinNumberOfImagePages: 31
[    93.197]     LinRedMaskSize: 0
[    93.197]     LinRedFieldPosition: 0
[    93.197]     LinGreenMaskSize: 0
[    93.197]     LinGreenFieldPosition: 0
[    93.197]     LinBlueMaskSize: 0
[    93.197]     LinBlueFieldPosition: 0
[    93.197]     LinRsvdMaskSize: 0
[    93.197]     LinRsvdFieldPosition: 0
[    93.197]     MaxPixelClock: 400000000
[    93.197] Mode: 105 (1024x768)
[    93.197]     ModeAttributes: 0xbb
[    93.197]     WinAAttributes: 0x7
[    93.197]     WinBAttributes: 0x0
[    93.197]     WinGranularity: 64
[    93.197]     WinSize: 64
[    93.197]     WinASegment: 0xa000
[    93.197]     WinBSegment: 0x0
[    93.197]     WinFuncPtr: 0xc00050ef
[    93.197]     BytesPerScanline: 1024
[    93.197]     XResolution: 1024
[    93.197]     YResolution: 768
[    93.197]     XCharSize: 8
[    93.197]     YCharSize: 16
[    93.197]     NumberOfPlanes: 1
[    93.197]     BitsPerPixel: 8
[    93.197]     NumberOfBanks: 1
[    93.197]     MemoryModel: 4
[    93.197]     BankSize: 0
[    93.197]     NumberOfImages: 18
[    93.197]     RedMaskSize: 0
[    93.197]     RedFieldPosition: 0
[    93.197]     GreenMaskSize: 0
[    93.197]     GreenFieldPosition: 0
[    93.198]     BlueMaskSize: 0
[    93.198]     BlueFieldPosition: 0
[    93.198]     RsvdMaskSize: 0
[    93.198]     RsvdFieldPosition: 0
[    93.198]     DirectColorModeInfo: 0
[    93.198]     PhysBasePtr: 0xd0000000
[    93.198]     LinBytesPerScanLine: 1024
[    93.198]     BnkNumberOfImagePages: 18
[    93.198]     LinNumberOfImagePages: 18
[    93.198]     LinRedMaskSize: 0
[    93.198]     LinRedFieldPosition: 0
[    93.198]     LinGreenMaskSize: 0
[    93.198]     LinGreenFieldPosition: 0
[    93.198]     LinBlueMaskSize: 0
[    93.198]     LinBlueFieldPosition: 0
[    93.198]     LinRsvdMaskSize: 0
[    93.198]     LinRsvdFieldPosition: 0
[    93.198]     MaxPixelClock: 400000000
[    93.198] Mode: 107 (1280x1024)
[    93.198]     ModeAttributes: 0xbb
[    93.198]     WinAAttributes: 0x7
[    93.198]     WinBAttributes: 0x0
[    93.198]     WinGranularity: 64
[    93.198]     WinSize: 64
[    93.198]     WinASegment: 0xa000
[    93.198]     WinBSegment: 0x0
[    93.198]     WinFuncPtr: 0xc00050ef
[    93.198]     BytesPerScanline: 1280
[    93.198]     XResolution: 1280
[    93.198]     YResolution: 1024
[    93.198]     XCharSize: 8
[    93.198]     YCharSize: 16
[    93.198]     NumberOfPlanes: 1
[    93.198]     BitsPerPixel: 8
[    93.198]     NumberOfBanks: 1
[    93.198]     MemoryModel: 4
[    93.198]     BankSize: 0
[    93.198]     NumberOfImages: 11
[    93.198]     RedMaskSize: 0
[    93.198]     RedFieldPosition: 0
[    93.198]     GreenMaskSize: 0
[    93.198]     GreenFieldPosition: 0
[    93.198]     BlueMaskSize: 0
[    93.198]     BlueFieldPosition: 0
[    93.198]     RsvdMaskSize: 0
[    93.198]     RsvdFieldPosition: 0
[    93.198]     DirectColorModeInfo: 0
[    93.198]     PhysBasePtr: 0xd0000000
[    93.198]     LinBytesPerScanLine: 1280
[    93.198]     BnkNumberOfImagePages: 11
[    93.198]     LinNumberOfImagePages: 11
[    93.198]     LinRedMaskSize: 0
[    93.198]     LinRedFieldPosition: 0
[    93.198]     LinGreenMaskSize: 0
[    93.198]     LinGreenFieldPosition: 0
[    93.198]     LinBlueMaskSize: 0
[    93.198]     LinBlueFieldPosition: 0
[    93.198]     LinRsvdMaskSize: 0
[    93.198]     LinRsvdFieldPosition: 0
[    93.198]     MaxPixelClock: 400000000
[    93.198] Mode: 110 (640x480)
[    93.198]     ModeAttributes: 0xbb
[    93.198]     WinAAttributes: 0x7
[    93.198]     WinBAttributes: 0x0
[    93.198]     WinGranularity: 64
[    93.198]     WinSize: 64
[    93.198]     WinASegment: 0xa000
[    93.198]     WinBSegment: 0x0
[    93.198]     WinFuncPtr: 0xc00050ef
[    93.198]     BytesPerScanline: 1280
[    93.198]     XResolution: 640
[    93.198]     YResolution: 480
[    93.198]     XCharSize: 8
[    93.198]     YCharSize: 16
[    93.198]     NumberOfPlanes: 1
[    93.198]     BitsPerPixel: 16
[    93.198]     NumberOfBanks: 1
[    93.198]     MemoryModel: 6
[    93.198]     BankSize: 0
[    93.198]     NumberOfImages: 24
[    93.198]     RedMaskSize: 5
[    93.198]     RedFieldPosition: 10
[    93.198]     GreenMaskSize: 5
[    93.198]     GreenFieldPosition: 5
[    93.198]     BlueMaskSize: 5
[    93.198]     BlueFieldPosition: 0
[    93.198]     RsvdMaskSize: 0
[    93.198]     RsvdFieldPosition: 0
[    93.198]     DirectColorModeInfo: 0
[    93.198]     PhysBasePtr: 0xd0000000
[    93.198]     LinBytesPerScanLine: 1280
[    93.198]     BnkNumberOfImagePages: 24
[    93.198]     LinNumberOfImagePages: 24
[    93.198]     LinRedMaskSize: 5
[    93.198]     LinRedFieldPosition: 10
[    93.198]     LinGreenMaskSize: 5
[    93.198]     LinGreenFieldPosition: 5
[    93.198]     LinBlueMaskSize: 5
[    93.198]     LinBlueFieldPosition: 0
[    93.198]     LinRsvdMaskSize: 0
[    93.198]     LinRsvdFieldPosition: 0
[    93.198]     MaxPixelClock: 400000000
[    93.198] Mode: 111 (640x480)
[    93.198]     ModeAttributes: 0xbb
[    93.198]     WinAAttributes: 0x7
[    93.198]     WinBAttributes: 0x0
[    93.198]     WinGranularity: 64
[    93.198]     WinSize: 64
[    93.198]     WinASegment: 0xa000
[    93.198]     WinBSegment: 0x0
[    93.198]     WinFuncPtr: 0xc00050ef
[    93.198]     BytesPerScanline: 1280
[    93.198]     XResolution: 640
[    93.198]     YResolution: 480
[    93.198]     XCharSize: 8
[    93.198]     YCharSize: 16
[    93.198]     NumberOfPlanes: 1
[    93.198]     BitsPerPixel: 16
[    93.198]     NumberOfBanks: 1
[    93.198]     MemoryModel: 6
[    93.198]     BankSize: 0
[    93.198]     NumberOfImages: 24
[    93.198]     RedMaskSize: 5
[    93.198]     RedFieldPosition: 11
[    93.198]     GreenMaskSize: 6
[    93.198]     GreenFieldPosition: 5
[    93.198]     BlueMaskSize: 5
[    93.198]     BlueFieldPosition: 0
[    93.198]     RsvdMaskSize: 0
[    93.198]     RsvdFieldPosition: 0
[    93.199]     DirectColorModeInfo: 0
[    93.199]     PhysBasePtr: 0xd0000000
[    93.199]     LinBytesPerScanLine: 1280
[    93.199]     BnkNumberOfImagePages: 24
[    93.199]     LinNumberOfImagePages: 24
[    93.199]     LinRedMaskSize: 5
[    93.199]     LinRedFieldPosition: 11
[    93.199]     LinGreenMaskSize: 6
[    93.199]     LinGreenFieldPosition: 5
[    93.199]     LinBlueMaskSize: 5
[    93.199]     LinBlueFieldPosition: 0
[    93.199]     LinRsvdMaskSize: 0
[    93.199]     LinRsvdFieldPosition: 0
[    93.199]     MaxPixelClock: 400000000
[    93.199] Mode: 113 (800x600)
[    93.199]     ModeAttributes: 0xbb
[    93.199]     WinAAttributes: 0x7
[    93.199]     WinBAttributes: 0x0
[    93.199]     WinGranularity: 64
[    93.199]     WinSize: 64
[    93.199]     WinASegment: 0xa000
[    93.199]     WinBSegment: 0x0
[    93.199]     WinFuncPtr: 0xc00050ef
[    93.199]     BytesPerScanline: 1600
[    93.199]     XResolution: 800
[    93.199]     YResolution: 600
[    93.199]     XCharSize: 8
[    93.199]     YCharSize: 14
[    93.199]     NumberOfPlanes: 1
[    93.199]     BitsPerPixel: 16
[    93.199]     NumberOfBanks: 1
[    93.199]     MemoryModel: 6
[    93.199]     BankSize: 0
[    93.199]     NumberOfImages: 16
[    93.199]     RedMaskSize: 5
[    93.199]     RedFieldPosition: 10
[    93.199]     GreenMaskSize: 5
[    93.199]     GreenFieldPosition: 5
[    93.199]     BlueMaskSize: 5
[    93.199]     BlueFieldPosition: 0
[    93.199]     RsvdMaskSize: 0
[    93.199]     RsvdFieldPosition: 0
[    93.199]     DirectColorModeInfo: 0
[    93.199]     PhysBasePtr: 0xd0000000
[    93.199]     LinBytesPerScanLine: 1600
[    93.199]     BnkNumberOfImagePages: 16
[    93.199]     LinNumberOfImagePages: 16
[    93.199]     LinRedMaskSize: 5
[    93.199]     LinRedFieldPosition: 10
[    93.199]     LinGreenMaskSize: 5
[    93.199]     LinGreenFieldPosition: 5
[    93.199]     LinBlueMaskSize: 5
[    93.199]     LinBlueFieldPosition: 0
[    93.199]     LinRsvdMaskSize: 0
[    93.199]     LinRsvdFieldPosition: 0
[    93.199]     MaxPixelClock: 400000000
[    93.199] Mode: 114 (800x600)
[    93.199]     ModeAttributes: 0xbb
[    93.199]     WinAAttributes: 0x7
[    93.199]     WinBAttributes: 0x0
[    93.199]     WinGranularity: 64
[    93.199]     WinSize: 64
[    93.199]     WinASegment: 0xa000
[    93.199]     WinBSegment: 0x0
[    93.199]     WinFuncPtr: 0xc00050ef
[    93.199]     BytesPerScanline: 1600
[    93.199]     XResolution: 800
[    93.199]     YResolution: 600
[    93.199]     XCharSize: 8
[    93.199]     YCharSize: 14
[    93.199]     NumberOfPlanes: 1
[    93.199]     BitsPerPixel: 16
[    93.199]     NumberOfBanks: 1
[    93.199]     MemoryModel: 6
[    93.199]     BankSize: 0
[    93.199]     NumberOfImages: 16
[    93.199]     RedMaskSize: 5
[    93.199]     RedFieldPosition: 11
[    93.199]     GreenMaskSize: 6
[    93.199]     GreenFieldPosition: 5
[    93.199]     BlueMaskSize: 5
[    93.199]     BlueFieldPosition: 0
[    93.199]     RsvdMaskSize: 0
[    93.199]     RsvdFieldPosition: 0
[    93.199]     DirectColorModeInfo: 0
[    93.199]     PhysBasePtr: 0xd0000000
[    93.199]     LinBytesPerScanLine: 1600
[    93.199]     BnkNumberOfImagePages: 16
[    93.199]     LinNumberOfImagePages: 16
[    93.199]     LinRedMaskSize: 5
[    93.199]     LinRedFieldPosition: 11
[    93.199]     LinGreenMaskSize: 6
[    93.199]     LinGreenFieldPosition: 5
[    93.199]     LinBlueMaskSize: 5
[    93.199]     LinBlueFieldPosition: 0
[    93.199]     LinRsvdMaskSize: 0
[    93.199]     LinRsvdFieldPosition: 0
[    93.199]     MaxPixelClock: 400000000
[    93.199] Mode: 116 (1024x768)
[    93.199]     ModeAttributes: 0xbb
[    93.199]     WinAAttributes: 0x7
[    93.199]     WinBAttributes: 0x0
[    93.199]     WinGranularity: 64
[    93.199]     WinSize: 64
[    93.199]     WinASegment: 0xa000
[    93.199]     WinBSegment: 0x0
[    93.199]     WinFuncPtr: 0xc00050ef
[    93.199]     BytesPerScanline: 2048
[    93.199]     XResolution: 1024
[    93.199]     YResolution: 768
[    93.199]     XCharSize: 8
[    93.199]     YCharSize: 16
[    93.199]     NumberOfPlanes: 1
[    93.199]     BitsPerPixel: 16
[    93.199]     NumberOfBanks: 1
[    93.199]     MemoryModel: 6
[    93.199]     BankSize: 0
[    93.199]     NumberOfImages: 9
[    93.199]     RedMaskSize: 5
[    93.199]     RedFieldPosition: 10
[    93.199]     GreenMaskSize: 5
[    93.199]     GreenFieldPosition: 5
[    93.199]     BlueMaskSize: 5
[    93.199]     BlueFieldPosition: 0
[    93.199]     RsvdMaskSize: 0
[    93.199]     RsvdFieldPosition: 0
[    93.199]     DirectColorModeInfo: 0
[    93.199]     PhysBasePtr: 0xd0000000
[    93.200]     LinBytesPerScanLine: 2048
[    93.200]     BnkNumberOfImagePages: 9
[    93.200]     LinNumberOfImagePages: 9
[    93.200]     LinRedMaskSize: 5
[    93.200]     LinRedFieldPosition: 10
[    93.200]     LinGreenMaskSize: 5
[    93.200]     LinGreenFieldPosition: 5
[    93.200]     LinBlueMaskSize: 5
[    93.200]     LinBlueFieldPosition: 0
[    93.200]     LinRsvdMaskSize: 0
[    93.200]     LinRsvdFieldPosition: 0
[    93.200]     MaxPixelClock: 400000000
[    93.200] Mode: 117 (1024x768)
[    93.200]     ModeAttributes: 0xbb
[    93.200]     WinAAttributes: 0x7
[    93.200]     WinBAttributes: 0x0
[    93.200]     WinGranularity: 64
[    93.200]     WinSize: 64
[    93.200]     WinASegment: 0xa000
[    93.200]     WinBSegment: 0x0
[    93.200]     WinFuncPtr: 0xc00050ef
[    93.200]     BytesPerScanline: 2048
[    93.200]     XResolution: 1024
[    93.200]     YResolution: 768
[    93.200]     XCharSize: 8
[    93.200]     YCharSize: 16
[    93.200]     NumberOfPlanes: 1
[    93.200]     BitsPerPixel: 16
[    93.200]     NumberOfBanks: 1
[    93.200]     MemoryModel: 6
[    93.200]     BankSize: 0
[    93.200]     NumberOfImages: 9
[    93.200]     RedMaskSize: 5
[    93.200]     RedFieldPosition: 11
[    93.200]     GreenMaskSize: 6
[    93.200]     GreenFieldPosition: 5
[    93.200]     BlueMaskSize: 5
[    93.200]     BlueFieldPosition: 0
[    93.200]     RsvdMaskSize: 0
[    93.200]     RsvdFieldPosition: 0
[    93.200]     DirectColorModeInfo: 0
[    93.200]     PhysBasePtr: 0xd0000000
[    93.200]     LinBytesPerScanLine: 2048
[    93.200]     BnkNumberOfImagePages: 9
[    93.200]     LinNumberOfImagePages: 9
[    93.200]     LinRedMaskSize: 5
[    93.200]     LinRedFieldPosition: 11
[    93.200]     LinGreenMaskSize: 6
[    93.200]     LinGreenFieldPosition: 5
[    93.200]     LinBlueMaskSize: 5
[    93.200]     LinBlueFieldPosition: 0
[    93.200]     LinRsvdMaskSize: 0
[    93.200]     LinRsvdFieldPosition: 0
[    93.200]     MaxPixelClock: 400000000
[    93.200] Mode: 119 (1280x1024)
[    93.200]     ModeAttributes: 0xbb
[    93.200]     WinAAttributes: 0x7
[    93.200]     WinBAttributes: 0x0
[    93.200]     WinGranularity: 64
[    93.200]     WinSize: 64
[    93.200]     WinASegment: 0xa000
[    93.200]     WinBSegment: 0x0
[    93.200]     WinFuncPtr: 0xc00050ef
[    93.200]     BytesPerScanline: 2560
[    93.200]     XResolution: 1280
[    93.200]     YResolution: 1024
[    93.200]     XCharSize: 8
[    93.200]     YCharSize: 16
[    93.200]     NumberOfPlanes: 1
[    93.200]     BitsPerPixel: 16
[    93.200]     NumberOfBanks: 1
[    93.200]     MemoryModel: 6
[    93.200]     BankSize: 0
[    93.200]     NumberOfImages: 5
[    93.200]     RedMaskSize: 5
[    93.200]     RedFieldPosition: 10
[    93.200]     GreenMaskSize: 5
[    93.200]     GreenFieldPosition: 5
[    93.200]     BlueMaskSize: 5
[    93.200]     BlueFieldPosition: 0
[    93.200]     RsvdMaskSize: 0
[    93.200]     RsvdFieldPosition: 0
[    93.200]     DirectColorModeInfo: 0
[    93.200]     PhysBasePtr: 0xd0000000
[    93.200]     LinBytesPerScanLine: 2560
[    93.200]     BnkNumberOfImagePages: 5
[    93.200]     LinNumberOfImagePages: 5
[    93.200]     LinRedMaskSize: 5
[    93.200]     LinRedFieldPosition: 10
[    93.200]     LinGreenMaskSize: 5
[    93.200]     LinGreenFieldPosition: 5
[    93.200]     LinBlueMaskSize: 5
[    93.200]     LinBlueFieldPosition: 0
[    93.200]     LinRsvdMaskSize: 0
[    93.200]     LinRsvdFieldPosition: 0
[    93.200]     MaxPixelClock: 400000000
[    93.200] Mode: 11a (1280x1024)
[    93.200]     ModeAttributes: 0xbb
[    93.201]     WinAAttributes: 0x7
[    93.201]     WinBAttributes: 0x0
[    93.201]     WinGranularity: 64
[    93.201]     WinSize: 64
[    93.201]     WinASegment: 0xa000
[    93.201]     WinBSegment: 0x0
[    93.201]     WinFuncPtr: 0xc00050ef
[    93.201]     BytesPerScanline: 2560
[    93.201]     XResolution: 1280
[    93.201]     YResolution: 1024
[    93.201]     XCharSize: 8
[    93.201]     YCharSize: 16
[    93.201]     NumberOfPlanes: 1
[    93.201]     BitsPerPixel: 16
[    93.201]     NumberOfBanks: 1
[    93.201]     MemoryModel: 6
[    93.201]     BankSize: 0
[    93.201]     NumberOfImages: 5
[    93.201]     RedMaskSize: 5
[    93.201]     RedFieldPosition: 11
[    93.201]     GreenMaskSize: 6
[    93.201]     GreenFieldPosition: 5
[    93.201]     BlueMaskSize: 5
[    93.201]     BlueFieldPosition: 0
[    93.201]     RsvdMaskSize: 0
[    93.201]     RsvdFieldPosition: 0
[    93.201]     DirectColorModeInfo: 0
[    93.201]     PhysBasePtr: 0xd0000000
[    93.201]     LinBytesPerScanLine: 2560
[    93.201]     BnkNumberOfImagePages: 5
[    93.201]     LinNumberOfImagePages: 5
[    93.201]     LinRedMaskSize: 5
[    93.201]     LinRedFieldPosition: 11
[    93.201]     LinGreenMaskSize: 6
[    93.201]     LinGreenFieldPosition: 5
[    93.201]     LinBlueMaskSize: 5
[    93.201]     LinBlueFieldPosition: 0
[    93.201]     LinRsvdMaskSize: 0
[    93.201]     LinRsvdFieldPosition: 0
[    93.201]     MaxPixelClock: 400000000
[    93.201] Mode: 10d (320x200)
[    93.201]     ModeAttributes: 0xbb
[    93.201]     WinAAttributes: 0x7
[    93.201]     WinBAttributes: 0x0
[    93.201]     WinGranularity: 64
[    93.201]     WinSize: 64
[    93.201]     WinASegment: 0xa000
[    93.201]     WinBSegment: 0x0
[    93.201]     WinFuncPtr: 0xc00050ef
[    93.201]     BytesPerScanline: 640
[    93.201]     XResolution: 320
[    93.201]     YResolution: 200
[    93.201]     XCharSize: 8
[    93.201]     YCharSize: 8
[    93.201]     NumberOfPlanes: 1
[    93.201]     BitsPerPixel: 16
[    93.201]     NumberOfBanks: 1
[    93.201]     MemoryModel: 6
[    93.201]     BankSize: 0
[    93.201]     NumberOfImages: 127
[    93.201]     RedMaskSize: 5
[    93.201]     RedFieldPosition: 10
[    93.201]     GreenMaskSize: 5
[    93.201]     GreenFieldPosition: 5
[    93.201]     BlueMaskSize: 5
[    93.201]     BlueFieldPosition: 0
[    93.201]     RsvdMaskSize: 0
[    93.201]     RsvdFieldPosition: 0
[    93.201]     DirectColorModeInfo: 0
[    93.201]     PhysBasePtr: 0xd0000000
[    93.201]     LinBytesPerScanLine: 640
[    93.201]     BnkNumberOfImagePages: 127
[    93.201]     LinNumberOfImagePages: 127
[    93.201]     LinRedMaskSize: 5
[    93.201]     LinRedFieldPosition: 10
[    93.201]     LinGreenMaskSize: 5
[    93.201]     LinGreenFieldPosition: 5
[    93.201]     LinBlueMaskSize: 5
[    93.201]     LinBlueFieldPosition: 0
[    93.201]     LinRsvdMaskSize: 0
[    93.201]     LinRsvdFieldPosition: 0
[    93.201]     MaxPixelClock: 400000000
[    93.201] Mode: 10e (320x200)
[    93.201]     ModeAttributes: 0xbb
[    93.201]     WinAAttributes: 0x7
[    93.201]     WinBAttributes: 0x0
[    93.201]     WinGranularity: 64
[    93.201]     WinSize: 64
[    93.201]     WinASegment: 0xa000
[    93.201]     WinBSegment: 0x0
[    93.201]     WinFuncPtr: 0xc00050ef
[    93.201]     BytesPerScanline: 640
[    93.201]     XResolution: 320
[    93.201]     YResolution: 200
[    93.201]     XCharSize: 8
[    93.201]     YCharSize: 8
[    93.201]     NumberOfPlanes: 1
[    93.201]     BitsPerPixel: 16
[    93.201]     NumberOfBanks: 1
[    93.201]     MemoryModel: 6
[    93.201]     BankSize: 0
[    93.201]     NumberOfImages: 127
[    93.201]     RedMaskSize: 5
[    93.201]     RedFieldPosition: 11
[    93.201]     GreenMaskSize: 6
[    93.201]     GreenFieldPosition: 5
[    93.201]     BlueMaskSize: 5
[    93.201]     BlueFieldPosition: 0
[    93.201]     RsvdMaskSize: 0
[    93.201]     RsvdFieldPosition: 0
[    93.201]     DirectColorModeInfo: 0
[    93.201]     PhysBasePtr: 0xd0000000
[    93.201]     LinBytesPerScanLine: 640
[    93.201]     BnkNumberOfImagePages: 127
[    93.201]     LinNumberOfImagePages: 127
[    93.201]     LinRedMaskSize: 5
[    93.201]     LinRedFieldPosition: 11
[    93.201]     LinGreenMaskSize: 6
[    93.201]     LinGreenFieldPosition: 5
[    93.201]     LinBlueMaskSize: 5
[    93.201]     LinBlueFieldPosition: 0
[    93.201]     LinRsvdMaskSize: 0
[    93.201]     LinRsvdFieldPosition: 0
[    93.201]     MaxPixelClock: 400000000
[    93.201] *Mode: 120 (320x200)
[    93.201]     ModeAttributes: 0xbb
[    93.201]     WinAAttributes: 0x7
[    93.201]     WinBAttributes: 0x0
[    93.201]     WinGranularity: 64
[    93.201]     WinSize: 64
[    93.201]     WinASegment: 0xa000
[    93.202]     WinBSegment: 0x0
[    93.202]     WinFuncPtr: 0xc00050ef
[    93.202]     BytesPerScanline: 1280
[    93.202]     XResolution: 320
[    93.202]     YResolution: 200
[    93.202]     XCharSize: 8
[    93.202]     YCharSize: 8
[    93.202]     NumberOfPlanes: 1
[    93.202]     BitsPerPixel: 32
[    93.202]     NumberOfBanks: 1
[    93.202]     MemoryModel: 6
[    93.202]     BankSize: 0
[    93.202]     NumberOfImages: 63
[    93.202]     RedMaskSize: 8
[    93.202]     RedFieldPosition: 16
[    93.202]     GreenMaskSize: 8
[    93.202]     GreenFieldPosition: 8
[    93.202]     BlueMaskSize: 8
[    93.202]     BlueFieldPosition: 0
[    93.202]     RsvdMaskSize: 0
[    93.202]     RsvdFieldPosition: 0
[    93.202]     DirectColorModeInfo: 0
[    93.202]     PhysBasePtr: 0xd0000000
[    93.202]     LinBytesPerScanLine: 1280
[    93.202]     BnkNumberOfImagePages: 63
[    93.202]     LinNumberOfImagePages: 63
[    93.202]     LinRedMaskSize: 8
[    93.202]     LinRedFieldPosition: 16
[    93.202]     LinGreenMaskSize: 8
[    93.202]     LinGreenFieldPosition: 8
[    93.202]     LinBlueMaskSize: 8
[    93.202]     LinBlueFieldPosition: 0
[    93.202]     LinRsvdMaskSize: 0
[    93.202]     LinRsvdFieldPosition: 0
[    93.202]     MaxPixelClock: 400000000
[    93.202] Mode: 193 (320x240)
[    93.202]     ModeAttributes: 0xbb
[    93.202]     WinAAttributes: 0x7
[    93.202]     WinBAttributes: 0x0
[    93.202]     WinGranularity: 64
[    93.202]     WinSize: 64
[    93.202]     WinASegment: 0xa000
[    93.202]     WinBSegment: 0x0
[    93.202]     WinFuncPtr: 0xc00050ef
[    93.202]     BytesPerScanline: 320
[    93.202]     XResolution: 320
[    93.202]     YResolution: 240
[    93.202]     XCharSize: 8
[    93.202]     YCharSize: 8
[    93.202]     NumberOfPlanes: 1
[    93.202]     BitsPerPixel: 8
[    93.202]     NumberOfBanks: 1
[    93.202]     MemoryModel: 4
[    93.202]     BankSize: 0
[    93.202]     NumberOfImages: 127
[    93.202]     RedMaskSize: 0
[    93.202]     RedFieldPosition: 0
[    93.202]     GreenMaskSize: 0
[    93.202]     GreenFieldPosition: 0
[    93.202]     BlueMaskSize: 0
[    93.202]     BlueFieldPosition: 0
[    93.202]     RsvdMaskSize: 0
[    93.202]     RsvdFieldPosition: 0
[    93.202]     DirectColorModeInfo: 0
[    93.202]     PhysBasePtr: 0xd0000000
[    93.202]     LinBytesPerScanLine: 320
[    93.202]     BnkNumberOfImagePages: 127
[    93.202]     LinNumberOfImagePages: 127
[    93.202]     LinRedMaskSize: 0
[    93.202]     LinRedFieldPosition: 0
[    93.202]     LinGreenMaskSize: 0
[    93.202]     LinGreenFieldPosition: 0
[    93.202]     LinBlueMaskSize: 0
[    93.202]     LinBlueFieldPosition: 0
[    93.202]     LinRsvdMaskSize: 0
[    93.202]     LinRsvdFieldPosition: 0
[    93.202]     MaxPixelClock: 400000000
[    93.202] Mode: 195 (320x240)
[    93.202]     ModeAttributes: 0xbb
[    93.202]     WinAAttributes: 0x7
[    93.202]     WinBAttributes: 0x0
[    93.202]     WinGranularity: 64
[    93.202]     WinSize: 64
[    93.202]     WinASegment: 0xa000
[    93.202]     WinBSegment: 0x0
[    93.202]     WinFuncPtr: 0xc00050ef
[    93.202]     BytesPerScanline: 640
[    93.202]     XResolution: 320
[    93.202]     YResolution: 240
[    93.202]     XCharSize: 8
[    93.202]     YCharSize: 8
[    93.202]     NumberOfPlanes: 1
[    93.202]     BitsPerPixel: 16
[    93.202]     NumberOfBanks: 1
[    93.202]     MemoryModel: 6
[    93.202]     BankSize: 0
[    93.202]     NumberOfImages: 84
[    93.202]     RedMaskSize: 5
[    93.202]     RedFieldPosition: 11
[    93.202]     GreenMaskSize: 6
[    93.202]     GreenFieldPosition: 5
[    93.202]     BlueMaskSize: 5
[    93.202]     BlueFieldPosition: 0
[    93.202]     RsvdMaskSize: 0
[    93.202]     RsvdFieldPosition: 0
[    93.202]     DirectColorModeInfo: 0
[    93.202]     PhysBasePtr: 0xd0000000
[    93.202]     LinBytesPerScanLine: 640
[    93.202]     BnkNumberOfImagePages: 84
[    93.202]     LinNumberOfImagePages: 84
[    93.202]     LinRedMaskSize: 5
[    93.202]     LinRedFieldPosition: 11
[    93.202]     LinGreenMaskSize: 6
[    93.202]     LinGreenFieldPosition: 5
[    93.202]     LinBlueMaskSize: 5
[    93.202]     LinBlueFieldPosition: 0
[    93.202]     LinRsvdMaskSize: 0
[    93.202]     LinRsvdFieldPosition: 0
[    93.202]     MaxPixelClock: 400000000
[    93.203] *Mode: 196 (320x240)
[    93.203]     ModeAttributes: 0xbb
[    93.203]     WinAAttributes: 0x7
[    93.203]     WinBAttributes: 0x0
[    93.203]     WinGranularity: 64
[    93.203]     WinSize: 64
[    93.203]     WinASegment: 0xa000
[    93.203]     WinBSegment: 0x0
[    93.203]     WinFuncPtr: 0xc00050ef
[    93.203]     BytesPerScanline: 1280
[    93.203]     XResolution: 320
[    93.203]     YResolution: 240
[    93.203]     XCharSize: 8
[    93.203]     YCharSize: 8
[    93.203]     NumberOfPlanes: 1
[    93.203]     BitsPerPixel: 32
[    93.203]     NumberOfBanks: 1
[    93.203]     MemoryModel: 6
[    93.203]     BankSize: 0
[    93.203]     NumberOfImages: 50
[    93.203]     RedMaskSize: 8
[    93.203]     RedFieldPosition: 16
[    93.203]     GreenMaskSize: 8
[    93.203]     GreenFieldPosition: 8
[    93.203]     BlueMaskSize: 8
[    93.203]     BlueFieldPosition: 0
[    93.203]     RsvdMaskSize: 0
[    93.203]     RsvdFieldPosition: 0
[    93.203]     DirectColorModeInfo: 0
[    93.203]     PhysBasePtr: 0xd0000000
[    93.203]     LinBytesPerScanLine: 1280
[    93.203]     BnkNumberOfImagePages: 50
[    93.203]     LinNumberOfImagePages: 50
[    93.203]     LinRedMaskSize: 8
[    93.203]     LinRedFieldPosition: 16
[    93.203]     LinGreenMaskSize: 8
[    93.203]     LinGreenFieldPosition: 8
[    93.203]     LinBlueMaskSize: 8
[    93.203]     LinBlueFieldPosition: 0
[    93.203]     LinRsvdMaskSize: 0
[    93.203]     LinRsvdFieldPosition: 0
[    93.203]     MaxPixelClock: 400000000
[    93.203] Mode: 1b3 (512x384)
[    93.203]     ModeAttributes: 0xbb
[    93.203]     WinAAttributes: 0x7
[    93.203]     WinBAttributes: 0x0
[    93.203]     WinGranularity: 64
[    93.203]     WinSize: 64
[    93.203]     WinASegment: 0xa000
[    93.203]     WinBSegment: 0x0
[    93.203]     WinFuncPtr: 0xc00050ef
[    93.203]     BytesPerScanline: 512
[    93.203]     XResolution: 512
[    93.203]     YResolution: 384
[    93.203]     XCharSize: 8
[    93.203]     YCharSize: 16
[    93.203]     NumberOfPlanes: 1
[    93.203]     BitsPerPixel: 8
[    93.203]     NumberOfBanks: 1
[    93.203]     MemoryModel: 4
[    93.203]     BankSize: 0
[    93.203]     NumberOfImages: 63
[    93.203]     RedMaskSize: 0
[    93.203]     RedFieldPosition: 0
[    93.203]     GreenMaskSize: 0
[    93.203]     GreenFieldPosition: 0
[    93.203]     BlueMaskSize: 0
[    93.203]     BlueFieldPosition: 0
[    93.203]     RsvdMaskSize: 0
[    93.203]     RsvdFieldPosition: 0
[    93.203]     DirectColorModeInfo: 0
[    93.203]     PhysBasePtr: 0xd0000000
[    93.203]     LinBytesPerScanLine: 512
[    93.203]     BnkNumberOfImagePages: 63
[    93.203]     LinNumberOfImagePages: 63
[    93.203]     LinRedMaskSize: 0
[    93.203]     LinRedFieldPosition: 0
[    93.203]     LinGreenMaskSize: 0
[    93.203]     LinGreenFieldPosition: 0
[    93.203]     LinBlueMaskSize: 0
[    93.203]     LinBlueFieldPosition: 0
[    93.203]     LinRsvdMaskSize: 0
[    93.203]     LinRsvdFieldPosition: 0
[    93.203]     MaxPixelClock: 400000000
[    93.203] Mode: 1b5 (512x384)
[    93.203]     ModeAttributes: 0xbb
[    93.203]     WinAAttributes: 0x7
[    93.203]     WinBAttributes: 0x0
[    93.203]     WinGranularity: 64
[    93.203]     WinSize: 64
[    93.203]     WinASegment: 0xa000
[    93.203]     WinBSegment: 0x0
[    93.203]     WinFuncPtr: 0xc00050ef
[    93.203]     BytesPerScanline: 1024
[    93.203]     XResolution: 512
[    93.203]     YResolution: 384
[    93.203]     XCharSize: 8
[    93.203]     YCharSize: 16
[    93.203]     NumberOfPlanes: 1
[    93.203]     BitsPerPixel: 16
[    93.203]     NumberOfBanks: 1
[    93.203]     MemoryModel: 6
[    93.203]     BankSize: 0
[    93.203]     NumberOfImages: 35
[    93.203]     RedMaskSize: 5
[    93.203]     RedFieldPosition: 11
[    93.203]     GreenMaskSize: 6
[    93.203]     GreenFieldPosition: 5
[    93.203]     BlueMaskSize: 5
[    93.203]     BlueFieldPosition: 0
[    93.203]     RsvdMaskSize: 0
[    93.203]     RsvdFieldPosition: 0
[    93.203]     DirectColorModeInfo: 0
[    93.203]     PhysBasePtr: 0xd0000000
[    93.203]     LinBytesPerScanLine: 1024
[    93.203]     BnkNumberOfImagePages: 35
[    93.203]     LinNumberOfImagePages: 35
[    93.203]     LinRedMaskSize: 5
[    93.203]     LinRedFieldPosition: 11
[    93.203]     LinGreenMaskSize: 6
[    93.203]     LinGreenFieldPosition: 5
[    93.203]     LinBlueMaskSize: 5
[    93.203]     LinBlueFieldPosition: 0
[    93.203]     LinRsvdMaskSize: 0
[    93.203]     LinRsvdFieldPosition: 0
[    93.203]     MaxPixelClock: 400000000
[    93.204] *Mode: 1b6 (512x384)
[    93.204]     ModeAttributes: 0xbb
[    93.204]     WinAAttributes: 0x7
[    93.204]     WinBAttributes: 0x0
[    93.204]     WinGranularity: 64
[    93.204]     WinSize: 64
[    93.204]     WinASegment: 0xa000
[    93.204]     WinBSegment: 0x0
[    93.204]     WinFuncPtr: 0xc00050ef
[    93.204]     BytesPerScanline: 2048
[    93.204]     XResolution: 512
[    93.204]     YResolution: 384
[    93.204]     XCharSize: 8
[    93.204]     YCharSize: 16
[    93.204]     NumberOfPlanes: 1
[    93.204]     BitsPerPixel: 32
[    93.204]     NumberOfBanks: 1
[    93.204]     MemoryModel: 6
[    93.204]     BankSize: 0
[    93.204]     NumberOfImages: 18
[    93.204]     RedMaskSize: 8
[    93.204]     RedFieldPosition: 16
[    93.204]     GreenMaskSize: 8
[    93.204]     GreenFieldPosition: 8
[    93.204]     BlueMaskSize: 8
[    93.204]     BlueFieldPosition: 0
[    93.204]     RsvdMaskSize: 0
[    93.204]     RsvdFieldPosition: 0
[    93.204]     DirectColorModeInfo: 0
[    93.204]     PhysBasePtr: 0xd0000000
[    93.204]     LinBytesPerScanLine: 2048
[    93.204]     BnkNumberOfImagePages: 18
[    93.204]     LinNumberOfImagePages: 18
[    93.204]     LinRedMaskSize: 8
[    93.204]     LinRedFieldPosition: 16
[    93.204]     LinGreenMaskSize: 8
[    93.204]     LinGreenFieldPosition: 8
[    93.204]     LinBlueMaskSize: 8
[    93.204]     LinBlueFieldPosition: 0
[    93.204]     LinRsvdMaskSize: 0
[    93.204]     LinRsvdFieldPosition: 0
[    93.204]     MaxPixelClock: 400000000
[    93.204] Mode: 1c3 (640x350)
[    93.204]     ModeAttributes: 0xbb
[    93.204]     WinAAttributes: 0x7
[    93.204]     WinBAttributes: 0x0
[    93.204]     WinGranularity: 64
[    93.204]     WinSize: 64
[    93.204]     WinASegment: 0xa000
[    93.204]     WinBSegment: 0x0
[    93.204]     WinFuncPtr: 0xc00050ef
[    93.204]     BytesPerScanline: 640
[    93.204]     XResolution: 640
[    93.204]     YResolution: 350
[    93.204]     XCharSize: 8
[    93.204]     YCharSize: 14
[    93.204]     NumberOfPlanes: 1
[    93.204]     BitsPerPixel: 8
[    93.204]     NumberOfBanks: 1
[    93.204]     MemoryModel: 4
[    93.204]     BankSize: 0
[    93.204]     NumberOfImages: 63
[    93.204]     RedMaskSize: 0
[    93.204]     RedFieldPosition: 0
[    93.204]     GreenMaskSize: 0
[    93.204]     GreenFieldPosition: 0
[    93.204]     BlueMaskSize: 0
[    93.204]     BlueFieldPosition: 0
[    93.204]     RsvdMaskSize: 0
[    93.204]     RsvdFieldPosition: 0
[    93.204]     DirectColorModeInfo: 0
[    93.204]     PhysBasePtr: 0xd0000000
[    93.204]     LinBytesPerScanLine: 640
[    93.204]     BnkNumberOfImagePages: 63
[    93.204]     LinNumberOfImagePages: 63
[    93.204]     LinRedMaskSize: 0
[    93.204]     LinRedFieldPosition: 0
[    93.204]     LinGreenMaskSize: 0
[    93.204]     LinGreenFieldPosition: 0
[    93.204]     LinBlueMaskSize: 0
[    93.204]     LinBlueFieldPosition: 0
[    93.204]     LinRsvdMaskSize: 0
[    93.204]     LinRsvdFieldPosition: 0
[    93.204]     MaxPixelClock: 400000000
[    93.204] Mode: 1c5 (640x350)
[    93.204]     ModeAttributes: 0xbb
[    93.204]     WinAAttributes: 0x7
[    93.204]     WinBAttributes: 0x0
[    93.204]     WinGranularity: 64
[    93.204]     WinSize: 64
[    93.204]     WinASegment: 0xa000
[    93.204]     WinBSegment: 0x0
[    93.204]     WinFuncPtr: 0xc00050ef
[    93.204]     BytesPerScanline: 1280
[    93.204]     XResolution: 640
[    93.204]     YResolution: 350
[    93.204]     XCharSize: 8
[    93.204]     YCharSize: 14
[    93.204]     NumberOfPlanes: 1
[    93.204]     BitsPerPixel: 16
[    93.204]     NumberOfBanks: 1
[    93.204]     MemoryModel: 6
[    93.204]     BankSize: 0
[    93.204]     NumberOfImages: 35
[    93.204]     RedMaskSize: 5
[    93.204]     RedFieldPosition: 11
[    93.204]     GreenMaskSize: 6
[    93.204]     GreenFieldPosition: 5
[    93.204]     BlueMaskSize: 5
[    93.204]     BlueFieldPosition: 0
[    93.204]     RsvdMaskSize: 0
[    93.204]     RsvdFieldPosition: 0
[    93.204]     DirectColorModeInfo: 0
[    93.204]     PhysBasePtr: 0xd0000000
[    93.204]     LinBytesPerScanLine: 1280
[    93.204]     BnkNumberOfImagePages: 35
[    93.204]     LinNumberOfImagePages: 35
[    93.204]     LinRedMaskSize: 5
[    93.204]     LinRedFieldPosition: 11
[    93.204]     LinGreenMaskSize: 6
[    93.204]     LinGreenFieldPosition: 5
[    93.204]     LinBlueMaskSize: 5
[    93.204]     LinBlueFieldPosition: 0
[    93.204]     LinRsvdMaskSize: 0
[    93.204]     LinRsvdFieldPosition: 0
[    93.204]     MaxPixelClock: 400000000
[    93.205] *Mode: 1c6 (640x350)
[    93.205]     ModeAttributes: 0xbb
[    93.205]     WinAAttributes: 0x7
[    93.205]     WinBAttributes: 0x0
[    93.205]     WinGranularity: 64
[    93.205]     WinSize: 64
[    93.205]     WinASegment: 0xa000
[    93.205]     WinBSegment: 0x0
[    93.205]     WinFuncPtr: 0xc00050ef
[    93.205]     BytesPerScanline: 2560
[    93.205]     XResolution: 640
[    93.205]     YResolution: 350
[    93.205]     XCharSize: 8
[    93.205]     YCharSize: 14
[    93.205]     NumberOfPlanes: 1
[    93.205]     BitsPerPixel: 32
[    93.205]     NumberOfBanks: 1
[    93.205]     MemoryModel: 6
[    93.205]     BankSize: 0
[    93.205]     NumberOfImages: 17
[    93.205]     RedMaskSize: 8
[    93.205]     RedFieldPosition: 16
[    93.205]     GreenMaskSize: 8
[    93.205]     GreenFieldPosition: 8
[    93.205]     BlueMaskSize: 8
[    93.205]     BlueFieldPosition: 0
[    93.205]     RsvdMaskSize: 0
[    93.205]     RsvdFieldPosition: 0
[    93.205]     DirectColorModeInfo: 0
[    93.205]     PhysBasePtr: 0xd0000000
[    93.205]     LinBytesPerScanLine: 2560
[    93.205]     BnkNumberOfImagePages: 17
[    93.205]     LinNumberOfImagePages: 17
[    93.205]     LinRedMaskSize: 8
[    93.205]     LinRedFieldPosition: 16
[    93.205]     LinGreenMaskSize: 8
[    93.205]     LinGreenFieldPosition: 8
[    93.205]     LinBlueMaskSize: 8
[    93.205]     LinBlueFieldPosition: 0
[    93.205]     LinRsvdMaskSize: 0
[    93.205]     LinRsvdFieldPosition: 0
[    93.205]     MaxPixelClock: 400000000
[    93.205] Mode: 133 (720x400)
[    93.205]     ModeAttributes: 0xbb
[    93.205]     WinAAttributes: 0x7
[    93.205]     WinBAttributes: 0x0
[    93.205]     WinGranularity: 64
[    93.205]     WinSize: 64
[    93.205]     WinASegment: 0xa000
[    93.205]     WinBSegment: 0x0
[    93.205]     WinFuncPtr: 0xc00050ef
[    93.205]     BytesPerScanline: 768
[    93.205]     XResolution: 720
[    93.205]     YResolution: 400
[    93.205]     XCharSize: 8
[    93.205]     YCharSize: 16
[    93.205]     NumberOfPlanes: 1
[    93.205]     BitsPerPixel: 8
[    93.205]     NumberOfBanks: 1
[    93.205]     MemoryModel: 4
[    93.205]     BankSize: 0
[    93.205]     NumberOfImages: 50
[    93.205]     RedMaskSize: 0
[    93.205]     RedFieldPosition: 0
[    93.205]     GreenMaskSize: 0
[    93.205]     GreenFieldPosition: 0
[    93.205]     BlueMaskSize: 0
[    93.205]     BlueFieldPosition: 0
[    93.205]     RsvdMaskSize: 0
[    93.205]     RsvdFieldPosition: 0
[    93.205]     DirectColorModeInfo: 0
[    93.205]     PhysBasePtr: 0xd0000000
[    93.205]     LinBytesPerScanLine: 768
[    93.205]     BnkNumberOfImagePages: 50
[    93.205]     LinNumberOfImagePages: 50
[    93.205]     LinRedMaskSize: 0
[    93.205]     LinRedFieldPosition: 0
[    93.205]     LinGreenMaskSize: 0
[    93.205]     LinGreenFieldPosition: 0
[    93.205]     LinBlueMaskSize: 0
[    93.205]     LinBlueFieldPosition: 0
[    93.205]     LinRsvdMaskSize: 0
[    93.205]     LinRsvdFieldPosition: 0
[    93.205]     MaxPixelClock: 400000000
[    93.205] Mode: 135 (720x400)
[    93.205]     ModeAttributes: 0xbb
[    93.205]     WinAAttributes: 0x7
[    93.205]     WinBAttributes: 0x0
[    93.205]     WinGranularity: 64
[    93.205]     WinSize: 64
[    93.205]     WinASegment: 0xa000
[    93.205]     WinBSegment: 0x0
[    93.205]     WinFuncPtr: 0xc00050ef
[    93.205]     BytesPerScanline: 1472
[    93.205]     XResolution: 720
[    93.205]     YResolution: 400
[    93.205]     XCharSize: 8
[    93.205]     YCharSize: 16
[    93.205]     NumberOfPlanes: 1
[    93.205]     BitsPerPixel: 16
[    93.205]     NumberOfBanks: 1
[    93.205]     MemoryModel: 6
[    93.205]     BankSize: 0
[    93.205]     NumberOfImages: 27
[    93.205]     RedMaskSize: 5
[    93.205]     RedFieldPosition: 11
[    93.205]     GreenMaskSize: 6
[    93.205]     GreenFieldPosition: 5
[    93.205]     BlueMaskSize: 5
[    93.205]     BlueFieldPosition: 0
[    93.205]     RsvdMaskSize: 0
[    93.205]     RsvdFieldPosition: 0
[    93.205]     DirectColorModeInfo: 0
[    93.205]     PhysBasePtr: 0xd0000000
[    93.205]     LinBytesPerScanLine: 1472
[    93.205]     BnkNumberOfImagePages: 27
[    93.205]     LinNumberOfImagePages: 27
[    93.205]     LinRedMaskSize: 5
[    93.205]     LinRedFieldPosition: 11
[    93.205]     LinGreenMaskSize: 6
[    93.205]     LinGreenFieldPosition: 5
[    93.205]     LinBlueMaskSize: 5
[    93.205]     LinBlueFieldPosition: 0
[    93.205]     LinRsvdMaskSize: 0
[    93.205]     LinRsvdFieldPosition: 0
[    93.205]     MaxPixelClock: 400000000
[    93.206] *Mode: 136 (720x400)
[    93.206]     ModeAttributes: 0xbb
[    93.206]     WinAAttributes: 0x7
[    93.206]     WinBAttributes: 0x0
[    93.206]     WinGranularity: 64
[    93.206]     WinSize: 64
[    93.206]     WinASegment: 0xa000
[    93.206]     WinBSegment: 0x0
[    93.206]     WinFuncPtr: 0xc00050ef
[    93.206]     BytesPerScanline: 2944
[    93.206]     XResolution: 720
[    93.206]     YResolution: 400
[    93.206]     XCharSize: 8
[    93.206]     YCharSize: 16
[    93.206]     NumberOfPlanes: 1
[    93.206]     BitsPerPixel: 32
[    93.206]     NumberOfBanks: 1
[    93.206]     MemoryModel: 6
[    93.206]     BankSize: 0
[    93.206]     NumberOfImages: 13
[    93.206]     RedMaskSize: 8
[    93.206]     RedFieldPosition: 16
[    93.206]     GreenMaskSize: 8
[    93.206]     GreenFieldPosition: 8
[    93.206]     BlueMaskSize: 8
[    93.206]     BlueFieldPosition: 0
[    93.206]     RsvdMaskSize: 0
[    93.206]     RsvdFieldPosition: 0
[    93.206]     DirectColorModeInfo: 0
[    93.206]     PhysBasePtr: 0xd0000000
[    93.206]     LinBytesPerScanLine: 2944
[    93.206]     BnkNumberOfImagePages: 13
[    93.206]     LinNumberOfImagePages: 13
[    93.206]     LinRedMaskSize: 8
[    93.206]     LinRedFieldPosition: 16
[    93.206]     LinGreenMaskSize: 8
[    93.206]     LinGreenFieldPosition: 8
[    93.206]     LinBlueMaskSize: 8
[    93.206]     LinBlueFieldPosition: 0
[    93.206]     LinRsvdMaskSize: 0
[    93.206]     LinRsvdFieldPosition: 0
[    93.206]     MaxPixelClock: 400000000
[    93.206] Mode: 153 (1152x864)
[    93.206]     ModeAttributes: 0xbb
[    93.206]     WinAAttributes: 0x7
[    93.206]     WinBAttributes: 0x0
[    93.206]     WinGranularity: 64
[    93.206]     WinSize: 64
[    93.206]     WinASegment: 0xa000
[    93.206]     WinBSegment: 0x0
[    93.206]     WinFuncPtr: 0xc00050ef
[    93.206]     BytesPerScanline: 1152
[    93.206]     XResolution: 1152
[    93.206]     YResolution: 864
[    93.206]     XCharSize: 8
[    93.206]     YCharSize: 16
[    93.206]     NumberOfPlanes: 1
[    93.206]     BitsPerPixel: 8
[    93.206]     NumberOfBanks: 1
[    93.206]     MemoryModel: 4
[    93.206]     BankSize: 0
[    93.206]     NumberOfImages: 15
[    93.206]     RedMaskSize: 0
[    93.206]     RedFieldPosition: 0
[    93.206]     GreenMaskSize: 0
[    93.206]     GreenFieldPosition: 0
[    93.206]     BlueMaskSize: 0
[    93.206]     BlueFieldPosition: 0
[    93.206]     RsvdMaskSize: 0
[    93.206]     RsvdFieldPosition: 0
[    93.206]     DirectColorModeInfo: 0
[    93.206]     PhysBasePtr: 0xd0000000
[    93.206]     LinBytesPerScanLine: 1152
[    93.206]     BnkNumberOfImagePages: 15
[    93.206]     LinNumberOfImagePages: 15
[    93.206]     LinRedMaskSize: 0
[    93.206]     LinRedFieldPosition: 0
[    93.206]     LinGreenMaskSize: 0
[    93.206]     LinGreenFieldPosition: 0
[    93.206]     LinBlueMaskSize: 0
[    93.206]     LinBlueFieldPosition: 0
[    93.206]     LinRsvdMaskSize: 0
[    93.206]     LinRsvdFieldPosition: 0
[    93.206]     MaxPixelClock: 400000000
[    93.206] Mode: 155 (1152x864)
[    93.206]     ModeAttributes: 0xbb
[    93.206]     WinAAttributes: 0x7
[    93.206]     WinBAttributes: 0x0
[    93.206]     WinGranularity: 64
[    93.206]     WinSize: 64
[    93.206]     WinASegment: 0xa000
[    93.206]     WinBSegment: 0x0
[    93.206]     WinFuncPtr: 0xc00050ef
[    93.206]     BytesPerScanline: 2304
[    93.206]     XResolution: 1152
[    93.206]     YResolution: 864
[    93.206]     XCharSize: 8
[    93.206]     YCharSize: 16
[    93.206]     NumberOfPlanes: 1
[    93.206]     BitsPerPixel: 16
[    93.206]     NumberOfBanks: 1
[    93.206]     MemoryModel: 6
[    93.206]     BankSize: 0
[    93.206]     NumberOfImages: 7
[    93.206]     RedMaskSize: 5
[    93.206]     RedFieldPosition: 11
[    93.206]     GreenMaskSize: 6
[    93.206]     GreenFieldPosition: 5
[    93.206]     BlueMaskSize: 5
[    93.206]     BlueFieldPosition: 0
[    93.206]     RsvdMaskSize: 0
[    93.206]     RsvdFieldPosition: 0
[    93.206]     DirectColorModeInfo: 0
[    93.206]     PhysBasePtr: 0xd0000000
[    93.206]     LinBytesPerScanLine: 2304
[    93.206]     BnkNumberOfImagePages: 7
[    93.206]     LinNumberOfImagePages: 7
[    93.206]     LinRedMaskSize: 5
[    93.206]     LinRedFieldPosition: 11
[    93.206]     LinGreenMaskSize: 6
[    93.206]     LinGreenFieldPosition: 5
[    93.206]     LinBlueMaskSize: 5
[    93.206]     LinBlueFieldPosition: 0
[    93.206]     LinRsvdMaskSize: 0
[    93.206]     LinRsvdFieldPosition: 0
[    93.206]     MaxPixelClock: 400000000
[    93.207] *Mode: 156 (1152x864)
[    93.207]     ModeAttributes: 0xbb
[    93.207]     WinAAttributes: 0x7
[    93.207]     WinBAttributes: 0x0
[    93.207]     WinGranularity: 64
[    93.207]     WinSize: 64
[    93.207]     WinASegment: 0xa000
[    93.207]     WinBSegment: 0x0
[    93.207]     WinFuncPtr: 0xc00050ef
[    93.207]     BytesPerScanline: 4608
[    93.207]     XResolution: 1152
[    93.207]     YResolution: 864
[    93.207]     XCharSize: 8
[    93.207]     YCharSize: 16
[    93.207]     NumberOfPlanes: 1
[    93.207]     BitsPerPixel: 32
[    93.207]     NumberOfBanks: 1
[    93.207]     MemoryModel: 6
[    93.207]     BankSize: 0
[    93.207]     NumberOfImages: 3
[    93.207]     RedMaskSize: 8
[    93.207]     RedFieldPosition: 16
[    93.207]     GreenMaskSize: 8
[    93.207]     GreenFieldPosition: 8
[    93.207]     BlueMaskSize: 8
[    93.207]     BlueFieldPosition: 0
[    93.207]     RsvdMaskSize: 0
[    93.207]     RsvdFieldPosition: 0
[    93.207]     DirectColorModeInfo: 0
[    93.207]     PhysBasePtr: 0xd0000000
[    93.207]     LinBytesPerScanLine: 4608
[    93.207]     BnkNumberOfImagePages: 3
[    93.207]     LinNumberOfImagePages: 3
[    93.207]     LinRedMaskSize: 8
[    93.207]     LinRedFieldPosition: 16
[    93.207]     LinGreenMaskSize: 8
[    93.207]     LinGreenFieldPosition: 8
[    93.207]     LinBlueMaskSize: 8
[    93.207]     LinBlueFieldPosition: 0
[    93.207]     LinRsvdMaskSize: 0
[    93.207]     LinRsvdFieldPosition: 0
[    93.207]     MaxPixelClock: 400000000
[    93.207] Mode: 163 (1280x960)
[    93.207]     ModeAttributes: 0xbb
[    93.207]     WinAAttributes: 0x7
[    93.207]     WinBAttributes: 0x0
[    93.207]     WinGranularity: 64
[    93.207]     WinSize: 64
[    93.207]     WinASegment: 0xa000
[    93.207]     WinBSegment: 0x0
[    93.207]     WinFuncPtr: 0xc00050ef
[    93.207]     BytesPerScanline: 1280
[    93.207]     XResolution: 1280
[    93.207]     YResolution: 960
[    93.207]     XCharSize: 8
[    93.207]     YCharSize: 16
[    93.207]     NumberOfPlanes: 1
[    93.207]     BitsPerPixel: 8
[    93.207]     NumberOfBanks: 1
[    93.207]     MemoryModel: 4
[    93.207]     BankSize: 0
[    93.207]     NumberOfImages: 12
[    93.207]     RedMaskSize: 0
[    93.207]     RedFieldPosition: 0
[    93.207]     GreenMaskSize: 0
[    93.207]     GreenFieldPosition: 0
[    93.207]     BlueMaskSize: 0
[    93.207]     BlueFieldPosition: 0
[    93.207]     RsvdMaskSize: 0
[    93.207]     RsvdFieldPosition: 0
[    93.207]     DirectColorModeInfo: 0
[    93.207]     PhysBasePtr: 0xd0000000
[    93.207]     LinBytesPerScanLine: 1280
[    93.207]     BnkNumberOfImagePages: 12
[    93.207]     LinNumberOfImagePages: 12
[    93.207]     LinRedMaskSize: 0
[    93.207]     LinRedFieldPosition: 0
[    93.207]     LinGreenMaskSize: 0
[    93.207]     LinGreenFieldPosition: 0
[    93.207]     LinBlueMaskSize: 0
[    93.207]     LinBlueFieldPosition: 0
[    93.207]     LinRsvdMaskSize: 0
[    93.207]     LinRsvdFieldPosition: 0
[    93.207]     MaxPixelClock: 400000000
[    93.207] Mode: 165 (1280x960)
[    93.207]     ModeAttributes: 0xbb
[    93.207]     WinAAttributes: 0x7
[    93.207]     WinBAttributes: 0x0
[    93.207]     WinGranularity: 64
[    93.207]     WinSize: 64
[    93.207]     WinASegment: 0xa000
[    93.207]     WinBSegment: 0x0
[    93.207]     WinFuncPtr: 0xc00050ef
[    93.207]     BytesPerScanline: 2560
[    93.207]     XResolution: 1280
[    93.207]     YResolution: 960
[    93.207]     XCharSize: 8
[    93.207]     YCharSize: 16
[    93.207]     NumberOfPlanes: 1
[    93.207]     BitsPerPixel: 16
[    93.207]     NumberOfBanks: 1
[    93.207]     MemoryModel: 6
[    93.207]     BankSize: 0
[    93.207]     NumberOfImages: 5
[    93.207]     RedMaskSize: 5
[    93.207]     RedFieldPosition: 11
[    93.207]     GreenMaskSize: 6
[    93.207]     GreenFieldPosition: 5
[    93.207]     BlueMaskSize: 5
[    93.207]     BlueFieldPosition: 0
[    93.207]     RsvdMaskSize: 0
[    93.207]     RsvdFieldPosition: 0
[    93.207]     DirectColorModeInfo: 0
[    93.207]     PhysBasePtr: 0xd0000000
[    93.207]     LinBytesPerScanLine: 2560
[    93.207]     BnkNumberOfImagePages: 5
[    93.207]     LinNumberOfImagePages: 5
[    93.207]     LinRedMaskSize: 5
[    93.207]     LinRedFieldPosition: 11
[    93.207]     LinGreenMaskSize: 6
[    93.207]     LinGreenFieldPosition: 5
[    93.207]     LinBlueMaskSize: 5
[    93.207]     LinBlueFieldPosition: 0
[    93.207]     LinRsvdMaskSize: 0
[    93.207]     LinRsvdFieldPosition: 0
[    93.207]     MaxPixelClock: 400000000
[    93.208] *Mode: 166 (1280x960)
[    93.208]     ModeAttributes: 0xbb
[    93.208]     WinAAttributes: 0x7
[    93.208]     WinBAttributes: 0x0
[    93.208]     WinGranularity: 64
[    93.208]     WinSize: 64
[    93.208]     WinASegment: 0xa000
[    93.208]     WinBSegment: 0x0
[    93.208]     WinFuncPtr: 0xc00050ef
[    93.208]     BytesPerScanline: 5120
[    93.208]     XResolution: 1280
[    93.208]     YResolution: 960
[    93.208]     XCharSize: 8
[    93.208]     YCharSize: 16
[    93.208]     NumberOfPlanes: 1
[    93.208]     BitsPerPixel: 32
[    93.208]     NumberOfBanks: 1
[    93.208]     MemoryModel: 6
[    93.208]     BankSize: 0
[    93.208]     NumberOfImages: 2
[    93.208]     RedMaskSize: 8
[    93.208]     RedFieldPosition: 16
[    93.208]     GreenMaskSize: 8
[    93.208]     GreenFieldPosition: 8
[    93.208]     BlueMaskSize: 8
[    93.208]     BlueFieldPosition: 0
[    93.208]     RsvdMaskSize: 0
[    93.208]     RsvdFieldPosition: 0
[    93.208]     DirectColorModeInfo: 0
[    93.208]     PhysBasePtr: 0xd0000000
[    93.208]     LinBytesPerScanLine: 5120
[    93.208]     BnkNumberOfImagePages: 2
[    93.208]     LinNumberOfImagePages: 2
[    93.208]     LinRedMaskSize: 8
[    93.208]     LinRedFieldPosition: 16
[    93.208]     LinGreenMaskSize: 8
[    93.208]     LinGreenFieldPosition: 8
[    93.208]     LinBlueMaskSize: 8
[    93.208]     LinBlueFieldPosition: 0
[    93.208]     LinRsvdMaskSize: 0
[    93.208]     LinRsvdFieldPosition: 0
[    93.208]     MaxPixelClock: 400000000
[    93.208] *Mode: 121 (640x480)
[    93.208]     ModeAttributes: 0xbb
[    93.208]     WinAAttributes: 0x7
[    93.208]     WinBAttributes: 0x0
[    93.208]     WinGranularity: 64
[    93.208]     WinSize: 64
[    93.208]     WinASegment: 0xa000
[    93.208]     WinBSegment: 0x0
[    93.208]     WinFuncPtr: 0xc00050ef
[    93.208]     BytesPerScanline: 2560
[    93.208]     XResolution: 640
[    93.208]     YResolution: 480
[    93.208]     XCharSize: 8
[    93.208]     YCharSize: 16
[    93.208]     NumberOfPlanes: 1
[    93.208]     BitsPerPixel: 32
[    93.208]     NumberOfBanks: 1
[    93.208]     MemoryModel: 6
[    93.208]     BankSize: 0
[    93.208]     NumberOfImages: 12
[    93.208]     RedMaskSize: 8
[    93.208]     RedFieldPosition: 16
[    93.208]     GreenMaskSize: 8
[    93.208]     GreenFieldPosition: 8
[    93.208]     BlueMaskSize: 8
[    93.208]     BlueFieldPosition: 0
[    93.208]     RsvdMaskSize: 0
[    93.208]     RsvdFieldPosition: 0
[    93.208]     DirectColorModeInfo: 0
[    93.208]     PhysBasePtr: 0xd0000000
[    93.208]     LinBytesPerScanLine: 2560
[    93.208]     BnkNumberOfImagePages: 12
[    93.208]     LinNumberOfImagePages: 12
[    93.208]     LinRedMaskSize: 8
[    93.208]     LinRedFieldPosition: 16
[    93.208]     LinGreenMaskSize: 8
[    93.208]     LinGreenFieldPosition: 8
[    93.208]     LinBlueMaskSize: 8
[    93.208]     LinBlueFieldPosition: 0
[    93.208]     LinRsvdMaskSize: 0
[    93.208]     LinRsvdFieldPosition: 0
[    93.208]     MaxPixelClock: 400000000
[    93.208] *Mode: 122 (800x600)
[    93.208]     ModeAttributes: 0xbb
[    93.208]     WinAAttributes: 0x7
[    93.208]     WinBAttributes: 0x0
[    93.208]     WinGranularity: 64
[    93.208]     WinSize: 64
[    93.208]     WinASegment: 0xa000
[    93.208]     WinBSegment: 0x0
[    93.208]     WinFuncPtr: 0xc00050ef
[    93.208]     BytesPerScanline: 3200
[    93.208]     XResolution: 800
[    93.208]     YResolution: 600
[    93.208]     XCharSize: 8
[    93.208]     YCharSize: 14
[    93.208]     NumberOfPlanes: 1
[    93.208]     BitsPerPixel: 32
[    93.208]     NumberOfBanks: 1
[    93.208]     MemoryModel: 6
[    93.208]     BankSize: 0
[    93.208]     NumberOfImages: 7
[    93.208]     RedMaskSize: 8
[    93.208]     RedFieldPosition: 16
[    93.208]     GreenMaskSize: 8
[    93.208]     GreenFieldPosition: 8
[    93.208]     BlueMaskSize: 8
[    93.208]     BlueFieldPosition: 0
[    93.208]     RsvdMaskSize: 0
[    93.208]     RsvdFieldPosition: 0
[    93.208]     DirectColorModeInfo: 0
[    93.208]     PhysBasePtr: 0xd0000000
[    93.208]     LinBytesPerScanLine: 3200
[    93.208]     BnkNumberOfImagePages: 7
[    93.208]     LinNumberOfImagePages: 7
[    93.208]     LinRedMaskSize: 8
[    93.208]     LinRedFieldPosition: 16
[    93.208]     LinGreenMaskSize: 8
[    93.208]     LinGreenFieldPosition: 8
[    93.208]     LinBlueMaskSize: 8
[    93.208]     LinBlueFieldPosition: 0
[    93.208]     LinRsvdMaskSize: 0
[    93.208]     LinRsvdFieldPosition: 0
[    93.208]     MaxPixelClock: 400000000
[    93.209] *Mode: 123 (1024x768)
[    93.209]     ModeAttributes: 0xbb
[    93.209]     WinAAttributes: 0x7
[    93.209]     WinBAttributes: 0x0
[    93.209]     WinGranularity: 64
[    93.209]     WinSize: 64
[    93.209]     WinASegment: 0xa000
[    93.209]     WinBSegment: 0x0
[    93.209]     WinFuncPtr: 0xc00050ef
[    93.209]     BytesPerScanline: 4096
[    93.209]     XResolution: 1024
[    93.209]     YResolution: 768
[    93.209]     XCharSize: 8
[    93.209]     YCharSize: 16
[    93.209]     NumberOfPlanes: 1
[    93.209]     BitsPerPixel: 32
[    93.209]     NumberOfBanks: 1
[    93.209]     MemoryModel: 6
[    93.209]     BankSize: 0
[    93.209]     NumberOfImages: 4
[    93.209]     RedMaskSize: 8
[    93.209]     RedFieldPosition: 16
[    93.209]     GreenMaskSize: 8
[    93.209]     GreenFieldPosition: 8
[    93.209]     BlueMaskSize: 8
[    93.209]     BlueFieldPosition: 0
[    93.209]     RsvdMaskSize: 0
[    93.209]     RsvdFieldPosition: 0
[    93.209]     DirectColorModeInfo: 0
[    93.209]     PhysBasePtr: 0xd0000000
[    93.209]     LinBytesPerScanLine: 4096
[    93.209]     BnkNumberOfImagePages: 4
[    93.209]     LinNumberOfImagePages: 4
[    93.209]     LinRedMaskSize: 8
[    93.209]     LinRedFieldPosition: 16
[    93.209]     LinGreenMaskSize: 8
[    93.209]     LinGreenFieldPosition: 8
[    93.209]     LinBlueMaskSize: 8
[    93.209]     LinBlueFieldPosition: 0
[    93.209]     LinRsvdMaskSize: 0
[    93.209]     LinRsvdFieldPosition: 0
[    93.209]     MaxPixelClock: 400000000
[    93.209] *Mode: 124 (1280x1024)
[    93.209]     ModeAttributes: 0xbb
[    93.209]     WinAAttributes: 0x7
[    93.209]     WinBAttributes: 0x0
[    93.209]     WinGranularity: 64
[    93.209]     WinSize: 64
[    93.209]     WinASegment: 0xa000
[    93.209]     WinBSegment: 0x0
[    93.209]     WinFuncPtr: 0xc00050ef
[    93.209]     BytesPerScanline: 5120
[    93.209]     XResolution: 1280
[    93.209]     YResolution: 1024
[    93.209]     XCharSize: 8
[    93.209]     YCharSize: 16
[    93.209]     NumberOfPlanes: 1
[    93.209]     BitsPerPixel: 32
[    93.209]     NumberOfBanks: 1
[    93.209]     MemoryModel: 6
[    93.209]     BankSize: 0
[    93.209]     NumberOfImages: 2
[    93.209]     RedMaskSize: 8
[    93.209]     RedFieldPosition: 16
[    93.209]     GreenMaskSize: 8
[    93.209]     GreenFieldPosition: 8
[    93.209]     BlueMaskSize: 8
[    93.209]     BlueFieldPosition: 0
[    93.209]     RsvdMaskSize: 0
[    93.209]     RsvdFieldPosition: 0
[    93.209]     DirectColorModeInfo: 0
[    93.209]     PhysBasePtr: 0xd0000000
[    93.209]     LinBytesPerScanLine: 5120
[    93.209]     BnkNumberOfImagePages: 2
[    93.209]     LinNumberOfImagePages: 2
[    93.209]     LinRedMaskSize: 8
[    93.209]     LinRedFieldPosition: 16
[    93.209]     LinGreenMaskSize: 8
[    93.209]     LinGreenFieldPosition: 8
[    93.209]     LinBlueMaskSize: 8
[    93.209]     LinBlueFieldPosition: 0
[    93.209]     LinRsvdMaskSize: 0
[    93.209]     LinRsvdFieldPosition: 0
[    93.209]     MaxPixelClock: 400000000
[    93.209] Mode: 143 (1400x1050)
[    93.209]     ModeAttributes: 0xbb
[    93.209]     WinAAttributes: 0x7
[    93.209]     WinBAttributes: 0x0
[    93.209]     WinGranularity: 64
[    93.209]     WinSize: 64
[    93.209]     WinASegment: 0xa000
[    93.209]     WinBSegment: 0x0
[    93.209]     WinFuncPtr: 0xc00050ef
[    93.209]     BytesPerScanline: 1408
[    93.209]     XResolution: 1400
[    93.209]     YResolution: 1050
[    93.209]     XCharSize: 8
[    93.209]     YCharSize: 16
[    93.209]     NumberOfPlanes: 1
[    93.209]     BitsPerPixel: 8
[    93.209]     NumberOfBanks: 1
[    93.209]     MemoryModel: 4
[    93.209]     BankSize: 0
[    93.209]     NumberOfImages: 10
[    93.209]     RedMaskSize: 0
[    93.209]     RedFieldPosition: 0
[    93.209]     GreenMaskSize: 0
[    93.209]     GreenFieldPosition: 0
[    93.209]     BlueMaskSize: 0
[    93.209]     BlueFieldPosition: 0
[    93.209]     RsvdMaskSize: 0
[    93.209]     RsvdFieldPosition: 0
[    93.209]     DirectColorModeInfo: 0
[    93.209]     PhysBasePtr: 0xd0000000
[    93.209]     LinBytesPerScanLine: 1408
[    93.209]     BnkNumberOfImagePages: 10
[    93.209]     LinNumberOfImagePages: 10
[    93.209]     LinRedMaskSize: 0
[    93.209]     LinRedFieldPosition: 0
[    93.209]     LinGreenMaskSize: 0
[    93.209]     LinGreenFieldPosition: 0
[    93.209]     LinBlueMaskSize: 0
[    93.209]     LinBlueFieldPosition: 0
[    93.210]     LinRsvdMaskSize: 0
[    93.210]     LinRsvdFieldPosition: 0
[    93.210]     MaxPixelClock: 400000000
[    93.210] Mode: 145 (1400x1050)
[    93.210]     ModeAttributes: 0xbb
[    93.210]     WinAAttributes: 0x7
[    93.210]     WinBAttributes: 0x0
[    93.210]     WinGranularity: 64
[    93.210]     WinSize: 64
[    93.210]     WinASegment: 0xa000
[    93.210]     WinBSegment: 0x0
[    93.210]     WinFuncPtr: 0xc00050ef
[    93.210]     BytesPerScanline: 2816
[    93.210]     XResolution: 1400
[    93.210]     YResolution: 1050
[    93.210]     XCharSize: 8
[    93.210]     YCharSize: 16
[    93.210]     NumberOfPlanes: 1
[    93.210]     BitsPerPixel: 16
[    93.210]     NumberOfBanks: 1
[    93.210]     MemoryModel: 6
[    93.210]     BankSize: 0
[    93.210]     NumberOfImages: 4
[    93.210]     RedMaskSize: 5
[    93.210]     RedFieldPosition: 11
[    93.210]     GreenMaskSize: 6
[    93.210]     GreenFieldPosition: 5
[    93.210]     BlueMaskSize: 5
[    93.210]     BlueFieldPosition: 0
[    93.210]     RsvdMaskSize: 0
[    93.210]     RsvdFieldPosition: 0
[    93.210]     DirectColorModeInfo: 0
[    93.210]     PhysBasePtr: 0xd0000000
[    93.210]     LinBytesPerScanLine: 2816
[    93.210]     BnkNumberOfImagePages: 4
[    93.210]     LinNumberOfImagePages: 4
[    93.210]     LinRedMaskSize: 5
[    93.210]     LinRedFieldPosition: 11
[    93.210]     LinGreenMaskSize: 6
[    93.210]     LinGreenFieldPosition: 5
[    93.210]     LinBlueMaskSize: 5
[    93.210]     LinBlueFieldPosition: 0
[    93.210]     LinRsvdMaskSize: 0
[    93.210]     LinRsvdFieldPosition: 0
[    93.210]     MaxPixelClock: 400000000
[    93.210] *Mode: 146 (1400x1050)
[    93.210]     ModeAttributes: 0xbb
[    93.210]     WinAAttributes: 0x7
[    93.210]     WinBAttributes: 0x0
[    93.210]     WinGranularity: 64
[    93.210]     WinSize: 64
[    93.210]     WinASegment: 0xa000
[    93.210]     WinBSegment: 0x0
[    93.210]     WinFuncPtr: 0xc00050ef
[    93.210]     BytesPerScanline: 5632
[    93.210]     XResolution: 1400
[    93.210]     YResolution: 1050
[    93.210]     XCharSize: 8
[    93.210]     YCharSize: 16
[    93.210]     NumberOfPlanes: 1
[    93.210]     BitsPerPixel: 32
[    93.210]     NumberOfBanks: 1
[    93.210]     MemoryModel: 6
[    93.210]     BankSize: 0
[    93.210]     NumberOfImages: 1
[    93.210]     RedMaskSize: 8
[    93.210]     RedFieldPosition: 16
[    93.210]     GreenMaskSize: 8
[    93.210]     GreenFieldPosition: 8
[    93.210]     BlueMaskSize: 8
[    93.210]     BlueFieldPosition: 0
[    93.210]     RsvdMaskSize: 0
[    93.210]     RsvdFieldPosition: 0
[    93.210]     DirectColorModeInfo: 0
[    93.210]     PhysBasePtr: 0xd0000000
[    93.210]     LinBytesPerScanLine: 5632
[    93.210]     BnkNumberOfImagePages: 1
[    93.210]     LinNumberOfImagePages: 1
[    93.210]     LinRedMaskSize: 8
[    93.210]     LinRedFieldPosition: 16
[    93.210]     LinGreenMaskSize: 8
[    93.210]     LinGreenFieldPosition: 8
[    93.210]     LinBlueMaskSize: 8
[    93.210]     LinBlueFieldPosition: 0
[    93.210]     LinRsvdMaskSize: 0
[    93.210]     LinRsvdFieldPosition: 0
[    93.210]     MaxPixelClock: 400000000
[    93.211] Mode: 173 (1600x1200)
[    93.211]     ModeAttributes: 0xbb
[    93.211]     WinAAttributes: 0x7
[    93.211]     WinBAttributes: 0x0
[    93.211]     WinGranularity: 64
[    93.211]     WinSize: 64
[    93.211]     WinASegment: 0xa000
[    93.211]     WinBSegment: 0x0
[    93.211]     WinFuncPtr: 0xc00050ef
[    93.211]     BytesPerScanline: 1600
[    93.211]     XResolution: 1600
[    93.211]     YResolution: 1200
[    93.211]     XCharSize: 8
[    93.211]     YCharSize: 16
[    93.211]     NumberOfPlanes: 1
[    93.211]     BitsPerPixel: 8
[    93.211]     NumberOfBanks: 1
[    93.211]     MemoryModel: 4
[    93.211]     BankSize: 0
[    93.211]     NumberOfImages: 7
[    93.211]     RedMaskSize: 0
[    93.211]     RedFieldPosition: 0
[    93.211]     GreenMaskSize: 0
[    93.211]     GreenFieldPosition: 0
[    93.211]     BlueMaskSize: 0
[    93.211]     BlueFieldPosition: 0
[    93.211]     RsvdMaskSize: 0
[    93.211]     RsvdFieldPosition: 0
[    93.211]     DirectColorModeInfo: 0
[    93.211]     PhysBasePtr: 0xd0000000
[    93.211]     LinBytesPerScanLine: 1600
[    93.211]     BnkNumberOfImagePages: 7
[    93.211]     LinNumberOfImagePages: 7
[    93.211]     LinRedMaskSize: 0
[    93.211]     LinRedFieldPosition: 0
[    93.211]     LinGreenMaskSize: 0
[    93.211]     LinGreenFieldPosition: 0
[    93.211]     LinBlueMaskSize: 0
[    93.211]     LinBlueFieldPosition: 0
[    93.211]     LinRsvdMaskSize: 0
[    93.211]     LinRsvdFieldPosition: 0
[    93.211]     MaxPixelClock: 400000000
[    93.211] Mode: 175 (1600x1200)
[    93.211]     ModeAttributes: 0xbb
[    93.211]     WinAAttributes: 0x7
[    93.211]     WinBAttributes: 0x0
[    93.211]     WinGranularity: 64
[    93.211]     WinSize: 64
[    93.211]     WinASegment: 0xa000
[    93.211]     WinBSegment: 0x0
[    93.211]     WinFuncPtr: 0xc00050ef
[    93.211]     BytesPerScanline: 3200
[    93.211]     XResolution: 1600
[    93.211]     YResolution: 1200
[    93.211]     XCharSize: 8
[    93.211]     YCharSize: 16
[    93.211]     NumberOfPlanes: 1
[    93.211]     BitsPerPixel: 16
[    93.211]     NumberOfBanks: 1
[    93.211]     MemoryModel: 6
[    93.211]     BankSize: 0
[    93.211]     NumberOfImages: 3
[    93.211]     RedMaskSize: 5
[    93.211]     RedFieldPosition: 11
[    93.211]     GreenMaskSize: 6
[    93.211]     GreenFieldPosition: 5
[    93.211]     BlueMaskSize: 5
[    93.211]     BlueFieldPosition: 0
[    93.211]     RsvdMaskSize: 0
[    93.211]     RsvdFieldPosition: 0
[    93.211]     DirectColorModeInfo: 0
[    93.211]     PhysBasePtr: 0xd0000000
[    93.211]     LinBytesPerScanLine: 3200
[    93.211]     BnkNumberOfImagePages: 3
[    93.211]     LinNumberOfImagePages: 3
[    93.211]     LinRedMaskSize: 5
[    93.211]     LinRedFieldPosition: 11
[    93.211]     LinGreenMaskSize: 6
[    93.211]     LinGreenFieldPosition: 5
[    93.211]     LinBlueMaskSize: 5
[    93.211]     LinBlueFieldPosition: 0
[    93.211]     LinRsvdMaskSize: 0
[    93.211]     LinRsvdFieldPosition: 0
[    93.211]     MaxPixelClock: 400000000
[    93.211] *Mode: 176 (1600x1200)
[    93.211]     ModeAttributes: 0xbb
[    93.211]     WinAAttributes: 0x7
[    93.211]     WinBAttributes: 0x0
[    93.211]     WinGranularity: 64
[    93.211]     WinSize: 64
[    93.211]     WinASegment: 0xa000
[    93.211]     WinBSegment: 0x0
[    93.211]     WinFuncPtr: 0xc00050ef
[    93.211]     BytesPerScanline: 6400
[    93.211]     XResolution: 1600
[    93.211]     YResolution: 1200
[    93.211]     XCharSize: 8
[    93.211]     YCharSize: 16
[    93.211]     NumberOfPlanes: 1
[    93.211]     BitsPerPixel: 32
[    93.211]     NumberOfBanks: 1
[    93.211]     MemoryModel: 6
[    93.211]     BankSize: 0
[    93.211]     NumberOfImages: 1
[    93.211]     RedMaskSize: 8
[    93.211]     RedFieldPosition: 16
[    93.211]     GreenMaskSize: 8
[    93.211]     GreenFieldPosition: 8
[    93.211]     BlueMaskSize: 8
[    93.211]     BlueFieldPosition: 0
[    93.211]     RsvdMaskSize: 0
[    93.211]     RsvdFieldPosition: 0
[    93.211]     DirectColorModeInfo: 0
[    93.211]     PhysBasePtr: 0xd0000000
[    93.211]     LinBytesPerScanLine: 6400
[    93.211]     BnkNumberOfImagePages: 1
[    93.211]     LinNumberOfImagePages: 1
[    93.211]     LinRedMaskSize: 8
[    93.211]     LinRedFieldPosition: 16
[    93.211]     LinGreenMaskSize: 8
[    93.211]     LinGreenFieldPosition: 8
[    93.211]     LinBlueMaskSize: 8
[    93.211]     LinBlueFieldPosition: 0
[    93.211]     LinRsvdMaskSize: 0
[    93.211]     LinRsvdFieldPosition: 0
[    93.211]     MaxPixelClock: 400000000
[    93.212] Mode: 183 (1792x1344)
[    93.212]     ModeAttributes: 0xbb
[    93.212]     WinAAttributes: 0x7
[    93.212]     WinBAttributes: 0x0
[    93.212]     WinGranularity: 64
[    93.212]     WinSize: 64
[    93.212]     WinASegment: 0xa000
[    93.212]     WinBSegment: 0x0
[    93.212]     WinFuncPtr: 0xc00050ef
[    93.212]     BytesPerScanline: 1792
[    93.212]     XResolution: 1792
[    93.212]     YResolution: 1344
[    93.212]     XCharSize: 8
[    93.212]     YCharSize: 16
[    93.212]     NumberOfPlanes: 1
[    93.212]     BitsPerPixel: 8
[    93.212]     NumberOfBanks: 1
[    93.212]     MemoryModel: 4
[    93.212]     BankSize: 0
[    93.212]     NumberOfImages: 5
[    93.212]     RedMaskSize: 0
[    93.212]     RedFieldPosition: 0
[    93.212]     GreenMaskSize: 0
[    93.212]     GreenFieldPosition: 0
[    93.212]     BlueMaskSize: 0
[    93.212]     BlueFieldPosition: 0
[    93.212]     RsvdMaskSize: 0
[    93.212]     RsvdFieldPosition: 0
[    93.212]     DirectColorModeInfo: 0
[    93.212]     PhysBasePtr: 0xd0000000
[    93.212]     LinBytesPerScanLine: 1792
[    93.212]     BnkNumberOfImagePages: 5
[    93.212]     LinNumberOfImagePages: 5
[    93.212]     LinRedMaskSize: 0
[    93.212]     LinRedFieldPosition: 0
[    93.212]     LinGreenMaskSize: 0
[    93.212]     LinGreenFieldPosition: 0
[    93.212]     LinBlueMaskSize: 0
[    93.212]     LinBlueFieldPosition: 0
[    93.212]     LinRsvdMaskSize: 0
[    93.212]     LinRsvdFieldPosition: 0
[    93.212]     MaxPixelClock: 400000000
[    93.212] Mode: 185 (1792x1344)
[    93.212]     ModeAttributes: 0xbb
[    93.212]     WinAAttributes: 0x7
[    93.212]     WinBAttributes: 0x0
[    93.212]     WinGranularity: 64
[    93.212]     WinSize: 64
[    93.212]     WinASegment: 0xa000
[    93.212]     WinBSegment: 0x0
[    93.212]     WinFuncPtr: 0xc00050ef
[    93.212]     BytesPerScanline: 3584
[    93.212]     XResolution: 1792
[    93.212]     YResolution: 1344
[    93.212]     XCharSize: 8
[    93.212]     YCharSize: 16
[    93.212]     NumberOfPlanes: 1
[    93.212]     BitsPerPixel: 16
[    93.212]     NumberOfBanks: 1
[    93.212]     MemoryModel: 6
[    93.212]     BankSize: 0
[    93.212]     NumberOfImages: 2
[    93.212]     RedMaskSize: 5
[    93.212]     RedFieldPosition: 11
[    93.212]     GreenMaskSize: 6
[    93.212]     GreenFieldPosition: 5
[    93.212]     BlueMaskSize: 5
[    93.212]     BlueFieldPosition: 0
[    93.212]     RsvdMaskSize: 0
[    93.212]     RsvdFieldPosition: 0
[    93.212]     DirectColorModeInfo: 0
[    93.212]     PhysBasePtr: 0xd0000000
[    93.212]     LinBytesPerScanLine: 3584
[    93.212]     BnkNumberOfImagePages: 2
[    93.212]     LinNumberOfImagePages: 2
[    93.212]     LinRedMaskSize: 5
[    93.212]     LinRedFieldPosition: 11
[    93.212]     LinGreenMaskSize: 6
[    93.212]     LinGreenFieldPosition: 5
[    93.212]     LinBlueMaskSize: 5
[    93.212]     LinBlueFieldPosition: 0
[    93.212]     LinRsvdMaskSize: 0
[    93.212]     LinRsvdFieldPosition: 0
[    93.212]     MaxPixelClock: 400000000
[    93.212] *Mode: 186 (1792x1344)
[    93.212]     ModeAttributes: 0xbb
[    93.212]     WinAAttributes: 0x7
[    93.212]     WinBAttributes: 0x0
[    93.212]     WinGranularity: 64
[    93.212]     WinSize: 64
[    93.212]     WinASegment: 0xa000
[    93.212]     WinBSegment: 0x0
[    93.212]     WinFuncPtr: 0xc00050ef
[    93.212]     BytesPerScanline: 7168
[    93.212]     XResolution: 1792
[    93.212]     YResolution: 1344
[    93.212]     XCharSize: 8
[    93.212]     YCharSize: 16
[    93.212]     NumberOfPlanes: 1
[    93.212]     BitsPerPixel: 32
[    93.212]     NumberOfBanks: 1
[    93.212]     MemoryModel: 6
[    93.212]     BankSize: 0
[    93.212]     NumberOfImages: 1
[    93.212]     RedMaskSize: 8
[    93.212]     RedFieldPosition: 16
[    93.212]     GreenMaskSize: 8
[    93.212]     GreenFieldPosition: 8
[    93.212]     BlueMaskSize: 8
[    93.212]     BlueFieldPosition: 0
[    93.212]     RsvdMaskSize: 0
[    93.212]     RsvdFieldPosition: 0
[    93.212]     DirectColorModeInfo: 0
[    93.212]     PhysBasePtr: 0xd0000000
[    93.212]     LinBytesPerScanLine: 7168
[    93.212]     BnkNumberOfImagePages: 1
[    93.212]     LinNumberOfImagePages: 1
[    93.212]     LinRedMaskSize: 8
[    93.212]     LinRedFieldPosition: 16
[    93.212]     LinGreenMaskSize: 8
[    93.212]     LinGreenFieldPosition: 8
[    93.212]     LinBlueMaskSize: 8
[    93.212]     LinBlueFieldPosition: 0
[    93.212]     LinRsvdMaskSize: 0
[    93.212]     LinRsvdFieldPosition: 0
[    93.212]     MaxPixelClock: 400000000
[    93.213] Mode: 1d3 (1856x1392)
[    93.213]     ModeAttributes: 0xbb
[    93.213]     WinAAttributes: 0x7
[    93.213]     WinBAttributes: 0x0
[    93.213]     WinGranularity: 64
[    93.213]     WinSize: 64
[    93.213]     WinASegment: 0xa000
[    93.213]     WinBSegment: 0x0
[    93.213]     WinFuncPtr: 0xc00050ef
[    93.213]     BytesPerScanline: 1856
[    93.213]     XResolution: 1856
[    93.213]     YResolution: 1392
[    93.213]     XCharSize: 8
[    93.213]     YCharSize: 16
[    93.213]     NumberOfPlanes: 1
[    93.213]     BitsPerPixel: 8
[    93.213]     NumberOfBanks: 1
[    93.213]     MemoryModel: 4
[    93.213]     BankSize: 0
[    93.213]     NumberOfImages: 5
[    93.213]     RedMaskSize: 0
[    93.213]     RedFieldPosition: 0
[    93.213]     GreenMaskSize: 0
[    93.213]     GreenFieldPosition: 0
[    93.213]     BlueMaskSize: 0
[    93.213]     BlueFieldPosition: 0
[    93.213]     RsvdMaskSize: 0
[    93.213]     RsvdFieldPosition: 0
[    93.213]     DirectColorModeInfo: 0
[    93.213]     PhysBasePtr: 0xd0000000
[    93.213]     LinBytesPerScanLine: 1856
[    93.213]     BnkNumberOfImagePages: 5
[    93.213]     LinNumberOfImagePages: 5
[    93.213]     LinRedMaskSize: 0
[    93.213]     LinRedFieldPosition: 0
[    93.213]     LinGreenMaskSize: 0
[    93.213]     LinGreenFieldPosition: 0
[    93.213]     LinBlueMaskSize: 0
[    93.213]     LinBlueFieldPosition: 0
[    93.213]     LinRsvdMaskSize: 0
[    93.213]     LinRsvdFieldPosition: 0
[    93.213]     MaxPixelClock: 400000000
[    93.213] Mode: 1d5 (1856x1392)
[    93.213]     ModeAttributes: 0xbb
[    93.213]     WinAAttributes: 0x7
[    93.213]     WinBAttributes: 0x0
[    93.213]     WinGranularity: 64
[    93.213]     WinSize: 64
[    93.213]     WinASegment: 0xa000
[    93.213]     WinBSegment: 0x0
[    93.213]     WinFuncPtr: 0xc00050ef
[    93.213]     BytesPerScanline: 3712
[    93.213]     XResolution: 1856
[    93.213]     YResolution: 1392
[    93.213]     XCharSize: 8
[    93.213]     YCharSize: 16
[    93.213]     NumberOfPlanes: 1
[    93.213]     BitsPerPixel: 16
[    93.213]     NumberOfBanks: 1
[    93.213]     MemoryModel: 6
[    93.213]     BankSize: 0
[    93.213]     NumberOfImages: 2
[    93.213]     RedMaskSize: 5
[    93.213]     RedFieldPosition: 11
[    93.213]     GreenMaskSize: 6
[    93.213]     GreenFieldPosition: 5
[    93.213]     BlueMaskSize: 5
[    93.213]     BlueFieldPosition: 0
[    93.213]     RsvdMaskSize: 0
[    93.213]     RsvdFieldPosition: 0
[    93.213]     DirectColorModeInfo: 0
[    93.213]     PhysBasePtr: 0xd0000000
[    93.213]     LinBytesPerScanLine: 3712
[    93.213]     BnkNumberOfImagePages: 2
[    93.213]     LinNumberOfImagePages: 2
[    93.213]     LinRedMaskSize: 5
[    93.213]     LinRedFieldPosition: 11
[    93.213]     LinGreenMaskSize: 6
[    93.213]     LinGreenFieldPosition: 5
[    93.213]     LinBlueMaskSize: 5
[    93.213]     LinBlueFieldPosition: 0
[    93.213]     LinRsvdMaskSize: 0
[    93.213]     LinRsvdFieldPosition: 0
[    93.213]     MaxPixelClock: 400000000
[    93.213] *Mode: 1d6 (1856x1392)
[    93.213]     ModeAttributes: 0xbb
[    93.213]     WinAAttributes: 0x7
[    93.213]     WinBAttributes: 0x0
[    93.213]     WinGranularity: 64
[    93.213]     WinSize: 64
[    93.213]     WinASegment: 0xa000
[    93.213]     WinBSegment: 0x0
[    93.213]     WinFuncPtr: 0xc00050ef
[    93.213]     BytesPerScanline: 7424
[    93.213]     XResolution: 1856
[    93.213]     YResolution: 1392
[    93.213]     XCharSize: 8
[    93.213]     YCharSize: 16
[    93.213]     NumberOfPlanes: 1
[    93.213]     BitsPerPixel: 32
[    93.213]     NumberOfBanks: 1
[    93.213]     MemoryModel: 6
[    93.213]     BankSize: 0
[    93.213]     NumberOfImages: 1
[    93.213]     RedMaskSize: 8
[    93.213]     RedFieldPosition: 16
[    93.213]     GreenMaskSize: 8
[    93.213]     GreenFieldPosition: 8
[    93.213]     BlueMaskSize: 8
[    93.213]     BlueFieldPosition: 0
[    93.213]     RsvdMaskSize: 0
[    93.213]     RsvdFieldPosition: 0
[    93.213]     DirectColorModeInfo: 0
[    93.213]     PhysBasePtr: 0xd0000000
[    93.213]     LinBytesPerScanLine: 7424
[    93.213]     BnkNumberOfImagePages: 1
[    93.213]     LinNumberOfImagePages: 1
[    93.213]     LinRedMaskSize: 8
[    93.213]     LinRedFieldPosition: 16
[    93.213]     LinGreenMaskSize: 8
[    93.213]     LinGreenFieldPosition: 8
[    93.213]     LinBlueMaskSize: 8
[    93.213]     LinBlueFieldPosition: 0
[    93.213]     LinRsvdMaskSize: 0
[    93.213]     LinRsvdFieldPosition: 0
[    93.213]     MaxPixelClock: 400000000
[    93.214] Mode: 1e3 (1920x1440)
[    93.214]     ModeAttributes: 0xbb
[    93.214]     WinAAttributes: 0x7
[    93.214]     WinBAttributes: 0x0
[    93.214]     WinGranularity: 64
[    93.214]     WinSize: 64
[    93.214]     WinASegment: 0xa000
[    93.214]     WinBSegment: 0x0
[    93.214]     WinFuncPtr: 0xc00050ef
[    93.214]     BytesPerScanline: 1920
[    93.214]     XResolution: 1920
[    93.214]     YResolution: 1440
[    93.214]     XCharSize: 8
[    93.214]     YCharSize: 16
[    93.214]     NumberOfPlanes: 1
[    93.214]     BitsPerPixel: 8
[    93.214]     NumberOfBanks: 1
[    93.214]     MemoryModel: 4
[    93.214]     BankSize: 0
[    93.214]     NumberOfImages: 4
[    93.214]     RedMaskSize: 0
[    93.214]     RedFieldPosition: 0
[    93.214]     GreenMaskSize: 0
[    93.214]     GreenFieldPosition: 0
[    93.214]     BlueMaskSize: 0
[    93.214]     BlueFieldPosition: 0
[    93.214]     RsvdMaskSize: 0
[    93.214]     RsvdFieldPosition: 0
[    93.214]     DirectColorModeInfo: 0
[    93.214]     PhysBasePtr: 0xd0000000
[    93.214]     LinBytesPerScanLine: 1920
[    93.214]     BnkNumberOfImagePages: 4
[    93.214]     LinNumberOfImagePages: 4
[    93.214]     LinRedMaskSize: 0
[    93.214]     LinRedFieldPosition: 0
[    93.214]     LinGreenMaskSize: 0
[    93.214]     LinGreenFieldPosition: 0
[    93.214]     LinBlueMaskSize: 0
[    93.214]     LinBlueFieldPosition: 0
[    93.214]     LinRsvdMaskSize: 0
[    93.214]     LinRsvdFieldPosition: 0
[    93.214]     MaxPixelClock: 400000000
[    93.214] Mode: 1e5 (1920x1440)
[    93.214]     ModeAttributes: 0xbb
[    93.214]     WinAAttributes: 0x7
[    93.214]     WinBAttributes: 0x0
[    93.214]     WinGranularity: 64
[    93.214]     WinSize: 64
[    93.214]     WinASegment: 0xa000
[    93.214]     WinBSegment: 0x0
[    93.214]     WinFuncPtr: 0xc00050ef
[    93.214]     BytesPerScanline: 3840
[    93.214]     XResolution: 1920
[    93.214]     YResolution: 1440
[    93.214]     XCharSize: 8
[    93.214]     YCharSize: 16
[    93.214]     NumberOfPlanes: 1
[    93.214]     BitsPerPixel: 16
[    93.214]     NumberOfBanks: 1
[    93.214]     MemoryModel: 6
[    93.214]     BankSize: 0
[    93.214]     NumberOfImages: 2
[    93.214]     RedMaskSize: 5
[    93.214]     RedFieldPosition: 11
[    93.214]     GreenMaskSize: 6
[    93.214]     GreenFieldPosition: 5
[    93.214]     BlueMaskSize: 5
[    93.214]     BlueFieldPosition: 0
[    93.214]     RsvdMaskSize: 0
[    93.214]     RsvdFieldPosition: 0
[    93.214]     DirectColorModeInfo: 0
[    93.214]     PhysBasePtr: 0xd0000000
[    93.214]     LinBytesPerScanLine: 3840
[    93.214]     BnkNumberOfImagePages: 2
[    93.214]     LinNumberOfImagePages: 2
[    93.214]     LinRedMaskSize: 5
[    93.214]     LinRedFieldPosition: 11
[    93.214]     LinGreenMaskSize: 6
[    93.214]     LinGreenFieldPosition: 5
[    93.214]     LinBlueMaskSize: 5
[    93.214]     LinBlueFieldPosition: 0
[    93.214]     LinRsvdMaskSize: 0
[    93.214]     LinRsvdFieldPosition: 0
[    93.214]     MaxPixelClock: 400000000
[    93.214] *Mode: 1e6 (1920x1440)
[    93.214]     ModeAttributes: 0xbb
[    93.214]     WinAAttributes: 0x7
[    93.214]     WinBAttributes: 0x0
[    93.214]     WinGranularity: 64
[    93.214]     WinSize: 64
[    93.214]     WinASegment: 0xa000
[    93.214]     WinBSegment: 0x0
[    93.214]     WinFuncPtr: 0xc00050ef
[    93.214]     BytesPerScanline: 7680
[    93.214]     XResolution: 1920
[    93.214]     YResolution: 1440
[    93.214]     XCharSize: 8
[    93.214]     YCharSize: 16
[    93.214]     NumberOfPlanes: 1
[    93.214]     BitsPerPixel: 32
[    93.214]     NumberOfBanks: 1
[    93.214]     MemoryModel: 6
[    93.214]     BankSize: 0
[    93.214]     NumberOfImages: 1
[    93.214]     RedMaskSize: 8
[    93.214]     RedFieldPosition: 16
[    93.214]     GreenMaskSize: 8
[    93.214]     GreenFieldPosition: 8
[    93.214]     BlueMaskSize: 8
[    93.214]     BlueFieldPosition: 0
[    93.214]     RsvdMaskSize: 0
[    93.214]     RsvdFieldPosition: 0
[    93.214]     DirectColorModeInfo: 0
[    93.214]     PhysBasePtr: 0xd0000000
[    93.214]     LinBytesPerScanLine: 7680
[    93.214]     BnkNumberOfImagePages: 1
[    93.214]     LinNumberOfImagePages: 1
[    93.214]     LinRedMaskSize: 8
[    93.214]     LinRedFieldPosition: 16
[    93.214]     LinGreenMaskSize: 8
[    93.214]     LinGreenFieldPosition: 8
[    93.214]     LinBlueMaskSize: 8
[    93.215]     LinBlueFieldPosition: 0
[    93.215]     LinRsvdMaskSize: 0
[    93.215]     LinRsvdFieldPosition: 0
[    93.215]     MaxPixelClock: 400000000
[    93.215] 
[    93.215] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    93.215] (II) VESA(0): Configured Monitor: Using hsync range of 31.00-70.00 kHz
[    93.215] (II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-85.00 Hz
[    93.215] (II) VESA(0): Configured Monitor: Using maximum pixel clock of 145.00 MHz
[    93.215] (WW) VESA(0): Unable to estimate virtual size
[    93.215] (II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "1856x1392" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "1792x1344" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    93.215] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    93.215] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    93.215] (**) VESA(0): *Built-in mode "1280x1024"
[    93.215] (**) VESA(0): *Built-in mode "1280x960"
[    93.215] (**) VESA(0): *Built-in mode "1152x864"
[    93.215] (**) VESA(0): *Built-in mode "1024x768"
[    93.215] (**) VESA(0): *Built-in mode "800x600"
[    93.215] (**) VESA(0): *Built-in mode "640x480"
[    93.215] (**) VESA(0): *Built-in mode "720x400"
[    93.215] (**) VESA(0): Display dimensions: (880, 490) mm
[    93.215] (**) VESA(0): DPI set to (36, 53)
[    93.215] (**) VESA(0): Using "Shadow Framebuffer"
[    93.215] (II) Loading sub module "shadow"
[    93.215] (II) LoadModule: "shadow"
[    93.215] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    93.215] (II) Module shadow: vendor="X.Org Foundation"
[    93.215]     compiled for 1.9.0, module version = 1.1.0
[    93.215]     ABI class: X.Org ANSI C Emulation, version 0.4
[    93.215] (II) Loading sub module "fb"
[    93.215] (II) LoadModule: "fb"
[    93.216] (II) Loading /usr/lib/xorg/modules/libfb.so
[    93.216] (II) Module fb: vendor="X.Org Foundation"
[    93.216]     compiled for 1.9.0, module version = 1.0.0
[    93.216]     ABI class: X.Org ANSI C Emulation, version 0.4
[    93.216] (==) Depth 24 pixmap format is 32 bpp
[    93.216] (II) Loading sub module "int10"
[    93.216] (II) LoadModule: "int10"
[    93.216] (II) Reloading /usr/lib/xorg/modules/libint10.so
[    93.216] (II) VESA(0): initializing int10
[    93.216] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    93.216] (II) VESA(0): VESA BIOS detected
[    93.216] (II) VESA(0): VESA VBE Version 3.0
[    93.216] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    93.216] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    93.216] (II) VESA(0): VESA VBE OEM Software Rev: 11.10
[    93.216] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    93.216] (II) VESA(0): VESA VBE OEM Product: RV770
[    93.216] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    93.218] (II) VESA(0): virtual address = 0x7f9cfaf97000,
    physical address = 0xd0000000, size = 16777216
[    93.230] (II) VESA(0): Setting up VESA Mode 0x124 (1280x1024)
[    93.230] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[    93.337] (==) VESA(0): Default visual is TrueColor
[    93.337] (==) VESA(0): Backing store disabled
[    93.337] (==) VESA(0): DPMS enabled
[    93.337] (==) RandR enabled
[    93.337] (II) Initializing built-in extension Generic Event Extension
[    93.337] (II) Initializing built-in extension SHAPE
[    93.337] (II) Initializing built-in extension MIT-SHM
[    93.337] (II) Initializing built-in extension XInputExtension
[    93.337] (II) Initializing built-in extension XTEST
[    93.337] (II) Initializing built-in extension BIG-REQUESTS
[    93.337] (II) Initializing built-in extension SYNC
[    93.337] (II) Initializing built-in extension XKEYBOARD
[    93.337] (II) Initializing built-in extension XC-MISC
[    93.337] (II) Initializing built-in extension SECURITY
[    93.337] (II) Initializing built-in extension XINERAMA
[    93.337] (II) Initializing built-in extension XFIXES
[    93.337] (II) Initializing built-in extension RENDER
[    93.337] (II) Initializing built-in extension RANDR
[    93.337] (II) Initializing built-in extension COMPOSITE
[    93.337] (II) Initializing built-in extension DAMAGE
[    93.337] (II) Initializing built-in extension GESTURE
[    93.339] (EE) GLX error: Can not get required symbols.
[    93.354] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    93.359] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    93.359] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    93.359] (II) LoadModule: "evdev"
[    93.360] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    93.360] (II) Module evdev: vendor="X.Org Foundation"
[    93.360]     compiled for 1.9.0, module version = 2.3.2
[    93.360]     Module class: X.Org XInput Driver
[    93.360]     ABI class: X.Org XInput driver, version 11.0
[    93.360] (**) Power Button: always reports core events
[    93.360] (**) Power Button: Device: "/dev/input/event1"
[    93.410] (II) Power Button: Found keys
[    93.410] (II) Power Button: Configuring as keyboard
[    93.410] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    93.410] (**) Option "xkb_rules" "evdev"
[    93.410] (**) Option "xkb_model" "pc105"
[    93.410] (**) Option "xkb_layout" "us"
[    93.410] (**) Option "xkb_options" "lv3:ralt_switch"
[    93.411] (II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
[    93.412] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    93.412] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    93.412] (**) Power Button: always reports core events
[    93.412] (**) Power Button: Device: "/dev/input/event0"
[    93.491] (II) Power Button: Found keys
[    93.491] (II) Power Button: Configuring as keyboard
[    93.491] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    93.491] (**) Option "xkb_rules" "evdev"
[    93.491] (**) Option "xkb_model" "pc105"
[    93.491] (**) Option "xkb_layout" "us"
[    93.491] (**) Option "xkb_options" "lv3:ralt_switch"
[    93.492] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    93.492] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    93.492] (**) USB Optical Mouse: always reports core events
[    93.492] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    93.571] (II) USB Optical Mouse: Found 3 mouse buttons
[    93.571] (II) USB Optical Mouse: Found scroll wheel(s)
[    93.571] (II) USB Optical Mouse: Found relative axes
[    93.571] (II) USB Optical Mouse: Found x and y relative axes
[    93.571] (II) USB Optical Mouse: Configuring as mouse
[    93.571] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    93.571] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    93.571] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    93.571] (II) USB Optical Mouse: initialized for relative axes.
[    93.571] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    93.571] (II) No input driver/identifier specified (ignoring)
[    93.574] (II) config/udev: Adding input device Broadcom Corp BCM2045B3 ROM (/dev/input/event5)
[    93.574] (**) Broadcom Corp BCM2045B3 ROM: Applying InputClass "evdev keyboard catchall"
[    93.574] (**) Broadcom Corp BCM2045B3 ROM: always reports core events
[    93.574] (**) Broadcom Corp BCM2045B3 ROM: Device: "/dev/input/event5"
[    93.651] (II) Broadcom Corp BCM2045B3 ROM: Found keys
[    93.651] (II) Broadcom Corp BCM2045B3 ROM: Configuring as keyboard
[    93.651] (II) XINPUT: Adding extended input device "Broadcom Corp BCM2045B3 ROM" (type: KEYBOARD)
[    93.651] (**) Option "xkb_rules" "evdev"
[    93.651] (**) Option "xkb_model" "pc105"
[    93.651] (**) Option "xkb_layout" "us"
[    93.651] (**) Option "xkb_options" "lv3:ralt_switch"
[    93.651] (II) config/udev: Adding input device Broadcom Corp BCM2045B3 ROM (/dev/input/event6)
[    93.651] (**) Broadcom Corp BCM2045B3 ROM: Applying InputClass "evdev pointer catchall"
[    93.651] (**) Broadcom Corp BCM2045B3 ROM: always reports core events
[    93.651] (**) Broadcom Corp BCM2045B3 ROM: Device: "/dev/input/event6"
[    93.730] (II) Broadcom Corp BCM2045B3 ROM: Found 3 mouse buttons
[    93.730] (II) Broadcom Corp BCM2045B3 ROM: Found relative axes
[    93.730] (II) Broadcom Corp BCM2045B3 ROM: Found x and y relative axes
[    93.730] (II) Broadcom Corp BCM2045B3 ROM: Configuring as mouse
[    93.730] (**) Broadcom Corp BCM2045B3 ROM: YAxisMapping: buttons 4 and 5
[    93.730] (**) Broadcom Corp BCM2045B3 ROM: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    93.730] (II) XINPUT: Adding extended input device "Broadcom Corp BCM2045B3 ROM" (type: MOUSE)
[    93.730] (II) Broadcom Corp BCM2045B3 ROM: initialized for relative axes.
[    93.730] (II) config/udev: Adding input device Broadcom Corp BCM2045B3 ROM (/dev/input/mouse1)
[    93.730] (II) No input driver/identifier specified (ignoring)
[    93.730] (II) config/udev: Adding input device Device Media Center Interface (/dev/input/event4)
[    93.730] (**) Device Media Center Interface: Applying InputClass "evdev keyboard catchall"
[    93.730] (**) Device Media Center Interface: always reports core events
[    93.730] (**) Device Media Center Interface: Device: "/dev/input/event4"
[    93.810] (II) Device Media Center Interface: Found keys
[    93.810] (II) Device Media Center Interface: Configuring as keyboard
[    93.810] (II) XINPUT: Adding extended input device "Device Media Center Interface" (type: KEYBOARD)
[    93.810] (**) Option "xkb_rules" "evdev"
[    93.810] (**) Option "xkb_model" "pc105"
[    93.810] (**) Option "xkb_layout" "us"
[    93.810] (**) Option "xkb_options" "lv3:ralt_switch"
[    93.811] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    93.811] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    93.812] (**) AT Translated Set 2 keyboard: always reports core events
[    93.812] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    93.890] (II) AT Translated Set 2 keyboard: Found keys
[    93.890] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    93.890] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    93.890] (**) Option "xkb_rules" "evdev"
[    93.890] (**) Option "xkb_model" "pc105"
[    93.890] (**) Option "xkb_layout" "us"
[    93.890] (**) Option "xkb_options" "lv3:ralt_switch"

---

