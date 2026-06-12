---
title: "Dapper upgrade - performance woes"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-06-02
I've upgraded my system successfully to Dapper and while everything appears to be installed correctly and running, the performance took a nosedive compared to Breezy. Maybe I've got to adjust my configuration.

I've got a P4-3GHz with 1GB ram and Intel onboard video. 

The problem is not with any specific application, but *all* applications seem to take an extra long time to start. Gedit for instance takes a full 5 or 6 seconds to appear once I launch it. This is the same for many apps I've tried. Breezy would just zip along, but this slowness on app launch is driving me crazy.

I read something about possibly Beagle being a culprit. Can anyone point at anything else I should check?

---

### Post by lkagan on 2006-06-02
The following command will output some important information when trying to debug performance issues.  Please paste the results back to the forum so we can have a closer look:
```
top -b
```

Larry

---

### Post by woot on 2006-06-02
well, finally a soulmate! 

I do not have 1gig of ram, i have 512 to be honest, and im on a laptop with a P4 1,8GHz but dapper seems so slow for me :S I mean ofcourse its not a super-brand-new machine, oh, i even have a dedicated gfx-card, no cutting edge neither but heh, its no shared memory: nvidia geforce mx 440, 64 mb.


So when i did a *fresh* install of dapper (like some month ago, the beta version) I immediately noticed the slower stuff..Im currently running kernel 2.6.15-23-386
and gnome window manager.

When i boot up into the graphic part and even when i let the desktop come up very long, so everything should be loaded the first time i have to load the main-start menu takes ages! The loading of the icons aswell, but thats not what i mean, i truely mean the popping up of the menu. And starting apps goes slow as hell. As the OP zit, gedit takes 5 -6 seconds, firefox takes to long as well. Once firefox is open, all is fine, i can switch between tabs as fast as i want no *lag* or whatsoever...

my current top -b

