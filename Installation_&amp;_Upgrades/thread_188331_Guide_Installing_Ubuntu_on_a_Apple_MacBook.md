---
title: "Guide: Installing Ubuntu on a Apple MacBook"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by tophfisher on 2006-06-03
Hi everyone. I pulled together a lot of the info I could find, and filled in some of the blanks on my own, on how to get Ubuntu Dapper installed on an Apple MacBook.

This guide is for Dual Booting, but could work for Tri-booting OS X, Windows, and Linux.

This guide covers basic install, the install of lilo, getting sound, high-res video, aiglx/Compiz, fn Keys, right click and SMP support.

[http://bin-false.org/?p=17]("http://bin-false.org/?p=17")

Hope it helps some! :)

---

### Post by llamakc on 2006-06-03
Very nice.

---

### Post by cromestant on 2006-06-04
Great job man, now all I have to do is buy my macbook...Probably a month or so..

I hope this get's build into the installer soon, since it seems like a lot of tweaking.

---

### Post by tophfisher on 2006-06-04
It's a bit of tweakaing for sure. But once you start it seems to go fairly fast. And the end result is one of the best Linux systems I have ever used.

A big warning though - Sleep is not yet working for me... I am sure there is a way, the system goes to sleep, just does not wake up... SOOO... That just somthing to know... I found that Dapper boots so quickly on this laptop that I am ok with just shutting down.

---

### Post by cromestant on 2006-06-04
I read somewhere that the two cores don't work well under linux, something about smp, but I am no t sure, are both your cores working? What about temperature, are the fans kicking in when they must?

I must say that I am really excited about this, now I  really am looking forward to getting a macbook and tripple booting

---

### Post by crimsondragon12 on 2006-06-05
Hmmmm this doesn't appear to work... I installed the packages on my Macbook Pro and nothing new..... any others know how to fix this?

---

### Post by cromestant on 2006-06-09
Hey you guys, I finally have my macbook, so I am doing the install.
Just a thing about your guide, after chrooting I had to apt-get update, to be able to install any package as it said that it did not have them.

Thanks for the guide, will post back when I  am done

---

### Post by cromestant on 2006-06-09
I had a little problem with the install ( well not the install of ubuntu
) but I don't know why, now the refit menu that is supposed to load windows xp also loads ubuntu...

I don't really care, I'll use paralels for windows, but I wanted to know How I could "absorbe the free space for ubuntu... or should I just reinstall the whole sistem?

thank you

---

### Post by tophfisher on 2006-06-12
Hey all... I just started a new Podcast, and we covered our thoughts/impressions on Ubuntu on the MacBook. You can check us out at:
[URL="http://www.linuxactionshow.com/"]
http://www.linuxactionshow.com/[/URL]

---

### Post by cromestant on 2006-06-16
Nice podcast btw, sent the link to a friend of mine here in venzuela, liked it too.

---

### Post by tophfisher on 2006-06-16
Right on, thanks!

---

### Post by cromestant on 2006-06-17
Hey, i'm here again, I decided to go with the glx install as described in your how too ( the one you link from linuxactionshow)
And followed it and all was well up until the part where one has to restart gdm. 
I did and it failed.
so I check the log at /var/log/xorg.conf.log and this is what I get  after all the LOOONG log wich only displays no errors:

