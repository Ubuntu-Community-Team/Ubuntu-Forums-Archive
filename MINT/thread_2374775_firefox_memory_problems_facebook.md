---
title: "firefox memory problems facebook"
date: 2017-10-19
forum: MINT
---

### Post by Kevin McCready on 2017-10-19
I've been having severe memory problems which slow down the keyboard and mouse and computer. 

I suspect firefox and perhaps facebook tab. System Monitor reports usage of up to 144% CPU.  How can that be?? 

My system=
 k-Lenovo-H50-55 Kernel: 4.4.0-21-generic i686 (32 bit) Desktop: MATE 1.14.1           Distro: Linux Mint 18 Sarah

I'm sorry, I don't know the terminal command to list the memory  information that I see when I click on the system tab of the System  Monitor. But my computer is pretty new and powerful.

Grateful for any help.

---

### Post by QIII on 2017-10-19
Moved to MINT for a better fit.

---

### Post by vasa1 on 2017-10-19
```
top -bn1 -o %MEM | head -20
```or```
top -bn1 -o %CPU | head -20
```and, if you have *inxi* installed ...```
inxi -Fxzc0
```

---

### Post by Kevin McCready on 2017-10-19
```
System:    Host: k-Lenovo-H50-55 Kernel: 4.4.0-21-generic i686 (32 bit gcc: 5.3.1)
           Desktop: MATE 1.14.1 (Gtk 3.18.9-1ubuntu3.3) Distro: Linux Mint 18 Sarah
Machine:   System: LENOVO product: 90BF0032AU v: Lenovo H50-55
           Mobo: LENOVO model: Bantry CRB v: SDK0J40709 WIN Bios: LENOVO v: IRKT54AUS date: 08/20/2015
CPU:       Quad core AMD A10-7800 Radeon R7 12 Compute Cores 4C+8G (-MCP-) cache: 8192 KB
           flags: (lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 27949
           clock speeds: max: 3500 MHz 1: 1900 MHz 2: 1400 MHz 3: 1900 MHz 4: 1400 MHz
Graphics:  Card-1: Advanced Micro Devices [AMD/ATI] Kaveri [Radeon R7 Graphics] bus-ID: 00:01.0
           Card-2: Advanced Micro Devices [AMD/ATI] Oland XT [Radeon HD 8670 / R7 250/350] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD OLAND (DRM 2.43.0 / 4.4.0-21-generic, LLVM 4.0.0)
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card-1 Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel bus-ID: 00:14.2
           Card-2 Advanced Micro Devices [AMD/ATI] Kaveri HDMI/DP Audio Controller
           driver: snd_hda_intel bus-ID: 00:01.1
           Card-3 Advanced Micro Devices [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
           driver: snd_hda_intel bus-ID: 01:00.1
           Sound: Advanced Linux Sound Architecture v: k4.4.0-21-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-2: Realtek RTL8821AE 802.11ac PCIe Wireless Network Adapter
           driver: rtl8821ae port: c000 bus-ID: 05:00.0
           IF: wlp5s0 state: up mac: <filter>
Drives:    HDD Total Size: 2000.4GB (13.1% used) ID-1: /dev/sda model: ST2000DM001 size: 2000.4GB
Partition: ID-1: / size: 1.8T used: 230G (14%) fs: ext4 dev: /dev/dm-0
           ID-2: /boot size: 472M used: 97M (22%) fs: ext2 dev: /dev/sda1
           ID-3: swap-1 size: 16.05GB used: 0.00GB (0%) fs: swap dev: /dev/dm-1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 13.1C mobo: N/A gpu: 7.0,30.0
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 229 Uptime: 9:33 Memory: 1443.9/15138.9MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

---

### Post by Kevin McCready on 2017-10-19
I've just noticed pulseaudio has nice of -11 and is listed as Very High priority. I don't really need sound rated so high?

---

### Post by Kevin McCready on 2017-10-19
```
top -bn1 -o MEM% | head -20
top: unrecognized field name 'MEM%'

top -bn1 -o CPU% | head -20
top: unrecognized field name 'CPU%'

```

---

### Post by vasa1 on 2017-10-19
Sorry!

That should be %MEM or %CPU.

I'll fix my post.

---

### Post by Kevin McCready on 2017-10-19
So I closed down the browser and opened it up again and the problem, for now, isn't there but FWIW ...

```
top -bn1 -o %MEM | head -20
top - 18:39:46 up  9:52,  2 users,  load average: 0.71, 0.78, 0.73
Tasks: 227 total,   2 running, 225 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.7 us,  1.6 sy,  0.0 ni, 87.1 id,  0.6 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 15502240 total, 11051212 free,  1646604 used,  2804424 buff/cache
KiB Swap: 15675388 total, 15675388 free,        0 used. 13671304 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
16795 k         20   0 1936860 954356 136040 S  13.3  6.2   7:24.86 firefox
 2963 k         20   0  758776 280804  81620 S  13.3  1.8  12:49.12 vlc
 3105 k         20   0  347916 160596  47400 S   0.0  1.0   5:34.25 sublime_text
 1446 root      20   0  417660 146356 123832 S  13.3  0.9  23:01.60 Xorg
 2854 k         20   0  281740 117508  54924 S   0.0  0.8   2:53.96 caja
 7043 k         20   0  242516 103324  50824 S   0.0  0.7   1:45.00 pcmanfm
 2942 k         20   0  233116  57012  46016 S   0.0  0.4   0:00.48 python2
 2858 k         20   0  152128  53752  28588 S   0.0  0.3   0:03.01 mintmenu
 3381 k         20   0  141280  47900  33552 S   0.0  0.3   0:00.85 mintUpdate
16468 k         20   0  130316  42596  33100 S   0.0  0.3   4:06.90 mate-system-mon
 2870 k         20   0  114720  31508  25216 S   0.0  0.2   0:01.28 clock-applet
 2943 k         20   0   92192  29576  25500 S   0.0  0.2   0:02.64 nm-applet
 2652 k         20   0   94156  26500  22084 S   0.0  0.2   2:22.67 marco


top -bn1 -o %CPU | head -20
top - 18:38:56 up  9:51,  2 users,  load average: 0.58, 0.78, 0.73
Tasks: 227 total,   1 running, 226 sleeping,   0 stopped,   0 zombie
%Cpu(s): 10.7 us,  1.6 sy,  0.0 ni, 87.1 id,  0.6 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem : 15502240 total, 11039052 free,  1658664 used,  2804524 buff/cache
KiB Swap: 15675388 total, 15675388 free,        0 used. 13659144 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1446 root      20   0  417504 146356 123832 S  12.5  0.9  22:58.18 Xorg
 2963 k         20   0  758776 280804  81620 S   6.2  1.8  12:45.40 vlc
16795 k         20   0 1936880 966988 136028 S   6.2  6.2   7:13.36 firefox
17026 k         20   0  111056  25820  22244 S   6.2  0.2   0:00.97 mate-terminal
    1 root      20   0   24228   5380   3872 S   0.0  0.0   0:02.24 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.02 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.48 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:15.18 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:07.40 migration/0
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.14 watchdog/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.12 watchdog/1



```

---

