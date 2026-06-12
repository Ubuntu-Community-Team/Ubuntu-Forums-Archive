---
title: "system bios recovery occurred(Error500)"
date: 2017-11-24
forum: Installation &amp; Upgrades
---

### Post by ucma on 2017-11-24
Hello!

When I switch on my Compaq 420 the screen auto starts without me pushing the power switch and then restarts after a few seconds to be presented with this error message :

Memory Size changed:System Reboot
A system bios recovery has occurred 
Bios Recovery (500)

After that it restarts again and shows the grub menu as usual multiboot(linuxmint18.2 and edu-ubuntu 14.4). After that there does not seem to be any problem except runs a bit slow.

There is no provision to install HP Support assistant for eduubuntu/linuxmint as the .exe files would not go AND I WANT TO INSTALL IT for the better. Kindly guide me how to do it in linux?

Pl. help me with some way so I do not get this message.Also i am **not sure whether to update/reinstallBIOS and if it that critical** as i am able to use my notebook after booting up.

utkarsh10


DETAILS:

System:    Host: uc-Compaq-420 Kernel: 4.4.0-83-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.4.6 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Linux Mint 18.2 Sonya
Machine:   System: Hewlett-Packard product: Compaq 420 v: F.20
           
           Mobo: Hewlett-Packard model: 1526 v: KBC Version 71.0E
            Manufacturer: Hewlett-Packard
    Product Name: Compaq 420
    Version: F.20
    Serial Number: CNU0215Z3V
    UUID: 40469898-DFD9-E011-BF86-8580BF0C50B5
    Wake-up Type: Power Switch
    SKU Number: WT741PA#ACJ
    Family: 103C_5336AN

           Bios: Hewlett-Packard v: 68PVI Ver. F.20 date: 12/12/2011
CPU:       Dual core Intel Core2 Duo T6570 (-MCP-) cache: 2048 KB
           flags: (lm nx sse sse2 sse3 sse4_1 ssse3 vmx) bmips: 8378
           clock speeds: max: 2101 MHz 1: 1200 MHz 2: 1200 MHz
Graphics:  Card: Intel Mobile 4 Series Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Servesr: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@59.64hz
           GLX Renderer: Mesa DRI Mobile Intel GM45 Express
           GLX Version: 2.1 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card Intel 82801I (ICH9 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-83-generic
Network:   Card: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: 2000 bus-ID: 84:00.0
           IF: ens5 state: down mac: <filter>
Drives:    HDD Total Size: 320.1GB (5.6% used)
           ID-1: /dev/sda model: WDC_WD3200BEKT size: 320.1GB
Partition: ID-1: / size: 26G used: 15G (61%) fs: ext4 dev: /dev/sda8
           ID-2: swap-1 size: 2.10GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 50.0C mobo: 16.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 169 Uptime: 6 min Memory: 677.3/1928.6MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

---

### Post by irv on 2017-11-29
Something like this happened to me awhile back and it turned out to be a loose memory. I had to remove the memory and reseat it in the slots. This fixed the problem.
I don't know if this is your problem or not, but it is worth a try.

---

