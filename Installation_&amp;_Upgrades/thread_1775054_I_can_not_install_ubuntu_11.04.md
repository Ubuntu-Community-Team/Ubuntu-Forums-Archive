---
title: "I can not install ubuntu 11.04"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by jjcarles on 2011-06-04
Hi.

 I have installed ubuntu version 9.10. I downloaded the CD version 11.04 but when the install, after the first screen where I select the language, the screen goes black with the cursor in the upper right corner and the computer locked. I tested the installation with two different CD and the result is the same. I've also tested with a CD version 10.04 with the same result.

 I have also tried to update the version with the Package Manager but once I installed the new packages and restarting the computer, the computer is locked, without running the GRUB.

 The information in my computer is:

```

Computer
********


Summary
-------

-Computer-
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
Memory        : 4058MB (651MB used)
Operating System        : Ubuntu 9.10
User Name        : falken (Joan Carles Jimenez)
Date/Time        : Sat 04 Jun 2011 09:34:03 AM CEST
-Display-
Resolution        : 3840x1080 pixels
OpenGL Renderer        : GeForce 210/PCI/SSE2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : NFORCE - NVidia CK804
Audio Adapter        : MPU-401 UART - MPU-401 UART
-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
 G15 Gaming Keyboard
 G15 Gaming Keyboard
 G15 GamePanel LCD
-Printers (CUPS)-
HL-5150D-series        : <i>Default</i>
-SCSI Disks-
ATA ST3160812AS
ATA ST3160812AS
ATA ST3160812AS
ATA ST3160812AS
PHILIPS DVDR1668L1
PHILIPS SPD6005T
ATA ST380011A
Y-E DATA USB   HS-CF Card
Y-E DATA USB   HS-xD/SM
Y-E DATA USB   HS-MS Card
Y-E DATA USB   HS-SD Card

Operating System
----------------

-Version-
Kernel        : Linux 2.6.31-23-generic (x86_64)
Compiled        : #75-Ubuntu SMP Fri Mar 18 18:16:06 UTC 2011
C Library        : GNU C Library version 2.10.1 (stable)
Default C Compiler        : GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
Distribution        : Ubuntu 9.10
-Current Session-
Computer Name        : falken-desktop
User Name        : falken (Joan Carles Jimenez)
Home Directory        : /home/falken
Desktop Environment        : GNOME 2.28.1
-Misc-
Uptime        : 38 minutes
Load Average        : 0.39, 0.79, 0.74

Kernel Modules
--------------

-Loaded Modules-
binfmt_misc
bridge
stp
bnep        : Bluetooth BNEP ver 1.3
vboxnetadp        : Oracle VM VirtualBox Network Adapter Driver
vboxnetflt        : Oracle VM VirtualBox Network Filter Driver
vboxdrv        : Oracle VM VirtualBox Support Driver
snd_intel8x0        : Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7012; Ali 5455
snd_ac97_codec        : Universal interface for Audio Codec &apos;97
ac97_bus
snd_pcm_oss        : PCM OSS emulation for ALSA.
snd_mixer_oss        : Mixer OSS emulation for ALSA.
snd_pcm        : Midlevel PCM code for ALSA.
snd_mpu401        : MPU-401 UART
snd_mpu401_uart        : Routines for control of MPU-401 in UART mode
snd_seq_dummy        : ALSA sequencer MIDI-through client
btusb        : Generic Bluetooth USB driver ver 0.5
usblp        : USB Printer Device Class driver
iptable_filter        : iptables filter table
snd_seq_oss        : OSS-compatible sequencer module
nvidia
snd_seq_midi        : Advanced Linux Sound Architecture sequencer MIDI synth.
ip_tables        : IPv4 packet filter
x_tables        : {ip,ip6,arp,eb}_tables backend module
snd_rawmidi        : Midlevel RawMidi code for ALSA.
snd_seq_midi_event        : MIDI byte &lt;-&gt; sequencer event coder
ppdev
snd_seq        : Advanced Linux Sound Architecture sequencer.
snd_timer        : ALSA timer interface
snd_seq_device        : ALSA sequencer device management
psmouse        : PS/2 mouse driver
amd64_edac_mod        : MC support for AMD64 memory controllers -  Ver: 3.2.0 Mar 18 2011
edac_core        : Core library routines for EDAC reporting
k8temp        : AMD K8 core temperature monitor
serio_raw        : Raw serio driver
parport_pc        : PC-style parallel port driver
lp
ns558        : Classic gameport (ISA/PnP) driver
gameport        : Generic gameport layer
parport
asus_atk0110
snd        : Advanced Linux Sound Architecture driver for soundcards.
soundcore        : Core sound module
snd_page_alloc        : Memory allocator for ALSA system.
i2c_nforce2        : nForce2/3/4/5xx SMBus driver
usb_storage        : USB Mass Storage driver for Linux
usbhid        : USB HID core driver
floppy
forcedeth        : Reverse Engineered nForce ethernet driver

Filesystems
-----------

-Mounted File Systems-
/dev/sda1    /    16.47 % (57.6 GiB of 68.9 GiB)    
udev    /dev    0.02 % (1.9 GiB of 1.9 GiB)    
none    /dev/shm    0.03 % (1.9 GiB of 1.9 GiB)    
none    /var/run    0.00 % (1.9 GiB of 1.9 GiB)    
none    /var/lock    0.00 % (1.9 GiB of 1.9 GiB)    
none    /lib/init/rw    0.00 % (1.9 GiB of 1.9 GiB)    
/dev/sdb1    /home    52.05 % (70.3 GiB of 146.7 GiB)    
/dev/sdc1    /virtual    49.69 % (73.8 GiB of 146.7 GiB)    
/dev/sdd1    /data    92.42 % (11.1 GiB of 146.7 GiB)    
/dev/sda3    /other    5.34 % (64.3 GiB of 68.0 GiB)    

Display
-------

-Display-
Resolution        : 3840x1080 pixels
Vendor        : The X.Org Foundation
Version        : 1.6.4
-Monitors-
Monitor 0        : 1920x1080 pixels
Monitor 1        : 1920x1080 pixels
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
Renderer        : GeForce 210/PCI/SSE2
Version        : 3.0.0 NVIDIA 185.18.36
Direct Rendering        : Yes

Environment Variables
---------------------

-Environment Variables-
ORBIT_SOCKETDIR        : /tmp/orbit-falken
SSH_AGENT_PID        : 2307
GPG_AGENT_INFO        : /tmp/seahorse-bzeR6P/S.gpg-agent:2330:1
TERM        : xterm
SHELL        : /bin/bash
XDG_SESSION_COOKIE        : 36038ceece7b0974ad8422ad4dde44c8-1307170580.226452-1734798701
GTK_RC_FILES        : /etc/gtk/gtkrc:/home/falken/.gtkrc-1.2-gnome2
WINDOWID        : 71303172
GTK_MODULES        : canberra-gtk-module
USER        : falken
LS_COLORS        : rs=0:di=01;34:ln=01;36:hl=44;37:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
GNOME_KEYRING_SOCKET        : /tmp/keyring-IMPE9W/socket
SSH_AUTH_SOCK        : /tmp/keyring-IMPE9W/socket.ssh
SESSION_MANAGER        : local/falken-desktop:@/tmp/.ICE-unix/2265,unix/falken-desktop:/tmp/.ICE-unix/2265
USERNAME        : falken
DESKTOP_SESSION        : gnome
PATH        : /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD        : /home/falken
GDM_KEYBOARD_LAYOUT        : es
LANG        : en_US.UTF-8
GNOME_KEYRING_PID        : 2250
GDM_LANG        : en_US.UTF-8
GDMSESSION        : gnome
HISTCONTROL        : ignoreboth
SPEECHD_PORT        : 7560
SHLVL        : 1
HOME        : /home/falken
GNOME_DESKTOP_SESSION_ID        : this-is-deprecated
LOGNAME        : falken
XDG_DATA_DIRS        : /usr/share/gnome:/usr/local/share/:/usr/share/
DBUS_SESSION_BUS_ADDRESS        : unix:abstract=/tmp/dbus-98mmsxu9eG,guid=61f12dfc45a1cda4f076a1e34de9d715
LESSOPEN        : | /usr/bin/lesspipe %s
DISPLAY        : :0.0
LESSCLOSE        : /usr/bin/lesspipe %s %s
XAUTHORITY        : /var/run/gdm/auth-for-falken-fGO6Z8/database
COLORTERM        : gnome-terminal
_        : /usr/bin/hardinfo

Processor
---------

-Processors-
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+        : 1000.00MHz
AMD Athlon(tm) 64 X2 Dual Core Processor 4200+        : 1000.00MHz

Memory
------

-Memory-
Total Memory        : 4058856 kB
Free Memory        : 2819956 kB
Buffers        : 163916 kB
Cached        : 587988 kB
Cached Swap        : 0 kB
Active        : 548980 kB
Inactive        : 440936 kB
Active(anon)        : 243120 kB
Inactive(anon)        : 16 kB
Active(file)        : 305860 kB
Inactive(file)        : 440920 kB
Unevictable        : 0 kB
Mlocked        : 0 kB
Virtual Memory        : 10482404 kB
Free Virtual Memory        : 10482404 kB
Dirty        : 120 kB
Writeback        : 0 kB
AnonPages        : 238012 kB
Mapped        : 75180 kB
Slab        : 104328 kB
SReclaimable        : 84536 kB
SUnreclaim        : 19792 kB
PageTables        : 20596 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 12511832 kB
Committed_AS        : 767216 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 317732 kB
VmallocChunk        : 34359417851 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 122816 kB
DirectMap2M        : 4071424 kB

PCI Devices
-----------

-PCI Devices-
Memory controller        : nVidia Corporation CK804 Memory Controller 
ISA bridge        : nVidia Corporation CK804 ISA Bridge 
SMBus        : nVidia Corporation CK804 SMBus 
USB Controller        : nVidia Corporation CK804 USB Controller 
USB Controller        : nVidia Corporation CK804 USB Controller 
Multimedia audio controller        : nVidia Corporation CK804 AC'97 Audio Controller 
IDE interface        : nVidia Corporation CK804 IDE 
IDE interface        : nVidia Corporation CK804 Serial ATA Controller 
IDE interface        : nVidia Corporation CK804 Serial ATA Controller 
PCI bridge        : nVidia Corporation CK804 PCI Bridge 
Bridge        : nVidia Corporation CK804 Ethernet Controller 
PCI bridge        : nVidia Corporation CK804 PCIE Bridge 
PCI bridge        : nVidia Corporation CK804 PCIE Bridge 
PCI bridge        : nVidia Corporation CK804 PCIE Bridge 
PCI bridge        : nVidia Corporation CK804 PCIE Bridge 
Host bridge        : Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
Host bridge        : Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
Host bridge        : Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
Host bridge        : Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
VGA compatible controller        : nVidia Corporation GT200 [GeForce 210] 
Audio device        : nVidia Corporation Device 0be3 
Multimedia video controller        : Device 1a0a:6200 
Serial controller        : Timedia Technology Co Ltd PCI2S550 
USB Controller        : VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
USB Controller        : VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
USB Controller        : VIA Technologies, Inc. USB 2.0 

USB Devices
-----------


Printers
--------

-Printers (CUPS)-
HL-5150D-series        : <i>Default</i>

Sensors
-------

-ACPI Thermal Zone-
THRM        : 40°C

Input Devices
-------------

-Input Devices-
 Power Button
 Power Button
 Macintosh mouse button emulation
 Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
 G15 Gaming Keyboard
 G15 Gaming Keyboard
 G15 GamePanel LCD

Storage
-------

-SCSI Disks-
ATA ST3160812AS
ATA ST3160812AS
ATA ST3160812AS
ATA ST3160812AS
PHILIPS DVDR1668L1
PHILIPS SPD6005T
ATA ST380011A
Y-E DATA USB   HS-CF Card
Y-E DATA USB   HS-xD/SM
Y-E DATA USB   HS-MS Card
Y-E DATA USB   HS-SD Card

DMI
---

-BIOS-
Date        : 04/07/2006
Vendor        : Phoenix Technologies, LTD
Version        : ASUS A8N-E ACPI BIOS Revision 1013
-Board-
Name        : A8N-E
Vendor        : ASUSTeK Computer INC.

Resources
---------

-I/O Ports-
<tt>0000-001f </tt>        : dma1
<tt>0020-0021 </tt>        : pic1
<tt>0040-0043 </tt>        : timer0
<tt>0050-0053 </tt>        : timer1
<tt>0060-0060 </tt>        : keyboard
<tt>0064-0064 </tt>        : keyboard
<tt>0070-0073 </tt>        : rtc0
<tt>0080-008f </tt>        : dma page reg
<tt>00a0-00a1 </tt>        : pic2
<tt>00c0-00df </tt>        : dma2
<tt>00f0-00ff </tt>        : fpu
<tt>0170-0177 </tt>        : nVidia Corporation CK804 IDE 
<tt>  0170-0177 </tt>        : pata_amd
<tt>01f0-01f7 </tt>        : nVidia Corporation CK804 IDE 
<tt>  01f0-01f7 </tt>        : pata_amd
<tt>0201-0201 </tt>        : ns558-pnp
<tt>0290-0297 </tt>        : pnp 00:02
<tt>0330-0331 </tt>        : MPU401 UART
<tt>0376-0376 </tt>        : nVidia Corporation CK804 IDE 
<tt>  0376-0376 </tt>        : pata_amd
<tt>0378-037a </tt>        : parport0
<tt>03c0-03df </tt>        : vga+
<tt>03f2-03f2 </tt>        : floppy
<tt>03f4-03f5 </tt>        : floppy
<tt>03f6-03f6 </tt>        : nVidia Corporation CK804 IDE 
<tt>  03f6-03f6 </tt>        : pata_amd
<tt>03f7-03f7 </tt>        : floppy
<tt>03f8-03ff </tt>        : serial
<tt>04d0-04d1 </tt>        : pnp 00:02
<tt>0778-077a </tt>        : parport0
<tt>0800-087f </tt>        : pnp 00:02
<tt>0960-0967 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  0960-0967 </tt>        : sata_nv
<tt>0970-0977 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  0970-0977 </tt>        : sata_nv
<tt>09e0-09e7 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  09e0-09e7 </tt>        : sata_nv
<tt>09f0-09f7 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  09f0-09f7 </tt>        : sata_nv
<tt>0b60-0b63 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  0b60-0b63 </tt>        : sata_nv
<tt>0b70-0b73 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  0b70-0b73 </tt>        : sata_nv
<tt>0be0-0be3 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  0be0-0be3 </tt>        : sata_nv
<tt>0bf0-0bf3 </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  0bf0-0bf3 </tt>        : sata_nv
<tt>0cf8-0cff </tt>        : PCI conf1
<tt>4000-407f </tt>        : pnp 00:01
<tt>  4000-4003 </tt>        : ACPI PM1a_EVT_BLK
<tt>  4004-4005 </tt>        : ACPI PM1a_CNT_BLK
<tt>  4008-400b </tt>        : ACPI PM_TMR
<tt>  401c-401c </tt>        : ACPI PM2_CNT_BLK
<tt>  4020-4027 </tt>        : ACPI GPE0_BLK
<tt>4080-40ff </tt>        : pnp 00:01
<tt>4400-447f </tt>        : pnp 00:01
<tt>4480-44ff </tt>        : pnp 00:01
<tt>  44a0-44af </tt>        : ACPI GPE1_BLK
<tt>4800-487f </tt>        : pnp 00:01
<tt>4880-48ff </tt>        : pnp 00:01
<tt>4c00-4c3f </tt>        : nVidia Corporation CK804 SMBus 
<tt>  4c00-4c3f </tt>        : nForce2_smbus
<tt>4c40-4c7f </tt>        : nVidia Corporation CK804 SMBus 
<tt>  4c40-4c7f </tt>        : nForce2_smbus
<tt>9000-9fff </tt>        : PCI Bus 0000:01
<tt>  9000-907f </tt>        : nVidia Corporation GT200 [GeForce 210] 
<tt>a000-afff </tt>        : PCI Bus 0000:05
<tt>  a000-a01f </tt>        : Timedia Technology Co Ltd PCI2S550 
<tt>    a000-a007 </tt>        : serial
<tt>    a008-a00f </tt>        : serial
<tt>  a400-a41f </tt>        : VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
<tt>    a400-a41f </tt>        : uhci_hcd
<tt>  a800-a81f </tt>        : VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller 
<tt>    a800-a81f </tt>        : uhci_hcd
<tt>b000-b007 </tt>        : nVidia Corporation CK804 Ethernet Controller 
<tt>  b000-b007 </tt>        : Reverse Engineered nForce ethernet driver
<tt>c400-c40f </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  c400-c40f </tt>        : sata_nv
<tt>d800-d80f </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  d800-d80f </tt>        : sata_nv
<tt>dc00-dcff </tt>        : nVidia Corporation CK804 AC'97 Audio Controller 
<tt>  dc00-dcff </tt>        : NVidia CK804
<tt>e000-e0ff </tt>        : nVidia Corporation CK804 AC'97 Audio Controller 
<tt>  e000-e0ff </tt>        : NVidia CK804
<tt>e400-e41f </tt>        : nVidia Corporation CK804 SMBus 
<tt>f000-f00f </tt>        : nVidia Corporation CK804 IDE 
<tt>  f000-f00f </tt>        : pata_amd
-Memory-
<tt>00000000-0000ffff </tt>        : reserved
<tt>00010000-0009f3ff </tt>        : System RAM
<tt>0009f400-0009ffff </tt>        : reserved
<tt>000f0000-000fffff </tt>        : reserved
<tt>00100000-9ffeffff </tt>        : System RAM
<tt>  01000000-0153586b </tt>        : Kernel code
<tt>  0153586c-01827daf </tt>        : Kernel data
<tt>  018dc000-019ebe8b </tt>        : Kernel bss
<tt>  20000000-23ffffff </tt>        : GART
<tt>9fff0000-9fff2fff </tt>        : ACPI Non-volatile Storage
<tt>9fff3000-9fffffff </tt>        : ACPI Tables
<tt>a0000000-bfffffff </tt>        : PCI Bus 0000:01
<tt>  a0000000-afffffff </tt>        : nVidia Corporation GT200 [GeForce 210] 
<tt>  b0000000-b1ffffff </tt>        : nVidia Corporation GT200 [GeForce 210] 
<tt>c0000000-c2ffffff </tt>        : PCI Bus 0000:01
<tt>  c0000000-c0ffffff </tt>        : nVidia Corporation GT200 [GeForce 210] 
<tt>    c0000000-c0ffffff </tt>        : nvidia
<tt>  c1000000-c107ffff </tt>        : nVidia Corporation GT200 [GeForce 210] 
<tt>  c2000000-c2003fff </tt>        : nVidia Corporation Device 0be3 
<tt>c3000000-c30fffff </tt>        : PCI Bus 0000:03
<tt>  c3000000-c3007fff </tt>        : Device 1a0a:6200 
<tt>c3100000-c31fffff </tt>        : PCI Bus 0000:05
<tt>  c3100000-c31000ff </tt>        : VIA Technologies, Inc. USB 2.0 
<tt>    c3100000-c31000ff </tt>        : ehci_hcd
<tt>c3200000-c3200fff </tt>        : nVidia Corporation CK804 Ethernet Controller 
<tt>  c3200000-c3200fff </tt>        : Reverse Engineered nForce ethernet driver
<tt>c3201000-c3201fff </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  c3201000-c3201fff </tt>        : sata_nv
<tt>c3202000-c3202fff </tt>        : nVidia Corporation CK804 Serial ATA Controller 
<tt>  c3202000-c3202fff </tt>        : sata_nv
<tt>c3203000-c3203fff </tt>        : nVidia Corporation CK804 AC'97 Audio Controller 
<tt>  c3203000-c3203fff </tt>        : NVidia CK804
<tt>c3204000-c3204fff </tt>        : nVidia Corporation CK804 USB Controller 
<tt>  c3204000-c3204fff </tt>        : ohci_hcd
<tt>e0000000-efffffff </tt>        : PCI MMCONFIG 0 [00-ff]
<tt>  e0000000-efffffff </tt>        : reserved
<tt>    e0000000-efffffff </tt>        : pnp 00:0c
<tt>feb00000-feb000ff </tt>        : nVidia Corporation CK804 USB Controller 
<tt>  feb00000-feb000ff </tt>        : ehci_hcd
<tt>fec00000-ffffffff </tt>        : reserved
<tt>  fec00000-fec00fff </tt>        : IOAPIC 0
<tt>  fee00000-feefffff </tt>        : pnp 00:0d
<tt>    fee00000-fee00fff </tt>        : Local APIC
<tt>  fefff000-feffffff </tt>        : pnp 00:0d
<tt>  fff80000-fff80fff </tt>        : pnp 00:0d
<tt>  fff90000-fffbffff </tt>        : pnp 00:0d
<tt>  fffed000-fffeffff </tt>        : pnp 00:0d
<tt>  ffff0000-ffffffff </tt>        : pnp 00:0d
<tt>100000000-15fffffff </tt>        : System RAM
-DMA-
<tt> 2</tt>        : floppy
<tt> 3</tt>        : parport0
<tt> 4</tt>        : cascade

Interfaces
----------

-Network Interfaces-
lo    0.01MiB    0.01MiB    127.0.0.1    
eth0    2.96MiB    0.37MiB    192.168.1.10    
vboxnet0    0.00MiB    0.00MiB        
pan0    0.00MiB    0.00MiB        

Benchmarks
**********


CPU Blowfish
------------

-CPU Blowfish-
<big><b>This Machine</b></big>    1000 MHz    8.150    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    26.1876862    
PowerPC 740/750 (280.00MHz)    (null)    172.816713    

CPU CryptoHash
--------------

-CPU Cryptohash-
<big><b>This Machine</b></big>    1000 MHz    145.156    

CPU Fibonacci
-------------

-CPU Fibonacci-
<big><b>This Machine</b></big>    1000 MHz    3.304    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    8.1375674    
PowerPC 740/750 (280.00MHz)    (null)    58.07682    

CPU N-Queens
------------

-CPU N-Queens-
<big><b>This Machine</b></big>    1000 MHz    17.174    

FPU FFT
-------

-FPU FFT-
<big><b>This Machine</b></big>    1000 MHz    7.742    

FPU Raytracing
--------------

-FPU Raytracing-
<big><b>This Machine</b></big>    1000 MHz    13.610    
Intel(R) Celeron(R) M processor         1.50GHz    (null)    40.8816714    
PowerPC 740/750 (280.00MHz)    (null)    161.312647    

```
Can you help? Thanks in advance.

---

### Post by mörgæs on 2011-06-04
Hi, welcome to the fora.

It sounds like you need boot options. There are some links for it here: 
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

