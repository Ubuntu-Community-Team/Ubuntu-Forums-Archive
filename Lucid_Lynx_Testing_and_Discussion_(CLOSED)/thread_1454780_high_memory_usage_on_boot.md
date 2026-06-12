---
title: "high memory usage on boot"
date: 2010-04-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yoavg on 2010-04-15
Hi,
(I know about cached disk entries and ureadahead, I don't think that's the issue)

I am run 64bit Lucid on a Macbook (4,1), 4gb ram (upgraded from Karmic).

Just after logging in to the gnome session, I get:

```
free -m
```

```

             total       used       free     shared    buffers     cached
Mem:          3930       1861       2068          0        226        853
-/+ buffers/cache:        781       3148
Swap:        11513          0      11513

```

and:

```
 ps aux | awk '{sum +=$4}; END {print sum}'

```

```

11.8

```


So ps is seeing about 400m of memory usage.  I am still missing about 400.

This is after booting the machine 3 times without logging in, so I do not think it's the ureadahead issue.

---

### Post by Kenda on 2010-04-17
I think I have noticed something strange with memory usage as well (64bit). 

Sometimes when I restart and log in the memory usage with no other programs running is 1.5 MiG if I immediately restart and try again it will be about 500 MiB.

It seems to be that every alternate log in has extra high memory usage.

I don't see anything in system monitor or top which would explain either figure although I am using fglrx.

Lucid in VirtualBox uses far less memory.

---

### Post by vinx on 2010-04-17
There's really something wrong. Here's with everything closed (of 2GB):
ps aux: 24%
free: 36%
Besides something seems to be missing, I think that's huge! 500MB of programs when there are mostly small programs (using around 0.1%).

With Firefox started:
ps aux: 38%
free: 50%

Starting up Chrome, Gwibber and a big image in Gimp:
ps aux: 91%
free: 86%

Closing everything except Firefox:
ps aux: 37%
free: 45%

Ok, there probably is something with Swap, but why sometimes less and sometimes more? Rounding? I certainly know that when I start 2 browsers (with lots of tabs open) my machine gets less responsive due to IOWait (swapping). I never had problems with memory before (previous 9.10-32, now 10.04-64). Is it the 64bit?

---

### Post by Götz on 2010-04-18
Using Lucid (KDE) I have the same problem, not on boot, but over the time, the swap gets used more and more. Today it went to 1.4 GB (1.5 GB RAM) and all the system becomes very slow. It is not an app like Firefox or so, the one that uses more memory when I close everything is Xorg, using ~30 MB, but the swap is still full. If I do: "sudo swapoff -a" I can see in htop that the swap begins to empty, but then the process (swapoff) dies (i says: Process killed), and the swap fills up again. 

I tried removing ureadahead but It is the same. Also testing with the Karmic kernel 2.6.31-20 I have the same problem. I don't know which program is the cause. I think it has to be something important or so (memory manager, but is that not the kernel?), because it doesn't appear in htop nor ps.

I think that this thread from nearly one month is about the same problem [http://ubuntuforums.org/showthread.php?t=1430763](http://ubuntuforums.org/showthread.php?t=1430763)

Maybe these bugs are related: 
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)
[https://bugs.launchpad.net/ubuntu/+bug/560859](https://bugs.launchpad.net/ubuntu/+bug/560859)

---

### Post by Longinus00 on 2010-04-19
If your memory consumption is high after an upgrade and rebooting lowers it then you're probably hit buy this bug. [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

If memory consumption is not related to upgrading your computer then that's not the right bug.

---

### Post by Götz on 2010-04-19
I don't think that the bug 501715 is the cause of my problem. 
As I sad, uninstalling ureadahead doesn't solve the problem (It should solve it, isn't it?)

---

### Post by rockmanz on 2010-04-19
I think I have the same problem (Kubuntu with 2gb ram) except that my ps finds 45.8 while free mem says 
>              total       used       free     shared    buffers     cached
Mem:          2009       1179        830          0         30        358
-/+ buffers/cache:        789       1220
Swap:         1906          0       1906

Still this is only with chromium open. On cold boot it uses 600mb and disabling X still results in 380mb of used ram (at this point ps aux finds 2.0).

---

