---
title: "Moblin vs Ubuntu Jaunty boot time"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by grigio on 2009-03-25
I tried Moblin image and it is super fast!! 16 seconds!

Is possible to import some boot performance changes in jaunty (1:20s)(*)?

It is a full desktop with XFCE.
[http://www.youtube.com/watch?v=GdFvSqL_8Yg](http://www.youtube.com/watch?v=GdFvSqL_8Yg)

(*)it is 40s (25+15) from a clean Jaunty in Vmware

---

### Post by cl333r on 2009-03-25
That's impressing, I think they not only tweaked the system for speed but also sacrificed certain features/functionality/compatibiliy, if so, I wonder which ones.

---

### Post by Marlonsm on 2009-03-25
To achieve such a fast boot, for sure they've cut something out.
And I'd rather wait 1 more min during the boot than have features missing.

I'm not saying it's not impressive, tho.

---

### Post by grigio on 2009-03-25
I think the best improvmnets are **sreadhead**, **kernel 2.6.29** and some daemons optimization/parallelization.

Moblin it's a FULL Desktop, you can install more sw from Fedora's repos and the responsiveness remains very high.

I don't see ANY sacrifice.

---

### Post by grigio on 2009-03-25
Here the Desktop loaded - i just added cairo-dock-, i don-t think Gnome would slow down much the boot time.

```

[moblin@localhost ~]$ ps -Al
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0     1     0  0  80   0 -   478 poll_s ?        00:00:00 init
5 S     0     2     0  0  75  -5 -     0 kthrea ?        00:00:00 kthreadd
1 S     0     3     2  0 -40   - -     0 migrat ?        00:00:00 migration/0
1 S     0     4     2  0  75  -5 -     0 ksofti ?        00:00:00 ksoftirqd/0
5 S     0     5     2  0 -40   - -     0 watchd ?        00:00:00 watchdog/0
1 S     0     6     2  0  75  -5 -     0 worker ?        00:00:00 events/0
1 S     0     7     2  0  75  -5 -     0 worker ?        00:00:00 work_on_cpu/0
1 S     0     8     2  0  75  -5 -     0 worker ?        00:00:00 khelper
1 S     0    11     2  0  75  -5 -     0 async_ ?        00:00:00 async/mgr
1 S     0   208     2  0  75  -5 -     0 worker ?        00:00:00 kblockd/0
1 S     0   210     2  0  75  -5 -     0 worker ?        00:00:00 kacpid
1 S     0   211     2  0  75  -5 -     0 worker ?        00:00:00 kacpi_notify
1 S     0   261     2  0  75  -5 -     0 worker ?        00:00:00 ata/0
1 S     0   262     2  0  75  -5 -     0 worker ?        00:00:00 ata_aux
1 S     0   264     2  0  75  -5 -     0 worker ?        00:00:00 ksuspend_usbd
1 S     0   269     2  0  75  -5 -     0 hub_th ?        00:00:00 khubd
1 S     0   272     2  0  75  -5 -     0 serio_ ?        00:00:00 kseriod
1 S     0   278     2  0  75  -5 -     0 worker ?        00:00:00 kmmcd
1 S     0   287     2  0  75  -5 -     0 worker ?        00:00:00 btaddconn
1 S     0   288     2  0  75  -5 -     0 worker ?        00:00:00 btdelconn
1 S     0   317     2  0  75  -5 -     0 worker ?        00:00:00 kondemand/0
1 S     0   342     2  0  80   0 -     0 pdflus ?        00:00:00 pdflush
1 S     0   343     2  0  80   0 -     0 pdflus ?        00:00:00 pdflush
1 S     0   344     2  0  75  -5 -     0 kswapd ?        00:00:00 kswapd0
1 S     0   345     2  0  75  -5 -     0 worker ?        00:00:00 aio/0
1 S     0   479     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_0
1 S     0   482     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_1
1 S     0   533     2  0  75  -5 -     0 worker ?        00:00:00 kpsmoused
1 S     0   553     2  0  75  -5 -     0 worker ?        00:00:00 hid_compat
5 S     0   582     2  0  70 -10 -     0 rfcomm ?        00:00:00 krfcommd
1 S     0   587     2  0  75  -5 -     0 kjourn ?        00:00:00 kjournald
5 S     0   623     1  0  76  -4 -   511 poll_s ?        00:00:00 udevd
1 S     0   806     2  0  75  -5 -     0 worker ?        00:00:00 mpt_poll_0
1 S     0   871     2  0  75  -5 -     0 scsi_e ?        00:00:00 scsi_eh_2
5 S    81   919     1  0  80   0 -   628 poll_s ?        00:00:00 dbus-daemon
4 S     0   930     1  0  80   0 -   474 n_tty_ tty1     00:00:00 mingetty
4 S     0   931     1  0  80   0 -  1725 poll_s ?        00:00:00 gdm-binary
5 S     0   940     1  0  99  19 -  8837 poll_s ?        00:00:00 rsyslogd
5 S    68   954     1  0  99  19 -  1383 poll_s ?        00:00:00 hald
1 S     0   957     1  0  80   0 -   476 poll_s ?        00:00:00 acpid
4 S     0   958   931  0  80   0 -  1792 poll_s ?        00:00:00 gdm-simple-sla
5 S     0   959     1  0  80   0 -  1994 poll_s ?        00:00:00 console-kit-da
4 S     0   961   958  2  80   0 -  7375 poll_s tty2     00:00:02 Xorg
0 S     0  1023   954  0  99  19 -   858 poll_s ?        00:00:00 hald-runner
0 S     0  1031  1023  0  99  19 -   877 poll_s ?        00:00:00 hald-addon-inp
4 S    68  1045  1023  0  99  19 -   790 unix_s ?        00:00:00 hald-addon-acp
5 S     0  1047     1  0  80   0 -  2928 poll_s ?        00:00:00 connmand
4 S     0  1049     1  0  80   0 -  1387 poll_s ?        00:00:00 wpa_supplicant
4 S     0  1064  1047  0  80   0 -   646 poll_s ?        00:00:00 dhclient
4 S     0  1068   958  0  80   0 -  1478 poll_s ?        00:00:00 gdm-session-wo
5 S   499  1070     1  0  80   0 -   722 poll_s ?        00:00:00 avahi-daemon
1 S   499  1071  1070  0  80   0 -   722 unix_s ?        00:00:00 avahi-daemon
4 S   500  1077  1068  0  80   0 -  1199 wait   ?        00:00:00 sh
1 S     0  1081     1  0  80   0 -  1519 poll_s ?        00:00:00 corewatcher
1 S     0  1087     1  0  80   0 -  1516 poll_s ?        00:00:00 kerneloops
1 S   500  1095     1  0  80   0 -   779 poll_s ?        00:00:00 dbus-launch
1 S     0  1096     1  0  80   0 -   752 hrtime ?        00:00:00 crond
5 S     0  1098     1  0  80   0 -   913 poll_s ?        00:00:00 bluetoothd
1 S   500  1108     1  0  80   0 -   627 poll_s ?        00:00:00 dbus-daemon
1 S   500  1115  1077  0  80   0 -  1381 poll_s ?        00:00:00 ssh-agent
0 S   500  1135  1077  0  80   0 -  4281 poll_s ?        00:00:00 xfce4-session
0 S   500  1137     1  0  80   0 -   898 poll_s ?        00:00:00 xfconfd
0 S   500  1141  1135  0  80   0 -  4632 poll_s ?        00:00:00 xfwm4
1 S   500  1142     1  0  80   0 -  3962 poll_s ?        00:00:00 xfsettingsd
1 S   500  1145     1  0  80   0 -  4634 poll_s ?        00:00:00 xfce4-settings
0 S   500  1146  1135  0  80   0 - 11126 poll_s ?        00:00:00 xfce4-panel
0 S   500  1147  1135  0  80   0 - 13559 poll_s ?        00:00:00 xfdesktop
0 S   500  1150     1  0  80   0 -   729 poll_s ?        00:00:00 gam_server
0 S   500  1151     1  0  80   0 -  3971 poll_s ?        00:00:00 kerneloops-app
0 S   500  1153     1  0  80   0 -  3971 poll_s ?        00:00:00 corewatcher-ap
0 S   500  1155     1  0  80   0 - 10101 poll_s ?        00:00:00 connman-applet
0 S   500  1158  1146  0  80   0 - 10677 poll_s ?        00:00:00 xfce4-menu-plu
0 S   500  1160     1  0  80   0 - 10772 poll_s ?        00:00:00 cairo-dock
1 S   500  1163     1  0  80   0 - 20559 poll_s ?        00:00:00 pulseaudio
0 S   500  1165     1  0  80   0 -  1581 poll_s ?        00:00:00 gvfsd
0 S   500  1170  1146  0  80   0 - 13487 poll_s ?        00:00:00 xfce4-mixer-pl
0 S   500  1171  1146  0  80   0 - 10303 poll_s ?        00:00:00 xfce4-battery-
0 S   500  1173  1146  0  80   0 - 10723 poll_s ?        00:00:00 thunar-tpa
0 S   500  1175     1  0  80   0 -  4384 poll_s ?        00:00:00 Thunar
0 S   500  1225     1  0  80   0 -  1591 poll_s ?        00:00:00 gconfd-2
0 S   500  1242     1  1  80   0 - 10744 poll_s ?        00:00:00 Terminal
0 S   500  1243  1242  0  80   0 -   490 unix_s ?        00:00:00 gnome-pty-help
0 R   500  1244  1242  0  80   0 -  1213 -      pts/0    00:00:00 bash
0 R   500  1257  1244  0  80   0 -  1159 -      pts/0    00:00:00 ps


```

---

### Post by cl333r on 2009-03-25
According to your signature you're testing Ubuntu 8.10 alpha 5.. hm..
Anyway, I've seen the benchmarks on phoronix on latest kernels put together including 2.6.29, they didn't mention any significant boot improvements.
Nonetheless, I 100% agree that Jaunty can do better, I just look at the services loaded by default and I got like 3 versions of power management, 3 actions schedulers, 2 activity loggers and even a remote backup server enabled by default, not to mention going deeper into things I have no clue about.

---

### Post by MadsRH on 2009-03-25
Did you guys read this? [http://www.phoronix.com/scan.php?page=article&item=intel_moblin_2a2&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_moblin_2a2&num=1")

If I'm not mistaken, one of the goals of Koala is to investigate how Moblin works (work has started) and implement the changes.

---

### Post by grigio on 2009-03-25
@cl333r: no I'm on **jaunty** now, anyway you are right.

I see there is sreadahed and 2.6.29 debs..

During the boot it holds on restricted drivers, wine config(?!), kernel logger and X blink 2/3 times (fglrx).

..and I have cleaned it as much as possible

---

### Post by MacUntu on 2009-03-25
> **grigio said:**
> 1:20s

I think it shouldn't need that long with your hardware.

---

### Post by zekopeko on 2009-03-25
> **grigio said:**
> I tried Moblin image and it is super fast!! 16 seconds!

Is possible to import some boot performance changes in jaunty (1:20s)?

It is a full desktop with XFCE.
[http://www.youtube.com/watch?v=GdFvSqL_8Yg](http://www.youtube.com/watch?v=GdFvSqL_8Yg)

somethings very wrong with your jaunty setup. it shouldn't boot so slow. my setup boots in like 20-30 and that's from an IDE drive.

---

### Post by grigio on 2009-03-26
> **zekopeko said:**
> somethings very wrong with your jaunty setup. it shouldn't boot so slow. my setup boots in like 20-30 and that's from an IDE drive.

It depends what software you run at boot.. what is your 

```
ls /etc/rc5.d/
```

---

### Post by grigio on 2009-03-26
moblin is only:

/etc/rc.d/rc5.d:
K84wpa_supplicant  K99ntpdate    S99local
K99ntpd            S26udev-post  S99sreadahead-pack

:O

---

### Post by taavikko on 2009-03-26
> **grigio said:**
> It depends what software you run at boot.. what is your 

```
ls /etc/rc5.d/
```

Ubuntu starts by default in runlevel 2.

---

### Post by ssam on 2009-03-26
there was a discussion on devel discuss.
[http://thread.gmane.org/gmane.linux.ubuntu.devel/27826](http://thread.gmane.org/gmane.linux.ubuntu.devel/27826)

one advantage moblin has is that it targets a small range of hardware. only intel GPUs etc. i think there will always be a trade off between speed and flexibility. however that does not mean the mainstream distros can't make big improvements.

i'd love to see a tool that rebuilds your kernel to just support your system. but then i think you might have trouble when you try to plug in a new device.

---

### Post by the8thstar on 2009-03-26
> **ssam said:**
> 
i'd love to see a tool that rebuilds your kernel to just support your system. but then i think you might have trouble when you try to plug in a new device.

I completely support this. I can't get my laptop to boot in less than 50 seconds... so boosting things up would be great, knowing I can't add more hardware anyway.

---

### Post by MacUntu on 2009-03-26
> **ssam said:**
> i'd love to see a tool that rebuilds your kernel to just support your system.

Benefits are small - at least on my systems.

---

### Post by xtoudi on 2009-03-26
> **the8thstar said:**
> I completely support this. I can't get my laptop to boot in less than 50 seconds... so boosting things up would be great, knowing I can't add more hardware anyway.

This is so strange! My boot takes about 12-14 secs on my laptop (JJ 9.04, kernel: 2.6.29) - now, with some additional services.
And after fresh install sth about 10-12 secs (kernel: 2.6.28 )..
Boot partition: ext4.

---

### Post by dirtylobster on 2009-03-26
Maybe you could boot Moblin in 6-8 seconds then. ;)

---

### Post by xtoudi on 2009-03-26
> **dirtylobster said:**
> Maybe you could boot Moblin in 6-8 seconds then. ;)

Yeah ... but ... am I wrong?? Moblin is Fedora??

---

### Post by glasen on 2009-03-26
Can you explain what you mean with "boots in 12-14 seconds"?

Does it mean time is stopped when GDM is shown? Does it mean time is stopped when GNOME is fully loaded. Or does it mean time is stopped when "usplash" is complete and GDM is loaded?

Have you used a stop watch to get the 12-14s or is it your opinion that is feels like 12-14s?

Many people say that their linux distros boot in under 20s and after asking them if they had stopped the time for a fully loaded desktop, they must admit that they only measured time to get to the boot prompt or the login-manager.

It is very hard to get a universally usable linux-distribution boot under 30s. Every second less means always trade-offs in hardware support and usability.

---

### Post by xtoudi on 2009-03-26
> **glasen said:**
> Can you explain what you mean with "boots in 12-14 seconds"?

Does it mean time is stopped when GDM is shown? Does it mean time is stopped when GNOME is fully loaded. Or does it mean time is stopped when "usplash" is complete and GDM is loaded?

Have you used a stop watch to get the 12-14s or is it your opinion that is feels like 12-14s?

Many people say that their linux distros boot in under 20s and after asking them if they had stopped the time for a fully loaded desktop, they must admit that they only measured time to get to the boot prompt or the login-manager.

It is very hard to get a universally usable linux-distribution boot under 30s. Every second less means always trade-offs in hardware support and usability.

Of course I mean time whed GDM is loaded (login screen).

---

### Post by xlnt01 on 2009-03-26
booting from grub to login (KDM kubuntu) takes me 17 seconds on my computer and 19 seconds on my laptop using Jaunty alpha 6.

---

### Post by the8thstar on 2009-03-26
Wow, you guys must have super fast hardware. BTW the boot time I was giving was from a cold boot to a fully usable desktop (I'm not counting the 3 seconds of typing in the GDM window).

---

