---
title: "1 second delay once again"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2022-09-07
New install of Mate 22.04

1 second delay on reacting to any mouse or keyboard when using remote monitor with laptop.

This problem has been resurfacing for so so so long! Anyone know what is going on?

Later

Now tried on v similar laptop and works ok. 

Problem laptop is HP 850 G1 with i7 and AMD graphics

Working laptop is HP 850 G2 with i5 and intel graphics

The evidence points to 22.04 not playing nice with the AMD. 

Not exactly solved. Still hoping for a resolution.

---

### Post by TheFu on 2022-09-09
More information about the systems and what is running would help.

**inxi -Fxxz** output, please.
Also, looking at the system logs would likely point to issues. For every issue, always check the system logs first.

The symptoms described could be low RAM, lots of swapping, bad networking, slow DNS, or other hardware failures that haven't died, yet.

---

### Post by MAFoElffen on 2022-09-09
So to add to TheFu's request for information, the utility 'inxi" is not installed by default, if not installed on your system, either install it OR please run the Official [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script... a section of it deal's with memory and swap related information.

Also, in DEV/TEST is this translated code, which is more related to your problem, and information that TheFu may need to help you. This is information that is needed based on things happening to users lately with 22.04. It's being added to the script now, because of those current issues.
```

grep 'swap' /etc/fstab
awk '{print $0}' /proc/swaps
awk '{print $0}' /proc/sys/vm/swappiness
grep 'vm.swappiness' /etc/sysctl.conf

```
Note to TheFu: Don't worry. If they do not have 'pastebinit' installed, the script now goes to other pastebins (that you do not have to log into to see). I took your input to heart on that. If there is no output on the last command, it only means that it is at the default setting of 60, so not declared as different than that... And if you need updated details on what is going on with swap // related to 22.04.x, please PM me.

@triplemaya - You are in very good hands with help from 'TheFu.'

EDIT - 
Additional. If you temporarily remove 'quiet splash' from your Grub startup boot line, watch for a delay saying that it is waiting for networking to come up (fails several times), before it is actually logically ready for that... There is another work-around for that, which speeds up the boot process by about 40-50 seconds.

---

### Post by triplemaya on 2022-09-10
Thank you both. Completely failed to see the command in the info request. I have tremendous difficulty with the small laptop screen.