```
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16064 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 5120 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0xffff000 (0x3712d000)
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0xfffb000 (0x36d7c000)
(II) I810(0): Allocated 4 kB for Overlay registers at 0xfffa000 (0x370a4000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0xffea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xf8e4a000
(II) I810(0): [drm] mapped SAREA 0xf8e4a000 to 0xb78e6000
(II) I810(0): [drm] framebuffer handle = 0x80020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Allocated 3072 kB for the back buffer at 0xf800000.
(II) I810(0): Allocated 3072 kB for the depth buffer at 0xf400000.
(II) I810(0): Allocated 32 kB for the logical context at 0xf3f8000.
(II) I810(0): Allocated 54016 kB for textures at 0x520000
(II) I810(0): Updated framebuffer allocation size from 5120 to 5128 kByte
(II) I810(0): Updated pixmap cache from 512 scanlines to 514 scanlines
(II) I810(0): 0x81fa54c: Memory at offset 0x00020000, size 5128 kBytes
(II) I810(0): 0x81feb20: Memory at offset 0x0ffff000, size 4 kBytes
(II) I810(0): 0x81feb48: Memory at offset 0x0fffb000, size 16 kBytes
(II) I810(0): 0x81faaf4: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x81fa58c: Memory at offset 0x0ffea000, size 64 kBytes
(II) I810(0): 0x81feb70: Memory at offset 0x0fffa000, size 4 kBytes
(II) I810(0): 0x81fa5dc: Memory at offset 0x0f800000, size 3072 kBytes
(II) I810(0): 0x81fa5fc: Memory at offset 0x0f400000, size 3072 kBytes
(II) I810(0): 0x81fa63c: Memory at offset 0x0f3f8000, size 32 kBytes
(II) I810(0): 0x81fa61c: Memory at offset 0x00520000, size 54016 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0x90380000
(II) I810(0): [drm] Back Buffer = 0x8f800000
(II) I810(0): [drm] Depth Buffer = 0x8f400000
(II) I810(0): [drm] ring buffer = 0x80000000
(II) I810(0): [drm] textures = 0x80520000
(II) I810(0): [drm] dma control initialized, using IRQ 177
(II) I810(0): [drm] Initialized kernel agp heap manager, 55312384
(II) I810(0): [dri] visual configs initialized
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x00fbf000 (pgoffset 4031)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x0ffff000 (pgoffset 65535)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x0fffb000 (pgoffset 65531)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x0ffea000 (pgoffset 65514)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x0fffa000 (pgoffset 65530)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x0f800000 (pgoffset 63488)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0f400000 (pgoffset 62464)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0f3f8000 (pgoffset 62456)
(WW) I810(0): PGTBL_ER is 0x00000102
(II) I810(0): Display plane A is disabled and connected to Pipe A.
(II) I810(0): Display plane B is enabled and connected to Pipe B.
(II) I810(0): Enabling plane B.
(II) I810(0): Display plane A is now disabled and connected to Pipe A.
(II) I810(0): Display plane B is now enabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x00000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 47 Mpixel/s
(II) I810(0): maxBandwidth is 1152 Mbyte/s, pipe bandwidths are 252 Mbyte/s, 0 Mbyte/s
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		16 128x128 slots
		4 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x1
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) I810(0): [drm] removed 1 reserved context for kernel
(II) I810(0): [drm] unmapping 8192 bytes of SAREA 0xf8e4a000 at 0xb78e6000
(WW) I810(0): Successfully set original devices
(WW) I810(0): Setting the original video mode instead of restoring
	the saved state
(WW) I810(0): Extended BIOS function 0x5f05 failed.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)

```

so I see there is a problem with wacom thingies.. so I go to /etc/X11/xorg.conf and comment them out. and try again with the same results.

I don;t know what happened and how to fix this, maybe you can help me out ( pleaaaase).

this is mu current xorg.conf :
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"dbe"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option	"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	#InputDevice     "stylus" "SendCoreEvents"
#	#InputDevice     "cursor" "SendCoreEvents"
#	#InputDevice     "eraser" "SendCoreEvents"
	Option	"AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
EndSection

```

I know this is long, and thank you for the help

---

### Post by cromestant on 2006-06-17
gdm.conf-custom file, just in  case :
```
# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
#
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
#
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
#
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# http://www.gnome.org/projects/gdm/
#
# NOTE: Lines that begin with "#" are considered comments.
#
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=aiglx

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true

