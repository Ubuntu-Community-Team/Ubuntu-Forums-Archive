---
title: "Mint 18 slow booting of 1.5 minutes"
date: 2016-08-03
forum: MINT
---

### Post by deepakdeshp on 2016-08-03
Hello,

I have upgraded from Mint 17.3 to Mint 18. The boot time is 1.5 minutes. I have opened a thread in Mint forums . [https://forums.linuxmint.com/viewtopic.php?f=46&t=225743](https://forums.linuxmint.com/viewtopic.php?f=46&t=225743)

The details of the investigation so far are
1. My swap partition had wrong uuid, after correcting the same the boot time came down to 1.5 minutes from 3 minutes.
The system details and dmesg command details are

```
 sc_scale vme vmmcall wdt xsave xsaveoptuma@uma-HP-Notebook ~ $ inxi -Fxz
System:    Host: uma-HP-Notebook Kernel: 4.4.0-31-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Cinnamon 3.0.7 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Linux Mint 18 Sarah
Machine:   System: Hewlett-Packard product: HP Notebook v: Type1ProductConfigId
           Mobo: Hewlett-Packard model: 80CC v: 99.02
           Bios: Insyde v: F.02 date: 04/01/2015
CPU:       Quad core AMD A8-7410 APU with AMD Radeon R5 Graphics (-MCP-) cache: 8192 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 17567
           clock speeds: max: 2200 MHz 1: 1300 MHz 2: 1000 MHz 3: 1000 MHz
           4: 2000 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Mullins [Radeon R4/R5 Graphics]
           bus-ID: 00:01.0
           Card-2: Advanced Micro Devices [AMD/ATI] Sun XT [Radeon HD 8670A/8670M/8690M / R5 M330]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.3 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.32hz
           GLX Renderer: Gallium 0.4 on AMD MULLINS (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller
           driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kabini HDMI/DP Audio
           driver: snd_hda_intel bus-ID: 00:01.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-31-generic
Network:   Card-1: Realtek RTL8723BE PCIe Wireless Network Adapter
           driver: rtl8723be port: 3000 bus-ID: 02:00.0
           IF: wlan0 state: up mac: <filter>
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 03:00.0
           IF: eth0 state: down mac: <filter>
Drives:    HDD Total Size: 500.1GB (16.6% used)
           ID-1: /dev/sda model: HGST_HTS545050A7 size: 500.1GB
Partition: ID-1: / size: 87G used: 73G (89%) fs: ext4 dev: /dev/sda12
           ID-2: swap-1 size: 5.35GB used: 0.00GB (0%) fs: swap dev: /dev/sda8
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 40.8C mobo: 20.0C gpu: 40.0,N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 230 Uptime: 4 min Memory: 933.1/3393.0MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.421) inxi: 2.2.35 



 
```

Dmesg problem area
```
 [FONT=Monaco] 55.038567] [drm] ib test on ring 4 succeeded in 0 usecs[/FONT]
[FONT=Monaco][  148.452514] Bluetooth: RFCOMM TTY layer initialized[/FONT]
[FONT=Monaco][  148.452530] Bluetooth: RFCOMM socket layer initialized[/FONT]
[FONT=Monaco][  148.452543] Bluetooth: RFCOMM ver 1.11[/FONT]
[FONT=Monaco][ 2854.991399] userif-3: sent link down event.[/FONT]
[FONT=Monaco][ 2854.991409] userif-3: sent link up event.[/FONT]
[FONT=Monaco][ 6082.882435] userif-3: sent link down event.[/FONT]
[FONT=Monaco][ 6082.882448] userif-3: sent link up event.
[/FONT]**[FONT=Monaco] systemd-analyze blame[/FONT]**
[FONT=Monaco]         18.672s NetworkManager-wait-online.service[/FONT]
[FONT=Monaco]         16.832s apt-daily.service[/FONT]
[FONT=Monaco]          9.696s dev-sda12.device[/FONT]
[FONT=Monaco]          8.942s vmware-USBArbitrator.service[/FONT]
[FONT=Monaco]          5.440s vmware-workstation-server.service[/FONT]
[FONT=Monaco]          5.086s accounts-daemon.service[/FONT]
[FONT=Monaco]          4.758s loadcpufreq.service[/FONT]
[FONT=Monaco]          4.711s systemd-fsck@dev-disk-by\x2duuid-3446\x2d8563.service[/FONT]
[FONT=Monaco]          3.894s networking.service[/FONT]
[FONT=Monaco]          3.698s ModemManager.service[/FONT]
[FONT=Monaco]          3.492s NetworkManager.service[/FONT]
[FONT=Monaco]          3.079s lvm2-monitor.service[/FONT]
[FONT=Monaco]          2.924s vmware.service[/FONT]
[FONT=Monaco]          2.840s samba-ad-dc.service[/FONT]
[FONT=Monaco]          2.708s speech-dispatcher.service[/FONT]
[FONT=Monaco]          2.688s console-kit-log-system-start.service[/FONT]
[FONT=Monaco]          2.641s lm-sensors.service[/FONT]
[FONT=Monaco]          2.622s gpu-manager.service[/FONT][FONT=Monaco]

[/FONT]
```

Please suggest any steps I need to take to reduce the boot time. Thank you in advance.
[COLOR=#2E8B57][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by deadflowr on 2016-08-03
*Thread moved to **MINT**.*

---

