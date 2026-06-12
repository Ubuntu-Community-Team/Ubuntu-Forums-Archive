---
title: "after updates applied to 16.04 can't use launcher, reboots desktop"
date: 2018-01-07
forum: Installation &amp; Upgrades
---

### Post by carlf39 on 2018-01-07
used standard software update app before I closed down last night. today, after boot up everything looks good until you try to use launcer, then desktop reboots.  tried to look at files and desktop reboots.  tried to shutdown system from menu and desktop reboots.  Sort of the pattern from anything on the gui desktop.  in order to start browser to log this I had to start a terminal with cntl+alt+t.

help! Help HELP!!!

here is the results on my system from inxi -Fxz ...

carlf39@Inspiron-1110:~$ inxi -Fxz
System:    Host: Inspiron-1110 Kernel: 4.10.0-28-generic i686 (32 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Dell model: 0KC6FD v: A06 Bios: Dell v: A06 date: 12/01/2009
CPU:       Single core Intel Celeron 743 (-UP-) cache: 1024 KB
           flags: (lm nx pae sse sse2 sse3 ssse3) bmips: 2593 speed: 1296 MHz (max)
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.08hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express x86/MMX/SSE2
           GLX Version: 2.1 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-28-generic
Network:   Card-1: Qualcomm Atheros AR8132 Fast Ethernet
           driver: atl1c v: 1.0.1.1-NAPI port: 2000 bus-ID: 02:00.0
           IF: enp2s0 state: down mac: <filter>
           Card-2: Broadcom BCM4312 802.11b/g LP-PHY
           driver: wl bus-ID: 08:00.0
           IF: wlp8s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (2.9% used)
           ID-1: /dev/sda model: ST1000LM048 size: 1000.2GB temp: 32C
Partition: ID-1: / size: 189G used: 26G (15%) fs: ext4 dev: /dev/sda3
           ID-2: swap-1 size: 2.07GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 49.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 187 Uptime: 26 min Memory: 718.6/1942.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

