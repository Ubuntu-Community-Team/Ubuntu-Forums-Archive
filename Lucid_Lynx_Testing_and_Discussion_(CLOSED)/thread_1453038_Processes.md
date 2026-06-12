---
title: "Processes"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Paradox Uncreated on 2010-04-12
Is there a detalied description of processes running when booted into Lucid Lynx, somewhere?

---

### Post by tajreed on 2010-04-12
system/admin/system monitor

---

### Post by Paradox Uncreated on 2010-04-13
root         1  0.0  0.0  23700  1804 ?        SNs  Apr12   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ksoftirqd/1]
root         5  0.0  0.0      0     0 ?        SN   Apr12   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        SN   Apr12   0:00 [events/1]
root         7  0.0  0.0      0     0 ?        SN   Apr12   0:00 [khelper]
root         8  0.0  0.0      0     0 ?        SN   Apr12   0:00 [async/mgr]
root         9  0.0  0.0      0     0 ?        SN   Apr12   0:00 [pm]
root        10  0.0  0.0      0     0 ?        SN   Apr12   0:00 [sync_supers]
root        11  0.0  0.0      0     0 ?        SN   Apr12   0:00 [bdi-default]
root        12  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kintegrityd/0]
root        13  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kintegrityd/1]
root        14  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kblockd/0]
root        15  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kblockd/1]
root        16  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        SN   Apr12   0:04 [ata/0]
root        20  0.0  0.0      0     0 ?        SN   Apr12   0:04 [ata/1]
root        21  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ata_aux]
root        22  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ksuspend_usbd]
root        23  0.0  0.0      0     0 ?        SN   Apr12   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kseriod]
root        25  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kswapd0]
root        29  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ksmd]
root        30  0.0  0.0      0     0 ?        SN   Apr12   0:00 [aio/0]
root        31  0.0  0.0      0     0 ?        SN   Apr12   0:00 [aio/1]
root        32  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ecryptfs-kthrea]
root        33  0.0  0.0      0     0 ?        SN   Apr12   0:00 [crypto/0]
root        34  0.0  0.0      0     0 ?        SN   Apr12   0:00 [crypto/1]
root        38  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kstriped]
root        39  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kmpathd/0]
root        40  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kmpathd/1]
root        41  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kmpath_handlerd]
root        42  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ksnapd]
root       226  0.0  0.0      0     0 ?        SN   Apr12   0:14 [scsi_eh_0]
root       249  0.0  0.0      0     0 ?        SN   Apr12   0:00 [scsi_eh_1]
root       252  0.0  0.0      0     0 ?        SN   Apr12   0:00 [khpsbpkt]
root       253  0.0  0.0      0     0 ?        SN   Apr12   0:00 [scsi_eh_2]
root       254  0.0  0.0      0     0 ?        SN   Apr12   0:00 [scsi_eh_3]
root       259  0.0  0.0      0     0 ?        SN   Apr12   0:00 [scsi_eh_4]
root       260  0.0  0.0      0     0 ?        SN   Apr12   0:02 [usb-storage]
root       278  0.0  0.0      0     0 ?        SN   Apr12   0:00 [knodemgrd_0]
root       298  0.0  0.0      0     0 ?        SN   Apr12   0:00 [usbhid_resumer]
root       308  0.0  0.0      0     0 ?        SN   Apr12   0:00 [jbd2/sdb8-8]
root       309  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ext4-dio-unwrit]
root       310  0.0  0.0      0     0 ?        SN   Apr12   0:00 [ext4-dio-unwrit]
root       319  0.0  0.0      0     0 ?        SN   Apr12   0:00 [scsi_eh_5]
root       320  0.0  0.0      0     0 ?        SN   Apr12   0:01 [usb-storage]
root       354  0.0  0.0  17028   752 ?        SN   Apr12   0:00 upstart-udev-bridge --daemon
root       364  0.0  0.0  17612   324 ?        SNs  Apr12   0:00 udevd --daemon
root       477  0.0  0.0      0     0 ?        SN   Apr12   0:00 [flush-8:16]
root       594  0.0  0.0  17476   316 ?        SN   Apr12   0:00 udevd --daemon
root       597  0.0  0.0  17608   316 ?        SN   Apr12   0:00 udevd --daemon
root       698  0.0  0.0      0     0 ?        SN   Apr12   0:00 [kpsmoused]
syslog     778  0.0  0.0 111608  1304 ?        SNl  Apr12   0:00 rsyslogd -c4
root       895  0.0  0.0      0     0 ?        SN   Apr12   0:00 [hd-audio0]
root       945  0.0  0.0   6072   548 tty4     SNs+ Apr12   0:00 /sbin/getty -8 38400 tty4
root       949  0.0  0.0   6072   548 tty5     SNs+ Apr12   0:00 /sbin/getty -8 38400 tty5
root       957  0.0  0.0   6072   548 tty2     SNs+ Apr12   0:00 /sbin/getty -8 38400 tty2
root       958  0.0  0.0   6072   548 tty3     SNs+ Apr12   0:00 /sbin/getty -8 38400 tty3
root       960  0.0  0.0   6072   548 tty6     SNs+ Apr12   0:00 /sbin/getty -8 38400 tty6
root       962  0.0  0.0   4420   568 ?        SNs  Apr12   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon     977  0.0  0.0  18876   304 ?        SNs  Apr12   0:00 atd
root       978  0.0  0.0  21068   848 ?        SNs  Apr12   0:00 cron
kernoops   991  0.0  0.0  22312   868 ?        SNs  Apr12   0:01 /usr/sbin/kerneloops
102        993  0.0  0.0  24364  1696 ?        SNs  Apr12   0:00 dbus-daemon --system --fork
avahi     1020  0.0  0.0  33920  1368 ?        SN   Apr12   0:00 avahi-daemon: running [Millennium.local]
avahi     1021  0.0  0.0  33920   312 ?        SNs  Apr12   0:00 avahi-daemon: chroot helper
root      1022  0.0  0.0  85508  3564 ?        SNsl Apr12   0:00 NetworkManager
root      1023  0.0  0.0  65796  1004 ?        SNs  Apr12   0:00 /usr/sbin/winbindd
root      1027  0.0  0.0  57856  2184 ?        SN   Apr12   0:00 /usr/sbin/modem-manager
root      1048  0.0  0.0  75300  2508 ?        SNs  Apr12   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1051  0.0  0.0  28344  1724 ?        SN   Apr12   0:00 /sbin/wpa_supplicant -u -s
root      1052  0.0  0.0  65796   748 ?        SN   Apr12   0:00 /usr/sbin/winbindd
root      1053  0.0  0.0   6548  1024 ?        SN   Apr12   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action
timidity  1182  0.0  0.0 102976  2488 ?        SN   Apr12   0:00 /usr/bin/timidity -Os -iAD
root      1185  0.0  0.0   6072   548 tty1     SNs+ Apr12   0:00 /sbin/getty -8 38400 tty1
root      1241  0.0  0.0  74488  3124 ?        SNsl Apr12   0:07 gdm-binary
root      1247  0.0  0.0 120540  2800 ?        SNl  Apr12   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1312  0.0  0.0  91508  3312 ?        SNl  Apr12   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManage
root      1315  2.0  1.1 154272 47976 tty7     SNs+ Apr12  17:37 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-upI9zN/d
gdm       1335  0.0  0.0  26252   516 ?        SN   Apr12   0:00 /usr/bin/dbus-launch --exit-with-session
root      1353  0.0  0.0 101772  2872 ?        SNl  Apr12   0:00 /usr/lib/gdm/gdm-session-worker
root      1355  0.0  0.0  53560  2604 ?        SN   Apr12   0:00 /usr/lib/upower/upowerd
root      1365  0.0  0.0  54040  3580 ?        SN   Apr12   0:00 /usr/lib/policykit-1/polkitd
109       1397  0.0  0.1  44808  4668 ?        SNsl Apr12   0:00 /usr/sbin/hald
root      1398  0.0  0.0  22308  1140 ?        SN   Apr12   0:00 hald-runner
root      1422  0.0  0.0  24428  1156 ?        SN   Apr12   0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event0 
root      1433  0.0  0.0  24424  1168 ?        SN   Apr12   0:01 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      1434  0.0  0.0  24424  1172 ?        SN   Apr12   0:10 hald-addon-storage: polling /dev/sr0 (every 2 sec)
109       1452  0.0  0.0  26260  1040 ?        SN   Apr12   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
uwaysi    1462  0.0  0.0  69688  2448 ?        SNl  Apr12   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
root      1473  0.0  0.0  24424  1164 ?        SN   Apr12   0:01 hald-addon-storage: polling /dev/sdd (every 2 sec)
uwaysi    1491  0.0  0.1 169648  6860 ?        SNsl Apr12   0:00 gnome-session
uwaysi    1525  0.0  0.0  11928   144 ?        SNs  Apr12   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-s
uwaysi    1528  0.0  0.0  26252   508 ?        SN   Apr12   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
uwaysi    1529  0.0  0.0  24340  1604 ?        SNs  Apr12   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
uwaysi    1532  0.0  0.0  46276  3988 ?        SN   Apr12   0:03 /usr/lib/libgconf2-4/gconfd-2
uwaysi    1538  0.0  0.2 312224  9456 ?        SNs  Apr12   0:16 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
uwaysi    1541  0.0  0.0  48064  2380 ?        SN   Apr12   0:00 /usr/lib/gvfs/gvfsd
uwaysi    1546  0.0  0.0 151884  2204 ?        SNsl Apr12   0:03 /usr/lib/gvfs//gvfs-fuse-daemon /home/uwaysi/.gvfs
uwaysi    1551  0.0  0.3 208784 13868 ?        SN   Apr12   0:09 metacity --sm-client-id 10f2fba2c3067bd6e12701364329894320000001296
uwaysi    1554  0.0  0.3 235636 12328 ?        SN   Apr12   0:00 nm-applet --sm-disable
uwaysi    1555  0.0  0.1 175808  7620 ?        SN   Apr12   0:00 gnome-power-manager
uwaysi    1556  0.0  0.2 168948  8644 ?        SN   Apr12   0:00 bluetooth-applet
uwaysi    1557  0.0  0.1 164080  6348 ?        SN   Apr12   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
uwaysi    1558  0.0  0.7 578148 30420 ?        SN   Apr12   0:31 nautilus --sm-client-id 10f2fba2c3067bd6e12701364332113000000129600
uwaysi    1559  0.0  0.5 270920 23220 ?        SN   Apr12   0:24 gnome-panel --sm-client-id 10f2fba2c3067bd6e12701364329897200000001
uwaysi    1561  0.0  0.4 313148 19488 ?        RNl  Apr12   0:05 gnome-terminal --sm-client-id 10f2fba2c3067bd6e12701365181621370000
uwaysi    1569  0.0  0.0  14480   816 ?        SN   Apr12   0:00 gnome-pty-helper
uwaysi    1570  0.0  0.1  22088  4904 pts/0    SNs+ Apr12   0:00 bash
uwaysi    1575  0.0  0.1  22088  4896 pts/1    SNs  Apr12   0:00 bash
uwaysi    1591  0.0  0.1 154272  4176 ?        SN   Apr12   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1599  0.0  0.0  63900  3856 ?        SNl  Apr12   0:01 /usr/lib/udisks/udisks-daemon
uwaysi    1607  0.0  0.0  52544  3196 ?        SN   Apr12   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
root      1608  0.0  0.0  46684  1080 ?        SN   Apr12   0:08 udisks-daemon: polling /dev/sdd /dev/sdc /dev/sr0
uwaysi    1610  0.0  0.0  55240  2664 ?        SN   Apr12   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
uwaysi    1612  0.0  0.0  69204  2720 ?        SNl  Apr12   0:01 /usr/lib/gvfs/gvfs-afc-volume-monitor
uwaysi    1614  0.0  0.1 152996  4280 ?        SNsl Apr12   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate -
uwaysi    1628  0.0  0.4 265016 17108 ?        SN   Apr12   0:15 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wn
uwaysi    1630  0.0  0.3 239636 12696 ?        SN   Apr12   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_
uwaysi    1635  0.0  0.3 305984 15992 ?        SN   Apr12   0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_C
uwaysi    1636  0.0  0.3 335572 15212 ?        SN   Apr12   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFII
uwaysi    1638  0.0  0.4 265288 17004 ?        SN   Apr12   0:03 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID
uwaysi    1641  0.0  0.2 208016 10240 ?        SN   Apr12   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OA
uwaysi    1642  0.3  0.2 227148 10992 ?        SN   Apr12   2:59 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID
uwaysi    1644  0.0  0.3 268120 15324 ?        SN   Apr12   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-i
uwaysi    1650  0.0  0.0  41792  2444 ?        SN   Apr12   0:00 /usr/lib/gvfs/gvfsd-metadata
uwaysi    1654  0.0  0.1 144004  5712 ?        SN   Apr12   0:10 /usr/lib/indicator-me/indicator-me-service
uwaysi    1658  0.0  0.1 173768  6200 ?        SNs  Apr12   0:00 gnome-screensaver
uwaysi    1661  0.0  0.1 140940  5564 ?        SN   Apr12   0:00 /usr/lib/indicator-session/indicator-session-service
uwaysi    1665  0.0  0.1 138576  5116 ?        SN   Apr12   0:00 /usr/lib/indicator-messages/indicator-messages-service
uwaysi    1667  0.0  0.1 219012  5428 ?        SN   Apr12   0:00 /usr/lib/indicator-sound/indicator-sound-service
uwaysi    1669  0.0  0.1 146872  4876 ?        SN   Apr12   0:00 /usr/lib/indicator-application/indicator-application-service
uwaysi    1671  0.0  0.0  48064  2656 ?        SN   Apr12   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
uwaysi    1689  0.0  0.2 176500  8176 ?        SN   Apr12   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
uwaysi    1693  0.0  0.5 231312 20968 ?        SN   Apr12   0:00 python /usr/share/system-config-printer/applet.py
uwaysi    1694  0.0  0.3 432132 13916 ?        SNl  Apr12   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
uwaysi    1701  0.0  0.3 429236 13864 ?        SNl  Apr12   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-i
uwaysi    1706  0.0  0.2 448108 10656 ?        SNl  Apr12   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OA
uwaysi    1740  0.0  0.3 204536 13772 ?        SN   Apr12   0:01 update-notifier
root      1744  0.0  0.2  78736 10724 ?        SN   Apr12   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root      1809  0.0  0.0  26252   816 pts/1    SN   Apr12   0:00 dbus-launch --autolaunch 629a5e63cdfb582da23685cc4bb128d1 --binary-
root      1810  0.0  0.0  23416   844 ?        SNs  Apr12   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
uwaysi    1884  0.0  0.1  22088  4908 pts/2    SNs+ Apr12   0:00 bash
uwaysi    1902  0.0  0.1 135516  4804 pts/2    SNl  Apr12   0:35 ffado-dbus-server
uwaysi    1949  8.1  4.1 168288 167884 ?       SNLl Apr12  71:12 /home/uwaysi/Installed/rns_2_5_1_reg/renoise
uwaysi    2036  3.2  4.6 370948 189000 ?       S<Lsl Apr12  28:49 /usr/bin/pulseaudio --start --log-target=syslog
uwaysi    2039  0.0  0.0  96640  3524 ?        S    Apr12   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
uwaysi    2084  0.5  0.5 313216 21988 ?        SN   Apr12   4:44 pavucontrol
uwaysi    2249  0.0  0.5 338804 23780 ?        SN   Apr12   0:18 gedit
uwaysi    2539  0.0  0.0      0     0 ?        ZN   Apr12   0:00 [renoise] <defunct>
uwaysi    2563  0.0  0.0   4088   616 pts/2    SN   Apr12   0:00 /bin/sh /usr/bin/qjackctl
uwaysi    2571  0.0  0.0 126376  2384 pts/2    SN   Apr12   0:00 /usr/bin/pasuspender -- /usr/bin/qjackctl.bin
uwaysi    2572  0.5  3.1 453548 126376 pts/2   SNLl Apr12   4:35 /usr/bin/qjackctl.bin
uwaysi    2848  0.0  0.1 167508  7552 ?        SN   Apr12   0:00 /usr/lib/notify-osd/notify-osd
root      3823  0.0  0.0  15516  1384 ?        SNs  01:08   0:03 /sbin/mount.ntfs /dev/sda5 /media/Production -o rw,nosuid,nodev,uhe
root      3844  0.2  0.0  16288  2188 ?        SNs  01:08   1:29 /sbin/mount.ntfs /dev/sda6 /media/Entertainment -o rw,nosuid,nodev,
uwaysi    4069  0.8  0.2  12224  9576 ?        SNs  01:13   5:26 /usr/bin/wineserver
uwaysi    4073  0.0  0.0 2642584 2612 ?        SNl  01:13   0:00 C:\windows\system32\services.exe                                  
uwaysi    4075  0.0  0.1 2648736 6020 ?        SNl  01:13   0:00 C:\windows\system32\winedevice.exe MountMgr                       
uwaysi    4083  0.0  0.1 2652680 6960 ?        SNs  01:13   0:03 C:\windows\system32\explorer.exe /desktop                         
uwaysi    4500  1.4  6.5 2721888 267904 ?      SNLsl 01:55   9:03 Z:\media\Entertainment\games\steam\Steam.exe                     
uwaysi    4701  5.1  2.6 158304 106048 ?       SNLsl 02:04  31:15 /usr/bin/jackd -R -t5000 -dfirewire -r44100 -p64 -n3
uwaysi    5489  0.0  0.0   4088   624 ?        SN   11:55   0:00 /bin/sh /usr/lib/firefox-3.6.3/firefox
uwaysi    5494  0.0  0.0   4088   652 ?        SN   11:55   0:00 /bin/sh /usr/lib/firefox-3.6.3/run-mozilla.sh /usr/lib/firefox-3.6.
uwaysi    5498 20.2  3.8 867700 156688 ?       SNl  11:55   2:46 /usr/lib/firefox-3.6.3/firefox-bin
uwaysi    5550  0.0  0.0   9980  1100 pts/1    TN   12:07   0:00 less
uwaysi    5560  0.0  0.0  15248  1204 pts/1    RN+  12:08   0:00 ps aux



