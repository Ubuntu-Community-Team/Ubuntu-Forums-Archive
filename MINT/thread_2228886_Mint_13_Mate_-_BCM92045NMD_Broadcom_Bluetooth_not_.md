---
title: "Mint 13 Mate - BCM92045NMD Broadcom Bluetooth not recognised"
date: 2014-06-10
forum: MINT
---

### Post by danielr2 on 2014-06-10
I have a HP 8730w with a BCM92045NMD Broadcom Bluetooth module (HP Part  No.: 398393-002). I have Mint 13 32-Bit Mate installed. Almost  everything works, except the Bluetooth. Neither lspci nor lsusb lists  anything to remotely resemble Bluetooth: 

```

~ $ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G94GLM [Quadro FX 2700M] (rev a1)
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
86:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 14)
86:06.4 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)

```

```
~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 004: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 001 Device 005: ID 03f0:031d Hewlett-Packard 
Bus 001 Device 006: ID 1058:071a Western Digital Technologies, Inc. My Passport 1TB
Bus 001 Device 007: ID 12bd:a02f  
Bus 001 Device 008: ID 046d:c05b Logitech, Inc. M-U0004 810-001317 [B110 Optical USB Mouse]
Bus 001 Device 009: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard

```

```
~ $ inxi -Fxz
System:    Host: NB-nc8430 Kernel: 3.2.0-23-generic i686 (32 bit, gcc: 4.6.3) Desktop: N/A Distro: Linux Mint 13 Maya
Machine:   System: Hewlett-Packard (portable) product: HP EliteBook 8730w version: F.13
           Mobo: Hewlett-Packard model: 30EC version: KBC Version 91.25
           Bios: Hewlett-Packard version: 68PAD Ver. F.13 date: 12/03/2010
CPU:        Dual core Intel Core2 Duo CPU P8600 (-MCP-) cache: 3072 KB flags:  (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 9575.98 
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz
Graphics:  Card: NVIDIA G94GLM [Quadro FX 2700M] bus-ID: 01:00.0 X.Org: 1.11.3 driver: nvidia Resolution: 1680x1050@60.0hz 
           GLX Renderer: Quadro FX 2700M/PCIe/SSE2 GLX Version: 3.3.0 NVIDIA 304.116 Direct Rendering: Yes
Audio:     Card: Intel 82801I (ICH9 Family) HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 Sound: ALSA ver: 1.0.24
Network:   Card-1: Intel Ultimate N WiFi Link 5300 driver: iwlwifi ver: in-tree: bus-ID: 03:00.0
           IF: wlan1 state: up mac: <filter>
           Card-2: Intel 82567LM Gigabit Network Connection driver: e1000e ver: 1.5.1-k port: 80e0 bus-ID: 00:19.0
           IF: eth1 state: down mac: <filter>
Drives:    HDD Total Size: 1000.2GB (63.4% used) 1: /dev/sda WDC_WD5000BPKX 500.1GB 
           2: /dev/sdb My_Passport_071A 500.1GB 
Partition: ID: / size: 462G used: 134G (31%) fs: ext4 ID: swap-1 size: 3.62GB used: 0.08GB (2%) fs: swap 
Sensors:   System Temperatures: cpu: 34.0C mobo: 30.0C gpu: 0.0:39C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 175 Uptime: 1 day Memory: 1125.2/2990.4MB Runlevel: 2 Gcc sys: 4.6.3 Client: Shell inxi: 1.7.33 

```

However, dmesg |grep Bluetooth lists some messages related to Bluetooth, but there are no entries for "Broadcom" or "BCM92045NMD":

```
~ $ dmesg |grep Bluetooth
[   15.948707] Bluetooth: Core ver 2.16
[   15.948730] Bluetooth: HCI device and connection manager initialized
[   15.948733] Bluetooth: HCI socket layer initialized
[   15.948735] Bluetooth: L2CAP socket layer initialized
[   15.948871] Bluetooth: SCO socket layer initialized
[   16.119445] Bluetooth: RFCOMM TTY layer initialized
[   16.119450] Bluetooth: RFCOMM socket layer initialized
[   16.119452] Bluetooth: RFCOMM ver 1.11
[   16.331226] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.331229] Bluetooth: BNEP filters: protocol multicast

```

