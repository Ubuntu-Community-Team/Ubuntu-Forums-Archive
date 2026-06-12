---
title: "ipolldevd takes 7-% cpu idling"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2009-12-15
There is a process 'ipolldevd' which takes around, 7-8% of CPU. Any idea what this could be about ? Is it polling some device ? System monitor says its waiting channel is worker_thread.

---

### Post by vikrant82 on 2009-12-15
The parent process for this is 'kthreadd' which looks like a kde process.

---

### Post by vikrant82 on 2009-12-16
Also this has something to do with my touchpad. Once I stop using my touchpad, CPU usage goes to average 2-3%. Using touchpad, its constantly around 7-8%.

---

### Post by vikrant82 on 2009-12-16
Ok Guys, I removed every single byte which could be linked to KDE and did a reboot. And there it sat, happily mocking at me. Poor KDE, got blasted for nothing.

Looks like it is spawned by kthreadd, which is something related to kernel itself. Hmm, Ok then! Let me try installing karmic version and confirm if its indeed a 2.6.32-8 kernel issue.

---

### Post by ronacc on 2009-12-16
I'm not even seeing that running on my kubuntu install .

---

### Post by vikrant82 on 2009-12-16
No luck even with previous kernel, 2.6.31.17. Looks like its something lucid has brought with it. ipolldevd still motoring at 7% ...

```

1 S     0     2     0  0  75  -5 -     0 kthrea ?        00:00:00 kthreadd
1 S     0  1121     2  7  75  -5 -     0 worker ?        00:01:55 ipolldevd

```

---

### Post by jpeddicord on 2009-12-16
kthreadd is a master kernel process that controls kernel threads. ipolldevd is likely what is polling your touchpad for information, as you seem to have found out. :)

Not entirely sure as to why ipolldevd is reporting a higher cpu percentage, though I do know that using a touchpad triggers a lot of cpu wakeups. Perhaps it is merely reporting on something that was already happening before that it didn't show?

I don't see the process here at all; maybe it is only used for certain touchpad models/drivers.

---

### Post by DouglasAWh on 2010-01-13
> **vikrant82 said:**
> There is a process 'ipolldevd' which takes around, 7-8% of CPU.

27% here. OUCH!

---

### Post by vikrant82 on 2010-01-13
And when this started for you?

---

### Post by DouglasAWh on 2010-01-13
> **vikrant82 said:**
> And when this started for you?

I just noticed it last night.  kernel is 2.6.32-10-generic (32-bit).  If any other info would be useful, it'll have to wait until I get home from work.

---

### Post by xir_ on 2010-01-14
i've noticed this with track pads.

