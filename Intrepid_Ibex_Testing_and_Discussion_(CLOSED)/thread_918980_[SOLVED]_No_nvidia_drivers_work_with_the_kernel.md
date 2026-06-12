---
title: "[SOLVED] No nvidia drivers work with the kernel"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tnunamak on 2008-09-13
Hi,

I recently updated to the newest kernel on intrepid, and now the nvidia drivers can't load. I've tried all of the ones listed in the restricted driver manager. Here is the log file, and xorg.conf. Another problem seems to be that it can't find fonts, although I don't think that's a big issue at the moment. Any ideas? Thanks.

```
(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
X.Org X Server 1.5.0
Release Date: 
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server i686 Ubuntu
Current Operating System: Linux tnunamak-desktop 2.6.27-3-generic #1 SMP Wed Sep 10 16:02:00 UTC 2008 i686
Build Date: 11 September 2008  06:24:46PM
xorg-server 2:1.5.0-1ubuntu1 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 13 12:20:04 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	unix/:7100,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xf4000000/0, 0xe0000000/0, 0xf5000000/0, I/O @ 0x00007000/0, BIOS @ 0x????????/131072
(--) PCI: (0@5:0:0) Conexant CX23880/1/2/3 PCI Video and Audio Decoder rev 5, Mem @ 0xf9000000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded by default.
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.70  Wed Aug 27 13:16:51 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "type1"

(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"

(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) LoadModule: "mouse"

(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.99.905, module version = 1.3.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(II) NVIDIA dlloader X Driver  177.70  Wed Aug 27 12:55:53 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1280x1024 +1920+0, DFP: 1920x1080 +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-1"
(**) NVIDIA(0): Option "DPI" "144 x 144"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Here is my xorg.conf file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

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
# again, run the following commands:
#
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
# sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
# sudo dpkg-reconfigure xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

# local font server
	# if the local font server has problems, we can fall back on these
	# paths to defoma fonts
    FontPath        "unix/:7100"
    FontPath        "/usr/lib/X11/fonts/misc"
    FontPath        "/usr/lib/X11/fonts/cyrillic"
    FontPath        "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/lib/X11/fonts/Type1"
    FontPath        "/usr/lib/X11/fonts/CID"
    FontPath        "/usr/lib/X11/fonts/100dpi"
    FontPath        "/usr/lib/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "keyboard"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"

#    HorizSync       59.0 - 61.0
#    VertRefresh     66.0 - 68.0
#    DisplaySize 508 285  #96 DPI @ 1920x1080
#    DisplaySize 406 228 #120 DPI @ 1920x1080
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NoLogo" "True"
    Option         "DPI" "144 x 144"
EndSection

Section "Screen"

    #Option	   "SecondMonitorVertRefresh" "66.0-68.0"
# Removed Option "metamodes" "1920x1080 +0+0; 1280x1024 +0+0; 800x600 +0+0; 640x480 +0+0"
# Removed Option "metamodes" "CRT: 1280x1024 +1280+0, DFP: 1280x1024 +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: 1280x1024 +1920+0, DFP: 1920x1080 +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
EndSection


```

---

### Post by mrsteveman1 on 2008-09-13
Sounds like their kernel module isn't loaded. I would assume that Ubuntu has packaged it and that it's installed but perhaps now?

Whats the output of lsmod say? There should be an nvidia module of some kind.

---

