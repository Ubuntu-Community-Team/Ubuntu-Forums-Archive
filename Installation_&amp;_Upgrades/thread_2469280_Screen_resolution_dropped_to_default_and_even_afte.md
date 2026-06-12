---
title: "Screen resolution dropped to default and even after reinstall reverts"
date: 2021-11-24
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2021-11-24
I have an odd one here.  My PC was running 21.04 and is left on 24/7 and only accessed via machines on the LAN for common files.  I noted about 4 days ago that I couldn't upload or change files so took a gander only to find the whole screen frozen.  I could do nothing with keys or mouse other than moving the cursor about.  I resorted to powering off.  When I rebooted the screen resolution was default with no options and the Additional Drivers was empty.  I did an upgrade to 21.10 along with many other upgrades and online Googled fixes that didn't work.  Spent all day yesterday trying to resolve and ended up this am doing a fresh install of 21.10 via USB, but again there were no Additional Drivers though screen resolution was fine.  After a reboot, it has reverted to Default again.

Anyone able to assist.  The video card is ```
NVIDIA Corporation GT218 [GeForce 210] (rev a2
```

---

### Post by ActionParsnip on 2021-11-24
Why do you have a GUI on a system that's running as a server? It's more to go wrong...

---

### Post by Jonners59 on 2021-11-24
I am not competent enough to run a server.  I need the GUI.  :-)

---

### Post by MAFoElffen on 2021-11-26
I could ask a lot of questions... 

What might be easier would be to have you run the Forum's 'system-info" script in my signature line. That will tell us, among other things about information on your hardware, settings, what the original installation media was, what graphics settings are configured, and set as.... such as the Desktop Environment that you installed for it. That would be a good start.

---

### Post by Jonners59 on 2021-11-26
> **MAFoElffen said:**
> I could ask a lot of questions... 

What might be easier would be to have you run the Forum's 'system-info" script in my signature line. That will tell us, among other things about the information on your hardware, settings, what the original installation media was, what graphics settings are configured, and set as.... such as the Desktop Environment that you installed for it. That would be a good start.

I don't know about that script.  Did do a search, but I have system info that gives this lot (I took a lot out)  BUT does it help at all.  I know I have an NVIDIA GeForce GT210 card, but no Additional Drivers listed inc X-Org...