```

top - 16:08:50 up 40 min,  2 users,  load average: 2.37, 1.94, 1.83
Tasks:  90 total,   1 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s): 37.0% us, 31.3% sy,  0.0% ni, 31.0% id,  0.0% wa,  0.3% hi,  0.3% si
Mem:    515880k total,   453992k used,    61888k free,     1840k buffers
Swap:   963860k total,    18968k used,   944892k free,   190180k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4991 woot      15   0 45488  31m  10m S 29.7  6.3   8:28.22 python
 4423 root      15   0 58096  35m 9868 S 16.4  7.0   1:56.05 Xorg
 5044 woot      15   0 54192  16m 9968 S  7.9  3.3   0:05.76 gnome-terminal
 4882 woot      15   0 14460 8576 6312 S  6.9  1.7   1:12.56 metacity
 4891 woot      15   0 37980  16m  11m S  2.8  3.3   0:35.45 gnome-panel
 5046 woot      15   0  134m  49m  19m S  1.6  9.7   1:25.99 firefox-bin
 5088 woot      15   0 57324  17m 6252 S  0.9  3.4   0:34.42 xmms
 5255 woot      15   0 43312  30m 4272 S  0.6  6.1   0:38.13 wish
 6301 woot      16   0  2204 1096  848 R  0.6  0.2   0:00.13 top
 4871 woot      15   0 27692 9484 7172 S  0.3  1.8   0:03.33 gnome-settings-
 4925 woot      15   0 32684  12m 8672 S  0.3  2.4   0:05.21 stickynotes_app
    1 root      16   0  1568  532  460 S  0.0  0.1   0:02.21 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.08 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.12 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  144 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  145 root      15   0     0    0    0 S  0.0  0.0   0:00.03 pdflush
  147 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  146 root      15   0     0    0    0 S  0.0  0.0   0:00.10 kswapd0
  734 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1831 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1844 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1853 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 2166 root      12  -4  2428  916  368 S  0.0  0.2   0:00.58 udevd
 2953 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3034 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3053 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3194 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 3195 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 usb-storage
 3479 dhcp      14  -2  2340  776  468 S  0.0  0.2   0:00.00 dhclient3
 4160 root      16   0  2152 1188  644 S  0.0  0.2   0:00.00 acpid
 4249 syslog    16   0  1764  672  548 S  0.0  0.1   0:00.02 syslogd
 4275 root      16   0  1680  496  412 S  0.0  0.1   0:00.02 dd
 4277 klog      20   0  2412 1332  388 S  0.0  0.3   0:00.08 klogd
 4296 messageb  16   0  2192  868  672 S  0.0  0.2   0:00.28 dbus-daemon
 4311 haldaemo  17   0  6952 5560 1568 S  0.0  1.1   0:04.20 hald
 4312 root      16   0  2720  992  848 S  0.0  0.2   0:00.04 hald-runner
 4317 haldaemo  17   0  2008  796  696 S  0.0  0.2   0:00.00 hald-addon-acpi
 4371 haldaemo  15   0  2004  796  692 S  0.0  0.2   0:00.06 hald-addon-keyb
 4388 haldaemo  16   0  2012  864  760 S  0.0  0.2   0:00.16 hald-addon-stor
 4389 haldaemo  16   0  2008  864  760 D  0.0  0.2   0:00.16 hald-addon-stor
 4419 root      16   0 10908 1812 1236 S  0.0  0.4   0:00.00 gdm
 4420 root      16   0 11312 2616 1980 S  0.0  0.5   0:00.05 gdm
 4450 hplip     16   0 12868  920  696 S  0.0  0.2   0:00.00 hpiod
 4459 hplip     15   0  9408 4668 1092 S  0.0  0.9   0:00.04 python
 4506 cupsys    16   0  4060 1864 1364 S  0.0  0.4   0:01.61 cupsd
 4548 root      21   0  1548  376  312 S  0.0  0.1   0:00.00 irattach
 4576 root      21   5  1556  260  192 S  0.0  0.1   0:00.11 powernowd
 4592 root      16   0  5772 1416  924 S  0.0  0.3   0:00.02 nmbd
 4594 root      18   0  8400 2104 1432 S  0.0  0.4   0:00.00 smbd
 4637 root      17   0  1968  712  616 S  0.0  0.1   0:00.00 hcid
 4641 root      18   0  1616  456  384 S  0.0  0.1   0:00.00 sdpd
 4656 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4669 root      16   0  1628  300  232 S  0.0  0.1   0:00.00 mdadm
 4691 root      18   0  8400  960  288 S  0.0  0.2   0:00.00 smbd
 4705 daemon    19   0  1800  396  296 S  0.0  0.1   0:00.00 atd
 4718 root      16   0  2120  840  680 S  0.0  0.2   0:00.00 cron
 4793 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4794 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4795 root      16   0  1564  492  424 S  0.0  0.1   0:00.00 getty
 4796 root      16   0  1564  492  424 S  0.0  0.1   0:00.00 getty
 4797 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4798 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4815 woot      16   0 19840  10m 7504 S  0.0  2.0   0:00.81 x-session-manag
 4858 woot      16   0  4332  688  444 S  0.0  0.1   0:00.00 ssh-agent
 4861 woot      15   0  2712  648  524 S  0.0  0.1   0:00.00 dbus-launch
 4862 woot      15   0  2196  908  768 S  0.0  0.2   0:00.00 dbus-daemon
 4864 woot      16   0  6224 3780 1884 S  0.0  0.7   0:00.71 gconfd-2
 4867 woot      18   0  2340  732  532 S  0.0  0.1   0:00.00 gnome-keyring-d
 4869 woot      16   0  6300 2980 2268 S  0.0  0.6   0:00.18 bonobo-activati
 4874 woot      16   0  5804 4324 1228 S  0.0  0.8   0:00.20 esd
 4893 woot      15   0 74056  15m  10m S  0.0  3.0   0:02.37 nautilus
 4898 woot      16   0 17376 5244 3908 S  0.0  1.0   0:00.34 gnome-volume-ma
 4907 woot      15   0 19332  10m 7780 S  0.0  2.0   0:00.95 update-notifier
 4910 woot      15   0  8656 3852 3020 S  0.0  0.7   0:00.23 gnome-vfs-daemo
 4919 woot      16   0 54368 8164 6484 S  0.0  1.6   0:03.89 gnome-cups-icon
 4931 woot      15   0 17868 5616 4064 S  0.0  1.1   0:00.48 gnome-power-man
 4935 woot      16   0  2284  800  700 S  0.0  0.2   0:00.00 mapping-daemon
 4956 woot      15   0 14752 2808 1852 S  0.0  0.5   0:04.11 gnome-screensav
 5053 woot      16   0  2288  684  580 S  0.0  0.1   0:00.00 gnome-pty-helpe
 5054 woot      15   0  5636 3280 1364 S  0.0  0.6   0:00.21 bash
 5082 woot      18   0  4184 1696 1080 S  0.0  0.3   0:00.01 mozilla-thunder
 5087 woot      21   0  4228 1724 1064 S  0.0  0.3   0:00.01 run-mozilla.sh
 5093 woot      16   0  110m  46m  19m S  0.0  9.3   0:37.18 mozilla-thunder
 5253 woot      15   0 70104  26m 7704 S  0.0  5.2   0:20.49 skype
 6070 woot      15   0 56380  11m 1044 S  0.0  2.3   0:00.00 xmms

```

