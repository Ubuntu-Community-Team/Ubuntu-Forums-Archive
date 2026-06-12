---
title: "update manager stalled"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by yuler on 2010-12-04
Newbie running 10.10.  Ran update manager, selected only critical updates.  Download successful.  Applying changes  stalled.

```

Selecting previously deselected package linux-image-2.6.35.23-generic.
(Reading database ... 120668 files and directories currently installed.)
Unpacking linux-image-2.6.35.23-generic (from ... /linux-image-2.6.35.23-generic_2.6.35-23.41_i386.deb) ...
Done.

```Loaded System Monitor.  Most apps sleeping.
Seached forums for "update manager".  A solution?

```

yuler@masterblaster:~$ sudo apt-get upgrade
[sudo] password for yuler: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```Searched forums more, saw thread with error response.  
Bug?  Maybe.
Remove file?  No.  
Reboot?  Possibly, but what if it doesn't come back?  
Kill process?  Possibly.
List processes.  

```

yuler@masterblaster:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2880  1552 ?        Ss   12:03   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    12:03   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    12:03   0:01 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    12:03   0:00 [migration/0]
root         5  0.0  0.0      0     0 ?        S    12:03   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    12:03   0:01 [events/0]
root         7  0.0  0.0      0     0 ?        S    12:03   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    12:03   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    12:03   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    12:03   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    12:03   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    12:03   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    12:03   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    12:03   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    12:03   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    12:03   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    12:03   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    12:03   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    12:03   0:00 [ata_aux]
root        20  0.0  0.0      0     0 ?        S    12:03   0:01 [ata_sff/0]
root        21  0.0  0.0      0     0 ?        S    12:03   0:00 [khubd]
root        22  0.0  0.0      0     0 ?        S    12:03   0:00 [kseriod]
root        23  0.0  0.0      0     0 ?        S    12:03   0:00 [kmmcd]
root        25  0.0  0.0      0     0 ?        S    12:03   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S    12:03   0:00 [kswapd0]
root        27  0.0  0.0      0     0 ?        SN   12:03   0:00 [ksmd]
root        28  0.0  0.0      0     0 ?        S    12:03   0:00 [aio/0]
root        29  0.0  0.0      0     0 ?        S    12:03   0:00 [ecryptfs-kthr]
root        30  0.0  0.0      0     0 ?        S    12:03   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    12:03   0:00 [kstriped]
root        37  0.0  0.0      0     0 ?        S    12:03   0:00 [kmpathd/0]
root        38  0.0  0.0      0     0 ?        S    12:03   0:00 [kmpath_handle]
root        39  0.0  0.0      0     0 ?        S    12:03   0:00 [ksnapd]
root        40  0.0  0.0      0     0 ?        S    12:03   0:00 [kondemand/0]
root        41  0.0  0.0      0     0 ?        S    12:03   0:00 [kconservative]
root       202  0.0  0.0      0     0 ?        S    12:04   0:00 [scsi_eh_0]
root       222  0.0  0.0      0     0 ?        S    12:04   0:00 [scsi_eh_1]
root       231  0.0  0.0      0     0 ?        S    12:04   0:00 [scsi_eh_2]
root       232  0.0  0.0      0     0 ?        S    12:04   0:01 [scsi_eh_3]
root       259  0.0  0.0      0     0 ?        S    12:04   0:00 [jbd2/sda5-8]
root       260  0.0  0.0      0     0 ?        S    12:04   0:00 [ext4-dio-unwr]
root       293  0.0  0.0      0     0 ?        S    12:04   0:00 [flush-8:0]
root       321  0.0  0.0   2396   672 ?        S    12:04   0:00 upstart-udev-br
root       324  0.0  0.0   2628   504 ?        S<s  12:04   0:00 udevd --daemon
root       531  0.0  0.0      0     0 ?        S    12:04   0:00 [kpsmoused]
root       706  0.0  0.0      0     0 ?        S    12:04   0:00 [kgameportd]
syslog     737  0.0  0.0  34596   904 ?        Sl   12:04   0:00 rsyslogd -c4
102        754  0.0  0.1   3588  1696 ?        Ss   12:04   0:02 dbus-daemon --s
root       767  0.0  0.3  19624  3640 ?        Ssl  12:04   0:01 NetworkManager
avahi      770  0.0  0.1   3016  1240 ?        S    12:04   0:00 avahi-daemon: r
avahi      774  0.0  0.0   3016   168 ?        S    12:04   0:00 avahi-daemon: c
root       775  0.0  0.1   4432  1780 ?        S    12:04   0:00 /usr/sbin/modem
root       804  0.0  0.1   4904  1928 ?        S    12:04   0:00 /sbin/wpa_suppl
root       829  0.0  0.0   1860   448 tty4     Ss+  12:04   0:00 /sbin/getty -8
root       835  0.0  0.0   1860   452 tty5     Ss+  12:04   0:00 /sbin/getty -8
root       843  0.0  0.0   1860   452 tty2     Ss+  12:04   0:00 /sbin/getty -8
root       845  0.0  0.0   1860   452 tty3     Ss+  12:04   0:00 /sbin/getty -8
root       849  0.0  0.0   1860   452 tty6     Ss+  12:04   0:00 /sbin/getty -8
root       850  0.0  0.0   2116   464 ?        Ss   12:04   0:00 acpid -c /etc/a
root       857  0.0  0.0   2460   728 ?        Ss   12:04   0:00 cron
daemon     858  0.0  0.0   2320   220 ?        Ss   12:04   0:00 atd
root       970  0.0  0.2  19852  2792 ?        Ssl  12:04   0:00 gdm-binary
root       976  0.0  0.2  19984  2272 ?        Sl   12:04   0:00 /usr/sbin/conso
root      1045  0.0  0.1   6792  1056 ?        Ss   12:04   0:00 /usr/sbin/cupsd
root      1047  0.0  0.2  21540  2728 ?        Sl   12:04   0:00 /usr/lib/gdm/gd
root      1062  2.4  4.7  73284 49164 tty7     Ss+  12:04   7:36 /usr/bin/X :0 -
root      1089  0.0  0.0   1860   532 tty1     Ss+  12:04   0:00 /sbin/getty -8
root      1104  0.0  0.2  19868  2716 ?        Sl   12:04   0:00 /usr/lib/gdm/gd
yuler    1113  0.0  0.6  34800  6408 ?        Ssl  12:04   0:00 gnome-session
yuler    1143  0.0  0.0   3352   200 ?        Ss   12:04   0:00 /usr/bin/ssh-ag
yuler    1146  0.0  0.0   3460   520 ?        S    12:04   0:00 /usr/bin/dbus-l
yuler    1147  0.0  0.2   4808  2088 ?        Ss   12:04   0:01 /bin/dbus-daemo
yuler    1152  0.0  0.4   9296  4204 ?        S    12:04   0:02 /usr/lib/libgco
yuler    1158  0.0  0.6  28512  6864 ?        Sl   12:04   0:00 gnome-power-man
yuler    1159  0.0  0.6  45056  6364 ?        SLl  12:04   0:00 /usr/bin/gnome-
yuler    1163  0.0  0.9  99216  9548 ?        Ssl  12:04   0:04 /usr/lib/gnome-
root      1167  0.0  0.2   8404  2880 ?        S    12:04   0:00 /usr/lib/upower
yuler    1172  0.0  0.2   7552  2344 ?        S    12:04   0:00 /usr/lib/gvfs/g
yuler    1186  0.0  0.2  30764  2204 ?        Ssl  12:04   0:00 /usr/lib/gvfs//
yuler    1193  0.0  0.7  38564  7920 ?        Sl   12:04   0:00 /usr/lib/evolut
yuler    1201  0.0  1.2 115656 12308 ?        SLl  12:04   0:02 nm-applet --sm-
yuler    1203  1.2  3.7  64080 38376 ?        Sl   12:04   4:00 /usr/bin/compiz
yuler    1204  0.0  1.4  77612 15208 ?        Sl   12:04   0:07 gnome-panel
yuler    1208  0.2  2.8 132704 29024 ?        Sl   12:04   0:41 nautilus
yuler    1212  0.0  1.1  72728 11836 ?        Sl   12:04   0:00 /usr/lib/policy
yuler    1213  0.4  0.3  95672  3996 ?        S<sl 12:04   1:27 /usr/bin/pulsea
root      1214  0.0  0.4   9084  4232 ?        S    12:04   0:00 /usr/lib/policy
rtkit     1219  0.0  0.1  22996  1128 ?        SNl  12:04   0:00 /usr/lib/rtkit/
yuler    1292  0.0  0.2  20684  2968 ?        Sl   12:04   0:00 /usr/lib/pulsea
yuler    1296  0.0  0.2   8000  3068 ?        S    12:04   0:00 /usr/lib/gvfs/g
yuler    1301  0.0  0.3  50528  3168 ?        Ssl  12:04   0:00 /usr/lib/bonobo
yuler    1304  0.0  0.3  33508  3588 ?        S    12:04   0:00 /usr/lib/gvfs/g
root      1307  0.0  0.3  16428  3392 ?        Sl   12:04   0:00 /usr/lib/udisks
root      1308  0.0  0.0   5616   708 ?        S    12:04   0:02 udisks-daemon: 
yuler    1316  0.0  1.2  75372 12820 ?        Sl   12:04   0:13 /usr/lib/gnome-
yuler    1317  0.0  1.0  74992 10392 ?        Sl   12:04   0:00 /usr/lib/gnome-
yuler    1326  0.0  0.2  18000  2152 ?        Sl   12:04   0:00 /usr/lib/gvfs/g
yuler    1329  0.0  0.2   8192  2268 ?        S    12:04   0:00 /usr/lib/gvfs/g
yuler    1345  0.0  0.0   1900   420 ?        Ss   12:04   0:00 /bin/sh -c /usr
yuler    1346  0.0  1.1  72652 11744 ?        Sl   12:04   0:03 /usr/bin/gtk-wi
yuler    1357  0.0  1.1  83564 12160 ?        Sl   12:04   0:01 /usr/lib/indica
yuler    1358  0.0  1.6  92224 16764 ?        Sl   12:04   0:07 /usr/lib/gnome-
yuler    1359  0.0  1.0  82824 11256 ?        Sl   12:04   0:00 /usr/lib/indica
yuler    1360  0.0  0.7  31096  7716 ?        Sl   12:04   0:00 /usr/lib/gnome-
yuler    1362  0.0  0.2   7452  2272 ?        S    12:04   0:00 /usr/lib/gvfs/g
yuler    1382  0.0  0.5  26948  5640 ?        Ss   12:04   0:01 gnome-screensav
yuler    1388  0.0  0.1   7332  1996 ?        S    12:04   0:00 /usr/lib/gvfs/g
yuler    1390  0.0  0.4  18208  4320 ?        S    12:04   0:00 /usr/lib/indica
yuler    1393  0.0  0.3  15720  3440 ?        S    12:04   0:00 /usr/lib/indica
yuler    1394  0.0  0.5  87508  5156 ?        S    12:04   0:00 /usr/lib/indica
yuler    1397  0.0  0.4  27060  5060 ?        Sl   12:04   0:00 /usr/lib/indica
yuler    1400  0.0  0.4  27996  5100 ?        Sl   12:04   0:00 /usr/lib/indica
yuler    1417  0.0  0.6  19236  6240 ?        S    12:04   0:00 /usr/lib/gnome-
yuler    1419  0.0  0.0   1900   428 ?        S    12:04   0:00 /bin/sh /usr/li
yuler    1423  0.0  0.0   1900   428 ?        S    12:04   0:00 /bin/sh /usr/li
yuler    1427  5.0 14.8 501228 152520 ?       Sl   12:04  15:59 /usr/lib/firefo
yuler    1447  0.0  1.3  32432 13524 ?        S    12:04   0:00 /usr/bin/python
yuler    1453  0.0  1.0  71912 10880 ?        Sl   12:05   0:03 update-notifier
root      1462  0.0  0.6  13940  6520 ?        S    12:05   0:00 /usr/bin/python
yuler    1464  0.3  4.8 132380 49832 ?        SNl  12:05   1:13 /usr/bin/python
root      1640  0.0  0.0      0     0 ?        S    12:14   0:00 [cfg80211]
root      1643  0.0  0.0      0     0 ?        S    12:14   0:01 [zd1211rw]
root      1644  0.0  0.0      0     0 ?        S    12:14   0:02 [phy0]
yuler    1698  0.0  1.0  71600 10700 ?        Sl   12:14   0:02 /usr/lib/notify
yuler    2066  0.0  1.8  33516 18652 ?        S    12:52   0:00 /usr/bin/python
yuler    2294  0.0  0.2  16100  2936 ?        S    13:11   0:00 /usr/lib/gvfs/g
root      2331  0.0  0.0   2300   996 ?        S    13:57   0:00 /sbin/dhclient
root      2544  0.0  0.0      0     0 ?        S    15:29   0:00 [scsi_eh_5]
root      2571  0.0  0.1   3168  1316 ?        Ss   15:30   0:00 /sbin/mount.ntf
yuler    2780  0.0  0.4  28424  4960 ?        Sl   15:48   0:00 /usr/lib/gvfs/g
root      2785  0.0  0.6  11536  6864 ?        S    15:48   0:00 /usr/bin/python
root      2863  0.0  0.0   2624   480 ?        S<   16:06   0:00 udevd --daemon
root      2864  0.0  0.0   2624   476 ?        S<   16:06   0:00 udevd --daemon
root      2959  0.1  3.2  50204 33560 ?        Sl   16:42   0:04 /usr/bin/python
yuler    2979  0.0  0.8  47676  8696 ?        Sl   16:48   0:00 /usr/lib/evolut
yuler    2986  0.0  0.8  54516  8700 ?        Sl   16:48   0:00 /usr/lib/evolut
yuler    3004  0.0  0.3   7476  3544 ?        SL   16:49   0:00 /usr/lib/telepa
yuler    3026  0.0  2.0  65860 20924 ?        Sl   16:49   0:00 /usr/bin/python
yuler    3036  0.0  1.0  49468 10412 ?        S    16:49   0:00 /usr/bin/python
root      3047  0.0  1.6  40208 17328 pts/2    Ss+  16:52   0:00 /usr/bin/python
root      3090  0.1  2.3  27816 24456 pts/3    Ds+  16:52   0:01 /usr/bin/dpkg -
yuler    3113  0.0  0.0      0     0 ?        ZN   16:53   0:00 [deb] <defunct>
yuler    3171  0.2  1.3  90064 13596 ?        Sl   17:15   0:00 gnome-terminal
yuler    3174  0.0  0.0   2056   692 ?        S    17:15   0:00 gnome-pty-helpe
yuler    3175  0.1  0.3   6520  3156 pts/4    Ss   17:15   0:00 bash
yuler    3213  0.0  0.1   4592  1072 pts/4    R+   17:18   0:00 ps aux

```This is where I'm stuck.  Advice?

