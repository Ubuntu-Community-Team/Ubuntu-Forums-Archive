---
title: "Wireless connection dropping"
date: 2017-12-15
forum: MINT
---

### Post by Nap1812 on 2017-12-15
Hope someone here can help me figure out why my wireless connection drops and reconnects at random intervals. However, if I open a terminal and run a ping the connection will not drop while the ping is running. If I stop the ping I notice the same behavior, wireless connection drops and reconnects after a while. If you can assist please let me know what information is beneficial. I can post logs and provide detail.


Help is greatly appreciated. Thanks...

```

System:    Host: linux Kernel: 4.10.0-38-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.6.6 (Gtk 3.18.9-1ubuntu3.3)
Machine:   System: LENOVO (portable) product: 20CLS11H00 v: ThinkPad X250
           Mobo: LENOVO model: 20CLS11H00 v: SDK0E50510 WIN
           Bios: LENOVO v: N10ET33W (1.12 ) date: 04/06/2015
CPU:       Dual core Intel Core i5-5300U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9178
           clock speeds: max: 2900 MHz 1: 799 MHz 2: 799 MHz 3: 799 MHz
           4: 799 MHz
Graphics:  Card: Intel Broadwell-U Integrated Graphics bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Broadwell-U Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-38-generic
Network:   Card-1: Intel Ethernet Connection (3) I218-LM
           driver: e1000e v: 3.2.6-k port: 3080 bus-ID: 00:19.0
           IF: enp0s25 state: down mac: <filter>
           Card-2: Intel Wireless 7265 driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 256.1GB (9.3% used)
           ID-1: /dev/sda model: SAMSUNG_MZ7LN256 size: 256.1GB
Partition: ID-1: / size: 219G used: 6.8G (4%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 126M (28%) fs: ext2 dev: /dev/sda2
           ID-3: swap-1 size: 17.05GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Unmounted: ID-1: /dev/sda3 size: 255.01G
           label: N/A uuid: e446367a-2490-40b5-9162-bf539ec990a4
           ID-2: /dev/dm-0 size: 255.01G label: N/A uuid: N/A
           ID-3: /dev/dm-2 size: 17.05G
           label: N/A uuid: ecdf42cc-effb-405e-b682-d9d4dcd879fe
Sensors:   System Temperatures: cpu: 29.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 304 Uptime: 17:38 Memory: 1926.5/15924.4MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

```

---

### Post by luca31 on 2017-12-17
Hi, I would try to disable the powersave on the card

sudo iwconfig wlp3s0 power off

to see if the problem persist
if you use network-manager glance the relative option on the [documentation]("https://docs.ubuntu.com/core/en/stacks/network/network-manager/docs/reference/snap-configuration/wifi-powersave")

---

### Post by jeremy31 on 2017-12-17
*Thread moved to **MINT**.*

---