```
Computer
Summary
Computer
Processor    AMD FX(tm)-8350 Eight-Core Processor
Memory    16220MB (3029MB used)
Machine Type    Desktop
Operating System    Ubuntu 21.10
User Name    administration (administration)
Date/Time    Fri 26 Nov 2021 10:51:00 GMT
Display
Resolution    1280x1024 pixels
OpenGL Renderer    NVA8
X11 Vendor    The X.Org Foundation
Audio Devices
Audio Adapter    HDA-Intel - HDA ATI SB
Audio Adapter    CX88x - Conexant CX8811
Audio Adapter    HDA-Intel - HDA NVidia
Input Devices
Power Button    
Power Button    
Logitech USB Optical Mouse    
Logitech K230    
NOVATEK USB Keyboard    
NOVATEK USB Keyboard System Control    
NOVATEK USB Keyboard Consumer Control    
NOVATEK USB Keyboard    
Eee PC WMI hotkeys    
HDA NVidia HDMI/DP,pcm:3    
HDA NVidia HDMI/DP,pcm:7    
HDA NVidia HDMI/DP,pcm:8    
HDA NVidia HDMI/DP,pcm:9    
HDA ATI SB Front Mic    
HDA ATI SB Rear Mic    
HDA ATI SB Line    
HDA ATI SB Line Out    
HDA ATI SB Front Headphone    
Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder    
Printers
No printers found    
SCSI Disks
ATA ST500DM002-1BD14    
ATA WDC WD40EZRZ-00G    
ATA WDC WD40EZRZ-00G    
HL-DT-ST DVDRAM GSA-H66N    
TO Exter nal USB 3.0    
Operating System
Version
Kernel    Linux 5.13.0-21-generic (x86_64)
Version    #21-Ubuntu SMP Tue Oct 19 08:59:28 UTC 2021
C Library    GNU C Library / (Ubuntu GLIBC 2.34-0ubuntu3) 2.34
Distribution    Ubuntu 21.10
Current Session
Computer Name    store
User Name    administration (administration)
Language    en_GB.UTF-8 (en_GB:en)
Home Directory    /home/administration
Misc
Uptime    44 minutes
Load Average    0.51, 1.07, 0.84
Available entropy in /dev/random    3822 bits (healthy)
Kernel Modules
Loaded Modules
xfrm_user    
xfrm_algo    
vboxnetadp    Oracle VM VirtualBox Network Adapter Driver
vboxnetflt    Oracle VM VirtualBox Network Filter Driver
vboxdrv    Oracle VM VirtualBox Support Driver
nls_iso8859_1    
si2157    Silicon Labs Si2141/Si2146/2147/2148/2157/2158 silicon tuner driver
si2168    Silicon Labs Si2168 DVB-T/T2/C demodulator driver
ts2020    Montage Technology TS2020 - Silicon tuner driver module
cx88_blackbird    driver for cx2388x/cx23416 based mpeg encoder cards
joydev    Joystick device interfaces
input_leds    Input -> LEDs Bridge
rc_hauppauge    
ir_kbd_i2c    input driver for i2c IR remote controls
snd_soc_wm8776    ASoC WM8776 driver
cx22702    Conexant CX22702 DVB-T Demodulator driver
snd_soc_core    ALSA SoC Core
snd_compress    ALSA Compressed offload framework
ac97_bus    
cx88_vp3054_i2c    driver for cx2388x VP3054 design
snd_pcm_dmaengine    
wm8775    wm8775 driver
tuner_simple    Simple 4-control-bytes style tuner driver
tuner_types    Simple tuner device type database
tda9887    
cx25840    Conexant CX25840 audio/video decoder driver
tda8290    Philips/NXP TDA8290/TDA8295 analog IF demodulator driver
snd_hda_codec_realtek    Realtek HD-audio codec
snd_hda_codec_generic    Generic HD-audio codec parser
cx23885    v4l2 driver module for cx23885 based TV cards
altera_ci    altera FPGA CI module
tda18271    NXP TDA18271HD analog / digital tuner driver
ledtrig_audio    LED trigger for audio mute control
altera_stapl    altera FPGA kernel module
m88ds3103    Montage Technology M88DS3103 DVB-S/S2 demodulator driver
snd_hda_codec_hdmi    HDMI HD-audio codec
tuner    device driver for various TV and TV+FM radio tuners
snd_hda_intel    Intel HDA driver
snd_intel_dspcfg    Intel DSP config driver
snd_intel_sdw_acpi    Intel Soundwire ACPI helpers
cx2341x    cx23415/6/8 driver
snd_hda_codec    HDA codec core
videobuf2_dvb    
snd_hda_core    HD-audio bus
dvb_core    DVB Core Driver
edac_mce_amd    AMD MCE decoder
i2c_mux    I2C driver for multiplexed I2C busses
cx88_alsa    ALSA driver module for cx2388x based TV cards
snd_hwdep    Hardware dependent layer
cx8802    mpeg driver for cx2388x based TV cards
cx8800    v4l2 driver module for cx2388x based TV cards
cx88xx    v4l2 driver module for cx2388x based TV cards
snd_pcm    Midlevel PCM code for ALSA.
kvm_amd    
snd_seq_midi    Advanced Linux Sound Architecture sequencer MIDI synth.
snd_seq_midi_event    MIDI byte <-> sequencer event coder
ccp    AMD Secure Processor driver
videobuf2_dma_sg    dma scatter/gather memory handling routines for videobuf2
videobuf2_memops    common memory handling routines for videobuf2
tveeprom    i2c Hauppauge eeprom decoder driver
eeepc_wmi    Eee PC WMI Hotkey Driver
snd_rawmidi    Midlevel RawMidi code for ALSA.
kvm    
videobuf2_v4l2    Driver helper framework for Video for Linux 2
videobuf2_common    Media buffer core framework
snd_seq    Advanced Linux Sound Architecture sequencer.
efi_pstore    EFI variable backend for pstore
snd_seq_device    ALSA sequencer device management
videodev    Video4Linux2 core driver
snd_timer    ALSA timer interface
mc    Device node registration for media drivers
snd    Advanced Linux Sound Architecture driver for soundcards.
soundcore    Core sound module
wmi_bmof    WMI embedded Binary MOF driver
fam15h_power    AMD Family 15h CPU processor power monitor
k10temp    AMD Family 10h+ CPU core temperature monitor
mac_hid    
ip6t_REJECT    Xtables: packet "rejection" target for IPv6
nf_reject_ipv6    
xt_hl    Xtables: Hoplimit/TTL field match
ip6_tables    IPv6 packet filter
ip6t_rt    Xtables: IPv6 Routing Header match
ipt_REJECT    Xtables: packet "rejection" target for IPv4
nf_reject_ipv4    
xt_LOG    Xtables: IPv4/IPv6 packet logging
nf_log_syslog    Netfilter syslog packet logging
nft_limit    nftables limit expression support
xt_limit    Xtables: rate-limit match
sch_fq_codel    Fair Queue CoDel discipline
xt_addrtype    Xtables: address type match
xt_tcpudp    Xtables: TCP, UDP and UDP-Lite match
nf_nat_pptp    Netfilter NAT helper module for PPTP
nf_conntrack_pptp    Netfilter connection tracking helper module for PPTP
xt_conntrack    Xtables: connection tracking state match
nf_nat    
nft_compat    x_tables over nftables support
nf_conntrack    
nf_defrag_ipv6    
nf_defrag_ipv4    
nft_counter    nftables counter rule support
msr    x86 generic MSR driver
nf_tables    
parport_pc    PC-style parallel port driver
libcrc32c    CRC32c (Castagnoli) calculations
ppdev    
nfnetlink    Netfilter messages via netlink socket
lp    
parport    
ip_tables    IPv4 packet filter
x_tables    {ip,ip6,arp,eb}_tables backend module
autofs4    
hid_logitech_hidpp    
uas    
usb_storage    USB Mass Storage driver for Linux
hid_logitech_dj    
hid_generic    HID generic driver
usbhid    USB HID core driver
hid    
nouveau    nVidia Riva/TNT/GeForce/Quadro/Tesla/Tegra K1+
i2c_algo_bit    I2C-Bus bit-banging algorithm
drm_ttm_helper    DRM gem ttm helpers
ttm    TTM memory manager subsystem (for DRM device)
drm_kms_helper    DRM KMS helper
syscopyarea    Generic copyarea (sys-to-sys)
sysfillrect    Generic fill rectangle (sys-to-sys)
sysimgblt    1-bit/8-bit to 1-32 bit color expansion (sys-to-sys)
fb_sys_fops    Generic file read (fb in system RAM)
cec    Device node registration for cec drivers
rc_core    
drm    DRM shared core routines
mfd_aaeon    AAEON Board WMI driver
asus_wmi    Asus Generic WMI Driver
sparse_keymap    Generic support for sparse keymaps
mxm_wmi    MXM WMI Driver
video    ACPI Video Driver
crct10dif_pclmul    T10 DIF CRC calculation accelerated with PCLMULQDQ.
crc32_pclmul    
ghash_clmulni_intel    GHASH hash function, accelerated by PCLMULQDQ-NI
aesni_intel    Rijndael (AES) Cipher Algorithm, Intel AES-NI instructions optimized
crypto_simd    
cryptd    Software async crypto daemon
ahci    AHCI SATA low-level driver
r8169    RealTek RTL-8169 Gigabit Ethernet driver
xhci_pci    xHCI PCI Host Controller Driver
i2c_piix4    PIIX4 SMBus driver
libahci    Common AHCI SATA low-level routines
xhci_pci_renesas    
realtek    Realtek PHY driver
wmi    ACPI-WMI Mapping Driver

Filesystems
Mounted File Systems
udev    /dev    0.00 % (7.7 GiB of 7.7 GiB)
tmpfs    /run    0.23 % (1.5 GiB of 1.5 GiB)
/dev/sda2    /    24.41 % (57.6 GiB of 76.2 GiB)
tmpfs    /dev/shm    0.05 % (7.7 GiB of 7.7 GiB)
tmpfs    /run/lock    0.08 % (5.0 MiB of 5.0 MiB)
/dev/loop0    /snap/bare/5    100.00 % (0.0 B of 128.0 KiB)
/dev/loop4    /snap/firefox/631    100.00 % (0.0 B of 150.5 MiB)
/dev/loop2    /snap/snap-store/557    100.00 % (0.0 B of 54.2 MiB)
/dev/loop5    /snap/core/11743    100.00 % (0.0 B of 99.4 MiB)
/dev/loop1    /snap/gnome-3-38-2004/76    100.00 % (0.0 B of 242.4 MiB)
/dev/loop6    /snap/gtk-common-themes/1519    100.00 % (0.0 B of 65.2 MiB)
/dev/loop3    /snap/core20/1169    100.00 % (0.0 B of 61.9 MiB)
/dev/loop7    /snap/snap-store/558    100.00 % (0.0 B of 54.2 MiB)
/dev/loop8    /snap/core/11993    100.00 % (0.0 B of 99.5 MiB)
/dev/loop9    /snap/firefox/731    100.00 % (0.0 B of 152.4 MiB)
/dev/loop10    /snap/core20/1242    100.00 % (0.0 B of 61.9 MiB)
/dev/loop11    /snap/gnome-3-38-2004/87    100.00 % (0.0 B of 248.0 MiB)
/dev/sdd2    /media/3CXExt    98.95 % (9.1 GiB of 867.9 GiB)
/dev/sdb1    /media/Backup    30.57 % (2.5 TiB of 3.6 TiB)
/dev/sdc1    /media/Documents    32.00 % (2.4 TiB of 3.6 TiB)
/dev/sda3    /home    5.53 % (135.6 GiB of 143.5 GiB)
/dev/sda1    /boot/efi    0.14 % (5.6 GiB of 5.6 GiB)
/dev/sda5    /home/administration/VirtualBox    39.23 % (110.9 GiB of 182.5 GiB)
/dev/sda6    /home/administration/.VirtualBox    5.25 % (45.3 GiB of 47.8 GiB)
tmpfs    /run/user/1000    0.30 % (1.5 GiB of 1.5 GiB)
tmpfs    /run/snapd/ns    0.23 % (1.5 GiB of 1.5 GiB)
Display
Display
Resolution    1280x1024 pixels
Vendor    The X.Org Foundation
Version    1.21.1.2
Current Display Name    :0
Monitors
Monitor 0    1280x1024 pixels
OpenGL
Vendor    nouveau
Renderer    NVA8
Version    3.3 (Compatibility Profile) Mesa 21.2.2
Direct Rendering    Yes
Extensions
Composite    
DAMAGE    
DOUBLE-BUFFER    
DRI3    
GLX    
Generic Event Extension    
MIT-SHM    
Present    
RANDR    
RECORD    
RENDER    
SHAPE    
SYNC    
X-Resource    
XC-MISC    
XFIXES    
XFree86-VidModeExtension    
XINERAMA    
XInputExtension    
XKEYBOARD    
XTEST    
XVideo    
default screen number: 0    
Environment Variables
Environment Variables
GJS_DEBUG_TOPICS    JS ERROR;JS LOG
LANGUAGE    en_GB:en
USER    administration
XDG_SESSION_TYPE    wayland
SHLVL    0
HOME    /home/administration
DESKTOP_SESSION    ubuntu
GIO_LAUNCHED_DESKTOP_FILE    /usr/share/applications/hardinfo.desktop
GTK_MODULES    gail:atk-bridge:appmenu-gtk-module:appmenu-gtk-module
GNOME_SHELL_SESSION_MODE    ubuntu
MANAGERPID    1557
SYSTEMD_EXEC_PID    1691
DBUS_SESSION_BUS_ADDRESS    unix:path=/run/user/1000/bus
GIO_LAUNCHED_DESKTOP_FILE_PID    6128
UBUNTU_MENUPROXY    1
IM_CONFIG_PHASE    1
WAYLAND_DISPLAY    wayland-0
LOGNAME    administration
_    /usr/bin/gnome-session
JOURNAL_STREAM    8:30971
XDG_SESSION_CLASS    user
USERNAME    administration
GNOME_DESKTOP_SESSION_ID    this-is-deprecated
PATH    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
SESSION_MANAGER    local/store:@/tmp/.ICE-unix/1672,unix/store:/tmp/.ICE-unix/1672
INVOCATION_ID    1bd8244d807946d186884e0a21de432c
XDG_RUNTIME_DIR    /run/user/1000
XDG_MENU_PREFIX    gnome-
GNOME_SETUP_DISPLAY    :1
DISPLAY    :0
LANG    en_GB.UTF-8
XDG_CURRENT_DESKTOP    ubuntu:GNOME
XDG_SESSION_DESKTOP    ubuntu
XMODIFIERS    @im=ibus
XAUTHORITY    /run/user/1000/.mutter-Xwaylandauth.VV4MD1
SSH_AGENT_LAUNCHER    gnome-keyring
SSH_AUTH_SOCK    /run/user/1000/keyring/ssh
SHELL    /bin/bash
QT_ACCESSIBILITY    1
GDMSESSION    ubuntu
GJS_DEBUG_OUTPUT    stderr
QT_IM_MODULE    ibus
PWD    /home/administration
XDG_DATA_DIRS    /usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
XDG_CONFIG_DIRS    /etc/xdg/xdg-ubuntu:/etc/xdg
Development
Scripting Languages
Gambas3 (gbr3)    Not found
Python    Not found
Python2    Not found
Python3    3.9.7
Perl    5.32.1
Perl6 (VM)    Not found
Perl6    Not found
PHP    Not found
Ruby    2.7.4
Bash    5.1.8(1)-release
Compilers
C (GCC)    11.2.0
C (Clang)    Not found
D (dmd)    Not found
Gambas3 (gbc3)    Not found
Java    Not found
CSharp (Mono, old)    Not found
CSharp (Mono)    Not found
Vala    Not found
Haskell (GHC)    Not found
FreePascal    Not found
Go    Not found
Tools
make    4.3
GDB    (Ubuntu 11.1-0ubuntu2) 11.1
strace    5.13
valgrind    Not found
QMake    Not found
CMake    Not found
Gambas3 IDE    Not found
Users
Users
root    root
daemon    daemon
bin    bin
sys    sys
sync    sync
games    games
man    man
lp    lp
mail    mail
news    news
uucp    uucp
proxy    proxy
www-data    www-data
backup    backup
list    Mailing List Manager
irc    ircd
gnats    Gnats Bug-Reporting System (admin)
nobody    nobody
systemd-network    systemd Network Management
systemd-resolve    systemd Resolver
systemd-timesync    systemd Time Synchronization
messagebus    
syslog    
_apt    
tss    TPM software stack
uuidd    
tcpdump    
avahi-autoipd    Avahi autoip daemon
usbmux    usbmux daemon
rtkit    RealtimeKit
dnsmasq    dnsmasq
kernoops    Kernel Oops Tracking Daemon
avahi    Avahi mDNS daemon
cups-pk-helper    user for cups-pk-helper service
whoopsie    
sssd    SSSD system user
speech-dispatcher    Speech Dispatcher
nm-openvpn    NetworkManager OpenVPN
saned    
colord    colord colour management daemon
geoclue    
pulse    PulseAudio daemon
gnome-initial-setup    
hplip    HPLIP system user
gdm    Gnome Display Manager
administration    administration
systemd-coredump    systemd Core Dumper
sshd    
ntp    
bind    
lightdm    Light Display Manager
sddm    Simple Desktop Display Manager
stunnel4    
minidlna    MiniDLNA server
strongswan    
Groups
Group
root    0
daemon    1
bin    2
sys    3
adm    4
tty    5
disk    6
lp    7
mail    8
news    9
uucp    10
man    12
proxy    13
kmem    15
dialout    20
fax    21
voice    22
cdrom    24
floppy    25
tape    26
sudo    27
audio    29
dip    30
www-data    33
backup    34
operator    37
list    38
irc    39
src    40
gnats    41
shadow    42
utmp    43
video    44
sasl    45
plugdev    46
staff    50
games    60
users    100
nogroup    65534
systemd-journal    101
systemd-network    102
systemd-resolve    103
systemd-timesync    104
crontab    105
messagebus    106
input    107
sgx    108
kvm    109
render    110
syslog    111
tss    112
bluetooth    113
ssl-cert    114
uuidd    115
tcpdump    116
_ssh    117
avahi-autoipd    118
rtkit    119
netdev    120
avahi    121
lpadmin    122
whoopsie    123
sssd    124
nm-openvpn    125
scanner    126
saned    127
colord    128
geoclue    129
pulse    130
pulse-access    131
gdm    132
lxd    133
administration    1000
sambashare    134
systemd-coredump    999
rdma    135
winbindd_priv    136
vboxsf    137
ntp    138
bind    139
mlocate    140
lightdm    141
nopasswdlogin    142
sddm    143
vboxusers    144
stunnel4    145
minidlna    146
Devices
Processor
Processors
Package Information
AMD FX(tm)-8350 Eight-Core Processor    0    0:0    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    1    0:1    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    2    0:2    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    3    0:3    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    4    0:4    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    5    0:5    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    6    0:6    4000.00 MHz
AMD FX(tm)-8350 Eight-Core Processor    7    0:7    4000.00 MHz
Memory
Memory
MemTotal    Total Memory    16220132 KiB
MemFree    Free Memory    12130524 KiB
MemAvailable        13994180 KiB
Buffers        168992 KiB
Cached        1944608 KiB
SwapCached    Cached Swap    0 KiB
Active        1019148 KiB
Inactive        2682212 KiB
Active(anon)        3208 KiB
Inactive(anon)        1645144 KiB
Active(file)        1015940 KiB
Inactive(file)        1037068 KiB
Unevictable        48 KiB
Mlocked        48 KiB
SwapTotal    Virtual Memory    12995580 KiB
SwapFree    Free Virtual Memory    12995580 KiB
Dirty        808 KiB
Writeback        0 KiB
AnonPages        1588000 KiB
Mapped        600276 KiB
Shmem        60572 KiB
KReclaimable        127272 KiB
Slab        228752 KiB
SReclaimable        127272 KiB
SUnreclaim        101480 KiB
KernelStack        16080 KiB
PageTables        27320 KiB
NFS_Unstable        0 KiB
Bounce        0 KiB
WritebackTmp        0 KiB
CommitLimit        21105644 KiB
Committed_AS        7258668 KiB
VmallocTotal        -1 KiB
VmallocUsed        41016 KiB
VmallocChunk        0 KiB
Percpu        7616 KiB
HardwareCorrupted        0 KiB
AnonHugePages        0 KiB
ShmemHugePages        0 KiB
ShmemPmdMapped        0 KiB
FileHugePages        0 KiB
FilePmdMapped        0 KiB
HugePages_Total        0
HugePages_Free        0
HugePages_Rsvd        0
HugePages_Surp        0
Hugepagesize        2048 KiB
Hugetlb        0 KiB
DirectMap4k        305788 KiB
DirectMap2M        9029632 KiB
DirectMap1G        7340032 KiB
PCI Devices
PCI Devices
Host bridge    Advanced Micro Devices, Inc. [AMD/ATI] RD9x0/RX980 Host Bridge (rev 02)
PCI bridge    Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GFX port 0) (prog-if 00 [Normal decode])
PCI bridge    Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 0) (prog-if 00 [Normal decode])
PCI bridge    Advanced Micro Devices, Inc. [AMD/ATI] RD890/RD9x0/RX980 PCI to PCI bridge (PCI Express GPP Port 3) (prog-if 00 [Normal decode])
SATA controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40) (prog-if 01 [AHCI 1.0])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
SMBus    Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
Audio device    Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
ISA bridge    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
PCI bridge    Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40) (prog-if 01 [Subtractive decode])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller (prog-if 10 [OHCI])
PCI bridge    Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0) (prog-if 00 [Normal decode])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller (prog-if 10 [OHCI])
USB controller    Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller (prog-if 20 [EHCI])
Host bridge    Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 0
Host bridge    Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 1
Host bridge    Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 2
Host bridge    Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 3
Host bridge    Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 4
Host bridge    Advanced Micro Devices, Inc. [AMD] Family 15h Processor Function 5
VGA compatible controller    NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
Audio device    NVIDIA Corporation High Definition Audio Controller (rev a1)
Ethernet controller    Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
USB controller    ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller (prog-if 30 [XHCI])
Communication controller    Conexant Systems, Inc. SoftV92 SpeakerPhone SoftRing Modem with SmartSP (rev 01)
Multimedia video controller    Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
Multimedia controller    Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
Multimedia controller    Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
Multimedia video controller    Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
USB Devices
USB Devices
Linux Foundation 2.0 root hub    
Linux Foundation 1.1 root hub    
Linux Foundation 1.1 root hub    
Linux Foundation 2.0 root hub    
Linux Foundation 1.1 root hub    
Unknown JMS578 based SATA bridge    
Linux Foundation 2.0 root hub    
Logitech, Inc. Unifying Receiver    
Linux Foundation 1.1 root hub    
Linux Foundation 3.0 root hub    
Novatek Microelectronics Corp. Keyboard (Labtec Ultra Flat Keyboard)    
Logitech, Inc. Optical Wheel Mouse    
Linux Foundation 2.0 root hub    
Printers
Printers
No printers found    
Battery
No batteries
No batteries found on this system    
Sensors
Sensors
nouveau/temp1    Temperature    58.00°C
nouveau/in0    Voltage    0.90V
k10temp/temp1    Temperature    18.62°C
Input Devices
Input Devices
Power Button    
Power Button    
Logitech USB Optical Mouse    
Logitech K230    
NOVATEK USB Keyboard    
NOVATEK USB Keyboard System Control    
NOVATEK USB Keyboard Consumer Control    
NOVATEK USB Keyboard    
Eee PC WMI hotkeys    
HDA NVidia HDMI/DP,pcm:3    
HDA NVidia HDMI/DP,pcm:7    
HDA NVidia HDMI/DP,pcm:8    
HDA NVidia HDMI/DP,pcm:9    
HDA ATI SB Front Mic    
HDA ATI SB Rear Mic    
HDA ATI SB Line    
HDA ATI SB Line Out    
HDA ATI SB Front Headphone    
Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder    
Storage
SCSI Disks
ATA ST500DM002-1BD14    
ATA WDC WD40EZRZ-00G    
ATA WDC WD40EZRZ-00G    
HL-DT-ST DVDRAM GSA-H66N    
TO Exter nal USB 3.0    
DMI
Product
Name    To be filled by O.E.M.
Family    To be filled by O.E.M.
Vendor    To be filled by O.E.M.
Version    To be filled by O.E.M.
BIOS
Date    10/01/2013
Vendor    American Megatrends Inc. (American Megatrends, www.ami.com)
Version    2006
Board
Name    M5A97 LE R2.0
Vendor    ASUSTeK COMPUTER INC. (SEAGATE, www.seagate.com)
Version    Rev 1.xx
Serial Number    (Not available; Perhaps try running HardInfo as root.)
Asset Tag    To be filled by O.E.M.
Chassis
Vendor    To Be Filled By O.E.M.
Type    [3] Desktop
Version    To Be Filled By O.E.M.
Serial Number    (Not available; Perhaps try running HardInfo as root.)
Asset Tag    To Be Filled By O.E.M.
Memory SPD
SPD
Please load the eeprom module to obtain information about memory SPD    
Resources


Shared Directories
SAMBA
Documents    /media/Documents
printers    /var/spool/samba
print$    /var/lib/samba/printers
The Boys    /media/Documents/The Boys
Jonathan    /media/Documents/Jonathan
Public    /home/administration/Public
configs    /media/Documents/configs
Teaching    /media/Documents/Teaching
Resources    /media/Documents/Resources
Shared    /media/Documents/Shared
Baroni Ltd    /media/Documents/Baroni Ltd
Chiara    /media/Documents/Chiara
NFS
No NFS exports    

```