well its kinda a snapshot, it refreshes every x seconds. As you can see i have some standard apps open: xmms, skype, amsn(2conversations), firefox (5 tabs), and a terminal

What tool should be used to monitor harddisk access? perhaps when id do a clean startup and monitor harddisk usage during loading progs id be able to figure out if there is a lot of reading or not

*edit*
forgot to tell: im also running gdesklets (some starterbar and some monitors) im quit aware that this stuff might be resource-hungry, but with or without (and they dont start up automatically at bootup) i have the same slow dapper (which i didnt had in breezy)

*edit*

P.S im not trying to hijack your thread, im just stating that your not alone, and im very curious what could cause it

---

### Post by lkagan on 2006-06-02
Okay, so now we have a starting point.  First off,  looks like memory is not the culprit here.  Linux will almost always use all available memory, that's a good thing.  However, when you start using swap is when things slow down.  You're using about 18 MB of swap which is okay, I'm currently using about 40 MB of swap and speed is not an issue.  However, your load average is high.  It looks like the first thing we should look into is why python is using 30% of your CPU.  This may be difficult because python is **very **widely used in Ubuntu.  To figure out what's using python, try typing the following:
```
ps auxw | grep python
```
and paste the results here.

I have a feeling it may be the gdesklets or some panel applet.

By the way, sorry for the not-so-perfect top command.  To only display the info once, you would use
```
top -b -n1
```
In case you didn't already figure it out, hitting <ctl>+c kills the repeating top command.

---

### Post by woot on 2006-06-02
Im quit sure it has nothing to do with gdesklets, as when i dont start em, i have to slow stuff aswell. Even before i had the desklets i had it already..

So to be honest, the disks reads quit alot whilst opening the main menu of ubuntu...im really thinking of some defragmented issue but i installed dapper on a empty 13 giga partition... I don´t know if its possible that this partion is fysically fragmented over other (ntfs) partions of the harddisk...

Some panel applet could cause it, though im not using anything special (that im aware of)

so: a newtop -b -n1 after a nice reboot:

