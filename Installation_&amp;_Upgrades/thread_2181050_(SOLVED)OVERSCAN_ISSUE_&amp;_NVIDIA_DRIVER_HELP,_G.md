---
title: "(SOLVED)OVERSCAN ISSUE &amp; NVIDIA DRIVER HELP, GeForce9200"
date: 2013-10-16
forum: Installation &amp; Upgrades
---

### Post by dan-espinosa on 2013-10-16
Hello All;
 Thanks for taking the time to read my thread. I'm not new to the Ubuntu forum, and for some reason, it seems I now have a new acct. 
I've been having major trouble trying to fix overscanning problems on my HDTV through the HD port. I've done plenty of reading and searched countless threads, youtube, etc. on ways to installing NVIDIA drivers. I believe I finally have done so, but I'm not sure if it's the correct one. I've made attempts to installing the downloaded package which I got from NVIDIA website (NVIDIA-Linux-x86_64-319.60.run), via "Terminal" and I was unsuccesful. I ended up with a black screen. What I've noticed is that this is a MAJOR concern; specially for those unfortunate like me, having NVIDIA.
A little about my computer:
AMD Athlon II X2 255 dual-core processor
4GB DDR3
2TB-"External HD"-This is where I'm running my current (ArtistX Linux System)
NVIDIA GeForce 9200
and more....

These are commands from "Terminal" obtained:

