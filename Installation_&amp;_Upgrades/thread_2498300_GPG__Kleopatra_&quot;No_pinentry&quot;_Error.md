---
title: "GPG / Kleopatra &quot;No pinentry&quot; Error"
date: 2024-06-07
forum: Installation &amp; Upgrades
---

### Post by nhatphongtran on 2024-06-07
In Kleopatra whenever I click on decrypt/encrypt anything (i.e. notepad), there's an error message saying "Encryption failed: No pinentry".

I tried 

pkill gpg-agent
gpg-agent --pinentry-program=/usr/bin/pinentry --daemon

But that just seems to stall. Any ideas?

---

### Post by #&amp;thj^% on 2024-06-07
Your lacking some very important details for anyone to help..
1st) What Hardware?
2nd) What system are you using?
Inxi might be enough to get started:
```
inxi -Fzyxxx
```

Kleopatra has always been problematic on my end.

A number of encrypted files we receive cannot be decrypted by the Kleopatra GUI but they can be decrypted on the command-line with GPG
```
gpg -v --decrypt "your file"
```

I got rid of it, I need things to just work.

I did try this a few times and it worked back then, but it's not a solution.
```
gpg -d --ignore-mdc-error -o <outputfile> <file_to_decrypt>
```

If you really need to use Kleopatra, some more useful info can found here: [https://usercomp.com/news/1059427/kleopatra-encryption-decryption-log-guide](https://usercomp.com/news/1059427/kleopatra-encryption-decryption-log-guide)

Just a guess but this might be useful:
```
gpg --full-gen-key --pinentry-mode loopback 
```

---

### Post by currentshaft on 2024-06-07
Is /usr/bin/pinentry a path to a valid program? What happens when you run it in terminal?

---

### Post by nhatphongtran on 2024-06-10
> **currentshaft said:**
> Is /usr/bin/pinentry a path to a valid program? What happens when you run it in terminal?

Thanks! Yes it is a valid path and program.

---

### Post by nhatphongtran on 2024-06-10
> **1fallen said:**
> Your lacking some very important details for anyone to help..
1st) What Hardware?
2nd) What system are you using?
Inxi might be enough to get started:
```
inxi -Fzyxxx
```

Kleopatra has always been problematic on my end.

A number of encrypted files we receive cannot be decrypted by the Kleopatra GUI but they can be decrypted on the command-line with GPG
```
gpg -v --decrypt "your file"
```

I got rid of it, I need things to just work.

I did try this a few times and it worked back then, but it's not a solution.
```
gpg -d --ignore-mdc-error -o <outputfile> <file_to_decrypt>
```

