---
title: "hp victus 15 not waking up from standby with nvidia driver enabled"
date: 2024-02-11
forum: Installation &amp; Upgrades
---

### Post by salva-tore on 2024-02-11
hello, i'm writing here on this forum because everything i found online didn't work. I have an hp victus with ubuntu 22.04 installed. When nvidia driver are enabled (when prime-select is on on-demand or nvidia) the laptop is not waking up from standby. This is the output from  inxi Fzx
```

System:
  Kernel: 6.5.0-17-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: Victus by HP Gaming Laptop 15-fa0xxx
    v: N/A serial: <superuser required>
  Mobo: HP model: 8A4F v: 37.54 serial: <superuser required> UEFI: AMI
    v: F.24 date: 10/26/2023
Battery:
  ID-1: BAT0 charge: 61.0 Wh (100.0%) condition: 61.0/70.1 Wh (87.0%)
    volts: 17.2 min: 15.4 model: HP Primary status: Full
CPU:
  Info: 14-core (6-mt/8-st) model: 12th Gen Intel Core i7-12700H bits: 64
    type: MST AMCP arch: Alder Lake rev: 3 cache: L1: 1.2 MiB L2: 11.5 MiB
    L3: 24 MiB
  Speed (MHz): avg: 458 high: 928 min/max: 400/4600:4700:3500 cores: 1: 400
    2: 400 3: 400 4: 400 5: 477 6: 400 7: 400 8: 400 9: 645 10: 400 11: 533
    12: 400 13: 928 14: 594 15: 400 16: 400 17: 400 18: 400 19: 400 20: 400
    bogomips: 107520
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: Hewlett-Packard
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GA107M [GeForce RTX 3050 Mobile] vendor: Hewlett-Packard
    driver: nvidia v: 535.154.05 bus-ID: 01:00.0
  Device-3: Luxvisions Innotech HP Wide Vision HD Camera type: USB
    driver: uvcvideo bus-ID: 3-6:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    vendor: Hewlett-Packard driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: Hewlett-Packard driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Sound Server-1: ALSA v: k6.5.0-17-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 04:00.0
  IF: wlp4s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus-ID: 05:00.0
  IF: eno1 state: down mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 3-7:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 476.94 GiB used: 36.11 GiB (7.6%)
  ID-1: /dev/nvme0n1 vendor: Western Digital
    model: WD PC SN810 SDCPNRY-512G-1006 size: 476.94 GiB temp: 32.9 C
Partition:
  ID-1: / size: 97.87 GiB used: 36.01 GiB (36.8%) fs: ext4
    dev: /dev/nvme0n1p5
  ID-2: /boot/efi size: 256 MiB used: 102.7 MiB (40.1%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 33.0 C mobo: N/A
  Fan Speeds (RPM): cpu: 2198 fan-2: 2017
Info:
  Processes: 413 Uptime: 18m Memory: 15.28 GiB used: 2.86 GiB (18.7%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2008 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

and this is what i visualize on screen when resume fails (i used journalctl | grep i915)
```

kernel: i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to write source OUI
i915 0000:00:02.0: [drm] *ERROR* failed to enable link training
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to write source OUI
i915 0000:00:02.0: [drm] *ERROR* failed to enable link training
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to write source OUI
i915 0000:00:02.0: [drm] *ERROR* failed to enable link training
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92

```
i hope anyone could help me. Thanks

EDIT: i open this thread because i saw a similar issue solved, but this guy has an amd cpu and i have intel

---

### Post by thatsdos on 2024-11-17
> **salva-tore said:**
> hello, i'm writing here on this forum because everything i found online didn't work. I have an hp victus with ubuntu 22.04 installed. When nvidia driver are enabled (when prime-select is on on-demand or nvidia) the laptop is not waking up from standby. This is the output from  inxi Fzx
```

