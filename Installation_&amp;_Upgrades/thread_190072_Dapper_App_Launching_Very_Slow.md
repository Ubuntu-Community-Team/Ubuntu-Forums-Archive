---
title: "Dapper App Launching Very Slow"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-06-05
Hi All, 

I upgraded Breezy to Dapper without any problems. Everything runs. However I'm noticing an annoying lag when starting apps. When I launch Gedit, Terminal Window, Calculator, Firefox, or anything else, it seems to take anywhere from 8 to 20 seconds sometimes before the window appears. Once the app is launched, performance appears to be normal. I'm not sure what's going on. If anybody has any clues, please let me know. I've got a P4-3GHz with 1Gig ram. Incidentally I posted about this a few days ago but the thread got kind of hijacked by someone with a similar problem but no feedback on my situation came directly back to me (or so I thought). I've included my top-b output below. Thanks.

```
richard@ubuntu:~$ top -b
top - 19:52:02 up  1:27,  2 users,  load average: 0.23, 0.45, 0.55
Tasks:  83 total,   1 running,  82 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.3% us,  0.9% sy,  8.6% ni, 60.8% id,  2.4% wa,  0.0% hi,  0.0% si
Mem:   1027204k total,   806168k used,   221036k free,   150928k buffers
Swap:  2931820k total,        0k used,  2931820k free,   444104k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8302 richard   15   0  2192  984  756 R  2.0  0.1   0:00.01 top
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.29 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.55 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  147 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  148 root      15   0     0    0    0 S  0.0  0.0   0:00.10 pdflush
  150 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  149 root      17   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  751 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1832 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1833 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata_hotplug/0
 1836 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1837 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1910 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1925 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1954 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 2052 root      15   0     0    0    0 S  0.0  0.0   0:00.17 kjournald
 2284 root      13  -4  2428  916  368 S  0.0  0.1   0:00.26 udevd
 3119 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3150 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 hda_codec/0
 3754 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 3755 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 3827 root      16   0  2712  856  660 S  0.0  0.1   0:00.00 pppd
 4268 root      16   0  1684  500  412 S  0.0  0.0   0:00.02 dd
 4270 klog      22   0  2428 1352  388 S  0.0  0.1   0:00.36 klogd
 4289 messageb  16   0  2192  872  664 S  0.0  0.1   0:00.59 dbus-daemon
 4304 haldaemo  16   0  7004 5608 1568 S  0.0  0.5   0:15.48 hald
 4305 root      17   0  2720  972  836 S  0.0  0.1   0:00.41 hald-runner
 4310 haldaemo  16   0  2008  796  696 S  0.0  0.1   0:00.00 hald-addon-acpi
 4404 haldaemo  15   0  2004  796  692 S  0.0  0.1   0:00.01 hald-addon-keyb
 4421 haldaemo  16   0  2008  864  760 S  0.0  0.1   0:00.49 hald-addon-stor
 4422 haldaemo  16   0  2008  860  760 S  0.0  0.1   0:00.59 hald-addon-stor
 4673 root      16   0 10912 1800 1228 S  0.0  0.2   0:00.00 gdm
 4685 root      15   0 11348 2628 1996 S  0.0  0.3   0:00.05 gdm
 4694 root      15   0  281m  17m 6960 S  0.0  1.8   7:23.50 Xorg
 4761 hplip     16   0 12868  924  696 S  0.0  0.1   0:00.00 hpiod
 4770 hplip     15   0  9404 4680 1100 S  0.0  0.5   0:00.01 python
 4877 root      20   0  1968  712  616 S  0.0  0.1   0:00.01 hcid
 4882 root      18   0  1620  460  384 S  0.0  0.0   0:00.00 sdpd
 4892 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4905 root      16   0  1624  296  232 S  0.0  0.0   0:00.00 mdadm
 4939 daemon    16   0  1804  400  296 S  0.0  0.0   0:00.00 atd
 4952 root      16   0  2116  840  684 S  0.0  0.1   0:00.00 cron
 5047 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 5048 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 5049 root      16   0  1560  488  424 S  0.0  0.0   0:00.00 getty
 5050 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 5051 root      16   0  1564  488  424 S  0.0  0.0   0:00.00 getty
 5052 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 5067 richard   16   0 19620 9.8m 7464 S  0.0  1.0   0:04.92 gnome-session
 5110 richard   16   0  4328  688  444 S  0.0  0.1   0:00.00 ssh-agent
 5113 richard   16   0  2712  648  520 S  0.0  0.1   0:00.00 dbus-launch
 5114 richard   16   0  2192  948  776 S  0.0  0.1   0:00.01 dbus-daemon
 5116 richard   16   0  6520 4112 1880 S  0.0  0.4   0:01.28 gconfd-2
 5119 richard   19   0  2340  728  532 S  0.0  0.1   0:00.02 gnome-keyring-d
 5121 richard   17   0  6544 3164 2264 S  0.0  0.3   0:00.21 bonobo-activati
 5123 richard   15   0 27556 9236 7112 S  0.0  0.9   0:01.45 gnome-settings-
 5129 richard   16   0  5804 4332 1232 S  0.0  0.4   0:01.33 esd
 5139 richard   15   0 15740 9684 6784 S  0.0  0.9   0:15.08 metacity
 5144 richard   15   0 50704  22m  13m S  0.0  2.3   0:11.95 gnome-panel
 5146 richard   15   0 70588  25m  17m S  0.0  2.5   0:14.94 nautilus
 5149 richard   15   0 17392 5280 3928 S  0.0  0.5   0:08.02 gnome-volume-ma
 5153 richard   15   0 30376  11m 8340 S  0.0  1.1   0:05.51 update-notifier
 5156 richard   15   0  8648 3860 3036 S  0.0  0.4   0:00.68 gnome-vfs-daemo
 5162 richard   15   0 37856 8032 6520 S  0.0  0.8   0:00.91 gnome-cups-icon
 5171 richard   15   0 17880 5656 4128 S  0.0  0.6   0:00.59 gnome-power-man
 5180 richard   15   0 53268 8368 6756 S  0.0  0.8   0:00.40 trashapplet
 5190 richard   16   0  2284  800  700 S  0.0  0.1   0:00.00 mapping-daemon
 5197 richard   16   0 23320  10m 7788 S  0.0  1.0   0:10.39 clock-applet
 5199 richard   15   0 31164  10m 8252 S  0.0  1.1   0:04.89 mixer_applet2
 5205 richard   15   0 15068 5480 4312 S  0.0  0.5   0:01.68 gnome-screensav
 5484 root      26  10  2152 1192  644 S  0.0  0.1   0:00.00 acpid
 5517 cupsys    26  10  4072 1764 1304 S  0.0  0.2   0:00.85 cupsd
 5628 syslog    26  10  1768  712  584 S  0.0  0.1   0:00.00 syslogd
 6815 richard   15   0 26776 9248 6340 S  0.0  0.9   0:06.02 notification-da
 8285 richard   15   0 40496  14m 9268 S  0.0  1.4   0:07.93 gnome-terminal
 8289 richard   25   0  2288  684  580 S  0.0  0.1   0:00.00 gnome-pty-helpe
 8290 richard   15   0  4532 2132 1324 S  0.0  0.2   0:00.04 bash

```