### Post by philinux on 2008-09-13
[http://ubuntuforums.org/showthread.php?p=5782561#post5782561](http://ubuntuforums.org/showthread.php?p=5782561#post5782561)

See post 41 too.

---

### Post by tnunamak on 2008-09-13
Here's lmsod:

```
Module                  Size  Used by
af_packet              23812  2 
binfmt_misc            12808  1 
rfcomm                 41744  2 
l2cap                  25728  9 rfcomm
bluetooth              61156  4 rfcomm,l2cap
tun                    12672  0 
vboxdrv                77504  0 
nfsd                  228848  13 
auth_rpcgss            43424  1 nfsd
exportfs                6016  1 nfsd
ppdev                  10372  0 
ipv6                  267780  12 
speedstep_lib           6532  0 
cpufreq_ondemand        9740  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
container               5632  0 
video                  19856  0 
output                  4736  1 video
dock                   11280  0 
sbs                    15112  0 
sbshc                   7680  1 sbs
battery                14212  0 
nfs                   262540  0 
lockd                  67720  3 nfsd,nfs
nfs_acl                 4608  2 nfsd,nfs
sunrpc                185500  11 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
sbp2                   24072  0 
parport_pc             36260  1 
lp                     12324  0 
parport                37832  3 ppdev,parport_pc,lp
snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
cx88_blackbird         21252  0 
cx2341x                13444  1 cx88_blackbird
snd_emu10k1           146880  1 snd_emu10k1_synth
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
cx88_alsa              14216  0 
tuner                  42912  0 
tea5767                 6788  1 tuner
tda8290                12420  1 tuner
tuner_simple           10248  1 tuner
mt20xx                 13192  1 tuner
tea5761                 6020  1 tuner
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_seq_midi            9376  0 
joydev                 13120  0 
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_pcm                78596  4 snd_emu10k1,snd_ac97_codec,cx88_alsa,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cx8800                 35720  1 cx88_blackbird
cx8802                 19588  1 cx88_blackbird
cx88xx                 65960  4 cx88_blackbird,cx88_alsa,cx8800,cx8802
nvidia               4718832  0 
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sky2                   47492  0 
ir_common              36100  1 cx88xx
i2c_algo_bit            7300  1 cx88xx
psmouse                40336  0 
serio_raw               7940  0 
tveeprom               16656  1 cx88xx
emu10k1_gp              4608  0 
snd                    56996  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_seq_dummy,snd_seq_oss,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  10 tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,cx88xx,nvidia,i2c_algo_bit,tveeprom
gameport               16008  2 emu10k1_gp
soundcore               8800  1 snd
videodev               29440  3 cx88_blackbird,cx8800,cx88xx
v4l1_compat            15492  1 videodev
compat_ioctl32          2304  1 cx8800
v4l2_common            18304  6 cx88_blackbird,cx2341x,tuner,cx8800,cx88xx,videodev
videobuf_dma_sg        14980  5 cx88_blackbird,cx88_alsa,cx8800,cx8802,cx88xx
videobuf_core          18820  5 cx88_blackbird,cx8800,cx8802,cx88xx,videobuf_dma_sg
btcx_risc               5896  4 cx88_alsa,cx8800,cx8802,cx88xx
button                  9232  0 
intel_agp              25492  0 
iTCO_wdt               13092  0 
iTCO_vendor_support     4868  1 iTCO_wdt
pcspkr                  4224  0 
shpchp                 34452  0 
agpgart                34760  2 nvidia,intel_agp
pci_hotplug            30880  1 shpchp
evdev                  13056  7 
ext3                  136712  3 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
sd_mod                 30720  6 
ata_generic             8324  0 
usbhid                 31872  0 
hid                    38784  1 usbhid
usb_storage            73664  0 
libusual               19108  1 usb_storage
pata_acpi               8320  0 
floppy                 59588  0 
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394
ahci                   28420  4 
ata_piix               19588  0 
pata_jmicron            7040  0 
libata                159344  5 ata_generic,pata_acpi,ahci,ata_piix,pata_jmicron
scsi_mod              151436  6 sbp2,sg,sr_mod,sd_mod,usb_storage,libata
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146028  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                16796  0 
processor              36872  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  1 

```

---

### Post by inportb on 2008-09-13
I wouldn't use the restricted drivers, as they have not yet been updated by their proprietors to work with the new Xorg. Try using the opensource drivers.

---

### Post by tnunamak on 2008-09-13
By open source do you mean the nouveau drivers? I installed them in the meantime but they don't work very well. 

philinux, I'll give that a try when I get a chance.

---

### Post by plun on 2008-09-13
You seems to have used nvidia-xconfig and it brakes Xorg 7.4

Reference
[http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1666354&postcount=4)

Also  "Configured Video Device" is now used.

My xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

```


Also what gives a locate  ?

```
plun@plun:~$ locate nvidia.ko
/lib/modules/2.6.27-2-generic/kernel/drivers/video/nvidia.ko
/lib/modules/2.6.27-3-generic/updates/dkms/nvidia.ko
/lib/modules/last-good-boot/updates/dkms/nvidia.ko
/var/lib/dkms/nvidia/177.70/2.6.27-3-generic/i686/module/nvidia.ko
/var/lib/dkms/nvidia/177.70/build/.nvidia.ko.cmd
/var/lib/dkms/nvidia/177.70/build/nvidia.ko
plun@plun:~$ 

```

A kernel reinstall trigger a DKMS rebuild, easiest with Synaptic.


Also file a bug...!!!

---

### Post by tnunamak on 2008-09-13
plun you nailed it, it was all an xorg.conf problem after reading the link you posted:
[http://www.nvnews.net/vbulletin/show...54&postcount=4](http://www.nvnews.net/vbulletin/show...54&postcount=4)

Here is my new xorg.conf:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	ModelName	"CRT-0"
	HorizSync	30.0-80.0
	VertRefresh	60.0-75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Monitor0"
	Device		"Configured Video Device"
	Option		"TwinView" "1"
#	Option		TwinViewXineramaInfoOrder"	"DFP-1"
	Option		"metamodes" "DFP: 1920x1080 +0+0, CRT: 1280x1024 +1920+0; DFP: 1280x1024 +0+0, CRT: 1280x1024; DFP: 1280x1024 +0+0, CRT: NULL"
EndSection

```

When I uncomment this line:
```
Option		TwinViewXineramaInfoOrder"	"DFP-1"
```
X fails again. I'm trying to set up TwinView, but I can't get the second monitor (DFP) to display anything. Does it even work with xserver right now?

---

### Post by plun on 2008-09-13
> **tnunamak said:**
> plun you nailed it, it was all an xorg.conf problem after reading the link you posted:

When I uncomment this line:
```
Option		TwinViewXineramaInfoOrder"	"DFP-1"
```
X fails again. I'm trying to set up TwinView, but I can't get the second monitor (DFP) to display anything. Does it even work with xserver right now?

Nope,  its more like "trial & error" for the moment.:)