To complete the listings, here is the output of lsmod:

```
~ $ lsmod
Module                  Size  Used by
snd_hrtimer            12648  1 
snd_atiixp_modem       18604  0 
snd_via82xx_modem      18377  0 
snd_intel8x0m          18498  0 
snd_ac97_codec        106082  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
ac97_bus               12642  1 snd_ac97_codec
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158438  10 bnep,rfcomm
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
xt_state               12514  14 
nvidia              10304303  32 
ip6table_filter        12711  1 
binfmt_misc            17292  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
snd_hda_codec_analog    75395  1 
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack            73847  8  nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ip_tables              18106  1 iptable_filter
arc4                   12473  2 
x_tables                21974  13  ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_pcm                80845  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_intel,snd_hda_codec
pata_pcmcia            16938  1 
tpm_infineon           13200  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
iwlwifi               287751  0 
mac80211              436455  1 iwlwifi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
nand                   49667  2 r852,sm_common
nand_ids                8547  1 nand
mtd                    35584  2 sm_common,nand
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39791  1 pata_pcmcia
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
snd                     62064  19  snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r592                   17808  0 
ses                    17217  0 
cfg80211              178679  2 iwlwifi,mac80211
yenta_socket           27428  0 
soundcore              14635  1 snd
enclosure              14744  1 ses
nand_ecc               13070  1 nand
hp_accel               25728  0 
memstick               15857  1 r592
lis3lv02d              19268  1 hp_accel
pcmcia_rsrc            18367  1 yenta_socket
tpm_tis                18308  0 
hp_wmi                 13652  0 
ppdev                  12849  0 
lp                     17455  0 
snd_page_alloc         14115  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
mxm_wmi                12859  0 
joydev                 17393  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
sparse_keymap          13658  1 hp_wmi
input_polldev          13648  1 lis3lv02d
psmouse                87140  0 
serio_raw              13027  0 
parport_pc             32114  1 
video                  19068  0 
wmi                    18744  2 hp_wmi,mxm_wmi
parport                40930  3 ppdev,lp,parport_pc
usbhid                 41906  0 
hid                    77367  1 usbhid
firewire_ohci          40180  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
usb_storage            39646  1 
e1000e                140005  0 

```

Occasionally, the Blueman  Bluetooth Manager Utility shows the  Bluetooth symbol in the taskbar but  klicking on it only reveals the note that no Bluetooth adapter is  pluged into my system. 

Does anyone know how to get this  Bluetooth Adapter working? Do I need to load a specific kernel module? If so,  which one and how? My Linux literacy still leaves a lot of room for  improvements. Any help is much appreciated.

---

### Post by kc1di on 2014-06-10
could you also list the output from this command?
```
rfkill list all
```

---

### Post by danielr2 on 2014-06-10
```

~ $ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by danielr2 on 2014-06-12
Bump

Has anyone any idea how I can get this BCM92045NMD Broadcom Bluetooth module working ?

---

### Post by danielr2 on 2014-06-21
Since the last software update some things have changed on my system. 1. rfkill now lists Bluetooth as well: 

```

~ $ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

2. I now have 2 Bluetooth Icons displayed in the Taskbar. One is from the Blueman Applet with several options for Bluetooth connection handling, the other seems to be the soft switch to switch Bluetooth on an off. This second icon is greyed out and when I move the mouse over the Icon the pop-up tip always states "Bluetooth disabled". Clicking on this icon reveals a menu with 3 options, "Bluetooth: On", "Turn off Bluetooth" and "Preferences". The "Bluetooth: On" option is greyed out. The "Preferences" menu item always states that Bluetooth is disabled and gives the option to turn Bluetooth on. However, I can click the "Turn on Bluetooth" button as much as I like, Bluetooth remains disabled. 

According to rfkill Bluetooth should be on. According to the Blueman software it isn't. 

Do I need to load some special driver or firmware as a kernel module to get this Broadcom Bluetooth module working? So far sources on the internet haven't been too helpful to find a solution for this problem. Aside from the abundance of Broadcom related problems in the various Linux distributions, I didn't find any useful specifics regarding this particular Broadcom chip.

---