---

### Post by ubuntu_demon on 2006-06-05
Report the result of :
$uname -a 

Memory probably isn't an issue but just in case you should post the result of :
$free -m

Try using top or gnome-system-monitor to find programs which use very much memory or cpu power. When you are logged into gnome without any programs running your cpu usage should be well below 5% on average with such a powerful cpu as yours.
$top 
$gnome-system-monitor

Maybe you used prelink in breezy and you are not using it in Dapper ?
Here's a guide for prelink : [http://ubuntuforums.org/showthread.php?t=74197&](http://ubuntuforums.org/showthread.php?t=74197&)

Maybe you were running a 686 kernel in breezy while running 386 in Dapper? Try the following :
$sudo apt-get install linux-686
and reboot :
$sudo reboot

Maybe you should switch to a different graphics driver. You mentioned having an intel onboard videocard.
$apt-cache search intel video
For example this might be the best one for you :
xserver-xorg-driver-i810 - X.Org X server -- Intel i8xx, i9xx display driver
$sudo apt-get install *video-driver*
You will probably have to reconfigure xserver-xorg :
$sudo dpkg-reconfigure-xserver
And reboot afterwards :
$sudo reboot

You should be able to get equal performance in Dapper as in Breezy. For me Dapper feels faster than Breezy.

Xubuntu is a bit faster than Ubuntu. You might want to try it :
$sudo apt-get install xubuntu-desktop

---

### Post by richardq on 2006-06-05
[QUOTE=ubuntu_demon]
Maybe you were running a 686 kernel in breezy while running 386 in Dapper? Try the following :
$sudo apt-get install linux-686
and reboot :
$sudo reboot
[/QUOTE]

I *was* running a 686 kernel in Breezy. Never thought of that. Just switched it per your instructions and launching (and overall snappiness) is now noticeably faster. Tremendous thanks!

I may still fiddle with the video drivers just to see if I can tweak it a bit more.

Thanks again for the help.

---

### Post by ubuntu_demon on 2006-06-06
[QUOTE=richardq]I *was* running a 686 kernel in Breezy. Never thought of that. Just switched it per your instructions and launching (and overall snappiness) is now noticeably faster. Tremendous thanks!

I may still fiddle with the video drivers just to see if I can tweak it a bit more.

Thanks again for the help.[/QUOTE]
No problem. Please also try prelink. It's easy to do and you'll notice it when launching big applications.

In some cases changing the videodriver brings down the cpu usage a bit. It probably won't help much regarding the launching time of applications.

---

### Post by heldal on 2006-06-06
You wouldn't happen to have a system with the harddisk and cd/dvd-drive on the same IDE-channel?

The HAL-daemon (hald) on dapper is polling optical drives for changes every 2 sec or so. If this is the case, check to see if it makes a difference if you put a CD/DVD in the drive, or if killing "hald" changes anything. 

The obvious fix to this problem is to make sure removable IDE-media are located on a separate IDE-channel. Those with no such option (notably notebooks) are screwed unless they can manage without the "hald" process.

---