```

:~$ inxi -Fxxz
System:
  Kernel: 5.15.0-47-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: MATE 1.26.0 wm: marco dm: LightDM
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Hewlett-Packard product: HP EliteBook 850 G1
    v: A3009DD10303 serial: <superuser required> Chassis: type: 10
    serial: <superuser required>
  Mobo: Hewlett-Packard model: 198F v: KBC Version 15.59
    serial: <superuser required> BIOS: Hewlett-Packard v: L71 Ver. 01.46
    date: 07/20/2018
Battery:
  ID-1: BAT0 charge: 41.8 Wh (97.0%) condition: 43.1/43.1 Wh (100.0%)
    volts: 11.8 min: 11.4 model: Hewlett-Packard Primary serial: <filter>
    status: Discharging
CPU:
  Info: dual core model: Intel Core i7-4600U bits: 64 type: MT MCP
    arch: Haswell rev: 1 cache: L1: 128 KiB L2: 512 KiB L3: 4 MiB
  Speed (MHz): avg: 1046 high: 1113 min/max: 800/3300 cores: 1: 1113 2: 998
    3: 998 4: 1077 bogomips: 21548
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Haswell-ULT Integrated Graphics vendor: Hewlett-Packard
    driver: i915 v: kernel ports: active: eDP-1
    empty: DP-1, DP-2, HDMI-A-1, HDMI-A-2 bus-ID: 00:02.0 chip-ID: 8086:0a16
  Device-2: AMD Mars [Radeon HD 8730M] vendor: Hewlett-Packard
    driver: radeon v: kernel pcie: speed: 5 GT/s lanes: 4 ports: active: none
    empty: DP-3,DP-4 bus-ID: 03:00.0 chip-ID: 1002:6601
  Device-3: Chicony HP HD Webcam type: USB driver: uvcvideo bus-ID: 2-7:6
    chip-ID: 04f2:b3ed
  Display: x11 server: X.Org v: 1.21.1.3 compositor: marco v: 1.26.0
    driver: X: loaded: ati,modesetting,radeon unloaded: fbdev,vesa gpu: i915
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96
  Monitor-1: eDP-1 model: Chi Mei Innolux res: 1920x1080 dpi: 142
    diag: 395mm (15.5")
  OpenGL: renderer: Mesa Intel HD Graphics 4400 (HSW GT2)
    v: 4.6 Mesa 22.0.5 compat-v: 3.1 direct render: Yes
Audio:
  Device-1: Intel Haswell-ULT HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:03.0 chip-ID: 8086:0a0c
  Device-2: Intel 8 Series HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0 chip-ID: 8086:9c20
  Device-3: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000
  Series]
    vendor: Hewlett-Packard driver: snd_hda_intel v: kernel pcie: speed: 5 GT/s
    lanes: 4 bus-ID: 03:00.1 chip-ID: 1002:aab0
  Sound Server-1: ALSA v: k5.15.0-47-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I218-LM vendor: Hewlett-Packard driver: e1000e
    v: kernel port: 4080 bus-ID: 00:19.0 chip-ID: 8086:155a
  IF: enp0s25 state: down mac: <filter>
  Device-2: Intel Wireless 7260 driver: iwlwifi v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 bus-ID: 02:00.0 chip-ID: 8086:08b1
  IF: wlo1 state: up mac: <filter>
  Device-3: HP HP hs3110 HSPA+ Mobile Broadband Device type: USB
    driver: N/A bus-ID: 2-6:9 chip-ID: 03f0:521d
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 2-3.2:4 chip-ID: 8087:07dc
  Report: hciconfig ID: hci0 rfk-id: 21 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.0 sub-v: 500
Drives:
  Local Storage: total: 931.51 GiB used: 105.67 GiB (11.3%)
  ID-1: /dev/sda vendor: Samsung model: SSD 870 QVO 1TB size: 931.51 GiB
    speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 25.99 GiB used: 20.14 GiB (77.5%) fs: ext4 dev: /dev/sda1
  ID-2: /home size: 890.17 GiB used: 85.53 GiB (9.6%) fs: ext4
    dev: /dev/sda5
Swap:
  ID-1: swap-1 type: file size: 1.23 GiB used: 67.6 MiB (5.4%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 42.0 C mobo: 0.0 C gpu: radeon temp: 36.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 336 Uptime: 2d 15h 32m Memory: 7.66 GiB used: 4.61 GiB (60.2%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.2.0 alt: 11/9
  Packages: 3165 apt: 3152 snap: 13 Shell: Bash v: 5.1.16
  running-in: mate-terminal inxi: 3.3.13

```

---

### Post by triplemaya on 2022-09-10
And it now occurs to me that I should do this with the monitor plugged in. Genius at work!

