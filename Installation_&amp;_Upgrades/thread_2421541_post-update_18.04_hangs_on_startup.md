---
title: "post-update 18.04 hangs on startup"
date: 2019-06-23
forum: Installation &amp; Upgrades
---

### Post by cwcamp on 2019-06-23
I run ubuntu 18.04 and up until recently kernel 4.18.0.21.22. It has ran flawlessly these last few months. After I did an update I turned my computer off for the night. when I went to boot it the next day it would hang on the splash screen with the loading dots. The mouse pointer would appear but not move. Upon researching I discovered adding "nomodeset" into the boot option on the grub menu. This got me into the system but with limited functionality and I'm now stuck. I've tried a couple different kernels but all of them do the same thing. I can only boot with "nomodeset" and I need the gpu to function for my daily use. I'll include system info below here:

I have installed a few games that took a lot to make function and I desperately do not want to clean boot my system.

This is my inxi output:

System:    Host: dragon-B450-AORUS-M Kernel: 5.1.14-050114-generic x86_64
           bits: 64 gcc: 8.3.0
           Desktop: Gnome 3.28.4 (Gtk 3.22.30-1ubuntu3)
           Distro: Ubuntu 18.04.2 LTS

Machine:   Device: desktop Mobo: Gigabyte model: B450 AORUS M v: x.x serial: N/A
           UEFI: American Megatrends v: F5 date: 01/25/2019

CPU:       Quad core AMD Ryzen 5 2400G with Radeon Vega Graphics (-MT-MCP-) 
           arch: Zen rev.0 cache: 2048 KB
           
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm) bmips: 28746
           clock speeds: max: 3600 MHz 1: 1510 MHz 2: 1520 MHz 3: 2237 MHz
           4: 2247 MHz 5: 1519 MHz 6: 1592 MHz 7: 1464 MHz 8: 1451 MHz

Graphics:  Card: Advanced Micro Devices [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series]
           bus-ID: 06:00.0
           Display Server: x11 (X.Org 1.20.1 )
           drivers: fbdev,ati (unloaded: modesetting,vesa,radeon)
           Resolution: 1024x768@76.00hz
           OpenGL: renderer: llvmpipe (LLVM 9.0, 128 bits)
           version: 3.3 Mesa 19.2.0-devel - padoka PPA Direct Render: Yes

Audio:     Card-1 Advanced Micro Devices [AMD] Device 15e3
           driver: snd_hda_intel bus-ID: 06:00.6
           Card-2 Advanced Micro Devices [AMD/ATI] Device 15de
           driver: snd_hda_intel bus-ID: 06:00.1
           Sound: Advanced Linux Sound Architecture v: k5.1.14-050114-generic

Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169 port: f000 bus-ID: 03:00.0
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>

Drives:    HDD Total Size: 500.1GB (58.9% used)
           ID-1: /dev/sda model: CT500MX500SSD4 size: 500.1GB temp: 44C

Partition: ID-1: / size: 457G used: 275G (64%) fs: ext4 dev: /dev/sda2

RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present

Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A

Info:      Processes: 318 Uptime: 18 min Memory: 2597.4/14031.8MB
           Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56

journalctl doesn't show anything wrong when I run it.

edit: I forgot to mention on startup I get a black screen that says this: "AMD-Vi: Unable to write to IOMMU perf counter"

---

### Post by cwcamp on 2019-06-23
[B]I seem to have fixed it. for anyone else who might have this issue here's what I did:

1. Press escape during purple screen before loading screen to bring up grub menu
2. Pressed e key to edit and replace "quiet splash" with "nomodeset" 
3. Installed kernel 4.19 and install lightdm
4. opened a terminal and ran "sudo dpkg-reconfigure lightdm"
5. chose light DM
6. ran "sudo reboot" 

then it was working again. I guess my gdm was messed up some kinda way.
[/B]

---

