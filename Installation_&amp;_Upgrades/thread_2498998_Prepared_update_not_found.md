---
title: "Prepared update not found?"
date: 2024-07-07
forum: Installation &amp; Upgrades
---

### Post by chicocanada on 2024-07-07
Hi all, I don't know how to resolved this 'Prepared update not found issue'. Any ideas?

---

### Post by ajgreeny on 2024-07-07
We need much more information to help you.

Please show us the full output of commands ```
inxi -Fzx
``` followed by ```
sudo apt update && sudo apt upgrade
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by chicocanada on 2024-08-26
~$ inxi -Fzx
System:
  Kernel: 6.8.0-40-generic x86_64 bits: 64 compiler: N/A
    Desktop: Cinnamon 5.2.7 Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 20RD002UUS v: ThinkPad E15
    serial: <superuser required>
  Mobo: LENOVO model: 20RD002UUS v: SDK0J40697 WIN
    serial: <superuser required> UEFI: LENOVO v: R16ET26W (1.12 )
    date: 06/08/2020
Battery:
  ID-1: BAT0 charge: 40.8 Wh (100.0%) condition: 40.8/45.7 Wh (89.2%)
    volts: 12.3 min: 11.1 model: SMP 5B10W138 status: Full
CPU:
  Info: quad core model: Intel Core i7-10510U bits: 64 type: MT MCP
    arch: Comet/Whiskey Lake note: check rev: C cache: L1: 256 KiB L2: 1024 KiB
    L3: 8 MiB
  Speed (MHz): avg: 450 high: 800 min/max: 400/4900 cores: 1: 400 2: 400
    3: 400 4: 400 5: 400 6: 400 7: 400 8: 800 bogomips: 36799
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel CometLake-U GT2 [UHD Graphics] vendor: Lenovo driver: i915
    v: kernel bus-ID: 00:02.0
  Device-2: Acer Integrated Camera type: USB driver: uvcvideo bus-ID: 1-8:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel UHD Graphics (CML GT2)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
Audio:
  Device-1: Intel Comet Lake PCH-LP cAVS vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Sound Server-1: ALSA v: k6.8.0-40-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Lenovo driver: r8169 v: kernel port: 3000 bus-ID: 04:00.0
  IF: enp4s0 state: down mac: <filter>
  Device-2: Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter
    vendor: Lenovo driver: rtw_8822ce v: N/A port: 2000 bus-ID: 05:00.0
  IF: wlp5s0 state: up mac: <filter>
Bluetooth:
  Device-1: Realtek 802.11ac WLAN Adapter type: USB driver: btusb v: 0.8
    bus-ID: 1-10:5
  Report: hciconfig ID: hci0 rfk-id: 7 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.1
Drives:
  Local Storage: total: 223.57 GiB used: 120.94 GiB (54.1%)
  ID-1: /dev/sda vendor: PNY model: CS2211 240GB SSD size: 223.57 GiB
Partition:
  ID-1: / size: 218.51 GiB used: 120.94 GiB (55.3%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 456 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 53.0 C pch: 50.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 330 Uptime: 3d 22h 15m Memory: 15.31 GiB used: 6.41 GiB (41.9%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2934 Shell: Bash
  v: 5.1.16 inxi: 3.3.13







~$ sudo apt update && sudo apt upgrade
[sudo] password for chicocanada: 
Hit:1 [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) focal InRelease         
Hit:2 [https://ocean.surfshark.com/debian](https://ocean.surfshark.com/debian) stretch InRelease                     
Hit:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) jammy InRelease                      
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [129 kB]      
Get:5 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) jammy-updates InRelease [128 kB]     
Get:6 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) jammy-apps-security InRelease [7,553 B]
Hit:7 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                        
Get:8 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) jammy-apps-updates InRelease [7,456 B]
Get:9 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-security InRelease [7,450 B]
Hit:10 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) jammy-backports InRelease           
Get:11 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-updates InRelease [7,449 B]
Fetched 287 kB in 2s (157 kB/s)       
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: [http://download.virtualbox.org/virtualbox/debian/dists/focal/InRelease:](http://download.virtualbox.org/virtualbox/debian/dists/focal/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libsdl-ttf2.0-0
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
  python3-update-manager update-manager update-manager-core
The following packages will be upgraded:
  libpython3-stdlib python3 python3-minimal shim-signed
4 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/722 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 468534 files and directories currently installed.)
Preparing to unpack .../python3-minimal_3.10.6-1~22.04.1_amd64.deb ...
Unpacking python3-minimal (3.10.6-1~22.04.1) over (3.10.6-1~22.04) ...
Setting up python3-minimal (3.10.6-1~22.04.1) ...
(Reading database ... 468534 files and directories currently installed.)
Preparing to unpack .../python3_3.10.6-1~22.04.1_amd64.deb ...
running python pre-rtupdate hooks for python3.10...
Unpacking python3 (3.10.6-1~22.04.1) over (3.10.6-1~22.04) ...
Preparing to unpack .../libpython3-stdlib_3.10.6-1~22.04.1_amd64.deb ...
Unpacking libpython3-stdlib:amd64 (3.10.6-1~22.04.1) over (3.10.6-1~22.04) ...
Preparing to unpack .../shim-signed_1.51.4+15.8-0ubuntu1_amd64.deb ...
Unpacking shim-signed (1.51.4+15.8-0ubuntu1) over (1.51.3+15.7-0ubuntu1) ...
Setting up shim-signed (1.51.4+15.8-0ubuntu1) ...
Installing grub to /boot/efi.
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up libpython3-stdlib:amd64 (3.10.6-1~22.04.1) ...
Setting up python3 (3.10.6-1~22.04.1) ...
running python rtupdate hooks for python3.10...
running python post-rtupdate hooks for python3.10...
Processing triggers for man-db (2.10.2-1) ...

---

### Post by grahammechanical on 2024-08-26
I do not use Ubuntu Software to update the operating system and the applications. I have noticed that Ubuntu Software gives notice in advance of the updates actually being available. I guess that this is to allow users to close the (to be updated) applications so that they can be updated. I imagine that there must be some users who never switch off the machine or close applications. I am just a home user. What do I know about anything? :)

Regards

---