```

~$ inxi -Fxxz
System:
  Kernel: 5.15.0-47-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: MATE 1.26.0 wm: marco dm: LightDM
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Hewlett-Packard product: HP EliteBook 850 G1
    v: A3009DD10303 serial: <superuser required> Chassis: type: 10
    serial: <superuser required>
  Mobo: Hewlett-Packard model: 198F v: KBC Version 15.59
    serial: <superuser required> BIOS: Hewlett-Packard v: L71 Ver. 01.46
    date: 07/20/2018
Battery:
  ID-1: BAT0 charge: 41.2 Wh (95.8%) condition: 43.0/43.0 Wh (100.0%)
    volts: 12.3 min: 11.4 model: Hewlett-Packard Primary serial: <filter>
    status: N/A
CPU:
  Info: dual core model: Intel Core i7-4600U bits: 64 type: MT MCP
    arch: Haswell rev: 1 cache: L1: 128 KiB L2: 512 KiB L3: 4 MiB
  Speed (MHz): avg: 1030 high: 1060 min/max: 800/3300 cores: 1: 1060 2: 947
    3: 1057 4: 1056 bogomips: 21548
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Haswell-ULT Integrated Graphics vendor: Hewlett-Packard
    driver: i915 v: kernel ports: active: none off: eDP-1
    empty: DP-1, DP-2, HDMI-A-1, HDMI-A-2 bus-ID: 00:02.0 chip-ID: 8086:0a16
  Device-2: AMD Mars [Radeon HD 8730M] vendor: Hewlett-Packard
    driver: radeon v: kernel pcie: speed: 5 GT/s lanes: 4 ports: active: DP-3
    empty: DP-4 bus-ID: 03:00.0 chip-ID: 1002:6601
  Device-3: Chicony HP HD Webcam type: USB driver: uvcvideo bus-ID: 2-7:6
    chip-ID: 04f2:b3ed
  Display: x11 server: X.Org v: 1.21.1.3 compositor: marco v: 1.26.0
    driver: X: loaded: ati,modesetting,radeon unloaded: fbdev,vesa gpu: radeon
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 2560x1600 s-dpi: 96
  Monitor-1: DisplayPort-1-2 mapped: DP-3 model: Dell U3014 res: 2560x1600
    dpi: 101 diag: 756mm (29.8")
  OpenGL: renderer: Mesa Intel HD Graphics 4400 (HSW GT2)
    v: 4.6 Mesa 22.0.5 compat-v: 3.1 direct render: Yes
Audio:
  Device-1: Intel Haswell-ULT HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:03.0 chip-ID: 8086:0a0c
  Device-2: Intel 8 Series HD Audio vendor: Hewlett-Packard
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0 chip-ID: 8086:9c20
  Device-3: AMD Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000
  Series]
    vendor: Hewlett-Packard driver: snd_hda_intel v: kernel pcie: speed: 5 GT/s
    lanes: 4 bus-ID: 03:00.1 chip-ID: 1002:aab0
  Sound Server-1: ALSA v: k5.15.0-47-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I218-LM vendor: Hewlett-Packard driver: e1000e
    v: kernel port: 4080 bus-ID: 00:19.0 chip-ID: 8086:155a
  IF: enp0s25 state: down mac: <filter>
  Device-2: Intel Wireless 7260 driver: iwlwifi v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 bus-ID: 02:00.0 chip-ID: 8086:08b1
  IF: wlo1 state: up mac: <filter>
  Device-3: HP HP hs3110 HSPA+ Mobile Broadband Device type: USB
    driver: N/A bus-ID: 2-6:9 chip-ID: 03f0:521d
Bluetooth:
  Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8
    bus-ID: 2-3.2:4 chip-ID: 8087:07dc
  Report: hciconfig ID: hci0 rfk-id: 21 state: up address: <filter>
    bt-v: 2.1 lmp-v: 4.0 sub-v: 500
Drives:
  Local Storage: total: 931.51 GiB used: 105.67 GiB (11.3%)
  ID-1: /dev/sda vendor: Samsung model: SSD 870 QVO 1TB size: 931.51 GiB
    speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 25.99 GiB used: 20.14 GiB (77.5%) fs: ext4 dev: /dev/sda1
  ID-2: /home size: 890.17 GiB used: 85.53 GiB (9.6%) fs: ext4
    dev: /dev/sda5
Swap:
  ID-1: swap-1 type: file size: 1.23 GiB used: 68.1 MiB (5.4%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 44.0 C mobo: 44.0 C gpu: radeon temp: 43.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 259 Uptime: 2d 15h 37m Memory: 7.66 GiB used: 4.54 GiB (59.3%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 11.2.0 alt: 11/9
  Packages: 3165 apt: 3152 snap: 13 Shell: Bash v: 5.1.16
  running-in: mate-terminal inxi: 3.3.13

```

---

### Post by triplemaya on 2022-09-10
```

pc@pc0:~$ grep 'swap' /etc/fstab
/swapfile                                 none            swap    sw              0       0
pc@pc0:~$ awk '{print $0}' /proc/swaps
Filename				Type		Size		Used	Priority
/swapfile                               file		1291944		69712	-2
pc@pc0:~$ awk '{print $0}' /proc/sys/vm/swappiness
60
pc@pc0:~$ grep 'vm.swappiness' /etc/sysctl.conf

```
No respoinse on last command

