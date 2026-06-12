---
title: "Xorg dead, no internet :("
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by danf_1979 on 2008-12-19
Hi folks, I had a show stopper today. X is dead and I have no networking. The thing would not have been that bad if I had internet, but I don't.

I'm "kind" of worried about the X problem, since I even tried vesa driver and it didn't work. But what I really want to fix right now is the wifi connection. So...

How can I enable the dhcp wifi connection from the console? I need to do by hand what the network manager applet does.

---

### Post by danf_1979 on 2008-12-19
Configuring /etc/resolv.conf and /etc/network/interfaces made the wifi connection work ok again.

$ cat /etc/resolv.conf
```

nameserver 190.160.0.11
nameserver 200.83.1.5
nameserver 200.74.121.12

```

$ cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid belkin54g
wireless-channels 11
wireless-mode managed

```

After having internet again, I ran a full upgrade with aptitude. This fixed Xorg.

---

### Post by danf_1979 on 2008-12-19
Till some minutes ago I wasn't sure to do a full-upgrade with aptitude. I was seeing a lot of packages being removed, so I used safe-upgrade for several days. This time that was a bad decision, and finally made my X unusable.

Here is the relevant aptitude's log from today's full-upgrade:

```

===============================================================================
[REMOVE, DEPENDENCIAS] xserver-xorg-video-all
[REMOVE, DEPENDENCIAS] xserver-xorg-video-apm
[REMOVE, DEPENDENCIAS] xserver-xorg-video-ark
[REMOVE, DEPENDENCIAS] xserver-xorg-video-ati
[REMOVE, DEPENDENCIAS] xserver-xorg-video-fbdev
[REMOVE, DEPENDENCIAS] xserver-xorg-video-mach64
[REMOVE, DEPENDENCIAS] xserver-xorg-video-mga
[REMOVE, DEPENDENCIAS] xserver-xorg-video-nsc
[REMOVE, DEPENDENCIAS] xserver-xorg-video-nv
[REMOVE, DEPENDENCIAS] xserver-xorg-video-openchrome
[REMOVE, DEPENDENCIAS] xserver-xorg-video-r128
[REMOVE, DEPENDENCIAS] xserver-xorg-video-radeonhd
[REMOVE, DEPENDENCIAS] xserver-xorg-video-rendition
[REMOVE, DEPENDENCIAS] xserver-xorg-video-s3
[REMOVE, DEPENDENCIAS] xserver-xorg-video-s3virge
[REMOVE, DEPENDENCIAS] xserver-xorg-video-siliconmotion
[REMOVE, DEPENDENCIAS] xserver-xorg-video-sis
[REMOVE, DEPENDENCIAS] xserver-xorg-video-tdfx
[REMOVE, DEPENDENCIAS] xserver-xorg-video-tga
[REMOVE, DEPENDENCIAS] xserver-xorg-video-trident
[REMOVE, DEPENDENCIAS] xserver-xorg-video-v4l
[REMOVE, DEPENDENCIAS] xserver-xorg-video-vesa
[UPGRADE] xserver-xorg 1:7.4~5ubuntu5 -> 1:7.4~5ubuntu7
[UPGRADE] xserver-xorg-core 2:1.5.3-1ubuntu1 -> 2:1.5.99.3-0ubuntu3
[UPGRADE] xserver-xorg-input-evdev 1:2.1.0-0ubuntu1 -> 1:2.1.0-0ubuntu2
[UPGRADE] xserver-xorg-input-kbd 1:1.3.1-1ubuntu2 -> 1:1.3.1-2ubuntu1
[UPGRADE] xserver-xorg-input-mouse 1:1.3.0-2 -> 1:1.3.0-2ubuntu1
[UPGRADE] xserver-xorg-input-synaptics 0.15.2-0ubuntu7 -> 0.15.2-0ubuntu8
[UPGRADE] xserver-xorg-input-vmmouse 1:12.5.1-4ubuntu1 -> 1:12.5.1-4ubuntu3
[UPGRADE] xserver-xorg-input-wacom 1:0.8.1.4-0ubuntu3 -> 1:0.8.1.6-1ubuntu1
[UPGRADE] xserver-xorg-video-chips 1:1.2.0-1build2 -> 1:1.2.0-1ubuntu1
[UPGRADE] xserver-xorg-video-cirrus 1:1.2.1-1build2 -> 1:1.2.1-1build3
[UPGRADE] xserver-xorg-video-geode 2.10.1-5 -> 2.11.0-1
[UPGRADE] xserver-xorg-video-i128 1:1.3.1-1 -> 1:1.3.1-1build1
[UPGRADE] xserver-xorg-video-i740 1:1.2.0-1build2 -> 1:1.2.0-1build3
[UPGRADE] xserver-xorg-video-intel 2:2.5.1-1ubuntu5 -> 2:2.5.1-1ubuntu6
[UPGRADE] xserver-xorg-video-neomagic 1:1.2.1-1build2 -> 1:1.2.1-1ubuntu1
[UPGRADE] xserver-xorg-video-radeon 1:6.9.0+git20081003.f9826a56-0ubuntu4 -> 1:6.9.0+git20081003.f9826a56-0ubuntu5
[UPGRADE] xserver-xorg-video-savage 1:2.2.1-3 -> 1:2.2.1-3build1
[UPGRADE] xserver-xorg-video-sisusb 1:0.9.0-1build2 -> 1:0.9.0-1ubuntu1
[UPGRADE] xserver-xorg-video-tseng 1:1.2.0-1build2 -> 1:1.2.0-1ubuntu1
[UPGRADE] xserver-xorg-video-vmware 1:10.16.5-1 -> 1:10.16.5-1build1
[UPGRADE] xserver-xorg-video-voodoo 1:1.2.0-1build2 -> 1:1.2.0-1ubuntu1
===============================================================================

```

---