System:
  Kernel: 6.5.0-17-generic x86_64 bits: 64 compiler: N/A Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: Victus by HP Gaming Laptop 15-fa0xxx
    v: N/A serial: <superuser required>
  Mobo: HP model: 8A4F v: 37.54 serial: <superuser required> UEFI: AMI
    v: F.24 date: 10/26/2023
Battery:
  ID-1: BAT0 charge: 61.0 Wh (100.0%) condition: 61.0/70.1 Wh (87.0%)
    volts: 17.2 min: 15.4 model: HP Primary status: Full
CPU:
  Info: 14-core (6-mt/8-st) model: 12th Gen Intel Core i7-12700H bits: 64
    type: MST AMCP arch: Alder Lake rev: 3 cache: L1: 1.2 MiB L2: 11.5 MiB
    L3: 24 MiB
  Speed (MHz): avg: 458 high: 928 min/max: 400/4600:4700:3500 cores: 1: 400
    2: 400 3: 400 4: 400 5: 477 6: 400 7: 400 8: 400 9: 645 10: 400 11: 533
    12: 400 13: 928 14: 594 15: 400 16: 400 17: 400 18: 400 19: 400 20: 400
    bogomips: 107520
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: Hewlett-Packard
    driver: i915 v: kernel bus-ID: 00:02.0
  Device-2: NVIDIA GA107M [GeForce RTX 3050 Mobile] vendor: Hewlett-Packard
    driver: nvidia v: 535.154.05 bus-ID: 01:00.0
  Device-3: Luxvisions Innotech HP Wide Vision HD Camera type: USB
    driver: uvcvideo bus-ID: 3-6:3
  Display: x11 server: X.Org v: 1.21.1.4 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,nouveau,vesa gpu: i915
    resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1 direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio
    vendor: Hewlett-Packard driver: sof-audio-pci-intel-tgl bus-ID: 00:1f.3
  Device-2: NVIDIA vendor: Hewlett-Packard driver: snd_hda_intel v: kernel
    bus-ID: 01:00.1
  Sound Server-1: ALSA v: k6.5.0-17-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: MEDIATEK MT7921 802.11ax PCI Express Wireless Network Adapter
    vendor: AzureWave driver: mt7921e v: kernel bus-ID: 04:00.0
  IF: wlp4s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus-ID: 05:00.0
  IF: eno1 state: down mac: <filter>
Bluetooth:
  Device-1: IMC Networks Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 3-7:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 476.94 GiB used: 36.11 GiB (7.6%)
  ID-1: /dev/nvme0n1 vendor: Western Digital
    model: WD PC SN810 SDCPNRY-512G-1006 size: 476.94 GiB temp: 32.9 C
Partition:
  ID-1: / size: 97.87 GiB used: 36.01 GiB (36.8%) fs: ext4
    dev: /dev/nvme0n1p5
  ID-2: /boot/efi size: 256 MiB used: 102.7 MiB (40.1%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 33.0 C mobo: N/A
  Fan Speeds (RPM): cpu: 2198 fan-2: 2017
Info:
  Processes: 413 Uptime: 18m Memory: 15.28 GiB used: 2.86 GiB (18.7%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2008 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

and this is what i visualize on screen when resume fails (i used journalctl | grep i915)
```

kernel: i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to write source OUI
i915 0000:00:02.0: [drm] *ERROR* failed to enable link training
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to write source OUI
i915 0000:00:02.0: [drm] *ERROR* failed to enable link training
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92
i915 0000:00:02.0: [drm] *ERROR* Failed to write source OUI
i915 0000:00:02.0: [drm] *ERROR* failed to enable link training
i915 0000:00:02.0: [drm] *ERROR* Failed to read DPCD register 0x92

```
i hope anyone could help me. Thanks

EDIT: i open this thread because i saw a similar issue solved, but this guy has an amd cpu and i have intel

I am having same problem although my system a bit old(i5 12450h + RTX 2050). Please let me know if you found any fix.

---

### Post by wildmanne39 on 2024-11-17
Hello and welcome to the forum this is a very old thread and has no replies to the OP please start your own thread so you can get the help you need.

Thread closed.

---

