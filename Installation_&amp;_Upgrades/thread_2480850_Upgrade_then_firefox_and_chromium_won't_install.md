---
title: "Upgrade then firefox and chromium won't install"
date: 2022-11-12
forum: Installation &amp; Upgrades
---

### Post by Visseroth on 2022-11-12
I'll post my system specs but I just upgraded from version 20 to 22 and during the upgrade I received an error during the upgrade regarding chromium and firefox so I uninstalled them then resumed the upgrade.
The upgrade completed successfully but I can't get chromium or firefox to install.

When I attempt to install here is what I get...

```
sudo apt install firefox
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/72.3 kB of archives.
After this operation, 261 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 236479 files and directories currently installed.)
Preparing to unpack .../firefox_1%3a1snap1-0ubuntu2_arm64.deb ...
=> Installing the firefox snap
==> Checking connectivity with the snap store
==> Installing the firefox snap
error: cannot perform the following tasks:
- Run hook connect-plug-host-hunspell of snap "firefox" (run hook "connect-plug-host-hunspell": cannot perform operati
on: mount --bind /snap/core20/current/etc/nsswitch.conf /tmp/snap.rootfs_gosfqH/etc/nsswitch.conf: Permission denied)
dpkg: error processing archive /var/cache/apt/archives/firefox_1%3a1snap1-0ubuntu2_arm64.deb (--unpack):
 new firefox package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1%3a1snap1-0ubuntu2_arm64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'v tried a few things, including attempting to delete the files in /tmp/ but I get the following...
```

sudo rm -rf *
rm: cannot remove 'snap.rootfs_7g1jTk': Device or resource busy
rm: cannot remove 'snap.rootfs_E9SFXU': Device or resource busy
rm: cannot remove 'snap.rootfs_O3Ik35': Device or resource busy
rm: cannot remove 'snap.rootfs_iYcxw6': Device or resource busy
rm: cannot remove 'snap.rootfs_uNzLgK': Device or resource busy
```

I've tried many things but nothing seems to work.

Here are my system specs....

```
inxi -Fxz
System:
  Kernel: 4.9.312-125 arch: aarch64 bits: 64 compiler: gcc v: 7.5.0 Console: pty pts/1
    Distro: Ubuntu 22.10 (Kinetic Kudu)
Machine:
  Type: ARM System: Hardkernel ODROID-N2Plus rev: 0400
CPU:
  Info: 2x 2-core model: N/A variant-1: cortex-a73 variant-2: cortex-a53 bits: 64 type: MCP AMP
    arch: ARMv8 rev: 4
  Speed (MHz): avg: 2272 high: 2400 min/max: 500/2016:2400 cores: 1: 2016 2: 2016 3: 2400
    4: 2400 5: 2400 6: 2400 bogomips: N/A
  Features: Use -f option to see features
Graphics:
  Device-1: amhdmitx driver: amhdmitx v: N/A bus-ID: N/A
  Device-2: meson-g12b driver: meson_fb v: N/A bus-ID: N/A
  Device-3: vpu-g12b driver: vpu v: N/A bus-ID: N/A
  Display: server: X.org v: 1.21.1.4 with: Xwayland v: 22.1.3 driver: X: loaded: fbdev
    unloaded: modesetting gpu: amhdmitx,meson_fb,vpu tty: 118x30
  Message: GL data unavailable in console. Try -G --display
Audio:
  Device-1: audio- driver: aml_audio_controller bus-ID: N/A
  Device-2: g12a-audio-clocks driver: audio_clocks bus-ID: N/A
  Device-3: g12a-audio-ddr-manager driver: audio_ddr_manager bus-ID: N/A
  Device-4: g12a-snd-spdif-a driver: snd_spdif bus-ID: N/A
  Device-5: g12a-snd-spdif-b driver: snd_spdif bus-ID: N/A
  Device-6: g12a-snd-tdmc driver: snd_tdm bus-ID: N/A
  Device-7: amhdmitx driver: amhdmitx bus-ID: N/A
  Device-8: snd-iomap driver: auge_snd_iomap bus-ID: N/A
  Device-9: audio_data driver: audio_data_debug bus-ID: N/A
  Device-10: audiolocker driver: audiolocker bus-ID: N/A
  Device-11: vdac-g12b driver: aml_vdac bus-ID: N/A
  Sound Server-1: ALSA v: k4.9.312-125 running: yes
  Sound Server-2: PulseAudio v: 16.1 running: no
  Sound Server-3: PipeWire v: 0.3.58 running: yes
Network:
  Device-1: g12a-eth-dwmac driver: meson6_dwmac v: N/A port: N/A bus-ID: N/A
  IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 59.48 GiB used: 8.47 GiB (14.2%)
  ID-1: /dev/mmcblk1 model: SR64G size: 59.48 GiB
Partition:
  ID-1: / size: 52.34 GiB used: 8.44 GiB (16.1%) fs: ext4 dev: /dev/mmcblk1p2
Swap:
  Alert: No swap data was found.
Sensors:
  System Temperatures: cpu: 36.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 487 Uptime: 11m Memory: 3.63 GiB used: 1 GiB (27.6%) Init: systemd
  target: graphical (5) Compilers: gcc: 12.2.0 Packages: 2448 Shell: Bash v: 5.2.2 inxi: 3.3.21
```

---

### Post by TheFu on 2022-11-12
In 20.04, chromium became a snap package, not APT.
In 22.04, firefox became a snap package, not APT.

The suckage of snap packages is very high, but there are work arounds, at least for Firefox.
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04) has the details.

Snap packages are being forced onto all Ubuntu users. Best to learn a bit about them, since they have pros and cons.

---