---

### Post by Quackers on 2010-12-04
Did you use Update Manager? Is the window still open?

---

### Post by yuler on 2010-12-04
Yes and yes.

---

### Post by Quackers on 2010-12-04
Well, I'm sure it's of no consolation to you whatsoever, but I just ran Update Manager and it crashed my whole system so badly it took 2 REISUB's to get it back! 
But I'm on a test version of Natty Narwhal so you shouldn't be experiencing anything like that!
Are all other functions usable normally on your system?
Is your update manager window usable? Can you cancel for instance?

---

### Post by yuler on 2010-12-04
You are correct - that is of no consolation to me.  :)

I do not know what a REISUB is.

All other functions are usable except the update manager - I cannot cancel it.  The secondary window of update manager, "Applying changes", is spinning it's wheel.  This is what it says (relisted here):

```

Selecting previously deselected package linux-image-2.6.35.23-generic.
(Reading database ... 120668 files and directories currently installed.)
Unpacking linux-image-2.6.35.23-generic (from ... /linux-image-2.6.35.23-generic_2.6.35-23.41_i386.deb) ...
Done.
```

---

### Post by Quackers on 2010-12-04
I see :-) didn't think so!
If the wheel is spinning it doesn't look so good.
It looks like it finished what it was doing, but has not continued to the end.
I have no suggestion for stopping it. Maybe somebody else can suggest something.

In order to force a reboot on a machine that has completely locked up (rather than pressing the power button) it is more tidy (and safer) to press and hold the ctrl + alt + Sys Rq (or Prt Sc) buttons and in turn press R E I S U B keys one at a time. You need three hands really, but it is just about manageable.

---

### Post by yuler on 2010-12-05
9 keys, 10 fingers, spread across 101 keys?  I can see how that'd be a challenge.

Well, the update manager has not changed in 3 hours.  I assume it's broken, but am concerned about the outcome of a system shutdown - hard, if necessary.  I'd rather try to fix it while it is still up.

---

### Post by yuler on 2010-12-05
System > admin > monitor > update-manager, update-notifier > end process

Ran update-manager again and it complained last update was incomplete, but gave me an option to partial update.  Chose that, then it downloaded 63mb more updates, reboot, got 2 more GRUB entries - linux kernel 2.6.23 and recovery.  

Seems to work.  Not sure why update manager stalled to begin with.

---

### Post by Quackers on 2010-12-05
I'm glad you got it sorted out :-)
Strange things happen sometimes.

---

