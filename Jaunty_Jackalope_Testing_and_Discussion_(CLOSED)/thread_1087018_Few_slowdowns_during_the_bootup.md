---
title: "Few slowdowns during the bootup"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrek on 2009-03-04
Hi!

I'm obviously using the Ubuntu 9.04 Jaunty Jackalope. I'm experiencing two little slowdowns while the system is booting up :

1) After selecting the ubuntu's entry in Grub menu, I'm seeing such an information:
```
Boot from (hd0,8) ext4...
```
and it takes few seconds before the ubuntu splash is being shown
What's going on?

2) I checked my dmesg.
Here's the interesting part

```
[    4.394093] usbcore: registered new interface driver usbhid
[    4.394099] usbhid: v2.6:USB HID core driver
[    6.247485] EXT4-fs: barriers enabled
[    6.265738] kjournald2 starting.  Commit interval 5 seconds
[    6.265763] EXT4-fs: delayed allocation enabled
[    6.265766] EXT4-fs: file extents enabled
[    6.266189] EXT4-fs: mballoc enabled
[    6.266197] EXT4-fs: mounted filesystem with ordered data mode.
[   15.563120] udev: starting version 139
[   16.016545] Linux agpgart interface v0.103
[   16.020733] agpgart: Detected VIA P4X266 chipset
[   16.105210] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   16.105325] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
```

and it goes on.. but have a look at the gap between 

[    **6.266197**] EXT4-fs: mounted filesystem with ordered data mode.
and
[   **15.563120**] udev: starting version 139

Correct me if I'm wrong - but those numbers on the left are.. passed time, right?
So, is ext4 that slowing down my bootup process? ( My / and /home are on ext4 fs, of course )

Another thing :

```
[   20.521381] EXT4 FS on sda9, internal journal on sda9:8
[   21.584221] EXT4-fs: barriers enabled
[   21.605609] kjournald2 starting.  Commit interval 5 seconds
[   21.605852] EXT4 FS on sda10, internal journal on sda10:8
[   21.605857] EXT4-fs: delayed allocation enabled
[   21.605860] EXT4-fs: file extents enabled
[   21.606062] EXT4-fs: mballoc enabled
[   21.606070] EXT4-fs: mounted filesystem with ordered data mode.
[   22.567048] type=1505 audit(1236199377.336:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2399
[   22.716764] type=1505 audit(1236199377.488:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2403
[   22.717113] type=1505 audit(1236199377.488:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2403
[   22.717226] type=1505 audit(1236199377.488:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2403
[   22.717326] type=1505 audit(1236199377.488:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2403
[   22.998000] type=1505 audit(1236199377.768:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2408
[   22.998425] type=1505 audit(1236199377.768:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2408
[   23.097406] type=1505 audit(1236199377.868:9): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2412
[   23.161750] type=1505 audit(1236199377.932:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2416
[   29.758064] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   29.758090] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   **29.758151**] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   **33.229707**] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   **41.356347**] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
[   **43.924042**] eth0: no IPv6 routers present

```

Especially the ending - what does eth0 do for such a long time? Or perhaps it's the fault of pulseaudio?

Thanks for any ideas.

---

### Post by MacUntu on 2009-03-04
Can only comment on this one:
```
[    6.266197] EXT4-fs: mounted filesystem with ordered data mode.
[   15.563120] udev: starting version 139
```
There are some scripts (like readahead) doing their jobs between those two lines so that's ok.

---