```
woot@patrick:~$ top -b -n1
top - 17:35:44 up 4 min,  2 users,  load average: 2.37, 1.31, 0.55
Tasks:  82 total,   1 running,  81 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.9% us,  5.5% sy,  0.5% ni, 36.4% id, 45.0% wa,  0.5% hi,  0.3% si
Mem:    515880k total,   298124k used,   217756k free,     4956k buffers
Swap:   963860k total,        0k used,   963860k free,   176644k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5229 woot      15   0  2192  984  756 R  2.0  0.2   0:00.01 top
    1 root      16   0  1568  532  460 S  0.0  0.1   0:02.21 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.63 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  144 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  145 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  147 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  146 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  734 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 1827 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1845 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1852 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 2174 root      12  -4  2428  924  368 S  0.0  0.2   0:00.54 udevd
 2953 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3028 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3036 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3224 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 3225 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 usb-storage
 3578 dhcp      13  -2  2336  552  244 S  0.0  0.1   0:00.00 dhclient3
 4039 root      16   0  2156 1196  644 S  0.0  0.2   0:00.00 acpid
 4128 syslog    16   0  1768  676  548 S  0.0  0.1   0:00.01 syslogd
 4154 root      16   0  1684  500  412 S  0.0  0.1   0:00.03 dd
 4156 klog      19   0  2412 1336  388 S  0.0  0.3   0:00.07 klogd
 4175 messageb  16   0  2192  864  672 S  0.0  0.2   0:00.09 dbus-daemon
 4190 haldaemo  17   0  6960 5564 1568 S  0.0  1.1   0:02.31 hald
 4191 root      17   0  2720  996  848 S  0.0  0.2   0:00.04 hald-runner
 4196 haldaemo  17   0  2008  796  696 S  0.0  0.2   0:00.00 hald-addon-acpi
 4250 haldaemo  16   0  2004  792  692 S  0.0  0.2   0:00.00 hald-addon-keyb
 4267 haldaemo  16   0  2008  816  716 S  0.0  0.2   0:00.00 hald-addon-stor
 4268 haldaemo  16   0  2012  820  716 S  0.0  0.2   0:00.00 hald-addon-stor
 4595 root      15   0 10908 1804 1228 S  0.0  0.3   0:00.00 gdm
 4614 root      16   0 11312 2616 1980 S  0.0  0.5   0:00.01 gdm
 4621 root      15   0 35764  21m 6780 S  0.0  4.4   0:02.98 Xorg
 4636 hplip     16   0 12868  920  696 S  0.0  0.2   0:00.00 hpiod
 4645 hplip     15   0  9408 4668 1092 S  0.0  0.9   0:00.00 python
 4692 cupsys    16   0  4064 1864 1364 S  0.0  0.4   0:00.11 cupsd
 4734 root      25   0  1548  376  312 S  0.0  0.1   0:00.00 irattach
 4762 root      21   5  1556  264  192 S  0.0  0.1   0:00.00 powernowd
 4778 root      16   0  5772 1388  896 S  0.0  0.3   0:00.00 nmbd
 4780 root      18   0  8396 2104 1432 S  0.0  0.4   0:00.00 smbd
 4823 root      18   0  1968  708  616 S  0.0  0.1   0:00.00 hcid
 4827 root      18   0  1616  456  384 S  0.0  0.1   0:00.00 sdpd
 4842 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4843 root      18   0  8396  960  288 S  0.0  0.2   0:00.00 smbd
 4856 root      16   0  1628  296  232 S  0.0  0.1   0:00.00 mdadm
 4891 daemon    20   0  1800  396  296 S  0.0  0.1   0:00.00 atd
 4904 root      16   0  2120  832  680 S  0.0  0.2   0:00.00 cron
 4981 root      16   0  1564  492  424 S  0.0  0.1   0:00.00 getty
 4982 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4983 root      17   0  1564  492  424 S  0.0  0.1   0:00.00 getty
 4984 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4985 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4986 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 5001 woot      15   0 19668   9m 7520 S  0.0  2.0   0:00.65 x-session-manag
 5044 woot      16   0  4332  688  444 S  0.0  0.1   0:00.00 ssh-agent
 5047 woot      15   0  2716  652  524 S  0.0  0.1   0:00.00 dbus-launch
 5048 woot      16   0  2192  904  768 S  0.0  0.2   0:00.01 dbus-daemon
 5050 woot      16   0  6228 3784 1884 S  0.0  0.7   0:00.69 gconfd-2
 5053 woot      18   0  2344  732  532 S  0.0  0.1   0:00.00 gnome-keyring-d
 5055 woot      17   0  6300 2972 2256 S  0.0  0.6   0:00.17 bonobo-activati
 5057 woot      15   0 27660 9508 7184 S  0.0  1.8   0:00.54 gnome-settings-
 5068 woot      16   0  5800 4324 1228 S  0.0  0.8   0:00.18 esd
 5074 woot      16   0 14300 8144 6036 S  0.0  1.6   0:00.75 metacity
 5083 woot      15   0 37336  15m  11m S  0.0  3.2   0:01.77 gnome-panel
 5085 woot      15   0 65676  15m  11m S  0.0  3.0   0:01.81 nautilus
 5088 woot      16   0 17352 5248 3904 S  0.0  1.0   0:00.07 gnome-volume-ma
 5100 woot      15   0 19308  10m 7772 S  0.0  2.0   0:00.56 update-notifier
 5105 woot      15   0  8512 3756 2996 S  0.0  0.7   0:00.09 gnome-vfs-daemo
 5109 woot      16   0 54216 7996 6480 S  0.0  1.5   0:00.42 gnome-cups-icon
 5111 woot      15   0 31972  11m 8588 S  0.0  2.3   0:01.10 stickynotes_app
 5123 woot      15   0 17840 5596 4036 S  0.0  1.1   0:00.08 gnome-power-man
 5131 woot      16   0  2284  800  700 S  0.0  0.2   0:00.00 mapping-daemon
 5147 woot      16   0 14756 2768 1844 S  0.0  0.5   0:00.05 gnome-screensav
 5160 woot      15   0 33032  13m 8552 S  0.0  2.7   0:01.35 gnome-terminal
 5163 woot      17   0  2288  684  580 S  0.0  0.1   0:00.00 gnome-pty-helpe
 5164 woot      16   0  5636 3284 1364 S  0.0  0.6   0:00.28 bash
 5185 woot      16   0  112m  33m  17m S  0.0  6.6   0:05.52 firefox-bin

woot@patrick:~$

```