---

### Post by MAFoElffen on 2021-11-26
I am the author/founder and project leader for that script, that was approved/accredited by the Ubuntu Forum's Admin Council. It is hosted at the Forum's GitHub account, along with the forum's 'wireless-info' script. Special Care has been taken with it to ensure that it is easy to use, safe for the user and their hardware... and that the final version of the report (the one that is the be shared with the public) is sanitized of any sensitive data and information. It went through many (months of) reviews to ensure that it had a logical and easy to read format. I am also the Repository Administrator for the Dev and Stable Repo's for that. There is a reason for each command and the information presented in it... In the way it relates to diagnostics of an installed system.

Yes. You have posted an overwhelming amount of information on your host system. It will take a while to go through that in the format presented...

Please go back to that post and edit it. If you look at the very first 'Editor Icon' (all the way on the left), and mouse-over it, you can see that it is the icon for "Switch Editor To Source Mode". If you select it once to switch the mode, then go to your HTML Tags, and change where the opening and closing tags say from [noparse][HTML] / [/HTML] to ```
 / 
```[/noparse].. That will add scroll bars to how that is displayed and make the post appear shorter,,, Which will make that output very much easier to read and analyze.

That is one of the reasons why the Moderators and Admins here keep reminding people to post output within Code Tags.

Back to what you did post, that looks like the NVidia Forum's Information script... which has a lot about what would matter to errors in the NVidia's own 3rd-party proprietary binary driver. 

