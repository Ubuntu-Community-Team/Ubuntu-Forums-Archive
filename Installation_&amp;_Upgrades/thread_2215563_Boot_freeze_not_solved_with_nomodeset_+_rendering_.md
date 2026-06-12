---
title: "Boot freeze not solved with nomodeset + rendering mode display"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by nicolaskokel on 2014-04-07
Dear forum,

I have an older configuration, Pavilion HDX 9150 EF, which I have formated in order to install Ubuntu.  
From the first install, I had boot issues but could anyway manage after rebooting in recovery mode to access to the graphical interface.
Lubuntu 12.04 was the first version I installed, but there were missing LCD management options and the display was not bright.
When upgrading to Lubuntu 12.10 64-bit, the brightness was good as it used to be with Windows installed.
A later upgrade to Lubuntu 13.04 made the boot issues and display management worse again.
I replaced it with LINUX MINT 16 Cinnamon 64-bit, and then booting became almost impossible
Only from time to time after multiple rebooting of the machine via the power-off / power-on, it has been possible to get the graphical interface, but with the mention :

> running in rendering mode

The screen resolution is 1280 x 1024 instead of native 1680 x 1050 and the screen is not bright. 

From the LINUX MINT boot menu, I edited the boot configuration and replaced 'quiet splash' with 'nomodeset' as suggested else where and it helped to reach the graphical interface.
Then I updated MINT via the update manager, and from there on, the boot issues reappeared.
The boot process freezes repeatedly (boot config shows 'quiet splash nomodeset' correctly and removing 'quiet splash from that line does not help either.
This image shows where the system hangs:

[IMG][IMG]http://i59.tinypic.com/1zvd75t.jpg[/IMG][/IMG]

The following details where collected before the MINT update :

nicolas@HP-Pavilion-HDX9000-Notebook-PC ~ $ grep -i bios /var/log/Xorg.0.log
[    83.309] (--) PCI:*(0:1:0:0) 1002:9583:103c:30d4 rev 0, Mem @ 0xd0000000/268435456, 0xe8300000/65536, I/O @ 0x00006000/256, BIOS @ 0x????????/131072
[    84.534] (II) VESA(0): VESA BIOS detected
[    84.534] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    85.927] (II) VESA(0): VESA BIOS detected
[    85.927] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS


nicolas@HP-Pavilion-HDX9000-Notebook-PC ~ $ inxi -Gx
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV630/M76 [Mobility Radeon HD 2600 XT/2700] bus-ID: 01:00.0 
           X.Org: 1.14.3 drivers: ati,radeon (unloaded: fbdev) FAILED: vesa Resolution: 1280x1024@61.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits) GLX Version: 2.1 Mesa 9.2.1 Direct Rendering: Yes

