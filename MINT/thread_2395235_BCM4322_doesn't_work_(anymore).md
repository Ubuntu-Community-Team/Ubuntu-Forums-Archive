---
title: "BCM4322 doesn't work (anymore?)"
date: 2018-06-28
forum: MINT
---

### Post by sp1een on 2018-06-28
Dear all,

I know there are Mint forums, though... I couldn't find an answer there. Thanks in advance!

I've been using Linux Mint 17.3 Rosa on a MacBook (13-inch, Aluminum, Late 2008) since August 2015. I never really had the need of upgrade this distribution as I was following the advice of do not hurry to have the latest version all the time if everything works simply fine. At the very beginning of my first installation I only had a few problems with screen regulation (brightness), which I did solve in a way I honestly don't remember (mixing up and attempt ways found on a couple of different forum, basically).

Since a couple of days ago, I never had problem with Wireless network, only a minor difficulty with EduRoam connection and the likes, which I never had the chance to make it work. However, all other typologies of network (home-based, libraries, streets, bars, restaurants, hotels, and so on...) always worked good. Now it suddenly stopped working and, although it does connect to my home network, it is not possible to browse the web, download file from Terminal, or for example update the cache of mintUpdate. I'm currently using my phone plugged and sharing connection via USB and everything listed above (and more) simply works.

I thought it was a problem of drivers: my machine is using a "Built-in AirPort Extreme Wi-Fi (based on IEEE 802.11n draft specification)" ([here]("https://support.apple.com/kb/SP500?viewlocale=en_US&locale=en_US")), or BCM4322 802.11a,  and it was working till now with the recommended driver **bcmwl-kernel-source** (vers.: 6.30.223.248).

Following a couple of discussions [here]("https://forums.linuxmint.com/viewtopic.php?f=53&t=270975&p=1481329&hilit=BCM4322#p1481329") and [here]("https://forums.linuxmint.com/viewtopic.php?f=53&t=266791"), I tried to:

[LIST]
[*]select other two listed drivers on my Driver Manager (frimware-b43-installer, 1:018-2; frimware-b43-legacyinstaller, 1:018-2): nothing changes with the first; Wireless networks did not even show in the list of networks from Panel with the second; 
[*]deactivate the device & restart, then reactivate it & restart again; 
[*]re-install the drivers with [c]sudo apt install bcmwl-kernel-source[/c], then updating dkms with [c]sudo apt install dkms[/c]: both times it says I already have the latest version (I also run [c]atp-get autoclean[/c] and [c]autoremove[/c] to be sure nothing was "stopping" this); 
[*]I finally tried [c]systemctl restart NetworkManager[/c], but it says the command *systemctl* was not found. 
[/LIST]


I haven't tried to reinstall Network Manager yet ([c]sudo apt-get install --reinstall network-manager[/c]), cause I don't want to lose a lot of different saved networks I used to work with for my job... but if you tell me is the only way I'll try.

Lastly, a more detailed info about my machine, wireless card, and Network Manager:

**inxi - Fxzs**
```
System:    Host: ***-MintBook Kernel: 3.19.0-32-generic x86_64 (64 bit gcc: 4.8.2)
           Desktop: Cinnamon 2.8.8 (Gtk 3.10.8~8+qiana) Distro: Linux Mint 17.3 Rosa
Machine:   System: Apple product: MacBook5 1 v: 1.0
           Mobo: Apple model: Mac-*** v: Proto Bios: Apple v: MB51.88Z.007D.B03.0904271443 date: 04/27/09
CPU:       Dual core Intel Core2 Duo P7350 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 7959
           clock speeds: max: 1995 MHz 1: 1596 MHz 2: 1596 MHz
Graphics:  Card: NVIDIA C79 [GeForce 9400M] bus-ID: 02:00.0
           Display Server: X.Org 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1280x800@60.2hz
           GLX Renderer: GeForce 9400M/integrated/SSE2 GLX Version: 3.3.0 NVIDIA 340.102 Direct Rendering: Yes
Audio:     Card NVIDIA MCP79 High Definition Audio driver: snd_hda_intel bus-ID: 00:08.0
           Sound: Advanced Linux Sound Architecture v: k3.19.0-32-generic
Network:   Card-1: NVIDIA MCP79 Ethernet driver: forcedeth port: 21e0 bus-ID: 00:0a.0
           IF: eth0 state: down mac: <filter>
           Card-2: Broadcom BCM4322 802.11a/b/g/n Wireless LAN Controller driver: wl bus-ID: 03:00.0
           IF: wlan0 state: down mac: <filter>
Drives:    HDD Total Size: 250.1GB (63.8% used) ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 221G used: 149G (71%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 66.0C mobo: N/A gpu: 0.0:67C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 173 Uptime: 30 min Memory: 1685.7/7729.1MB Init: Upstart runlevel: 2 Gcc sys: 4.8.4
           Client: Shell (bash 4.3.251) inxi: 2.2.28 

```

**sudo lshw** (excerpt)
```
           *-network
                description: Wireless interface
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: ***
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=*** latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:21 memory:d3100000-d3103fff

```

and finally **dpkg -l | grep network-manager**
```
ii  network-manager                                   0.9.8.8-0ubuntu7.3                                            amd64        network management framework (daemon and userspace tools)
ii  network-manager-gnome                             0.9.8.8-0ubuntu4.1-mint1                                      amd64        network management framework (GNOME frontend)
ii  network-manager-pptp                              0.9.8.2-1ubuntu2                                              amd64        network management framework (PPTP plugin core)
ii  network-manager-pptp-gnome                        0.9.8.2-1ubuntu2                                              amd64        network management framework (PPTP plugin GNOME GUI)
```

Do you think it's just broken? Can I be sure of this and... is there an easy way to replace it?

Thanks for any advice.

---

### Post by QIII on 2018-06-28
Moved to Mint.

---

### Post by sp1een on 2018-07-02
Thnaks and sorry!

---