The NVidia Information Report has nothing about Information on the Linux Desktop and other graphics settings, or installed pieces of the Linux Graphics Layer. It was written when their weren't many choices out there yet, and honestly, as it relates to their own driver, that other information does not matter to them. It was written for information just related to that graphics driver. 

That may sound slighted, but I promise you that it is not. I use NVidia GPU's... I have supported the Linux Graphics Layer (as a whole) for over 16 years now... That means that besides helping make all GPU drivers work (no matter what brand of), that they work with the other pieces and layers of the Graphics Layer. They all have to work together, or nothing works. I am not the one to pass it on to someone else and say it is their problem. I'm looking for 'the solution' to make it work for someone. I here to find a solution for you.

You may laugh or not, but I need more related information... That report has provided a lot of information about the host hardware and about the NVidia GPU that is there, but... Is missing some Ubuntu and system settings related information.

If you do not want to run that script, then I want and need information on the installed Desktop Environment, whether it is running XServer or Wayland? What resolution it was running at before? What it running now? Is it running as traditional kernel series or the Hardware Enablement Platform (HWE)? Is the Hardware HWE capable? At what VTTY is the Graphics running on? What changed about the same time you got the error?

I apologize that we don't have a Wiki page done yet to explain what the individual sections of the 'system-info' script means and what they mean, related to diagnostics of Ubuntu. It was written to help Users Seeking help at this Forum to run on their hardware, so the Users of the Forum could see what they are recommending solutions for... To help us, help you. 

You can Google the commands, look at the script to figure out how to run them manually, or I could post them individually... You are free to do what you want, the way you want. It doesn't matter. I am here to help in either way.

---

### Post by Jonners59 on 2021-11-26
> **MAFoElffen said:**
> I am the author/founder and project leader for that script, that was approved/accredited by the Ubuntu Forum's Admin Council. It is hosted at the Forum's GitHub account, along with the forum's 'wireless-info' script. Special Care has been taken with it to ensure that it is easy to use, safe for the user and their hardware... and that the final version of the report (the one that is the be shared with the public) is sanitized of any sensitive data and information. It went through many (months of) reviews to ensure that it had a logical and easy to read format. I am also the Repository Administrator for the Dev and Stable Repo's for that. There is a reason for each command and the information presented in it... In the way it relates to diagnostics of an installed system.

Yes. You have posted an overwhelming amount of information on your host system. It will take a while to go through that in the format presented...

Please go back to that post and edit it. If you look at the very first 'Editor Icon' (all the way on the left), and mouse-over it, you can see that it is the icon for "Switch Editor To Source Mode". If you select it once to switch the mode, then go to your HTML Tags, and change where the opening and closing tags say from [noparse][HTML] / [/HTML] to ```
 / 
```[/noparse].. That will add scroll bars to how that is displayed and make the post appear shorter,,, Which will make that output very much easier to read and analyze.

That is one of the reasons why the Moderators and Admins here keep reminding people to post output within Code Tags.

Back to what you did post, that looks like the NVidia Forum's Information script... which has a lot about what would matter to errors in the NVidia's own 3rd-party proprietary binary driver. 

The NVidia Information Report has nothing about Information on the Linux Desktop and other graphics settings, or installed pieces of the Linux Graphics Layer. It was written when their weren't many choices out there yet, and honestly, as it relates to their own driver, that other information does not matter to them. It was written for information just related to that graphics driver. 

That may sound slighted, but I promise you that it is not. I use NVidia GPU's... I have supported the Linux Graphics Layer (as a whole) for over 16 years now... That means that besides helping make all GPU drivers work (no matter what brand of), that they work with the other pieces and layers of the Graphics Layer. They all have to work together, or nothing works. I am not the one to pass it on to someone else and say it is their problem. I'm looking for 'the solution' to make it work for someone. I here to find a solution for you.

You may laugh or not, but I need more related information... That report has provided a lot of information about the host hardware and about the NVidia GPU that is there, but... Is missing some Ubuntu and system settings related information.

If you do not want to run that script, then I want and need information on the installed Desktop Environment, whether it is running XServer or Wayland? What resolution it was running at before? What it running now? Is it running as traditional kernel series or the Hardware Enablement Platform (HWE)? Is the Hardware HWE capable? At what VTTY is the Graphics running on? What changed about the same time you got the error?

I apologize that we don't have a Wiki page done yet to explain what the individual sections of the 'system-info' script means and what they mean, related to diagnostics of Ubuntu. It was written to help Users Seeking help at this Forum to run on their hardware, so the Users of the Forum could see what they are recommending solutions for... To help us, help you. 

