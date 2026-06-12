---
title: "WOL not working"
date: 2015-12-30
forum: MINT
---

### Post by Richard_Romick on 2015-12-30
I can't seem to get WOL to work under Linux Mint, though if I boot to Windows 10 on the same system, it works fine.  That tells me it isn't my bios settings or NIC, but rather something I haven't set up right.  The attempt to WOL is over the LAN after computer has been set to suspend manually.  Here is my system info.

System:    

```
Host: senlis-System-Product-Name Kernel: 3.13.0-37-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Linux Mint 17.1 Rebecca
Machine:   Mobo: ASUSTeK model: P8Z77-V LK version: Rev X.0x Bios: American Megatrends version: 1001 date: 02/01/2013
CPU:       Quad core Intel Core i5-3570K CPU (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 28021.2 
           Clock Speeds: 1: 1600.00 MHz 2: 1700.00 MHz 3: 1600.00 MHz 4: 1600.00 MHz
Graphics:  Card: NVIDIA GK104 [GeForce GTX 670] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1920x1080@60.0hz, 1920x1080@60.0hz 
           GLX Renderer: GeForce GTX 670/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 352.63 Direct Rendering: Yes
Audio:     Card-1: NVIDIA GK104 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1
           Card-2: Intel 7 Series/C210 Series Chipset Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-37-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: d000 bus-ID: 03:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1280.3GB (10.4% used) 1: id: /dev/sda model: WDC_WD6400AAKS size: 640.1GB 
           2: id: /dev/sdb model: WDC_WD6400AAKS size: 640.1GB 
Partition: ID: / size: 579G used: 125G (23%) fs: ext4 ID: /boot size: 236M used: 48M (22%) fs: ext2 
           ID: swap-1 size: 8.53GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 0.0:27C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 184 Uptime: 17:10 Memory: 1535.3/7926.9MB Runlevel: 2 Gcc sys: 4.8.4 Client: Shell inxi: 1.8.4 

```

Settings for eth0:
```

    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```

```

/usr/bin/wakewol
#!/bin/bash
ethtool -s eth0 wol g

```

/etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
post-down /usr/bin/wakewol

```

Any help you could provide would be greatly appreciated.

---

### Post by howefield on 2015-12-30
Thread moved to the "*MINT*" forum.

---

### Post by matt_symes on 2015-12-30
Hi

```
Wake-on: g
```

The network card supports and has enabled wake on lan.

Have you sent a magic packet to the hardware interface of the ethernet card yet ?

I use wakeonlan

```
sudo apt-get install wakeonlan
```

```
wakeonlan <mac_address_of_interface>
```

I don't use it to wake from a suspend state, but i do use it to wake my backup server from a powered down (but plugged in) state.

Kind regards

---

### Post by Richard_Romick on 2015-12-30
wakeonlan was what I was using to send a magic packet to the machine.  The laptop I am sending the packet from is on the LAN.

---

### Post by CharlesA on 2015-12-30
You will more than likely need to enable the WoL flag each time the machine is booted. I had to do that with my backup server by using this script placed in /etc/init.d/

```
#!/bin/bash
## /etc/init.d/wakeonlan
#
# description: Force NIC into WOL mode
#

/sbin/ethtool -s eth0 wol g
```

I wake that machine up from a powered off state like matt_symes does.

---