We are on "the edge of development" and nVidias driver works at least for
basic functions.  (worse for ATI)

This is also a case for nVidia developers because its a closed driver.

This is nVidias official manual
[ftp://download.nvidia.com/XFree86/Linux-x86/177.70/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.70/README/index.html)

But... Xorg 7.4 isn't final yet.

---

### Post by MALEADt on 2008-09-13
> **plun said:**
> But... Xorg 7.4 isn't final yet.

[It soon will be](http://www.phoronix.com/scan.php?page=article&item=xorg_74_released&num=1) :)

---

### Post by Nullack on 2008-09-13
Im not sure there is any evidence to support the complexities of a video driver are better served by FOSS projects.

Nvidia afterall have full opengl support accelerated in hardware while the FOSS drivers seem to progress very slowly. Even when ati release tech doco. Herding cats comes to mind :)

And we still dont have a unified video memory manager

---

### Post by mrsteveman1 on 2008-09-13
> **Nullack said:**
> Im not sure there is any evidence to support the complexities of a video driver are better served by FOSS projects.

That is a logical fallacy. It isn't about closed source manufacturer supported drivers vs. open source community supported drivers. Things can be open without relying on the community to support them. 

If Nvidia opened their main drivers (hell even released specs) everyone would be happy. 

> **Nullack said:**
> 
Nvidia afterall have full opengl support accelerated in hardware 

The nvidia driver actually sucks, I seem to remember Linus saying something to the effect that it isn't even a native linux driver (conversation was about the derivative works of the kernel stuff, its not because it was written for another OS, or so they say).

> **Nullack said:**
> 
the FOSS drivers seem to progress very slowly. Even when ati release tech doco. Herding cats comes to mind :)

