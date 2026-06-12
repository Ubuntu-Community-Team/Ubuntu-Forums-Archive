---
title: "I can't use any distro without &quot;acpi=off nolapic&quot; kernel parameters"
date: 2020-02-11
forum: Installation &amp; Upgrades
---

### Post by gencoglutugrul on 2020-02-11
Hello guys i bought a new laptop and try to install ubuntu but i get some error messages (about acpi). Later that i try to install another distros for example debian, manjaro ... But no one works. After that i research that error and find acpi parameters can work. And finally i install ubuntu with using acpi=off and nolapic kernel parameters. I can also boot with using this parameters but for example i can't get any info about my battery. When i try to boot without acpi parameters i get errors like in image;
[IMG]https://i.hizliresim.com/6M7BNl.png[/IMG]


What i try to solve this problem;
- Update Kernel to 5.5.2 with ukuu
- Some of another acpi parameters like acpi_osi, acpi=strict, acpi=force ...
- Installed nvidia driver
- Disabled nouveau
- Some of another nouveau kernel parameters like nouveau.modeset=0, nomodeset, nouveau.blacklist=1, modprobe.blacklist=nouveau
Sadly no one works :(

System Informations;
$ uname -a
```
Linux casper 5.5.2-050502-generic #202002041931 SMP Tue Feb 4 19:33:15 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

$ [COLOR=#333333][FONT=&amp]lsb_release -a
```
[/FONT][/COLOR]No LSB modules are available.Distributor ID:    Ubuntu
Description:    Ubuntu 19.10
Release:    19.10
Codename:    eoan

```[COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]
$ inxi -Fxxxx
```
System:
  Host: casper Kernel: 5.5.2-050502-generic x86_64 bits: 64 compiler: gcc 
  v: 9.2.1 Desktop: Gnome 3.34.1 wm: gnome-shell dm: GDM3 3.34.1 
  Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Laptop Mobo: CASPER BILGISAYAR SISTEMLERI.A.S model: F15KR 002 
  v: 1.0 serial: <root required> UEFI: INSYDE v: 205 date: 03/30/2018 
CPU:
  Topology: Single Core model: Intel Core i5-8250U bits: 64 type: MCP 
  arch: Kaby Lake rev: A L2 cache: 6144 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 3600 
  Speed: 800 MHz min/max: 400/3400 MHz Core speed (MHz): 1: 800 
Graphics:
  Device-1: Intel UHD Graphics 620 vendor: Pegatron driver: i915 v: kernel 
  bus ID: 00:02.0 chip ID: 8086:5917 
  Device-2: NVIDIA GM108M [GeForce MX130] vendor: Pegatron driver: N/A 
  bus ID: 01:00.0 chip ID: 10de:174d 
  Display: x11 server: X.Org 1.20.5 driver: none compositor: gnome-shell 
  resolution: 1600x900_60.00~60Hz 
  OpenGL: renderer: Mesa DRI Intel UHD Graphics 620 (Kabylake GT2) 
  v: 4.5 Mesa 19.2.8 compat-v: 3.0 direct render: Yes 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Pegatron 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 chip ID: 8086:9d71 
  Sound Server: ALSA v: k5.5.2-050502-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Pegatron driver: r8169 v: kernel port: 4000 bus ID: 02:00.0 
  chip ID: 10ec:8168 
  IF: enp2s0 state: down mac: 54:b2:03:1e:2c:d7 
  Device-2: Realtek RTL8723BE PCIe Wireless Network Adapter 
  vendor: AzureWave driver: rtl8723be v: kernel port: 3000 bus ID: 03:00.0 
  chip ID: 10ec:b723 
  IF: wlp3s0 state: up mac: d0:c5:d3:ef:38:95 
Drives:
  Local Storage: total: 223.57 GiB used: 13.82 GiB (6.2%) 
  ID-1: /dev/sda vendor: Kingston model: SA400M8240G size: 223.57 GiB 
  speed: 6.0 Gb/s serial: 50026B728248B70A rev: 61E1 scheme: GPT 
Partition:
  ID-1: / size: 218.57 GiB used: 13.80 GiB (6.3%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 41.5 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 215 Uptime: 4h 23m Memory: 7.69 GiB used: 2.33 GiB (30.3%) 
  Init: systemd v: 242 runlevel: 5 Compilers: gcc: 9.2.1 alt: 9 Shell: zsh 
  v: 5.7.1 running in: gnome-terminal inxi: 3.0.36 

```
[COLOR=#333333][FONT=&amp]
[/FONT][/COLOR]

---

### Post by ubfan1 on 2020-02-11
Check with HP for any BIOs/firmware updates, they may help, although with an i5, that's not as likely to be the problem as with a new Ryzen.

---

### Post by gencoglutugrul on 2020-03-08
I just updated bios now and what i get is same acpi error but this time if i use acpi=off and nolapic i get a new kernel error "no msi-x/msi found" i just want to use linux distro not so much
I also tried to add pci=nomsi but it is not work

---

### Post by CelticWarrior on 2020-03-08
Instead of those parameters try 'nomodeset'. If that alone doesn't work try the other ones one at the time, keep 'nomodeset' (because Nvidia...).

---