```

thanks again

---

### Post by cromestant on 2006-06-17
I can't understand any of this... since I was waiting for your reply, I decided just to shutdown and go to sleep... so I inputed the clasic shutdown now command I used in gentoo, and I get the services shuting down, then a message that says to provide root password or press control d to continue.. so I input the password and back to the terminal....
now.
i do it again but this time I get back to the message and press control d, and I don't know why... or how, I am suddenly greeted in the gdm login ( no reboot happened)...
and I have xgl working...

i don;t know if this will work tomorow, so if you could still check the previous posts to see if you can see an error...

this is weird.

Thanks

---

### Post by tophfisher on 2006-06-17
[QUOTE=cromestant]
i don;t know if this will work tomorow, so if you could still check the previous posts to see if you can see an error...

this is weird.

Thanks[/QUOTE]

This sounds very werid... Hmm.. I would like to know if this is still an issue for you?

Just a correction too..  With the MacBooks we are using a combo of aiglx and Compiz. aiglx is an extension to the regular X11 server, and Compiz is the software that enables all the cool effects and renders them through the aiglx exensions. XGL is not the same as aiglx, it is a replacement of the X11 server that also uses Compiz to create the effects and render them through the XGL X11 server.

XGL does not yet have strong support for the Intel cards in our MacBooks, where aiglx seems to be working great.

Not sure on your error stuff... Keep us updated?

-Chris

---

### Post by cromestant on 2006-06-17
well all is working today... strange.. might be something with the dist-upgrade.. unsynched packages maybe?

well, but anyways, it works.
i just have some more questions.

FN key does not seem to be working.. no backlight control... ( installed the packages in the how too)...

On the dsrt page you link from the how too, cris, thsy have updated saying that one should not use them now, suposedly dapper has them now. do you know anything about that?

Can I xmodmap  my second enter key to have a del ( not backspace) key ( reverse deleting)?

Why is the wifi signal lower on ubuntu than on macos.?

Well thanks for your patience...

When is the next linux action show podcast?

Charles

---

### Post by tophfisher on 2006-06-17
Charles,

When the packages are installed from that link I gave out, the backlight control should be automatic via Gnome-Powermanager.

The FN keys SHOULD be working if those packages are installed correctly? Maybe re-install them?

The next Linux Action Show! Episode should be out in a couple days, thanks for asking!
-Chris

[QUOTE=cromestant]well all is working today... strange.. might be something with the dist-upgrade.. unsynched packages maybe?

well, but anyways, it works.
i just have some more questions.

FN key does not seem to be working.. no backlight control... ( installed the packages in the how too)...

On the dsrt page you link from the how too, cris, thsy have updated saying that one should not use them now, suposedly dapper has them now. do you know anything about that?

Can I xmodmap  my second enter key to have a del ( not backspace) key ( reverse deleting)?

Why is the wifi signal lower on ubuntu than on macos.?

Well thanks for your patience...

When is the next linux action show podcast?

Charles[/QUOTE]

---

### Post by cromestant on 2006-06-19
Which package did you install, there is a macbook-backlight-hal which is the one I installed, and there is another one that I did not install since the dsrt guy said that the hald was the way to go.

Also, I just checked and with xev I can see that my fn key does not generate an event.

Thank you again
Charles

---

### Post by tophfisher on 2006-06-19
I did install the hal version... You might check his blog:
[http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

he says there have been some updates to the dapper kernel that make it so you no longer need to install the macbook-modules package... I have not gotten a chance to play with this... I guess one thing to try would be to remove the macbook-modules package, make sure you are running the latest kernel (be sure to run lilo after kernel upgrades) and see if your fn key works...

Let me know!
-Chris

[QUOTE=cromestant]Which package did you install, there is a macbook-backlight-hal which is the one I installed, and there is another one that I did not install since the dsrt guy said that the hald was the way to go.

Also, I just checked and with xev I can see that my fn key does not generate an event.

Thank you again
Charles[/QUOTE]

---

### Post by cromestant on 2006-06-19
Ok top.. will try it and report back.

One question though
does your macbook get hot?

---

### Post by tophfisher on 2006-06-19
Yeah... Yeah it gets warm. I guess all the new Duo Core laptops get really warm. And Apple puts a metal sheet along the bottom of the case that I gotta figure heats up. I mean, it gets to warm to put in my lap, but I think thats the price we pay for such fast CPUs in our laptops.

-Chris

[QUOTE=cromestant]Ok top.. will try it and report back.

One question though
does your macbook get hot?[/QUOTE]

---

### Post by cromestant on 2006-06-19
wel lI was just checking wether it was a flaw in mine, but you are right... migut be a little hot for the lap, but it's still a great computer for the price

---

### Post by zhuomingliang on 2006-06-20
some hours ago,i have this problem,
and after apt-get upgrade,
the gdm(with /etc/gdm/modules updating ) is OK.
now there is no problem.

---

### Post by arroc on 2006-06-20
Did anybody have any luck with getting the DVI-out to work?

---

### Post by phico on 2006-06-20
[QUOTE=arroc]Did anybody have any luck with getting the DVI-out to work?[/QUOTE]

Yes I did with Macbook **Pro**
( [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453) )
I believe I should be the same with Macbook ..

---

### Post by cromestant on 2006-06-21
Nice second podcast man!...

Reinstalled the macbook backlight hal package and no dice, although i am able to control the backilight using the other package, mabook-backlight + ( or -) 10

still no event from fn key... I am sad... don' t know what to do...

I also have a little question... do you know how I could xmod a del key?

I have the second enters key keycode which I could use to xmod map to a del key... but I don;t know how i would put it... although I reall would just prefer to get the fn key working for the backlight dimming ( volume would also be nice)...

any advice?

---

### Post by tophfisher on 2006-06-21
So my fn key for volume seems to be working now, but thats it! heh.. MAN... 

For the key bindings, I really do not know much about it... I JUST started playing with them for switching around the ALT key with the Apple key. And a few other small things... Maybe you can see what I have done,
[http://bin-false.org/?p=17](http://bin-false.org/?p=17)

And take it from there?

Good luck! Thanks for listening to the Podcast too!
-Chris


[QUOTE=cromestant]Nice second podcast man!...

I also have a little question... do you know how I could xmod a del key?

I have the second enters key keycode which I could use to xmod map to a del key... but I don;t know how i would put it... although I reall would just prefer to get the fn key working for the backlight dimming ( volume would also be nice)...

any advice?[/QUOTE]

---

### Post by muted on 2006-06-23
So as far as i have heard, the graphic card in the macbook (the non-pro) is pretty weak for games and so on. I do not game meself, but i'd really want compiz working, so I was wondering if anyone have tried this and could compare it to the compiz working with ie a good nvidia card??

---

### Post by cromestant on 2006-06-23
Compiz works great... just  a little problem tho.

Java swing apps don't work well... I have to ( for example net beans) start it, get a grey screen, then switch to metacity ( all the proper things appear on the screen) then switch back to compiz and all is great.

---

### Post by tophfisher on 2006-06-23
The vdieo card is very weak for games, but Compiz seems to work fine. Have an Nivdia 6800GT in a tower that I also run Compiz on, it uses XGL. And I in fact perfer aiglx/compiz on my MacBook over the tower.

-Chris

[QUOTE=cromestant]Compiz works great... just  a little problem tho.

Java swing apps don't work well... I have to ( for example net beans) start it, get a grey screen, then switch to metacity ( all the proper things appear on the screen) then switch back to compiz and all is great.[/QUOTE]

---

### Post by cromestant on 2006-07-03
By the way, us figured out what to do with the second enter key.
I Configured it for it to be a Delete ( since the keyboard has no delete button, just a backspace.).
If you are interested in doing this, just add this to your xmodmap file :

```
keycode 108 = Delete

