---
title: "Kernel Panic error in Ubuntu live"
date: 2020-04-13
forum: Installation &amp; Upgrades
---

### Post by imthegavereguy on 2020-04-13
I was trying to start a live session of Ubuntu, but this error keeps showing up soon after the grub menu. I'm using USB flash drive that i've prepared with rufus.

the exact error is : ---[ end Kernel panic - not syncing: Fatal exeption in interrupt ]---

what can i do to fix this???

---

### Post by CelticWarrior on 2020-04-13
Welcome.

Please post the hardware specifications -and- the Ubuntu release/version you're using.

---

### Post by imthegavereguy on 2020-04-14
here's the specifications

cpu: ryzen 5 1600
gpu: rx 580
ram: 12gb 2666mhz
mobo: msi b350 tomahawk (with newest bios firmaware)

i've tried the 18.04 and 19.10 versions on ubuntu. i've even tried a to use kali linux with an image that i had laying around but it has the same problem

---

### Post by mörgæs on 2020-04-15
Does 20.04 work better?

---

### Post by yancek on 2020-04-15
Did you verify the download before putting the iso on the usb?  When you click the download link, you should get a page similar to the one at the link blow which is for thee 18.04 version.  Just click on Verify your download.

[https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64)

---

### Post by P-I H on 2020-04-16
I have about the same hardware, that works fine.
I reinstalled Ubuntu 20.04 (daily ISO) today.
First I used Rufus in W10 to create the USB installation device. The installation device was created, but it didn't work. The new disk check utility in Ubuntu 20.04 found errors and didn't pass. In Rufus I used the settings GPT to get an UEFI installation and DD to create a disk copy on the USB.
Made an USB installation device on an Ubuntu installation with mkusb. This worked OK.
```
p-i@pi-MS-7A34:~$ inxi -Fz
System:    Kernel: 5.4.0-21-generic x86_64 bits: 64 Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: <filter> UEFI: American Megatrends 
           v: 1.H0 date: 05/02/2018 
CPU:       Topology: Quad Core model: AMD Ryzen 3 1200 bits: 64 type: MCP L2 cache: 2048 KiB 
           Speed: 1379 MHz min/max: 1550/3600 MHz Core speeds (MHz): 1: 1377 2: 1378 3: 1378 4: 1378 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X/590] driver: amdgpu 
           v: kernel 
           Display: x11 server: X.Org 1.20.8 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 DRM 3.35.0 5.4.0-21-generic LLVM 9.0.1) v: 4.6 Mesa 20.0.4 
Audio:     Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso 
           Device-2: AMD Ellesmere HDMI Audio [Radeon RX 470/480 / 570/580/590] driver: snd_hda_intel 
           Device-3: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-21-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet driver: r8169 
           IF: enp30s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 454.60 GiB used: 7.51 GiB (1.7%) 
           ID-1: /dev/sda vendor: SanDisk model: Ultra II 240GB size: 223.57 GiB 
           ID-2: /dev/sdb vendor: Samsung model: SSD 830 Series size: 119.24 GiB 
           ID-3: /dev/sdc vendor: Kingston model: SV300S37A120G size: 111.79 GiB 
Partition: ID-1: / size: 109.04 GiB used: 7.46 GiB (6.8%) fs: ext4 dev: /dev/sdc2 
Sensors:   System Temperatures: cpu: 35.5 C mobo: N/A gpu: amdgpu temp: 32 C 
           Fan Speeds (RPM): N/A gpu: amdgpu fan: 1161 
Info:      Processes: 249 Uptime: 21m Memory: 15.65 GiB used: 1.45 GiB (9.3%) Shell: bash inxi: 3.0.38 
p-i@pi-MS-7A34:~$ 

```

---