The FOSS drivers progress slowly because they are wandering around in the dark hoping stuff works, while Nvidia knows exactly how the chip works and can do whatever they want.

AMD released specs for those ATI chips, but it takes time to actually write drivers for them.

---

### Post by Nullack on 2008-09-13
You can call it a logical fallacy or an unfortunate decision or whatever, but ultimately NVIDIA owns the software and has decided how to licence it.

The NVIDIA driver provides me with full opengl hardware acceleration. Any alternative does not, so your conclusions about the NVIDIA driver are truly bizzare. The functionality of the driver aside, (which is superior to others), the performance of the NVIDIA driver has been greatly improved in recent releases.

I'll make the point that even when the FOSS community has the tech doco like with AMD, progress is slow. Somehow some individuals in their zealism automatically consider closed source software to be "evil and worthless" and when it comes to the simple fact that FOSS alternatives lack key attributes and cant be used effectively the response is "oh it takes time" completing ignorning the serious effect it has on the user experience.

GPU's are non trivial devices and I see no practical evidence from AMD or NVIDIA FOSS driver projects where such projects can realistically match the closed source driver capabilities. Yes it would be nice if NVIDIA opened their source code, but its their decision to make.

---

### Post by AdrianVeidt on 2008-09-14
Nullack, I couldn't agree more. But it would still be nice to have the drivers in the kernel. I'm sure RadeonHD/DRI2/Gallium3d/GEM will be in there with no showstoppers. Some time in the 26th century.

---

### Post by Nullack on 2008-09-14
My friends, can I have a brief moment of pure honesty?

I think what NVIDIA did is really crappy, and their decision is poor.

But as much as well all spend these days working on Ubuntu, the dollar has power. NVIDIA had the power to employ people who sit there 40 hours + a weel working on Linux drivers. That gets results. You cant write a GPU driver in 100 lines of code :)

Atleast NVIDIA offered Linux drivers.....On the numbers, we dont really matter to them were a small group of many much larger groups.

---

### Post by mrsteveman1 on 2008-09-14
[quote=Nullack]You can call it a logical fallacy or an unfortunate decision or whatever, but ultimately NVIDIA owns the software and has decided how to licence it.[/quote]

The logical fallacy is in continuing to repeat the idea that drivers CAN'T be supported competently by anyone but the manufacturer, or that there is this hard line between closed, manufacturer supported drivers, or open community drivers, with "community" being falsely assumed to mean random people involved in the project. I think you will find that a lot of the work being done on the open drivers is done by other, large companies or professional programmers working for those companies. Novell is the one doing a lot of the work on the ATI/AMD driver right now thanks to the documentation that was released. Simply because distros aren't using the newest code to come out of that effort doesn't mean real progress isn't being made quickly. I would even go so far as to say that it is possible for the community (including other companies) to develop a driver FASTER than the original manufacturer of the chip, simply because there are more people working on it, but that assumes there is documentation available.

[quote=Nullack]Atleast NVIDIA offered Linux drivers.....On the numbers, we dont really matter to them were a small group of many much larger groups.[/quote]

Not only is the Linux home user market not small (there are millions of hardware devices shipping with Linux right now), the market for Nvidia products specifically on Linux is not small or financially insignificant. Nvidia makes workstation cards that are used on Linux, those things are expensive, much more than the ~$200 the consumer cards cost. Overall, Nvidias support for Linux isn't even up to the level one would expect if it WAS a small insignificant market.

Nvidias driver is better than the community one for one reason and one reason only, they know how the chips work. It is still a very poor driver, but no one but Nvidia can do anything about that. 

I see nothing wrong with blasting them for putting everyone in this situation. Only they can write a competent native driver, they aren't doing that, and simultaneously they prevent everyone else from being able to do so by refusing to document their own hardware. Clearly this is not a situation common to all GPU makers, AMD sees no problem releasing specs for their chips, so i highly doubt this is a case of trade secrets needing to be protected. I think its about control, Nvidia uses their driver to differentiate the expensive workstation stuff from the cheaper consumer stuff (even though they are virtually identical chips in some cases).

