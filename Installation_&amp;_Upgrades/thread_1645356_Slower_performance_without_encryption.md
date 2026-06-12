---
title: "Slower performance without encryption?"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by bryceowen on 2010-12-14
I had previously installed Lucid on my system using the alternate install CD so I could create an encrypted install to run along a TrueCrypt encrypted Windows install. (I was experimenting with various encryption methods and their impact on system performance.) Despite the lack of swap space on the Ubuntu install, I was pleased with the performance.

After finishing my experimentation, I decided to reinstall Lucid using the normal desktop install CD. This is where performance is poor. All I did was install the system then run the update manager and now this thing is running more sluggishly than it did when it had to deal with the encryption and no swap!

My question, I suppose, is what could be happening here to drag the system down?

Here's a list of all currently running programs (courtesy of ps aux):
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2784  1696 ?        Ss   11:28   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    11:28   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    11:28   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    11:28   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    11:28   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    11:28   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S    11:28   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S    11:28   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S    11:28   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S    11:28   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S    11:28   0:00 [pm]
root        12  0.0  0.0      0     0 ?        S    11:28   0:00 [sync_supers]
root        13  0.0  0.0      0     0 ?        S    11:28   0:00 [bdi-default]
root        14  0.0  0.0      0     0 ?        S    11:28   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S    11:28   0:00 [kblockd/0]
root        16  0.0  0.0      0     0 ?        S    11:28   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        S    11:28   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        S    11:28   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        S    11:28   0:02 [ata/0]
root        20  0.0  0.0      0     0 ?        S    11:28   0:00 [ata_aux]
root        21  0.0  0.0      0     0 ?        S    11:28   0:00 [ksuspend_usbd]
root        22  0.0  0.0      0     0 ?        S    11:28   0:00 [khubd]
root        23  0.0  0.0      0     0 ?        S    11:28   0:00 [kseriod]
root        24  0.0  0.0      0     0 ?        S    11:28   0:00 [kmmcd]
root        27  0.0  0.0      0     0 ?        S    11:28   0:00 [khungtaskd]
root        28  0.0  0.0      0     0 ?        S    11:28   0:01 [kswapd0]
root        29  0.0  0.0      0     0 ?        SN   11:28   0:00 [ksmd]
root        30  0.0  0.0      0     0 ?        S    11:28   0:00 [aio/0]
root        31  0.0  0.0      0     0 ?        S    11:28   0:00 [ecryptfs-kthrea]
root        32  0.0  0.0      0     0 ?        S    11:28   0:00 [crypto/0]
root        36  0.0  0.0      0     0 ?        S    11:28   0:00 [scsi_eh_0]
root        37  0.0  0.0      0     0 ?        S    11:28   0:06 [scsi_eh_1]
root        39  0.0  0.0      0     0 ?        S    11:28   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S    11:28   0:00 [scsi_eh_3]
root        44  0.0  0.0      0     0 ?        S    11:28   0:00 [kstriped]
root        45  0.0  0.0      0     0 ?        S    11:28   0:00 [kmpathd/0]
root        46  0.0  0.0      0     0 ?        S    11:28   0:00 [kmpath_handlerd]
root        47  0.0  0.0      0     0 ?        S    11:28   0:00 [ksnapd]
root        48  0.0  0.0      0     0 ?        S    11:28   0:00 [kondemand/0]
root        49  0.0  0.0      0     0 ?        S    11:28   0:00 [kconservative/0]
root       181  0.0  0.0      0     0 ?        S    11:28   0:00 [usbhid_resumer]
root       184  0.0  0.0      0     0 ?        S    11:28   0:00 [i915]
root       228  0.0  0.0      0     0 ?        S    11:28   0:00 [jbd2/sda5-8]
root       229  0.0  0.0      0     0 ?        S    11:28   0:00 [ext4-dio-unwrit]
root       259  0.0  0.0      0     0 ?        S    11:28   0:00 [flush-8:0]
root       289  0.0  0.0   2316   860 ?        S    11:28   0:00 upstart-udev-bridge --daemon
root       293  0.0  0.0   2656   964 ?        S<s  11:28   0:00 udevd --daemon
root       399  0.0  0.0   2652   928 ?        S<   11:28   0:00 udevd --daemon
root       400  0.0  0.0   2652   928 ?        S<   11:28   0:00 udevd --daemon
root       495  0.0  0.0      0     0 ?        S    11:28   0:00 [kpsmoused]
root       598  0.0  0.0      0     0 ?        S    11:28   0:00 [jbd2/sda2-8]
root       599  0.0  0.0      0     0 ?        S    11:28   0:00 [ext4-dio-unwrit]
syslog     642  0.0  0.1  33516  1472 ?        Sl   11:28   0:00 rsyslogd -c4
root       644  0.0  0.0      0     0 ?        S<   11:28   0:00 [kslowd000]
root       645  0.0  0.0      0     0 ?        S<   11:28   0:00 [kslowd001]
102        657  0.0  0.1   3244  1600 ?        Ss   11:29   0:01 dbus-daemon --system --fork
root       674  0.0  0.3  18780  3236 ?        Ssl  11:29   0:00 gdm-binary
avahi      684  0.0  0.1   2928  1496 ?        S    11:29   0:00 avahi-daemon: running [tmsaws.local]
avahi      685  0.0  0.0   2928   544 ?        Ss   11:29   0:00 avahi-daemon: chroot helper
root       697  0.0  0.0   5552   904 ?        Ss   11:29   0:00 /usr/sbin/sshd
root       718  0.0  0.3   8740  3836 ?        Ss   11:29   0:00 NetworkManager
root       720  0.0  0.2   4168  2268 ?        S    11:29   0:00 /usr/sbin/modem-manager
root       722  0.0  0.0   1792   560 tty4     Ss+  11:29   0:00 /sbin/getty -8 38400 tty4
root       728  0.0  0.0   1792   564 tty5     Ss+  11:29   0:00 /sbin/getty -8 38400 tty5
root       734  0.0  0.3  19672  3244 ?        Sl   11:29   0:00 /usr/sbin/console-kit-daemon --no-daemon
root       737  0.0  0.2   5628  2532 tty2     Ss   11:29   0:00 /bin/login --        
root       738  0.0  0.0   1792   568 tty3     Ss+  11:29   0:00 /sbin/getty -8 38400 tty3
root       740  0.0  0.0   1792   564 tty6     Ss+  11:29   0:00 /sbin/getty -8 38400 tty6
daemon     747  0.0  0.0   2248   436 ?        Ss   11:29   0:00 atd
root       748  0.0  0.0   2376   888 ?        Ss   11:29   0:00 cron
root       749  0.0  0.0   2048   864 ?        Ss   11:29   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       822  0.0  0.1   4836  1712 ?        S    11:29   0:00 /sbin/wpa_supplicant -u -s
root       826  0.0  0.3  20500  3728 ?        Sl   11:29   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root       857  1.7  1.9  40724 20456 tty7     Rs+  11:29   2:33 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-VU8sto/database -nolisten tcp vt7
root       886  0.0  0.1  11736  1388 ?        Ss   11:29   0:00 /usr/sbin/winbindd
root       912  0.0  0.1  11736  1164 ?        S    11:29   0:00 /usr/sbin/winbindd
root       927  0.0  0.0      0     0 ?        S    11:29   0:00 [cifsd]
root       938  0.0  0.2   6700  2520 ?        Ss   11:29   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
gdm       1063  0.0  0.0   3384   752 ?        S    11:29   0:00 /usr/bin/dbus-launch --exit-with-session
root      1078  0.0  0.3  21004  3684 ?        Sl   11:30   0:00 /usr/lib/gdm/gdm-session-worker
root      1082  0.0  0.2   5512  2744 ?        S    11:30   0:00 /usr/lib/upower/upowerd
root      1091  0.0  0.3   6324  3860 ?        S    11:30   0:00 /usr/lib/policykit-1/polkitd
rtkit     1115  0.0  0.1  22908  1188 ?        SNl  11:30   0:00 /usr/lib/rtkit/rtkit-daemon
108       1120  0.0  0.4  16836  4376 ?        Ssl  11:30   0:00 /usr/sbin/hald
root      1121  0.0  0.1   3532  1264 ?        S    11:30   0:00 hald-runner
root      1147  0.0  0.1   3608  1224 ?        S    11:30   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event0 /dev/input/event1
root      1161  0.0  0.1   3612  1212 ?        S    11:30   0:04 hald-addon-storage: polling /dev/sr0 (every 2 sec)
108       1163  0.0  0.1   3420  1152 ?        S    11:30   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
(username)   1189  0.0  0.2  23984  2560 ?        Sl   11:30   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
(username)   1207  0.0  0.6  25896  6608 ?        Ssl  11:30   0:00 gnome-session
(username)   1247  0.0  0.0   3284   356 ?        Ss   11:30   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
(username)   1250  0.0  0.0   3384   744 ?        S    11:30   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
(username)   1251  0.0  0.1   3060  1336 ?        Ss   11:30   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
(username)   1254  0.0  0.4   7544  4228 ?        S    11:30   0:01 /usr/lib/libgconf2-4/gconfd-2
(username)   1260  0.0  1.0  89744 10312 ?        Ss   11:30   0:02 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
(username)   1263  0.0  0.2   6380  2260 ?        S    11:30   0:00 /usr/lib/gvfs/gvfsd
(username)   1268  0.0  0.2  30280  2592 ?        Ssl  11:30   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/(username)/.gvfs
(username)   1272  0.0  1.1  35112 11684 ?        S    11:30   0:08 metacity
(username)   1275  0.0  0.4  94304  4584 ?        S<sl 11:30   0:00 /usr/bin/pulseaudio --start --log-target=syslog
(username)   1278  0.0  0.5  18432  5996 ?        S    11:30   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
(username)   1279  0.0  1.0  48748 10996 ?        S    11:30   0:00 nm-applet --sm-disable
(username)   1281  0.0  0.7  19656  7448 ?        S    11:30   0:00 gnome-power-manager
(username)   1282  0.0  0.7  18996  7296 ?        S    11:30   0:00 bluetooth-applet
(username)   1283  0.0  1.4  40756 14848 ?        S    11:30   0:03 gnome-panel
(username)   1284  0.0  0.2  10752  2972 ?        S    11:30   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
(username)   1286  0.0  1.8  62872 18536 ?        S    11:30   0:02 nautilus
(username)   1292  0.0  0.3   7780  3248 ?        S    11:31   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1294  0.0  0.2  15676  3040 ?        Sl   11:31   0:00 /usr/lib/udisks/udisks-daemon
root      1295  0.0  0.0   5180   852 ?        S    11:31   0:01 udisks-daemon: polling /dev/sr0
(username)   1298  0.0  0.2  16956  2324 ?        Sl   11:31   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
(username)   1299  0.0  0.6  18720  7012 ?        Ss   11:31   0:00 gnome-screensaver
(username)   1302  0.0  0.2   7128  2340 ?        S    11:31   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
(username)   1305  0.0  0.6  18528  6812 ?        S    11:31   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
(username)   1311  0.0  0.3  40896  3464 ?        Ssl  11:31   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=19
(username)   1313  0.0  0.2   6808  2968 ?        S    11:31   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
(username)   1319  0.0  1.2  38712 12676 ?        S    11:31   0:02 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=18
(username)   1321  0.0  1.0  37440 10704 ?        S    11:31   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=24
(username)   1331  0.0  1.4  53360 15364 ?        S    11:31   0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=19
(username)   1332  0.0  1.1  46740 12220 ?        S    11:31   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=28
(username)   1333  0.0  0.8  22608  8320 ?        S    11:31   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Factory --oaf-ior-fd=34
(username)   1338  0.0  1.0  34612 10920 ?        Sl   11:31   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
(username)   1341  0.0  1.4  31500 15144 ?        S    11:31   0:00 python /usr/share/system-config-printer/applet.py
(username)   1351  0.0  0.1   6248  1948 ?        S    11:31   0:00 /usr/lib/gvfs/gvfsd-metadata
(username)   1354  0.0  0.2   6380  2352 ?        S    11:31   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
(username)   1358  0.0  0.4  24304  4248 ?        S    11:31   0:00 /usr/lib/indicator-application/indicator-application-service
(username)   1360  0.0  0.4  85080  4528 ?        S    11:31   0:00 /usr/lib/indicator-sound/indicator-sound-service
(username)   1372  2.0  2.8  49904 29172 ?        SLl  11:31   2:55 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
(username)   1379  0.0  1.0  34988 11264 ?        S    11:31   0:04 update-notifier
(username)   1411  0.0  1.1  35160 11708 ?        S    11:35   0:00 tsclient
(username)   1412  0.0  0.3  13028  3340 ?        S    11:36   0:03 rdesktop -T'192.168.1.165 - Terminal Server Client' -u(username) -g1152x864 -rsound:off -rclipboard:PRIMARYCLIPBOARD -rdisk:Local / -5 192.168.1.165
root      1474  0.0  0.7  13688  8012 ?        S    11:57   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
(username)   1674  0.0  0.3   6040  3380 tty2     S    12:01   0:00 -bash
(username)   1699  0.0  0.3   6024  3360 tty2     S+   12:01   0:02 ssh (private).no-ip.org -2 -l (username) -p (port)
(username)   1705  0.0  0.0   1832   528 ?        S    12:01   0:00 /bin/sh /usr/lib/firefox-3.6.13/firefox
(username)   1710  0.0  0.0   1832   544 ?        S    12:01   0:00 /bin/sh /usr/lib/firefox-3.6.13/run-mozilla.sh /usr/lib/firefox-3.6.13/firefox-bin
(username)   1714  5.3  7.2 344328 74352 ?        Sl   12:01   6:07 /usr/lib/firefox-3.6.13/firefox-bin
(username)   2239  1.3  2.1  88644 21700 ?        Sl   12:29   1:11 /usr/lib/firefox-3.6.13/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so 1714 plugin true
root      2357  0.0  0.0   1792   564 tty1     Ss+  13:49   0:00 /sbin/getty -8 38400 tty1
(username)   2386  2.7  1.2  44808 12348 ?        Sl   13:55   0:01 gnome-terminal
(username)   2387  0.0  0.0   1988   704 ?        S    13:55   0:00 gnome-pty-helper
(username)   2388  1.0  0.3   6012  3348 pts/0    Ss   13:55   0:00 bash
(username)   2409  0.0  0.1   2716  1040 pts/0    R+   13:56   0:00 ps aux
```
It takes almost a whole minute to boot, whereas before it would come up in under 30 seconds.

---

