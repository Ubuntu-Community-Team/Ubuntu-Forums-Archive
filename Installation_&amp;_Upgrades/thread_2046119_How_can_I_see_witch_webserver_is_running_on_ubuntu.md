---
title: "How can I see witch webserver is running on ubuntu 12.04 desktop"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2012-08-22
I have installed wordpress on xaamp and it is working fine,
now i want to install joomla.
But I am not sure witch webserver I am using 
I don't think that it is apache.
How can see witch webserver is running on my ubuntu 12.04 desktop ?
tks

---

### Post by rukiaEnix on 2012-08-22
Type this command:

```

lsof -i @0.0.0.0:80

```

If your server is running with the 80 port then it will show you the process that uses it, if not use the right port.

---

### Post by hoboy on 2012-08-22
> **rukiaEnix said:**
> Type this command:

```

lsof -i @0.0.0.0:80

```

If your server is running with the 80 port then it will show you the process that uses it, if not use the right port.

Tks but how do I identified a webserver on the output ?

---

### Post by rukiaEnix on 2012-08-22
Please post the result of:

```

ps -A

```

---

### Post by hoboy on 2012-08-22
> **rukiaEnix said:**
> Please post the result of:

```

ps -A

```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:01 ksoftirqd/0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 watchdog/0
    8 ?        00:00:00 migration/1
   10 ?        00:00:01 ksoftirqd/1
   12 ?        00:00:00 watchdog/1
   13 ?        00:00:00 cpuset
   14 ?        00:00:00 khelper
   15 ?        00:00:00 kdevtmpfs
   16 ?        00:00:00 netns
   18 ?        00:00:00 sync_supers
   19 ?        00:00:00 bdi-default
   20 ?        00:00:00 kintegrityd
   21 ?        00:00:00 kblockd
   23 ?        00:00:00 ata_sff
   24 ?        00:00:00 khubd
   25 ?        00:00:00 md
   26 ?        00:00:00 khungtaskd
   27 ?        00:00:02 kswapd0
   28 ?        00:00:00 ksmd
   29 ?        00:00:00 khugepaged
   30 ?        00:00:00 fsnotify_mark
   31 ?        00:00:00 ecryptfs-kthrea
   32 ?        00:00:00 crypto
   40 ?        00:00:00 kthrotld
   43 ?        00:00:00 scsi_eh_0
   44 ?        00:00:00 scsi_eh_1
   45 ?        00:00:00 scsi_eh_2
   46 ?        00:00:00 scsi_eh_3
   69 ?        00:00:00 devfreq_wq
  200 ?        00:00:01 jbd2/sda1-8
  201 ?        00:00:00 ext4-dio-unwrit
  235 ?        00:00:00 scsi_eh_4
  236 ?        00:00:00 scsi_eh_5
  327 ?        00:00:00 upstart-udev-br
  332 ?        00:00:00 udevd
  650 ?        00:00:00 udevd
  651 ?        00:00:00 udevd
  675 ?        00:00:00 cfg80211
  750 ?        00:00:00 firewire
  752 ?        00:00:00 kpsmoused
  812 ?        00:00:00 ttm_swap
  815 ?        00:00:00 hci0
  836 ?        00:00:02 flush-8:0
  885 ?        00:00:00 rsyslogd
  890 ?        00:00:00 upstart-socket-
  910 ?        00:00:00 hd-audio0
  918 ?        00:00:00 hd-audio1
  952 ?        00:00:01 dbus-daemon
  967 ?        00:00:00 modem-manager
  991 ?        00:00:00 bluetoothd
  994 ?        00:00:00 cupsd
 1000 ?        00:00:00 krfcommd
 1025 ?        00:00:00 avahi-daemon
 1026 ?        00:00:00 avahi-daemon
 1036 ?        00:00:01 NetworkManager
 1066 ?        00:00:00 polkitd
 1082 tty4     00:00:00 getty
 1089 tty5     00:00:00 getty
 1093 ?        00:00:00 wpa_supplicant
 1101 tty2     00:00:00 getty
 1102 tty3     00:00:00 getty
 1104 tty6     00:00:00 getty
 1111 ?        00:00:00 acpid
 1112 ?        00:00:00 cron
 1113 ?        00:00:00 atd
 1146 ?        00:00:00 lightdm
 1147 ?        00:00:01 irqbalance
 1151 ?        00:00:00 whoopsie
 1153 ?        00:00:00 iprt
 1160 tty7     00:09:25 Xorg
 1182 ?        00:00:00 dhclient
 1197 ?        00:00:00 winbindd
 1212 ?        00:00:00 dhclient
 1246 ?        00:00:00 winbindd
 1256 ?        00:00:00 lightdm
 1259 ?        00:00:00 accounts-daemon
 1295 ?        00:00:01 dnsmasq
 1335 ?        00:00:00 console-kit-dae
 1410 ?        00:00:00 gnome-session
 1447 ?        00:00:00 ssh-agent
 1450 ?        00:00:00 dbus-launch
 1502 ?        00:00:00 httpd
 1519 ?        00:00:00 mysqld_safe
 1522 ?        00:00:00 httpd
 1524 ?        00:00:00 httpd
 1527 ?        00:00:00 httpd
 1528 ?        00:00:00 httpd
 1532 ?        00:00:00 httpd
 1597 ?        00:00:07 dbus-daemon
 1602 ?        00:00:05 mysqld
 1627 ?        00:00:05 gnome-settings-
 1633 ?        00:00:00 gnome-keyring-d
 1646 ?        00:00:00 upowerd
 1710 ?        00:00:00 proftpd
 1713 ?        00:00:00 gvfsd
 1724 ?        00:00:00 gvfs-fuse-daemo
 1910 tty1     00:00:00 getty
 1912 ?        00:04:40 compiz
 1914 ?        00:00:00 colord
 1922 ?        00:00:02 syndaemon
 1928 ?        00:00:37 pulseaudio
 1930 ?        00:00:00 rtkit-daemon
 1934 ?        00:00:00 gconfd-2
 1939 ?        00:00:00 gvfsd-metadata
 1943 ?        00:00:00 gconf-helper
 1944 ?        00:00:00 nm-applet
 1945 ?        00:00:00 polkit-gnome-au
 1946 ?        00:00:00 bluetooth-apple
 1954 ?        00:00:54 nautilus
 1958 ?        00:00:00 gnome-fallback-
 1965 ?        00:00:00 gvfs-gdu-volume
 1968 ?        00:00:00 udisks-daemon
 1969 ?        00:00:00 udisks-daemon
 1974 ?        00:00:00 gvfs-afc-volume
 1979 ?        00:00:00 gvfs-gphoto2-vo
 1986 ?        00:00:00 gvfsd-trash
 1989 ?        00:00:00 gvfsd-burn
 1993 ?        00:00:05 bamfdaemon
 2006 ?        00:00:00 gdu-notificatio
 2015 ?        00:00:00 sh
 2016 ?        00:00:03 gtk-window-deco
 2020 ?        00:00:17 unity-panel-ser
 2022 ?        00:00:07 hud-service
 2041 ?        00:00:00 indicator-messa
 2042 ?        00:00:00 indicator-sound
 2043 ?        00:00:00 indicator-datet
 2044 ?        00:00:00 indicator-sessi
 2047 ?        00:00:00 indicator-print
 2048 ?        00:00:00 indicator-appli
 2089 ?        00:00:00 geoclue-master
 2091 ?        00:00:00 ubuntu-geoip-pr
 2093 ?        00:00:00 telepathy-indic
 2097 ?        00:00:00 mission-control
 2102 ?        00:00:00 goa-daemon
 2122 ?        00:00:00 unity-applicati
 2124 ?        00:00:00 unity-files-dae
 2126 ?        00:00:00 unity-music-dae
 2128 ?        00:00:00 unity-lens-vide
 2140 ?        00:00:00 zeitgeist-daemo
 2157 ?        00:00:00 gnome-screensav
 2167 ?        00:00:00 zeitgeist-fts
 2169 ?        00:00:01 zeitgeist-datah
 2181 ?        00:00:00 cat
 2186 ?        00:00:00 unity-musicstor
 2207 ?        00:00:00 at-spi-bus-laun
 2236 ?        00:00:00 unity-scope-vid
 2295 ?        00:00:00 update-notifier
 2323 ?        00:00:00 deja-dup-monito
 3796 ?        00:00:00 dconf-service
 4249 ?        00:05:13 java
 4634 ?        00:00:00 notify-osd
 4890 ?        00:06:14 firefox
 4928 ?        00:00:00 httpd
 4931 ?        00:00:01 httpd
 4932 ?        00:00:00 httpd
 4933 ?        00:00:00 httpd
 4934 ?        00:00:00 httpd
 4976 ?        00:00:00 httpd
 4982 ?        00:00:03 kworker/0:2
 5003 ?        00:00:00 kworker/u:2
 5028 ?        00:00:02 kworker/1:2
 5057 ?        00:00:05 gnome-terminal
 5063 ?        00:00:00 kworker/u:1
 5065 ?        00:00:00 gnome-pty-helpe
 5066 pts/0    00:00:00 bash
 5125 ?        00:00:00 kworker/0:0
 5131 ?        00:00:00 kworker/1:0
 5137 ?        00:00:00 kworker/u:0
 5150 ?        00:00:00 kworker/1:1
 5154 pts/0    00:00:00 ps

---

### Post by rukiaEnix on 2012-08-22
It is httpd. Always check  your processes, it could only have been Apache or httpd.

---

### Post by hoboy on 2012-08-22
> **rukiaEnix said:**
> It is httpd. Always check  your processes, it could only have been Apache or httpd.

tks

---

### Post by rukiaEnix on 2012-08-22
You're welcome.

Also the lsof command should have show you something, but for the next time try with the processes list.

---