You can Google the commands, look at the script to figure out how to run them manually, or I could post them individually... You are free to do what you want, the way you want. It doesn't matter. I am here to help in either way.
Thank you.  I have been an Linux user for a very long time, and have some IT knowledge and experience from all the fixes over the years but I am very ignorant of how all this works, so I'll do whatever I'm told.

I don't recall the resolution the screen was set to before the problems as the last time I even looked at the machine was a couple of years ago.  All I know is I had to upgrade the guest OS, Debian from 9 to 10 but when I'd tried some time back had issues so left it.  Then a few days ago found I couldn't save files on the Host from other PCs on the LAN so I took a look only to find a very low resolution and the screen unresponsive to keyboard and mouse, bar I could move the cursor around so had to power off...  all went down hill from there.  What I do is there used to be X-Org and various NVIDIA drivers in Additional Drivers, but since there are none and the resolution and quality are vastly lower.

So, if I can find the script I'll run it and happy to run any cmds I'm told to.  The young lady is out tomorrow so I'll try and slip into the room and do some tests.  I'm currently using my mobile to reply...

Thank you and please feel free to give me whatever cmds and tasks...

---

### Post by MAFoElffen on 2021-11-26
Thank you very much. That was so very much easier to read once you changed those tags to code tags. My eyes are not what they used to be. LOL

I see it is running on the Nouveau driver, which  the GeForce 210  (tesla) is NV50, which by the Nouveau feature Map most all is working with it for 3D Rendering to work.

But very odd that it is not showing any additional drivers on your host. NVidia 340 should work for it, but nothing newer... Ubuntu package nvidia-340 shows up for 18.04 through 22.04 in the Ubuntu Restricted Repo's. Nvidia driver 340.108 still shows up for me in the Additional Drivers Tab in Software & Updates. Do you still have the Restricted Repo's enabled in your settings? You can check that by checking in the Ubuntu Software Tab of Software & Updates... Or by looking at your /etc/apt/sources.list and making sure it is not commented out.

What happens if you do:
```

sudo ubuntu-drivers list

```
If that returns that ubuntu-drivers is not installed, it is in package ubuntu-drivers-extra now...

---

### Post by Jonners59 on 2021-11-27
> **MAFoElffen said:**
> Thank you very much. That was so very much easier to read once you changed those tags to code tags. My eyes are not what they used to be. LOL

I normally do use CODE and not HTML.  Not sure why I did TBH.  Maybe because the output report was HTML and I didn't think.

> **MAFoElffen said:**
> 
I see it is running on the Nouveau driver, which  the GeForce 210   (tesla) is NV50, which by the Nouveau feature Map most all is working  with it for 3D Rendering to work.

But very odd that it is not showing any additional drivers on your host.  NVidia 340 should work for it, but nothing newer... Ubuntu package  nvidia-340 shows up for 18.04 through 22.04 in the Ubuntu Restricted  Repo's. Nvidia driver 340.108 still shows up for me in the Additional  Drivers Tab in Software & Updates. Do you still have the Restricted  Repo's enabled in your settings? You can check that by checking in the  Ubuntu Software Tab of Software & Updates... Or by looking at your  /etc/apt/sources.list and making sure it is not commented out.

Yes, I recall it and other drivers to 490 I think.  NVIDIA recommends, and its final driver for an NVIDIA Corporation GT218 [GeForce 210] (rev a2) was/is, from their website:

                                     **[SIZE=2]Linux x64 (AMD64/EM64T) Display Driver[/SIZE]**

                                      
                                 
                                                                                                                                                                                                                                                                                                                                                                                                                      [TABLE]