nicolas@HP-Pavilion-HDX9000-Notebook-PC ~ $ grep -i module /var/log/Xorg.0.log
[    83.305] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    83.305] (II) Module ABI versions:
[    83.310] (II) LoadModule: "dri2"
[    83.310] (II) Module "dri2" already built-in
[    83.310] (II) LoadModule: "glamoregl"
[    83.337] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    83.497] (II) Module glamoregl: vendor="X.Org Foundation"
[    83.498]     compiled for 1.14.2.901, module version = 0.5.1
[    83.498] (II) LoadModule: "glx"
[    83.498] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    83.498] (II) Module glx: vendor="X.Org Foundation"
[    83.498]     compiled for 1.14.3, module version = 1.0.0
[    83.499] (II) LoadModule: "fglrx"
[    83.499] (WW) Warning, couldn't open module fglrx
[    83.499] (II) UnloadModule: "fglrx"
[    83.499] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    83.499] (II) LoadModule: "ati"
[    83.500] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    83.500] (II) Module ati: vendor="X.Org Foundation"
[    83.500]     compiled for 1.14.3, module version = 7.2.0
[    83.500]     Module class: X.Org Video Driver
[    83.500] (II) LoadModule: "radeon"
[    83.500] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    83.511] (II) Module radeon: vendor="X.Org Foundation"
[    83.511]     compiled for 1.14.3, module version = 7.2.0
[    83.511]     Module class: X.Org Video Driver
[    83.511] (II) LoadModule: "vesa"
[    83.511] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    83.512] (II) Module vesa: vendor="X.Org Foundation"
[    83.512]     compiled for 1.14.1, module version = 2.3.2
[    83.512]     Module class: X.Org Video Driver
[    83.512] (II) LoadModule: "modesetting"
[    83.512] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    83.512] (II) Module modesetting: vendor="X.Org Foundation"
[    83.512]     compiled for 1.14.1, module version = 0.8.0
[    83.512]     Module class: X.Org Video Driver
[    83.512] (II) LoadModule: "fbdev"
[    83.513] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    83.513] (II) Module fbdev: vendor="X.Org Foundation"
[    83.513]     compiled for 1.14.1, module version = 0.4.3
[    83.513]     Module class: X.Org Video Driver
[    83.513] (II) LoadModule: "fglrx"
[    83.514] (WW) Warning, couldn't open module fglrx
[    83.514] (II) UnloadModule: "fglrx"
[    83.514] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    83.514] (II) LoadModule: "ati"
[    83.514] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    83.514] (II) Module ati: vendor="X.Org Foundation"
[    83.514]     compiled for 1.14.3, module version = 7.2.0
[    83.514]     Module class: X.Org Video Driver
[    83.514] (II) LoadModule: "vesa"
[    83.515] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    83.515] (II) Module vesa: vendor="X.Org Foundation"
[    83.515]     compiled for 1.14.1, module version = 2.3.2
[    83.515]     Module class: X.Org Video Driver
[    83.515] (II) UnloadModule: "vesa"
[    83.515] (II) Failed to load module "vesa" (already loaded, 0)
[    83.515] (II) LoadModule: "modesetting"
[    83.515] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    83.515] (II) Module modesetting: vendor="X.Org Foundation"
[    83.515]     compiled for 1.14.1, module version = 0.8.0
[    83.515]     Module class: X.Org Video Driver
[    83.515] (II) UnloadModule: "modesetting"
[    83.515] (II) Failed to load module "modesetting" (already loaded, 0)
[    83.515] (II) LoadModule: "fbdev"
[    83.516] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    83.516] (II) Module fbdev: vendor="X.Org Foundation"
[    83.516]     compiled for 1.14.1, module version = 0.4.3
[    83.516]     Module class: X.Org Video Driver
[    83.516] (II) UnloadModule: "fbdev"
[    83.516] (II) Failed to load module "fbdev" (already loaded, 0)
[    83.528] (II) Loading sub module "fbdevhw"
[    83.528] (II) LoadModule: "fbdevhw"
[    83.528] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    83.528] (II) Module fbdevhw: vendor="X.Org Foundation"
[    83.528]     compiled for 1.14.3, module version = 0.0.2
[    83.528] (II) UnloadModule: "radeon"
[    83.528] (II) UnloadModule: "radeon"
[    83.528] (II) UnloadModule: "radeon"
[    83.528] (II) UnloadModule: "radeon"
[    83.528] (II) Loading sub module "vbe"
[    83.528] (II) LoadModule: "vbe"
[    83.529] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    83.529] (II) Module vbe: vendor="X.Org Foundation"
[    83.529]     compiled for 1.14.3, module version = 1.1.0
[    83.529] (II) Loading sub module "int10"
[    83.529] (II) LoadModule: "int10"
[    83.529] (II) Loading /usr/lib/xorg/modules/libint10.so
[    83.529] (II) Module int10: vendor="X.Org Foundation"
[    83.529]     compiled for 1.14.3, module version = 1.0.0
[    84.555] (II) Loading sub module "ddc"
[    84.555] (II) LoadModule: "ddc"
[    84.555] (II) Module "ddc" already built-in
[    84.790] (II) Loading sub module "shadow"
[    84.790] (II) LoadModule: "shadow"
[    84.790] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    84.790] (II) Module shadow: vendor="X.Org Foundation"
[    84.790]     compiled for 1.14.3, module version = 1.1.0
[    84.790] (II) Loading sub module "fb"
[    84.790] (II) LoadModule: "fb"
[    84.790] (II) Loading /usr/lib/xorg/modules/libfb.so
[    84.791] (II) Module fb: vendor="X.Org Foundation"
[    84.791]     compiled for 1.14.3, module version = 1.0.0
[    84.791] (II) UnloadModule: "radeon"
[    84.791] (II) UnloadModule: "modesetting"
[    84.791] (II) UnloadModule: "fbdev"
[    84.791] (II) UnloadSubModule: "fbdevhw"
[    84.791] (II) Loading sub module "int10"
[    84.791] (II) LoadModule: "int10"
[    84.791] (II) Loading /usr/lib/xorg/modules/libint10.so
[    84.791] (II) Module int10: vendor="X.Org Foundation"
[    84.791]     compiled for 1.14.3, module version = 1.0.0
[    86.383] (II) LoadModule: "evdev"
[    86.384] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.402] (II) Module evdev: vendor="X.Org Foundation"
[    86.402]     compiled for 1.14.1, module version = 2.7.3
[    86.402]     Module class: X.Org XInput Driver
[    86.420] (II) LoadModule: "synaptics"
[    86.421] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    86.421] (II) Module synaptics: vendor="X.Org Foundation"
[    86.421]     compiled for 1.14.2, module version = 1.7.1
[    86.421]     Module class: X.Org XInput Driver

Pls let me know which additional details are needed and how to collect them from a command line.

---