I do think that regardless of all this, Nvidia is about to take a huge hit in the market for making defective chips, which might open things up a bit for AMD to regain ground.

---

### Post by jfernyhough on 2008-09-14
Just to throw in another workaround I used when I did a fresh Alpha5 install:

1) Install Intrepid. Update. (A reboot might be a good idea here too).
2) Use Jockey to install nvidia-177
3) Reboot
4) X will fail so continue in failsafe, drop to a shell, ensure GDM is stopped with a $ sudo /etc/init.d/gdm stop
5) $ sudo dpkg-reconfigure -phigh xserver-xorg (this undoes changes Jockey makes, breaking X)
6) $ sudo nano /etc/X11/xorg.conf
7) Add Driver  "nvidia" to display section
8) Start GDM again with $ sudo /etc/init.d/gdm start
9) Everything should work

---

### Post by gtdaqua on 2008-09-15
NVIDIA doesnt load - if it loads, cant see X. Adding Driver "nvidia" doesnt help! 
Have to go to recovery mode and use the option to fix X Server alone works for now and the default resolution is 800x600 not even an option to choose 1024x768!

---

### Post by gtdaqua on 2008-09-16
The beta driver of NVIDIA 177.70 helps. 

Here is the link:

[ftp://download.nvidia.com/XFree86/Linux-x86/177.70/NVIDIA-Linux-x86-177.70-pkg1.run]("ftp://download.nvidia.com/XFree86/Linux-x86/177.70/NVIDIA-Linux-x86-177.70-pkg1.run")

---

### Post by Nullack on 2008-09-16
I highly recommend not using that link and deploying the new version through the official Ubuntu repos

---

### Post by MaX on 2008-09-16
Nullack: Then maybe you can explain how to get this to work. Because jockey-gtk doesn't install the new driver.

---

### Post by Nullack on 2008-09-16
> **MaX said:**
> Nullack: Then maybe you can explain how to get this to work. Because jockey-gtk doesn't install the new driver.

Your free to do anything you want with Intrepid of course :) You are though encouraged to contribute to the development process by trying things out and reporting bugs, then working with people to fix the problems with Intrepid. Hacking things up outside the repos and not being involved in bugs does not add value to Intrepid as whole - it just fixes the individuals machine.

Max take a look at this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816)

Theres a number of things mentioned there to try.

Were going to need more details from you to do deeper debugging. Does the nvidia module load onto the kernel? What does your X logs say? What exactly happens? Does this occur on a clean Intrepid build / have you hacked up any needed dependencies?

---

### Post by xebian on 2008-09-16
@nullack
I'm just curious as to how Intrepid is installing it.  

177.70 won't install because of the Xen kernel.  I can install it by ignoring it but it's unuseable, very slow, white screen in plain KDE4 without desktop effects.

173.14.12 does not support kernel 2.6.27.

177.70 is running great in hardy kde3 and debian/kde4

Appreciate your inputs and links.

---

### Post by MaX on 2008-09-16
> **Nullack said:**
> Your free to do anything you want with Intrepid of course :) You are though encouraged to contribute to the development process by trying things out and reporting bugs, then working with people to fix the problems with Intrepid. Hacking things up outside the repos and not being involved in bugs does not add value to Intrepid as whole - it just fixes the individuals machine.

Max take a look at this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-envy-2.6.24/+bug/261816)

Theres a number of things mentioned there to try.

Were going to need more details from you to do deeper debugging. Does the nvidia module load onto the kernel? What does your X logs say? What exactly happens? Does this occur on a clean Intrepid build / have you hacked up any needed dependencies?

I figured it out... 
Uninstall mdks mkds?
Then manually remove /var/lib/mdks/nvidia
reinstall nvidia-glx-177 and mdks
et voila!

---

### Post by JairunCaloth on 2008-09-22
I was able to simply install nvidia-glx-177. Then run nvidia-xconfig.

$ glxinfo | grep direct
direct rendering: Yes

---

