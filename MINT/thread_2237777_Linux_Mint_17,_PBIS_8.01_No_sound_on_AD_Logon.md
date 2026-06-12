---
title: "Linux Mint 17, PBIS 8.01 No sound on AD Logon"
date: 2014-08-03
forum: MINT
---

### Post by calvin9 on 2014-08-03
I have no sound when I authenticate to AD. When I logon with an AD account I also have the software rendering mode message. If I logon with a local account I do not have this problem.

~ $ sudo inxi -Fx

System:    Host: mint-laptop Kernel: 3.13.0-24-generic x86_64 (64 bit, gcc: 4.8.2) Desktop: N/A Distro: Linux Mint 17 Qiana
Machine:   System: Hewlett-Packard product: HP PAVILIONDV6T-6100NOTEBOOK version: 058C110000244720001620100 serial: 5CH138114Q 
           Mobo: Hewlett-Packard model: 1658 version: 10.31 serial: PBZBB01HT1E39T
           Bios: Hewlett-Packard version: F.1B date: 10/05/2011
CPU:       Dual core Intel Core i5-2410M CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9178.72 
           Clock Speeds: 1: 2301.00 MHz 2: 800.00 MHz 3: 800.00 MHz 4: 2301.00 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0 
           X.org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) tty size: 80x24 Advanced Data: N/A for root 
Audio:     Card: Intel 6 Series/C200 Series Chipset Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-24-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: 4000 bus-ID: 01:00.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 10:1f:74:17:4e:1a
Drives:    HDD Total Size: 750.2GB (0.6% used) 1: id: /dev/sda model: WDC_WD7500BPKT size: 750.2GB temp: 55C 
Partition: ID: / size: 71G used: 3.6G (6%) fs: ext4 ID: /boot size: 180M used: 44M (27%) fs: ext4 
           ID: /tmp size: 4.5G used: 9.5M (1%) fs: ext4 ID: /home size: 14G used: 153M (2%) fs: ext4 
           ID: /var size: 9.1G used: 532M (7%) fs: ext4 ID: swap-1 size: 12.00GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 80.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 234 Uptime: 1:34 Memory: 1419.8/5916.5MB Runlevel: 2 Gcc sys: 4.8.2 Client: Shell inxi: 1.8.4

---

### Post by coffeecat on 2014-08-04
*Thread moved to **Other Operating Systems and Projects**.*

---