[TR]
[TD="class: contentsummaryleft"][SIZE=2]                                                 Version:                                             
[/SIZE][/TD]
[TD="class: contentsummaryright, colspan: 2"][SIZE=2]                                                 340.108                                             
[/SIZE][/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"][SIZE=2]                                                      Release Date:                                             
[/SIZE][/TD]
[TD="class: contentsummaryright, colspan: 2"][SIZE=2]                                                                                                     2019.12.23                                             
[/SIZE][/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"][SIZE=2]                                                                                                     Operating System:                                             
[/SIZE][/TD]
[TD="class: contentsummaryright, colspan: 2"][SIZE=2]                                                     Linux 64-bit                                             [/SIZE][/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"][SIZE=2]                                                                                                     Language:                                             
[/SIZE][/TD]
[TD="class: contentsummaryright, colspan: 2"][SIZE=2]                                                     English (UK)                                             
[/SIZE][/TD]
[/TR]
[TR]
[TD="class: contentsummaryleft"][SIZE=2]                                                                                                     File Size:                                             
[/SIZE][/TD]
[TD="class: contentsummaryright, colspan: 2"][SIZE=2]                                                                                                     66.92 MB                                                                                       
[/SIZE][/TD]
[/TR]
[/TABLE]

So I took a look at my sources file by running
                       ```
 sudo gedit /etc/apt/sources.list


``` 
And listed were, so they are there:
 
 [HTML]deb-src http://archive.ubuntu.com/ubuntu impish main restricted #Added by software-properties

 deb http://archive.ubuntu.com/ubuntu impish-updates main restricted

 deb-src http://archive.ubuntu.com/ubuntu impish-updates main multiverse restricted universe #Added by software-properties

[/HTML] 
 
  PS from a previous question.  The current resolution is 1280 x 1024  Which is OK but nothing like it was and also means that the VM Guest is very grainy.


> **MAFoElffen said:**
> 
What happens if you do:
```

sudo ubuntu-drivers list

```
If that returns that ubuntu-drivers is not installed, it is in package ubuntu-drivers-extra now...

Blank.  Absolutely nothing listed.

I typed "ubuntu-drivers in to synaptic and had about 6 entries.  I selected 5 of them, namely Nvidia graphics, but made no change.

I then search nvidia 340 and found nvidia 340 and nvidia 340-dev and installed them.  That too made no difference.  Nothing listed in Additional Drivers or when I ran the code.

Any further thoughts?  I'll try and find that script you mention...

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
[SIZE=4]**Update 1.**[/SIZE]

I tried to install the NVIDIA driver I downloaded from NVIDIA following their instructions.

[HTML]sudo  sh ./NVIDIA-Linux-x86_64-340.107.run[/HTML]

It failed, said that  QUOTE: "You appear to be running an X server; please exit X before installing."  So that failed too.

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
[SIZE=4]**Update 2.**[/SIZE]

Followed the link for the system-info file:
[HTML]https://github.com/UbuntuForums/system-info[/HTML]

REPORT:
[https://paste.ubuntu.com/p/y9kvg4FYBp/](https://paste.ubuntu.com/p/y9kvg4FYBp/)

```
Starting the Ubuntu Forums 'system-info' Report: 2021-11-27  11:23:12 GMT (+0000)
    Part of the Ama-gi Project
    Version: 01.00-01, Script Date: 2021.09.30

---------------------------------------------------------------
Main Complaint: graphics dropped and inability to share directories and fikles[D[D[D[D[[3~[3~[C[Cles
Problem Description:  No additional drivers appear and the resolution is not as high as it was.  something changed during an uopdate at some point.  Also this machine is used as a central storage and backup, but since the upgrade/update sharing is not working.  The directores are not visiable on the LAN to any device.  SAMBA is installed.
---------- General Computer Specifications:

  --- Computer/CPU Information from 'lshw -C cpu' --- 
*-Cpu
    Description: CPU
    Product: AMD FX(tm)-8350 Eight-Core Processor
    Vendor: Advanced Micro Devices [AMD]
    Physical id: 4
    Bus info: cpu@0
    Version: AMD FX(tm)-8350 Eight-Core Processor
    Serial: [REMOVED]
    Slot: Socket 942
    Size: 2098MHz
    Capacity: 4GHz
    Width: 64 bits
    Clock: 200MHz
    Capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 
        apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht 
        syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good 
        nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor 
        ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm 
        cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch 
        osvw ibs xop skinit wdt fma4 tce nodeid_msr tbm topoext perfctr_core 
        perfctr_nb cpb hw_pstate ssbd ibpb vmmcall bmi1 arat npt lbrv svm_lock 
        nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter 
        pfthreshold lwp cpufreq
    Configuration: cores=8 enabledcores=8 threads=8

computer
    Description: Desktop Computer
    Product: To be filled by O.E.M. (SKU)
    Vendor: To be filled by O.E.M.
    Version: To be filled by O.E.M.
    Serial: [REMOVED]
    Width: 64 bits
    Capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    Configuration:
        boot=normal
        chassis=desktop
        family=To be filled by O.E.M.
        sku=SKU
        uuid=[REMOVED]

------------------ SMBIOS Information from '/sys/class/dmi/id/' 
Bios Vendor:         American Megatrends Inc.
Bios Version:        2006
Bios Release:        4.6
Board Vendor:        ASUSTeK COMPUTER INC.
Board Name:          M5A97 LE R2.0
Board Version:       Rev 1.xx
Board Serial:        131118679702918
Board Asset Tag:     To be filled by O.E.M.

Current boot mode:   UEFI Firmware mode
SecureBoot enabled


---------- Memory Information:
               total        used        free      shared  buff/cache   available
Mem:            15Gi       7.6Gi       449Mi        64Mi       7.4Gi       7.5Gi
Swap:           12Gi       3.0Mi        12Gi

---------- IP Adress Information:
  --- IP Adress Information from 'ip addr' --- 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet [REMOVED]
    inet6 [REMOVED]
3: vboxnet0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000

  --- Internet Connection Status from 'ping [various addresses]' --- 
Connected to Internet with DNS

  --- Network Device Status Summary from 'ip addr' ---  
These Network Devices are up:
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000

  --- Hostname from 'hostname --fqdn' ---  
The 'Hostname' of the computer system is: store


---------- File system specs from 'df -h':
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4   77G   15G   59G  20% /
/dev/sdb1      ext4  3.6T  935G  2.5T  27% /media/Backup
/dev/sdc1      ext4  3.6T  987G  2.5T  29% /media/Documents
/dev/sdd2      ext4  868G  815G  9.1G  99% /media/3CXExt
/dev/sda1      vfat  5.6G  7.8M  5.6G   1% /boot/efi
/dev/sda3      ext4  144G  899M  136G   1% /home
/dev/sda5      ext4  183G   66G  108G  38% /home/administration/VirtualBox
/dev/sda6      ext4   48G   53M   46G   1% /home/administration/.VirtualBox

---------- Disk/Partition Information From 'fdisk':

Disk /dev/sdc: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EZRZ-00G
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B0452280-28A6-42F0-AE56-62F9A3EEF7E0

Device     Start        End    Sectors  Size Type
/dev/sdc1   2048 7814035455 7814033408  3.6T Linux filesystem

Disk /dev/sdb: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EZRZ-00G
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 378C83C8-8715-4708-8543-2E657ECFC350

Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 7814035455 7814033408  3.6T Linux filesystem

Disk /dev/sda: 465.76 GiB, 500106780160 bytes, 976771055 sectors
Disk model: ST500DM002-1BD14
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9f340666

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048  11743231  11741184   5.6G ef EFI (FAT-12/16/32)
/dev/sda2        11743232 175344794 163601563    78G 83 Linux
/dev/sda3       175345664 483317759 307972096 146.9G 83 Linux
/dev/sda4       483319806 976769023 493449218 235.3G  5 Extended
/dev/sda5       483319808 874369023 391049216 186.5G 83 Linux
/dev/sda6       874371072 976769023 102397952  48.8G 83 Linux

Partition 4 does not start on physical sector boundary.

Disk /dev/sdd: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: nal USB 3.0     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00057726

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdd1       1849409536 1875400703   25991168  12.4G 82 Linux swap / Solaris
/dev/sdd2             2048 1849409535 1849407488 881.9G 83 Linux

Partition table entries are not in disk order.


---------- Disk/Partition Information From 'lsblk':
NAME     SIZE FSTYPE   LABEL       MOUNTPOINT                       MODEL
sda    465.8G                                                       ST500DM002-1BD142
|-sda1   5.6G vfat                 /boot/efi                        
|-sda2    78G ext4     root        /                                
|-sda3 146.9G ext4     home        /home                            
|-sda4     1K                                                       
|-sda5 186.5G ext4     VIRTUALBOX  /home/administration/VirtualBox  
`-sda6  48.8G ext4     .VIRTUALBOX /home/administration/.VirtualBox 
sdb      3.6T                                                       WDC_WD40EZRZ-00GXCB0
`-sdb1   3.6T ext4     Backup      /media/Backup                    
sdc      3.6T                                                       WDC_WD40EZRZ-00GXCB0
`-sdc1   3.6T ext4     Documents   /media/Documents                 
sdd    931.5G                                                       nal_USB_3.0
|-sdd1  12.4G swap     SWAP        [SWAP]                           
`-sdd2 881.9G ext4     3CXExt      /media/3CXExt                    
sr0      1.3G                                                       HL-DT-ST_DVDRAM_GSA-H66N
   ------- 'lsblk' information continued ...
NAME   HOTPLUG PARTUUID                             UUID
sda          0                                      
|-sda1       0 9f340666-01                          1B72-B161
|-sda2       0 9f340666-02                          26a204d6-fb83-4d0e-9d55-8d514c97669d
|-sda3       0 9f340666-03                          908263d4-b703-449d-aa49-f2c45a85e631
|-sda4       0 9f340666-04                          
|-sda5       0 9f340666-05                          80635bcd-57cd-4a6d-bba8-f46e63928cff
`-sda6       0 9f340666-06                          da72055b-1010-461d-ba7e-a4ab3b85f08c
sdb          0                                      
`-sdb1       0 a81c1c24-1646-4684-ab05-4b3ba0ae525b 28f57bf2-b6d4-4dee-af23-73a2054eb968
sdc          0                                      
`-sdc1       0 6694bd1d-d448-4c65-9130-3fbbe01ef2b4 6f78df6e-1e94-43c1-aa4b-85d30bd8f18c
sdd          1                                      
|-sdd1       1 00057726-01                          00716615-1473-446e-aeb5-4530e220f3d9
`-sdd2       1 00057726-02                          a2c0c31c-d9bc-4b12-9681-0f08f56d4a89
sr0          1                                      

---------- Mount Details of '/etc/fstab':
UUID=26a204d6-fb83-4d0e-9d55-8d514c97669d /               ext4    errors=remount-ro 0       1


UUID=908263d4-b703-449d-aa49-f2c45a85e631 /home           ext4    defaults        0       2

UUID=00716615-1473-446e-aeb5-4530e220f3d9 none            swap    sw              0       0

UUID=6f78df6e-1e94-43c1-aa4b-85d30bd8f18c /media/Documents        ext4    defaults           1      2

UUID=28f57bf2-b6d4-4dee-af23-73a2054eb968 /media/Backup            ext4    defaults            1       2

UUID=80635bcd-57cd-4a6d-bba8-f46e63928cff /home/administration/VirtualBox         ext4    defaults        0       2

UUID=da72055b-1010-461d-ba7e-a4ab3b85f08c /home/administration/.VirtualBox        ext4    defaults        0       2

/dev/sdd2 /media/3CXExt           ext4    defaults,noatime 0 2

/dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=1B72-B161  /boot/efi       vfat    defaults      0       1

---------- Current Mount Details of 'mount':
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda3 on /home type ext4 (rw,relatime)
/dev/sda5 on /home/administration/VirtualBox type ext4 (rw,relatime)
/dev/sda6 on /home/administration/.VirtualBox type ext4 (rw,relatime)
/dev/sdb1 on /media/Backup type ext4 (rw,relatime,stripe=8191)
/dev/sdc1 on /media/Documents type ext4 (rw,relatime,stripe=8191)
/dev/sdd2 on /media/3CXExt type ext4 (rw,noatime,stripe=32750)

---------- USB Information from 'lsusb -t -v':
/:  Bus 09.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
    ID 1d6b:0003 Linux Foundation 3.0 root hub
/:  Bus 08.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
    |__ Port 2: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 0603:00f2 Novatek Microelectronics Corp. Keyboard (Labtec Ultra Flat Keyboard)
    |__ Port 2: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
        ID 0603:00f2 Novatek Microelectronics Corp. Keyboard (Labtec Ultra Flat Keyboard)
/:  Bus 07.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/4p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/2p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/5p, 12M
    ID 1d6b:0001 Linux Foundation 1.1 root hub
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        ID 046d:c52b Logitech, Inc. Unifying Receiver
    |__ Port 2: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        ID 046d:c52b Logitech, Inc. Unifying Receiver
    |__ Port 2: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
        ID 046d:c52b Logitech, Inc. Unifying Receiver
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/4p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/5p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 4: Dev 3, If 0, Class=Mass Storage, Driver=uas, 480M
        ID 0080:a001 Unknown JMS578 based SATA bridge

---------- Video Details from 'lshw':

  *-display
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: 
           irq:42 
           memory:fd000000-fdffffff 
           memory:c0000000-cfffffff 
           memory:d0000000-d1ffffff 
           ioport:e000(size=128) 
           memory:c0000-dffff

   --- Graphics Environment Continued form 'various graphics ENVs' ----
The Current Configured Destop is: XFCE 
The Current Desktop Session is: xfce 
The Current Session Type is: x11 
The Current Display Manager is: lightdm
The Current Desktop Theme: 'Breeze'
The Current Virtual TTYs being used are:
    TTY#    Used By
    tty7    Xorg
    tty1    agetty

---------- Repository Information from '/etc/apt/sources.list and etc/apt/sources.list.d/':

Sources List:
deb http://archive.ubuntu.com/ubuntu impish main restricted
deb http://archive.ubuntu.com/ubuntu impish-updates main restricted
deb http://archive.ubuntu.com/ubuntu impish universe
deb http://archive.ubuntu.com/ubuntu impish-updates universe
deb http://archive.ubuntu.com/ubuntu impish multiverse
deb http://archive.ubuntu.com/ubuntu impish-updates multiverse
deb http://archive.ubuntu.com/ubuntu impish-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu impish partner
deb-src http://archive.canonical.com/ubuntu impish partner
deb http://archive.ubuntu.com/ubuntu impish-security main restricted
deb http://archive.ubuntu.com/ubuntu impish-security universe
deb http://archive.ubuntu.com/ubuntu impish-security multiverse

---------- Other Details from 'Various':
The current kernel version is:       5.13.0-21-generic 
The current release description is:  Ubuntu 21.10 
Original Installation Date:          2021-11-25+16:08:40 
Original Installation Media: Ubuntu 21.10 "Impish Indri" - Release amd64 (20211012)
Do-Release-Upgrade Date: This system may have not had a 'Release Upgrade' through 'do-release-upgrade'

These are the current kernel ranges for HWE kernels for this release.
   --- HWE Kernel Reference from 'apt-cache show':


   --- HWE Package Status from 'dpkg':
HWE package linux-generic-hwe-21.10 was not detected. Please check 
kernel version to verify range

   --- Certified Hardware Platform Status: (By the Ubuntu Wiki Standards)
Ubuntu Certified Hardware Platform. Safe to install 
the Hardware Enablement Stack (HWE).

Currently logged in User(s):
NAME     LINE         TIME         COMMENT
administration tty7         Nov 26 11:29 (:0)

The User running this script was: administration
uid=1000(administration)
gid=1000(administration)
groups=1000(administration),4(adm),20(dialout),21(fax),24(cdrom),
25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),
120(netdev),122(lpadmin),126(scanner),133(lxd),134(sambashare),
144(vboxusers)

*** End Of Report ***
```

---

### Post by MAFoElffen on 2021-11-27
Well... I explain in my Graphic Resolution Sticky (also Linked in my sig-line, that you can kill the XServer to get to a Console to run the NVidia Script to install their Binary (ut do not do that,I'll explain why you might not want to do that after this)... By doing 
```

sudo kill $(pidof lightdm)

```
But, here is why you might not want to do that. It is a P.I.T.A. to do that. I used to do it this way myself years ago. The binaries work, but the script compiles to whatever the current Kernel is. When a Kernel updates (which it will), then sometimes the NVidia Binary driver would fail on the next reboot after that Kernel update, because it was compiled against an earlier kernel. What we had to do in years past, was install this driver... If just after an update, it came up to a black screen... Check to see if the kernel updated... Then boot as text only console, then reinstall the binary driver... (rerun that same script to recompile it on the newer kernel)... This was not a good solution for mid-level skilled to lower-level skilled Users.

Where as, with the newer Ubuntu Repo NVidia drivers in Restricted and in the Graphics Team PPA... Those .deb drivers are scripted to use DRM to recognize that if there is a Kernel update, to automatically recompile the video driver to the newer Kernel. That is pro-actively a much better solution, and will save you so much work and headaches in the long run. Does that make sense to you?

Why make your life harder or more challenging than it needs to be, right?

Yes, I see from the output there that it NVidia driver 304.108 could be installed by either installing it directly from restricted, by the ubuntu-drivers utility or via the Ubuntu Graphics team PPA.

---

### Post by Jonners59 on 2021-11-27
> **MAFoElffen said:**
> Well... I explain in my Graphic Resolution Sticky (also Linked in my sig-line, that you can kill the XServer to get to a Console to run the NVidia Script to install their Binary (ut do not do that,I'll explain why you might not want to do that after this)... By doing 
```

sudo kill $(pidof lightdm)

```
But, here is why you might not want to do that. It is a P.I.T.A. to do that. I used to do it this way myself years ago. The binaries work, but the script compiles to whatever the current Kernel is. When a Kernel updates (which it will), then sometimes the NVidia Binary driver would fail on the next reboot after that Kernel update, because it was compiled against an earlier kernel. What we had to do in years past, was install this driver... If just after an update, it came up to a black screen... Check to see if the kernel updated... Then boot as text only console, then reinstall the binary driver... (rerun that same script to recompile it on the newer kernel)... This was not a good solution for mid-level skilled to lower-level skilled Users.

Where as, with the newer Ubuntu Repo NVidia drivers in Restricted and in the Graphics Team PPA... Those .deb drivers are scripted to use DRM to recognize that if there is a Kernel update, to automatically recompile the video driver to the newer Kernel. That is pro-actively a much better solution, and will save you so much work and headaches in the long run. Does that make sense to you?

Why make your life harder or more challenging than it needs to be, right?

I fall in to the latter group...  :-) and a believer in KISS, so yes, absolutely.  Didn't know all that.  Beggers why NVIDIA couldn't have worked just that little bit closer to the Ubuntu team to create a ppa (I think that's correct terminology) so that updates are automatic.

> **MAFoElffen said:**
> 
Yes, I see from the output there that it NVidia driver 304.108 could be  installed by either installing it directly from restricted, by the  ubuntu-drivers utility or via the Ubuntu Graphics team PPA.

I think you mean 340, but yes, so tried to install and it said it installed but still doesn't exist....  I used synaptic again for that.  Nothing seems to work.  ;-(

---

### Post by MAFoElffen on 2021-11-27
What is the output from(/)
```

sudo apt-cache show nvidia-340

```
Here is what it show's on mine, but I am running 20.04.3 LTS
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo apt-cache show nvidia-340 | egrep -v 'Modaliases:'
Package: nvidia-340
Architecture: amd64
Version: 340.108-0ubuntu5.20.04.2
Priority: optional
Section: restricted/misc
Source: nvidia-graphics-drivers-340
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 268730
Provides: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-driver-binary, nvidia-kernel-common, nvidia-persistenced, xorg-driver-binary, xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc-s1, libc6-i386, passwd, adduser, xserver-xorg-legacy, libc6 (>= 2.2.5), libgl1, libx11-6, libxext6, xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19 | xorg-video-abi-20 | xorg-video-abi-23 | xorg-video-abi-24, xserver-xorg-core (>= 2:1.19.6-1ubuntu2)
Recommends: nvidia-settings (>= 331.20), libcuda1-340, nvidia-opencl-icd-340
Conflicts: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-kernel-common, nvidia-persistenced, xorg-driver-binary
Replaces: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-kernel-common, nvidia-persistenced, xorg-driver-binary
Filename: pool/restricted/n/nvidia-graphics-drivers-340/nvidia-340_340.108-0ubuntu5.20.04.2_amd64.deb
Size: 51999180
MD5sum: a51d6c80f15ff940fd778d9bdadb696c
SHA1: edc24a35d2ec0d8e6843bc6a648f6d7275817f4d
SHA256: cad24a6ac23618cc60a2bbe21f3cde57705467aef2b03bbacd7756df55b0b2b3
SHA512: 727188e8ac7950870a747ceeff57ab5d74735e90a3f0dd0656405ecd17a507bd9de25393645a012c8359f162bfc8f0b946133390af8540645444199ce08210ac
Description-en: NVIDIA binary driver - version 340.108
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
 and flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of
 the Video Decode and presentation API. The latter enables acceleration
 for GeForce 8 and later series cards for h264 video.
 .
 Release Notes and supported GPUs:
 http://www.nvidia.com/object/linux-display-amd64-340.108-driver.html
Description-md5: 8597c97ef19d5359374bc2742e6dd180

Package: nvidia-340
Architecture: amd64
Version: 340.108-0ubuntu2
Priority: optional
Section: restricted/misc
Source: nvidia-graphics-drivers-340
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 268697
Provides: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-driver-binary, nvidia-persistenced, xorg-driver-binary, xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc1, libc6-i386, passwd, adduser, xserver-xorg-legacy, libc6 (>= 2.2.5), libgl1, libx11-6, libxext6, xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19 | xorg-video-abi-20 | xorg-video-abi-23 | xorg-video-abi-24, xserver-xorg-core (>= 2:1.19.6-1ubuntu2)
Recommends: nvidia-settings (>= 331.20), libcuda1-340, nvidia-opencl-icd-340
Conflicts: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-persistenced, xorg-driver-binary
Replaces: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-persistenced, xorg-driver-binary
Filename: pool/restricted/n/nvidia-graphics-drivers-340/nvidia-340_340.108-0ubuntu2_amd64.deb
Size: 51995952
MD5sum: 13aa2f488f58d19d661d6c58300ff5fd
SHA1: 0906d8fdd9c948dc76873dcbf34a638d58cd2352
SHA256: 9b2afc6cfd85b0cf1c4b25db9927a52680e71f58da98dafc216a2006125b1d88
Description-en: NVIDIA binary driver - version 340.108
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
 and flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of
 the Video Decode and presentation API. The latter enables acceleration
 for GeForce 8 and later series cards for h264 video.
 .
 Release Notes and supported GPUs:
 http://www.nvidia.com/object/linux-display-amd64-340.108-driver.html
Description-md5: 8597c97ef19d5359374bc2742e6dd180

```

If it has none... Then maybe it's because you are on 21.10? But I see that listed in restricted for that... Strange.

Note that under 'Source' for that package, it is 'nvidia-graphics-drivers-340'... That is the package name of the same driver in the Ubuntu Graphics Team P.P.A.

---

### Post by Jonners59 on 2021-11-27
> **MAFoElffen said:**
> What is the output from(/)
```

sudo apt-cache show nvidia-340

```
Here is what it show's on mine, but I am running 20.04.3 LTS
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo apt-cache show nvidia-340 | egrep -v 'Modaliases:'
Package: nvidia-340
Architecture: amd64
Version: 340.108-0ubuntu5.20.04.2
Priority: optional
Section: restricted/misc
Source: nvidia-graphics-drivers-340
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 268730
Provides: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-driver-binary, nvidia-kernel-common, nvidia-persistenced, xorg-driver-binary, xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc-s1, libc6-i386, passwd, adduser, xserver-xorg-legacy, libc6 (>= 2.2.5), libgl1, libx11-6, libxext6, xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19 | xorg-video-abi-20 | xorg-video-abi-23 | xorg-video-abi-24, xserver-xorg-core (>= 2:1.19.6-1ubuntu2)
Recommends: nvidia-settings (>= 331.20), libcuda1-340, nvidia-opencl-icd-340
Conflicts: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-kernel-common, nvidia-persistenced, xorg-driver-binary
Replaces: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-kernel-common, nvidia-persistenced, xorg-driver-binary
Filename: pool/restricted/n/nvidia-graphics-drivers-340/nvidia-340_340.108-0ubuntu5.20.04.2_amd64.deb
Size: 51999180
MD5sum: a51d6c80f15ff940fd778d9bdadb696c
SHA1: edc24a35d2ec0d8e6843bc6a648f6d7275817f4d
SHA256: cad24a6ac23618cc60a2bbe21f3cde57705467aef2b03bbacd7756df55b0b2b3
SHA512: 727188e8ac7950870a747ceeff57ab5d74735e90a3f0dd0656405ecd17a507bd9de25393645a012c8359f162bfc8f0b946133390af8540645444199ce08210ac
Description-en: NVIDIA binary driver - version 340.108
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
 and flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of
 the Video Decode and presentation API. The latter enables acceleration
 for GeForce 8 and later series cards for h264 video.
 .
 Release Notes and supported GPUs:
 http://www.nvidia.com/object/linux-display-amd64-340.108-driver.html
Description-md5: 8597c97ef19d5359374bc2742e6dd180

Package: nvidia-340
Architecture: amd64
Version: 340.108-0ubuntu2
Priority: optional
Section: restricted/misc
Source: nvidia-graphics-drivers-340
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 268697
Provides: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-driver-binary, nvidia-persistenced, xorg-driver-binary, xorg-driver-video
Depends: x11-common (>= 1:7.0.0), make, sed (>> 3.0), dkms, linux-libc-dev, libc6-dev, patch, acpid, lib32gcc1, libc6-i386, passwd, adduser, xserver-xorg-legacy, libc6 (>= 2.2.5), libgl1, libx11-6, libxext6, xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14 | xorg-video-abi-15 | xorg-video-abi-18 | xorg-video-abi-19 | xorg-video-abi-20 | xorg-video-abi-23 | xorg-video-abi-24, xserver-xorg-core (>= 2:1.19.6-1ubuntu2)
Recommends: nvidia-settings (>= 331.20), libcuda1-340, nvidia-opencl-icd-340
Conflicts: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-persistenced, xorg-driver-binary
Replaces: libnvidia-cfg1-any, libnvidia-decode, libnvidia-encode, libnvidia-fbc1, libnvidia-gl, libnvidia-ifr1, nvidia-dkms-kernel, nvidia-persistenced, xorg-driver-binary
Filename: pool/restricted/n/nvidia-graphics-drivers-340/nvidia-340_340.108-0ubuntu2_amd64.deb
Size: 51995952
MD5sum: 13aa2f488f58d19d661d6c58300ff5fd
SHA1: 0906d8fdd9c948dc76873dcbf34a638d58cd2352
SHA256: 9b2afc6cfd85b0cf1c4b25db9927a52680e71f58da98dafc216a2006125b1d88
Description-en: NVIDIA binary driver - version 340.108
 The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
 and flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver, and provides NVIDIA's implementation of
 the Video Decode and presentation API. The latter enables acceleration
 for GeForce 8 and later series cards for h264 video.
 .
 Release Notes and supported GPUs:
 http://www.nvidia.com/object/linux-display-amd64-340.108-driver.html
Description-md5: 8597c97ef19d5359374bc2742e6dd180

```

If it has none... Then maybe it's because you are on 21.10? But I see that listed in restricted for that... Strange.

Note that under 'Source' for that package, it is 'nvidia-graphics-drivers-340'... That is the package name of the same driver in the Ubuntu Graphics Team P.P.A.

YUP!  No question it's to do with the upgrade.  Not sure if it started during 21.04 and I missed it, but definitely 21.10.  When I get a chance I'll run that cmd and see what it gives me, but it is something to do with the latest build, whether a bug or this is the direction they want to go.  Should be allowed to install drivers for older cards, but 5 years is not even old.  Anyway.  Here we are.

++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

[SIZE=4]**UPDATE 1.**[/SIZE]

```
sudo apt-cache show nvidia-340
```

```
Package: nvidia-340
Architecture: amd64
Version: 340.108-0ubuntu8
Priority: optional
Section: restricted/misc
Source: nvidia-graphics-drivers-340
Origin: Ubuntu
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 21
Depends: xserver-xorg-video-nouveau
Filename: pool/restricted/n/nvidia-graphics-drivers-340/nvidia-340_340.108-0ubuntu8_amd64.deb
Size: 6452
MD5sum: 75d47baa1b7bb214dea660908e2a1e72
SHA1: c6d9a3b9c7a06f3bc2067beb923ba9529db5a484
SHA256: 495def2a1675784fc5c796cfce91662f43c460119866094034c1802a9cea3929
SHA512: 34eff89b2766f75375832ce6cc67a0d3e4d543dab4ed3a3cdaf16efa3d9c1bbde515158afed362e1598430f605479079d5485e712185844c855206b47ecb2ec2
Description-en: Transitional package for xserver-xorg-video-nouveau
 This is a transitional package for xserver-xorg-video-nouveau,
 and can be safely removed after the installation is complete.
Description-md5: 72561af068042237387957ca2ea4776c

```

And re dependency:  xserver-xorg-video-nouveau is  the newest version (1:1.0.17-1build1) and installed.

So this is a deliberate or error in the new upgrade.   Maybe I should raise another query in "Hardware" or "Installations & Upgrades" or somewhere else?  What do you think?

---

### Post by Jonners59 on 2021-11-28
[SIZE=3]**HUH!**[/SIZE]  A clue.

[https://www.cyberciti.biz/faq/update-upgrade-debian-9-to-debian-10-buster/](https://www.cyberciti.biz/faq/update-upgrade-debian-9-to-debian-10-buster/)

> Debian Linux 10 “Buster” released. The new version offers updated  packages and five years of support. In this release, GNOME defaults to  using the Wayland display server instead of Xorg. However, the Xorg  display server still installed by default.

---

