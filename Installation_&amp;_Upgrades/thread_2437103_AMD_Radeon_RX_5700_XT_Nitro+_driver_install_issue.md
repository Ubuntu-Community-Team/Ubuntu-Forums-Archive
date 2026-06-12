---
title: "AMD Radeon RX 5700 XT Nitro+ driver install issue"
date: 2020-02-18
forum: Installation &amp; Upgrades
---

### Post by mastercore on 2020-02-18
I am having trouble getting the driver for my Radeon RX 5700 XT GPU installed

I first noticed it in  Blender. There is a place in Blender where you can select how rendering is done, and you can manually select your CPU or your GPU depending on the render engines
My system is not seeing my GPU, eventhough my screen is plugged into it.

First I tried to follow the instructions posted here ([https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-latest-amd-radeon-drivers-on-ubuntu-18-04-bionic-beaver-linux))
But at the end of the install in the Terminal I see these 2 lines at the end:

```
ERROR: Unable to install amdgpu-pro-pin.
This driver may not support the running operating system.
```

I have 2 questions:
The first is obvious: how to get this driver installed
The second: where can I see if my GPU is using the correct driver in Ubuntu?

Many thanks in advance for any help

---

### Post by mastercore on 2020-02-18
btw, I have 19.10 installed

---

### Post by P-I H on 2020-02-18
You don't have to install a specific driver. amdgpu shall be used and normally is installed during installation of Ubuntu.
Use the terminal command inxi -Fz to look at your configuration. It is however possible that some applications don't recognize the GPU. That's the case with Steam in my installation.
```
p-i@pi-asus-b450f-gaming:~$ inxi -FzSystem:    Host: pi-asus-b450f-gaming Kernel: 5.4.0-14-generic x86_64 bits: 64 Desktop: Gnome 3.34.3 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: <filter> UEFI: American Megatrends 
           v: 2704 date: 08/23/2019 
CPU:       Topology: 8-Core model: AMD Ryzen 7 1700 bits: 64 type: MT MCP L2 cache: 4096 KiB 
           Speed: 1375 MHz min/max: 1550/3750 MHz Core speeds (MHz): 1: 1373 2: 1375 3: 1375 4: 1375 5: 1357 6: 1453 7: 1372 
           8: 1357 9: 1375 10: 1372 11: 1358 12: 1733 13: 1348 14: 1349 15: 1375 16: 1372 
Graphics:  Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] driver: amdgpu 
           v: kernel 
           Display: wayland server: X.Org 1.20.7 driver: amdgpu resolution: 2560x1440~60Hz 
           OpenGL: renderer: AMD NAVI10 (DRM 3.35.0 5.4.0-14-generic LLVM 9.0.1) v: 4.5 Mesa 19.3.3 
Audio:     Device-1: Advanced Micro Devices [AMD/ATI] Navi 10 HDMI Audio driver: snd_hda_intel 
           Device-2: Advanced Micro Devices [AMD] Family 17h HD Audio driver: snd_hda_intel 
           Sound Server: ALSA v: k5.4.0-14-generic 
Network:   Device-1: Intel I211 Gigabit Network driver: igb 
           IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 680.02 GiB used: 37.94 GiB (5.6%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: SA1000M8480G size: 447.13 GiB 
           ID-2: /dev/nvme1n1 vendor: Samsung model: SSD 960 EVO 250GB size: 232.89 GiB 
           ID-3: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB 
Partition: ID-1: / size: 227.74 GiB used: 37.94 GiB (16.7%) fs: ext4 dev: /dev/nvme1n1p2 
Sensors:   System Temperatures: cpu: 38.5 C mobo: 38.0 C gpu: amdgpu temp: 56 C 
           Fan Speeds (RPM): cpu: 740 case-1: 897 case-2: 828 case-3: 582 gpu: amdgpu fan: 0 
Info:      Processes: 374 Uptime: 3h 07m Memory: 15.56 GiB used: 2.51 GiB (16.1%) Shell: bash inxi: 3.0.37 
p-i@pi-asus-b450f-gaming:~$ 

```

---

### Post by oldrocker99 on 2020-02-18
ATI, some time ago, to their great credit, worked with FOSS developers to create an open-source Radeon driver, which started a bit sketchy a decade ago, but is as good a driver as possible, just like the open-source Intel drivers.the

You can't do any better than the drivers you have.

---

### Post by mastercore on 2020-02-18
@P-I H
Do you suggest I take this issue up with the Blender community?
Blender was one of the main use cases for this setup in the first place.
My old box (8y old, but had a pretty cutting edge GPU installed for the era) rendered faster that this new box.


The output from $  inxi -Fz

```
System:
  Host: AlexTower Kernel: 5.3.0-29-generic x86_64 bits: 64 
  Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Desktop System: Gigabyte product: B450 GAMING X v: N/A 
  serial: <filter> 
  Mobo: Gigabyte model: B450 GAMING X v: x.x serial: <filter> 
  UEFI: American Megatrends v: F41 date: 07/22/2019 
CPU:
  Topology: 8-Core model: AMD Ryzen 7 1800X bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1946 MHz min/max: 2200/3600 MHz Core speeds (MHz): 1: 1959 2: 1840 
  3: 3674 4: 1870 5: 2518 6: 1837 7: 1851 8: 2325 9: 3467 10: 1838 11: 1889 
  12: 1836 13: 1835 14: 3103 15: 2271 16: 1857 
Graphics:
  Device-1: AMD Navi 10 driver: amdgpu v: kernel 
  Display: x11 server: X.Org 1.20.5 driver: ati,vesa 
  unloaded: fbdev,modesetting,radeon resolution: 1920x1080~60Hz 
  OpenGL: renderer: AMD NAVI10 (DRM 3.33.0 5.3.0-29-generic LLVM 9.0.0) 
  v: 4.5 Mesa 19.2.8 
Audio:
  Device-1: AMD Navi 10 HDMI Audio driver: snd_hda_intel 
  Device-2: AMD Family 17h HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.3.0-29-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter> 
Drives:
  Local Storage: total: 1.82 TiB used: 27.52 GiB (1.5%) 
  ID-1: /dev/nvme0n1 vendor: Toshiba model: RC500 size: 465.76 GiB 
  ID-2: /dev/sda vendor: Seagate model: ST31500541AS size: 1.36 TiB 
Partition:
  ID-1: / size: 456.95 GiB used: 27.51 GiB (6.0%) fs: ext4 
  dev: /dev/nvme0n1p3 
Sensors:
  System Temperatures: cpu: 48.2 C mobo: N/A gpu: amdgpu temp: 16 C 
  Fan Speeds (RPM): N/A gpu: amdgpu fan: 995 
Info:
  Processes: 435 Uptime: 9h 58m Memory: 31.37 GiB used: 5.50 GiB (17.5%) 
  Shell: bash inxi: 3.0.36 
```

---

### Post by P-I H on 2020-02-18
Seems to be an OpenCL problem.
Googled with "blender opencl" and set search to latest month. Found some threads that seems relevant

[https://devtalk.blender.org/t/cant-enable-opencl-for-amd-rx-5700-xt-on-linux/10274](https://devtalk.blender.org/t/cant-enable-opencl-for-amd-rx-5700-xt-on-linux/10274)
[https://forum.manjaro.org/t/blender-cant-detect-my-gpu-as-an-opencl-device/120577](https://forum.manjaro.org/t/blender-cant-detect-my-gpu-as-an-opencl-device/120577)

Perhaps this will work
[https://math.dartmouth.edu/~sarunas/amdgpu.html](https://math.dartmouth.edu/~sarunas/amdgpu.html)

---

