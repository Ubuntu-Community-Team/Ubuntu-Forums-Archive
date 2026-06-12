---
title: "Keybord issuse in asus laptop"
date: 2020-07-14
forum: Installation &amp; Upgrades
---

### Post by abhishekroy261193 on 2020-07-14
I am facing keyboard  issuse in my laptop in which some keys stops working. I have tried to find the solution from other forum by installing xserver-xorg-input. I did so  by sudo apt-get install xserver-xorg-input-all. But still I am facing the problem. 
It will be great help if anyone help me in this matter..

---

### Post by ActionParsnip on 2020-07-14
What is the full model of the system? Asus make a LOT of laptops.
Which release of Ubuntu?
Is it fully updated?
Do you have the latest BIOS?
Is this a dual boot system? If so, does everything work OK in the other OS?

---

### Post by abhishekroy261193 on 2020-07-14
**I am attaching my system info in this thread.**

System:    Host: abhishekroy-VivoBook-ASUSLaptop-X430FA-S430FA Kernel: 5.3.0-62-generic x86_64
           bits: 64 gcc: 7.5.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu4)
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: laptop System: ASUSTeK product: VivoBook_ASUSLaptop X430FA_S430FA v: 1.0 serial: N/A
           Mobo: ASUSTeK model: X430FA v: 1.0 serial: N/A
           UEFI: American Megatrends v: X430FA.308 date: 05/28/2019
Battery    BAT0: charge: 41.6 Wh 100.0% condition: 41.6/42.2 Wh (99%)
           model: ASUSTeK ASUS status: Not charging
CPU:       Quad core Intel Core i5-8265U (-MT-MCP-) 
           arch: Kaby Lake rev.12 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 14400
           clock speeds: max: 3900 MHz 1: 1305 MHz 2: 2765 MHz 3: 2992 MHz
           4: 1825 MHz 5: 1629 MHz 6: 3036 MHz 7: 3030 MHz 8: 3060 MHz
Graphics:  Card: Intel Device 3ea0 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.20.8 ) driver: i915
           Resolution: 1920x1080@60.01hz
           OpenGL: renderer: Mesa DRI Intel UHD Graphics (Whiskey Lake 3x8 GT2)
           version: 4.5 Mesa 19.2.8 Direct Render: Yes
Audio:     Card Intel Device 9dc8 driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k5.3.0-62-generic
Network:   Card: Realtek RTL8822BE 802.11a/b/g/n/ac WiFi adapter
           driver: rtw_pci port: 3000 bus-ID: 02:00.0
           IF: wlo1 state: up mac: <filter>
Drives:    HDD Total Size: 1256.3GB (3.8% used)
           ID-1: /dev/sda model: ST1000LM035 size: 1000.2GB
           ID-2: /dev/sdb model: HFS256G39TNH size: 256.1GB
Partition: ID-1: / size: 234G used: 24G (11%) fs: ext4 dev: /dev/sdb2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 285 Uptime: 26 min Memory: 1776.9/7812.8MB
           Init: systemd runlevel: 5 Gcc sys: 7.5.0
           Client: Shell (bash 4.4.201) inxi: 2.3.56 

[B]I dont have dual boot in my system.
[/B]
**I am also attaching the output from input method .**

Current configuration for the input method:
 * Active configuration: none (normally missing)
 * Normal automatic choice: ibus (normally ibus or fcitx or uim)
 * Override rule: 
 * Current override choice:  (en_IN)
 * Current automatic choice: ibus
 * Number of valid choices: 2 (normally 1)
The override rule is defined in /etc/default/im-config.
The configuration set by im-config is activated by re-starting X.
Explicit selection is not required to enable the automatic configuration if the active one is default/auto/cjkv/missing.
  Available input methods: ibus xim
Unless you really need them all, please make sure to install only one input method tool.

---

