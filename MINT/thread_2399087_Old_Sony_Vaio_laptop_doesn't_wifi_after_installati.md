---
title: "Old Sony Vaio laptop doesn't wifi after installation"
date: 2018-08-21
forum: MINT
---

### Post by tackskull on 2018-08-21
Hi there  [IMG]https://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG] 

A friend of mine asked me to install Linux Mint on his Sony Vaio laptop  (a six/seven years old laptop). So I am not new with this operative  system in fact linux mint is working fine on my own laptop and the wi-fi  is working well.

The problem is that in this Sony Vaio (I can't tell you the model that  is not write on it) after a fine Mint installation doesn't see any wifi  network without getting acces to the internet. Connecting via cable the  internet is going ok if fact I am writing you from this pc. I have  enabled the broacom driver from the driver manager app but nothiing  change. I tryed to see if there is any kind of physic switch to enable  the wifi but nothing. I am not able to see any wifi from this pc.

with lspci i get:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 7 Series Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
07:00.0 Network controller: Broadcom Limited BCM43142 802.11b/g/n (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
```

with inxi -Fxzd  I get:```
System:    Host: valeria-SVF1521A1EW Kernel: 4.15.0-32-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Cinnamon 3.8.8 (Gtk 3.22.30-1ubuntu1) Distro: Linux Mint 19 Tara
Machine:   Device: laptop System: Sony product: SVF1521A1EW v: C10GX8Z0 serial: N/A
           Mobo: Sony model: VAIO serial: N/A UEFI: Insyde v: R0220DA date: 11/18/2013
Battery    BAT1: charge: 16.6 Wh 79.3% condition: 20.9/42.2 Wh (50%) model: SONY VGP-BPS35A status: N/A
CPU:       Dual core Intel Pentium 987 (-MCP-) arch: Sandy Bridge rev.7 cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3) bmips: 5986
           clock speeds: max: 1500 MHz 1: 928 MHz 2: 1036 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.96hz
           OpenGL: renderer: Mesa DRI Intel Sandybridge Mobile version: 3.3 Mesa 18.0.5 Direct Render: Yes
Audio:     Card Intel 7 Series/C216 Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-32-generic
Network:   Card-1: Broadcom Limited BCM43142 802.11b/g/n bus-ID: 07:00.0
           IF: N/A state: N/A mac: N/A
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 0e:00.0
           IF: enp14s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 500.1GB (4.8% used)
           ID-1: /dev/sda model: ST500LT012 size: 500.1GB
           Optical-1: /dev/sr0 model: MATSHITA DVD-RAM UJ8C2 rev: 1.00 dev-links: cdrom,cdrw,dvd,dvdrw
           Features: speed: 24x multisession: yes
           audio: yes dvd: yes rw: cd-r,cd-rw,dvd-r,dvd-ram state: running
Partition: ID-1: / size: 457G used: 23G (6%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 174 Uptime: 7 min Memory: 908.1/3820.8MB Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

Can you guys help me? I would very thankfull for your help :)

---

### Post by jeremy31 on 2018-08-21
Moved to Mint

---

### Post by mörgæs on 2018-08-22
Please see the footnote in the post above.

---