### Post by nicolaskokel on 2014-04-07
Finally I booted from an USB drive with MINT 13 Long Term Support.
I had to add 'nomodeset' anyway from the MINT boot menu in order to have the system started and got an error message related to xorg server:

[IMG]http://i62.tinypic.com/2agus8z.jpg[/IMG]

After system start the display resolution is correct, and I could retrieve system and log details.
Here after hardware info report.
[COLOR=#ff0000][B]I also have copied : auth.log ; boot.log ; syslog ; Xorg.failsafe.log ; XOrg.0.log
Please let me know which of these files are needed to help identifying the problem, and I will copy them here.[/B][/COLOR]


SYSTEM INFO
> Computer
********




Summary
-------


-Computer-
Processor        : 2x Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
Memory        : 4049MB (655MB used)
Operating System        : Linux Mint 13 Maya
User Name        : mint (Live session user)
Date/Time        : Mon 07 Apr 2014 04:43:28 PM UTC
-Display-
Resolution        : 1680x1050 pixels
OpenGL Renderer        : Gallium 0.4 on llvmpipe (LLVM 0x300)
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel
Audio Adapter        : HDA-Intel - HDA ATI HDMI
-Input Devices-
 Sleep Button
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 HP WMI hotkeys
 SynPS/2 Synaptics TouchPad
 HP Webcam
 HDA Intel Front Headphone
 HDA Intel Mic
 HDA Intel Front Headphone Front
 HDA ATI HDMI HDMI/DP,pcm        : 3=
-Printers-
No printers found
-SCSI Disks-
ATA TOSHIBA MK1637GS
ATA TOSHIBA MK1637GS
MATSHITA DVD-RAM UJ-861H
LaCie iamaKey


Operating System
----------------


-Version-
Kernel        : Linux 3.2.0-23-generic (x86_64)
Compiled        : #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) 
Distribution        : Linux Mint 13 Maya
-Current Session-
Computer Name        : mint
User Name        : mint (Live session user)
Home Directory        : /home/mint
Desktop Environment        : Unknown (Window Manager: Metacity)
-Misc-
Uptime        : 2 hours, 40 minutes
Load Average        : 0.47, 0.44, 0.34


Kernel Modules
--------------


-Loaded Modules-
ufs
qnx4
hfsplus        : Extended Macintosh Filesystem
hfs
minix
ntfs        : NTFS 1.2/3.x driver - Copyright (c) 2001-2011 Anton Altaparmakov and Tuxera Inc.
msdos        : MS-DOS filesystem support
xfs        : SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
reiserfs        : ReiserFS journaled filesystem
jfs        : The Journaled Filesystem (JFS)
dm_crypt        : device-mapper target for transparent encryption / decryption
snd_hda_codec_hdmi        : HDMI HD-audio codec
snd_hda_codec_idt        : IDT/Sigmatel HD-audio codec
arc4        : ARC4 Cipher Algorithm
snd_hda_intel        : Intel HDA driver
snd_hda_codec        : HDA codec core
uvcvideo        : USB Video Class driver
iwl4965        : Intel(R) Wireless WiFi 4965 driver for Linux
snd_hwdep        : Hardware dependent layer
videodev        : Device registrar for Video4Linux drivers v2
snd_pcm        : Midlevel PCM code for ALSA.
iwl_legacy        : iwl-legacy: common functions for 3945 and 4965
joydev        : Joystick device interfaces
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
mac80211        : IEEE 802.11 subsystem
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_timer        : ALSA timer interface
v4l2_compat_ioctl32
snd_seq_device        : ALSA sequencer device management
snd        : Advanced Linux Sound Architecture driver for soundcards.
psmouse        : PS/2 mouse driver
r852        : Ricoh 85xx xD/smartmedia card reader driver
sm_common        : Common SmartMedia/xD functions
soundcore        : Core sound module
nand        : Generic NAND flash driver code
nand_ids        : Nand device &amp; manufacturer IDs
snd_page_alloc        : Memory allocator for ALSA system.
cfg80211        : wireless configuration support
mtd        : Core MTD registration and access routines
nand_bch        : NAND software BCH ECC support
bch        : Binary BCH encoder/decoder
hp_wmi        : HP laptop WMI hotkeys driver
nand_ecc        : Generic NAND ECC support
sparse_keymap        : Generic support for sparse keymaps
r592        : Ricoh R5C592 Memstick/Memstick PRO card reader driver
memstick        : Sony MemoryStick core driver
serio_raw        : Raw serio driver
parport_pc        : PC-style parallel port driver
dm_multipath        : device-mapper multipath target
bnep        : Bluetooth BNEP ver 1.3
ppdev
lp
rfcomm        : Bluetooth RFCOMM ver 1.11
mac_hid
parport
bluetooth        : Bluetooth Core ver 2.16
binfmt_misc
squashfs        : squashfs 4.0, a compressed read-only filesystem
overlayfs        : Overlay filesystem
nls_iso8859_1
nls_cp437
vfat        : VFAT filesystem support
fat
ext2        : Second Extended Filesystem
dm_raid45        : device-mapper raid4/5 target
xor
dm_mirror        : device-mapper mirror target
dm_region_hash        : device-mapper region hash
dm_log        : device-mapper dirty region log
btrfs
zlib_deflate
libcrc32c        : CRC32c (Castagnoli) calculations
firewire_ohci        : Driver for PCI OHCI IEEE1394 controllers
firewire_core        : Core IEEE1394 transaction logic
sdhci_pci        : Secure Digital Host Controller Interface PCI driver
radeon        : ATI Radeon
sdhci        : Secure Digital Host Controller Interface core driver
crc_itu_t        : CRC ITU-T V.41 calculations
sky2        : Marvell Yukon 2 Gigabit Ethernet driver
sata_sil24        : Silicon Image 3124/3132 SATA low-level driver
ttm        : TTM memory manager subsystem (for DRM device)
drm_kms_helper        : DRM KMS helper
drm        : DRM shared core routines
i2c_algo_bit        : I2C-Bus bit-banging algorithm
video        : ACPI Video Driver
wmi        : ACPI-WMI Mapping Driver
usb_storage        : USB Mass Storage driver for Linux


Boots
-----


-Boots-
Mon Apr 7 1:03        : 33..2.0-23-generic|-


Languages
---------


-Available Languages-
en_AG        : English language locale for Antigua and Barbuda
en_AG.utf8        : English language locale for Antigua and Barbuda
en_AU.utf8        : English locale for Australia
en_BW.utf8        : English locale for Botswana
en_CA.utf8        : English locale for Canada
en_DK.utf8        : English locale for Denmark
en_GB.utf8        : English locale for Britain
en_HK.utf8        : English locale for Hong Kong
en_IE.utf8        : English locale for Ireland
en_IN        : English language locale for India
en_IN.utf8        : English language locale for India
en_NG        : English locale for Nigeria
en_NG.utf8        : English locale for Nigeria
en_NZ.utf8        : English locale for New Zealand
en_PH.utf8        : English language locale for Philippines
en_SG.utf8        : English language locale for Singapore
en_US.utf8        : English locale for the USA
en_ZA.utf8        : English locale for South Africa
en_ZM        : English locale for Zambia
en_ZM.utf8        : English locale for Zambia
en_ZW.utf8        : English locale for Zimbabwe
zh_CN.utf8        : Chinese locale for Peoples Republic of China
zh_SG.utf8        : Chinese language locale for Singapore


Filesystems
-----------


-Mounted File Systems-
/cow    /    6.55 % (1.8 GiB of 1.9 GiB)    
udev    /dev    0.00 % (1.9 GiB of 1.9 GiB)    
tmpfs    /run    0.13 % (789.9 MiB of 790.9 MiB)    
/dev/sdc1    /cdrom    53.15 % (1.8 GiB of 3.8 GiB)    
/dev/loop0    /rofs    100.00 % (0.0 B of 769.4 MiB)    
tmpfs    /tmp    0.00 % (1.9 GiB of 1.9 GiB)    
none    /run/lock    0.08 % (5.0 MiB of 5.0 MiB)    
none    /run/shm    0.00 % (1.9 GiB of 1.9 GiB)    


Display
-------


-Display-
Resolution        : 1680x1050 pixels
Vendor        : The X.Org Foundation
Version        : 1.11.3
-Monitors-
Monitor 0        : 1680x1050 pixels
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
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-DRI
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
XVideo-MotionCompensation
-OpenGL-
Vendor        : VMware, Inc.
Renderer        : Gallium 0.4 on llvmpipe (LLVM 0x300)
Version        : 2.1 Mesa 8.0.2
Direct Rendering        : Yes


Environment Variables
---------------------


-Environment Variables-
USER        : mint
SSH_AGENT_PID        : 2790
HOME        : /home/mint
MDM_LANG        : en_US.UTF-8
XDG_SESSION_COOKIE        : f7012485049ff17774093e5800000011-1396879408.173781-658712300
DESKTOP_SESSION        : default.desktop
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-kI3fQAHDrl,guid=9ec1397bed374a237de044220000001c
MDMSESSION        : default.desktop
MANDATORY_PATH        : /usr/share/gconf/default.desktop.mandatory.path
LOGNAME        : mint
DEFAULTS_PATH        : /usr/share/gconf/default.desktop.default.path
USERNAME        : mint
WINDOWPATH        : 8
PATH        : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
DISPLAY        : :0.0
LANG        : en_US.UTF-8
XAUTHORITY        : /home/mint/.Xauthority
SSH_AUTH_SOCK        : /tmp/keyring-7MlJ46/ssh
SHELL        : /bin/bash
RUNNING_UNDER_GDM        : yes
PWD        : /home/mint
XDG_DATA_DIRS        : /usr/share/default.desktop:/usr/share/gnome:/usr/local/share/:/usr/share/:/usr/share/mdm/
XDG_CONFIG_DIRS        : /etc/xdg/xdg-default.desktop:/etc/xdg
MDM_XSERVER_LOCATION        : local
GNOME_DESKTOP_SESSION_ID        : this-is-deprecated
SESSION_MANAGER        : local/mint:@/tmp/.ICE-unix/2713,unix/mint:/tmp/.ICE-unix/2713
XDG_CURRENT_DESKTOP        : GNOME
GNOME_KEYRING_CONTROL        : /tmp/keyring-7MlJ46
GPG_AGENT_INFO        : /tmp/keyring-7MlJ46/gpg:0:1
GIO_LAUNCHED_DESKTOP_FILE        : /usr/share/applications/hardinfo.desktop
GIO_LAUNCHED_DESKTOP_FILE_PID        : 8936


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
nobody        : nobody
libuuid
syslog
messagebus
colord        : colord colour management daemon
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
haldaemon        : Hardware abstraction layer
mdm        : MDM Display Manager
mint        : Live session user


Devices
*******




Processor
---------


-Processors-
Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz        : 2001.00MHz
Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz        : 2001.00MHz


Memory
------


-Memory-
Total Memory        : 4049608 kB
Free Memory        : 2449860 kB
Buffers        : 186676 kB
Cached        : 946060 kB
Cached Swap        : 0 kB
Active        : 510212 kB
Inactive        : 867232 kB
Active(anon)        : 308400 kB
Inactive(anon)        : 70760 kB
Active(file)        : 201812 kB
Inactive(file)        : 796472 kB
Unevictable        : 0 kB
Mlocked        : 0 kB
Virtual Memory        : 0 kB
Free Virtual Memory        : 0 kB
Dirty        : 0 kB
Writeback        : 0 kB
AnonPages        : 244708 kB
Mapped        : 64888 kB
Shmem        : 134452 kB
Slab        : 91648 kB
SReclaimable        : 66020 kB
SUnreclaim        : 25628 kB
KernelStack        : 2776 kB
PageTables        : 21616 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 2024804 kB
Committed_AS        : 1731128 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 123888 kB
VmallocChunk        : 34359606776 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 118464 kB
DirectMap2M        : 4075520 kB


PCI Devices
-----------


-PCI Devices-
Host bridge        : Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
PCI bridge        : Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
Audio device        : Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
PCI bridge        : Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
PCI bridge        : Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
USB controller        : Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
PCI bridge        : Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
ISA bridge        : Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
IDE interface        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
SATA controller        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
SMBus        : Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
VGA compatible controller        : Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT] (prog-if 00 [VGA controller])
Audio device        : Advanced Micro Devices [AMD] nee ATI RV630 audio device [Radeon HD 2600 Series]
FireWire (IEEE 1394)        : Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
SD Host controller        : Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
System peripheral        : Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
System peripheral        : Ricoh Co Ltd xD-Picture Card Controller (rev 12)
Network controller        : Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
Mass storage controller        : Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
Ethernet controller        : Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)


