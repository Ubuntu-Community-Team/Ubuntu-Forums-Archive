---
title: "Long startup time after install of Ubuntu MATE 18.04"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by joesplace2 on 2018-07-09
I did a fresh install of Ubuntu MATE and from the press of power button to  desktop it's 13 minutes. I have reinstalled three time and no  difference at all. Can someone please tell me how to troubleshoot this  problem? Here's some info about my system:

inxi -Fxz```
System:    Host: shortstop-Inspiron-1720 Kernel: 4.15.0-24-generic x86_64
           bits: 64 gcc: 7.3.0
           Desktop: MATE 1.20.1 (Gtk 3.22.30-1ubuntu1)
           Distro: Ubuntu 18.04 LTS
Machine:   Device: portable System: Dell product: Inspiron 1720 serial: N/A
           Mobo: Dell model: 0UK439 serial: N/A
           BIOS: Dell v: A09 date: 07/11/2008
Battery    BAT0: charge: 68.6 Wh 92.2% condition: 74.4/73.3 Wh (102%)
           model: Sony DELL 00 status: Charging
CPU:       Dual core Intel Core2 Duo T7250 (-MCP-) 
           arch: Conroe rev.13 cache: 2048 KB
           flags: (lm nx sse sse2 sse3 ssse3 vmx) bmips: 7980
           clock speeds: max: 2001 MHz 1: 1273 MHz 2: 1308 MHz
Graphics:  Card: Intel Mobile GM965/GL960 Integrated Graphics Controller (primary)
           bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1200@59.98hz
           OpenGL: renderer: Mesa DRI Intel 965GM
           version: 2.1 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel 82801H (ICH8 Family) HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-24-generic
Network:   Card-1: Broadcom Limited BCM4401-B0 100Base-TX
           driver: b44 v: 2.0 bus-ID: 03:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Broadcom Limited BCM4321 802.11a/b/g/n
           driver: wl bus-ID: 0c:00.0
           IF: wlp12s0 state: up mac: <filter>
Drives:    HDD Total Size: 128.0GB (13.7% used)
           ID-1: /dev/sda model: SAMSUNG_SSD_SM84 size: 128.0GB
Partition: ID-1: / size: 117G used: 17G (15%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 44.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 178 Uptime: 1:26 Memory: 1552.2/3935.9MB
           Init: systemd runlevel: 5 Gcc sys: 7.3.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 [CODE]

systemd-analyze blame
[CODE]    1min 25.554s nmbd.service
         13.267s dev-sda1.device
         10.636s dev-loop0.device
         10.586s dev-loop3.device
         10.508s dev-loop1.device
         10.485s dev-loop4.device
         10.463s dev-loop2.device
         10.450s dev-loop5.device
          6.161s snapd.service
          3.104s udisks2.service
          2.368s systemd-rfkill.service
          2.296s networkd-dispatcher.service
          2.291s snapd.seeded.service
          1.942s systemd-udev-trigger.service
          1.773s ModemManager.service
          1.666s keyboard-setup.service
          1.665s loadcpufreq.service
          1.580s systemd-journald.service
          1.567s NetworkManager.service
          1.440s lightdm.service
          1.393s plymouth-quit-wait.service
          1.367s swapfile.swap
          1.207s apparmor.service
          1.181s avahi-daemon.service
          1.079s accounts-daemon.service
           986ms networking.service
           925ms lm-sensors.service
           921ms NetworkManager-wait-online.service
           917ms upower.service
           866ms wpa_supplicant.service
           695ms hddtemp.service
           680ms rsyslog.service
           659ms thermald.service
           638ms gpu-manager.service
           634ms grub-common.service
           616ms pppd-dns.service
           616ms apport.service
           536ms cpufrequtils.service
           465ms speech-dispatcher.service
           442ms systemd-timesyncd.service
           400ms systemd-journal-flush.service
           375ms systemd-resolved.service
           365ms systemd-backlight@backlight:acpi_video0.service
           344ms systemd-udevd.service
           334ms smbd.service
           316ms snap-core-4486.mount
           302ms plymouth-read-write.service
           282ms user@1000.service
           269ms polkit.service
           267ms systemd-user-sessions.service
           262ms console-setup.service
           260ms systemd-logind.service
           255ms ufw.service
           253ms kmod-static-nodes.service
           241ms dev-hugepages.mount
           232ms snap-software\x2dboutique-31.mount
           227ms systemd-modules-load.service
           213ms snap-pulsemixer-23.mount
           201ms snap-ubuntu\x2dmate\x2dwelcome-169.mount
           191ms systemd-random-seed.service
           189ms snap-pulsemixer-8.mount
           181ms sys-fs-fuse-connections.mount
           178ms kerneloops.service
           171ms dev-mqueue.mount
           161ms snap-core-4917.mount
           160ms sys-kernel-debug.mount
           158ms sys-kernel-config.mount
           151ms openvpn.service
           135ms systemd-sysctl.service
           120ms systemd-tmpfiles-setup-dev.service
           115ms systemd-tmpfiles-setup.service
           114ms systemd-remount-fs.service
           106ms motd-news.service
            91ms systemd-update-utmp.service
            76ms systemd-tmpfiles-clean.service
            75ms systemd-backlight@backlight:intel_backlight.service
            60ms systemd-update-utmp-runlevel.service
            58ms bluetooth.service
            57ms packagekit.service
            35ms setvtrgb.service
            34ms plymouth-start.service
            34ms snapd.socket
            33ms colord.service
            32ms rtkit-daemon.service
            31ms ureadahead-stop.service
```

---

### Post by apeitheo2 on 2018-07-09
There's an issue with kernel 4.15.0-24 that results in low entropy on boot. This workaround is installing & enabling haveged, which generates extra entropy on boot. This may or may not work depending on if this is your problem, but it's simple enough to remove if it doesn't work.
```
sudo apt install haveged
sudo systemctl enable haveged
```
Good luck.

---