and a new ps auxw | grep python:
```

woot@patrick:~$ ps auxw | grep python
hplip     4645  0.0  0.9   9408  4668 ?        S    17:31   0:00 python /usr/sbin/hpssd
woot      5271  0.0  0.1   2884   812 pts/0    S+   17:37   0:00 grep python
woot@patrick:~$

```

---

### Post by lkagan on 2006-06-02
Hmm.  Not too much documentation around on hpssd.  It looks like that turns on your printer detection.  I've looked around for an answer as to why it's hogging the processor but found nothing.  All I can say is for a temporary solution, simply kill the process.  
```
sudo kill <processid>
```
Where <processid> would be 4645 from your output above.  Note that this process number will change every time the process starts.

Things should run faster for the current session.  I wish I had more to offer.

Larry

---

### Post by woot on 2006-06-02
thanks for the clear explanation, but i was aware that the process id changes :)

ill give it a try

---

### Post by lkagan on 2006-06-02
Sorry, I didn't mean to belittle you. Ubuntu has helped bring in a new breed of Linux users so I was going for the least common denomenator.

---

### Post by woot on 2006-06-02
nono, ofcourse, and perhaps someone else who reads it might need it. Being complete is positive...cant do any harm with it :D

---

### Post by richardq on 2006-06-02
[QUOTE=lkagan]Please paste the results back to the forum so we can have a closer look:
```
top -b
```

Larry[/QUOTE]

Well I finally got back from work to my home pc. Doing a fresh reboot, and taking a quick peek at application start times, I'm actually getting: gedit (25sec), firefox (20sec) and terminal window (18sec). Each time is from the time I click the icon to the time it appears on screen. Something's definitely wrong.

Here is the top -b output:

```
richard@ubuntu:~$ top -b
top - 20:20:09 up  1:09,  2 users,  load average: 0.29, 0.68, 0.45
Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.3% us,  0.4% sy,  0.3% ni, 89.0% id,  2.0% wa,  0.0% hi,  0.0% si
Mem:   1027204k total,   520400k used,   506804k free,   133080k buffers
Swap:  2931820k total,        0k used,  2931820k free,   177832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6263 richard   16   0  2192  988  756 R 11.8  0.1   0:00.14 top
 6073 richard   15   0 99284  33m  17m S  1.7  3.4   0:51.21 firefox-bin
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.31 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.34 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  147 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  148 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush
  150 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  149 root      17   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  751 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1832 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1833 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 ata_hotplug/0
 1836 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 1837 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1
 1909 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1925 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1954 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 2052 root      15   0     0    0    0 S  0.0  0.0   0:00.02 kjournald
 2284 root      12  -4  2432  916  368 S  0.0  0.1   0:00.43 udevd
 3111 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3164 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 hda_codec/0
 3754 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 3755 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 3828 root      16   0  2712  860  660 S  0.0  0.1   0:00.00 pppd
 4123 root      16   0  2152 1192  644 S  0.0  0.1   0:00.03 acpid
 4269 root      15   0  1684  496  412 S  0.0  0.0   0:00.02 dd
 4271 klog      20   0  2424 1348  388 S  0.0  0.1   0:03.21 klogd
 4297 messageb  16   0  2196  860  664 S  0.0  0.1   0:00.16 dbus-daemon
 4312 haldaemo  16   0  7008 5612 1568 S  0.0  0.5   1:00.43 hald
 4313 root      15   0  2716  968  836 S  0.0  0.1   0:00.03 hald-runner
 4318 haldaemo  16   0  2008  792  696 S  0.0  0.1   0:00.00 hald-addon-acpi
 4407 haldaemo  15   0  2008  796  692 S  0.0  0.1   0:00.00 hald-addon-keyb
 4424 haldaemo  16   0  2008  864  760 S  0.0  0.1   0:00.11 hald-addon-stor
 4425 haldaemo  16   0  2008  864  760 S  0.0  0.1   0:00.33 hald-addon-stor
 4449 root      16   0 10912 1804 1236 S  0.0  0.2   0:00.01 gdm
 4450 root      16   0 11348 2624 1996 S  0.0  0.3   0:00.05 gdm
 4453 root      15   0  280m  16m 7124 S  0.0  1.6   0:19.70 Xorg
 4531 hplip     16   0 12872  920  696 S  0.0  0.1   0:00.00 hpiod
 4534 hplip     15   0  9404 4676 1100 S  0.0  0.5   0:00.01 python
 4647 root      20   0  1972  708  616 S  0.0  0.1   0:00.00 hcid
 4653 root      20   0  1620  460  384 S  0.0  0.0   0:00.00 sdpd
 4662 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4675 root      16   0  1624  292  232 S  0.0  0.0   0:00.00 mdadm
 4709 daemon    16   0  1804  396  296 S  0.0  0.0   0:00.00 atd
 4722 root      16   0  2120  840  684 S  0.0  0.1   0:00.00 cron
 4815 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 4816 root      16   0  1560  492  424 S  0.0  0.0   0:00.00 getty
 4817 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 4818 root      16   0  1564  496  424 S  0.0  0.0   0:00.00 getty
 4819 root      16   0  1560  492  424 S  0.0  0.0   0:00.00 getty
 4820 root      16   0  1560  488  424 S  0.0  0.0   0:00.00 getty
 5428 cupsys    26  10  4068 1776 1304 S  0.0  0.2   0:00.20 cupsd
 5697 syslog    26  10  1768  708  584 S  0.0  0.1   0:00.00 syslogd
 5824 richard   15   0 19588 9984 7404 S  0.0  1.0   0:09.06 gnome-session
 5867 richard   16   0  4328  692  444 S  0.0  0.1   0:00.00 ssh-agent
 5870 richard   16   0  2716  648  520 S  0.0  0.1   0:00.00 dbus-launch
 5871 richard   16   0  2192  904  768 S  0.0  0.1   0:00.01 dbus-daemon
 5873 richard   16   0  6520 4108 1880 S  0.0  0.4   0:03.54 gconfd-2
 5876 richard   20   0  2340  732  532 S  0.0  0.1   0:00.12 gnome-keyring-d
 5878 richard   17   0  6312 2988 2252 S  0.0  0.3   0:00.48 bonobo-activati
 5880 richard   15   0 27408 9128 7100 S  0.0  0.9   0:01.19 gnome-settings-
 5884 richard   16   0  6012 4344 1340 S  0.0  0.4   0:00.04 esd
 5958 richard   15   0  3020  444  224 S  0.0  0.0   0:00.00 esd
 5966 richard   15   0 14364 8052 6092 S  0.0  0.8   0:10.59 metacity
 5971 richard   15   0 39296  19m  11m S  0.0  2.0   0:13.54 gnome-panel
 5973 richard   15   0 56644  15m  11m S  0.0  1.5   0:09.84 nautilus
 5976 richard   16   0 17396 5220 3880 S  0.0  0.5   0:00.26 gnome-volume-ma
 5983 richard   15   0 19236  10m 7772 S  0.0  1.0   0:08.87 update-notifier
 5985 richard   15   0  8516 3764 3012 S  0.0  0.4   0:00.33 gnome-vfs-daemo
 5997 richard   15   0 37844 8032 6516 S  0.0  0.8   0:00.80 gnome-cups-icon
 5999 richard   16   0  2284  800  700 S  0.0  0.1   0:00.00 mapping-daemon
 6003 richard   15   0 17888 5608 4084 S  0.0  0.5   0:00.22 gnome-power-man
 6012 richard   15   0 14752 2776 1852 S  0.0  0.3   0:00.53 gnome-screensav
 6015 richard   15   0 53260 8248 6644 S  0.0  0.8   0:00.84 trashapplet
 6025 richard   15   0 38588  10m 7964 S  0.0  1.1   0:08.39 gweather-applet
 6031 richard   16   0 23392  10m 7784 S  0.0  1.0   0:09.78 clock-applet
 6033 richard   15   0 31172  10m 8252 S  0.0  1.1   0:08.50 mixer_applet2
 6062 richard   15   0 40416  18m  11m S  0.0  1.9   0:12.73 gedit
 6123 richard   15   0 40948  15m 9308 S  0.0  1.5   0:22.06 gnome-terminal
 6128 richard   22   0  2288  684  580 S  0.0  0.1   0:00.00 gnome-pty-helpe
 6129 richard   15   0  4528 2132 1328 S  0.0  0.2   0:00.20 bash
```