USB Devices
-----------




Printers
--------


-Printers-
No printers found


Battery
-------


-Battery: C1FB-
State        : charged (load: 0 mA)
Capacity        : 3531 mAh / 3531 mAh (100.00%)
Battery Technology        : rechargeable (LIon)
Model Number        : Primary
Serial Number        : 02450 08/09/2007


Sensors
-------




Input Devices
-------------


-Input Devices-
 Sleep Button
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 HP WMI hotkeys
 SynPS/2 Synaptics TouchPad
 HP Webcam
 HDA Intel Front Headphone
 HDA Intel Mic
 HDA Intel Front Headphone Front
 HDA ATI HDMI HDMI/DP,pcm        : 3=


Storage
-------


-SCSI Disks-
ATA TOSHIBA MK1637GS
ATA TOSHIBA MK1637GS
MATSHITA DVD-RAM UJ-861H
LaCie iamaKey


DMI
---


-BIOS-
Date        : 08/28/2008
Vendor        : Hewlett-Packard ([www.hp.com]("http://www.hp.com"))
Version        : 68DVD Ver. F.40
-Board-
Name        : 30D4
Vendor        : Hewlett-Packard ([www.hp.com]("http://www.hp.com"))


Resources
---------


-I/O Ports-
<tt>0000-0cf7 </tt>        : PCI Bus 0000:00
<tt>  0000-001f </tt>        : dma1
<tt>  0020-0021 </tt>        : pic1
<tt>  0040-0043 </tt>        : timer0
<tt>  0050-0053 </tt>        : timer1
<tt>  0060-0060 </tt>        : keyboard
<tt>  0062-0062 </tt>        : EC data
<tt>  0064-0064 </tt>        : keyboard
<tt>  0066-0066 </tt>        : EC cmd
<tt>  0070-0071 </tt>        : rtc0
<tt>  0080-008f </tt>        : dma page reg
<tt>  00a0-00a1 </tt>        : pic2
<tt>  00c0-00df </tt>        : dma2
<tt>  00f0-00ff </tt>        : fpu
<tt>  0170-0177 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    0170-0177 </tt>        : ata_piix
<tt>  01f0-01f7 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    01f0-01f7 </tt>        : ata_piix
<tt>  0376-0376 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    0376-0376 </tt>        : ata_piix
<tt>  03c0-03df </tt>        : vga+
<tt>  03f6-03f6 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    03f6-03f6 </tt>        : ata_piix
<tt>  04d0-04d1 </tt>        : pnp 00:0b
<tt>  0500-057f </tt>        : pnp 00:0a
<tt>  0800-080f </tt>        : pnp 00:0a
<tt>0cf8-0cff </tt>        : PCI conf1
<tt>0d00-ffff </tt>        : PCI Bus 0000:00
<tt>  1000-107f </tt>        : Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
<tt>    1000-107f </tt>        : pnp 00:0b
<tt>      1000-1003 </tt>        : ACPI PM1a_EVT_BLK
<tt>      1004-1005 </tt>        : ACPI PM1a_CNT_BLK
<tt>      1008-100b </tt>        : ACPI PM_TMR
<tt>      1010-1015 </tt>        : ACPI CPU throttle
<tt>      1020-1020 </tt>        : ACPI PM2_CNT_BLK
<tt>      1028-102f </tt>        : ACPI GPE0_BLK
<tt>  1100-113f </tt>        : Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
<tt>    1100-113f </tt>        : pnp 00:0b
<tt>  1200-121f </tt>        : Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
<tt>    1200-121f </tt>        : pnp 00:0b
<tt>  1370-1377 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
<tt>    1370-1377 </tt>        : ahci
<tt>  13f0-13f7 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
<tt>    13f0-13f7 </tt>        : ahci
<tt>  1574-1577 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
<tt>    1574-1577 </tt>        : ahci
<tt>  15f4-15f7 </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
<tt>    15f4-15f7 </tt>        : ahci
<tt>  2000-2fff </tt>        : PCI Bus 0000:28
<tt>    2000-20ff </tt>        : Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
<tt>      2000-20ff </tt>        : Marvell Yukon 2 Gigabit Ethernet driver
<tt>  3000-3fff </tt>        : PCI Bus 0000:20
<tt>    3000-307f </tt>        : Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
<tt>  4000-5fff </tt>        : PCI Bus 0000:08
<tt>  6000-6fff </tt>        : PCI Bus 0000:01
<tt>    6000-60ff </tt>        : Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT] (prog-if 00 [VGA controller])
<tt>  7000-701f </tt>        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
<tt>    7000-701f </tt>        : uhci_hcd
<tt>  7020-703f </tt>        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
<tt>    7020-703f </tt>        : uhci_hcd
<tt>  7040-705f </tt>        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
<tt>    7040-705f </tt>        : uhci_hcd
<tt>  7060-707f </tt>        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
<tt>    7060-707f </tt>        : uhci_hcd
<tt>  7080-709f </tt>        : Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
<tt>    7080-709f </tt>        : uhci_hcd
<tt>  70a0-70af </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
<tt>    70a0-70af </tt>        : ata_piix
<tt>  70e0-70ff </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
<tt>    70e0-70ff </tt>        : ahci
<tt>  8000-8fff </tt>        : PCI Bus 0000:30
<tt>  9000-9fff </tt>        : PCI Bus 0000:10
-Memory-
<tt>00000000-0000ffff </tt>        : reserved
<tt>00010000-0009fbff </tt>        : System RAM
<tt>0009fc00-0009ffff </tt>        : reserved
<tt>000a0000-000bffff </tt>        : PCI Bus 0000:00
<tt>000c0000-000cefff </tt>        : Video ROM
<tt>000cf000-000cffff </tt>        : pnp 00:0c
<tt>000d0000-000dffff </tt>        : PCI Bus 0000:00
<tt>000e0000-000fffff </tt>        : reserved
<tt>  000f0000-000fffff </tt>        : System ROM
<tt>00100000-bffaffff </tt>        : System RAM
<tt>  01000000-016699ab </tt>        : Kernel code
<tt>  016699ac-01ce4fff </tt>        : Kernel data
<tt>  01dd3000-01f28fff </tt>        : Kernel bss
<tt>bffb0000-bffc53ff </tt>        : reserved
<tt>bffc5400-bffe7fb7 </tt>        : ACPI Non-volatile Storage
<tt>bffe7fb8-bfffffff </tt>        : reserved
<tt>c0000000-fedfffff </tt>        : PCI Bus 0000:00
<tt>  c0100000-c01000ff </tt>        : Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
<tt>  c0200000-c03fffff </tt>        : PCI Bus 0000:30
<tt>  c0400000-c05fffff </tt>        : PCI Bus 0000:30
<tt>  c0600000-c08fffff </tt>        : PCI Bus 0000:28
<tt>    c0600000-c061ffff </tt>        : Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
<tt>  c0900000-c0afffff </tt>        : PCI Bus 0000:10
<tt>  d0000000-dfffffff </tt>        : PCI Bus 0000:01
<tt>    d0000000-dfffffff </tt>        : Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT] (prog-if 00 [VGA controller])
<tt>  e0000000-e00fffff </tt>        : PCI Bus 0000:28
<tt>    e0000000-e0003fff </tt>        : Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
<tt>      e0000000-e0003fff </tt>        : Marvell Yukon 2 Gigabit Ethernet driver
<tt>  e0100000-e01fffff </tt>        : PCI Bus 0000:20
<tt>    e0100000-e010007f </tt>        : Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
<tt>      e0100000-e010007f </tt>        : Silicon Image 3124/3132 SATA low-level driver
<tt>    e0102000-e0103fff </tt>        : Silicon Image, Inc. SiI 3531 [SATALink/SATARaid] Serial ATA Controller (rev 01)
<tt>      e0102000-e0103fff </tt>        : Silicon Image 3124/3132 SATA low-level driver
<tt>  e0200000-e02fffff </tt>        : PCI Bus 0000:10
<tt>    e0200000-e0201fff </tt>        : Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
<tt>      e0200000-e0201fff </tt>        : Intel(R) Wireless WiFi 4965 driver for Linux
<tt>  e4000000-e7ffffff </tt>        : PCI Bus 0000:08
<tt>  e8000000-e82fffff </tt>        : PCI Bus 0000:02
<tt>    e8000000-e80007ff </tt>        : Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
<tt>      e8000000-e80007ff </tt>        : Driver for PCI OHCI IEEE1394 controllers
<tt>    e8001000-e80010ff </tt>        : Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
<tt>      e8001000-e80010ff </tt>        : mmc0
<tt>    e8003000-e80030ff </tt>        : Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
<tt>      e8003000-e80030ff </tt>        : Ricoh R5C592 Memstick/Memstick PRO card reader driver
<tt>    e8004000-e80040ff </tt>        : Ricoh Co Ltd xD-Picture Card Controller (rev 12)
<tt>      e8004000-e80040ff </tt>        : Ricoh 85xx xD/smartmedia card reader driver
<tt>  e8300000-e83fffff </tt>        : PCI Bus 0000:01
<tt>    e8300000-e830ffff </tt>        : Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT] (prog-if 00 [VGA controller])
<tt>    e8310000-e8313fff </tt>        : Advanced Micro Devices [AMD] nee ATI RV630 audio device [Radeon HD 2600 Series]
<tt>      e8310000-e8313fff </tt>        : ICH HD audio
<tt>    e8320000-e833ffff </tt>        : Advanced Micro Devices [AMD] nee ATI RV630 [Mobility Radeon HD 2600 XT] (prog-if 00 [VGA controller])
<tt>  e8400000-e84003ff </tt>        : Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
<tt>    e8400000-e84003ff </tt>        : ehci_hcd
<tt>  e8404000-e8407fff </tt>        : Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
<tt>    e8404000-e8407fff </tt>        : ICH HD audio
<tt>  e8408000-e84083ff </tt>        : Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
<tt>    e8408000-e84083ff </tt>        : ehci_hcd
<tt>  e8409000-e84097ff </tt>        : Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03) (prog-if 01 [AHCI 1.0])
<tt>    e8409000-e84097ff </tt>        : ahci
<tt>  f8000000-fbffffff </tt>        : PCI MMCONFIG 0000 [bus 00-3f]
<tt>    f8000000-fbffffff </tt>        : pnp 00:0b
<tt>  fec00000-fec00fff </tt>        : reserved
<tt>    fec00000-fec003ff </tt>        : IOAPIC 0
<tt>  fed00000-fed003ff </tt>        : HPET 0
<tt>  fed20000-fed99fff </tt>        : reserved
<tt>    fed20000-fed3ffff </tt>        : pnp 00:0b
<tt>    fed45000-fed8ffff </tt>        : pnp 00:0b
<tt>    fed90000-fed99fff </tt>        : pnp 00:0b
<tt>  feda0000-fedbffff </tt>        : reserved
<tt>    feda0000-fedbffff </tt>        : pnp 00:0c
<tt>fee00000-fee00fff </tt>        : Local APIC
<tt>  fee00000-fee00fff </tt>        : reserved
<tt>    fee00000-fee00fff </tt>        : pnp 00:0c
<tt>fee01000-ffffffff </tt>        : PCI Bus 0000:00
<tt>  ffb00000-ffbfffff </tt>        : reserved
<tt>    ffb00000-ffbfffff </tt>        : pnp 00:0a
<tt>  fff00000-ffffffff </tt>        : reserved
<tt>    fff00000-ffffffff </tt>        : pnp 00:0a
<tt>100000000-13fffffff </tt>        : System RAM
-DMA-
<tt> 4</tt>        : cascade