Now, what I am wondering, is most of these processes casual processes, so that I can renice them without that affecting audiovisual performance?

For instance, I want to renice all processes that do not affect audiovisual performance, to 14.

---

### Post by Paradox Uncreated on 2010-04-13
Wait, I did a reboot, so that lots of processes aren't running.

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0  23688  1900 ?        SNs  12:30   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        SN   12:30   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        SN   12:30   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        SN   12:30   0:00 [ksoftirqd/1]
root         5  0.0  0.0      0     0 ?        SN   12:30   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        SN   12:30   0:00 [events/1]
root         7  0.0  0.0      0     0 ?        SN   12:30   0:00 [khelper]
root         8  0.0  0.0      0     0 ?        SN   12:30   0:00 [async/mgr]
root         9  0.0  0.0      0     0 ?        SN   12:30   0:00 [pm]
root        10  0.0  0.0      0     0 ?        SN   12:30   0:00 [sync_supers]
root        11  0.0  0.0      0     0 ?        SN   12:30   0:00 [bdi-default]
root        12  0.0  0.0      0     0 ?        SN   12:30   0:00 [kintegrityd/0]
root        13  0.0  0.0      0     0 ?        SN   12:30   0:00 [kintegrityd/1]
root        14  0.0  0.0      0     0 ?        SN   12:30   0:00 [kblockd/0]
root        15  0.0  0.0      0     0 ?        SN   12:30   0:00 [kblockd/1]
root        16  0.0  0.0      0     0 ?        SN   12:30   0:00 [kacpid]
root        17  0.0  0.0      0     0 ?        SN   12:30   0:00 [kacpi_notify]
root        18  0.0  0.0      0     0 ?        SN   12:30   0:00 [kacpi_hotplug]
root        19  0.0  0.0      0     0 ?        SN   12:30   0:00 [ata/0]
root        20  0.0  0.0      0     0 ?        SN   12:30   0:00 [ata/1]
root        21  0.0  0.0      0     0 ?        SN   12:30   0:00 [ata_aux]
root        22  0.0  0.0      0     0 ?        SN   12:30   0:00 [ksuspend_usbd]
root        23  0.0  0.0      0     0 ?        SN   12:30   0:00 [khubd]
root        24  0.0  0.0      0     0 ?        SN   12:30   0:00 [kseriod]
root        25  0.0  0.0      0     0 ?        SN   12:30   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        SN   12:30   0:00 [kswapd0]
root        29  0.0  0.0      0     0 ?        SN   12:30   0:00 [ksmd]
root        30  0.0  0.0      0     0 ?        SN   12:30   0:00 [aio/0]
root        31  0.0  0.0      0     0 ?        SN   12:30   0:00 [aio/1]
root        32  0.0  0.0      0     0 ?        SN   12:30   0:00 [ecryptfs-kthrea]
root        33  0.0  0.0      0     0 ?        SN   12:30   0:00 [crypto/0]
root        34  0.0  0.0      0     0 ?        SN   12:30   0:00 [crypto/1]
root        38  0.0  0.0      0     0 ?        SN   12:30   0:00 [kstriped]
root        39  0.0  0.0      0     0 ?        SN   12:30   0:00 [kmpathd/0]
root        40  0.0  0.0      0     0 ?        SN   12:30   0:00 [kmpathd/1]
root        41  0.0  0.0      0     0 ?        SN   12:30   0:00 [kmpath_handlerd]
root        42  0.0  0.0      0     0 ?        SN   12:30   0:00 [ksnapd]
root       185  0.0  0.0      0     0 ?        SN   12:30   0:00 [scsi_eh_0]
root       223  0.0  0.0      0     0 ?        SN   12:30   0:00 [scsi_eh_1]
root       224  0.0  0.0      0     0 ?        SN   12:30   0:00 [khpsbpkt]
root       254  0.0  0.0      0     0 ?        SN   12:30   0:00 [knodemgrd_0]
root       257  0.0  0.0      0     0 ?        SN   12:30   0:00 [scsi_eh_2]
root       258  0.0  0.0      0     0 ?        SN   12:30   0:00 [scsi_eh_3]
root       272  0.0  0.0      0     0 ?        SN   12:30   0:00 [scsi_eh_4]
root       273  0.0  0.0      0     0 ?        SN   12:30   0:00 [usb-storage]
root       300  0.0  0.0      0     0 ?        SN   12:30   0:00 [usbhid_resumer]
root       310  0.0  0.0      0     0 ?        SN   12:30   0:00 [jbd2/sdb8-8]
root       311  0.0  0.0      0     0 ?        SN   12:30   0:00 [ext4-dio-unwrit]
root       312  0.0  0.0      0     0 ?        SN   12:30   0:00 [ext4-dio-unwrit]
root       321  0.0  0.0      0     0 ?        SN   12:30   0:00 [scsi_eh_5]
root       322  0.0  0.0      0     0 ?        SN   12:30   0:00 [usb-storage]
root       356  0.0  0.0  17028   948 ?        SN   12:30   0:00 upstart-udev-bridge --daemon
root       366  0.0  0.0  17192  1064 ?        SNs  12:30   0:00 udevd --daemon
root       503  0.0  0.0      0     0 ?        SN   12:30   0:00 [flush-8:16]
root       611  0.0  0.0  17476  1248 ?        SN   12:30   0:00 udevd --daemon
root       682  0.0  0.0      0     0 ?        SN   12:30   0:00 [kpsmoused]
syslog     751  0.0  0.0 111608  1476 ?        Sl   12:30   0:00 rsyslogd -c4
root       890  0.0  0.0      0     0 ?        SN   12:30   0:00 [hd-audio0]
root       917  0.0  0.0   6072   648 tty4     SNs+ 12:30   0:00 /sbin/getty -8 38400 tty4
root       921  0.0  0.0   6072   652 tty5     SNs+ 12:30   0:00 /sbin/getty -8 38400 tty5
root       939  0.0  0.0   6072   652 tty2     SNs+ 12:30   0:00 /sbin/getty -8 38400 tty2
root       940  0.0  0.0   6072   652 tty3     SNs+ 12:30   0:00 /sbin/getty -8 38400 tty3
root       942  0.0  0.0   6072   648 tty6     SNs+ 12:30   0:00 /sbin/getty -8 38400 tty6
root       944  0.0  0.0   4420  1156 ?        SNs  12:30   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       959  0.0  0.0  21068  1016 ?        SNs  12:30   0:00 cron
daemon     960  0.0  0.0  18876   460 ?        SNs  12:30   0:00 atd
102        968  0.0  0.0  24240  1804 ?        Ss   12:30   0:00 dbus-daemon --system --fork
kernoops   980  0.0  0.0  22312   976 ?        Ss   12:30   0:00 /usr/sbin/kerneloops
avahi      991  0.0  0.0  33920  1580 ?        S    12:30   0:00 avahi-daemon: running [Millennium.local]
avahi      992  0.0  0.0  33920   572 ?        Ss   12:30   0:00 avahi-daemon: chroot helper
root      1004  0.0  0.1  85508  4064 ?        SNsl 12:30   0:00 NetworkManager
root      1006  0.0  0.0  57856  2524 ?        SN   12:30   0:00 /usr/sbin/modem-manager
root      1007  0.0  0.0  65796  1484 ?        SNs  12:30   0:00 /usr/sbin/winbindd
root      1032  0.0  0.0  28344  2096 ?        SN   12:30   0:00 /sbin/wpa_supplicant -u -s
root      1033  0.0  0.0   6548  1104 ?        SN   12:30   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action
root      1035  0.0  0.0  75300  2864 ?        SNs  12:30   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1037  0.0  0.0  65796  1272 ?        SN   12:30   0:00 /usr/sbin/winbindd
timidity  1164  0.0  0.1 102976  7220 ?        SN   12:30   0:00 /usr/bin/timidity -Os -iAD
root      1167  0.0  0.0   6072   652 tty1     Ss+  12:30   0:00 /sbin/getty -8 38400 tty1
root      1223  0.0  0.0  74488  3512 ?        Ssl  12:30   0:00 gdm-binary
root      1229  0.0  0.0 120544  3756 ?        Sl   12:30   0:00 /usr/sbin/console-kit-daemon --no-daemon
root      1294  0.0  0.1  91508  4292 ?        Sl   12:30   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManage
root      1297  1.0  0.8 125816 32756 tty7     Ss+  12:30   0:02 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-oiAyxB/d
gdm       1317  0.0  0.0  26252   828 ?        S    12:30   0:00 /usr/bin/dbus-launch --exit-with-session
root      1335  0.0  0.0 101772  3656 ?        Sl   12:30   0:00 /usr/lib/gdm/gdm-session-worker
root      1337  0.0  0.0  53560  3048 ?        S    12:30   0:00 /usr/lib/upower/upowerd
root      1347  0.0  0.1  54040  4124 ?        S    12:30   0:00 /usr/lib/policykit-1/polkitd
109       1379  0.0  0.1  44840  5184 ?        Ssl  12:30   0:00 /usr/sbin/hald
root      1380  0.0  0.0  22308  1388 ?        S    12:30   0:00 hald-runner
root      1403  0.0  0.0  24428  1288 ?        S    12:30   0:00 hald-addon-input: Listening on /dev/input/event4 /dev/input/event0 
root      1415  0.0  0.0  24424  1300 ?        S    12:30   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      1416  0.0  0.0  24424  1308 ?        S    12:30   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
109       1433  0.0  0.0  26260  1248 ?        S    12:30   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
uwaysi    1443  0.0  0.0  69684  2748 ?        Sl   12:30   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
root      1454  0.0  0.0  24424  1300 ?        S    12:31   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
uwaysi    1472  0.0  0.1 169648  7968 ?        Ssl  12:31   0:00 gnome-session
uwaysi    1506  0.0  0.0  11928   408 ?        Ss   12:31   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-s
uwaysi    1509  0.0  0.0  26252   820 ?        S    12:31   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
uwaysi    1510  0.0  0.0  24080  1568 ?        Ss   12:31   0:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
uwaysi    1513  0.0  0.1  46248  5752 ?        S    12:31   0:00 /usr/lib/libgconf2-4/gconfd-2
uwaysi    1519  0.0  0.2 312224 10956 ?        Ss   12:31   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
uwaysi    1522  0.0  0.0  48064  2576 ?        S    12:31   0:00 /usr/lib/gvfs/gvfsd
uwaysi    1527  0.0  0.0  78016  2780 ?        Ssl  12:31   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/uwaysi/.gvfs
uwaysi    1533  0.0  0.1 213028  5160 ?        S<sl 12:31   0:00 /usr/bin/pulseaudio --start --log-target=syslog
uwaysi    1534  0.0  0.2 169332 10516 ?        S    12:31   0:00 metacity --sm-client-id 10f2fba2c3067bd6e12701364329894320000001296
uwaysi    1535  0.0  0.2 175808  8812 ?        S    12:31   0:00 gnome-power-manager
uwaysi    1536  0.0  0.2 168948  8692 ?        S    12:31   0:00 bluetooth-applet
uwaysi    1537  0.0  0.1 164080  7128 ?        S    12:31   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
uwaysi    1538  0.1  0.5 484512 22264 ?        S    12:31   0:00 nautilus --sm-client-id 10f2fba2c3067bd6e12701364332113000000129600
uwaysi    1539  0.2  0.4 263624 19944 ?        S    12:31   0:00 gnome-panel --sm-client-id 10f2fba2c3067bd6e12701364329897200000001
uwaysi    1544  0.0  0.3 235508 13108 ?        S    12:31   0:00 nm-applet --sm-disable
uwaysi    1548  0.0  0.0  96640  3500 ?        S    12:31   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
uwaysi    1552  0.0  0.1 152996  4284 ?        Ssl  12:31   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate -
uwaysi    1556  0.0  0.1 154184  4172 ?        S    12:31   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
root      1558  0.0  0.0  63880  3848 ?        Sl   12:31   0:00 /usr/lib/udisks/udisks-daemon
root      1559  0.0  0.0  46684  1084 ?        S    12:31   0:00 udisks-daemon: polling /dev/sdc /dev/sdd /dev/sr0
uwaysi    1561  0.0  0.0  55240  2672 ?        S    12:31   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
uwaysi    1563  0.0  0.0  69204  2720 ?        Sl   12:31   0:00 /usr/lib/gvfs/gvfs-afc-volume-monitor
uwaysi    1565  0.0  0.0  52544  3188 ?        S    12:31   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.6 /org/gtk/gvfs/exec_spaw/0
uwaysi    1570  0.0  0.3 255348 14368 ?        S    12:31   0:00 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wn
uwaysi    1574  0.0  0.3 239504 12416 ?        S    12:31   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_
uwaysi    1578  0.0  0.3 335292 14760 ?        S    12:31   0:00 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFII
uwaysi    1580  0.0  0.3 262556 15940 ?        S    12:31   0:00 /usr/lib/gnome-applets/stickynotes_applet --oaf-activate-iid=OAFIID
uwaysi    1583  0.0  0.2 207860 10012 ?        S    12:31   0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OA
uwaysi    1585  0.0  0.3 305984 15960 ?        S    12:31   0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_C
uwaysi    1587  0.0  0.3 267876 14900 ?        Sl   12:31   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-i
uwaysi    1588  0.2  0.2 220456 10168 ?        S    12:31   0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID
uwaysi    1593  0.0  0.0  41792  2448 ?        S    12:31   0:00 /usr/lib/gvfs/gvfsd-metadata
uwaysi    1595  0.0  0.1 144004  5704 ?        S    12:31   0:00 /usr/lib/indicator-me/indicator-me-service
uwaysi    1599  0.0  0.1 140944  5564 ?        S    12:31   0:00 /usr/lib/indicator-session/indicator-session-service
uwaysi    1602  0.0  0.1 138580  5124 ?        S    12:31   0:00 /usr/lib/indicator-messages/indicator-messages-service
uwaysi    1604  0.0  0.1 219012  5368 ?        S    12:31   0:00 /usr/lib/indicator-sound/indicator-sound-service
uwaysi    1608  0.0  0.1 146884  4884 ?        S    12:31   0:00 /usr/lib/indicator-application/indicator-application-service
uwaysi    1610  0.0  0.0 173636  3024 ?        Ss   12:31   0:00 gnome-screensaver
uwaysi    1612  0.0  0.0  48064  2656 ?        S    12:31   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.6 /org/gtk/gvfs/exec_spaw/1
root      1620  0.0  0.0  17252  1052 ?        S<   12:31   0:00 udevd --daemon
uwaysi    1633  0.0  0.2 176500  8172 ?        S    12:31   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
uwaysi    1635  0.0  0.5 231308 20960 ?        S    12:31   0:00 python /usr/share/system-config-printer/applet.py
uwaysi    1636  0.0  0.3 432132 13900 ?        Sl   12:31   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
uwaysi    1645  0.0  0.3 363700 13824 ?        Sl   12:31   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-i
uwaysi    1649  0.0  0.2 382552 10620 ?        Sl   12:31   0:00 /usr/lib/evolution/evolution-data-server-2.28 --oaf-activate-iid=OA
uwaysi    1678  0.0  0.3 204340 13492 ?        S    12:32   0:00 update-notifier
root      1682  0.0  0.2  78740 10716 ?        S    12:32   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root      1687  0.1  0.3  95668 15764 ?        S    12:32   0:00 /usr/bin/python /usr/sbin/aptd
uwaysi    1697  2.4  0.3 214148 14548 ?        Dl   12:34   0:00 gnome-terminal
uwaysi    1698  0.0  0.0  14480   812 ?        S    12:34   0:00 gnome-pty-helper
uwaysi    1699  3.2  0.1  22088  4908 pts/0    Ss   12:34   0:00 bash
uwaysi    1718  0.0  0.0  15248  1204 pts/0    R+   12:34   0:00 ps aux

---

### Post by Paradox Uncreated on 2010-04-13
For instance, we can start with /sbin/init

This is just a process initializing some other services. It can be called "a casual process" I can renice this to 14, without affecting audiovisual performance.

If anyone sees where I want to go with this, chime in with your information please.

---

### Post by Drenriza on 2010-04-13
You can open a terminal and type

```
top
```

---

### Post by Paradox Uncreated on 2010-04-13
I just made a script chrtall,

[B]for pid in `pgrep ""`; do
      chrt -f -p 1 $pid;
done[/B]

Which changes scheduling to fifo, for all processes. It was quite nice. Anyone know any good reasons for not doing this?

---

