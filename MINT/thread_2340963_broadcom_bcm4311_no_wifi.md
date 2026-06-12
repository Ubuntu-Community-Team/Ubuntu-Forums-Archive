---
title: "broadcom bcm4311 no wifi"
date: 2016-10-23
forum: MINT
---

### Post by cheif on 2016-10-23
I have been having issues trying to get my wifi to connect. I do have ethernet connection. I have attached wireless info.txt file for further assistance.

cheifrocker@REDPILL ~ $ sudo sed -i 's/^REG.*=$/&ES/' /etc/default/crda
cheifrocker@REDPILL ~ $ inxi -Fxz
System:    Host: REDPILL Kernel: 4.4.0-43-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.0.6 (Gtk 3.18.9-1ubuntu3)
           Distro: Linux Mint 18 Sarah
Machine:   System: Dell (portable) product: Latitude D830
           Mobo: Dell model: 0UY141 Bios: Dell v: A04 date: 08/08/2007
CPU:       Dual core Intel Core2 Duo T7100 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 7182
           clock speeds: max: 1801 MHz 1: 1200 MHz 2: 1200 MHz
Graphics:  Card: NVIDIA G86M [Quadro NVS 140M] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1280x800@63.15hz
           GLX Renderer: Quadro NVS 140M/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 340.96 Direct Rendering: Yes
Audio:     Card Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-43-generic
Network:   Card-1: Broadcom NetXtreme BCM5755M Gigabit Ethernet PCI Express
           driver: tg3 v: 3.137 bus-ID: 09:00.0
           IF: enp9s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Broadcom BCM4311 802.11a/b/g bus-ID: 0c:00.0
           IF: N/A state: N/A mac: N/A
Drives:    HDD Total Size: 250.1GB (3.8% used)
           ID-1: /dev/sda model: ST9250315AS size: 250.1GB temp: 44C
Partition: ID-1: / size: 227G used: 6.1G (3%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 54.0C mobo: N/A gpu: 0.0:63C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 171 Uptime: 24 min Memory: 995.1/3006.9MB
           Init: systemd runlevel: 5 Gcc sys: 5.3.1
           Client: Shell (bash 4.3.421) inxi: 2.2.35 
cheifrocker@REDPILL ~ $ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
    Subsystem: Dell NetXtreme BCM5755M Gigabit Ethernet PCI Express [1028:01fe]
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel modules: ssb, wl
cheifrocker@REDPILL ~ $ wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && chmod +x wireless-info && ./wireless-info
--2016-10-23 19:41:07--  [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info)
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info) [following]
--2016-10-23 19:41:08--  [https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info](https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.32.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.32.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: ‘wireless-info’

wireless-info       100%[===================>]  15.78K  --.-KB/s    in 0.02s   

Last-modified header missing -- time-stamps turned off.
2016-10-23 19:41:08 (663 KB/s) - ‘wireless-info’ saved [16156/16156]


Results saved in "/home/cheifrocker/wireless-info.txt".

---

### Post by chili555 on 2016-10-23
You have the wrong driver. Please hook up the ethernet for a few moments and open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Reboot.

NOTE: The procedure I gave you is correct for Ubuntu. I do not know about this:> Distro: Linux Mint 18 Sarah

---

### Post by jeremy31 on 2016-10-23
*Thread moved to **MINT**.*

I think chili555's advise will work great in LM18

---

### Post by cheif on 2016-10-23
Thank you for the assistance. I entered the codes into terminal and rebooted. Still no wifi. Is there something I am missing?

---

### Post by chili555 on 2016-10-23
Please let us see:```
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by cheif on 2016-10-24
cheifrocker@REDPILL ~ $ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by cheif on 2016-10-24
I finally got the wifi up from the linux mint forum thread that I started.  Thank you for your help.

[https://forums.linuxmint.com/viewtopic.php?f=53&t=232330](https://forums.linuxmint.com/viewtopic.php?f=53&t=232330)

---