---

### Post by MAFoElffen on 2022-09-10
Please go back to your last 3 posts, please put your output within CODE TAGS like this: [noparse]```
 Output 
```[/noparse].

 The easiest way to do that is to Edit Post, Go Advanced... Select/highlight the ouptut, then select the [SIZE=4]**"#"**[/SIZE] Code Icon.

---

### Post by MAFoElffen on 2022-09-10
Should be the workaround for your problem:
```

sudo su -
modprobe drm_kms_helper
echo 0 > /sys/module/drm_kms_helper/parameters/poll
echo "drm_kms_helper" >> /etc/modprobe.d/local.conf
echo "drm_kms_helper" >> /etc/modules-load.d/local.conf
echo "options drm_kms_helper poll=0" >> /etc/modprobe.d/local.conf
update-initramfs -u 

```
Where 0 is turning the polling for that off (1 is on, which is where the lag is coming from...)

---

### Post by triplemaya on 2022-09-11
Thanks

```

root@pc0:/home/pc# modprobe drm_kms_helper
root@pc0:/home/pc# echo 0 > /sys/module/drm_kms_helper/parameters/poll
root@pc0:/home/pc# echo "drm_kms_helper" >> /etc/modprobe.d/local.conf
root@pc0:/home/pc# echo "drm_kms_helper" >> /etc/modules-load.d/local.conf
root@pc0:/home/pc# echo "options drm_kms_helper poll=N" >> /etc/modprobe.d/local.conf
root@pc0:/home/pc# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-5.15.0-47-generic
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
W: Possible missing firmware /lib/firmware/amdgpu/yellow_carp_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vangogh_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_sdma1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/cyan_skillfish_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/sienna_cichlid_mes.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/navi10_mes.bin for module amdgpu
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'
libkmod: ERROR ../libkmod/libkmod-config.c:712 kmod_config_parse: /etc/modprobe.d/local.conf line 1: ignoring bad line starting with 'drm_kms_helper'

```

---

### Post by triplemaya on 2022-09-11
> **MAFoElffen said:**
> Please go back to your last 3 posts, please put your output within CODE TAGS like this: [noparse]```
 Output 
```[/noparse].

 The easiest way to do that is to Edit Post, Go Advanced... Select/highlight the ouptut, then select the [SIZE=4]**"#"**[/SIZE] Code Icon.

All done. Apologies! Go Advanced tells me I am not authorised. ?

---

### Post by triplemaya on 2022-09-11
I had a look in the files and everything seems to have worked except poll contained the value N and not 0. Corrected. 
So still left with the problem of libkmod not liking the format of drm_kms_helper in local.conf.

---

### Post by triplemaya on 2022-09-13
Hello?

---

### Post by MAFoElffen on 2022-09-15
Sorry. That worked for me, though I have NVidia GPU, not AMD...

To backoff those changes:
```

# Become root
sudo su -

# Remove module drm_kms_helper
modprobe -r drm_kms_helper

# Remove file /sys/module/drm_kms_helper/parameters/poll
rm /sys/module/drm_kms_helper/parameters/poll

# Remove drm_kms_helper from file /etc/modprobe.d/local.conf
sed 's/^drm_kms_helper//g' /etc/modprobe.d/local.conf

# Remove drm_kms_helper from file /etc/modules-load.d/local.conf
sed 's/^drm_kms_helper//g' /etc/modules-load.d/local.conf

# Remove drm_kms_helper from file /etc/modeprobe.d/local.conf
sed 's/^drm_kms_helper//g' /etc/modeprobe.d/local.conf

update-initramfs -u

```
Not absolutely sure then. And I don't have an AMD GPU to test on...

---

### Post by triplemaya on 2022-09-15
Thanks. The problem though seems to be that the format is wrong for the files the update reads. I cannot see why the format would be different for NVidia to AMD.

---

