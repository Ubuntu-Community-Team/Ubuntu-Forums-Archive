---
title: "Stuck installing Xubuntu"
date: 2017-11-18
forum: Installation &amp; Upgrades
---

### Post by gb6903 on 2017-11-18
So I started to do a clean install of Xubuntu, wiping out the WIndows partitions. However, it seems to be stuck at this screen:  

See below

|
v

[ATTACH=CONFIG]277562[/ATTACH]



I've been trying to do a fresh install of Xubuntu, However, I get stuck at this screen:

P.S. I installed it from a USB disk,

---

### Post by vasa1 on 2017-11-18
Did you first try the Live USB successfully?

---

### Post by gb6903 on 2017-11-18
I didn' try that. But i'm still stuck here: 

And FYI Vasa, this is on a different PC then the one I was referring to in the other thread.[ATTACH=CONFIG]277567[/ATTACH]

---

### Post by vasa1 on 2017-11-18
You should always _first_ try the Live USB first to see how things work on your hardware.

---

### Post by gb6903 on 2017-11-18
Good point...but now it's too late :(. Besides, I don't know why it *wouldn't* work. I mean I don't see any good reason,

---

### Post by ajgreeny on 2017-11-18
Tell us what hardware you have and which version of Xubuntu you're trying to install.

Did you check the md5sum of the ISO file you downloaded?
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by gb6903 on 2017-11-18
Hardware: ```
****r-HP-250-G6-Notebook-PC:~$ inxi -Fxz
System:    Host: *****-HP-250-G6-Notebook-PC Kernel: 4.13.0-16-generic x86_64
           bits: 64 gcc: 7.2.0
           Desktop: Gnome 3.26.1 (Gtk 3.22.24-0ubuntu1) Distro: Ubuntu 17.10
Machine:   Device: laptop System: HP product: HP 250 G6 Notebook PC v: Type1ProductConfigId serial: N/A
           Mobo: HP model: 832A v: 23.40 serial: N/A
           UEFI: Insyde v: F.24 date: 09/25/2017
Battery    BAT1: charge: 16.5 Wh 54.0% condition: 30.6/31.1 Wh (99%)
           model: Hewlett-Packard PABAS0241231 status: Discharging
CPU:       Dual core Intel Core i5-7200U (-HT-MCP-) 
           arch: Kaby Lake rev.9 cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10848
           clock speeds: max: 3100 MHz 1: 2700 MHz 2: 2700 MHz 3: 2700 MHz
           4: 2700 MHz
Graphics:  Card: Intel HD Graphics 620 bus-ID: 00:02.0
           Display Server: wayland (X.Org 1.19.5 ) driver: i915
           Resolution: 1366x768@59.80hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 620 (Kaby Lake GT2)
           version: 4.5 Mesa 17.2.2 Direct Render: Yes
Audio:     Card Intel Device 9d71 driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.13.0-16-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: 3000 bus-ID: 01:00.0
           IF: eno1 state: down mac: <filter>
           Card-2: Intel Device 24fb driver: iwlwifi bus-ID: 02:00.0
           IF: wlo1 state: up speed: N/A duplex: N/A mac: <filter>
Drives:    HDD Total Size: 1752.6GB (28.4% used)
           ID-1: /dev/sda model: SanDisk_SD8SN8U size: 128.0GB temp: 36C
           ID-2: /dev/sdc model: Name n/a size: 500.1GB temp: 0C
           ID-3: USB /dev/sdd model: External_USB_3.0 size: 1000.2GB temp: 0C
           ID-4: USB /dev/sdb model: Ultra size: 124.2GB temp: 0C
Partition: ID-1: / size: 31G used: 9.6G (34%) fs: ext4 dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.5C mobo: 29.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 266 Uptime: 15:23 Memory: 4164.0/7897.7MB
           Init: systemd runlevel: 5 Gcc sys: 7.2.0
           Client: Shell (bash 4.4.121) inxi: 2.3.37 


```

I will check the sum now.

---

### Post by ajgreeny on 2017-11-18
It looks from your hardware printout that you already have ubuntu 17.10 on that machine with a gnome-3.26 desktop and that it is a fairly recent machine with plenty of resources.

Is that already a dual boot with the Windows you want to overwrite?
Is the machine running with UEFI or BIOS  as all the OSs on it will need to utilise the same mode to make life as simple as possible

---

