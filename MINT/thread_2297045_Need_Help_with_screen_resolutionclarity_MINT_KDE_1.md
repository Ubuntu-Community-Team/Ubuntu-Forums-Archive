---
title: "Need Help with screen resolution/clarity MINT KDE 17.2"
date: 2015-09-30
forum: MINT
---

### Post by Stosskraft on 2015-09-30
Hello all, I just bought a new HP all in one with 23' LED display. I have just installed linux mint 17 and did the upgrade to 17.2. Now the display looks terrible, everything is fuzzy and not clear. However when I right click on the desktop to change the wall paper, I can display wall paper at 5312x2976 yet in the display settings I am limited to : 192ox1080



```
xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 32767 x 32767
eDP1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      59.0*+
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
But I am lost besides that. Please help

> inxi -Fxz
System: Host: yanek-23-r009 Kernel: 3.13.0-24-generic x86_64 (64 bit, gcc: 4.8.2)
Desktop: KDE 4.14.2 (Qt 4.8.6) Distro: Linux Mint 17.2 Rafaela
Machine: System: Hewlett-Packard product: 23-r009 version: 1.00
Mobo: Hewlett-Packard model: 2B3C version: 1.02 Bios: AMI version: 80.01 date: 03/04/2015
CPU: Dual core Intel Core i3-4160T CPU (-HT-MCP-) cache: 3072 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 12371.6
Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz 3: 800.00 MHz 4: 800.00 MHz
Graphics: Card: Intel Device 041e bus-ID: 00:02.0
X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 1920x1080@59.0hz
GLX Renderer: Mesa DRI Intel Haswell GLX Version: 3.0 Mesa 10.1.0 Direct Rendering: Yes
Audio: Card-1: Intel 8 Series/C220 Series High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
Card-2: Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
Sound: Advanced Linux Sound Architecture ver: k3.13.0-24-generic
Network: Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
driver: r8169 ver: 2.3LK-NAPI port: d000 bus-ID: 05:00.0
IF: eth0 state: down mac: <filter>
Card-2: Realtek RTL8188EE Wireless Network Adapter driver: rtl8188ee port: e000 bus-ID: 04:00.0
IF: wlan0 state: up mac: <filter>
Drives: HDD Total Size: 1000.2GB (0.7% used) 1: id: /dev/sda model: ST1000DM003 size: 1000.2GB
Partition: ID: / size: 909G used: 6.3G (1%) fs: ext4 ID: swap-1 size: 8.50GB used: 0.00GB (0%) fs: swap
RAID: No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors: System Temperatures: cpu: 29.8C mobo: 27.8C
Fan Speeds (in rpm): cpu: N/A
Info: Processes: 179 Uptime: 15 min Memory: 1150.3/7901.5MB Runlevel: 2 Gcc sys: 4.8.4
Client: Shell (bash 4.3.11) inxi: 1.9.17

Photos of problem: [img][IMG]http://i300.photobucket.com/albums/nn35/yrolling/snapshot1_zpse2gdards.png[/IMG][/img]

[img][IMG]http://i300.photobucket.com/albums/nn35/yrolling/mag2.jpeg_zpso5pf6jma.png[/IMG][/img]

> uname -a
Linux yanek-23-r009 3.19.0-30-generic #33~14.04.1-Ubuntu SMP Tue Sep 22 09:27:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

