---
title: "problems on boot-repair"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by penguincwarrior on 2013-01-31
my newly bought laptop uses UEFI bios, which causes me a lot trouble trying to install ubuntu.
Eventually I got to this site:[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and downloaded Ubuntu-Secure-Remix iso .I chose not to boot u disk in UEFI mode. After installation, ubuntu cannot be booted, so I tried the boot-repair.
I chose the Recommend Repair, but the software says:
"please close all your package managers (software center, update manager, synaptic,...) then try again"
I typed ps aux under terminal, and sure no package manager is working.
How can I solve this problem?
 
PS: the software gave me an report [paste.ubuntu.com/1592583]("http://ubuntuforums.org/paste.ubuntu.com/1592583") will this help?
Laptop:Asus r400ei321vd-sl, using k45vd
Current System:win7 home 64 bit
Wanna run both win7 and Ubuntu(12.10) systems
Thanks!

Another PS:
ubuntu@ubuntu:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  24588  2572 ?        Ss   09:49   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    09:49   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    09:49   0:00 [ksoftirqd/0]
root         6  0.0  0.0      0     0 ?        S    09:49   0:00 [migration/0]
root         7  0.0  0.0      0     0 ?        S    09:49   0:00 [watchdog/0]
root         8  0.0  0.0      0     0 ?        S    09:49   0:00 [migration/1]
root        10  0.0  0.0      0     0 ?        S    09:49   0:00 [ksoftirqd/1]
root        11  0.0  0.0      0     0 ?        S    09:49   0:00 [watchdog/1]
root        12  0.0  0.0      0     0 ?        S    09:49   0:00 [migration/2]
root        14  0.0  0.0      0     0 ?        S    09:49   0:00 [ksoftirqd/2]
root        15  0.0  0.0      0     0 ?        S    09:49   0:00 [watchdog/2]
root        16  0.0  0.0      0     0 ?        S    09:49   0:00 [migration/3]
root        18  0.0  0.0      0     0 ?        S    09:49   0:00 [ksoftirqd/3]
root        19  0.0  0.0      0     0 ?        S    09:49   0:00 [watchdog/3]
root        20  0.0  0.0      0     0 ?        S<   09:49   0:00 [cpuset]
root        21  0.0  0.0      0     0 ?        S<   09:49   0:00 [khelper]
root        22  0.0  0.0      0     0 ?        S    09:49   0:00 [kdevtmpfs]
root        23  0.0  0.0      0     0 ?        S<   09:49   0:00 [netns]
root        25  0.0  0.0      0     0 ?        S    09:49   0:00 [sync_supers]
root        26  0.0  0.0      0     0 ?        S    09:49   0:00 [bdi-default]
root        27  0.0  0.0      0     0 ?        S<   09:49   0:00 [kintegrityd]
root        28  0.0  0.0      0     0 ?        S<   09:49   0:00 [kblockd]
root        29  0.0  0.0      0     0 ?        S<   09:49   0:00 [ata_sff]
root        30  0.0  0.0      0     0 ?        S    09:49   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S<   09:49   0:00 [md]
root        32  0.0  0.0      0     0 ?        S    09:49   0:00 [kworker/0:1]
root        34  0.0  0.0      0     0 ?        S    09:49   0:00 [khungtaskd]
root        35  0.0  0.0      0     0 ?        S    09:49   0:00 [kswapd0]
root        36  0.0  0.0      0     0 ?        SN   09:49   0:00 [ksmd]
root        37  0.0  0.0      0     0 ?        SN   09:49   0:00 [khugepaged]
root        38  0.0  0.0      0     0 ?        S    09:49   0:00 [fsnotify_mark]
root        39  0.0  0.0      0     0 ?        S    09:49   0:00 [ecryptfs-kthre
root        40  0.0  0.0      0     0 ?        S<   09:49   0:00 [crypto]
root        49  0.0  0.0      0     0 ?        S<   09:49   0:00 [kthrotld]
root        51  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_0]
root        52  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_1]
root        53  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_2]
root        54  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_3]
root        55  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_4]
root        56  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_5]
root        60  0.1  0.0      0     0 ?        S    09:49   0:06 [kworker/u:5]
root        61  0.1  0.0      0     0 ?        S    09:49   0:06 [kworker/u:6]
root        63  0.0  0.0      0     0 ?        S<   09:49   0:00 [binder]
root        83  0.0  0.0      0     0 ?        S<   09:49   0:00 [deferwq]
root        84  0.0  0.0      0     0 ?        S<   09:49   0:00 [charger_manage
root        85  0.0  0.0      0     0 ?        S<   09:49   0:00 [devfreq_wq]
root       166  0.0  0.0      0     0 ?        S    09:49   0:00 [kworker/2:2]
root       310  0.0  0.0      0     0 ?        S    09:49   0:00 [scsi_eh_6]
root       311  0.0  0.0      0     0 ?        S    09:49   0:00 [usb-storage]
root       332  0.0  0.0      0     0 ?        S<   09:49   0:00 [ttm_swap]
root       629  0.0  0.0      0     0 ?        S<   09:49   0:00 [loop0]
root       996  0.0  0.0      0     0 ?        S    09:49   0:01 [kworker/1:2]
root      1620  0.0  0.0  17364   900 ?        S    09:49   0:00 upstart-udev-br
root      1635  0.0  0.0  22428  2188 ?        Ss   09:49   0:00 /sbin/udevd --d
syslog    1639  0.0  0.0 249468  1432 ?        Sl   09:49   0:00 rsyslogd -c5
102       1643  0.0  0.0  25088  2380 ?        Ss   09:49   0:01 dbus-daemon --s
root      1654  0.0  0.0  19168  1724 ?        Ss   09:49   0:00 /usr/sbin/bluet
avahi     1661  0.0  0.0  32300  1764 ?        S    09:49   0:00 avahi-daemon: r
avahi     1662  0.0  0.0  32176   468 ?        S    09:49   0:00 avahi-daemon: c
root      1789  0.0  0.0      0     0 ?        S<   09:49   0:00 [cfg80211]
root      1807  0.0  0.0      0     0 ?        S    09:49   0:00 [irq/45-mei]
root      1814  0.0  0.0      0     0 ?        S<   09:49   0:00 [krfcommd]
root      1877  0.0  0.0  69716  3280 ?        Ss   09:49   0:00 /usr/sbin/cupsd
root      1920  0.0  0.0      0     0 ?        S<   09:49   0:00 [led_workqueue]
root      1936  0.0  0.0      0     0 ?        S<   09:49   0:00 [kpsmoused]
root      1953  0.0  0.0      0     0 ?        S<   09:49   0:00 [kmpathd]
root      1960  0.0  0.0      0     0 ?        S<   09:49   0:00 [kmpath_handler
root      1964  0.0  0.0      0     0 ?        S    09:49   0:00 [kworker/3:2]
root      1984  0.0  0.0  15188   400 ?        S    09:49   0:00 upstart-socket-
root      2015  0.0  0.0      0     0 ?        S<   09:49   0:00 [kvm-irqfd-clea
root      2048  0.0  0.0  83304  3244 ?        Ss   09:49   0:00 /usr/sbin/modem
root      2085  0.0  0.0      0     0 ?        S<   09:49   0:00 [hd-audio0]
root      2098  0.0  0.1 246432  6060 ?        Ssl  09:49   0:00 NetworkManager
root      2126  0.0  0.0  87444  2436 tty4     Ss   09:49   0:00 /bin/login -f  
root      2132  0.0  0.0  87444  2432 tty5     Ss   09:49   0:00 /bin/login -f  
root      2156  0.0  0.0  87444  2436 tty2     Ss   09:49   0:00 /bin/login -f  
root      2166  0.0  0.0  87444  2436 tty3     Ss   09:49   0:00 /bin/login -f  
root      2172  0.0  0.0  87444  2436 tty6     Ss   09:49   0:00 /bin/login -f  
root      2201  0.0  0.0   4464   820 ?        Ss   09:49   0:00 acpid -c /etc/a
root      2205  0.0  0.0  19112   980 ?        Ss   09:49   0:00 cron
daemon    2207  0.0  0.0  16908   156 ?        Ss   09:49   0:00 atd
root      2327  0.0  0.0  21116   688 ?        Ss   09:49   0:00 /usr/sbin/irqba
root      2470  0.0  0.1 2091796 3936 ?        Sl   09:49   0:00 /usr/sbin/conso
ubuntu    2646  0.0  0.0  26500  3492 tty2     S+   09:49   0:00 -bash
ubuntu    2647  0.0  0.0  26500  3492 tty6     S+   09:49   0:00 -bash
ubuntu    2648  0.0  0.0  26500  3488 tty3     S+   09:49   0:00 -bash
ubuntu    2649  0.0  0.0  26500  3488 tty4     S+   09:49   0:00 -bash
ubuntu    2651  0.0  0.0  26500  3488 tty5     S+   09:49   0:00 -bash
root      2673  0.0  0.0  31860  2428 ?        Ss   09:49   0:00 /sbin/wpa_suppl
whoopsie  2679  0.0  0.1 204376  5060 ?        Ssl  09:49   0:00 whoopsie
root      3044  0.0  0.0  87444  2436 tty1     Ss   09:49   0:00 /bin/login -f  
ubuntu    3279  0.0  0.0  26500  3488 tty1     S+   09:49   0:00 -bash
root      3468  0.0  0.1 222164  4412 ?        Sl   09:49   0:00 /usr/lib/upower
root      3632  0.0  0.0 190816  3476 ?        Sl   09:49   0:00 /usr/lib/accoun
ubuntu    3645  0.0  0.1 369228  6396 ?        S<l  09:49   0:00 /usr/bin/pulsea
rtkit     3647  0.0  0.0 168872  1348 ?        SNl  09:49   0:00 /usr/lib/rtkit/
ubuntu    3661  0.0  0.0  96052  3020 ?        S    09:49   0:00 /usr/lib/pulsea
colord    3675  0.0  0.1 279180  4688 ?        Sl   09:49   0:00 /usr/lib/x86_64
root      5288  0.0  0.1 195940  4564 ?        Sl   09:50   0:00 /usr/lib/policy
root      5354  0.0  0.7 270704 31220 ?        SLsl 09:50   0:00 lightdm
root      5367  1.0  0.4 114540 18896 tty7     Ss+  09:50   0:43 /usr/bin/X :0 -
root      5371  0.0  0.1 174984  3944 ?        Sl   09:50   0:00 lightdm --sessi
ubuntu    5402  0.0  0.2 398020 10480 ?        Ssl  09:50   0:00 gnome-session -
ubuntu    5437  0.0  0.0  12488   320 ?        Ss   09:50   0:00 /usr/bin/ssh-ag
ubuntu    5440  0.0  0.0  24420   604 ?        S    09:50   0:00 /usr/bin/dbus-l
ubuntu    5441  0.0  0.0  26616  2924 ?        Ss   09:50   0:00 //bin/dbus-daem
ubuntu    5443  0.0  0.0 347796  3488 ?        Sl   09:50   0:00 /usr/lib/at-spi
ubuntu    5447  0.0  0.0  24072  1708 ?        S    09:50   0:00 /bin/dbus-daemo
ubuntu    5450  0.0  0.0 124624  3336 ?        Sl   09:50   0:00 /usr/lib/at-spi
ubuntu    5461  0.0  0.0 262608  3220 ?        Sl   09:50   0:00 /usr/lib/dconf/
ubuntu    5470  0.0  0.0  57760  3388 ?        S    09:50   0:00 /usr/lib/x86_64
ubuntu    5482  0.0  0.7 801448 30516 ?        Sl   09:50   0:01 /usr/lib/gnome-
ubuntu    5489  0.0  0.0 378688  3880 ?        Sl   09:50   0:00 /usr/bin/gnome-
ubuntu    5495  0.0  0.0 197828  3112 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
ubuntu    5499  0.0  0.0 345104  3256 ?        Sl   09:50   0:00 /usr/lib/gvfs//
ubuntu    5507  0.8  2.2 1322024 88472 ?       Sl   09:50   0:36 compiz
ubuntu    5516  0.0  0.0  20208   944 ?        S    09:50   0:02 syndaemon -i 2.
ubuntu    5520  0.0  0.7 1033076 29468 ?       Sl   09:50   0:01 nautilus -n
ubuntu    5521  0.0  0.6 808656 27364 ?        Sl   09:50   0:03 nm-applet
ubuntu    5522  0.0  0.2 313044  9172 ?        Sl   09:50   0:00 /usr/lib/policy
ubuntu    5525  0.0  0.3 513056 12892 ?        Sl   09:50   0:00 bluetooth-apple
ubuntu    5526  0.0  0.2 460604  9620 ?        Sl   09:50   0:00 /usr/lib/gnome-
ubuntu    5536  0.0  0.1 214064  5928 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
root      5543  0.0  0.1 344056  5424 ?        Sl   09:50   0:00 /usr/lib/udisks
ubuntu    5559  0.0  0.0 203408  3216 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
ubuntu    5563  0.0  0.0 287460  3232 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
ubuntu    5568  0.0  0.0 276180  3736 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
ubuntu    5578  0.0  0.0 115520  2612 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
ubuntu    5582  0.0  0.3 429856 12300 ?        Sl   09:50   0:00 /usr/lib/bamf/b
ubuntu    5587  0.0  0.3 369068 14924 ?        Sl   09:50   0:00 /usr/lib/notify
ubuntu    5591  0.0  0.0 263128  2628 ?        Sl   09:50   0:00 /usr/lib/gvfs/g
ubuntu    5595  0.0  0.2 322344 10860 ?        Sl   09:50   0:00 /usr/bin/gnome-
ubuntu    5599  0.0  0.0   4396   616 ?        Ss   09:50   0:00 /bin/sh -c /usr
ubuntu    5600  0.0  0.2 313396 11308 ?        Sl   09:50   0:00 /usr/bin/gtk-wi
ubuntu    5612  0.0  0.5 536752 20872 ?        Sl   09:50   0:03 /usr/lib/unity/
ubuntu    5614  0.0  0.1 357604  5192 ?        Sl   09:50   0:03 /usr/lib/indica
ubuntu    5623  0.0  0.1 565840  5192 ?        Sl   09:50   0:00 /usr/lib/x86_64
ubuntu    5625  0.0  0.2 594820  9908 ?        Sl   09:50   0:00 /usr/lib/indica
ubuntu    5628  0.0  0.1 435432  4960 ?        Sl   09:50   0:00 /usr/lib/indica
ubuntu    5630  0.0  0.1 505672  5384 ?        Sl   09:50   0:00 /usr/lib/indica
ubuntu    5634  0.0  0.1 537088  6884 ?        Sl   09:50   0:00 /usr/lib/indica
ubuntu    5639  0.0  0.2 429204 10732 ?        Sl   09:50   0:00 /usr/lib/indica
ubuntu    5662  0.0  0.1 363104  6996 ?        Sl   09:50   0:00 /usr/lib/evolut
ubuntu    5671  0.0  0.1 238736  5336 ?        Sl   09:50   0:00 /usr/lib/geoclu
ubuntu    5683  0.0  0.1 319492  6500 ?        Sl   09:50   0:00 /usr/lib/ubuntu
ubuntu    5692  0.0  0.2 435204 11760 ?        Sl   09:50   0:00 telepathy-indic
ubuntu    5698  0.0  0.1 330408  7384 ?        Sl   09:50   0:00 /usr/lib/telepa
ubuntu    5704  0.0  0.6 449436 25416 ?        Sl   09:50   0:00 /usr/bin/signon
ubuntu    5707  0.0  0.1 415660  5200 ?        Sl   09:50   0:00 zeitgeist-datah
ubuntu    5713  0.0  0.1 346040  4664 ?        Sl   09:50   0:00 /usr/bin/zeitge
ubuntu    5719  0.0  0.2 243532  9104 ?        Sl   09:50   0:00 /usr/lib/zeitge
ubuntu    5728  0.0  0.0  11372   360 ?        S    09:50   0:00 /bin/cat
root      5731  0.0  0.0      0     0 ?        S    09:50   0:00 [kworker/0:2]
ubuntu    5742  0.0  0.2 415484 11256 ?        Sl   09:51   0:00 /usr/lib/unity-
ubuntu    5744  0.0  0.1 747936  6668 ?        Sl   09:51   0:00 /usr/lib/unity-
ubuntu    5746  0.0  0.1 828312  6796 ?        Sl   09:51   0:00 /usr/lib/gwibbe
ubuntu    5749  0.0  0.6 973020 25916 ?        Sl   09:51   0:00 /usr/bin/python
ubuntu    5751  0.0  0.2 849316  9844 ?        Sl   09:51   0:00 /usr/lib/x86_64
ubuntu    5752  0.0  0.2 672944  8168 ?        Sl   09:51   0:00 /usr/lib/x86_64
ubuntu    5754  0.0  0.5 645664 21672 ?        Sl   09:51   0:00 /usr/bin/python
ubuntu    5823  0.0  0.4 531008 19240 ?        Sl   09:51   0:00 /usr/bin/python
ubuntu    5825  0.0  0.1 673220  5104 ?        Sl   09:51   0:00 /usr/lib/x86_64
ubuntu    5841  0.0  0.4 618292 18804 ?        Sl   09:51   0:00 /usr/bin/python
root      5866  0.0  0.0  24420   604 ?        S    09:51   0:00 dbus-launch --a
root      5867  0.0  0.0  23808   936 ?        Ss   09:51   0:00 //bin/dbus-daem
ubuntu    6510  0.0  0.3 403220 13232 ?        Sl   09:51   0:00 update-notifier
root      7205  0.0  0.0      0     0 ?        S<   09:51   0:00 [xfsalloc]
root      7206  0.0  0.0      0     0 ?        S<   09:51   0:00 [xfs_mru_cache]
root      7209  0.0  0.0      0     0 ?        S<   09:51   0:00 [xfslogd]
root      7212  0.0  0.0      0     0 ?        S    09:51   0:00 [jfsIO]
root      7213  0.0  0.0      0     0 ?        S    09:51   0:00 [jfsCommit]
root      7214  0.0  0.0      0     0 ?        S    09:51   0:00 [jfsCommit]
root      7215  0.0  0.0      0     0 ?        S    09:51   0:00 [jfsCommit]
root      7216  0.0  0.0      0     0 ?        S    09:51   0:00 [jfsCommit]
root      7217  0.0  0.0      0     0 ?        S    09:51   0:00 [jfsSync]
ubuntu   13015  0.0  0.1 372300  4192 ?        Sl   09:52   0:00 /usr/lib/x86_64
ubuntu   13019  0.0  0.5 117932 21024 ?        S    09:52   0:00 /usr/bin/python
ubuntu   13029  0.0  0.5 123512 20964 ?        S    09:52   0:00 /usr/bin/python
root     13389  0.0  0.0  10184  3712 ?        S    09:52   0:00 /sbin/dhclient 
nobody   13393  0.0  0.0  33072  1552 ?        S    09:52   0:00 /usr/sbin/dnsma
root     13608  0.0  0.0  21768  1240 ?        S    09:53   0:00 /sbin/udevd --d
root     13988  0.0  0.0      0     0 ?        S    10:31   0:00 [kworker/2:1]
ubuntu   13998  5.9  2.9 863568 117740 ?       Sl   10:47   0:42 /usr/lib/firefo
ubuntu   14014  0.0  0.0 267268  3032 ?        Sl   10:47   0:00 /usr/lib/libuni
root     14046  0.0  0.0      0     0 ?        S    10:49   0:00 [kworker/3:1]
root     14054  0.0  0.0      0     0 ?        S    10:52   0:00 [kworker/1:0]
root     14061  0.0  0.0      0     0 ?        S    10:54   0:00 [kworker/u:0]
root     14063  0.0  0.0      0     0 ?        S    10:55   0:00 [kworker/3:0]
root     14064  0.0  0.0      0     0 ?        S    10:58   0:00 [kworker/1:1]
root     14071  0.0  0.0      0     0 ?        S    10:58   0:00 [flush-8:0]
root     14095  0.0  0.0  22424  1436 ?        S    10:58   0:00 /sbin/udevd --d
ubuntu   14111  0.0  0.0   4396   612 ?        Ss   10:58   0:00 /bin/sh -c gnom
ubuntu   14112  9.0  0.4 529928 17700 ?        Sl   10:58   0:00 gnome-terminal
ubuntu   14116  0.0  0.0  14788   824 ?        S    10:58   0:00 gnome-pty-helpe
ubuntu   14117  1.5  0.0  26016  2988 pts/1    Ss   10:58   0:00 bash
ubuntu   14168  0.0  0.0  22600  1312 pts/1    R+   10:58   0:00 ps aux

---