```

---

### Post by cromestant on 2006-08-01
Hey fish, i don;t kow if you are still monitoring this, but i had a kernel upgrade recently and now refit shows 2 linux icons.. i supose it's because he sees two kernels in mi linux partition.

Since I usually run grub i don't know how to fix this fith lilo.

or should i just unistall the old kernel

please post some code. 
thanks

---

### Post by tophfisher on 2006-08-01
I no longer have the MacBook.. It was tied to the job :-)

Sorry about that!

---

### Post by martinbures on 2006-08-04
> **cromestant said:**
> wel lI was just checking wether it was a flaw in mine, but you are right... migut be a little hot for the lap, but it's still a great computer for the price

My Macbook gets pretty hot when I am using it with Dapper.  When I use it with OS X it does not really get this hot - only when I am really maxing it out.  I seems to me that the CPU scaling is probably not working properly.  As the kernel panic seems to be caused by a timing issue and the sleep does not seem to be working because some things are not pointed in the right places, the temperature issue probably has similar origins.  Does anyone know where this is controlled?  How can I go about looking into this?

---

### Post by we2by on 2006-09-22
I have Ubuntu dapper installed on my macbook with compiz etc. it works perfect. I can play video files with mplayer without any lag. and sound , wireless, batery status working.  except one thing. 
When I choose System => Quit, my ubuntu froze (vlc still playing music), so I think gnome is broken? any one got a fix for this or experiencing the same problem. 
Sometimes I can't even boot Ubuntu after manually force shutdown by holding the power button. To boot Ubuntu again, I had to put in the ubuntu cd and boot from it. Then mount /dev/sda3 as /mnt/ubuntu , same for proc and dev. then do lilo -b /dev/sda. This fix the problem temporaly.

---

### Post by martinbures on 2006-09-22
From what I can tell, a lot of the problems with Ubuntu stem from the kernel.  Putting a more modern kernel with various intel/apple chipset fixes would make it work properly.  That is why I am heavily anticipating Edgy.  However, it seems that getting Edgy installing on a macbook is not a priority for the devs.  You should look at Fedora Core 6 when it finalizes.  Red Hat made it a priority to get linux working on the new intel apple hardware and it shows.  I installed FC6-test 2 and no special steps were needed to get it to install.  It "just worked."  I would prefer to run Ubuntu, but I would prefer to run linux over OS X more.

---

### Post by goneskiing on 2006-09-22
marinbures
I'm with you - prefer Ubuntu but prefer linux more (I may sell my macbook and get a thinkpad) but meanwhile - I've tried FC6 T3 but install fails on X and screen gets garbled - did you use any special parameters to start.

---

### Post by martinbures on 2006-09-23
I have not installed with T3, but used T2, and am in the same boat.  I really like the macbook but am sitting here going "Should have just gotten the thinkpad - would not be going through this."

When I installed with T2, I just booted as normal.  It automatically detected my display - I am using a macbook so it is the integrated intel - I don't know what might happen with the ATI. 

So you are saying that the installer itself didn't work?

In my opinion, the fedora bug tracker is a lot easier to search and then when you do add a bug, it seems to get much more attention from the developers - especially for something like this.  I used to use Fedora - core 3 and 4 but 4 was really buggy and around that time, Ubuntu finally got to a state that was workable.

---

### Post by goneskiing on 2006-09-23
on my macbook pro 15"  FC6 T3 install would not load X - fought thru garbled text install - but then could not get xorg.conf to accept any driver including "vesa".  I also tried FC6 T2 but install hung on not finding display.  Edgy knot 3 hung in the install during timezones

I'm tired of fighting it and accepting that linux doesnt run well on macbook so I'm cutting my losses and dumping my macbook and buying a Thinkpad - between hardware and lost productivity I figure the Mac has cost me about $5000.  Expensive lesson.

---

### Post by we2by on 2006-09-23
After hours searching on the inetrnet and trying things out, I have found this. If you shut down you r macbook by running sudo poweroff in your terminal, you won't get kernel panic (yet. have tried this a few times and no kernel panic.). I hope this helps you guys too!

I'm using a smp kernel and used this guide to install Ubuntu [http://bin-false.org/?p=17](http://bin-false.org/?p=17)

---