Network
*******




Interfaces
----------


-Network Interfaces-
lo    0.01MiB    0.01MiB    127.0.0.1    
wlan0    1.84MiB    0.95MiB    192.168.1.13    
eth0    0.00MiB    0.00MiB        


IP Connections
--------------


-Connections-
0.0.0.0:139    LISTEN    0.0.0.0:*    tcp    
127.0.0.1:53        0.0.0.0:*    udp    
127.0.0.1:631    LISTEN    0.0.0.0:*    tcp    
0.0.0.0:445    LISTEN    0.0.0.0:*    tcp    
192.168.1.13:44576    CLOSE_WAIT    91.189.94.25:80    tcp    
:::139    LISTEN    :::*    tcp6    
::1:631    LISTEN    :::*    tcp6    
:::445    LISTEN    :::*    tcp6    
127.0.0.1:53        0.0.0.0:*    udp    
0.0.0.0:68        0.0.0.0:*    udp    
192.168.1.255:137        0.0.0.0:*    udp    
192.168.1.13:137        0.0.0.0:*    udp    
0.0.0.0:137        0.0.0.0:*    udp    
192.168.1.255:138        0.0.0.0:*    udp    
192.168.1.13:138        0.0.0.0:*    udp    
0.0.0.0:138        0.0.0.0:*    udp    
0.0.0.0:33652        0.0.0.0:*    udp    
0.0.0.0:5353        0.0.0.0:*    udp    
:::5353        :::*    udp6    
:::40333        :::*    udp6    


