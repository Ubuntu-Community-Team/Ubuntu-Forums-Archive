---
title: "HDMI stopped working after update"
date: 2018-11-23
forum: MINT
---

### Post by nowewiesci on 2018-11-23
I've made an update on my Linux Mint 18.3 Sylvia and HDMI for monitor stopped working. Below are things updated:

[ATTACH=CONFIG]281748[/ATTACH]
[IMG]http://wrzuc.se/i/5bf7ce6e5770c[/IMG]

$ inxi -Fxz:

[IMG]http://wrzuc.se/i/5bf7ce6e5770c[/IMG]
```

System:    Host: damian-ThinkPad-T460p Kernel: 4.15.0-39-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.6.7 (Gtk 3.18.9-1ubuntu3.3) Distro: Linux Mint 18.3 Sylvia
Machine:   System: LENOVO (portable) product: 20FXA00HPB v: ThinkPad T460p
           Mobo: LENOVO model: 20FXA00HPB v: SDK0J40705 WIN Bios: LENOVO v: R07ET69W (2.09 ) date: 07/28/2016
CPU:       Quad core Intel Core i7-6700HQ (-HT-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 20736
           clock speeds: max: 3500 MHz 1: 1842 MHz 2: 1963 MHz 3: 1558 MHz 4: 2376 MHz 5: 2124 MHz 6: 2067 MHz
           7: 2054 MHz 8: 1952 MHz
Graphics:  Card-1: Intel Skylake Integrated Graphics bus-ID: 00:02.0
           Card-2: NVIDIA GM108M [GeForce 940MX] bus-ID: 02:00.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1920x1080@60.00hz, 2560x1440@59.95hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.15.0-39-generic
Network:   Card-1: Intel Ethernet Connection (2) I219-LM driver: e1000e v: 3.2.6-k bus-ID: 00:1f.6
           IF: enp0s31f6 state: down mac: <filter>
           Card-2: Intel Wireless 8260 driver: iwlwifi bus-ID: 03:00.0
           IF: wlp3s0 state: up mac: <filter>
Drives:    HDD Total Size: 256.1GB (34.0% used) ID-1: /dev/sda model: LITEON_LCH size: 256.1GB
Partition: ID-1: / size: 219G used: 66G (32%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 391M (88%) fs: ext2 dev: /dev/sda2
           ID-3: swap-1 size: 16.90GB used: 0.00GB (0%) fs: swap dev: /dev/dm-3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 38.0C mobo: N/A
           Fan Speeds (in rpm): cpu: 2008
Info:      Processes: 310 Uptime: 38 min Memory: 2190.4/15779.8MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (zsh 5.1.1) inxi: 2.2.35 

```

How can I make my HDMI working again?

---

### Post by jeremy31 on 2018-11-23
Thread moved to Mint

---