out of interest check the number of wakeups with powertop. I find that the track pad can really kill battery life (doesn't let the CPU idle.

---

### Post by highlandsun on 2010-01-18
Same problem here. ~20% on my HP dv5z. I even have the trackpad disabled, but that didn't affect it. I just upgraded from Karmic to Lucid Alpha2 today.

---

### Post by DouglasAWh on 2010-01-18
> **highlandsun said:**
> ~20% on my HP dv5z.

Hmm, what video card and computer manufacture do people have?

I have HP/ATI on this particular machine.  Yes, 2 out of 2 isn't anything, but it got me thinking...

---

### Post by vikrant82 on 2010-01-18
```

description: VGA compatible controller
product: Mobile GM965/GL960 Integrated Graphics Controller
vendor: Intel Corporation

```
```

description: Audio device
product: 82801H (ICH8 Family) HD Audio Controller
vendor: Intel Corporation
```
```

description: CPU
product: Intel(R) Celeron(R) CPU          560  @ 2.13GHz
vendor: Intel Corp.
```
```

description: Notebook
product: HP Compaq 6710b
vendor: Hewlett-Packard
```
```
&#9116; "SynPS/2 Synaptics TouchPad" 
```

All latest updates applied. Still 6-7%.

---

### Post by vikrant82 on 2010-01-18
```
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
```

---

### Post by DouglasAWh on 2010-01-18
> **vikrant82 said:**
> [
```

description: Notebook
product: HP Compaq 6710b
vendor: Hewlett-Packard
```


We're still in the speculation stage, but 3 out of 3 HPs.

---

### Post by vikrant82 on 2010-01-20
Great news. 

The issue is fixed with following set of updates. Most noticeable is the new 2.6.32-11 kernel.

```
Start-Date: 2010-01-21  03:22:27
Install: linux-image-2.6.32-11-generic (2.6.32-11.15), linux-headers-2.6.32-11 (2.6.32-11.15), linux-headers-2.6.32-11-generic (2.6.32-11.15), keyutils (1.2-12)
Upgrade: mesa-utils (7.8.0~git20100118.0d6e3dd8-0ubuntu0sarvatt, 7.8.0~git20100120.c8b694b2-0ubuntu0sarvatt), liblaunchpad-integration1 (0.1.29, 0.1.30), xserver-xorg-input-evdev (2.3.2+git20091222.d6beb16b-0ubuntu0sarvatt, 2.3.2+git20100121.e81cd935-0ubuntu0sarvatt), bind9-host (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), linux-headers-generic (2.6.32.10.10, 2.6.32.11.11), libxine1-x (1.1.16.3-1ubuntu2, 1.1.16.3-1ubuntu3), xserver-xorg-video-ati (6.12.99+git20100114.3d158716-0ubuntu0sarvatt, 6.12.99+git20100120.30a19b75-0ubuntu0sarvatt), indicator-application (0.0.9-0ubuntu1, 0.0.9-0ubuntu3), apport-symptoms (0.3, 0.5), smbclient (3.4.3-2ubuntu1, 3.4.3-2ubuntu2), bash-completion (1.0-3ubuntu2, 1.1-3), dnsutils (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), linux-image-generic (2.6.32.10.10, 2.6.32.11.11), gnome-screensaver (2.28.0-1ubuntu4, 2.28.0-1ubuntu5), libxine1-misc-plugins (1.1.16.3-1ubuntu2, 1.1.16.3-1ubuntu3), libmp4v2-0 (1.6dfsg-0.2ubuntu6, 1.6dfsg-0.2ubuntu7), smbfs (3.4.3-2ubuntu1, 3.4.3-2ubuntu2), libglu1-mesa (7.8.0~git20100118.0d6e3dd8-0ubuntu0sarvatt, 7.8.0~git20100120.c8b694b2-0ubuntu0sarvatt), mplayer (1.0~rc3+svn20090426-1ubuntu12, 1.0~rc3+svn20090426-1ubuntu13), libdns53 (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), mysql-common (5.1.41-3ubuntu1, 5.1.41-3ubuntu2), mesa-common-dev (7.8.0~git20100118.0d6e3dd8-0ubuntu0sarvatt, 7.8.0~git20100120.c8b694b2-0ubuntu0sarvatt), libfontconfig1 (2.6.0-1ubuntu13, 2.8.0-2ubuntu1), fontconfig-config (2.6.0-1ubuntu13, 2.8.0-2ubuntu1), libxine1-bin (1.1.16.3-1ubuntu2, 1.1.16.3-1ubuntu3), apport (1.11-0ubuntu5, 1.12-0ubuntu1), linux-libc-dev (2.6.32-10.14, 2.6.32-11.15), libavcodec-extra-52 (0.5+svn20090706-5ubuntu2, 0.5+svn20090706-5ubuntu3), libsmbclient (3.4.3-2ubuntu1, 3.4.3-2ubuntu2), libisccc50 (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), libavutil-extra-49 (0.5+svn20090706-5ubuntu2, 0.5+svn20090706-5ubuntu3), libpanel-applet2-0 (2.29.5.1-0ubuntu1, 2.29.5.1-0ubuntu2), fontconfig (2.6.0-1ubuntu13, 2.8.0-2ubuntu1), software-center (1.1.8, 1.1.9), mysql-server-core-5.1 (5.1.41-3ubuntu1, 5.1.41-3ubuntu2), gstreamer0.10-ffmpeg (0.10.9-3, 0.10.9-3build1), samba-common-bin (3.4.3-2ubuntu1, 3.4.3-2ubuntu2), liblwres50 (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), libxine1-ffmpeg (1.1.16.3-1ubuntu2, 1.1.16.3-1ubuntu3), python-imaging (1.1.6-3ubuntu1, 1.1.7-1), libhal1 (0.5.14-0ubuntu2, 0.5.14-0ubuntu3), gdm (2.29.5-0ubuntu3, 2.29.5-0ubuntu5), launchpad-integration (0.1.29, 0.1.30), libgsf-1-common (1.14.15-1ubuntu1, 1.14.16-1ubuntu1), libhal-storage1 (0.5.14-0ubuntu2, 0.5.14-0ubuntu3), gnome-system-monitor (2.28.0-1ubuntu1, 2.28.0-1ubuntu2), libbind9-50 (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), python-gnupginterface (0.3.2-9ubuntu2, 0.3.2-9.1), python-problem-report (1.11-0ubuntu5, 1.12-0ubuntu1), xdg-utils (1.0.2-6.1, 1.0.2-6.1ubuntu1), libwbclient0 (3.4.3-2ubuntu1, 3.4.3-2ubuntu2), python-launchpad-integration (0.1.29, 0.1.30), libappindicator0 (0.0.9-0ubuntu1, 0.0.9-0ubuntu3), libgl1-mesa-dev (7.8.0~git20100118.0d6e3dd8-0ubuntu0sarvatt, 7.8.0~git20100120.c8b694b2-0ubuntu0sarvatt), libmysqlclient16 (5.1.41-3ubuntu1, 5.1.41-3ubuntu2), libisccfg50 (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), libgl1-mesa-dri (7.8.0~git20100118.0d6e3dd8-0ubuntu0sarvatt, 7.8.0~git20100120.c8b694b2-0ubuntu0sarvatt), libgl1-mesa-glx (7.8.0~git20100118.0d6e3dd8-0ubuntu0sarvatt, 7.8.0~git20100120.c8b694b2-0ubuntu0sarvatt), samba-common (3.4.3-2ubuntu1, 3.4.3-2ubuntu2), libgtkmathview0c2a (0.8.0-3ubuntu2, 0.8.0-4), libgc1c2 (6.8-1.2, 6.8-1.2ubuntu1), gnome-panel (2.29.5.1-0ubuntu1, 2.29.5.1-0ubuntu2), python-apport (1.11-0ubuntu5, 1.12-0ubuntu1), libisc50 (9.6.1.dfsg.P2-1, 9.6.1.dfsg.P3-1~build1), libquicktime1 (1.1.3+debian-1, 1.1.3+debian-1build1), xserver-xorg-input-synaptics (1.2.0+git20091212.babe5288-0ubuntu0tormod, 1.2.0+git20100120.f7559a5e-0ubuntu0sarvatt), mplayer-nogui (1.0~rc3+svn20090426-1ubuntu12, 1.0~rc3+svn20090426-1ubuntu13), apport-gtk (1.11-0ubuntu5, 1.12-0ubuntu1), linux-generic (2.6.32.10.10, 2.6.32.11.11), xserver-xorg-video-radeon (6.12.99+git20100114.3d158716-0ubuntu0sarvatt, 6.12.99+git20100120.30a19b75-0ubuntu0sarvatt), libgsf-1-114 (1.14.15-1ubuntu1, 1.14.16-1ubuntu1), gnome-panel-data (2.29.5.1-0ubuntu1, 2.29.5.1-0ubuntu2), libxine1-console (1.1.16.3-1ubuntu2, 1.1.16.3-1ubuntu3), libxine1 (1.1.16.3-1ubuntu2, 1.1.16.3-1ubuntu3)
Remove: libwildmidi0 (0.2.2-2), libdc1394-22 (2.1.2-1), libsoundtouch1c2 (1.3.1-2), libdca0 (0.0.5-3), libopenspc0 (0.3.99a-2), libfftw3-3 (3.2.1-2ubuntu2), libass4 (0.9.8-1), abiword-help (2.6.8-5ubuntu2), libgnomeprint2.2-data (2.18.6-1build1), libcelt0 (0.7.0-1), libgme0 (0.5.5-1), libkate1 (0.3.7-3), libmimic0 (1.0.4-2), libgnomeprint2.2-0 (2.18.6-1build1), libgnomeprintui2.2-0 (2.18.4-1), libgnomeprintui2.2-common (2.18.4-1), libofa0 (0.9.3-3.1), libiptcdata0 (1.0.3-1ubuntu1), libgnomecups1.0-1 (0.2.3-3build1)
End-Date: 2010-01-21  03:28:52
```

---

### Post by vikrant82 on 2010-01-20
Well, it wasn't a kernel issue. As problem disappeared from old kernel also.  Some *other* package fixed it.

---

### Post by xir_ on 2010-01-21
> **vikrant82 said:**
> Well, it wasn't a kernel issue. As problem disappeared from old kernel also.  Some *other* package fixed it.

Thanks for the update.

One thing ubuntu really isn't all that great with is power management. Hopefully it'll become more of a focus now that the boot time goals have been achieved.

hopefully one day there will be an option to dynamically under-volt CPUs and GPUs and more focus on getting the cpu to idle.

---

