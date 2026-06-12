---
title: "Ubuntu 24.04 LTS - I can't install, error without any logs"
date: 2024-07-15
forum: Installation &amp; Upgrades
---

### Post by domsad on 2024-07-15
Hello, 

I have a problem with installation new Ubuntu on my laptop. Every time I try to install, an error window appears without any logs [https://imgur.com/a/6bY7iY0](https://imgur.com/a/6bY7iY0). I don't have idea why it doesn't work, it's not the first Linux I've installed on this laptop, but It's first time i have such a big problem with that. I would be grateful if someone could help me solve this problem. 

inxi:

```
System:
  Kernel: 6.8.0-31-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
  Desktop: GNOME v: 46.0 Distro: Ubuntu 24.04 LTS (Noble Numbat)
Machine:
  Type: Laptop System: LENOVO product: 81FK v: Lenovo ideapad 330-15ICH
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: NO DPK serial: <superuser required>
    UEFI: LENOVO v: 7ZCN37WW date: 11/27/2020
Battery:
  ID-1: BAT0 charge: 4.8 Wh (100.0%) condition: 4.8/45.3 Wh (10.7%)
    volts: 12.3 min: 11.4 model: Celxpert L17C3PB0 status: full
CPU:
  Info: quad core model: Intel Core i5-8300H bits: 64 type: MT MCP
    arch: Coffee Lake rev: A cache: L1: 256 KiB L2: 1024 KiB L3: 8 MiB
  Speed (MHz): avg: 2300 min/max: 800/4000 cores: 1: 2300 2: 2300 3: 2300
    4: 2300 5: 2300 6: 2300 7: 2300 8: 2300 bogomips: 36799
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CoffeeLake-H GT2 [UHD Graphics 630] vendor: Lenovo
    driver: i915 v: kernel arch: Gen-9.5 bus-ID: 00:02.0
  Device-2: NVIDIA GP107M [GeForce GTX 1050 Mobile] vendor: Lenovo
    driver: nouveau v: kernel arch: Pascal bus-ID: 01:00.0 temp: 44.0 C
  Device-3: Chicony EasyCamera driver: uvcvideo type: USB bus-ID: 1-8:4
  Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: iris gpu: i915 resolution:
    1: 1920x1080~75Hz 2: N/A
  API: EGL v: 1.5 drivers: iris,nouveau,swrast platforms:
    active: gbm,x11,surfaceless,device inactive: wayland
  API: OpenGL v: 4.6 compat-v: 4.3 vendor: intel mesa v: 24.0.5-1ubuntu1
    glx-v: 1.4 direct-render: yes renderer: Mesa Intel UHD Graphics 630 (CFL
    GT2)
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  API: ALSA v: k6.8.0-31-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active
Network:
  Device-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
    vendor: Lenovo driver: ath10k_pci v: kernel bus-ID: 07:00.0
  IF: wlp7s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet
    vendor: Lenovo RTL8111/8168/8411 driver: r8169 v: kernel port: 3000
    bus-ID: 08:00.0
  IF: enp8s0 state: down mac: <filter>
Bluetooth:
  Device-1: Qualcomm Atheros driver: btusb v: 0.8 type: USB bus-ID: 1-14:6
  Report: hciconfig ID: hci0 rfk-id: 2 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
Drives:
  Local Storage: total: 1.2 TiB used: 5.72 GiB (0.5%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB256HBHQ-000L2
    size: 238.47 GiB temp: 45.9 C
  ID-2: /dev/sda vendor: Western Digital model: WD10SPZX-24Z10
    size: 931.51 GiB
  ID-3: /dev/sdb vendor: SanDisk model: Ultra USB 3.0 size: 57.3 GiB
    type: USB
Partition:
  ID-1: / size: 3.82 GiB used: 273.2 MiB (7.0%) fs: overlay source: ERR-102
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 51.0 C pch: 53.0 C mobo: N/A gpu: nouveau
    temp: 44.0 C
  Fan Speeds (rpm): N/A
Info:
  Memory: total: 8 GiB available: 7.63 GiB used: 3.22 GiB (42.2%)
  Processes: 324 Uptime: 23m Init: systemd target: graphical (5)
  Packages: 1825 Compilers: N/A Shell: Bash v: 5.2.21 inxi: 3.3.34

```

---

