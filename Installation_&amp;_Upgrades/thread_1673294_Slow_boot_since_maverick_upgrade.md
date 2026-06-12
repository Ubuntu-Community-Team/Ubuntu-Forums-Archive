---
title: "Slow boot since maverick upgrade"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by JohnReid on 2011-01-22
Hi,

Since upgrading my mythbuntu box from lucid to maverick my boot times have been much slower. Looking at dmesg I can see delays. Can anyone who knows more than me point me in the right direction to fix these?

```
[    2.123939] usbhid: USB HID core driver
[    2.396712] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.396721] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 124
[    2.396746] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 93
[    2.396752] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 81
[    2.396757] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 80
[    2.396763] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 70
[    2.396767] EXT4-fs (sda1): 5 orphan inodes deleted
[    2.396768] EXT4-fs (sda1): recovery complete
[    2.904650] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   22.524338] udev[387]: starting version 163
[   22.550341] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[   22.551534] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[   22.604799] lp: driver loaded but no devices found
[   22.663618] usbcore: deregistering interface driver usbhid
[   22.663636] Adding 11285624k swap on /dev/sda5.  Priority:-1 extents:1 across:11285624k 
[   22.678818] parport_pc 00:03: reported by Plug and Play ACPI
[   22.678940] parport0: PC-style at 0x378 (0x778), irq 5, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   22.683131] saa7164 driver loaded
[   22.683172] saa7164 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.685018] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=4,insmod option]
[   22.685025] saa7164[0]/0: found at 0000:02:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfb800000
[   22.685032] saa7164 0000:02:00.0: setting latency timer to 64
[   22.703527] ppdev: user-space parallel port driver
[   22.706245] IR NEC protocol handler initialized
[   22.706490] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   22.708772] IR RC5(x) protocol handler initialized
[   22.711488] IR RC6 protocol handler initialized
[   22.713834] IR JVC protocol handler initialized
[   22.716150] IR Sony protocol handler initialized
[   22.720336] lirc_dev: IR Remote Control driver registered, major 250 
[   22.723500] IR LIRC bridge handler initialized
[   22.732255] Registered IR keymap rc-rc6-mce
[   22.732345] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/virtual/rc/rc0/input4
[   22.749594]   alloc irq_desc for 22 on node -1

``````
[   23.484757] drm: registered panic notifier
[   23.484763] Slow work thread pool: Starting up
[   23.485653] Slow work thread pool: Ready
[   23.485807] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20100428/video-1937)
[   23.485870] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   23.485921] ACPI: Video Device [GFX0] (multi-head: no  rom: yes  post: no)
[   23.485942] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   23.538424] type=1400 audit(1295697442.113:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1105 comm="apparmor_parser"
[   23.538848] type=1400 audit(1295697442.113:11): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1109 comm="apparmor_parser"
[   24.438740] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   24.438745] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   24.440624] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.113494] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   30.231073] saa7164_downloadimage() Image downloaded, booting...
[   30.341368] saa7164_downloadimage() Image booted successfully.
[   30.341387] starting firmware download(2)
[   32.674118] saa7164_downloadimage() Image downloaded, booting...
[   34.101002] saa7164_downloadimage() Image booted successfully.
[   34.101019] firmware download complete.
[   34.140958] tveeprom 5-0000: Hauppauge model 89619, rev D3F2, serial# 7088724
[   34.140961] tveeprom 5-0000: MAC address is 00:0d:fe:6c:2a:54
[   34.140963] tveeprom 5-0000: tuner model is NXP 18271C2_716x (idx 152, type 4)
[   34.140965] tveeprom 5-0000: TV standards PAL(B/G) NTSC(M) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xfc)
[   34.140968] tveeprom 5-0000: audio processor is SAA7164 (idx 43)
[   34.140969] tveeprom 5-0000: decoder processor is SAA7164 (idx 40)
[   34.140971] tveeprom 5-0000: has radio
[   34.140972] saa7164[0]: Hauppauge eeprom: model=89619
[   34.290597] tda18271 6-0060: creating new instance
[   34.294981] TDA18271HD/C2 detected @ 6-0060
[   34.802508] DVB: registering new adapter (saa7164)
[   34.802514] DVB: registering adapter 0 frontend 0 (NXP TDA10048HN DVB-T)...
[   34.831989] tda18271 7-0060: creating new instance
[   34.836230] TDA18271HD/C2 detected @ 7-0060

```

---

### Post by JohnReid on 2011-01-22
Apologies for double post.

---

