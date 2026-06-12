---
title: "K# processes under gnome?"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by jhaquo on 2006-12-05
hi
when i do a "ps -A" iget a lot of processes which belongs to kde (which is installed) but i use gnome
how can i avoid those proceses to auto start please?

i removed all those i knew from the list, but the k# ones disturb me the most since im not in KDE
```
jhaquo@jhaquo-laptop:~$ ps -A
  PID TTY          TIME CMD
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  117 ?        00:00:00 kseriod
  151 ?        00:00:00 pdflush
  152 ?        00:00:00 pdflush
  153 ?        00:00:02 kswapd0
  154 ?        00:00:00 aio/0
 1702 ?        00:00:00 khubd
 1720 ?        00:00:00 khpsbpkt
 1749 ?        00:00:00 knodemgrd_0
 1798 ?        00:00:00 kjournald
 1873 ?        00:00:00 logd
 2020 ?        00:00:00 udevd
 2863 ?        00:00:00 shpchpd
 2875 ?        00:00:00 kpsmoused
 2881 ?        00:00:00 tifm0
 2943 ?        00:00:00 pccardd
 2962 ?        00:00:00 hda_codec
 2981 ?        00:00:00 ipw2200/0
 3209 ?        00:00:02 kjournald
 3352 ?        00:00:00 dhclient3
 3533 tty1     00:00:00 getty
 3534 tty2     00:00:00 getty
 3535 tty3     00:00:00 getty
 3536 tty4     00:00:00 getty
 3537 tty5     00:00:00 getty
 3538 tty6     00:00:00 getty
 3749 ?        00:00:00 acpid
 3839 ?        00:00:00 syslogd
 3865 ?        00:00:00 dd
 3867 ?        00:00:00 klogd
 4020 ?        00:00:00 cupsd
 4043 ?        00:00:00 hpiod
 4166 ?        00:00:00 logger
 4263 ?        00:00:00 apt-index-watch
 4284 ?        00:00:01 dbus-daemon
 4311 ?        00:00:03 hald
 4312 ?        00:00:00 hald-runner
 4332 ?        00:00:00 hald-addon-acpi
 4335 ?        00:00:00 hald-addon-keyb
 4362 ?        00:00:00 perl
 4435 ?        00:00:00 ondemand
 4541 ?        00:00:00 hcid
 4545 ?        00:00:00 sdpd
 4557 ?        00:00:00 krfcommd
 4581 ?        00:00:00 atd
 4594 ?        00:00:00 cron
 4722 ?        00:00:00 dbus-launch
 4728 ?        00:00:00 dbus-daemon
 4745 ?        00:00:00 sh
 4746 ?        00:00:00 esd
 4764 ?        00:00:00 bonobo-activati
 4834 ?        00:00:00 evolution-data-
 4842 ?        00:00:00 mapping-daemon
 4889 ?        00:00:00 mixer_applet2
 4972 ?        00:00:00 kdeinit
 4977 ?        00:00:00 dcopserver
 4980 ?        00:00:00 klauncher
 4982 ?        00:00:03 kded
13440 ?        00:00:00 hald-addon-keyb
13843 ?        00:00:00 kio_file
13844 ?        00:00:00 ruby


```

---

### Post by jhaquo on 2006-12-08
up :(

---

### Post by christhemonkey on 2006-12-08
Some (most?) of the K# commands (such as klogd and kacpid) are **k**ernel processes, not kde ones.

---

### Post by jhaquo on 2006-12-09
ow! ok, thx

---