---

### Post by woot on 2006-06-03
how about your partitions? would you think its possible they're fragmented? do you hear your harddisk doing a lot of reading whilst opening firefox/gedit etc? Im trying to find out if you got the same issue as i have cuz it sounds a lot like!

btw i dont even know if its possible that a fragmented harddisk would cause gedit to load slow..as the gedit binary (if it works like that) supposable should be small....

---

### Post by llamakc on 2006-06-03
hdparm can make a world of difference with slowly-performing disks.

---

### Post by lkagan on 2006-06-04
Oh boy.  This one isn't going to be easy.  Your system looks fine as far as performance is concerned.  

Let's take a look at your logs.  Please restart your system, then start one of the applications that takes too long.  Next, do the following  at your system terminal:
```

$ cd
$ mkdir logs
$ tail -n50 .xsession-errors > logs/xsession
$ sudo tail -n50 /var/log/debug > logs/debug
$ sudo tail -n50 /var/log/dmesg > logs/dmesg
$ sudo tail -n50 /var/log/kern.log > logs/kern
$ sudo tail -n50 /var/log/messages > logs/messages
$ sudo tail -n50 /var/log/user.log > logs/user
$ sudo tail -n50 /var/log/Xorg.0.log > logs/Xorg
$ tar -cvjf logs.tar.bz logs

```
Now attach the logs.tar.bz file to your post and I'll have a look at them and hopefully I can catch something.

You can now optionally remove the logs directory you just created and the log.tar.gz file.

Larry

---

### Post by woot on 2006-06-04
[QUOTE=llamakc]hdparm can make a world of difference with slowly-performing disks.[/QUOTE]


you mean to make sure DMA is on? if im not mistaken dma was on here by default...

---

