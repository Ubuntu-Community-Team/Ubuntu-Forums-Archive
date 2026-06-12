---
title: "ACER V15 Nitro sound issues - LM17.1 64bit"
date: 2015-05-31
forum: MINT
---

### Post by martin154 on 2015-05-31
Hi,

i recently purchased a new acer VN7 571G 5050 which  unfortunately has the qualcomm NFA344 wifi and bluetooth chip which is  not yet supported by linux. will be using an EDIMAX dongle till the linux update  arrives which supports this card.

almost everything else is working, I am just having problems with sound.

1. periodic clicking from the speakers every 20 seconds or so in battery mode
2.  no sound though hdmi, no possibility to select sound through hdmi in  the sound settings. If i install pavucontrol there is no hdmi setting in  the profiles either

if anyone could give me some pointers it would be appreciated. sound through the speakers and headphone jack is fine!

here a little more info abut my setup. BIOS is current and I am running the latest 3.19 Kernel.

jones@jones-aspire ~ $ inxi -Fxz
System:    Host: jones-aspire Kernel: 3.19.0-18-generic x86_64 (64 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Linux Mint 17.1 Rebecca
Machine:   Mobo: Acer model: Aspire VN7-571G version: V1.14 Bios: Insyde version: V1.14 date: 01/08/2015
CPU:        Dual core Intel Core i5-5200U CPU (-HT-MCP-) cache: 3072 KB  flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 8779.82 
           Clock Speeds: 1: 2650.226 MHz 2: 2689.585 MHz 3: 2672.914 MHz 4: 2682.453 MHz
Graphics:  Card: Intel Broadwell-U Integrated Graphics bus-ID: 00:02.0 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@60.0hz 
           GLX Renderer: Mesa DRI Intel Broadwell GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Intel Wildcat Point-LP High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2: Intel Broadwell-U Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-18-generic
Network:   Card-1: Qualcomm Atheros Device 003e bus-ID: 03:00.0
           IF: N/A state: N/A speed: N/A duplex: N/A mac: N/A
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller 
           driver: r8169 ver: 2.3LK-NAPI port: 4000 bus-ID: 02:00.0
           IF: eth0 state: down mac: <filter>
           Card-3: Edimax EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS] driver: rtl8192cu usb-ID: 7392:7811
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (1.3% used) 1: id: /dev/sda model: ST500LM000 size: 500.1GB 
Partition: ID: / size: 451G used: 5.9G (2%) fs: ext4 ID: swap-1 size: 8.50GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 44.0C mobo: 38.0C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 241 Uptime: 1:00 Memory: 528.1/7903.9MB Runlevel: 2 Gcc sys: 4.8.2 Client: Shell inxi: 1.8.4 
jones@jones-aspire ~ $

thanks for your help

---

### Post by martin154 on 2015-06-02
anyone??

---