daniel@daniel-Aspire-X3400G:~$ sudo lspci -k
00:00.0 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 0228
00:01.0 ISA bridge: NVIDIA Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 0228
00:01.1 SMBus: NVIDIA Corporation MCP78S [GeForce 8200] SMBus (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: nForce2_smbus
00:01.2 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
00:01.3 Co-processor: NVIDIA Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 0228
00:01.4 RAM memory: NVIDIA Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
00:02.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: ohci_hcd
00:02.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: ehci-pci
00:04.0 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: ohci_hcd
00:04.1 USB controller: NVIDIA Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: ehci-pci
00:07.0 Audio device: NVIDIA Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: snd_hda_intel
00:08.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 SATA controller: NVIDIA Corporation MCP78S [GeForce 8200] AHCI Controller (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: ahci
00:0a.0 Ethernet controller: NVIDIA Corporation MCP77 Ethernet (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 8000
    Kernel driver in use: forcedeth
00:0b.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Kernel driver in use: pcieport
00:12.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
    Kernel driver in use: pcieport
00:13.0 PCI bridge: NVIDIA Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
    Kernel driver in use: pcieport
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Kernel driver in use: k10temp
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200] (rev a2)
    Subsystem: Acer Incorporated [ALI] Device 0228
    Kernel driver in use: nvidia
daniel@daniel-Aspire-X3400G:~$ locate Xorg.0.log
/var/log/Xorg.0.log
daniel@daniel-Aspire-X3400G:~$ grep -i LoadModule /var/log/Xorg.0.log
[    23.717] (II) LoadModule: "glx"
[    25.370] (II) LoadModule: "nvidia"
[    25.541] (II) LoadModule: "nouveau"
[    25.593] (II) LoadModule: "vesa"
[    25.593] (II) LoadModule: "modesetting"
[    25.594] (II) LoadModule: "fbdev"
[    25.606] (II) LoadModule: "wfb"
[    25.615] (II) LoadModule: "ramdac"
[    25.641] (II) LoadModule: "fbdevhw"
[    26.224] (II) UnloadModule: "nouveau"
[    26.224] (II) UnloadModule: "vesa"
[    26.224] (II) UnloadModule: "modesetting"
[    26.224] (II) UnloadModule: "fbdev"
[    26.292] (II) LoadModule: "dri2"
[    26.316] (II) LoadModule: "evdev"
daniel@daniel-Aspire-X3400G:~$ lsmod | grep video
video                  18894  0 
daniel@daniel-Aspire-X3400G:~$ lsmod | grep nvidia
nvidia               8582455  48 
daniel@daniel-Aspire-X3400G:~$ hwinfo -gfxcard
oops: don't know what to do with "gfxcard"

*******************************************************************************************

And the following Info was obtained thanks to "hardinfo":

Summary
-------

-Computer-
Processor        : 2x AMD Athlon(tm) II X2 255 Processor
Memory        : 3611MB (663MB used)
Operating System        : Ubuntu 13.04
User Name        : daniel 
Date/Time        : Mon 14 Oct 2013 09:23:19 PM EDT
-Display-
Resolution        : 1920x1080 pixels
OpenGL Renderer        : GeForce 9200/integrated/SSE2/3DNOW!
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
-Input Devices-
 Power Button
 Power Button
 Video Bus
 Logitech USB Optical Mouse
 Lite-On Technology Corp. USB Multimedia Keyboard
 Lite-On Technology Corp. USB Multimedia Keyboard
 HDA NVidia HDMI/DP,pcm        : 3 Phantom=
 HDA NVidia Line
 HDA NVidia Rear Mic
 HDA NVidia Front Mic
 HDA NVidia Front Headphone
 HDA NVidia Line Out CLFE
 HDA NVidia Line Out Surround
 HDA NVidia Line Out Front
-Printers-
No printers found
-SCSI Disks-
HL-DT-ST DVDRAM GH60N
Generic- Compact Flash
Multiple Flash Reader
WD My Book 1140
WD SES Device

Operating System
----------------

-Version-
Kernel        : Linux 3.8.0-31-generic (i686)
Compiled        : #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) 
Distribution        : Ubuntu 13.04
-Current Session-
Computer Name        : daniel-Aspire-X3400G
User Name        : daniel (Daniel Espinosa)
Home Directory        : /home/daniel
Desktop Environment        : GNOME (gnome-fallback-compiz)
-Misc-
Uptime        : 33 minutes
Load Average        : 0.52, 0.41, 0.46

Kernel Modules
--------------

-Loaded Modules-
parport_pc        : PC-style parallel port driver
ppdev
bnep        : Bluetooth BNEP ver 1.3
rfcomm        : Bluetooth RFCOMM ver 1.11
bluetooth        : Bluetooth Core ver 2.16
binfmt_misc
snd_hda_codec_hdmi        : HDMI HD-audio codec
nvidia
snd_hda_codec_realtek        : Realtek HD-audio codec
kvm_amd
kvm
wmi        : ACPI-WMI Mapping Driver
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
snd_hwdep        : Hardware dependent layer
snd_pcm        : Midlevel PCM code for ALSA.
snd_page_alloc        : Memory allocator for ALSA system.
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq        : Advanced Linux Sound Architecture sequencer.
r8712u        : rtl871x wireless lan driver
snd_seq_device        : ALSA sequencer device management
snd_timer        : ALSA timer interface
joydev        : Joystick device interfaces
snd        : Advanced Linux Sound Architecture driver for soundcards.
mac_hid
shpchp        : Standard Hot Plug PCI Controller Driver
k10temp        : AMD Family 10h+ CPU core temperature monitor
i2c_nforce2        : nForce2/3/4/5xx SMBus driver
dm_multipath        : device-mapper multipath target
psmouse        : PS/2 mouse driver
scsi_dh        : SCSI device handler
soundcore        : Core sound module
microcode        : Microcode Update Driver
serio_raw        : Raw serio driver
lp
parport
btrfs
zlib_deflate
libcrc32c        : CRC32c (Castagnoli) calculations
dm_raid45        : device-mapper raid4/5 target
xor
dm_mirror        : device-mapper mirror target
dm_region_hash        : device-mapper region hash
dm_log        : device-mapper dirty region log
ses        : SCSI Enclosure Services (ses) driver
enclosure        : Enclosure Services
hid_generic        : HID generic driver
usbhid        : USB HID core driver
hid
usb_storage        : USB Mass Storage driver for Linux
video        : ACPI Video Driver
forcedeth        : Reverse Engineered nForce ethernet driver
ahci        : AHCI SATA low-level driver
libahci        : Common AHCI SATA low-level routines

Boots
-----

-Boots-
Mon Oct 14 20:49        : 3..8.0-31-generic|-
Mon Oct 14 18:12        : 3..8.0-31-generic|-
Mon Oct 14 17:44        : 3..8.0-31-generic|-

-Mounted File Systems-
/dev/sdd4    /    33.71 % (24.8 GiB of 37.4 GiB)    
none    /sys/fs/cgroup    0.00 % (4.0 KiB of 4.0 KiB)    
udev    /dev    0.00 % (1.7 GiB of 1.7 GiB)    
tmpfs    /run    0.26 % (351.8 MiB of 352.7 MiB)    
none    /run/lock    0.00 % (5.0 MiB of 5.0 MiB)    
none    /run/shm    0.00 % (1.7 GiB of 1.7 GiB)    
none    /run/user    0.05 % (99.9 MiB of 100.0 MiB)    
/dev/sdd5    /home    5.17 % (539.4 GiB of 568.9 GiB)    

Display
-------

-Display-
Resolution        : 1920x1080 pixels
Vendor        : The X.Org Foundation
Version        : 1.13.3
-Monitors-
Monitor 0        : 1920x1080 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-VidModeExtension
XINERAMA
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor        : NVIDIA Corporation
Renderer        : GeForce 9200/integrated/SSE2/3DNOW!
Version        : 3.3.0 NVIDIA 310.44
Direct Rendering        : Yes

Environment Variables
---------------------

-Environment Variables-
GNOME_KEYRING_PID        : 2660
USER        : daniel
TEXTDOMAIN        : im-config
SSH_AGENT_PID        : 2758
HOME        : /home/daniel
DESKTOP_SESSION        : gnome-fallback-compiz
XDG_SESSION_COOKIE        : ed22be89e85abd9069008e62525c4a6b-1381798213.930074-755814192
XDG_SEAT_PATH        : /org/freedesktop/DisplayManager/Seat0
GTK_MODULES        : gtk-vector-screenshot:overlay-scrollbar
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-TN8wPNPNLz,guid=ea2ac8ed510eec6c9aa7ebbc525c9147
GNOME_KEYRING_CONTROL        : /run/user/daniel/keyring-nnJNWf
UBUNTU_MENUPROXY        : libappmenu.so
MANDATORY_PATH        : /usr/share/gconf/gnome-fallback-compiz.mandatory.path
LOGNAME        : daniel
SUIL_MODULE_DIR        : /opt/kxstudio/lib/suil-0
DEFAULTS_PATH        : /usr/share/gconf/gnome-fallback-compiz.default.path
PATH        : /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
LADSPA_PATH        : /home/daniel/.ladspa:/usr/lib/ladspa:/usr/local/lib/ladspa
XDG_SESSION_PATH        : /org/freedesktop/DisplayManager/Session0
XDG_RUNTIME_DIR        : /run/user/daniel
DISPLAY        : :0
LANG        : en_US.UTF-8
XAUTHORITY        : /home/daniel/.Xauthority
SSH_AUTH_SOCK        : /run/user/daniel/keyring-nnJNWf/ssh
SHELL        : /bin/bash
GDMSESSION        : gnome-fallback-compiz
LV2_PATH        : /home/daniel/.lv2:/usr/lib/lv2:/usr/local/lib/lv2
TEXTDOMAINDIR        : /usr/share/locale/
PWD        : /home/daniel
XDG_DATA_DIRS        : /usr/share/gnome-fallback-compiz:/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_CONFIG_DIRS        : /etc/xdg/xdg-gnome-fallback-compiz:/etc/xdg
DSSI_PATH        : /home/daniel/.dssi:/usr/lib/dssi:/usr/local/lib/dssi
VST_PATH        : /home/daniel/.vst:/usr/lib/vst:/usr/local/lib/vst
GNOME_DESKTOP_SESSION_ID        : this-is-deprecated
SESSION_MANAGER        : local/daniel-Aspire-X3400G:@/tmp/.ICE-unix/2670,unix/daniel-Aspire-X3400G:/tmp/.ICE-unix/2670
XDG_CURRENT_DESKTOP        : GNOME
GPG_AGENT_INFO        : /run/user/daniel/keyring-nnJNWf/gpg:0:1
DESKTOP_AUTOSTART_ID        : 10a27e11bfef6541321381798216888900000026700003
GIO_LAUNCHED_DESKTOP_FILE        : /usr/share/applications/hardinfo.desktop
GIO_LAUNCHED_DESKTOP_FILE_PID        : 7056

Users
-----

-Users-
root        : root
daemon        : daemon
bin        : bin
sys        : sys
sync        : sync
games        : games
man        : man
lp        : lp
mail        : mail
news        : news
uucp        : uucp
proxy        : proxy
www-data        : www-data
backup        : backup
list        : Mailing List Manager
irc        : ircd
gnats        : Gnats Bug-Reporting System (admin)
libuuid
syslog
messagebus
colord        : colord colour management daemon
lightdm        : Light Display Manager
whoopsie
avahi-autoipd        : Avahi autoip daemon
avahi        : Avahi mDNS daemon
usbmux        : usbmux daemon
kernoops        : Kernel Oops Tracking Daemon
pulse        : PulseAudio daemon
rtkit        : RealtimeKit
speech-dispatcher        : Speech Dispatcher
hplip        : HPLIP system user
saned
postfix
couchdb        : CouchDB Administrator
haldaemon        : Hardware abstraction layer
motion
freevo
vdr        : VDR user
icecast2
timidity        : TiMidity++ MIDI sequencer service
postgres        : PostgreSQL administrator
rabbitmq        : RabbitMQ messaging server
gdm        : Gnome Display Manager
dnsmasq        : dnsmasq
nobody        : nobody
daniel        : Daniel

"NOTE: DID NOT DISPLAY NETWORK DETAILS" (Not needed)

Shared Directories
------------------

-SAMBA-
-NFS-

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>    3100 MHz    7.103    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    

CPU CryptoHash
--------------

-CPU CryptoHash-
<big><b>This Machine</b></big>    3100 MHz    222.074    

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>    3100 MHz    1.738    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>    3100 MHz    9.235    

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>    3100 MHz    2.974    

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>    3100 MHz    22.656    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647

*******************************************************************************************************


Any HELP or advice, direction, is more than appreciatted. 
THANK YOU,
Daniel



I  downloaded the newest available driver through synaptics- NVIDIA -319, and made some adjustments thanks to this helpful resource, I was able to resolve my problem.
[http://askubuntu.com/questions/80324/hdmi-vga-connection-cuts-borders-of-screen-or-creates-blurry-text](http://askubuntu.com/questions/80324/hdmi-vga-connection-cuts-borders-of-screen-or-creates-blurry-text)
Thanks Luis Alvarado. You tha "MAN"!!! :o:o:o

---