Routing Table
-------------


-IP routing table-
0.0.0.0 / 192.168.1.1    0.0.0.0    UG    wlan0    
169.254.0.0 / 0.0.0.0    255.255.0.0    U    wlan0    
192.168.1.0 / 0.0.0.0    255.255.255.0    U    wlan0    


ARP Table
---------


-ARP Table-
192.168.1.1    00:1f:95:1c:03:4d    wlan0    


DNS Servers
-----------


-Name servers-


Statistics
----------


-IP-
6432        : Total packets received
4        : With invalid addresses
0        : Incoming packets discarded
0        : Incoming packets discarded
6271        : Incoming packets delivered
4611        : Requests sent out
15        : Dropped because of missing route
-ICMP-
18        : ICMP messages received
14        : Input ICMP message failed.
3126        : ICMP messages sent
0        : ICMP messages failed
-ICMPMSG-
-TCP-
22        : Active connections openings
0        : Bad segments received.
1        : Segments retransmited
0        : Bad segments received.
0        : Bad segments received.
1828        : Segments received
1123        : Segments send out
1        : Segments retransmited
0        : Bad segments received.
532        : Resets sent
-UDP-
486        : Packets received
4014        : Packets to unknown port received.
0        : Packet receive errors
354        : Packets sent
-UDPLITE-
-TCPEXT-
14        : TCP sockets finished time wait in fast timer
16        : Delayed acks sent
553        : Packet headers predicted
32        : Acknowledgments not containing data payload received
10        : Predicted acknowledgments
1        : Connections aborted due to timeout
1        : Connections aborted due to timeout
5        : DSACKs sent for old packets
1        : Connections aborted due to timeout
1        : Connections aborted due to timeout
-IPEXT-


Shared Directories
------------------


-SAMBA-
-NFS-


Benchmarks
**********




CPU Blowfish
------------


-CPU Blowfish-
<big><b>This Machine</b></big>    2001 MHz    8.938    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    


CPU CryptoHash
--------------


-CPU CryptoHash-
<big><b>This Machine</b></big>    2001 MHz    161.055    


CPU Fibonacci
-------------


-CPU Fibonacci-
<big><b>This Machine</b></big>    2001 MHz    4.530    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    


CPU N-Queens
------------


-CPU N-Queens-
<big><b>This Machine</b></big>    2001 MHz    12.238    


FPU FFT
-------


-FPU FFT-
<big><b>This Machine</b></big>    2001 MHz    3.999    


FPU Raytracing
--------------


-FPU Raytracing-
<big><b>This Machine</b></big>    2001 MHz    7.184    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647    

Thanks a lot.

---

### Post by nicolaskokel on 2014-04-10
I downgraded this machine to MINT 13, but then could not even boot any longer.
After the splash screen, I now have a black screen with a blinking cursor and not even the possibility to access the MINT bott screen by pressing and holding 'TAB' or ''SHIFT'.
This computer is totally dead...
Any solution to recover a bootable system?

---