### Post by woot on 2006-06-04
[QUOTE=lkagan]
Let's take a look at your logs.  Please restart your system, then start one of the applications that takes too long.  Next, do the following  at your system terminal:
```
code

```
[/QUOTE]


should the new log files be made during the startup of the prog, or just after it was loaded completely?

---

### Post by lkagan on 2006-06-04
Just after

---

### Post by woot on 2006-06-04
well here it is...

---

### Post by lkagan on 2006-06-04
After looking through the logs, I don't see anything that would give me any clues.  I'm sorry but I'm stuck.  Can I suggest that you update the file of your logs though.  Someone else with a bit more knowledge than me may try to help you out but not be able to view the archive.  You saved it as tar.gz but it's really compressed with bzip2 so should be tar.bz.  I wish you the best of luck and please let us know if/when you find a solution.

Larry

---

### Post by woot on 2006-06-05
thnx for your time, after this exam period ill probably do a total format of my win/linux partitions...


i rezipped it to .gz with the same command as the forum wouldnt let me upload a bz... :)

---

### Post by heldal on 2006-06-21
Slow disk-reads may be caused by the HAL-daemon (hald) polling IDE-devices for changes and blocking the IDE channel on some computers with HDD and CD/DVD-drives on the same channel. Try to kill 'hald' or stop the service with the following command and see if that does anything to the performance:

sudo /etc/init.d/dbus stop

---

### Post by Bene on 2006-08-15
Hi,

I had problems with disk speed until I done this ```
sudo /etc/init.d/dbus stop
```. HAL is stopped now. Can you please give me some hint which services will not working any more, after disabling dbus? For example my USB stick is not found automagically anymore, and I can not mount it.

FYI: Before  I have had around 5MB/sec, after 15-17MB/sec

Thanks a lot,
 Bene

---

### Post by richardq on 2006-08-15
> **Bene said:**
> Hi,

I had problems with disk speed until I done this ```
sudo /etc/init.d/dbus stop
```. HAL is stopped now. Can you please give me some hint which services will not working any more, after disabling dbus? 

Thanks a lot,
 Bene

I'm not sure about what stopping dbus will do. However I found out two useful things:

1. If I started my pc and let it sit at the gdm login prompt for a few minutes before logging in, I wouldn't get the HAL initialization error. If I logged in right away I'd get the error.

2. More importantly, I was seeing slow application launching and general slowness on much of the system. Unrelated to this problem, I followed [this thread]("http://ubuntuforums.org/showthread.php?t=89491&highlight=speeding") on speeding up the boot process by disabling unneeded services and it fixed ALL my performance problems. The system now boots slightly quicker, gives no HAL error even when immediately logging in, and my application startup times and overall system performance are much much better. I didn't disable a lot of services, only those that seemed obviously superfluous to me (like PCMCIA, some HP-related services, some Nvidia drivers - I have Intel graphics), but obviously one of them was causing all my problems.

Good luck. Hopefully this is of some help.

---

### Post by Bene on 2006-08-16
Hi,

there is no problem with boot up speed at my laptop - there are problems with disk-speed. If HAL is enabled, then I have a result of 5MB/sec with ```
hdparm -t /dev/hda
```. After disabling via ```
sudo /etc/init.d/dbus stop
``` I get 15-17MB/sec.

So my question is if I may disable HAL without disabling the automount feature of my USB stick.

Have a nice day - Bene

---

### Post by richardq on 2006-08-16
Did you try letting it sit for 5 minutes at the login prompt before logging in? Originally this allowed me to log in without giving the HAL error. Not a good solution but I'm not sure if you tried it.

I'm not sure how old or new your laptop is, and I know that generally those drives are slower than desktop drives, but just for reference, my hard drives are giving hdparm -t results of about 55MB/s. This is over 3 times more than what you're getting. Is this reasonable? I'm not sure.

I tried stopping dbus a while back when first trying to solve my problem but it gave me several different problems including the automount problem you mention.

[This thread]("http://ubuntuforums.org/showthread.php?t=198277&highlight=hal+fstab") might be useful.

---

