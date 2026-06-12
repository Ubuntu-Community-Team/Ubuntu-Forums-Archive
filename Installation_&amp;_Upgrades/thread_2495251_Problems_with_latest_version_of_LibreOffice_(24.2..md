---
title: "Problems with latest version of LibreOffice (24.2.1.1)"
date: 2024-02-13
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2024-02-13
Version: 24.2.1.1 (X86_64) / LibreOffice Community
Build ID: 15ef5d8c4e19091ee2fab7577bf0884a1331c6f8
CPU threads: 8; OS: Linux 6.5; UI render: default; VCL: gtk3
Locale: en-US (en_US.UTF-8); UI: en-US
Calc: threaded
OS: Ubuntu Unity 23.1o

Trying to get LanguageTool to work:
"Could not create Java implementation loader at /build/libreoffice/parts/libreoffice/build/stoc/source/javaloader/javaloader/javaloader.cxx:533"

I am not an IT professional.  LanguageTool extension gave above error after Ubuntu forced update to LibreOffice version listed above.  I write professionally.  LanguageTool is mission-critical.  Snap copy and paste version is not satisfactory.

How do I get LanguageTool working?

Thank you, John

---

### Post by ajgreeny on 2024-02-13
Are still using Ubuntu 22.10 as shown in your details we all see?
If so you need to upgrade your system to a fully supported version as 22.10 lost all support in July last year.

If you are already using another version give us all the details by showing the output of command **inxi -Fzx** using code tags for the terminal output.

Where did your version of LO come from as it can not be from the repos of 22.10?

**EDIT**
Apologies! It looks as if you're using 23.10; I missed your comment.
The **inxi** output may still be valuable so please show us that

---

### Post by cigtoxdoc on 2024-02-13
Thank you.  The output you requested is shown below.  BTW, I have another PC that has the DEB version of 24.2 LO (downloaded from LO website) and LanguageTool works perfectly.  John

   ```
 resolution: 1920x1080~60Hz
  API: OpenGL v: 4.6 Mesa 23.2.1-1ubuntu3.1 renderer: Mesa Intel HD
    Graphics 630 (KBL GT2) direct-render: Yes
Audio:
  Device-1: Intel CM238 HD Audio vendor: Dell driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3
  Device-2: NVIDIA GP104 High Definition Audio driver: snd_hda_intel
    v: kernel bus-ID: 01:00.1
  API: ALSA v: k6.5.0-17-generic status: kernel-api
  Server-1: PulseAudio v: 16.1 status: active
Network:
  Device-1: Intel Ethernet I219-LM vendor: Dell driver: e1000e v: kernel
    port: N/A bus-ID: 00:1f.6
  IF: enp0s31f6 state: up speed: 1000 Mbps duplex: full mac: <filter>
  Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel
    bus-ID: 02:00.0
  IF: wlp2s0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface driver: btusb v: 0.8 type: USB
    bus-ID: 1-6:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 4.2
    lmp-v: 8
Drives:
  Local Storage: total: 476.94 GiB used: 147.21 GiB (30.9%)
  ID-1: /dev/nvme0n1 vendor: Toshiba model: KXG50ZNV512G NVMe 512GB
    size: 476.94 GiB temp: 39.9 C
Partition:
  ID-1: / size: 68.09 GiB used: 45.4 GiB (66.7%) fs: ext4 dev: /dev/nvme0n1p11
  ID-2: /boot/efi size: 95 MiB used: 68.8 MiB (72.4%) fs: vfat
    dev: /dev/nvme0n1p2
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 0.0 C pch: 45.5 C mobo: 42.0 C
  Fan Speeds (rpm): cpu: 0 fan-2: 0
Info:
  Processes: 315 Uptime: 12h 11m Memory: total: 32 GiB available: 31.19 GiB
  used: 6.81 GiB (21.8%) Init: systemd target: graphical (5) Compilers:
  gcc: 13.2.0 Packages: 2351 Shell: Bash v: 5.2.15 inxi: 3.3.29
john@john-Precision-7720:~$
```

---