### Post by rifak on 2010-04-19
this is also happening with me. it SEEMS to be random, but not sure. after some restarts, ill be using 500-600 mb of ram with no programs running, when other restarts will show 180 mb. i usually just do another restart after this happening and it will go back down. running 32bit lucid on macbook.

---

### Post by hurdevan on 2010-04-20
This is haunting me too.
I'm running a Ubuntu Lucid(32 Bit) on a IBM Thinkpad T42 with 1GB ram. Previous versions of Ubuntu I had to actually TRY to use anything more then 500MB of ram. But now it just slowly climes its way up there. Right now it I am using 850 MB of ram with just Firefox, Gedit, Gnome-do and Rhythmbox. Also, there are some smaller applets process running in the background.

Actually the circumstances have changed since I updated yesterday. Now it appears that the X server is using about 270 MB of ram which is not right. Previously I could not find much of a reason why my system was consuming so much ram and it bothered me so much. 

When if Run: ps aux
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2796  1272 ?        Ss   14:45   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    14:45   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    14:45   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    14:45   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    14:45   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    14:45   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    14:45   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    14:45   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    14:45   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    14:45   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    14:45   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    14:45   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    14:45   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    14:45   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    14:45   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    14:45   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    14:45   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    14:45   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    14:45   0:06 [ata/0]
root        20  0.0  0.0      0     0 ?        S    14:45   0:00 [ata_aux]
root        21  0.0  0.0      0     0 ?        S    14:45   0:00 [ksuspend_usbd]
root        22  0.0  0.0      0     0 ?        S    14:45   0:00 [khubd]
root        23  0.0  0.0      0     0 ?        S    14:45   0:00 [kseriod]
root        24  0.0  0.0      0     0 ?        S    14:45   0:00 [kmmcd]
root        27  0.0  0.0      0     0 ?        S    14:45   0:00 [khungtaskd]
root        28  0.0  0.0      0     0 ?        S    14:45   0:01 [kswapd0]
root        29  0.0  0.0      0     0 ?        SN   14:45   0:00 [ksmd]
root        30  0.0  0.0      0     0 ?        S    14:45   0:00 [aio/0]
root        31  0.0  0.0      0     0 ?        S    14:45   0:00 [ecryptfs-kthrea]
root        32  0.0  0.0      0     0 ?        S    14:45   0:00 [crypto/0]
root        38  0.0  0.0      0     0 ?        S    14:45   0:00 [scsi_eh_0]
root        40  0.0  0.0      0     0 ?        S    14:45   0:11 [scsi_eh_1]
root        42  0.0  0.0      0     0 ?        S    14:45   0:00 [kstriped]
root        43  0.0  0.0      0     0 ?        S    14:45   0:00 [kmpathd/0]
root        44  0.0  0.0      0     0 ?        S    14:45   0:00 [kmpath_handlerd]
root        45  0.0  0.0      0     0 ?        S    14:45   0:00 [ksnapd]
root        46  0.0  0.0      0     0 ?        S    14:45   0:00 [kondemand/0]
root        47  0.0  0.0      0     0 ?        S    14:45   0:00 [kconservative/0]
root       237  0.0  0.0      0     0 ?        S    14:45   0:00 [jbd2/sda1-8]
root       238  0.0  0.0      0     0 ?        S    14:45   0:00 [ext4-dio-unwrit]
root       271  0.0  0.0      0     0 ?        S    14:45   0:00 [flush-8:0]
root       298  0.0  0.0   2312   568 ?        S    14:45   0:00 upstart-udev-bridge --daemon
root       300  0.0  0.0   2616   252 ?        S<s  14:45   0:00 udevd --daemon
root       469  0.0  0.0      0     0 ?        S    14:45   0:00 [kpsmoused]
root       563  0.0  0.0      0     0 ?        S    14:45   0:00 [ktpacpid]
root       615  0.0  0.0      0     0 ?        S    14:45   0:00 [pccardd]
root       616  0.0  0.0      0     0 ?        S    14:45   0:00 [ipw2200/0]
root       627  0.0  0.0      0     0 ?        S    14:45   0:00 [radeon/0]
root       628  0.0  0.0      0     0 ?        S    14:45   0:00 [ttm_swap]
root       630  0.0  0.0   2648   236 ?        S<   14:45   0:00 udevd --daemon
root       634  0.0  0.0   2648   236 ?        S<   14:45   0:00 udevd --daemon
syslog     656  0.0  0.1  33508  1100 ?        Sl   14:45   0:00 rsyslogd -c4
102        668  0.0  0.1   3308  1432 ?        Ss   14:45   0:02 dbus-daemon --system --fork
root       682  0.0  0.2  18428  2704 ?        Ssl  14:45   0:00 gdm-binary
root       689  0.0  0.2  18548  2788 ?        Ssl  14:45   0:06 NetworkManager
avahi      693  0.0  0.1   3040  1368 ?        S    14:45   0:00 avahi-daemon: running [evan-laptop.local]
avahi      695  0.0  0.0   2924   304 ?        Ss   14:45   0:00 avahi-daemon: chroot helper
root       706  0.0  0.1   4164  1756 ?        S    14:45   0:00 /usr/sbin/modem-manager
root       719  0.0  0.2  19672  2436 ?        Sl   14:45   0:00 /usr/sbin/console-kit-daemon --no-daemon
root       723  0.0  0.1   4824  1564 ?        S    14:45   0:00 /sbin/wpa_supplicant -u -s
root       794  0.0  0.2  20492  2552 ?        Sl   14:45   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root       801  0.0  0.0      0     0 ?        S    14:45   0:00 [pccardd]
root       836  0.0  0.0   1788   456 tty4     Ss+  14:45   0:00 /sbin/getty -8 38400 tty4
root       841  0.0  0.0   1788   460 tty5     Ss+  14:45   0:00 /sbin/getty -8 38400 tty5
root       849  0.0  0.0   1788   460 tty2     Ss+  14:45   0:00 /sbin/getty -8 38400 tty2
root       852  0.0  0.0   1788   460 tty3     Ss+  14:45   0:00 /sbin/getty -8 38400 tty3
root       856  0.0  0.0   1788   460 tty6     Ss+  14:45   0:00 /sbin/getty -8 38400 tty6
root       860  0.0  0.1   2308  1136 ?        Ss   14:45   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       863  3.8 26.4 310908 271096 tty7    Ss+  14:45  14:53 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-ZfrQBa/database -nolisten tcp vt7
root       865  0.0  0.0   2372   760 ?        Ss   14:45   0:00 cron
daemon     866  0.0  0.0   2244   304 ?        Ss   14:45   0:00 atd
clamav     979  0.0  0.0  12064   940 ?        Ss   14:45   0:00 /usr/bin/freshclam -d --quiet
root      1073  0.0  0.0   6824   964 ?        Ss   14:45   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1124  0.0  0.1  11460  1804 ?        S    14:45   0:07 python /usr/sbin/tpfand --quiet
109       1128  0.0  0.1  16776  2028 ?        Ssl  14:45   0:00 /usr/sbin/hald
root      1130  0.0  0.1   3528  1048 ?        S    14:45   0:00 hald-runner
gdm       1135  0.0  0.0   3380   476 ?        S    14:45   0:00 /usr/bin/dbus-launch --exit-with-session
root      1227  0.0  0.0   3600   976 ?        S    14:45   0:00 /usr/lib/hal/hald-addon-ipw-killswitch
root      1228  0.0  0.1   3604  1144 ?        S    14:45   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/event4 /dev/input/event1 /dev/input/event5 /dev/input/event2 /dev/input/event0
root      1235  0.0  0.0   3604   980 ?        S    14:45   0:00 /usr/lib/hal/hald-addon-leds
root      1237  0.0  0.0   3600  1012 ?        S    14:45   0:00 /usr/lib/hal/hald-addon-generic-backlight
root      1249  0.0  0.1   3608  1048 ?        S    14:45   0:09 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1252  0.0  0.0   3616   976 ?        S    14:45   0:00 /usr/lib/hal/hald-addon-cpufreq
109       1255  0.0  0.1   3416  1040 ?        S    14:45   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1262  0.0  0.0   1788   460 tty1     Ss+  14:45   0:00 /sbin/getty -8 38400 tty1
root      1274  0.0  0.2  18872  2100 ?        Sl   14:45   0:00 /usr/lib/gdm/gdm-session-worker
root      1276  0.0  0.2   5492  2268 ?        S    14:45   0:00 /usr/lib/upower/upowerd
root      1281  0.0  0.3   6168  3132 ?        S    14:45   0:00 /usr/lib/policykit-1/polkitd
evan      1330  0.0  0.1  23980  1652 ?        Sl   14:46   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
evan      1348  0.0  0.5  25892  5676 ?        Ssl  14:46   0:00 gnome-session
evan      1382  0.0  0.0   3280   148 ?        Ss   14:46   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
evan      1385  0.0  0.0   3380   476 ?        S    14:46   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
evan      1386  0.1  0.1   3420  1472 ?        Ss   14:46   0:25 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
evan      1389  0.0  0.3   7852  3872 ?        S    14:46   0:11 /usr/lib/libgconf2-4/gconfd-2
evan      1396  0.0  1.0 180088 11188 ?        Ssl  14:46   0:08 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
evan      1398  0.0  0.2   6508  2156 ?        S    14:46   0:00 /usr/lib/gvfs/gvfsd
evan      1403  0.0  0.2  30200  2120 ?        Ssl  14:46   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/evan/.gvfs
evan      1416  3.3  0.6 168548  6408 ?        S<sl 14:46  13:06 /usr/bin/pulseaudio --start --log-target=syslog
rtkit     1418  0.0  0.0  22904   948 ?        SNl  14:46   0:00 /usr/lib/rtkit/rtkit-daemon
evan      1419  0.0  0.0   1828   368 ?        S    14:46   0:00 /bin/sh /usr/bin/gnome-do
evan      1423  0.0  1.7 123812 17620 ?        Sl   14:46   0:20 gnome-panel
evan      1429  0.0  2.0 171208 21060 ?        Sl   14:46   0:17 nautilus
evan      1430  0.2  3.3 168856 34500 ?        Sl   14:46   1:08 /usr/bin/cli /usr/lib/gnome-do/Do.exe
evan      1434  0.0  0.8  52668  8832 ?        S    14:46   0:01 nm-applet --sm-disable
evan      1439  0.0  0.4  18424  4644 ?        S    14:46   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
evan      1440  0.0  0.7  95924  7408 ?        Sl   14:46   0:00 gnome-power-manager
evan      1442  0.0  0.2  10748  2244 ?        S    14:46   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
evan      1475  0.0  0.2   7736  2792 ?        S    14:46   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1477  0.0  0.2  15640  2580 ?        Sl   14:46   0:00 /usr/lib/udisks/udisks-daemon
root      1478  0.0  0.0   5176   680 ?        S    14:46   0:07 udisks-daemon: polling /dev/sr0
evan      1480  0.0  0.1  16948  1936 ?        Sl   14:46   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
evan      1484  0.0  0.1   7124  1896 ?        S    14:46   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
root      1485  0.0  0.0   2228   740 ?        S    14:46   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth1.pid -lf /var/lib/dhcp3/dhclient-f99fd48e-7ed1-4d19-9d6b-6940331aefcc-eth1.lease -cf /var/run/nm-dhclient-eth1.conf eth1
evan      1490  0.0  0.2   6728  2596 ?        S    14:46   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
evan      1492  0.0  0.2  41008  3004 ?        Ssl  14:46   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
evan      1493  0.0  0.5  17952  5380 ?        Ss   14:46   0:01 gnome-screensaver
evan      1518  0.0  0.0   1828   356 ?        Ss   14:46   0:00 /bin/sh -c /usr/bin/compiz-decorator
evan      1519  0.0  0.9  96160  9592 ?        Sl   14:46   0:03 /usr/bin/gtk-window-decorator
evan      1521  0.0  0.5  18304  5680 ?        S    14:46   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
proxy     1531  0.0  0.0   2220   304 ?        Ss   14:46   0:00 /usr/bin/polipo -c /etc/polipo/config pidFile=/var/run/polipo/polipo.pid daemonise=true logFile=/var/log/polipo/polipo.log forbiddenFile=/etc/polipo/forbidden proxyOffline=false
evan      1551  0.0  0.1   6376  1920 ?        S    14:46   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
evan      1588  0.0  1.3 118296 14136 ?        Sl   14:46   0:08 /usr/lib/talika/talika --oaf-activate-iid=OAFIID:TalikaApplet_Factory --oaf-ior-fd=18
evan      1589  0.0  1.5 122008 16176 ?        Sl   14:46   0:09 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID:GNOME_StickyNotesApplet_Factory --oaf-ior-fd=30
evan      1590  0.0  0.7  41260  7988 ?        S    14:46   0:21 /usr/lib/alarm-clock-applet/alarm-clock-applet --oaf-activate-iid=OAFIID:AlarmClock_Factory --oaf-ior-fd=36
evan      1592  0.0  1.1 125600 11552 ?        Sl   14:46   0:19 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=48
evan      1593  0.0  0.6  22724  6680 ?        S    14:46   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=54
evan      1594  0.0  1.0 126120 11040 ?        Sl   14:46   0:01 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=60
evan      1595  0.0  1.0 107956 11052 ?        Sl   14:46   0:02 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=66
evan      1629  0.0  0.2   9420  2588 ?        S    14:46   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
evan      1672  0.0  0.1   6392  1924 ?        S    14:46   0:00 /usr/lib/gvfs/gvfsd-metadata
evan      1674  0.0  0.3  17908  3920 ?        S    14:46   0:00 /usr/lib/indicator-session/indicator-session-service
evan      1682  0.0  0.3  18756  3864 ?        S    14:46   0:00 /usr/lib/indicator-me/indicator-me-service
evan      1687  0.0  0.3  24084  3556 ?        S    14:46   0:00 /usr/lib/indicator-application/indicator-application-service
evan      1689  0.0  0.3  17428  3500 ?        S    14:46   0:00 /usr/lib/indicator-messages/indicator-messages-service
evan      1691  0.0  0.3  85072  3724 ?        S    14:46   0:00 /usr/lib/indicator-sound/indicator-sound-service
evan      1695  0.0  0.6  31480  7172 ?        S    14:46   0:14 python /usr/share/system-config-printer/applet.py
evan      1768  0.0  0.1   3848  1544 ?        S    14:47   0:00 /usr/lib/xfconfd
root      1826  0.0  0.5  11440  5944 ?        S    14:56   0:00 /usr/bin/python /usr/share/apt-xapian-index/update-apt-xapian-index-dbus
evan      1867  6.3  5.7 382232 59140 ?        Sl   15:02  23:35 rhythmbox
evan      1921  0.1  2.0 136620 21052 ?        Sl   15:03   0:36 gedit
evan      1932  0.0  1.1  37880 11756 ?        S    15:05   0:12 /usr/lib/notify-osd/notify-osd
evan      2566  0.0  0.3  19128  3832 ?        S    15:23   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.6 /org/gtk/gvfs/exec_spaw/2
evan      5994  0.0  0.0   1828   448 ?        S    18:51   0:00 /bin/sh /usr/lib/firefox-3.6.3/firefox
evan      5999  0.0  0.0   1828   464 ?        S    18:51   0:00 /bin/sh /usr/lib/firefox-3.6.3/run-mozilla.sh /usr/lib/firefox-3.6.3/firefox-bin
evan      6003  5.1  9.5 506492 97524 ?        Sl   18:51   7:27 /usr/lib/firefox-3.6.3/firefox-bin
evan      7549  0.1  1.0  95960 10584 ?        Sl   20:43   0:02 metacity --replace
evan      7650  0.1  1.3 123384 13528 ?        Sl   20:55   0:01 gnome-terminal
evan      7652  0.0  0.0   1984   704 ?        S    20:55   0:00 gnome-pty-helper
evan      7653  0.0  0.3   6600  3952 pts/0    Ss   20:55   0:00 bash
evan      7674 12.7  2.0 121548 20896 ?        Sl   20:55   2:28 gnome-system-monitor
evan      7763  0.0  0.1   2712  1044 pts/0    R+   21:15   0:00 ps aux
[/QUOTE]
 

free -m
> 
             total       used       free     shared    buffers     cached
Mem:          1001        972         29          0         15        103
-/+ buffers/cache:        853        148
Swap:         1608         79       1528

```

And then, from the first person who posted, the sum of mem% usage from ps aux:  ps aux | awk '{sum +=$4}; END {print sum}'
[QUOTE]78.1

And finely, not sure if its relevant, but I can't seam to get my harddrive to spin down when the computer is idle.

Additionally, when my ram does max out then my computer will get real slow. After the the computer has been idle for a while then I guess it starts bumping programs into the swap because it will fill about 400 MB there. Also, after a idle and the system filling the swap then the computer will get almost unresponsive when comping back to it and programs will sometimes fail to load.

---