If you really need to use Kleopatra, some more useful info can found here: [https://usercomp.com/news/1059427/kleopatra-encryption-decryption-log-guide](https://usercomp.com/news/1059427/kleopatra-encryption-decryption-log-guide)

Just a guess but this might be useful:
```
gpg --full-gen-key --pinentry-mode loopback 
```

Thank you for your reply! 

Yes through commandline gpg encryption/decryption works. It's just Kleopatra. I installed all pinentry, pinentry-qt, etc. that I could find. But still the same error from Kleopatra.

Here's the output from inxi:

```
System:
  Kernel: 6.8.0-35-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
    clocksource: tsc
  Desktop: GNOME v: 46.0 tk: GTK v: 3.24.41 wm: gnome-shell
    tools: gsd-screensaver-proxy dm: GDM3 v: 46.0 Distro: Ubuntu 24.04 LTS
    (Noble Numbat)
Machine:
  Type: Convertible System: Dell product: XPS 13 7390 2-in-1 v: N/A
    serial: <superuser required> Chassis: type: 31 serial: <superuser required>
  Mobo: Dell model: 06CDVY v: A00 serial: <superuser required> part-nu: 08B0
    uuid: <superuser required> UEFI: Dell v: 1.9.1 date: 07/27/2021
Battery:
  ID-1: BAT0 charge: 34.9 Wh (100.0%) condition: 34.9/50.0 Wh (69.9%)
    volts: 8.4 min: 7.6 model: BYD DELL XX3T704 type: Li-poly serial: <filter>
    status: full
CPU:
  Info: quad core model: Intel Core i7-1065G7 bits: 64 type: MT MCP
    smt: enabled arch: Ice Lake rev: 5 cache: L1: 320 KiB L2: 2 MiB L3: 8 MiB
  Speed (MHz): avg: 2663 high: 3822 min/max: 400/3900 cores: 1: 400 2: 3505
    3: 1353 4: 3667 5: 3655 6: 3500 7: 3822 8: 1406 bogomips: 23961
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Iris Plus Graphics G7 vendor: Dell driver: i915 v: kernel
    arch: Gen-11 ports: active: eDP-1 empty: DP-1, DP-2, DP-3, DP-4
    bus-ID: 00:02.0 chip-ID: 8086:8a52 class-ID: 0300
  Device-2: NVIDIA TU102 [GeForce RTX 2080 Ti Rev. A] vendor: PNY
    driver: nvidia v: 555.42.02 arch: Turing pcie: speed: 2.5 GT/s lanes: 4
    ports: active: none off: DP-5,HDMI-A-1 empty: DP-6,DP-7,Unknown-1
    bus-ID: 2e:00.0 chip-ID: 10de:1e07 class-ID: 0300
  Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6
    compositor: gnome-shell driver: X: loaded: modesetting,nvidia dri: iris
    gpu: i915,nvidia,nvidia-nvswitch display-ID: :1 screens: 1
  Screen-1: 0 s-res: 4480x1440 s-dpi: 96 s-size: 1185x381mm (46.65x15.00")
    s-diag: 1245mm (49.01")
  Monitor-1: not-matched mapped: DP-0 pos: primary,right res: 2560x1440
    hz: 60 dpi: 109 size: 597x336mm (23.5x13.23") diag: 685mm (26.97") modes: N/A
  Monitor-2: not-matched mapped: HDMI-0 size-res: N/A modes: N/A
  Monitor-3: eDP-1 mapped: eDP-1-1 pos: left model: Sharp 0x14a8
    res: 1920x1200 hz: 60 dpi: 169 size: 288x180mm (11.34x7.09")
    diag: 340mm (13.4") modes: 3840x2400
  API: EGL v: 1.5 hw: drv: intel iris drv: nvidia platforms: device: 0
    drv: nvidia device: 2 drv: iris device: 3 drv: swrast gbm: drv: nvidia
    surfaceless: drv: nvidia x11: drv: nvidia inactive: wayland,device-1
  API: OpenGL v: 4.6.0 compat-v: 4.5 vendor: nvidia mesa v: 555.42.02
    glx-v: 1.4 direct-render: yes renderer: NVIDIA GeForce RTX 2080 Ti/PCIe/SSE2
Audio:
  Device-1: Intel Image Signal Processor vendor: Dell driver: N/A
    bus-ID: 00:05.0 chip-ID: 8086:8a19 class-ID: 0480
  Device-2: Intel Ice Lake-LP Smart Sound Audio vendor: Dell
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:34c8
    class-ID: 0403
  Device-3: NVIDIA TU102 High Definition Audio vendor: PNY
    driver: snd_hda_intel v: kernel pcie: speed: 8 GT/s lanes: 4 bus-ID: 2e:00.1
    chip-ID: 10de:10f7 class-ID: 0403
  Device-4: Shure MV7 driver: hid-generic,snd-usb-audio,usbhid type: USB
    rev: 2.0 speed: 12 Mb/s lanes: 1 bus-ID: 9-1:2 chip-ID: 14ed:1012
    class-ID: 0300
  API: ALSA v: k6.8.0-35-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
Network:
  Device-1: Intel Ice Lake-LP PCH CNVi WiFi vendor: Rivet Networks
    driver: iwlwifi v: kernel bus-ID: 00:14.3 chip-ID: 8086:34f0 class-ID: 0280
  IF: wlp0s20f3 state: up mac: <filter>
  Device-2: ASIX AX88179 Gigabit Ethernet driver: ax88179_178a type: USB
    rev: 3.0 speed: 5 Gb/s lanes: 1 bus-ID: 12-1:2 chip-ID: 0b95:1790
    class-ID: ff00 serial: <filter>
  IF: eth0 state: down mac: <filter>
Bluetooth:
  Device-1: Intel AX201 Bluetooth driver: btusb v: 0.8 type: USB rev: 2.0
    speed: 12 Mb/s lanes: 1 bus-ID: 3-10:6 chip-ID: 8087:0026 class-ID: e001
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 5.2
    lmp-v: 11 sub-v: 20f9 hci-v: 11 rev: 20f9 class-ID: 6c0000
Drives:
  Local Storage: total: 8.44 TiB used: 2.34 TiB (27.7%)
  ID-1: /dev/mmcblk0 vendor: Swissbit model: SF256 size: 238.3 GiB
    type: Removable tech: SSD serial: <filter> scheme: MBR
  ID-2: /dev/nvme0n1 vendor: Toshiba model: KBG40ZPZ1T02 NVMe KIOXIA 1024GB
    size: 953.87 GiB speed: 31.6 Gb/s lanes: 4 tech: SSD serial: <filter>
    fw-rev: 10400104 temp: 53.9 C scheme: GPT
  ID-3: /dev/sda vendor: Seagate model: Backup+ Desk size: 7.28 TiB type: USB
    rev: 3.0 spd: 5 Gb/s lanes: 1 tech: N/A serial: <filter> fw-rev: 0511
    scheme: GPT
Partition:
  ID-1: / size: 936.79 GiB used: 273.69 GiB (29.2%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 1.05 GiB used: 6.2 MiB (0.6%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 8 GiB used: 0 KiB (0.0%) priority: -2
    file: /swap.img
Sensors:
  System Temperatures: cpu: 74.0 C mobo: N/A gpu: nvidia temp: 42 C
  Fan Speeds (rpm): N/A gpu: nvidia fan: 29%
Info:
  Memory: total: 32 GiB note: est. available: 31.12 GiB used: 10.27 GiB (33.0%)
  Processes: 381 Power: uptime: 12h 31m states: freeze,mem suspend: s2idle
    wakeups: 0 hibernate: disabled Init: systemd v: 255 target: graphical (5)
    default: graphical
  Packages: 2025 pm: dpkg pkgs: 1984 pm: flatpak pkgs: 13 pm: snap pkgs: 28
    Compilers: gcc: 13.2.0 Shell: Bash v: 5.2.21 running-in: gnome-terminal
    inxi: 3.3.34
```

---

### Post by #&amp;thj^% on 2024-06-10
I never did get  Kleopatra to work correctly, so I just resorted to the CLI method and removed  Kleopatra.

I guess I'm just lost on why there is a need for pinentry.
```
Depends On      : akonadi-mime  gcc-libs  glibc  gpgme  kcodecs  kcolorscheme  kconfig
                  kconfigwidgets  kcoreaddons  kcrash  kdbusaddons  ki18n  kiconthemes
                  kidentitymanagement  kio  kitemmodels  kmailtransport  kmime  kstatusnotifieritem
                  ktextwidgets  kwidgetsaddons  kwindowsystem  kxmlgui  libassuan  libgpg-error
                  libkleo  mimetreeparser  qgpgme-qt6  qt6-base

```

At first glance on your first post I thought this may be a Mac Book/Laptop  But I see it is not from inxi.
ie:
```
Collection of simple PIN or passphrase entry dialogs which utilize the Assuan protocol

```
It is a valid path:
```
ls /usr/bin/pinentry 
/usr/bin/pinentry

```

---

### Post by nhatphongtran on 2024-06-10
> **1fallen said:**
> I never did get  Kleopatra to work correctly, so I just resorted to the CLI method and removed  Kleopatra.

I guess I'm just lost on why there is a need for pinentry.


I believe the pinentry is supposed to ask you for your passphrase to sign or decrypt.

---

### Post by #&amp;thj^% on 2024-06-11
Well it seems to always show up after installing Kleopatra, so I'll take your word on that.

Just thinking aloud, To force GPG to use the console-mode pinentry to prompt for passwords, you can try the following solutions:

Using export GPG_TTY=$(tty) and unset DISPLAY: This method works by setting the GPG_TTY environment variable to the current terminal and unsetting the DISPLAY variable. This will tell GPG to use the console-mode pinentry instead of the GTK pinentry.
Example:
```

export GPG_TTY=$(tty)
unset DISPLAY
gpg --decrypt file.gpg
```

---

### Post by nhatphongtran on 2024-06-12
> **1fallen said:**
> Well it seems to always show up after installing Kleopatra, so I'll take your word on that.

Just thinking aloud, To force GPG to use the console-mode pinentry to prompt for passwords, you can try the following solutions:

Using export GPG_TTY=$(tty) and unset DISPLAY: This method works by setting the GPG_TTY environment variable to the current terminal and unsetting the DISPLAY variable. This will tell GPG to use the console-mode pinentry instead of the GTK pinentry.
Example:
```

export GPG_TTY=$(tty)
unset DISPLAY
gpg --decrypt file.gpg
```

Thanks for the workaround! In GPG I don't have issues with the pinentry. I don't know why Kleopatra has such a problem with it.

---

### Post by currentshaft on 2024-06-17
> **nhatphongtran said:**
> Thanks! Yes it is a valid path and program.

Now answer the second part: what happens when you run it.

---

