---
title: "[SOLVED] 7.10 nautilus errors"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by beorn! on 2007-07-17
I recently upgraded 7.10 alpha 2, running the 2.6.22.8 kernel. Everything is working perfectly, I like the updates with fwcutter and the vpn... however, nautulis is taking 500+ Mb or ram and 99% of my  1.4Ghz cpu... I think there is a bug, however I am not a guru... 

lsof shows the following.... /any ideas?/

COMMAND     PID       USER   FD      TYPE     DEVICE    SIZE       NODE NAME
init          1       root  cwd       DIR        3,1    4096          2 /
init          1       root  rtd       DIR        3,1    4096          2 /
init          1       root  txt       REG        3,1   88672    1261618 /sbin/init
init          1       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
init          1       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
init          1       root    0u      CHR        5,1               2198 /dev/console (deleted)
init          1       root    1u      CHR        5,1               2198 /dev/console (deleted)
init          1       root    2u      CHR        5,1               2198 /dev/console (deleted)
init          1       root    3u     unix 0xdfb9ee00               8073 socket
init          1       root    4r      DIR       0,10       0          1 inotify
init          1       root    5r     FIFO        0,6               8074 pipe
init          1       root    6w     FIFO        0,6               8074 pipe
kthreadd      2       root  cwd       DIR        3,1    4096          2 /
kthreadd      2       root  rtd       DIR        3,1    4096          2 /
kthreadd      2       root  txt   unknown                               /proc/2/exe
migration     3       root  cwd       DIR        3,1    4096          2 /
migration     3       root  rtd       DIR        3,1    4096          2 /
migration     3       root  txt   unknown                               /proc/3/exe
ksoftirqd     4       root  cwd       DIR        3,1    4096          2 /
ksoftirqd     4       root  rtd       DIR        3,1    4096          2 /
ksoftirqd     4       root  txt   unknown                               /proc/4/exe
watchdog/     5       root  cwd       DIR        3,1    4096          2 /
watchdog/     5       root  rtd       DIR        3,1    4096          2 /
watchdog/     5       root  txt   unknown                               /proc/5/exe
events/0      6       root  cwd       DIR        3,1    4096          2 /
events/0      6       root  rtd       DIR        3,1    4096          2 /
events/0      6       root  txt   unknown                               /proc/6/exe
khelper       7       root  cwd       DIR        3,1    4096          2 /
khelper       7       root  rtd       DIR        3,1    4096          2 /
khelper       7       root  txt   unknown                               /proc/7/exe
kblockd/0    27       root  cwd       DIR        3,1    4096          2 /
kblockd/0    27       root  rtd       DIR        3,1    4096          2 /
kblockd/0    27       root  txt   unknown                               /proc/27/exe
kacpid       28       root  cwd       DIR        3,1    4096          2 /
kacpid       28       root  rtd       DIR        3,1    4096          2 /
kacpid       28       root  txt   unknown                               /proc/28/exe
kacpi_not    29       root  cwd       DIR        3,1    4096          2 /
kacpi_not    29       root  rtd       DIR        3,1    4096          2 /
kacpi_not    29       root  txt   unknown                               /proc/29/exe
kseriod     134       root  cwd       DIR        3,1    4096          2 /
kseriod     134       root  rtd       DIR        3,1    4096          2 /
kseriod     134       root  txt   unknown                               /proc/134/exe
pdflush     153       root  cwd       DIR        3,1    4096          2 /
pdflush     153       root  rtd       DIR        3,1    4096          2 /
pdflush     153       root  txt   unknown                               /proc/153/exe
pdflush     154       root  cwd       DIR        3,1    4096          2 /
pdflush     154       root  rtd       DIR        3,1    4096          2 /
pdflush     154       root  txt   unknown                               /proc/154/exe
kswapd0     155       root  cwd       DIR        3,1    4096          2 /
kswapd0     155       root  rtd       DIR        3,1    4096          2 /
kswapd0     155       root  txt   unknown                               /proc/155/exe
aio/0       206       root  cwd       DIR        3,1    4096          2 /
aio/0       206       root  rtd       DIR        3,1    4096          2 /
aio/0       206       root  txt   unknown                               /proc/206/exe
ata/0      2033       root  cwd       DIR        3,1    4096          2 /
ata/0      2033       root  rtd       DIR        3,1    4096          2 /
ata/0      2033       root  txt   unknown                               /proc/2033/exe
ata_aux    2034       root  cwd       DIR        3,1    4096          2 /
ata_aux    2034       root  rtd       DIR        3,1    4096          2 /
ata_aux    2034       root  txt   unknown                               /proc/2034/exe
ksuspend_  2038       root  cwd       DIR        3,1    4096          2 /
ksuspend_  2038       root  rtd       DIR        3,1    4096          2 /
ksuspend_  2038       root  txt   unknown                               /proc/2038/exe
khubd      2053       root  cwd       DIR        3,1    4096          2 /
khubd      2053       root  rtd       DIR        3,1    4096          2 /
khubd      2053       root  txt   unknown                               /proc/2053/exe
kjournald  2314       root  cwd       DIR        3,1    4096          2 /
kjournald  2314       root  rtd       DIR        3,1    4096          2 /
kjournald  2314       root  txt   unknown                               /proc/2314/exe
udevd      2493       root  cwd       DIR        3,1    4096          2 /
udevd      2493       root  rtd       DIR        3,1    4096          2 /
udevd      2493       root  txt       REG        3,1   65704    1261576 /sbin/udevd
udevd      2493       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
udevd      2493       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
udevd      2493       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
udevd      2493       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
udevd      2493       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
udevd      2493       root  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
udevd      2493       root  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
udevd      2493       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
udevd      2493       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
udevd      2493       root    0u      CHR        1,3               8184 /dev/null
udevd      2493       root    1u      CHR        1,3               8184 /dev/null
udevd      2493       root    2u      CHR        1,3               8184 /dev/null
udevd      2493       root    3r      DIR       0,10       0          1 inotify
udevd      2493       root    4u     unix 0xdfb9d700               8200 socket
udevd      2493       root    5u     sock        0,5               8201 can't identify protocol
udevd      2493       root    6r     FIFO        0,6               8202 pipe
udevd      2493       root    7w     FIFO        0,6               8202 pipe
tifm       3343       root  cwd       DIR        3,1    4096          2 /
tifm       3343       root  rtd       DIR        3,1    4096          2 /
tifm       3343       root  txt   unknown                               /proc/3343/exe
pccardd    3353       root  cwd       DIR        3,1    4096          2 /
pccardd    3353       root  rtd       DIR        3,1    4096          2 /
pccardd    3353       root  txt   unknown                               /proc/3353/exe
kmmcd      3355       root  cwd       DIR        3,1    4096          2 /
kmmcd      3355       root  rtd       DIR        3,1    4096          2 /
kmmcd      3355       root  txt   unknown                               /proc/3355/exe
kpsmoused  3486       root  cwd       DIR        3,1    4096          2 /
kpsmoused  3486       root  rtd       DIR        3,1    4096          2 /
kpsmoused  3486       root  txt   unknown                               /proc/3486/exe
kgameport  3574       root  cwd       DIR        3,1    4096          2 /
kgameport  3574       root  rtd       DIR        3,1    4096          2 /
kgameport  3574       root  txt   unknown                               /proc/3574/exe
dhclient3  3823       dhcp  cwd       DIR        3,1    4096          2 /
dhclient3  3823       dhcp  rtd       DIR        3,1    4096          2 /
dhclient3  3823       dhcp  txt       REG        3,1  352904    1261632 /sbin/dhclient3
dhclient3  3823       dhcp  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
dhclient3  3823       dhcp  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
dhclient3  3823       dhcp  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
dhclient3  3823       dhcp  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
dhclient3  3823       dhcp  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dhclient3  3823       dhcp  mem       REG        3,1   11088    4735019 /lib/libcap.so.1.10
dhclient3  3823       dhcp  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dhclient3  3823       dhcp    0u      CHR        1,3               8184 /dev/null
dhclient3  3823       dhcp    1u      CHR        1,3               8184 /dev/null
dhclient3  3823       dhcp    2u      CHR        1,3               8184 /dev/null
dhclient3  3823       dhcp    4u     IPv4      12362                UDP *:bootpc 
dhclient3  3823       dhcp    5u     sock        0,5              12236 can't identify protocol
dhclient3  3823       dhcp    6w      REG        3,1     519     786818 /var/lib/dhcp3/dhclient.eth2.leases
getty      4214       root  cwd       DIR       0,14   13860       2193 /dev
getty      4214       root  rtd       DIR        3,1    4096          2 /
getty      4214       root  txt       REG        3,1   14896    1261672 /sbin/getty
getty      4214       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
getty      4214       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
getty      4214       root    0u      CHR        4,4               2501 /dev/tty4
getty      4214       root    1u      CHR        4,4               2501 /dev/tty4
getty      4214       root    2u      CHR        4,4               2501 /dev/tty4
getty      4215       root  cwd       DIR       0,14   13860       2193 /dev
getty      4215       root  rtd       DIR        3,1    4096          2 /
getty      4215       root  txt       REG        3,1   14896    1261672 /sbin/getty
getty      4215       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
getty      4215       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
getty      4215       root    0u      CHR        4,5               2504 /dev/tty5
getty      4215       root    1u      CHR        4,5               2504 /dev/tty5
getty      4215       root    2u      CHR        4,5               2504 /dev/tty5
getty      4218       root  cwd       DIR       0,14   13860       2193 /dev
getty      4218       root  rtd       DIR        3,1    4096          2 /
getty      4218       root  txt       REG        3,1   14896    1261672 /sbin/getty
getty      4218       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
getty      4218       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
getty      4218       root    0u      CHR        4,2               2495 /dev/tty2
getty      4218       root    1u      CHR        4,2               2495 /dev/tty2
getty      4218       root    2u      CHR        4,2               2495 /dev/tty2
getty      4219       root  cwd       DIR       0,14   13860       2193 /dev
getty      4219       root  rtd       DIR        3,1    4096          2 /
getty      4219       root  txt       REG        3,1   14896    1261672 /sbin/getty
getty      4219       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
getty      4219       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
getty      4219       root    0u      CHR        4,3               2498 /dev/tty3
getty      4219       root    1u      CHR        4,3               2498 /dev/tty3
getty      4219       root    2u      CHR        4,3               2498 /dev/tty3
getty      4220       root  cwd       DIR       0,14   13860       2193 /dev
getty      4220       root  rtd       DIR        3,1    4096          2 /
getty      4220       root  txt       REG        3,1   14896    1261672 /sbin/getty
getty      4220       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
getty      4220       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
getty      4220       root    0u      CHR        4,1               2492 /dev/tty1
getty      4220       root    1u      CHR        4,1               2492 /dev/tty1
getty      4220       root    2u      CHR        4,1               2492 /dev/tty1
getty      4221       root  cwd       DIR       0,14   13860       2193 /dev
getty      4221       root  rtd       DIR        3,1    4096          2 /
getty      4221       root  txt       REG        3,1   14896    1261672 /sbin/getty
getty      4221       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
getty      4221       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
getty      4221       root    0u      CHR        4,6               2507 /dev/tty6
getty      4221       root    1u      CHR        4,6               2507 /dev/tty6
getty      4221       root    2u      CHR        4,6               2507 /dev/tty6
acpid      4418       root  cwd       DIR        3,1    4096          2 /
acpid      4418       root  rtd       DIR        3,1    4096          2 /
acpid      4418       root  txt       REG        3,1   19604    5867534 /usr/sbin/acpid
acpid      4418       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
acpid      4418       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
acpid      4418       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
acpid      4418       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
acpid      4418       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
acpid      4418       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
acpid      4418       root    0r      CHR        1,3               8184 /dev/null
acpid      4418       root    1w      REG        3,1  252795     786803 /var/log/acpid
acpid      4418       root    2w      REG        3,1  252795     786803 /var/log/acpid
acpid      4418       root    3r      REG        0,3       0 4026531924 /proc/acpi/event
acpid      4418       root    4u     unix 0xdfb9ec40              14623 /var/run/acpid.socket
acpid      4418       root    5u     unix 0xdfb9d8c0              15029 /var/run/acpid.socket
acpid      4418       root    6u     unix 0xf2e628c0              15765 /var/run/acpid.socket
kondemand  4463       root  cwd       DIR        3,1    4096          2 /
kondemand  4463       root  rtd       DIR        3,1    4096          2 /
kondemand  4463       root  txt   unknown                               /proc/4463/exe
syslogd    4507       root  cwd       DIR        3,1    4096          2 /
syslogd    4507       root  rtd       DIR        3,1    4096          2 /
syslogd    4507       root  txt       REG        3,1   32084    1261587 /sbin/syslogd
syslogd    4507       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
syslogd    4507       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
syslogd    4507       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
syslogd    4507       root    0u     unix 0xc19b0380              14721 /dev/log
syslogd    4507       root    1w      REG        3,1   10586     786850 /var/log/auth.log
syslogd    4507       root    2w      REG        3,1  282023     786774 /var/log/syslog
syslogd    4507       root    3w      REG        3,1  353399     786847 /var/log/daemon.log
syslogd    4507       root    4w      REG        3,1  257737     786851 /var/log/kern.log
syslogd    4507       root    5w      REG        3,1       0     786780 /var/log/lpr.log
syslogd    4507       root    6w      REG        3,1       0     786783 /var/log/mail.log
syslogd    4507       root    7w      REG        3,1    6886     786695 /var/log/user.log
syslogd    4507       root    8w      REG        3,1       0     786782 /var/log/mail.info
syslogd    4507       root    9w      REG        3,1       0     786784 /var/log/mail.warn
syslogd    4507       root   10w      REG        3,1       0     786781 /var/log/mail.err
syslogd    4507       root   11w      REG        3,1       0     835594 /var/log/news/news.crit
syslogd    4507       root   12w      REG        3,1       0     835597 /var/log/news/news.err
syslogd    4507       root   13w      REG        3,1       0     835598 /var/log/news/news.notice
syslogd    4507       root   14w      REG        3,1   54071     786849 /var/log/debug
syslogd    4507       root   15w      REG        3,1  226842     786848 /var/log/messages
syslogd    4507       root   16u     FIFO       0,14              14711 /dev/xconsole
dd         4559       root  cwd       DIR        3,1    4096          2 /
dd         4559       root  rtd       DIR        3,1    4096          2 /
dd         4559       root  txt       REG        3,1   38780    5439515 /bin/dd
dd         4559       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
dd         4559       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dd         4559       root  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
dd         4559       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dd         4559       root    0r      REG        0,3       0 4026531849 /proc/kmsg
dd         4559       root    1w     FIFO       0,16              14760 /var/run/klogd/kmsg
dd         4559       root    2u      CHR        1,3               8184 /dev/null
klogd      4561       klog  cwd       DIR        3,1    4096          2 /
klogd      4561       klog  rtd       DIR        3,1    4096          2 /
klogd      4561       klog  txt       REG        3,1   23040    1261588 /sbin/klogd
klogd      4561       klog  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
klogd      4561       klog  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
klogd      4561       klog    0r     FIFO       0,16              14760 /var/run/klogd/kmsg
klogd      4561       klog    1r      REG        3,1  821814    4947993 /boot/System.map-2.6.22-8-generic
klogd      4561       klog    3u     unix 0xf5a33700              14798 socket
dbus-daem  4582 messagebus  cwd       DIR        3,1    4096          2 /
dbus-daem  4582 messagebus  rtd       DIR        3,1    4096          2 /
dbus-daem  4582 messagebus  txt       REG        3,1  302692    5865655 /usr/bin/dbus-daemon
dbus-daem  4582 messagebus  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
dbus-daem  4582 messagebus  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
dbus-daem  4582 messagebus  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
dbus-daem  4582 messagebus  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
dbus-daem  4582 messagebus  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dbus-daem  4582 messagebus    0u      CHR        1,3               8184 /dev/null
dbus-daem  4582 messagebus    1u      CHR        1,3               8184 /dev/null
dbus-daem  4582 messagebus    2u      CHR        1,3               8184 /dev/null
dbus-daem  4582 messagebus    3u     unix 0xf5a33380              14805 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus    4u      CHR        1,3               8184 /dev/null
dbus-daem  4582 messagebus    5r      DIR        3,1    4096    2573085 /etc/dbus-1/system.d
dbus-daem  4582 messagebus    6u     unix 0xc19b0700              14807 socket
dbus-daem  4582 messagebus    7u     unix 0xf64dcc40              14808 socket
dbus-daem  4582 messagebus    8u     unix 0xdfb9de00              14833 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus    9u     unix 0xf42dd000              14836 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   10u     unix 0xf42dd700              14862 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   11u     unix 0xf30b1c40              15257 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   12u     unix 0xf315de00              15268 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   13u     unix 0xf3358000              15283 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   14u     unix 0xf28601c0              16492 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   15u     unix 0xf1c81380              16705 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   16u     unix 0xf1572540              17542 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   17u     unix 0xf08aa000              17806 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   18u     unix 0xf0561380              17876 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   19u     unix 0xf0689380              17985 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   20u     unix 0xefe338c0              18022 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   21u     unix 0xee003c40              18182 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   22u     unix 0xee389000              21007 /var/run/dbus/system_bus_socket
dbus-daem  4582 messagebus   23u     unix 0xeda8e540              19980 /var/run/dbus/system_bus_socket
NetworkMa  4598       root  cwd       DIR        3,1    4096          2 /
NetworkMa  4598       root  rtd       DIR        3,1    4096          2 /
NetworkMa  4598       root  txt       REG        3,1  294480    5866645 /usr/sbin/NetworkManager
NetworkMa  4598       root  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
NetworkMa  4598       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
NetworkMa  4598       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
NetworkMa  4598       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
NetworkMa  4598       root  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
NetworkMa  4598       root  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
NetworkMa  4598       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
NetworkMa  4598       root  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
NetworkMa  4598       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
NetworkMa  4598       root  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
NetworkMa  4598       root  mem       REG        3,1   33744    5867291 /usr/lib/libnm-util.so.0.0.0
NetworkMa  4598       root  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
NetworkMa  4598       root  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
NetworkMa  4598       root  mem       REG        3,1  209972    5867317 /usr/lib/libnl.so.1.0-pre6
NetworkMa  4598       root  mem       REG        3,1   27012    4735046 /lib/libiw.so.29
NetworkMa  4598       root  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
NetworkMa  4598       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
NetworkMa  4598       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
NetworkMa  4598       root    0u      CHR        1,3               8184 /dev/null
NetworkMa  4598       root    1u      CHR        1,3               8184 /dev/null
NetworkMa  4598       root    2u      CHR        1,3               8184 /dev/null
NetworkMa  4598       root    3u     unix 0xdfb9dc40              14828 socket
NetworkMa  4598       root    4r     FIFO        0,6              14829 pipe
NetworkMa  4598       root    5w     FIFO        0,6              14829 pipe
NetworkMa  4598       root    6r     FIFO        0,6              14830 pipe
NetworkMa  4598       root    7w     FIFO        0,6              14830 pipe
NetworkMa  4598       root    8u     sock        0,5              14831 can't identify protocol
NetworkMa  4598       root    9u     unix 0xdfb9d540              14832 socket
NetworkMa  4598       root   10r      DIR       0,10       0          1 inotify
NetworkMa  4598       root   11r     FIFO        0,6              16542 pipe
NetworkMa  4598       root   12w     FIFO        0,6              16542 pipe
NetworkMa  4598       root   13r     FIFO        0,6              16698 pipe
NetworkMa  4598       root   14w     FIFO        0,6              16698 pipe
NetworkMa  4598       root   15r     FIFO        0,6              16700 pipe
NetworkMa  4598       root   16w     FIFO        0,6              16700 pipe
NetworkMa  4598       root   17r     FIFO        0,6              22028 pipe
NetworkMa  4598       root   18w     FIFO        0,6              22028 pipe
NetworkMa  4598       root   19u     unix 0xf79b2c40              22054 /var/run/NetworkManager/wpa_ctrl_4598-2
NetworkMa  4611       root  cwd       DIR        3,1    4096          2 /
NetworkMa  4611       root  rtd       DIR        3,1    4096          2 /
NetworkMa  4611       root  txt       REG        3,1   16032    5866646 /usr/sbin/NetworkManagerDispatcher
NetworkMa  4611       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
NetworkMa  4611       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
NetworkMa  4611       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
NetworkMa  4611       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
NetworkMa  4611       root  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
NetworkMa  4611       root  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
NetworkMa  4611       root  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
NetworkMa  4611       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
NetworkMa  4611       root  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
NetworkMa  4611       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
NetworkMa  4611       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
NetworkMa  4611       root    0u      CHR        1,3               8184 /dev/null
NetworkMa  4611       root    1u      CHR        1,3               8184 /dev/null
NetworkMa  4611       root    2u      CHR        1,3               8184 /dev/null
NetworkMa  4611       root    3u     unix 0xc18b01c0              14835 socket
NetworkMa  4611       root    4r     FIFO        0,6              14837 pipe
NetworkMa  4611       root    5w     FIFO        0,6              14837 pipe
system-to  4625       root  cwd       DIR        3,1    4096          2 /
system-to  4625       root  rtd       DIR        3,1    4096          2 /
system-to  4625       root  txt       REG        3,1   10060    5866379 /usr/bin/system-tools-backends
system-to  4625       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
system-to  4625       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
system-to  4625       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
system-to  4625       root  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
system-to  4625       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
system-to  4625       root  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
system-to  4625       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
system-to  4625       root    0u      CHR        1,3               8184 /dev/null
system-to  4625       root    1u      CHR        1,3               8184 /dev/null
system-to  4625       root    2u      CHR        1,3               8184 /dev/null
system-to  4625       root    3u     unix 0xf42dd1c0              14859 socket
system-to  4625       root    4u     unix 0xf42dd380              14861 socket
system-to  4625       root    5r     FIFO        0,6              14846 pipe
dbus-daem  4626       root  cwd       DIR        3,1    4096          2 /
dbus-daem  4626       root  rtd       DIR        3,1    4096          2 /
dbus-daem  4626       root  txt       REG        3,1  302692    5865655 /usr/bin/dbus-daemon
dbus-daem  4626       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
dbus-daem  4626       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
dbus-daem  4626       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
dbus-daem  4626       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
dbus-daem  4626       root  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
dbus-daem  4626       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
dbus-daem  4626       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dbus-daem  4626       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
dbus-daem  4626       root  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
dbus-daem  4626       root  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
dbus-daem  4626       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dbus-daem  4626       root    0r      CHR        1,3               8184 /dev/null
dbus-daem  4626       root    1w     FIFO        0,6              14846 pipe
dbus-daem  4626       root    2u      CHR        1,3               8184 /dev/null
dbus-daem  4626       root    3u     unix 0xc18b08c0              14856 socket
dbus-daem  4626       root    4u     unix 0xf64dce00              14857 socket
dbus-daem  4626       root    5u     unix 0xf42ddc40              14858 socket
dbus-daem  4626       root    6u     unix 0xf42dd540              14860 socket
gdm        4656       root  cwd       DIR        3,1    4096     786661 /var/lib/gdm
gdm        4656       root  rtd       DIR        3,1    4096          2 /
gdm        4656       root  txt       REG        3,1  298892    5867594 /usr/sbin/gdm
gdm        4656       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gdm        4656       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gdm        4656       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gdm        4656       root  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gdm        4656       root  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gdm        4656       root  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gdm        4656       root  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gdm        4656       root  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gdm        4656       root  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gdm        4656       root  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gdm        4656       root  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gdm        4656       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gdm        4656       root  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gdm        4656       root  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gdm        4656       root  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gdm        4656       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gdm        4656       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gdm        4656       root  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gdm        4656       root  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gdm        4656       root  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gdm        4656       root  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gdm        4656       root  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gdm        4656       root  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gdm        4656       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gdm        4656       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gdm        4656       root  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gdm        4656       root  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gdm        4656       root  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gdm        4656       root  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gdm        4656       root  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gdm        4656       root  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gdm        4656       root  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gdm        4656       root  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gdm        4656       root  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gdm        4656       root  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gdm        4656       root  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gdm        4656       root  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gdm        4656       root  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gdm        4656       root  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gdm        4656       root  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gdm        4656       root  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gdm        4656       root  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gdm        4656       root  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gdm        4656       root  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gdm        4656       root  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gdm        4656       root  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
gdm        4656       root  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gdm        4656       root  mem       REG        3,1   27648    4735117 /lib/libwrap.so.0.7.6
gdm        4656       root  mem       REG        3,1   30596    4735077 /lib/libpam.so.0.79
gdm        4656       root  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gdm        4656       root  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gdm        4656       root  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gdm        4656       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gdm        4656       root  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gdm        4656       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gdm        4656       root    0r      CHR        1,3               8184 /dev/null
gdm        4656       root    1u      CHR        1,3               8184 /dev/null
gdm        4656       root    2u      CHR        1,3               8184 /dev/null
gdm        4656       root    3u     FIFO        3,1             786499 /var/lib/gdm/.gdmfifo
gdm        4656       root    4r     FIFO        0,6              14963 pipe
gdm        4656       root    5w     FIFO        0,6              14963 pipe
gdm        4656       root    6u     unix 0xf465d540              14964 /var/run/gdm_socket
gdm        4656       root    8w     FIFO        0,6              14967 pipe
gdm        4657       root  cwd       DIR        3,1    4096     786661 /var/lib/gdm
gdm        4657       root  rtd       DIR        3,1    4096          2 /
gdm        4657       root  txt       REG        3,1  298892    5867594 /usr/sbin/gdm
gdm        4657       root  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
gdm        4657       root  mem       REG        3,1   11088    4735019 /lib/libcap.so.1.10
gdm        4657       root  mem       REG        3,1   17228    4735532 /lib/security/pam_limits.so
gdm        4657       root  mem       REG        3,1   52088    4735549 /lib/security/pam_unix.so
gdm        4657       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gdm        4657       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gdm        4657       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gdm        4657       root  mem       REG        3,1    2948    4735527 /lib/security/pam_foreground.so
gdm        4657       root  mem       REG        3,1   11052    4735525 /lib/security/pam_env.so
gdm        4657       root  mem       REG        3,1    5828    4735538 /lib/security/pam_nologin.so
gdm        4657       root  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gdm        4657       root  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gdm        4657       root  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gdm        4657       root  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gdm        4657       root  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gdm        4657       root  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gdm        4657       root  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gdm        4657       root  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gdm        4657       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gdm        4657       root  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gdm        4657       root  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gdm        4657       root  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gdm        4657       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gdm        4657       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gdm        4657       root  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gdm        4657       root  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gdm        4657       root  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gdm        4657       root  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gdm        4657       root  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gdm        4657       root  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gdm        4657       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gdm        4657       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gdm        4657       root  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gdm        4657       root  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gdm        4657       root  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gdm        4657       root  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gdm        4657       root  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gdm        4657       root  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gdm        4657       root  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gdm        4657       root  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gdm        4657       root  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gdm        4657       root  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gdm        4657       root  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gdm        4657       root  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gdm        4657       root  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gdm        4657       root  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gdm        4657       root  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gdm        4657       root  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gdm        4657       root  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gdm        4657       root  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gdm        4657       root  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gdm        4657       root  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gdm        4657       root  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
gdm        4657       root  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gdm        4657       root  mem       REG        3,1   27648    4735117 /lib/libwrap.so.0.7.6
gdm        4657       root  mem       REG        3,1   30596    4735077 /lib/libpam.so.0.79
gdm        4657       root  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gdm        4657       root  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gdm        4657       root  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gdm        4657       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gdm        4657       root  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gdm        4657       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gdm        4657       root    0r      CHR        1,3               8184 /dev/null
gdm        4657       root    1u      CHR        1,3               8184 /dev/null
gdm        4657       root    2u      CHR        1,3               8184 /dev/null
gdm        4657       root    3r     unix 0xf465dc40              15027 socket
gdm        4657       root    4u     unix 0xf315d000              16943 socket
gdm        4657       root    5w     FIFO        0,6              14963 pipe
gdm        4657       root    6w      CHR        5,1               8177 /dev/console
gdm        4657       root    7r     FIFO        0,6              14967 pipe
gdm        4657       root    8w      REG        3,1  200079    4079624 /home/bemorder/.xsession-errors
gdm        4657       root    9r     FIFO        0,6              16950 pipe
gdm        4657       root   10r     FIFO        0,6              16944 pipe
gdm        4657       root   11w     FIFO        0,6              16944 pipe
Xorg       4664       root  cwd       DIR        3,1    4096    2572292 /etc/X11
Xorg       4664       root  rtd       DIR        3,1    4096          2 /
Xorg       4664       root  txt       REG        3,1 1739480    5866491 /usr/bin/Xorg
Xorg       4664       root  DEL       REG        0,9             524303 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             491534 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             655376 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             458765 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             425996 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             393227 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             360458 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             262151 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             229382 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             196613 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             753668 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             917522 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             950291 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             884745 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             851976 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             819217 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9             720899 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9              98306 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9              65537 /SYSV00000000
Xorg       4664       root  DEL       REG        0,9              32768 /SYSV00000000
Xorg       4664       root  mem       REG        3,1 2425208    6049842 /usr/lib/xorg/modules/extensions/libGLcore.so
Xorg       4664       root  mem       CHR        1,1               2740 /dev/mem
Xorg       4664       root  mem       REG        3,1  256577    6046977 /usr/lib/xorg/modules/libfb.so
Xorg       4664       root  mem       REG        3,1   21880    6046982 /usr/lib/xorg/modules/libshadow.so
Xorg       4664       root  mem       REG        3,1  154980    6046978 /usr/lib/xorg/modules/libint10.so
Xorg       4664       root  mem       REG        3,1   22496    6046984 /usr/lib/xorg/modules/libvbe.so
Xorg       4664       root  mem       REG        3,1   37692    6046018 /usr/lib/xorg/modules/input/synaptics_drv.so
Xorg       4664       root  mem       REG        3,1   73884    6046019 /usr/lib/xorg/modules/input/wacom_drv.so
Xorg       4664       root  mem       REG        3,1   41772    6046017 /usr/lib/xorg/modules/input/mouse_drv.so
Xorg       4664       root  mem       REG        3,1   24524    6046016 /usr/lib/xorg/modules/input/kbd_drv.so
Xorg       4664       root  mem       REG        3,1   34444    5866923 /usr/lib/libdrm.so.2.3.0
Xorg       4664       root  mem       REG        3,1   24100    6046000 /usr/lib/xorg/modules/drivers/vesa_drv.so
Xorg       4664       root  mem       REG        3,1   35862    6049838 /usr/lib/xorg/modules/extensions/libdri.so
Xorg       4664       root  mem       REG        3,1   28021    6049849 /usr/lib/xorg/modules/extensions/librecord.so
Xorg       4664       root  mem       REG        3,1  424370    6049843 /usr/lib/xorg/modules/extensions/libglx.so
Xorg       4664       root  mem       REG        3,1  147972    6049841 /usr/lib/xorg/modules/extensions/libextmod.so
Xorg       4664       root  mem       REG        3,1  877427    6046980 /usr/lib/xorg/modules/libpcidata.so
Xorg       4664       root  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
Xorg       4664       root  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
Xorg       4664       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
Xorg       4664       root  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
Xorg       4664       root  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
Xorg       4664       root  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
Xorg       4664       root  mem       REG        3,1   20116    5866967 /usr/lib/libfontenc.so.1.0.0
Xorg       4664       root  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
Xorg       4664       root  mem       REG        3,1  395892    5866781 /usr/lib/libXfont.so.1.4.1
Xorg       4664       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
Xorg       4664       root  mem       REG        3,1    4445    6049859 /usr/lib/xorg/modules/fonts/libtype1.so
Xorg       4664       root  mem       REG        3,1    4461    6049858 /usr/lib/xorg/modules/fonts/libfreetype.so
Xorg       4664       root  mem       REG        3,1   19355    6049837 /usr/lib/xorg/modules/extensions/libdbe.so
Xorg       4664       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
Xorg       4664       root    0r      REG        3,1   55157     786498 /var/log/Xorg.0.log
Xorg       4664       root    1u     unix 0xc18b0700              15017 /tmp/.X11-unix/X0
Xorg       4664       root    2u      REG        3,1    1281     835710 /var/log/gdm/:0.log
Xorg       4664       root    3r     unix 0xf465de00              15028 socket
Xorg       4664       root    4w      CHR        4,7               2510 /dev/tty7
Xorg       4664       root    5w      REG        0,3     256 4026531995 /proc/bus/pci/01/00.0
Xorg       4664       root    6w      REG        0,3       0 4026531913 /proc/mtrr
Xorg       4664       root    7r      CHR      13,63               3995 /dev/input/mice
Xorg       4664       root    8u      CHR      13,67              13560 /dev/input/event3
Xorg       4664       root    9r     unix 0xf465d1c0              16496 /tmp/.X11-unix/X0
Xorg       4664       root   10u     unix 0xf173fc40              17017 /tmp/.X11-unix/X0
Xorg       4664       root   11u     unix 0xf22be380              17352 /tmp/.X11-unix/X0
Xorg       4664       root   12u     unix 0xf2331e00              17395 /tmp/.X11-unix/X0
Xorg       4664       root   13u     unix 0xf1c811c0              17525 /tmp/.X11-unix/X0
Xorg       4664       root   14u     unix 0xf0c3ba80              17714 /tmp/.X11-unix/X0
Xorg       4664       root   15u     unix 0xf0dc1700              17792 /tmp/.X11-unix/X0
Xorg       4664       root   16u     unix 0xf08aac40              17819 /tmp/.X11-unix/X0
Xorg       4664       root   17u     unix 0xd02be540              20983 /tmp/.X11-unix/X0
Xorg       4664       root   18u     unix 0xf0b7ca80              17849 /tmp/.X11-unix/X0
Xorg       4664       root   19u     unix 0xf0689e00              17910 /tmp/.X11-unix/X0
Xorg       4664       root   20u     unix 0xf0689000              17994 /tmp/.X11-unix/X0
Xorg       4664       root   21u     unix 0xf03aa380              18007 /tmp/.X11-unix/X0
Xorg       4664       root   22u     unix 0xf15728c0              18133 /tmp/.X11-unix/X0
Xorg       4664       root   23u     unix 0xeea4f1c0              18151 /tmp/.X11-unix/X0
Xorg       4664       root   24u     unix 0xf0561700              19282 /tmp/.X11-unix/X0
Xorg       4664       root   25u     unix 0xecb12540              19226 /tmp/.X11-unix/X0
Xorg       4664       root   26u     unix 0xef8fb000              19557 /tmp/.X11-unix/X0
Xorg       4664       root   27u     unix 0xeda8e1c0              19968 /tmp/.X11-unix/X0
Xorg       4664       root   28u     unix 0xed364a80              21332 /tmp/.X11-unix/X0
Xorg       4664       root   29u     unix 0xe8c61c40              20270 /tmp/.X11-unix/X0
Xorg       4664       root   30u     unix 0xe2c96a80              20445 /tmp/.X11-unix/X0
Xorg       4664       root   31u     unix 0xef8fb540              21376 /tmp/.X11-unix/X0
Xorg       4664       root   32u     unix 0xf726e380              22105 /tmp/.X11-unix/X0
cupsd      4698     cupsys  cwd       DIR        3,1    4096          2 /
cupsd      4698     cupsys  rtd       DIR        3,1    4096          2 /
cupsd      4698     cupsys  txt       REG        3,1  349564    5865548 /usr/sbin/cupsd
cupsd      4698     cupsys  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
cupsd      4698     cupsys  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
cupsd      4698     cupsys  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
cupsd      4698     cupsys  mem       REG        3,1   89120    5867420 /usr/lib/libsasl2.so.2.0.22
cupsd      4698     cupsys  mem       REG        3,1   47212    5867256 /usr/lib/liblber.so.2.0.130
cupsd      4698     cupsys  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
cupsd      4698     cupsys  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
cupsd      4698     cupsys  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
cupsd      4698     cupsys  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
cupsd      4698     cupsys  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
cupsd      4698     cupsys  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
cupsd      4698     cupsys  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
cupsd      4698     cupsys  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
cupsd      4698     cupsys  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
cupsd      4698     cupsys  mem       REG        3,1  197292    5867015 /usr/lib/libcups.so.2
cupsd      4698     cupsys  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
cupsd      4698     cupsys  mem       REG        3,1    8336    5867362 /usr/lib/libpaper.so.1.1.2
cupsd      4698     cupsys  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
cupsd      4698     cupsys  mem       REG        3,1   30596    4735077 /lib/libpam.so.0.79
cupsd      4698     cupsys  mem       REG        3,1  217924    5867262 /usr/lib/libldap_r.so.2.0.130
cupsd      4698     cupsys  mem       REG        3,1   60548    5867438 /usr/lib/libslp.so.1.0.1
cupsd      4698     cupsys  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
cupsd      4698     cupsys  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
cupsd      4698     cupsys  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
cupsd      4698     cupsys    0r      CHR        1,9               4047 /dev/urandom
cupsd      4698     cupsys    1u     IPv4      15117                TCP localhost:ipp (LISTEN)
cupsd      4698     cupsys    2u     unix 0xf4339a80              15118 /var/run/cups/cups.sock
cupsd      4698     cupsys    3r     FIFO        0,6              15120 pipe
cupsd      4698     cupsys    4w     FIFO        0,6              15120 pipe
cupsd      4698     cupsys    5u     unix 0xecab3380              18215 /var/run/cups/cups.sock
hpiod      4722       root  cwd       DIR        3,1    4096          2 /
hpiod      4722       root  rtd       DIR        3,1    4096          2 /
hpiod      4722       root  txt       REG        3,1  107008    5867614 /usr/sbin/hpiod
hpiod      4722       root  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
hpiod      4722       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hpiod      4722       root  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
hpiod      4722       root  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
hpiod      4722       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
hpiod      4722       root  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
hpiod      4722       root  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
hpiod      4722       root  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
hpiod      4722       root  mem       REG        3,1 1305220    5947677 /usr/lib/i686/cmov/libcrypto.so.0.9.8
hpiod      4722       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hpiod      4722       root  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
hpiod      4722       root  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
hpiod      4722       root  mem       REG        3,1  970680    5865600 /usr/lib/libstdc++.so.6.0.9
hpiod      4722       root  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
hpiod      4722       root  mem       REG        3,1   28376    4735107 /lib/libusb-0.1.so.4.4.4
hpiod      4722       root  mem       REG        3,1  197292    5867015 /usr/lib/libcups.so.2
hpiod      4722       root  mem       REG        3,1  587004    5867305 /usr/lib/libnetsnmp.so.10.0.1
hpiod      4722       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hpiod      4722       root    0u     IPv4      15148                TCP localhost:2208 (LISTEN)
hpiod      4722       root    1u     unix 0xdfb9e1c0              15150 socket
hpiod      4722       root    3u      REG       0,16       5      15147 /var/run/hplip/hpiod.pid
python     4725      hplip  cwd       DIR        3,1    4096          2 /
python     4725      hplip  rtd       DIR        3,1    4096          2 /
python     4725      hplip  txt       REG        3,1 1157620    5866335 /usr/bin/python2.5
python     4725      hplip  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
python     4725      hplip  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
python     4725      hplip  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
python     4725      hplip  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
python     4725      hplip  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
python     4725      hplip  mem       REG        3,1  197292    5867015 /usr/lib/libcups.so.2
python     4725      hplip  mem       REG        3,1   25216    6014557 /usr/lib/python-support/hplip/python2.5/cupsext.so
python     4725      hplip  mem       REG        3,1   18256    6030257 /usr/lib/python2.5/lib-dynload/zlib.so
python     4725      hplip  mem       REG        3,1    8060    6030248 /usr/lib/python2.5/lib-dynload/resource.so
python     4725      hplip  mem       REG        3,1   15556    6030254 /usr/lib/python2.5/lib-dynload/termios.so
python     4725      hplip  mem       REG        3,1  154492    6030907 /usr/lib/python2.5/site-packages/_xmlplus/parsers/pyexpat.so
python     4725      hplip  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
python     4725      hplip  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
python     4725      hplip  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
python     4725      hplip  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
python     4725      hplip  mem       REG        3,1   24772    6030218 /usr/lib/python2.5/lib-dynload/_struct.so
python     4725      hplip  mem       REG        3,1   17016    6030226 /usr/lib/python2.5/lib-dynload/cStringIO.so
python     4725      hplip  mem       REG        3,1   21556    6030252 /usr/lib/python2.5/lib-dynload/strop.so
python     4725      hplip  mem       REG        3,1   25332    6030243 /usr/lib/python2.5/lib-dynload/operator.so
python     4725      hplip  mem       REG        3,1 1305220    5947677 /usr/lib/i686/cmov/libcrypto.so.0.9.8
python     4725      hplip  mem       REG        3,1  261004    5947678 /usr/lib/i686/cmov/libssl.so.0.9.8
python     4725      hplip  mem       REG        3,1    5764    6030253 /usr/lib/python2.5/lib-dynload/syslog.so
python     4725      hplip  mem       REG        3,1   15700    6030211 /usr/lib/python2.5/lib-dynload/_locale.so
python     4725      hplip  mem       REG        3,1   10308    6030214 /usr/lib/python2.5/lib-dynload/_random.so
python     4725      hplip  mem       REG        3,1   16676    6030223 /usr/lib/python2.5/lib-dynload/binascii.so
python     4725      hplip  mem       REG        3,1   12976    6030240 /usr/lib/python2.5/lib-dynload/math.so
python     4725      hplip  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
python     4725      hplip  mem       REG        3,1   21056    6030228 /usr/lib/python2.5/lib-dynload/collections.so
python     4725      hplip  mem       REG        3,1   16480    6030255 /usr/lib/python2.5/lib-dynload/time.so
python     4725      hplip  mem       REG        3,1   54200    6030215 /usr/lib/python2.5/lib-dynload/_socket.so
python     4725      hplip  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
python     4725      hplip  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
python     4725      hplip  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
python     4725      hplip  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
python     4725      hplip  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
python     4725      hplip  mem       REG        3,1   13476    6030233 /usr/lib/python2.5/lib-dynload/fcntl.so
python     4725      hplip  mem       REG        3,1   12628    6030250 /usr/lib/python2.5/lib-dynload/select.so
python     4725      hplip  mem       REG        3,1   15392    6030217 /usr/lib/python2.5/lib-dynload/_ssl.so
python     4725      hplip  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
python     4725      hplip    0r      CHR        1,3               8184 /dev/null
python     4725      hplip    1u      CHR        1,3               8184 /dev/null
python     4725      hplip    2u      CHR        1,3               8184 /dev/null
python     4725      hplip    3u      REG       0,16       5      15158 /var/run/hplip/hpssd.pid
python     4725      hplip    4u     IPv4      15159                TCP localhost:2207 (LISTEN)
avahi-dae  4830      avahi  cwd       DIR        3,1    4096    2572298 /etc/avahi
avahi-dae  4830      avahi  rtd       DIR        3,1    4096    2572298 /etc/avahi
avahi-dae  4830      avahi  txt       REG        3,1  110348    5867545 /usr/sbin/avahi-daemon
avahi-dae  4830      avahi  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
avahi-dae  4830      avahi  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
avahi-dae  4830      avahi  mem       REG        3,1   11088    4735019 /lib/libcap.so.1.10
avahi-dae  4830      avahi  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
avahi-dae  4830      avahi  mem       REG        3,1   14720    5866893 /usr/lib/libdaemon.so.0.2.4
avahi-dae  4830      avahi  mem       REG        3,1  201516    5866843 /usr/lib/libavahi-core.so.5.0.2
avahi-dae  4830      avahi  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
avahi-dae  4830      avahi  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
avahi-dae  4830      avahi    0r      CHR        1,3               8184 /dev/null
avahi-dae  4830      avahi    1w      CHR        1,3               8184 /dev/null
avahi-dae  4830      avahi    2w      CHR        1,3               8184 /dev/null
avahi-dae  4830      avahi    5u     unix 0xf4339000              15248 socket
avahi-dae  4830      avahi    6u     unix 0xf4339540              15250 socket
avahi-dae  4830      avahi    7r     FIFO        0,6              15252 pipe
avahi-dae  4830      avahi    8w     FIFO        0,6              15252 pipe
avahi-dae  4830      avahi    9r     FIFO        0,6              15253 pipe
avahi-dae  4830      avahi   10w     FIFO        0,6              15253 pipe
avahi-dae  4830      avahi   11u     unix 0xf5a331c0              15254 /var/run/avahi-daemon/socket
avahi-dae  4830      avahi   12u     unix 0xf30b1700              15256 socket
avahi-dae  4830      avahi   13r      DIR       0,10       0          1 inotify
avahi-dae  4830      avahi   14u     IPv4      15258                UDP *:mdns 
avahi-dae  4830      avahi   15u     IPv4      15259                UDP *:32768 
avahi-dae  4830      avahi   16u     sock        0,5              15260 can't identify protocol
avahi-dae  4831      avahi  cwd       DIR        3,1    4096          2 /
avahi-dae  4831      avahi  rtd       DIR        3,1    4096          2 /
avahi-dae  4831      avahi  txt       REG        3,1  110348    5867545 /usr/sbin/avahi-daemon
avahi-dae  4831      avahi  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
avahi-dae  4831      avahi  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
avahi-dae  4831      avahi  mem       REG        3,1   11088    4735019 /lib/libcap.so.1.10
avahi-dae  4831      avahi  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
avahi-dae  4831      avahi  mem       REG        3,1   14720    5866893 /usr/lib/libdaemon.so.0.2.4
avahi-dae  4831      avahi  mem       REG        3,1  201516    5866843 /usr/lib/libavahi-core.so.5.0.2
avahi-dae  4831      avahi  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
avahi-dae  4831      avahi  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
avahi-dae  4831      avahi    0r      CHR        1,3               8184 /dev/null
avahi-dae  4831      avahi    1w      CHR        1,3               8184 /dev/null
avahi-dae  4831      avahi    2w      CHR        1,3               8184 /dev/null
avahi-dae  4831      avahi    5u     unix 0xf4339000              15248 socket
avahi-dae  4831      avahi    7u     unix 0xf43391c0              15251 socket
dhcdbd     4845       root  cwd       DIR        3,1    4096          2 /
dhcdbd     4845       root  rtd       DIR        3,1    4096          2 /
dhcdbd     4845       root  txt       REG        3,1  116508    5867570 /usr/sbin/dhcdbd
dhcdbd     4845       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dhcdbd     4845       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
dhcdbd     4845       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dhcdbd     4845       root    0u      CHR        1,3               8184 /dev/null
dhcdbd     4845       root    1u      CHR        1,3               8184 /dev/null
dhcdbd     4845       root    2u      CHR        1,3               8184 /dev/null
dhcdbd     4845       root    3u     unix 0xf315da80              15264 socket
dhcdbd     4845       root    4u     unix 0xf315dc40              15267 socket
hald       4861  haldaemon  cwd       DIR        3,1    4096          2 /
hald       4861  haldaemon  rtd       DIR        3,1    4096          2 /
hald       4861  haldaemon  txt       REG        3,1  271044    5867532 /usr/sbin/hald
hald       4861  haldaemon  mem       REG        3,1  450308     786468 /var/cache/hald/fdi-cache
hald       4861  haldaemon  mem       REG        3,1   58046     786746 /var/lib/misc/usb.ids
hald       4861  haldaemon  mem       REG        3,1  428084    6050945 /usr/share/misc/pci.ids
hald       4861  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald       4861  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald       4861  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald       4861  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald       4861  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald       4861  haldaemon  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
hald       4861  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald       4861  haldaemon  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
hald       4861  haldaemon  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
hald       4861  haldaemon  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
hald       4861  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald       4861  haldaemon    0u      CHR        1,3               8184 /dev/null
hald       4861  haldaemon    1u      CHR        1,3               8184 /dev/null
hald       4861  haldaemon    2u      CHR        1,3               8184 /dev/null
hald       4861  haldaemon    3u     unix 0xf28608c0              16540 socket
hald       4861  haldaemon    4r      REG        0,3       0 4026532214 /proc/acpi/battery/BAT0/info
hald       4861  haldaemon    5r     FIFO        0,6              15280 pipe
hald       4861  haldaemon    6w     FIFO        0,6              15280 pipe
hald       4861  haldaemon    7u     unix 0xf315d1c0              15281 socket
hald       4861  haldaemon    8u     unix 0xf315d540              15282 socket
hald       4861  haldaemon    9u     unix 0xf33581c0              15284 socket
hald       4861  haldaemon   10u     unix 0xf33588c0              15287 socket
hald       4861  haldaemon   11u     unix 0xf3358a80              15292 socket
hald       4861  haldaemon   12r      REG        0,3       0      15294 /proc/4861/mounts
hald       4861  haldaemon   13r      DIR       0,10       0          1 inotify
hald       4861  haldaemon   14u     unix 0xf3270000              15735 socket
hald       4861  haldaemon   15u     unix 0xf3270c40              15739 socket
hald       4861  haldaemon   16u     unix 0xf2dcd000              15740 socket
hald       4861  haldaemon   17u     unix 0xf2dcd700              15741 socket
hald       4861  haldaemon   18u     unix 0xf2dcde00              16152 socket
hald       4861  haldaemon   19u     unix 0xf2e62540              15747 socket
hald-runn  4862       root  cwd       DIR        3,1    4096          2 /
hald-runn  4862       root  rtd       DIR        3,1    4096          2 /
hald-runn  4862       root  txt       REG        3,1   12556    5882484 /usr/lib/hal/hald-runner
hald-runn  4862       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-runn  4862       root  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
hald-runn  4862       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-runn  4862       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-runn  4862       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
hald-runn  4862       root  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
hald-runn  4862       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-runn  4862       root    0r      CHR        1,3               8184 /dev/null
hald-runn  4862       root    1u      CHR        1,3               8184 /dev/null
hald-runn  4862       root    2u      CHR        1,3               8184 /dev/null
hald-runn  4862       root    3u     unix 0xf3358540              15286 socket
hald-addo  4868  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4868  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4868  haldaemon  txt       REG        3,1   11668    5882475 /usr/lib/hal/hald-addon-keyboard
hald-addo  4868  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4868  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4868  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4868  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4868  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4868  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4868  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4868  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4868  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4868  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4868  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4868  haldaemon    3u     unix 0xf3270700              15694 socket
hald-addo  4868  haldaemon    4r      CHR      13,65              13000 /dev/input/event1
hald-addo  4869  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4869  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4869  haldaemon  txt       REG        3,1   11668    5882475 /usr/lib/hal/hald-addon-keyboard
hald-addo  4869  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4869  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4869  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4869  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4869  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4869  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4869  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4869  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4869  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4869  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4869  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4869  haldaemon    3u     unix 0xf3270a80              15712 socket
hald-addo  4869  haldaemon    4r      CHR      13,68              14468 /dev/input/event4
hald-addo  4870  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4870  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4870  haldaemon  txt       REG        3,1   11668    5882475 /usr/lib/hal/hald-addon-keyboard
hald-addo  4870  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4870  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4870  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4870  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4870  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4870  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4870  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4870  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4870  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4870  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4870  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4870  haldaemon    3u     unix 0xf3358c40              15719 socket
hald-addo  4870  haldaemon    4r      CHR      13,69              14490 /dev/input/event5
hald-addo  4871  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4871  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4871  haldaemon  txt       REG        3,1   11668    5882475 /usr/lib/hal/hald-addon-keyboard
hald-addo  4871  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4871  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4871  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4871  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4871  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4871  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4871  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4871  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4871  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4871  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4871  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4871  haldaemon    3u     unix 0xf2dcd380              15726 socket
hald-addo  4871  haldaemon    4r      CHR      13,70              14512 /dev/input/event6
hald-addo  4874  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4874  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4874  haldaemon  txt       REG        3,1   10916    5882478 /usr/lib/hal/hald-addon-acpi
hald-addo  4874  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4874  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4874  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4874  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4874  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4874  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4874  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4874  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4874  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4874  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4874  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4874  haldaemon    3u     unix 0xf2e62380              15738 socket
hald-addo  4874  haldaemon    4u     unix 0xf2e62700              15764 socket
hald-addo  4875  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4875  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4875  haldaemon  txt       REG        3,1   11668    5882475 /usr/lib/hal/hald-addon-keyboard
hald-addo  4875  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4875  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4875  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4875  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4875  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4875  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4875  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4875  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4875  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4875  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4875  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4875  haldaemon    3u     unix 0xf2e62c40              15767 socket
hald-addo  4875  haldaemon    4r      CHR      13,71              14541 /dev/input/event7
hald-addo  4885  haldaemon  cwd       DIR        3,1    4096    5882058 /usr/lib/hal
hald-addo  4885  haldaemon  rtd       DIR        3,1    4096          2 /
hald-addo  4885  haldaemon  txt       REG        3,1   16624    5882476 /usr/lib/hal/hald-addon-storage
hald-addo  4885  haldaemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
hald-addo  4885  haldaemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
hald-addo  4885  haldaemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
hald-addo  4885  haldaemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
hald-addo  4885  haldaemon  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
hald-addo  4885  haldaemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hald-addo  4885  haldaemon  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
hald-addo  4885  haldaemon  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hald-addo  4885  haldaemon  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
hald-addo  4885  haldaemon  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
hald-addo  4885  haldaemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hald-addo  4885  haldaemon    0r      CHR        1,3               8184 /dev/null
hald-addo  4885  haldaemon    1u      CHR        1,3               8184 /dev/null
hald-addo  4885  haldaemon    2u      CHR        1,3               8184 /dev/null
hald-addo  4885  haldaemon    3u     unix 0xf2860000              16491 socket
hald-addo  4885  haldaemon    4u     unix 0xf2860700              16493 socket
hcid       4926       root  cwd       DIR        3,1    4096          2 /
hcid       4926       root  rtd       DIR        3,1    4096          2 /
hcid       4926       root  txt       REG        3,1  203984    5866246 /usr/sbin/hcid
hcid       4926       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
hcid       4926       root  mem       REG        3,1   74808    5865504 /usr/lib/libbluetooth.so.2.7.0
hcid       4926       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
hcid       4926       root  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
hcid       4926       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
hcid       4926       root    0u      CHR        1,3               8184 /dev/null
hcid       4926       root    1u      CHR        1,3               8184 /dev/null
hcid       4926       root    2u      CHR        1,3               8184 /dev/null
hcid       4926       root    3u     unix 0xf173f8c0              16633 socket
hcid       4926       root    4u     sock        0,5              16634 can't identify protocol
hcid       4926       root    5r     FIFO        0,6              16703 pipe
hcid       4926       root    6w     FIFO        0,6              16703 pipe
hcid       4926       root    7u     unix 0xf1c81000              16704 socket
hcid       4926       root    8u     sock        0,5              16706 can't identify protocol
hcid       4926       root    9u     unix 0xf30b1e00              16719 /var/run/sdp
hcid       4926       root   10r      DIR       0,10       0          1 inotify
hcid       4926       root   11u     unix 0xf1c81c40              16721 socket
krfcommd   4954       root  cwd       DIR        3,1    4096          2 /
krfcommd   4954       root  rtd       DIR        3,1    4096          2 /
krfcommd   4954       root  txt   unknown                               /proc/4954/exe
atd        5016     daemon  cwd       DIR        3,1    4096     836836 /var/spool/cron/atjobs
atd        5016     daemon  rtd       DIR        3,1    4096          2 /
atd        5016     daemon  txt       REG        3,1   16040    5867543 /usr/sbin/atd
atd        5016     daemon  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
atd        5016     daemon  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
atd        5016     daemon  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
atd        5016     daemon  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
atd        5016     daemon  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
atd        5016     daemon  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
atd        5016     daemon  mem       REG        3,1   30596    4735077 /lib/libpam.so.0.79
atd        5016     daemon  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
atd        5016     daemon    0u      CHR        1,3               8184 /dev/null
atd        5016     daemon    1u      CHR        1,3               8184 /dev/null
atd        5016     daemon    2u      CHR        1,3               8184 /dev/null
atd        5016     daemon    3uW     REG       0,16       5      16793 /var/run/atd.pid
cron       5037       root  cwd       DIR        3,1    4096     836833 /var/spool/cron
cron       5037       root  rtd       DIR        3,1    4096          2 /
cron       5037       root  txt       REG        3,1   32192    5867555 /usr/sbin/cron
cron       5037       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
cron       5037       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
cron       5037       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
cron       5037       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
cron       5037       root  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
cron       5037       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
cron       5037       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
cron       5037       root  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
cron       5037       root  mem       REG        3,1   30596    4735077 /lib/libpam.so.0.79
cron       5037       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
cron       5037       root    0r      CHR        1,3               8184 /dev/null
cron       5037       root    1w      CHR        1,3               8184 /dev/null
cron       5037       root    2w      CHR        1,3               8184 /dev/null
cron       5037       root    3u      REG       0,16       5      16820 /var/run/crond.pid
x-session  5120   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
x-session  5120   bemorder  rtd       DIR        3,1    4096          2 /
x-session  5120   bemorder  txt       REG        3,1  140004    5865884 /usr/bin/gnome-session
x-session  5120   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
x-session  5120   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
x-session  5120   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
x-session  5120   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
x-session  5120   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
x-session  5120   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
x-session  5120   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
x-session  5120   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
x-session  5120   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
x-session  5120   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
x-session  5120   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
x-session  5120   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
x-session  5120   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
x-session  5120   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
x-session  5120   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
x-session  5120   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
x-session  5120   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
x-session  5120   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
x-session  5120   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
x-session  5120   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
x-session  5120   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
x-session  5120   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
x-session  5120   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
x-session  5120   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
x-session  5120   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
x-session  5120   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
x-session  5120   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
x-session  5120   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
x-session  5120   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
x-session  5120   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
x-session  5120   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
x-session  5120   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
x-session  5120   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
x-session  5120   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
x-session  5120   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
x-session  5120   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
x-session  5120   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
x-session  5120   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
x-session  5120   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
x-session  5120   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
x-session  5120   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
x-session  5120   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
x-session  5120   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
x-session  5120   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
x-session  5120   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
x-session  5120   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
x-session  5120   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
x-session  5120   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
x-session  5120   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
x-session  5120   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
x-session  5120   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
x-session  5120   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
x-session  5120   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
x-session  5120   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
x-session  5120   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
x-session  5120   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
x-session  5120   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
x-session  5120   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
x-session  5120   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
x-session  5120   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
x-session  5120   bemorder  mem       REG        3,1   27648    4735117 /lib/libwrap.so.0.7.6
x-session  5120   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
x-session  5120   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
x-session  5120   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
x-session  5120   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
x-session  5120   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
x-session  5120   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
x-session  5120   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
x-session  5120   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
x-session  5120   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
x-session  5120   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
x-session  5120   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
x-session  5120   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
x-session  5120   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
x-session  5120   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
x-session  5120   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
x-session  5120   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
x-session  5120   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
x-session  5120   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
x-session  5120   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
x-session  5120   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
x-session  5120   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
x-session  5120   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
x-session  5120   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
x-session  5120   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
x-session  5120   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
x-session  5120   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
x-session  5120   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
x-session  5120   bemorder    0r      CHR        1,3               8184 /dev/null
x-session  5120   bemorder    1w     FIFO        0,6              16950 pipe
x-session  5120   bemorder    2w     FIFO        0,6              16950 pipe
x-session  5120   bemorder    3u     unix 0xf173f700              17016 socket
x-session  5120   bemorder    4r     unix 0xf2dcda80              17036 socket
x-session  5120   bemorder    5w     FIFO        0,6              14963 pipe
x-session  5120   bemorder    6w     FIFO        0,6              17033 pipe
x-session  5120   bemorder    7r     FIFO        0,6              14967 pipe
x-session  5120   bemorder    8w     FIFO        0,6              17033 pipe
x-session  5120   bemorder    9r     FIFO        0,6              17034 pipe
x-session  5120   bemorder   10r     FIFO        0,6              17034 pipe
x-session  5120   bemorder   11w     FIFO        0,6              17035 pipe
x-session  5120   bemorder   12w     FIFO        0,6              17035 pipe
x-session  5120   bemorder   13u     unix 0xf2860a80              17037 /tmp/orbit-bemorder/linc-1400-0-36437c66eb8bc
x-session  5120   bemorder   14u     unix 0xf355c000              17283 /tmp/orbit-bemorder/linc-1400-0-36437c66eb8bc
x-session  5120   bemorder   15u     unix 0xf155d8c0              17299 /tmp/.ICE-unix/5120
x-session  5120   bemorder   16u     unix 0xf155da80              17324 socket
x-session  5120   bemorder   17w     FIFO        0,6              17302 pipe
x-session  5120   bemorder   18r     FIFO        0,6              17554 pipe
x-session  5120   bemorder   19w     FIFO        0,6              17554 pipe
x-session  5120   bemorder   20u     unix 0xf12b58c0              17685 socket
x-session  5120   bemorder   21u     unix 0xf0c3be00              17719 /tmp/.ICE-unix/5120
x-session  5120   bemorder   22u     unix 0xf0dc18c0              17797 /tmp/.ICE-unix/5120
x-session  5120   bemorder   23u     unix 0xf13378c0              17823 /tmp/.ICE-unix/5120
x-session  5120   bemorder   24u     unix 0xd02be380              20988 /tmp/.ICE-unix/5120
x-session  5120   bemorder   25u     unix 0xf0b7ce00              17961 /tmp/.ICE-unix/5120
x-session  5120   bemorder   26u     unix 0xf00a1000              17962 /tmp/.ICE-unix/5120
x-session  5120   bemorder   27u     unix 0xf03aa700              18012 /tmp/.ICE-unix/5120
x-session  5120   bemorder   28u     unix 0xf2331540              18138 /tmp/.ICE-unix/5120
x-session  5120   bemorder   29u     unix 0xeea4f540              18156 /tmp/.ICE-unix/5120
x-session  5120   bemorder   30u     unix 0xea7f7000              19287 /tmp/.ICE-unix/5120
x-session  5120   bemorder   31u     unix 0xe96b4c40              20002 /tmp/.ICE-unix/5120
x-session  5120   bemorder   32u     unix 0xe8c618c0              20275 /tmp/.ICE-unix/5120
ssh-agent  5158   bemorder  cwd       DIR        3,1    4096          2 /
ssh-agent  5158   bemorder  rtd       DIR        3,1    4096          2 /
ssh-agent  5158   bemorder  txt       REG        3,1   80688    5866460 /usr/bin/ssh-agent
ssh-agent  5158   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
ssh-agent  5158   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
ssh-agent  5158   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
ssh-agent  5158   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
ssh-agent  5158   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
ssh-agent  5158   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
ssh-agent  5158   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
ssh-agent  5158   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
ssh-agent  5158   bemorder  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
ssh-agent  5158   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
ssh-agent  5158   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
ssh-agent  5158   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
ssh-agent  5158   bemorder  mem       REG        3,1 1305220    5947677 /usr/lib/i686/cmov/libcrypto.so.0.9.8
ssh-agent  5158   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
ssh-agent  5158   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
ssh-agent  5158   bemorder    0u      CHR        1,3               8184 /dev/null
ssh-agent  5158   bemorder    1u      CHR        1,3               8184 /dev/null
ssh-agent  5158   bemorder    2u      CHR        1,3               8184 /dev/null
ssh-agent  5158   bemorder    3u     unix 0xf173f540              17011 /tmp/ssh-SgZnZB5120/agent.5120
ssh-agent  5158   bemorder    5w     FIFO        0,6              14963 pipe
ssh-agent  5158   bemorder    7r     FIFO        0,6              14967 pipe
gconfd-2   5160   bemorder  cwd       DIR        3,1    4096          2 /
gconfd-2   5160   bemorder  rtd       DIR        3,1    4096          2 /
gconfd-2   5160   bemorder  txt       REG        3,1   51672    5882381 /usr/lib/libgconf2-4/gconfd-2
gconfd-2   5160   bemorder  mem       REG        3,1   51544    5947815 /usr/lib/libgconf2-4/2/libgconfbackend-xml.so
gconfd-2   5160   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gconfd-2   5160   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gconfd-2   5160   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gconfd-2   5160   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gconfd-2   5160   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gconfd-2   5160   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gconfd-2   5160   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gconfd-2   5160   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gconfd-2   5160   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gconfd-2   5160   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gconfd-2   5160   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gconfd-2   5160   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gconfd-2   5160   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gconfd-2   5160   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gconfd-2   5160   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gconfd-2   5160   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gconfd-2   5160   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gconfd-2   5160   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gconfd-2   5160   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gconfd-2   5160   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gconfd-2   5160   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gconfd-2   5160   bemorder    0u      CHR        1,3               8184 /dev/null
gconfd-2   5160   bemorder    1u      CHR        1,3               8184 /dev/null
gconfd-2   5160   bemorder    2u      CHR        1,3               8184 /dev/null
gconfd-2   5160   bemorder    3u      CHR        1,3               8184 /dev/null
gconfd-2   5160   bemorder    4r     FIFO        0,6              17023 pipe
gconfd-2   5160   bemorder    5w     FIFO        0,6              17023 pipe
gconfd-2   5160   bemorder    6u     unix 0xf2860c40              17281 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder    7r     FIFO        0,6              17024 pipe
gconfd-2   5160   bemorder    8w     FIFO        0,6              17024 pipe
gconfd-2   5160   bemorder    9r     FIFO        0,6              17025 pipe
gconfd-2   5160   bemorder   10w     FIFO        0,6              17025 pipe
gconfd-2   5160   bemorder   11u     unix 0xdfb9e000              17027 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   12wW     REG        3,1     625    2392076 /tmp/gconfd-bemorder/lock/0t1184696545ut842881u1000p5160r1212177201k3217945336 (deleted)
gconfd-2   5160   bemorder   13u     unix 0xf726e700              22110 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   14u     unix 0xf355ca80              17282 socket
gconfd-2   5160   bemorder   15u     unix 0xf22be8c0              17357 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   16u     unix 0xf22bec40              17360 socket
gconfd-2   5160   bemorder   17u     unix 0xf1572c40              17534 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   18u     unix 0xf64dc1c0              17537 socket
gconfd-2   5160   bemorder   19u     unix 0xf13371c0              17722 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   20u     unix 0xf1337e00              17725 socket
gconfd-2   5160   bemorder   21u     unix 0xf0dc1e00              17800 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   22u     unix 0xf0c3b540              17803 socket
gconfd-2   5160   bemorder   23u     unix 0xf08aa380              17813 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   24u     unix 0xf08aa700              17816 socket
gconfd-2   5160   bemorder   25u     unix 0xd02bec40              20990 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   26u     unix 0xf0ad8380              20993 socket
gconfd-2   5160   bemorder   27u     unix 0xf0557700              17870 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   28u     unix 0xf05571c0              17873 socket
gconfd-2   5160   bemorder   29u     unix 0xf03841c0              17975 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   30u     unix 0xf0b7c380              17978 socket
gconfd-2   5160   bemorder   31u     unix 0xf0384540              17965 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   32u     unix 0xf03848c0              17968 socket
gconfd-2   5160   bemorder   33u     unix 0xf00a1700              17999 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   34u     unix 0xf00a1a80              18002 socket
gconfd-2   5160   bemorder   35u     unix 0xf03aaa80              18015 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   36u     unix 0xf03aae00              18018 socket
gconfd-2   5160   bemorder   37u     unix 0xf23318c0              18141 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   38u     unix 0xf1c81e00              18144 socket
gconfd-2   5160   bemorder   39u     unix 0xeea4f8c0              18159 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   40u     unix 0xeea4fc40              18162 socket
gconfd-2   5160   bemorder   41u     unix 0xecab3c40              18340 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   42u     unix 0xec7a2000              18343 socket
gconfd-2   5160   bemorder   43u     unix 0xecb12e00              19231 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   44u     unix 0xeccce1c0              19234 socket
gconfd-2   5160   bemorder   45u     unix 0xea7f7380              19290 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   46u     unix 0xea7f7700              19293 socket
gconfd-2   5160   bemorder   47u     unix 0xed4698c0              19562 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   48u     unix 0xec7a2c40              19565 socket
gconfd-2   5160   bemorder   49u     unix 0xe96b4380              21337 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   50u     unix 0xe8c61e00              20278 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   51u     unix 0xe96b4e00              20281 socket
gconfd-2   5160   bemorder   52u     unix 0xe2c96e00              20456 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   53u     unix 0xe331aa80              20459 socket
gconfd-2   5160   bemorder   54u     unix 0xec7a2380              20838 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   55u     unix 0xec7a21c0              20841 socket
gconfd-2   5160   bemorder   56u     unix 0xe96b4540              21340 socket
gconfd-2   5160   bemorder   57u     unix 0xe3dcbc40              21383 /tmp/orbit-bemorder/linc-1428-0-48d5cfa4cdbbb
gconfd-2   5160   bemorder   58u     unix 0xc2a231c0              21386 socket
gconfd-2   5160   bemorder   59u     unix 0xf726ea80              22113 socket
gnome-key  5163   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
gnome-key  5163   bemorder  rtd       DIR        3,1    4096          2 /
gnome-key  5163   bemorder  txt       REG        3,1   96712    5865793 /usr/bin/gnome-keyring-daemon
gnome-key  5163   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-key  5163   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-key  5163   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-key  5163   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-key  5163   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-key  5163   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-key  5163   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-key  5163   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-key  5163   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-key  5163   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-key  5163   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-key  5163   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-key  5163   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-key  5163   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-key  5163   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-key  5163   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-key  5163   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-key  5163   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-key  5163   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-key  5163   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-key  5163   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-key  5163   bemorder    0r      CHR        1,3               8184 /dev/null
gnome-key  5163   bemorder    1w      CHR        1,3               8184 /dev/null
gnome-key  5163   bemorder    2w     FIFO        0,6              16950 pipe
gnome-key  5163   bemorder    3u     unix 0xf155d540              17308 /tmp/keyring-ScbG33/socket
gnome-key  5163   bemorder    4r     FIFO        0,6              17310 pipe
gnome-key  5163   bemorder    5w     FIFO        0,6              17310 pipe
gnome-key  5163   bemorder    6r     FIFO        0,6              17311 pipe
gnome-key  5163   bemorder    7u     unix 0xf155d700              17312 socket
gnome-key  5163   bemorder   13r     FIFO        0,6              21114 pipe
gnome-key  5163   bemorder   16r     FIFO        0,6              17302 pipe
dbus-daem  5166   bemorder  cwd       DIR        3,1    4096          2 /
dbus-daem  5166   bemorder  rtd       DIR        3,1    4096          2 /
dbus-daem  5166   bemorder  txt       REG        3,1  302692    5865655 /usr/bin/dbus-daemon
dbus-daem  5166   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
dbus-daem  5166   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
dbus-daem  5166   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
dbus-daem  5166   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
dbus-daem  5166   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dbus-daem  5166   bemorder    0u      CHR        1,3               8184 /dev/null
dbus-daem  5166   bemorder    1u      CHR        1,3               8184 /dev/null
dbus-daem  5166   bemorder    2u      CHR        1,3               8184 /dev/null
dbus-daem  5166   bemorder    3u     unix 0xf155d380              17321 socket
dbus-daem  5166   bemorder    4u      CHR        1,3               8184 /dev/null
dbus-daem  5166   bemorder    5u     unix 0xf355c1c0              17322 socket
dbus-daem  5166   bemorder    6u     unix 0xf355c540              17323 socket
dbus-daem  5166   bemorder    7u     unix 0xf155dc40              17325 socket
dbus-daem  5166   bemorder    8u     unix 0xf1c818c0              17540 socket
dbus-daem  5166   bemorder    9u     unix 0xf2331700              17393 socket
dbus-daem  5166   bemorder   10u     unix 0xf0ad8000              21000 socket
dbus-daem  5166   bemorder   11u     unix 0xf06898c0              17981 socket
dbus-daem  5166   bemorder   12u     unix 0xf0557e00              17866 socket
dbus-daem  5166   bemorder   13u     unix 0xefe33c40              18024 socket
dbus-daem  5166   bemorder   14u     unix 0xf00a11c0              18027 socket
dbus-daem  5166   bemorder   15u     unix 0xee003540              18173 socket
dbus-daem  5166   bemorder   16u     unix 0xecccee00              19241 socket
dbus-daem  5166   bemorder   17u     unix 0xea656c40              19263 socket
dbus-daem  5166   bemorder   18u     unix 0xeda8ea80              19971 socket
dbus-daem  5166   bemorder   19u     unix 0xc26a01c0              21422 socket
dbus-daem  5166   bemorder   21u     unix 0xc21aa000              22122 socket
gnome-set  5168   bemorder  cwd       DIR        3,1    4096          2 /
gnome-set  5168   bemorder  rtd       DIR        3,1    4096          2 /
gnome-set  5168   bemorder  txt       REG        3,1  172796    6229690 /usr/lib/gnome-control-center/gnome-settings-daemon
gnome-set  5168   bemorder  DEL       REG        0,9             819217 /SYSV00000000
gnome-set  5168   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-set  5168   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
gnome-set  5168   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
gnome-set  5168   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-set  5168   bemorder  mem       REG        3,1   81100    6438919 /usr/lib/gstreamer-0.10/libgstalsa.so
gnome-set  5168   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
gnome-set  5168   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
gnome-set  5168   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
gnome-set  5168   bemorder  mem       REG        3,1   19492    6438915 /usr/lib/gstreamer-0.10/libgstadder.so
gnome-set  5168   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
gnome-set  5168   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-set  5168   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-set  5168   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-set  5168   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-set  5168   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-set  5168   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-set  5168   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-set  5168   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-set  5168   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-set  5168   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-set  5168   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-set  5168   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-set  5168   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-set  5168   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-set  5168   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-set  5168   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-set  5168   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-set  5168   bemorder  mem       REG        3,1  148140    5867135 /usr/lib/libgstbase-0.10.so.0.12.0
gnome-set  5168   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-set  5168   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-set  5168   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-set  5168   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-set  5168   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-set  5168   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-set  5168   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-set  5168   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-set  5168   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
gnome-set  5168   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-set  5168   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-set  5168   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
gnome-set  5168   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
gnome-set  5168   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
gnome-set  5168   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
gnome-set  5168   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-set  5168   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-set  5168   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-set  5168   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-set  5168   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-set  5168   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
gnome-set  5168   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
gnome-set  5168   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
gnome-set  5168   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
gnome-set  5168   bemorder  mem       REG        3,1  134292    5867513 /usr/lib/libxkbfile.so.1.0.2
gnome-set  5168   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-set  5168   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-set  5168   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-set  5168   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-set  5168   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-set  5168   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-set  5168   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-set  5168   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-set  5168   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-set  5168   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-set  5168   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-set  5168   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-set  5168   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-set  5168   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-set  5168   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-set  5168   bemorder  mem       REG        3,1  101608    5867133 /usr/lib/libgstaudio-0.10.so.0.9.0
gnome-set  5168   bemorder  mem       REG        3,1   32012    5867145 /usr/lib/libgstinterfaces-0.10.so.0.9.0
gnome-set  5168   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-set  5168   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-set  5168   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-set  5168   bemorder  mem       REG        3,1  650160    5867153 /usr/lib/libgstreamer-0.10.so.0.12.0
gnome-set  5168   bemorder  mem       REG        3,1    8992    5866811 /usr/lib/libXxf86misc.so.1.1.0
gnome-set  5168   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-set  5168   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-set  5168   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-set  5168   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-set  5168   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-set  5168   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
gnome-set  5168   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-set  5168   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
gnome-set  5168   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-set  5168   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
gnome-set  5168   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
gnome-set  5168   bemorder  mem       REG        3,1   95736    5867515 /usr/lib/libxklavier.so.11.0.0
gnome-set  5168   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-set  5168   bemorder  mem       REG        3,1   32020    5867083 /usr/lib/libgnomekbd.so.1.0.0
gnome-set  5168   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-set  5168   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-set  5168   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-set  5168   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-set  5168   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-set  5168   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-set  5168   bemorder    0u      CHR        1,3               8184 /dev/null
gnome-set  5168   bemorder    1u      CHR        1,3               8184 /dev/null
gnome-set  5168   bemorder    2u      CHR        1,3               8184 /dev/null
gnome-set  5168   bemorder    3u     unix 0xf22be1c0              17351 socket
gnome-set  5168   bemorder    4u      CHR        1,3               8184 /dev/null
gnome-set  5168   bemorder    5r     FIFO        0,6              17353 pipe
gnome-set  5168   bemorder    6w     FIFO        0,6              17353 pipe
gnome-set  5168   bemorder    7r     FIFO        0,6              17354 pipe
gnome-set  5168   bemorder    8w     FIFO        0,6              17354 pipe
gnome-set  5168   bemorder    9r     FIFO        0,6              17355 pipe
gnome-set  5168   bemorder   10w     FIFO        0,6              17355 pipe
gnome-set  5168   bemorder   11u     unix 0xf22be540              17356 socket
gnome-set  5168   bemorder   12u     unix 0xf22bea80              17358 /tmp/orbit-bemorder/linc-1430-0-255afc7a2ffbf
gnome-set  5168   bemorder   13u     unix 0xf22bee00              17361 /tmp/orbit-bemorder/linc-1430-0-255afc7a2ffbf
gnome-set  5168   bemorder   14u     unix 0xf2331380              17392 socket
gnome-set  5168   bemorder   15u     unix 0xf2331c40              17394 socket
gnome-set  5168   bemorder   16r     FIFO        0,6              17444 pipe
gnome-set  5168   bemorder   17w     FIFO        0,6              17444 pipe
gnome-set  5168   bemorder   18r      DIR       0,10       0          1 inotify
gnome-set  5168   bemorder   19r     FIFO        0,6              17472 pipe
gnome-set  5168   bemorder   20w     FIFO        0,6              17472 pipe
gnome-set  5168   bemorder   22u     unix 0xed364540              21243 socket
gnome-scr  5379   bemorder  cwd       DIR        3,1    4096          2 /
gnome-scr  5379   bemorder  rtd       DIR        3,1    4096          2 /
gnome-scr  5379   bemorder  txt       REG        3,1  131364    5865923 /usr/bin/gnome-screensaver
gnome-scr  5379   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-scr  5379   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-scr  5379   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-scr  5379   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-scr  5379   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-scr  5379   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-scr  5379   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-scr  5379   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-scr  5379   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-scr  5379   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-scr  5379   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-scr  5379   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-scr  5379   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-scr  5379   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-scr  5379   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-scr  5379   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-scr  5379   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-scr  5379   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-scr  5379   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-scr  5379   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-scr  5379   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-scr  5379   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-scr  5379   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-scr  5379   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-scr  5379   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-scr  5379   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-scr  5379   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-scr  5379   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1    8992    5866811 /usr/lib/libXxf86misc.so.1.1.0
gnome-scr  5379   bemorder  mem       REG        3,1   16220    5866813 /usr/lib/libXxf86vm.so.1.0.0
gnome-scr  5379   bemorder  mem       REG        3,1    7472    5866801 /usr/lib/libXss.so.1.0.0
gnome-scr  5379   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-scr  5379   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-scr  5379   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-scr  5379   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-scr  5379   bemorder  mem       REG        3,1   81488    5866936 /usr/lib/libgnome-menu.so.2.1.13
gnome-scr  5379   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-scr  5379   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-scr  5379   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-scr  5379   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-scr  5379   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-scr  5379   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-scr  5379   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-scr  5379   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-scr  5379   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-scr  5379   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-scr  5379   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-scr  5379   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-scr  5379   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-scr  5379   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-scr  5379   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-scr  5379   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-scr  5379   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-scr  5379   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-scr  5379   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-scr  5379   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-scr  5379   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-scr  5379   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-scr  5379   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-scr  5379   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-scr  5379   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-scr  5379   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-scr  5379   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-scr  5379   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-scr  5379   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-scr  5379   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-scr  5379   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-scr  5379   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-scr  5379   bemorder    0r      CHR        1,3               8184 /dev/null
gnome-scr  5379   bemorder    1u      CHR        1,3               8184 /dev/null
gnome-scr  5379   bemorder    2u      CHR        1,3               8184 /dev/null
gnome-scr  5379   bemorder    3u     unix 0xf1c81a80              17524 socket
gnome-scr  5379   bemorder    4r     FIFO        0,6              17530 pipe
gnome-scr  5379   bemorder    5w     FIFO        0,6              17530 pipe
gnome-scr  5379   bemorder    6r     FIFO        0,6              17531 pipe
gnome-scr  5379   bemorder    7w     FIFO        0,6              17531 pipe
gnome-scr  5379   bemorder    8r     FIFO        0,6              17532 pipe
gnome-scr  5379   bemorder    9w     FIFO        0,6              17532 pipe
gnome-scr  5379   bemorder   10u     unix 0xf1572000              17533 socket
gnome-scr  5379   bemorder   11u     unix 0xf315d380              17535 /tmp/orbit-bemorder/linc-1501-0-25de74a19292b
gnome-scr  5379   bemorder   12u     unix 0xf22be700              17538 /tmp/orbit-bemorder/linc-1501-0-25de74a19292b
gnome-scr  5379   bemorder   13u     unix 0xf22be000              17539 socket
gnome-scr  5379   bemorder   14u     unix 0xf1572380              17541 socket
esd        5383   bemorder  cwd       DIR        3,1    4096          2 /
esd        5383   bemorder  rtd       DIR        3,1    4096          2 /
esd        5383   bemorder  txt       REG        3,1   59640    5867072 /usr/bin/esd
esd        5383   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
esd        5383   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
esd        5383   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
esd        5383   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
esd        5383   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
esd        5383   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
esd        5383   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
esd        5383   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
esd        5383   bemorder  mem       REG        3,1   27648    4735117 /lib/libwrap.so.0.7.6
esd        5383   bemorder  mem       CHR      116,9              13700 /dev/snd/pcmC0D0p
esd        5383   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
esd        5383   bemorder    0u      CHR        1,3               8184 /dev/null
esd        5383   bemorder    1u      CHR        1,3               8184 /dev/null
esd        5383   bemorder    2u      CHR        1,3               8184 /dev/null
esd        5383   bemorder    3u     unix 0xf12b5540              17682 socket
esd        5383   bemorder    4u     unix 0xf12b5700              17683 /tmp/.esd/socket
esd        5383   bemorder    5u     unix 0xf12b5c40              17686 /tmp/.esd/socket
esd        5383   bemorder    6u      CHR      116,9              13700 /dev/snd/pcmC0D0p
esd        5383   bemorder    7u     unix 0xee0038c0              18175 /tmp/.esd/socket
esd        5383   bemorder    8u     unix 0xef8fbc40              18296 /tmp/.esd/socket
esd        5383   bemorder    9u     unix 0xea6568c0              19253 /tmp/.esd/socket
esd        5383   bemorder   10u     unix 0xf0b7c000              21015 /tmp/.esd/socket
esd        5383   bemorder   11u     unix 0xec900e00              19454 /tmp/.esd/socket
esd        5383   bemorder   12u     unix 0xeda8e000              19582 /tmp/.esd/socket
esd        5383   bemorder   13u     unix 0xe3dcb540              20299 /tmp/.esd/socket
esd        5383   bemorder   14u     unix 0xed3641c0              21244 /tmp/.esd/socket
esd        5383   bemorder   15u     unix 0xecab3700              21358 /tmp/.esd/socket
metacity   5385   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
metacity   5385   bemorder  rtd       DIR        3,1    4096          2 /
metacity   5385   bemorder  txt       REG        3,1  476776    5866152 /usr/bin/metacity
metacity   5385   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
metacity   5385   bemorder  DEL       REG        0,9             393227 /SYSV00000000
metacity   5385   bemorder  DEL       REG        0,9             360458 /SYSV00000000
metacity   5385   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
metacity   5385   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
metacity   5385   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
metacity   5385   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
metacity   5385   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
metacity   5385   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
metacity   5385   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
metacity   5385   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
metacity   5385   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
metacity   5385   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
metacity   5385   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
metacity   5385   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
metacity   5385   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
metacity   5385   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
metacity   5385   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
metacity   5385   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
metacity   5385   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
metacity   5385   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
metacity   5385   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
metacity   5385   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
metacity   5385   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
metacity   5385   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
metacity   5385   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
metacity   5385   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
metacity   5385   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
metacity   5385   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
metacity   5385   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
metacity   5385   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
metacity   5385   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
metacity   5385   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
metacity   5385   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
metacity   5385   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
metacity   5385   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
metacity   5385   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
metacity   5385   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
metacity   5385   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
metacity   5385   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
metacity   5385   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
metacity   5385   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
metacity   5385   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
metacity   5385   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
metacity   5385   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
metacity   5385   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
metacity   5385   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
metacity   5385   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
metacity   5385   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
metacity   5385   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
metacity   5385   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
metacity   5385   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
metacity   5385   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
metacity   5385   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
metacity   5385   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
metacity   5385   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
metacity   5385   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
metacity   5385   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
metacity   5385   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
metacity   5385   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
metacity   5385   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
metacity   5385   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
metacity   5385   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
metacity   5385   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
metacity   5385   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
metacity   5385   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
metacity   5385   bemorder    0r      CHR        1,3               8184 /dev/null
metacity   5385   bemorder    1w     FIFO        0,6              16950 pipe
metacity   5385   bemorder    2w     FIFO        0,6              16950 pipe
metacity   5385   bemorder    3r     FIFO        0,6              17809 pipe
metacity   5385   bemorder    4w     FIFO        0,6              17809 pipe
metacity   5385   bemorder    5r     FIFO        0,6              17810 pipe
metacity   5385   bemorder    6w     FIFO        0,6              17810 pipe
metacity   5385   bemorder    7r     FIFO        0,6              17811 pipe
metacity   5385   bemorder    8w     FIFO        0,6              17811 pipe
metacity   5385   bemorder    9u     unix 0xf08aa1c0              17812 socket
metacity   5385   bemorder   10u     unix 0xf08aa540              17814 /tmp/orbit-bemorder/linc-1509-0-63cf07ca7e2be
metacity   5385   bemorder   11u     unix 0xf08aa8c0              17817 /tmp/orbit-bemorder/linc-1509-0-63cf07ca7e2be
metacity   5385   bemorder   12u     unix 0xf08aaa80              17818 socket
metacity   5385   bemorder   13u     unix 0xf08aae00              17822 socket
gnome-pan  5386   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
gnome-pan  5386   bemorder  rtd       DIR        3,1    4096          2 /
gnome-pan  5386   bemorder  txt       REG        3,1  509420    5865874 /usr/bin/gnome-panel
gnome-pan  5386   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
gnome-pan  5386   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
gnome-pan  5386   bemorder  mem       REG        3,1   60804    6050067 /usr/share/mime/mime.cache
gnome-pan  5386   bemorder  mem       REG        3,1   82328    5866849 /usr/lib/libbeagle.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   41724    5931744 /usr/lib/gtk-2.0/2.10.0/filesystems/libgnome-vfs.so
gnome-pan  5386   bemorder  mem       REG        3,1   58716    6096346 /usr/share/fonts/truetype/ttf-bitstream-vera/VeraBd.ttf
gnome-pan  5386   bemorder  mem       REG        3,1  204988    6096367 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
gnome-pan  5386   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
gnome-pan  5386   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
gnome-pan  5386   bemorder  mem       REG        3,1  309420    5867447 /usr/lib/libsoftokn3.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
gnome-pan  5386   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
gnome-pan  5386   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
gnome-pan  5386   bemorder  mem       REG        3,1  152912    5867457 /usr/lib/libssl3.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1  144328    5867441 /usr/lib/libsmime3.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1  462004    5867325 /usr/lib/libnss3.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1 1038208    5866898 /usr/lib/libdb-4.4.so
gnome-pan  5386   bemorder  mem       REG        3,1  193772    5867324 /usr/lib/libnspr4.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1   14332    5867378 /usr/lib/libplc4.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1  305520    5866934 /usr/lib/libcamel-1.2.so.10.0.1
gnome-pan  5386   bemorder  mem       REG        3,1  147812    5867066 /usr/lib/libedataserver-1.2.so.9.0.1
gnome-pan  5386   bemorder  mem       REG        3,1  204152    5866869 /usr/lib/libebook-1.2.so.9.1.0
gnome-pan  5386   bemorder  mem       REG        3,1  159764    5866928 /usr/lib/libedataserverui-1.2.so.8.0.2
gnome-pan  5386   bemorder  mem       REG        3,1  644084    5866926 /usr/lib/libecal-1.2.so.7.0.2
gnome-pan  5386   bemorder  mem       REG        3,1   37580    6291473 /usr/lib/gnome-panel/libnotification-area-applet.so
gnome-pan  5386   bemorder  mem       REG        3,1  160544    6291471 /usr/lib/gnome-panel/libclock-applet.so
gnome-pan  5386   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
gnome-pan  5386   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
gnome-pan  5386   bemorder  mem       REG        3,1    8232    5867379 /usr/lib/libplds4.so.0d
gnome-pan  5386   bemorder  mem       REG        3,1   18785    6291470 /usr/share/locale-langpack/en_US/LC_MESSAGES/gcalctool.mo
gnome-pan  5386   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
gnome-pan  5386   bemorder  mem       REG        3,1   24100    5932336 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
gnome-pan  5386   bemorder  mem       REG        3,1  219416    5866859 /usr/lib/libwnck-1.so.22.2.0
gnome-pan  5386   bemorder  mem       REG        3,1   54256    5866575 /usr/lib/libpanel-applet-2.so.0.2.21
gnome-pan  5386   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
gnome-pan  5386   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
gnome-pan  5386   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-pan  5386   bemorder  mem       REG        3,1   48176    6291474 /usr/lib/gnome-panel/libwnck-applet.so
gnome-pan  5386   bemorder  DEL       REG        0,9              65537 /SYSV00000000
gnome-pan  5386   bemorder  mem       REG        3,1   66276    4735016 /lib/libbz2.so.1.0.4
gnome-pan  5386   bemorder  mem       REG        3,1  203840    5866882 /usr/lib/libcroco-0.6.so.3.0.1
gnome-pan  5386   bemorder  mem       REG        3,1  210652    5867125 /usr/lib/libgsf-1.so.114.0.4
gnome-pan  5386   bemorder  mem       REG        3,1  192656    5867415 /usr/lib/librsvg-2.so.2.16.1
gnome-pan  5386   bemorder  mem       REG        3,1    5748    5866758 /usr/lib/libXRes.so.1.0.0
gnome-pan  5386   bemorder  mem       REG        3,1    7052    5867269 /usr/lib/liblpint-bonobo.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   15168    5898805 /usr/lib/bonobo/monikers/libmoniker_std_2.so
gnome-pan  5386   bemorder  mem       REG        3,1    5108    5931777 /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
gnome-pan  5386   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
gnome-pan  5386   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
gnome-pan  5386   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
gnome-pan  5386   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-pan  5386   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-pan  5386   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-pan  5386   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-pan  5386   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-pan  5386   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-pan  5386   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-pan  5386   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-pan  5386   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-pan  5386   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-pan  5386   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-pan  5386   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-pan  5386   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
gnome-pan  5386   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-pan  5386   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-pan  5386   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-pan  5386   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-pan  5386   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-pan  5386   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-pan  5386   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-pan  5386   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-pan  5386   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-pan  5386   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-pan  5386   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-pan  5386   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-pan  5386   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
gnome-pan  5386   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
gnome-pan  5386   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-pan  5386   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-pan  5386   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-pan  5386   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-pan  5386   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
gnome-pan  5386   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-pan  5386   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-pan  5386   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-pan  5386   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-pan  5386   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-pan  5386   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-pan  5386   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-pan  5386   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-pan  5386   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-pan  5386   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-pan  5386   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-pan  5386   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-pan  5386   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-pan  5386   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-pan  5386   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-pan  5386   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-pan  5386   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-pan  5386   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-pan  5386   bemorder  mem       REG        3,1   81488    5866936 /usr/lib/libgnome-menu.so.2.1.13
gnome-pan  5386   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-pan  5386   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-pan  5386   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-pan  5386   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-pan  5386   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-pan  5386   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-pan  5386   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-pan  5386   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-pan  5386   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
gnome-pan  5386   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-pan  5386   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
gnome-pan  5386   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-pan  5386   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
gnome-pan  5386   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
gnome-pan  5386   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
gnome-pan  5386   bemorder  mem       REG        3,1   85152    5865794 /usr/lib/libgnome-desktop-2.so.2.3.10
gnome-pan  5386   bemorder  mem       REG        3,1   10548    5867254 /usr/lib/liblaunchpad-integration.so.0.0.0
gnome-pan  5386   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-pan  5386   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-pan  5386   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-pan  5386   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-pan  5386   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-pan  5386   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-pan  5386   bemorder    0r      CHR        1,3               8184 /dev/null
gnome-pan  5386   bemorder    1w     FIFO        0,6              16950 pipe
gnome-pan  5386   bemorder    2w     FIFO        0,6              16950 pipe
gnome-pan  5386   bemorder    3u     unix 0xf0c3b700              17713 socket
gnome-pan  5386   bemorder    4r     FIFO        0,6              17715 pipe
gnome-pan  5386   bemorder    5w     FIFO        0,6              17715 pipe
gnome-pan  5386   bemorder    6r     FIFO        0,6              17716 pipe
gnome-pan  5386   bemorder    7w     FIFO        0,6              17716 pipe
gnome-pan  5386   bemorder    8r     FIFO        0,6              17717 pipe
gnome-pan  5386   bemorder    9w     FIFO        0,6              17717 pipe
gnome-pan  5386   bemorder   10u     unix 0xf0c3bc40              17718 socket
gnome-pan  5386   bemorder   11u     unix 0xf1337380              17721 socket
gnome-pan  5386   bemorder   12u     unix 0xf1337540              17723 /tmp/orbit-bemorder/linc-150a-0-7943e0ef241b3
gnome-pan  5386   bemorder   13u     unix 0xf23311c0              17726 /tmp/orbit-bemorder/linc-150a-0-7943e0ef241b3
gnome-pan  5386   bemorder   14u     unix 0xee389e00              18195 socket
gnome-pan  5386   bemorder   15u     unix 0xec9008c0              18203 /tmp/orbit-bemorder/linc-150a-0-7943e0ef241b3
gnome-pan  5386   bemorder   16u     unix 0xef8fbe00              18295 socket
gnome-pan  5386   bemorder   17r      DIR       0,10       0          1 inotify
gnome-pan  5386   bemorder   18u     unix 0xea656a80              19262 socket
gnome-pan  5386   bemorder   19u     unix 0xea656000              19248 socket
gnome-pan  5386   bemorder   20u     unix 0xea656540              19251 /tmp/orbit-bemorder/linc-150a-0-7943e0ef241b3
gnome-pan  5386   bemorder   23u     unix 0xeb457700              19577 socket
gnome-pan  5386   bemorder   24u     unix 0xeb457a80              19580 /tmp/orbit-bemorder/linc-150a-0-7943e0ef241b3
gnome-pan  5386   bemorder   25u     unix 0xe8c2b8c0              21353 socket
gnome-pan  5386   bemorder   26u     unix 0xe8c2b000              21356 /tmp/orbit-bemorder/linc-150a-0-7943e0ef241b3
bonobo-ac  5396   bemorder  cwd       DIR        3,1    4096          2 /
bonobo-ac  5396   bemorder  rtd       DIR        3,1    4096          2 /
bonobo-ac  5396   bemorder  txt       REG        3,1   84964    5701634 /usr/lib/bonobo-activation/bonobo-activation-server
bonobo-ac  5396   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
bonobo-ac  5396   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
bonobo-ac  5396   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
bonobo-ac  5396   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
bonobo-ac  5396   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
bonobo-ac  5396   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
bonobo-ac  5396   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
bonobo-ac  5396   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
bonobo-ac  5396   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
bonobo-ac  5396   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
bonobo-ac  5396   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
bonobo-ac  5396   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
bonobo-ac  5396   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
bonobo-ac  5396   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
bonobo-ac  5396   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
bonobo-ac  5396   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
bonobo-ac  5396   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
bonobo-ac  5396   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
bonobo-ac  5396   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
bonobo-ac  5396   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
bonobo-ac  5396   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
bonobo-ac  5396   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
bonobo-ac  5396   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
bonobo-ac  5396   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
bonobo-ac  5396   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
bonobo-ac  5396   bemorder    0u      CHR        1,3               8184 /dev/null
bonobo-ac  5396   bemorder    1u      CHR        1,3               8184 /dev/null
bonobo-ac  5396   bemorder    2u      CHR        1,3               8184 /dev/null
bonobo-ac  5396   bemorder    3u     unix 0xee389c40              18197 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder    4r     FIFO        0,6              17782 pipe
bonobo-ac  5396   bemorder    5w     FIFO        0,6              17782 pipe
bonobo-ac  5396   bemorder    6r     FIFO        0,6              17783 pipe
bonobo-ac  5396   bemorder    7w     FIFO        0,6              17783 pipe
bonobo-ac  5396   bemorder    8r     FIFO        0,6              17784 pipe
bonobo-ac  5396   bemorder    9w     FIFO        0,6              17784 pipe
bonobo-ac  5396   bemorder   10r     FIFO        0,6              17785 pipe
bonobo-ac  5396   bemorder   11w     FIFO        0,6              17785 pipe
bonobo-ac  5396   bemorder   12r     FIFO        0,6              17786 pipe
bonobo-ac  5396   bemorder   13w     FIFO        0,6              17786 pipe
bonobo-ac  5396   bemorder   14u     unix 0xee389700              18191 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   15u     unix 0xf00a1c40              18198 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   16u     unix 0xec9001c0              18199 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   17u     unix 0xec900380              18200 socket
bonobo-ac  5396   bemorder   18u     unix 0xec900700              18202 socket
bonobo-ac  5396   bemorder   19u     unix 0xec900a80              18204 socket
bonobo-ac  5396   bemorder   20u     unix 0xecab38c0              20284 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   21u     unix 0xf0ad88c0              21003 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   22u     unix 0xea7f7c40              19297 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   23u     unix 0xeb4571c0              19568 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   24u     unix 0xf0ad8a80              21004 socket
bonobo-ac  5396   bemorder   25u     unix 0xea7f7e00              19298 socket
bonobo-ac  5396   bemorder   26u     unix 0xee389540              19214 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   27u     unix 0xe3dcb000              20285 socket
bonobo-ac  5396   bemorder   29u     unix 0xecb12000              19215 socket
bonobo-ac  5396   bemorder   30u     unix 0xeb457380              19569 socket
bonobo-ac  5396   bemorder   31u     unix 0xe8c611c0              21343 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   32u     unix 0xeccce700              19237 /tmp/orbit-bemorder/linc-1514-0-25b04741ed5de
bonobo-ac  5396   bemorder   34u     unix 0xeccce8c0              19238 socket
bonobo-ac  5396   bemorder   36u     unix 0xe8c2b380              21344 socket
gnome-vol  5398   bemorder  cwd       DIR        3,1    4096          2 /
gnome-vol  5398   bemorder  rtd       DIR        3,1    4096          2 /
gnome-vol  5398   bemorder  txt       REG        3,1   52156    5865946 /usr/bin/gnome-volume-manager
gnome-vol  5398   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-vol  5398   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-vol  5398   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-vol  5398   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-vol  5398   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-vol  5398   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-vol  5398   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-vol  5398   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-vol  5398   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-vol  5398   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-vol  5398   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-vol  5398   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-vol  5398   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-vol  5398   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-vol  5398   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-vol  5398   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-vol  5398   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-vol  5398   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
gnome-vol  5398   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
gnome-vol  5398   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-vol  5398   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-vol  5398   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-vol  5398   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-vol  5398   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-vol  5398   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-vol  5398   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-vol  5398   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
gnome-vol  5398   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-vol  5398   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-vol  5398   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-vol  5398   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   25068    5867323 /usr/lib/libnotify.so.1.1.2
gnome-vol  5398   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-vol  5398   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-vol  5398   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-vol  5398   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-vol  5398   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-vol  5398   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-vol  5398   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-vol  5398   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-vol  5398   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-vol  5398   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-vol  5398   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-vol  5398   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-vol  5398   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-vol  5398   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-vol  5398   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-vol  5398   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-vol  5398   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-vol  5398   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-vol  5398   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-vol  5398   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-vol  5398   bemorder  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-vol  5398   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-vol  5398   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-vol  5398   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-vol  5398   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-vol  5398   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-vol  5398   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-vol  5398   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
gnome-vol  5398   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
gnome-vol  5398   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
gnome-vol  5398   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
gnome-vol  5398   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-vol  5398   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
gnome-vol  5398   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-vol  5398   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-vol  5398   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
gnome-vol  5398   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-vol  5398   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-vol  5398   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-vol  5398   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-vol  5398   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-vol  5398   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-vol  5398   bemorder    0u      CHR        1,3               8184 /dev/null
gnome-vol  5398   bemorder    1u      CHR        1,3               8184 /dev/null
gnome-vol  5398   bemorder    2u      CHR        1,3               8184 /dev/null
gnome-vol  5398   bemorder    3u     unix 0xf0dc1540              17791 socket
gnome-vol  5398   bemorder    4r     FIFO        0,6              17793 pipe
gnome-vol  5398   bemorder    5w     FIFO        0,6              17793 pipe
gnome-vol  5398   bemorder    6r     FIFO        0,6              17794 pipe
gnome-vol  5398   bemorder    7w     FIFO        0,6              17794 pipe
gnome-vol  5398   bemorder    8r     FIFO        0,6              17795 pipe
gnome-vol  5398   bemorder    9w     FIFO        0,6              17795 pipe
gnome-vol  5398   bemorder   10u     unix 0xf0dc1a80              17796 socket
gnome-vol  5398   bemorder   11u     unix 0xf0dc1c40              17799 socket
gnome-vol  5398   bemorder   12u     unix 0xf1c81700              17801 /tmp/orbit-bemorder/linc-150d-0-7943e0ef738b7
gnome-vol  5398   bemorder   13u     unix 0xf0c3b8c0              17804 /tmp/orbit-bemorder/linc-150d-0-7943e0ef738b7
gnome-vol  5398   bemorder   14u     unix 0xf0c3b380              17805 socket
gnome-vol  5398   bemorder   15r     FIFO        0,6              18025 pipe
gnome-vol  5398   bemorder   16w     FIFO        0,6              18025 pipe
gnome-vol  5398   bemorder   17u     unix 0xefe33e00              18026 socket
vino-sess  5399   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
vino-sess  5399   bemorder  rtd       DIR        3,1    4096          2 /
vino-sess  5399   bemorder  txt       REG        3,1    8960    5866558 /usr/bin/vino-session
vino-sess  5399   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
vino-sess  5399   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
vino-sess  5399   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
vino-sess  5399   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
vino-sess  5399   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
vino-sess  5399   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
vino-sess  5399   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
vino-sess  5399   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
vino-sess  5399   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
vino-sess  5399   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
vino-sess  5399   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
vino-sess  5399   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
vino-sess  5399   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
vino-sess  5399   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
vino-sess  5399   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
vino-sess  5399   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
vino-sess  5399   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
vino-sess  5399   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
vino-sess  5399   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
vino-sess  5399   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
vino-sess  5399   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
vino-sess  5399   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
vino-sess  5399   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
vino-sess  5399   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
vino-sess  5399   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
vino-sess  5399   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
vino-sess  5399   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
vino-sess  5399   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
vino-sess  5399   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
vino-sess  5399   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
vino-sess  5399   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
vino-sess  5399   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
vino-sess  5399   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
vino-sess  5399   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
vino-sess  5399   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
vino-sess  5399   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
vino-sess  5399   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
vino-sess  5399   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
vino-sess  5399   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
vino-sess  5399   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
vino-sess  5399   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
vino-sess  5399   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
vino-sess  5399   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
vino-sess  5399   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
vino-sess  5399   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
vino-sess  5399   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
vino-sess  5399   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
vino-sess  5399   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
vino-sess  5399   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
vino-sess  5399   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
vino-sess  5399   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
vino-sess  5399   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
vino-sess  5399   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
vino-sess  5399   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
vino-sess  5399   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
vino-sess  5399   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
vino-sess  5399   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
vino-sess  5399   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
vino-sess  5399   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
vino-sess  5399   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
vino-sess  5399   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
vino-sess  5399   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
vino-sess  5399   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
vino-sess  5399   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
vino-sess  5399   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
vino-sess  5399   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
vino-sess  5399   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
vino-sess  5399   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
vino-sess  5399   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
vino-sess  5399   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
vino-sess  5399   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
vino-sess  5399   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
vino-sess  5399   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
vino-sess  5399   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
vino-sess  5399   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
vino-sess  5399   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
vino-sess  5399   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
vino-sess  5399   bemorder    0r      CHR        1,3               8184 /dev/null
vino-sess  5399   bemorder    1w     FIFO        0,6              16950 pipe
vino-sess  5399   bemorder    2w     FIFO        0,6              16950 pipe
vino-sess  5399   bemorder    3u     unix 0xf0b7c8c0              17848 socket
vino-sess  5399   bemorder    4r     FIFO        0,6              17850 pipe
vino-sess  5399   bemorder    5w     FIFO        0,6              17850 pipe
vino-sess  5399   bemorder    6r     FIFO        0,6              17851 pipe
vino-sess  5399   bemorder    7w     FIFO        0,6              17851 pipe
vino-sess  5399   bemorder    8r     FIFO        0,6              17852 pipe
vino-sess  5399   bemorder    9w     FIFO        0,6              17852 pipe
vino-sess  5399   bemorder   10u     unix 0xf0b7cc40              17853 socket
vino-sess  5399   bemorder   11u     unix 0xf0384380              17964 socket
vino-sess  5399   bemorder   12u     unix 0xf0384700              17966 /tmp/orbit-bemorder/linc-1517-0-2bc73f4971d22
vino-sess  5399   bemorder   13u     unix 0xf0384a80              17970 /tmp/orbit-bemorder/linc-1517-0-2bc73f4971d22
gnome-vfs  5402   bemorder  cwd       DIR        3,1    4096          2 /
gnome-vfs  5402   bemorder  rtd       DIR        3,1    4096          2 /
gnome-vfs  5402   bemorder  txt       REG        3,1   86664    6373377 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
gnome-vfs  5402   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
gnome-vfs  5402   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
gnome-vfs  5402   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
gnome-vfs  5402   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
gnome-vfs  5402   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-vfs  5402   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-vfs  5402   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-vfs  5402   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-vfs  5402   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-vfs  5402   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-vfs  5402   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-vfs  5402   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-vfs  5402   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-vfs  5402   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-vfs  5402   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-vfs  5402   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-vfs  5402   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-vfs  5402   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-vfs  5402   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-vfs  5402   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-vfs  5402   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-vfs  5402   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-vfs  5402   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-vfs  5402   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-vfs  5402   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-vfs  5402   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-vfs  5402   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-vfs  5402   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-vfs  5402   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-vfs  5402   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-vfs  5402   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-vfs  5402   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-vfs  5402   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-vfs  5402   bemorder  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
gnome-vfs  5402   bemorder  mem       REG        3,1   35944    5865759 /usr/lib/libhal-storage.so.1.0.0
gnome-vfs  5402   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-vfs  5402   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-vfs  5402   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-vfs  5402   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-vfs  5402   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-vfs  5402   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-vfs  5402   bemorder    0u      CHR        1,3               8184 /dev/null
gnome-vfs  5402   bemorder    1u      CHR        1,3               8184 /dev/null
gnome-vfs  5402   bemorder    2u      CHR        1,3               8184 /dev/null
gnome-vfs  5402   bemorder    3r     FIFO        0,6              17864 pipe
gnome-vfs  5402   bemorder    4u      CHR        1,3               8184 /dev/null
gnome-vfs  5402   bemorder    5w     FIFO        0,6              17864 pipe
gnome-vfs  5402   bemorder    6u     unix 0xf0557a80              17865 socket
gnome-vfs  5402   bemorder    7r     FIFO        0,6              17867 pipe
gnome-vfs  5402   bemorder    8w     FIFO        0,6              17867 pipe
gnome-vfs  5402   bemorder    9r     FIFO        0,6              17868 pipe
gnome-vfs  5402   bemorder   10w     FIFO        0,6              17868 pipe
gnome-vfs  5402   bemorder   11u     unix 0xf0557540              17869 socket
gnome-vfs  5402   bemorder   12u     unix 0xf0557380              17871 /tmp/orbit-bemorder/linc-151a-0-b5f57231d25f
gnome-vfs  5402   bemorder   13u     unix 0xf0561000              17874 /tmp/orbit-bemorder/linc-151a-0-b5f57231d25f
gnome-vfs  5402   bemorder   14u     unix 0xf05611c0              17875 socket
gnome-vfs  5402   bemorder   15r      DIR       0,10       0          1 inotify
update-no  5403   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
update-no  5403   bemorder  rtd       DIR        3,1    4096          2 /
update-no  5403   bemorder  txt       REG        3,1   61120    5866540 /usr/bin/update-notifier
update-no  5403   bemorder  mem       REG        3,1   66276    4735016 /lib/libbz2.so.1.0.4
update-no  5403   bemorder  mem       REG        3,1  203840    5866882 /usr/lib/libcroco-0.6.so.3.0.1
update-no  5403   bemorder  mem       REG        3,1  210652    5867125 /usr/lib/libgsf-1.so.114.0.4
update-no  5403   bemorder  mem       REG        3,1  192656    5867415 /usr/lib/librsvg-2.so.2.16.1
update-no  5403   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
update-no  5403   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
update-no  5403   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
update-no  5403   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
update-no  5403   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
update-no  5403   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
update-no  5403   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
update-no  5403   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
update-no  5403   bemorder  mem       REG        3,1    5108    5931777 /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
update-no  5403   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
update-no  5403   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
update-no  5403   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
update-no  5403   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
update-no  5403   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
update-no  5403   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
update-no  5403   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
update-no  5403   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
update-no  5403   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
update-no  5403   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
update-no  5403   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
update-no  5403   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
update-no  5403   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
update-no  5403   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
update-no  5403   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
update-no  5403   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
update-no  5403   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
update-no  5403   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
update-no  5403   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
update-no  5403   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
update-no  5403   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
update-no  5403   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
update-no  5403   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
update-no  5403   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
update-no  5403   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
update-no  5403   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
update-no  5403   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
update-no  5403   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
update-no  5403   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
update-no  5403   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
update-no  5403   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
update-no  5403   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
update-no  5403   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
update-no  5403   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
update-no  5403   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
update-no  5403   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
update-no  5403   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
update-no  5403   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
update-no  5403   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
update-no  5403   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
update-no  5403   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
update-no  5403   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
update-no  5403   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
update-no  5403   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
update-no  5403   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
update-no  5403   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
update-no  5403   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
update-no  5403   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
update-no  5403   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
update-no  5403   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
update-no  5403   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
update-no  5403   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
update-no  5403   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
update-no  5403   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
update-no  5403   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
update-no  5403   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
update-no  5403   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
update-no  5403   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
update-no  5403   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
update-no  5403   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
update-no  5403   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
update-no  5403   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
update-no  5403   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
update-no  5403   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
update-no  5403   bemorder  mem       REG        3,1   25068    5867323 /usr/lib/libnotify.so.1.1.2
update-no  5403   bemorder  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
update-no  5403   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
update-no  5403   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
update-no  5403   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
update-no  5403   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
update-no  5403   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
update-no  5403   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
update-no  5403   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
update-no  5403   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
update-no  5403   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
update-no  5403   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
update-no  5403   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
update-no  5403   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
update-no  5403   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
update-no  5403   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
update-no  5403   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
update-no  5403   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
update-no  5403   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
update-no  5403   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
update-no  5403   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
update-no  5403   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
update-no  5403   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
update-no  5403   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
update-no  5403   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
update-no  5403   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
update-no  5403   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
update-no  5403   bemorder    0r      CHR        1,3               8184 /dev/null
update-no  5403   bemorder    1w     FIFO        0,6              16950 pipe
update-no  5403   bemorder    2w     FIFO        0,6              16950 pipe
update-no  5403   bemorder    3u     unix 0xf0561e00              17909 socket
update-no  5403   bemorder    4r     FIFO        0,6              17911 pipe
update-no  5403   bemorder    5w     FIFO        0,6              17911 pipe
update-no  5403   bemorder    6r     FIFO        0,6              17912 pipe
update-no  5403   bemorder    7w     FIFO        0,6              17912 pipe
update-no  5403   bemorder    8r     FIFO        0,6              17913 pipe
update-no  5403   bemorder    9w     FIFO        0,6              17913 pipe
update-no  5403   bemorder   10u     unix 0xf0b7c540              17914 socket
update-no  5403   bemorder   11u     unix 0xf0384e00              17974 socket
update-no  5403   bemorder   12u     unix 0xf0384000              17976 /tmp/orbit-bemorder/linc-151b-0-2bc73f49e982a
update-no  5403   bemorder   13u     unix 0xf0b7c700              17979 /tmp/orbit-bemorder/linc-151b-0-2bc73f49e982a
update-no  5403   bemorder   14u     unix 0xf0689a80              17980 socket
update-no  5403   bemorder   15u     unix 0xf0689540              17984 socket
update-no  5403   bemorder   16r      DIR       0,10       0          1 inotify
evolution  5408   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
evolution  5408   bemorder  rtd       DIR        3,1    4096          2 /
evolution  5408   bemorder  txt       REG        3,1  119172    5898900 /usr/lib/evolution/2.12/evolution-alarm-notify
evolution  5408   bemorder  mem       REG        3,1   24100    5932336 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
evolution  5408   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
evolution  5408   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
evolution  5408   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
evolution  5408   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
evolution  5408   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
evolution  5408   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
evolution  5408   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
evolution  5408   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
evolution  5408   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
evolution  5408   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
evolution  5408   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
evolution  5408   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
evolution  5408   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
evolution  5408   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
evolution  5408   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
evolution  5408   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
evolution  5408   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
evolution  5408   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
evolution  5408   bemorder  mem       REG        3,1  309420    5867447 /usr/lib/libsoftokn3.so.0d
evolution  5408   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
evolution  5408   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
evolution  5408   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
evolution  5408   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
evolution  5408   bemorder  mem       REG        3,1 1038208    5866898 /usr/lib/libdb-4.4.so
evolution  5408   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
evolution  5408   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
evolution  5408   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
evolution  5408   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
evolution  5408   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
evolution  5408   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
evolution  5408   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
evolution  5408   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
evolution  5408   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
evolution  5408   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
evolution  5408   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
evolution  5408   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
evolution  5408   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
evolution  5408   bemorder  mem       REG        3,1   26920    5866981 /usr/lib/libgailutil.so.18.0.1
evolution  5408   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
evolution  5408   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
evolution  5408   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
evolution  5408   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
evolution  5408   bemorder  mem       REG        3,1  152912    5867457 /usr/lib/libssl3.so.0d
evolution  5408   bemorder  mem       REG        3,1  144328    5867441 /usr/lib/libsmime3.so.0d
evolution  5408   bemorder  mem       REG        3,1  462004    5867325 /usr/lib/libnss3.so.0d
evolution  5408   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
evolution  5408   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
evolution  5408   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
evolution  5408   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
evolution  5408   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
evolution  5408   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
evolution  5408   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
evolution  5408   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
evolution  5408   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
evolution  5408   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
evolution  5408   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
evolution  5408   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
evolution  5408   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
evolution  5408   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
evolution  5408   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
evolution  5408   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
evolution  5408   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
evolution  5408   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
evolution  5408   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
evolution  5408   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
evolution  5408   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
evolution  5408   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
evolution  5408   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
evolution  5408   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
evolution  5408   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
evolution  5408   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
evolution  5408   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
evolution  5408   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
evolution  5408   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
evolution  5408   bemorder  mem       REG        3,1   25068    5867323 /usr/lib/libnotify.so.1.1.2
evolution  5408   bemorder  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
evolution  5408   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
evolution  5408   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
evolution  5408   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
evolution  5408   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
evolution  5408   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
evolution  5408   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
evolution  5408   bemorder  mem       REG        3,1  147812    5867066 /usr/lib/libedataserver-1.2.so.9.0.1
evolution  5408   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
evolution  5408   bemorder  mem       REG        3,1  204152    5866869 /usr/lib/libebook-1.2.so.9.1.0
evolution  5408   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
evolution  5408   bemorder  mem       REG        3,1  159764    5866928 /usr/lib/libedataserverui-1.2.so.8.0.2
evolution  5408   bemorder  mem       REG        3,1  644084    5866926 /usr/lib/libecal-1.2.so.7.0.2
evolution  5408   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
evolution  5408   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
evolution  5408   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
evolution  5408   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
evolution  5408   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
evolution  5408   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
evolution  5408   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
evolution  5408   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
evolution  5408   bemorder  mem       REG        3,1  658996    5866572 /usr/lib/libgtkhtml-3.14.so.19.1.0
evolution  5408   bemorder  mem       REG        3,1  305520    5866934 /usr/lib/libcamel-1.2.so.10.0.1
evolution  5408   bemorder  mem       REG        3,1  325764    5867343 /usr/lib/libcamel-provider-1.2.so.10.0.1
evolution  5408   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
evolution  5408   bemorder  mem       REG        3,1  193772    5867324 /usr/lib/libnspr4.so.0d
evolution  5408   bemorder  mem       REG        3,1   14332    5867378 /usr/lib/libplc4.so.0d
evolution  5408   bemorder  mem       REG        3,1    8232    5867379 /usr/lib/libplds4.so.0d
evolution  5408   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
evolution  5408   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
evolution  5408   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
evolution  5408   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
evolution  5408   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
evolution  5408   bemorder  mem       REG        3,1   77096    5898518 /usr/lib/evolution/2.12/libevolution-a11y.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1   32420    5898531 /usr/lib/evolution/2.12/libevolution-widgets-a11y.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1  469596    5898514 /usr/lib/evolution/2.12/libetable.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1  110460    5898515 /usr/lib/evolution/2.12/libetext.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1  371424    5898511 /usr/lib/evolution/2.12/libemiscwidgets.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1  184344    5898517 /usr/lib/evolution/2.12/libeutil.so.0.0.0
evolution  5408   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
evolution  5408   bemorder    0r      CHR        1,3               8184 /dev/null
evolution  5408   bemorder    1w     FIFO        0,6              16950 pipe
evolution  5408   bemorder    2w     FIFO        0,6              16950 pipe
evolution  5408   bemorder    3u     unix 0xeea4f000              18150 socket
evolution  5408   bemorder    4r     FIFO        0,6              18152 pipe
evolution  5408   bemorder    5w     FIFO        0,6              18152 pipe
evolution  5408   bemorder    6r     FIFO        0,6              18153 pipe
evolution  5408   bemorder    7w     FIFO        0,6              18153 pipe
evolution  5408   bemorder    8r     FIFO        0,6              18154 pipe
evolution  5408   bemorder    9w     FIFO        0,6              18154 pipe
evolution  5408   bemorder   10u     unix 0xeea4f380              18155 socket
evolution  5408   bemorder   11u     unix 0xeea4f700              18158 socket
evolution  5408   bemorder   12u     unix 0xeea4fa80              18160 /tmp/orbit-bemorder/linc-1520-0-71ffb14dd3d9e
evolution  5408   bemorder   13u     unix 0xeea4fe00              18163 /tmp/orbit-bemorder/linc-1520-0-71ffb14dd3d9e
evolution  5408   bemorder   14r     FIFO        0,6              18164 pipe
evolution  5408   bemorder   15w     FIFO        0,6              18164 pipe
evolution  5408   bemorder   16r     FIFO        0,6              18165 pipe
evolution  5408   bemorder   17w     FIFO        0,6              18165 pipe
evolution  5408   bemorder   18r     FIFO        0,6              18166 pipe
evolution  5408   bemorder   19w     FIFO        0,6              18166 pipe
evolution  5408   bemorder   20u     unix 0xee003380              18172 socket
evolution  5408   bemorder   21u     unix 0xec900540              18201 /tmp/orbit-bemorder/linc-1520-0-71ffb14dd3d9e
evolution  5408   bemorder   22u     unix 0xee389a80              18194 socket
evolution  5408   bemorder   23u     unix 0xed4691c0              19302 socket
evolution  5408   bemorder   24u     unix 0xed469700              19305 /tmp/orbit-bemorder/linc-1520-0-71ffb14dd3d9e
nm-applet  5414   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
nm-applet  5414   bemorder  rtd       DIR        3,1    4096          2 /
nm-applet  5414   bemorder  txt       REG        3,1  183932    5866190 /usr/bin/nm-applet
nm-applet  5414   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
nm-applet  5414   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
nm-applet  5414   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
nm-applet  5414   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
nm-applet  5414   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
nm-applet  5414   bemorder  DEL       REG        0,9              32768 /SYSV00000000
nm-applet  5414   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
nm-applet  5414   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
nm-applet  5414   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
nm-applet  5414   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
nm-applet  5414   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
nm-applet  5414   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
nm-applet  5414   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
nm-applet  5414   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
nm-applet  5414   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
nm-applet  5414   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
nm-applet  5414   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
nm-applet  5414   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
nm-applet  5414   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
nm-applet  5414   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
nm-applet  5414   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
nm-applet  5414   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
nm-applet  5414   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
nm-applet  5414   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
nm-applet  5414   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
nm-applet  5414   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
nm-applet  5414   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
nm-applet  5414   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
nm-applet  5414   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
nm-applet  5414   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
nm-applet  5414   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
nm-applet  5414   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
nm-applet  5414   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
nm-applet  5414   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
nm-applet  5414   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
nm-applet  5414   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   33744    5867291 /usr/lib/libnm-util.so.0.0.0
nm-applet  5414   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
nm-applet  5414   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
nm-applet  5414   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
nm-applet  5414   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
nm-applet  5414   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
nm-applet  5414   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
nm-applet  5414   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
nm-applet  5414   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
nm-applet  5414   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
nm-applet  5414   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
nm-applet  5414   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
nm-applet  5414   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
nm-applet  5414   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
nm-applet  5414   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
nm-applet  5414   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
nm-applet  5414   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
nm-applet  5414   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
nm-applet  5414   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
nm-applet  5414   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
nm-applet  5414   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
nm-applet  5414   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
nm-applet  5414   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
nm-applet  5414   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
nm-applet  5414   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
nm-applet  5414   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
nm-applet  5414   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
nm-applet  5414   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
nm-applet  5414   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
nm-applet  5414   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
nm-applet  5414   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
nm-applet  5414   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
nm-applet  5414   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
nm-applet  5414   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
nm-applet  5414   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
nm-applet  5414   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
nm-applet  5414   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
nm-applet  5414   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
nm-applet  5414   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
nm-applet  5414   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
nm-applet  5414   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
nm-applet  5414   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
nm-applet  5414   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
nm-applet  5414   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
nm-applet  5414   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
nm-applet  5414   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
nm-applet  5414   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
nm-applet  5414   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
nm-applet  5414   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
nm-applet  5414   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
nm-applet  5414   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
nm-applet  5414   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
nm-applet  5414   bemorder    0r      CHR        1,3               8184 /dev/null
nm-applet  5414   bemorder    1w     FIFO        0,6              16950 pipe
nm-applet  5414   bemorder    2w     FIFO        0,6              16950 pipe
nm-applet  5414   bemorder    3u     unix 0xf06891c0              17993 socket
nm-applet  5414   bemorder    4r     FIFO        0,6              17995 pipe
nm-applet  5414   bemorder    5w     FIFO        0,6              17995 pipe
nm-applet  5414   bemorder    6r     FIFO        0,6              17996 pipe
nm-applet  5414   bemorder    7w     FIFO        0,6              17996 pipe
nm-applet  5414   bemorder    8r     FIFO        0,6              17997 pipe
nm-applet  5414   bemorder    9w     FIFO        0,6              17997 pipe
nm-applet  5414   bemorder   10u     unix 0xf00a18c0              17998 socket
nm-applet  5414   bemorder   11u     unix 0xf00a1380              18000 /tmp/orbit-bemorder/linc-1526-0-5d2ee51e29c8f
nm-applet  5414   bemorder   12u     unix 0xf03aa000              18003 /tmp/orbit-bemorder/linc-1526-0-5d2ee51e29c8f
nm-applet  5414   bemorder   13u     unix 0xee003700              18174 socket
nm-applet  5414   bemorder   14u     unix 0xee003a80              18181 socket
gnome-cup  5415   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
gnome-cup  5415   bemorder  rtd       DIR        3,1    4096          2 /
gnome-cup  5415   bemorder  txt       REG        3,1   25280    5865892 /usr/bin/gnome-cups-icon
gnome-cup  5415   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-cup  5415   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-cup  5415   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-cup  5415   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-cup  5415   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-cup  5415   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-cup  5415   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-cup  5415   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-cup  5415   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-cup  5415   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-cup  5415   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   89120    5867420 /usr/lib/libsasl2.so.2.0.22
gnome-cup  5415   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
gnome-cup  5415   bemorder  mem       REG        3,1   47212    5867256 /usr/lib/liblber.so.2.0.130
gnome-cup  5415   bemorder  mem       REG        3,1  217924    5867262 /usr/lib/libldap_r.so.2.0.130
gnome-cup  5415   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
gnome-cup  5415   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
gnome-cup  5415   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
gnome-cup  5415   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
gnome-cup  5415   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
gnome-cup  5415   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-cup  5415   bemorder  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
gnome-cup  5415   bemorder  mem       REG        3,1  970680    5865600 /usr/lib/libstdc++.so.6.0.9
gnome-cup  5415   bemorder  mem       REG        3,1 2175856    5867440 /usr/lib/libsmbclient.so.0.1
gnome-cup  5415   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-cup  5415   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-cup  5415   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-cup  5415   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-cup  5415   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-cup  5415   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
gnome-cup  5415   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
gnome-cup  5415   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-cup  5415   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-cup  5415   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-cup  5415   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-cup  5415   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-cup  5415   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-cup  5415   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-cup  5415   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
gnome-cup  5415   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-cup  5415   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-cup  5415   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1  188692    5867081 /usr/lib/libgnomecupsui-1.0.so.1.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-cup  5415   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
gnome-cup  5415   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-cup  5415   bemorder  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-cup  5415   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-cup  5415   bemorder  mem       REG        3,1  197292    5867015 /usr/lib/libcups.so.2
gnome-cup  5415   bemorder  mem       REG        3,1   53368    5867079 /usr/lib/libgnomecups-1.0.so.1.0.0
gnome-cup  5415   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-cup  5415   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-cup  5415   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-cup  5415   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-cup  5415   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-cup  5415   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-cup  5415   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-cup  5415   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-cup  5415   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-cup  5415   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-cup  5415   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-cup  5415   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-cup  5415   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-cup  5415   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-cup  5415   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-cup  5415   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-cup  5415   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-cup  5415   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-cup  5415   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-cup  5415   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-cup  5415   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-cup  5415   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
gnome-cup  5415   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
gnome-cup  5415   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
gnome-cup  5415   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-cup  5415   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-cup  5415   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-cup  5415   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
gnome-cup  5415   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-cup  5415   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
gnome-cup  5415   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-cup  5415   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-cup  5415   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
gnome-cup  5415   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-cup  5415   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-cup  5415   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-cup  5415   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-cup  5415   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-cup  5415   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-cup  5415   bemorder    0r      CHR        1,3               8184 /dev/null
gnome-cup  5415   bemorder    1w     FIFO        0,6              16950 pipe
gnome-cup  5415   bemorder    2w     FIFO        0,6              16950 pipe
gnome-cup  5415   bemorder    3u     unix 0xf1572e00              18132 socket
gnome-cup  5415   bemorder    4r     FIFO        0,6              18134 pipe
gnome-cup  5415   bemorder    5w     FIFO        0,6              18134 pipe
gnome-cup  5415   bemorder    6r     FIFO        0,6              18135 pipe
gnome-cup  5415   bemorder    7w     FIFO        0,6              18135 pipe
gnome-cup  5415   bemorder    8r     FIFO        0,6              18136 pipe
gnome-cup  5415   bemorder    9w     FIFO        0,6              18136 pipe
gnome-cup  5415   bemorder   10u     unix 0xef8fb8c0              18137 socket
gnome-cup  5415   bemorder   11u     unix 0xf2331a80              18140 socket
gnome-cup  5415   bemorder   12u     unix 0xf2331000              18142 /tmp/orbit-bemorder/linc-1527-0-71ffb14d836b9
gnome-cup  5415   bemorder   13u     unix 0xf1c81540              18145 /tmp/orbit-bemorder/linc-1527-0-71ffb14d836b9
gnome-cup  5415   bemorder   14u     unix 0xec900c40              18205 /tmp/orbit-bemorder/linc-1527-0-71ffb14d836b9
gnome-cup  5415   bemorder   15u     unix 0xec900000              18196 socket
gnome-cup  5415   bemorder   16r      CHR        1,9               4047 /dev/urandom
gnome-cup  5415   bemorder   17u     unix 0xecab31c0              18214 socket
gnome-pow  5417   bemorder  cwd       DIR        3,1    4096          2 /
gnome-pow  5417   bemorder  rtd       DIR        3,1    4096          2 /
gnome-pow  5417   bemorder  txt       REG        3,1  322824    5866010 /usr/bin/gnome-power-manager
gnome-pow  5417   bemorder  mem       REG        3,1   81100    6438919 /usr/lib/gstreamer-0.10/libgstalsa.so
gnome-pow  5417   bemorder  mem       REG        3,1   32036    5867141 /usr/lib/libgstcontroller-0.10.so.0.12.0
gnome-pow  5417   bemorder  mem       REG        3,1  404500    5867331 /usr/lib/liboil-0.3.so.0.1.0
gnome-pow  5417   bemorder  mem       REG        3,1   35020    6438925 /usr/lib/gstreamer-0.10/libgstaudioresample.so
gnome-pow  5417   bemorder  mem       REG        3,1   31084    6438922 /usr/lib/gstreamer-0.10/libgstaudioconvert.so
gnome-pow  5417   bemorder  mem       REG        3,1  101608    5867133 /usr/lib/libgstaudio-0.10.so.0.9.0
gnome-pow  5417   bemorder  mem       REG        3,1   40872    5867155 /usr/lib/libgstriff-0.10.so.0.9.0
gnome-pow  5417   bemorder  mem       REG        3,1   14532    6438991 /usr/lib/gstreamer-0.10/libgstvolume.so
gnome-pow  5417   bemorder  mem       REG        3,1   15696    6438928 /usr/lib/gstreamer-0.10/libgstautodetect.so
gnome-pow  5417   bemorder  mem       REG        3,1   40680    6438995 /usr/lib/gstreamer-0.10/libgstwavparse.so
gnome-pow  5417   bemorder  mem       REG        3,1   48528    6438979 /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
gnome-pow  5417   bemorder  mem       REG        3,1   33872    6438938 /usr/lib/gstreamer-0.10/libgstdecodebin.so
gnome-pow  5417   bemorder  DEL       REG        0,9             229382 /SYSV00000000
gnome-pow  5417   bemorder  mem       REG        3,1  159500    6438934 /usr/lib/gstreamer-0.10/libgstcoreelements.so
gnome-pow  5417   bemorder  mem       REG        3,1   98872    6438944 /usr/lib/gstreamer-0.10/libgstffmpegcolorspace.so
gnome-pow  5417   bemorder  mem       REG        3,1   14392    5866807 /usr/lib/libXv.so.1.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  148140    5867135 /usr/lib/libgstbase-0.10.so.0.12.0
gnome-pow  5417   bemorder  mem       REG        3,1   32012    5867145 /usr/lib/libgstinterfaces-0.10.so.0.9.0
gnome-pow  5417   bemorder  mem       REG        3,1   76752    6438981 /usr/lib/gstreamer-0.10/libgstvideo4linux.so
gnome-pow  5417   bemorder  mem       REG        3,1   40668    5867151 /usr/lib/libgstpbutils-0.10.so.0.9.0
gnome-pow  5417   bemorder  mem       CHR      116,9              13700 /dev/snd/pcmC0D0p
gnome-pow  5417   bemorder  mem       REG        3,1   31332    6438968 /usr/lib/gstreamer-0.10/libgstpng.so
gnome-pow  5417   bemorder  mem       REG        3,1   89224    6438967 /usr/lib/gstreamer-0.10/libgstplaybin.so
gnome-pow  5417   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-pow  5417   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
gnome-pow  5417   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
gnome-pow  5417   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-pow  5417   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-pow  5417   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-pow  5417   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-pow  5417   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-pow  5417   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-pow  5417   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-pow  5417   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-pow  5417   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-pow  5417   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-pow  5417   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-pow  5417   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-pow  5417   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-pow  5417   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-pow  5417   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
gnome-pow  5417   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
gnome-pow  5417   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-pow  5417   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-pow  5417   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-pow  5417   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-pow  5417   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-pow  5417   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-pow  5417   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-pow  5417   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
gnome-pow  5417   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-pow  5417   bemorder  mem       REG        3,1    5748    5866758 /usr/lib/libXRes.so.1.0.0
gnome-pow  5417   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-pow  5417   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-pow  5417   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-pow  5417   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-pow  5417   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-pow  5417   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-pow  5417   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-pow  5417   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-pow  5417   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-pow  5417   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-pow  5417   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-pow  5417   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-pow  5417   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-pow  5417   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-pow  5417   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-pow  5417   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-pow  5417   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-pow  5417   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-pow  5417   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-pow  5417   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-pow  5417   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-pow  5417   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-pow  5417   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-pow  5417   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-pow  5417   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-pow  5417   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-pow  5417   bemorder  mem       REG        3,1   25068    5867323 /usr/lib/libnotify.so.1.1.2
gnome-pow  5417   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-pow  5417   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-pow  5417   bemorder  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-pow  5417   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-pow  5417   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-pow  5417   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
gnome-pow  5417   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
gnome-pow  5417   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
gnome-pow  5417   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-pow  5417   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
gnome-pow  5417   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-pow  5417   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
gnome-pow  5417   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-pow  5417   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
gnome-pow  5417   bemorder  mem       REG        3,1   54256    5866575 /usr/lib/libpanel-applet-2.so.0.2.21
gnome-pow  5417   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
gnome-pow  5417   bemorder  mem       REG        3,1  219416    5866859 /usr/lib/libwnck-1.so.22.2.0
gnome-pow  5417   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-pow  5417   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
gnome-pow  5417   bemorder  mem       REG        3,1  650160    5867153 /usr/lib/libgstreamer-0.10.so.0.12.0
gnome-pow  5417   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-pow  5417   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-pow  5417   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-pow  5417   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-pow  5417   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-pow  5417   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-pow  5417   bemorder    0u      CHR        1,3               8184 /dev/null
gnome-pow  5417   bemorder    1u      CHR        1,3               8184 /dev/null
gnome-pow  5417   bemorder    2u      CHR        1,3               8184 /dev/null
gnome-pow  5417   bemorder    3u     unix 0xf03aa1c0              18006 socket
gnome-pow  5417   bemorder    4r     FIFO        0,6              18008 pipe
gnome-pow  5417   bemorder    5w     FIFO        0,6              18008 pipe
gnome-pow  5417   bemorder    6r     FIFO        0,6              18009 pipe
gnome-pow  5417   bemorder    7w     FIFO        0,6              18009 pipe
gnome-pow  5417   bemorder    8r     FIFO        0,6              18010 pipe
gnome-pow  5417   bemorder    9w     FIFO        0,6              18010 pipe
gnome-pow  5417   bemorder   10u     unix 0xf03aa540              18011 socket
gnome-pow  5417   bemorder   11u     unix 0xf03aa8c0              18014 socket
gnome-pow  5417   bemorder   12u     unix 0xf03aac40              18016 /tmp/orbit-bemorder/linc-1523-0-5d2ee51e511fa
gnome-pow  5417   bemorder   13u     unix 0xefe33000              18019 /tmp/orbit-bemorder/linc-1523-0-5d2ee51e511fa
gnome-pow  5417   bemorder   14u     unix 0xefe331c0              18020 socket
gnome-pow  5417   bemorder   15u     unix 0xefe33700              18021 socket
gnome-pow  5417   bemorder   16u     unix 0xefe33a80              18023 socket
gnome-pow  5417   bemorder   17u     unix 0xed469c40              19453 socket
gnome-pow  5417   bemorder   18r      REG        3,1    1706    6050507 /usr/share/gnome-power-manager/gpm-unplugged.wav
gnome-pow  5417   bemorder   21u      CHR      116,9              13700 /dev/snd/pcmC0D0p
evolution  5630   bemorder  cwd       DIR        3,1    4096          2 /
evolution  5630   bemorder  rtd       DIR        3,1    4096          2 /
evolution  5630   bemorder  txt       REG        3,1   23716    5881956 /usr/lib/evolution/evolution-data-server-1.12
evolution  5630   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
evolution  5630   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
evolution  5630   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
evolution  5630   bemorder  mem       REG        3,1   89120    5867420 /usr/lib/libsasl2.so.2.0.22
evolution  5630   bemorder  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
evolution  5630   bemorder  mem       REG        3,1   47212    5867256 /usr/lib/liblber.so.2.0.130
evolution  5630   bemorder  mem       REG        3,1  217924    5867262 /usr/lib/libldap_r.so.2.0.130
evolution  5630   bemorder  mem       REG        3,1   17224    5931303 /usr/lib/evolution-data-server-1.2/extensions/libebookbackendvcf.so
evolution  5630   bemorder  mem       REG        3,1   65532    5931302 /usr/lib/evolution-data-server-1.2/extensions/libebookbackendldap.so
evolution  5630   bemorder  mem       REG        3,1   93480    5931308 /usr/lib/evolution-data-server-1.2/extensions/libecalbackendgroupwise.so
evolution  5630   bemorder  mem       REG        3,1   27064    5931300 /usr/lib/evolution-data-server-1.2/extensions/libebookbackendfile.so
evolution  5630   bemorder  mem       REG        3,1   44324    5931306 /usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
evolution  5630   bemorder  mem       REG        3,1  143420    5866121 /usr/lib/libegroupwise-1.2.so.13.0.1
evolution  5630   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
evolution  5630   bemorder  mem       REG        3,1   24036    5931311 /usr/lib/evolution-data-server-1.2/extensions/libecalbackendhttp.so
evolution  5630   bemorder  mem       REG        3,1   62312    5931301 /usr/lib/evolution-data-server-1.2/extensions/libebookbackendgroupwise.so
evolution  5630   bemorder  mem       REG        3,1   19560    5931305 /usr/lib/evolution-data-server-1.2/extensions/libecalbackendcontacts.so
evolution  5630   bemorder  mem       REG        3,1  180344    5867449 /usr/lib/libsoup-2.2.so.8.5.0
evolution  5630   bemorder  mem       REG        3,1   27784    5931312 /usr/lib/evolution-data-server-1.2/extensions/libecalbackendweather.so
evolution  5630   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
evolution  5630   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
evolution  5630   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
evolution  5630   bemorder  mem       REG        3,1   32980    5931304 /usr/lib/evolution-data-server-1.2/extensions/libecalbackendcaldav.so
evolution  5630   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
evolution  5630   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
evolution  5630   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
evolution  5630   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
evolution  5630   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
evolution  5630   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
evolution  5630   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
evolution  5630   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
evolution  5630   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
evolution  5630   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
evolution  5630   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
evolution  5630   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
evolution  5630   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
evolution  5630   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
evolution  5630   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
evolution  5630   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
evolution  5630   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
evolution  5630   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
evolution  5630   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
evolution  5630   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
evolution  5630   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
evolution  5630   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
evolution  5630   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
evolution  5630   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
evolution  5630   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
evolution  5630   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
evolution  5630   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
evolution  5630   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
evolution  5630   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
evolution  5630   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
evolution  5630   bemorder  mem       REG        3,1  309420    5867447 /usr/lib/libsoftokn3.so.0d
evolution  5630   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
evolution  5630   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
evolution  5630   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
evolution  5630   bemorder  mem       REG        3,1  193772    5867324 /usr/lib/libnspr4.so.0d
evolution  5630   bemorder  mem       REG        3,1   14332    5867378 /usr/lib/libplc4.so.0d
evolution  5630   bemorder  mem       REG        3,1    8232    5867379 /usr/lib/libplds4.so.0d
evolution  5630   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
evolution  5630   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
evolution  5630   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
evolution  5630   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
evolution  5630   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
evolution  5630   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
evolution  5630   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
evolution  5630   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
evolution  5630   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
evolution  5630   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
evolution  5630   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
evolution  5630   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
evolution  5630   bemorder  mem       REG        3,1 1038208    5866898 /usr/lib/libdb-4.4.so
evolution  5630   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
evolution  5630   bemorder  mem       REG        3,1  147812    5867066 /usr/lib/libedataserver-1.2.so.9.0.1
evolution  5630   bemorder  mem       REG        3,1  644084    5866926 /usr/lib/libecal-1.2.so.7.0.2
evolution  5630   bemorder  mem       REG        3,1  159644    5866116 /usr/lib/libedata-cal-1.2.so.6.0.2
evolution  5630   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
evolution  5630   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
evolution  5630   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
evolution  5630   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
evolution  5630   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
evolution  5630   bemorder  mem       REG        3,1  152912    5867457 /usr/lib/libssl3.so.0d
evolution  5630   bemorder  mem       REG        3,1  144328    5867441 /usr/lib/libsmime3.so.0d
evolution  5630   bemorder  mem       REG        3,1  462004    5867325 /usr/lib/libnss3.so.0d
evolution  5630   bemorder  mem       REG        3,1  305520    5866934 /usr/lib/libcamel-1.2.so.10.0.1
evolution  5630   bemorder  mem       REG        3,1  204152    5866869 /usr/lib/libebook-1.2.so.9.1.0
evolution  5630   bemorder  mem       REG        3,1  121628    5865736 /usr/lib/libedata-book-1.2.so.2.4.1
evolution  5630   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
evolution  5630   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
evolution  5630   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
evolution  5630   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
evolution  5630   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
evolution  5630   bemorder    0u      CHR        1,3               8184 /dev/null
evolution  5630   bemorder    1u      CHR        1,3               8184 /dev/null
evolution  5630   bemorder    2u      CHR        1,3               8184 /dev/null
evolution  5630   bemorder    3r     FIFO        0,6              18308 pipe
evolution  5630   bemorder    4w     FIFO        0,6              18308 pipe
evolution  5630   bemorder    5r     FIFO        0,6              18309 pipe
evolution  5630   bemorder    6w     FIFO        0,6              18309 pipe
evolution  5630   bemorder    7r     FIFO        0,6              18310 pipe
evolution  5630   bemorder    8w     FIFO        0,6              18310 pipe
evolution  5630   bemorder    9u     unix 0xecab3000              18311 socket
evolution  5630   bemorder   10u     unix 0xec7a2e00              18341 /tmp/orbit-bemorder/linc-15fe-0-28ffe022d9b1d
evolution  5630   bemorder   11u     unix 0xee003e00              18344 /tmp/orbit-bemorder/linc-15fe-0-28ffe022d9b1d
evolution  5630   bemorder   12r     FIFO        0,6              19211 pipe
evolution  5630   bemorder   13w     FIFO        0,6              19211 pipe
evolution  5630   bemorder   14r     FIFO        0,6              19212 pipe
evolution  5630   bemorder   15w     FIFO        0,6              19212 pipe
evolution  5630   bemorder   16u     unix 0xecb121c0              19216 /tmp/orbit-bemorder/linc-15fe-0-28ffe022d9b1d
evolution  5630   bemorder   17u     unix 0xee3898c0              19213 socket
evolution  5630   bemorder   18u     unix 0xed469380              19303 /tmp/orbit-bemorder/linc-15fe-0-28ffe022d9b1d
evolution  5630   bemorder   19u     unix 0xed469540              19304 socket
evolution  5630   bemorder   21r     FIFO        0,6              19306 pipe
evolution  5630   bemorder   22w     FIFO        0,6              19306 pipe
trashappl  5838   bemorder  cwd       DIR        3,1    4096          2 /
trashappl  5838   bemorder  rtd       DIR        3,1    4096          2 /
trashappl  5838   bemorder  txt       REG        3,1   37916    6214051 /usr/lib/gnome-applets/trashapplet
trashappl  5838   bemorder  DEL       REG        0,9              98306 /SYSV00000000
trashappl  5838   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
trashappl  5838   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
trashappl  5838   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
trashappl  5838   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
trashappl  5838   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
trashappl  5838   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
trashappl  5838   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
trashappl  5838   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
trashappl  5838   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
trashappl  5838   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
trashappl  5838   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
trashappl  5838   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
trashappl  5838   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
trashappl  5838   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
trashappl  5838   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
trashappl  5838   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
trashappl  5838   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
trashappl  5838   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
trashappl  5838   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
trashappl  5838   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
trashappl  5838   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
trashappl  5838   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
trashappl  5838   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
trashappl  5838   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
trashappl  5838   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
trashappl  5838   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
trashappl  5838   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
trashappl  5838   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
trashappl  5838   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
trashappl  5838   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
trashappl  5838   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
trashappl  5838   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
trashappl  5838   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
trashappl  5838   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
trashappl  5838   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
trashappl  5838   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
trashappl  5838   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
trashappl  5838   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
trashappl  5838   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
trashappl  5838   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
trashappl  5838   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
trashappl  5838   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
trashappl  5838   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
trashappl  5838   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
trashappl  5838   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
trashappl  5838   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
trashappl  5838   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
trashappl  5838   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
trashappl  5838   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
trashappl  5838   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
trashappl  5838   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
trashappl  5838   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
trashappl  5838   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
trashappl  5838   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
trashappl  5838   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
trashappl  5838   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
trashappl  5838   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
trashappl  5838   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
trashappl  5838   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
trashappl  5838   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
trashappl  5838   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
trashappl  5838   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
trashappl  5838   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
trashappl  5838   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
trashappl  5838   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
trashappl  5838   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
trashappl  5838   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
trashappl  5838   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
trashappl  5838   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
trashappl  5838   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
trashappl  5838   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
trashappl  5838   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
trashappl  5838   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
trashappl  5838   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
trashappl  5838   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
trashappl  5838   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
trashappl  5838   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
trashappl  5838   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
trashappl  5838   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
trashappl  5838   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
trashappl  5838   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
trashappl  5838   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
trashappl  5838   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
trashappl  5838   bemorder  mem       REG        3,1   54256    5866575 /usr/lib/libpanel-applet-2.so.0.2.21
trashappl  5838   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
trashappl  5838   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
trashappl  5838   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
trashappl  5838   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
trashappl  5838   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
trashappl  5838   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
trashappl  5838   bemorder    0u      CHR        1,3               8184 /dev/null
trashappl  5838   bemorder    1u      CHR        1,3               8184 /dev/null
trashappl  5838   bemorder    2u      CHR        1,3               8184 /dev/null
trashappl  5838   bemorder    3u     unix 0xecb12380              19225 socket
trashappl  5838   bemorder    4r     FIFO        0,6              19227 pipe
trashappl  5838   bemorder    5w     FIFO        0,6              19227 pipe
trashappl  5838   bemorder    6r     FIFO        0,6              19228 pipe
trashappl  5838   bemorder    7w     FIFO        0,6              19228 pipe
trashappl  5838   bemorder    8r     FIFO        0,6              19229 pipe
trashappl  5838   bemorder    9w     FIFO        0,6              19229 pipe
trashappl  5838   bemorder   10u     unix 0xecb12c40              19230 socket
trashappl  5838   bemorder   11u     unix 0xeccce000              19232 /tmp/orbit-bemorder/linc-16ce-0-5ac9fa0fe335d
trashappl  5838   bemorder   12u     unix 0xeccce380              19235 /tmp/orbit-bemorder/linc-16ce-0-5ac9fa0fe335d
trashappl  5838   bemorder   13u     unix 0xecccea80              19239 /tmp/orbit-bemorder/linc-16ce-0-5ac9fa0fe335d
trashappl  5838   bemorder   14u     unix 0xeccce540              19236 socket
trashappl  5838   bemorder   15u     unix 0xecccec40              19240 socket
trashappl  5838   bemorder   16r      DIR       0,10       0          1 inotify
trashappl  5838   bemorder   17u     unix 0xea656700              19252 socket
trashappl  5838   bemorder   18u     unix 0xea6561c0              19249 /tmp/orbit-bemorder/linc-16ce-0-5ac9fa0fe335d
trashappl  5838   bemorder   19u     unix 0xea656380              19250 socket
evolution  5841   bemorder  cwd       DIR        3,1    4096          2 /
evolution  5841   bemorder  rtd       DIR        3,1    4096          2 /
evolution  5841   bemorder  txt       REG        3,1  241808    5898420 /usr/lib/evolution/2.12/evolution-exchange-storage
evolution  5841   bemorder  mem       REG        3,1   24100    5932336 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
evolution  5841   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
evolution  5841   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
evolution  5841   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
evolution  5841   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
evolution  5841   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
evolution  5841   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
evolution  5841   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
evolution  5841   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
evolution  5841   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
evolution  5841   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
evolution  5841   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
evolution  5841   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
evolution  5841   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
evolution  5841   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
evolution  5841   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
evolution  5841   bemorder  mem       REG        3,1   26920    5866981 /usr/lib/libgailutil.so.18.0.1
evolution  5841   bemorder  mem       REG        3,1   77096    5898518 /usr/lib/evolution/2.12/libevolution-a11y.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1   32420    5898531 /usr/lib/evolution/2.12/libevolution-widgets-a11y.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1  110460    5898515 /usr/lib/evolution/2.12/libetext.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1  469596    5898514 /usr/lib/evolution/2.12/libetable.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
evolution  5841   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
evolution  5841   bemorder  mem       REG        3,1  309420    5867447 /usr/lib/libsoftokn3.so.0d
evolution  5841   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
evolution  5841   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
evolution  5841   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
evolution  5841   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
evolution  5841   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
evolution  5841   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
evolution  5841   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
evolution  5841   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
evolution  5841   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
evolution  5841   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
evolution  5841   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
evolution  5841   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
evolution  5841   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
evolution  5841   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
evolution  5841   bemorder  mem       REG        3,1   18816    5866908 /usr/lib/libnm_glib.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1  658996    5866572 /usr/lib/libgtkhtml-3.14.so.19.1.0
evolution  5841   bemorder  mem       REG        3,1   10548    5867254 /usr/lib/liblaunchpad-integration.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1    7052    5867269 /usr/lib/liblpint-bonobo.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1  371424    5898511 /usr/lib/evolution/2.12/libemiscwidgets.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
evolution  5841   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
evolution  5841   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
evolution  5841   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
evolution  5841   bemorder  mem       REG        3,1  152912    5867457 /usr/lib/libssl3.so.0d
evolution  5841   bemorder  mem       REG        3,1  144328    5867441 /usr/lib/libsmime3.so.0d
evolution  5841   bemorder  mem       REG        3,1  462004    5867325 /usr/lib/libnss3.so.0d
evolution  5841   bemorder  mem       REG        3,1  193772    5867324 /usr/lib/libnspr4.so.0d
evolution  5841   bemorder  mem       REG        3,1   14332    5867378 /usr/lib/libplc4.so.0d
evolution  5841   bemorder  mem       REG        3,1    8232    5867379 /usr/lib/libplds4.so.0d
evolution  5841   bemorder  mem       REG        3,1   89120    5867420 /usr/lib/libsasl2.so.2.0.22
evolution  5841   bemorder  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
evolution  5841   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
evolution  5841   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
evolution  5841   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
evolution  5841   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
evolution  5841   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
evolution  5841   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
evolution  5841   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
evolution  5841   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
evolution  5841   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
evolution  5841   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
evolution  5841   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
evolution  5841   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
evolution  5841   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
evolution  5841   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
evolution  5841   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
evolution  5841   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
evolution  5841   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
evolution  5841   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
evolution  5841   bemorder  mem       REG        3,1  180344    5867449 /usr/lib/libsoup-2.2.so.8.5.0
evolution  5841   bemorder  mem       REG        3,1  270152    5866311 /usr/lib/libexchange-storage-1.2.so.3.0.0
evolution  5841   bemorder  mem       REG        3,1  147812    5867066 /usr/lib/libedataserver-1.2.so.9.0.1
evolution  5841   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
evolution  5841   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
evolution  5841   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
evolution  5841   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
evolution  5841   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
evolution  5841   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
evolution  5841   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
evolution  5841   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
evolution  5841   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
evolution  5841   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
evolution  5841   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
evolution  5841   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
evolution  5841   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
evolution  5841   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
evolution  5841   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
evolution  5841   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
evolution  5841   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
evolution  5841   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
evolution  5841   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
evolution  5841   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
evolution  5841   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
evolution  5841   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
evolution  5841   bemorder  mem       REG        3,1  204152    5866869 /usr/lib/libebook-1.2.so.9.1.0
evolution  5841   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
evolution  5841   bemorder  mem       REG        3,1  159764    5866928 /usr/lib/libedataserverui-1.2.so.8.0.2
evolution  5841   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
evolution  5841   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
evolution  5841   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
evolution  5841   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
evolution  5841   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
evolution  5841   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
evolution  5841   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
evolution  5841   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
evolution  5841   bemorder  mem       REG        3,1   57812    5898512 /usr/lib/evolution/2.12/libeshell.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1  305520    5866934 /usr/lib/libcamel-1.2.so.10.0.1
evolution  5841   bemorder  mem       REG        3,1  325764    5867343 /usr/lib/libcamel-provider-1.2.so.10.0.1
evolution  5841   bemorder  mem       REG        3,1  413772    5867087 /usr/lib/libgnomeprint-2-2.so.0.1.0
evolution  5841   bemorder  mem       REG        3,1  644084    5866926 /usr/lib/libecal-1.2.so.7.0.2
evolution  5841   bemorder  mem       REG        3,1  159644    5866116 /usr/lib/libedata-cal-1.2.so.6.0.2
evolution  5841   bemorder  mem       REG        3,1  121628    5865736 /usr/lib/libedata-book-1.2.so.2.4.1
evolution  5841   bemorder  mem       REG        3,1  184344    5898517 /usr/lib/evolution/2.12/libeutil.so.0.0.0
evolution  5841   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
evolution  5841   bemorder  mem       REG        3,1   47212    5867256 /usr/lib/liblber.so.2.0.130
evolution  5841   bemorder  mem       REG        3,1  217924    5867262 /usr/lib/libldap_r.so.2.0.130
evolution  5841   bemorder  mem       REG        3,1 1038208    5866898 /usr/lib/libdb-4.4.so
evolution  5841   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
evolution  5841   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
evolution  5841   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
evolution  5841   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
evolution  5841   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
evolution  5841   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
evolution  5841   bemorder    0u      CHR        1,3               8184 /dev/null
evolution  5841   bemorder    1u      CHR        1,3               8184 /dev/null
evolution  5841   bemorder    2u      CHR        1,3               8184 /dev/null
evolution  5841   bemorder    3u     unix 0xecab3e00              19281 socket
evolution  5841   bemorder    4r     FIFO        0,6              19283 pipe
evolution  5841   bemorder    5w     FIFO        0,6              19283 pipe
evolution  5841   bemorder    6r     FIFO        0,6              19284 pipe
evolution  5841   bemorder    7w     FIFO        0,6              19284 pipe
evolution  5841   bemorder    8r     FIFO        0,6              19285 pipe
evolution  5841   bemorder    9w     FIFO        0,6              19285 pipe
evolution  5841   bemorder   10u     unix 0xecb128c0              19286 socket
evolution  5841   bemorder   11u     unix 0xea7f71c0              19289 socket
evolution  5841   bemorder   12u     unix 0xea7f7540              19291 /tmp/orbit-bemorder/linc-16d1-0-3e90645eb3281
evolution  5841   bemorder   13u     unix 0xea7f78c0              19294 /tmp/orbit-bemorder/linc-16d1-0-3e90645eb3281
evolution  5841   bemorder   14u     unix 0xed469000              19299 /tmp/orbit-bemorder/linc-16d1-0-3e90645eb3281
evolution  5841   bemorder   15u     unix 0xea7f7a80              19296 socket
evolution  5841   bemorder   16r     FIFO        0,6              19300 pipe
evolution  5841   bemorder   17w     FIFO        0,6              19300 pipe
evolution  5841   bemorder   18r     FIFO        0,6              19301 pipe
evolution  5841   bemorder   19w     FIFO        0,6              19301 pipe
mapping-d  5856   bemorder  cwd       DIR        3,1    4096          2 /
mapping-d  5856   bemorder  rtd       DIR        3,1    4096          2 /
mapping-d  5856   bemorder  txt       REG        3,1   25360      65538 /usr/lib/nautilus-cd-burner/mapping-daemon
mapping-d  5856   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
mapping-d  5856   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
mapping-d  5856   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
mapping-d  5856   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
mapping-d  5856   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
mapping-d  5856   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
mapping-d  5856   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
mapping-d  5856   bemorder    0r      CHR        1,3               8184 /dev/null
mapping-d  5856   bemorder    1w     FIFO        0,6              16950 pipe
mapping-d  5856   bemorder    2w     FIFO        0,6              16950 pipe
mapping-d  5856   bemorder    3u     unix 0xee0031c0              19271 /tmp/mapping-bemorder
mapping-d  5856   bemorder    4u     unix 0xed469e00              21011 /tmp/mapping-bemorder
mixer_app  6096   bemorder  cwd       DIR        3,1    4096          2 /
mixer_app  6096   bemorder  rtd       DIR        3,1    4096          2 /
mixer_app  6096   bemorder  txt       REG        3,1   40648    6214046 /usr/lib/gnome-applets/mixer_applet2
mixer_app  6096   bemorder  DEL       REG        0,9             196613 /SYSV00000000
mixer_app  6096   bemorder  mem       REG        3,1   42096    6438965 /usr/lib/gstreamer-0.10/libgstossaudio.so
mixer_app  6096   bemorder  mem       REG        3,1   81100    6438919 /usr/lib/gstreamer-0.10/libgstalsa.so
mixer_app  6096   bemorder  mem       REG        3,1   19492    6438915 /usr/lib/gstreamer-0.10/libgstadder.so
mixer_app  6096   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
mixer_app  6096   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
mixer_app  6096   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
mixer_app  6096   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
mixer_app  6096   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
mixer_app  6096   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
mixer_app  6096   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
mixer_app  6096   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
mixer_app  6096   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
mixer_app  6096   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
mixer_app  6096   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
mixer_app  6096   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
mixer_app  6096   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
mixer_app  6096   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
mixer_app  6096   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
mixer_app  6096   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
mixer_app  6096   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
mixer_app  6096   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
mixer_app  6096   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
mixer_app  6096   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
mixer_app  6096   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
mixer_app  6096   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
mixer_app  6096   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
mixer_app  6096   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
mixer_app  6096   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
mixer_app  6096   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
mixer_app  6096   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
mixer_app  6096   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
mixer_app  6096   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
mixer_app  6096   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
mixer_app  6096   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
mixer_app  6096   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
mixer_app  6096   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
mixer_app  6096   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
mixer_app  6096   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
mixer_app  6096   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
mixer_app  6096   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
mixer_app  6096   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
mixer_app  6096   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
mixer_app  6096   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
mixer_app  6096   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
mixer_app  6096   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
mixer_app  6096   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
mixer_app  6096   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
mixer_app  6096   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
mixer_app  6096   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
mixer_app  6096   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
mixer_app  6096   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
mixer_app  6096   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
mixer_app  6096   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
mixer_app  6096   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
mixer_app  6096   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
mixer_app  6096   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
mixer_app  6096   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
mixer_app  6096   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
mixer_app  6096   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
mixer_app  6096   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
mixer_app  6096   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
mixer_app  6096   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
mixer_app  6096   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
mixer_app  6096   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
mixer_app  6096   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
mixer_app  6096   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
mixer_app  6096   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
mixer_app  6096   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
mixer_app  6096   bemorder  mem       REG        3,1  148140    5867135 /usr/lib/libgstbase-0.10.so.0.12.0
mixer_app  6096   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
mixer_app  6096   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
mixer_app  6096   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
mixer_app  6096   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
mixer_app  6096   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
mixer_app  6096   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
mixer_app  6096   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
mixer_app  6096   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
mixer_app  6096   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
mixer_app  6096   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
mixer_app  6096   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
mixer_app  6096   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
mixer_app  6096   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
mixer_app  6096   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
mixer_app  6096   bemorder  mem       REG        3,1   85152    5865794 /usr/lib/libgnome-desktop-2.so.2.3.10
mixer_app  6096   bemorder  mem       REG        3,1   54256    5866575 /usr/lib/libpanel-applet-2.so.0.2.21
mixer_app  6096   bemorder  mem       REG        3,1  101608    5867133 /usr/lib/libgstaudio-0.10.so.0.9.0
mixer_app  6096   bemorder  mem       REG        3,1   32012    5867145 /usr/lib/libgstinterfaces-0.10.so.0.9.0
mixer_app  6096   bemorder  mem       REG        3,1  650160    5867153 /usr/lib/libgstreamer-0.10.so.0.12.0
mixer_app  6096   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
mixer_app  6096   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
mixer_app  6096   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
mixer_app  6096   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
mixer_app  6096   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
mixer_app  6096   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
mixer_app  6096   bemorder    0u      CHR        1,3               8184 /dev/null
mixer_app  6096   bemorder    1u      CHR        1,3               8184 /dev/null
mixer_app  6096   bemorder    2u      CHR        1,3               8184 /dev/null
mixer_app  6096   bemorder    3u     unix 0xef8fb1c0              19556 socket
mixer_app  6096   bemorder    4r     FIFO        0,6              19558 pipe
mixer_app  6096   bemorder    5w     FIFO        0,6              19558 pipe
mixer_app  6096   bemorder    6r     FIFO        0,6              19559 pipe
mixer_app  6096   bemorder    7w     FIFO        0,6              19559 pipe
mixer_app  6096   bemorder    8r     FIFO        0,6              19560 pipe
mixer_app  6096   bemorder    9w     FIFO        0,6              19560 pipe
mixer_app  6096   bemorder   10u     unix 0xef8fb700              19561 socket
mixer_app  6096   bemorder   11u     unix 0xec7a2a80              19563 /tmp/orbit-bemorder/linc-17d0-0-61cfddbfa0a2
mixer_app  6096   bemorder   12u     unix 0xec7a2540              19566 /tmp/orbit-bemorder/linc-17d0-0-61cfddbfa0a2
mixer_app  6096   bemorder   13u     unix 0xeb457540              19570 /tmp/orbit-bemorder/linc-17d0-0-61cfddbfa0a2
mixer_app  6096   bemorder   14u     unix 0xeb457000              19567 socket
mixer_app  6096   bemorder   15u     unix 0xeb4578c0              19578 /tmp/orbit-bemorder/linc-17d0-0-61cfddbfa0a2
mixer_app  6096   bemorder   16u     unix 0xeb457c40              19579 socket
mixer_app  6096   bemorder   17u     unix 0xeb457e00              19581 socket
mixer_app  6096   bemorder   18u      CHR     116,11              13723 /dev/snd/controlC0
pidgin     6508   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
pidgin     6508   bemorder  rtd       DIR        3,1    4096          2 /
pidgin     6508   bemorder  txt       REG        3,1  703704    5866272 /usr/bin/pidgin
pidgin     6508   bemorder  DEL       REG        0,9             655376 /SYSV00000000
pidgin     6508   bemorder  mem       REG        3,1   81100    6438919 /usr/lib/gstreamer-0.10/libgstalsa.so
pidgin     6508   bemorder  mem       REG        3,1   32036    5867141 /usr/lib/libgstcontroller-0.10.so.0.12.0
pidgin     6508   bemorder  mem       REG        3,1   15696    6438928 /usr/lib/gstreamer-0.10/libgstautodetect.so
pidgin     6508   bemorder  mem       REG        3,1  404500    5867331 /usr/lib/liboil-0.3.so.0.1.0
pidgin     6508   bemorder  mem       REG        3,1   14532    6438991 /usr/lib/gstreamer-0.10/libgstvolume.so
pidgin     6508   bemorder  mem       REG        3,1   35020    6438925 /usr/lib/gstreamer-0.10/libgstaudioresample.so
pidgin     6508   bemorder  mem       REG        3,1   32012    5867145 /usr/lib/libgstinterfaces-0.10.so.0.9.0
pidgin     6508   bemorder  mem       REG        3,1  101608    5867133 /usr/lib/libgstaudio-0.10.so.0.9.0
pidgin     6508   bemorder  mem       REG        3,1   40872    5867155 /usr/lib/libgstriff-0.10.so.0.9.0
pidgin     6508   bemorder  mem       REG        3,1   31084    6438922 /usr/lib/gstreamer-0.10/libgstaudioconvert.so
pidgin     6508   bemorder  mem       REG        3,1   40680    6438995 /usr/lib/gstreamer-0.10/libgstwavparse.so
pidgin     6508   bemorder  mem       REG        3,1   48528    6438979 /usr/lib/gstreamer-0.10/libgsttypefindfunctions.so
pidgin     6508   bemorder  mem       REG        3,1   40668    5867151 /usr/lib/libgstpbutils-0.10.so.0.9.0
pidgin     6508   bemorder  mem       REG        3,1   89224    6438967 /usr/lib/gstreamer-0.10/libgstplaybin.so
pidgin     6508   bemorder  mem       REG        3,1  148140    5867135 /usr/lib/libgstbase-0.10.so.0.12.0
pidgin     6508   bemorder  mem       REG        3,1   33872    6438938 /usr/lib/gstreamer-0.10/libgstdecodebin.so
pidgin     6508   bemorder  mem       REG        3,1  159500    6438934 /usr/lib/gstreamer-0.10/libgstcoreelements.so
pidgin     6508   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
pidgin     6508   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
pidgin     6508   bemorder  mem       REG        3,1   28116    6438948 /usr/lib/gstreamer-0.10/libgstgconfelements.so
pidgin     6508   bemorder  mem       REG        3,1  219996     147458 /usr/lib/nss/libfreebl3.so
pidgin     6508   bemorder  DEL       REG        0,9             262151 /SYSV00000000
pidgin     6508   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
pidgin     6508   bemorder  mem       REG        3,1   90976     786719 /var/lib/aspell/en_US-wo_accents-only.rws
pidgin     6508   bemorder  mem       REG        3,1 2650848     786707 /var/lib/aspell/en-common.rws
pidgin     6508   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
pidgin     6508   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
pidgin     6508   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
pidgin     6508   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
pidgin     6508   bemorder  mem       REG        3,1   66276    4735016 /lib/libbz2.so.1.0.4
pidgin     6508   bemorder  mem       REG        3,1  203840    5866882 /usr/lib/libcroco-0.6.so.3.0.1
pidgin     6508   bemorder  mem       REG        3,1  210652    5867125 /usr/lib/libgsf-1.so.114.0.4
pidgin     6508   bemorder  mem       REG        3,1  192656    5867415 /usr/lib/librsvg-2.so.2.16.1
pidgin     6508   bemorder  mem       REG        3,1   22428    5932325 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
pidgin     6508   bemorder  mem       REG        3,1   14840    5932327 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
pidgin     6508   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
pidgin     6508   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
pidgin     6508   bemorder  mem       REG        3,1   37720     376853 /usr/lib/purple-2/libsimple.so
pidgin     6508   bemorder  mem       REG        3,1  171576    5867281 /usr/lib/libmeanwhile.so.1.0.2
pidgin     6508   bemorder  mem       REG        3,1    5108    5931777 /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
pidgin     6508   bemorder  mem       REG        3,1    8412     376863 /usr/lib/purple-2/ssl-nss.so
pidgin     6508   bemorder  mem       REG        3,1    6068     376838 /usr/lib/purple-2/libaim.so
pidgin     6508   bemorder  mem       REG        3,1    3996     376858 /usr/lib/purple-2/newline.so
pidgin     6508   bemorder  mem       REG        3,1   83380     376852 /usr/lib/purple-2/libsametime.so
pidgin     6508   bemorder  mem       REG        3,1    4736     376834 /usr/lib/purple-2/buddynote.so
pidgin     6508   bemorder  mem       REG        3,1  172500     376851 /usr/lib/purple-2/libqq.so
pidgin     6508   bemorder  mem       REG        3,1   74000     376842 /usr/lib/purple-2/libirc.so
pidgin     6508   bemorder  mem       REG        3,1  102872     376847 /usr/lib/purple-2/libnovell.so
pidgin     6508   bemorder  mem       REG        3,1  872548    5866896 /usr/lib/libdb-4.2.so
pidgin     6508   bemorder  mem       REG        3,1    8444     376833 /usr/lib/purple-2/autoaccept.so
pidgin     6508   bemorder  mem       REG        3,1    8152     376837 /usr/lib/purple-2/joinpart.so
pidgin     6508   bemorder  mem       REG        3,1   13388     524318 /usr/lib/sasl2/libplain.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1   17984     524323 /usr/lib/sasl2/libsasldb.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1   15312     524298 /usr/lib/sasl2/libcrammd5.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1   43460     524303 /usr/lib/sasl2/libdigestmd5.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1 1305220    5947677 /usr/lib/i686/cmov/libcrypto.so.0.9.8
pidgin     6508   bemorder  mem       REG        3,1    3264     376862 /usr/lib/purple-2/ssl-gnutls.so
pidgin     6508   bemorder  mem       REG        3,1   13228     524308 /usr/lib/sasl2/liblogin.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1   12848     524293 /usr/lib/sasl2/libanonymous.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1   89120    5867420 /usr/lib/libsasl2.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1    8792     376836 /usr/lib/purple-2/idle.so
pidgin     6508   bemorder  mem       REG        3,1   29420     524313 /usr/lib/sasl2/libntlm.so.2.0.22
pidgin     6508   bemorder  mem       REG        3,1  164000     376845 /usr/lib/purple-2/libjabber.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1  211596     376855 /usr/lib/purple-2/libyahoo.so
pidgin     6508   bemorder  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
pidgin     6508   bemorder  mem       REG        3,1 1170528    5865498 /usr/lib/libperl.so.5.8.8
pidgin     6508   bemorder  mem       REG        3,1    8092     376859 /usr/lib/purple-2/offlinemsg.so
pidgin     6508   bemorder  mem       REG        3,1    8276     376854 /usr/lib/purple-2/libxmpp.so
pidgin     6508   bemorder  mem       REG        3,1    6552     376861 /usr/lib/purple-2/psychic.so
pidgin     6508   bemorder  mem       REG        3,1    3928     376864 /usr/lib/purple-2/ssl.so
pidgin     6508   bemorder  mem       REG        3,1   37356     376860 /usr/lib/purple-2/perl.so
pidgin     6508   bemorder  mem       REG        3,1  248412     376850 /usr/lib/purple-2/liboscar.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1    6068     376841 /usr/lib/purple-2/libicq.so
pidgin     6508   bemorder  mem       REG        3,1    6868     376835 /usr/lib/purple-2/dbus-example.so
pidgin     6508   bemorder  mem       REG        3,1  172152     376846 /usr/lib/purple-2/libmsn.so
pidgin     6508   bemorder  mem       REG        3,1   52092    5867207 /usr/lib/libhowl.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1   26620     376857 /usr/lib/purple-2/log_reader.so
pidgin     6508   bemorder  mem       REG        3,1    6812     376865 /usr/lib/purple-2/statenotify.so
pidgin     6508   bemorder  mem       REG        3,1   31736     376839 /usr/lib/purple-2/libbonjour.so
pidgin     6508   bemorder  mem       REG        3,1    8796     311302 /usr/lib/pidgin/history.so
pidgin     6508   bemorder  mem       REG        3,1   59796     311309 /usr/lib/pidgin/spellchk.so
pidgin     6508   bemorder  mem       REG        3,1   16536     311299 /usr/lib/pidgin/gestures.so
pidgin     6508   bemorder  mem       REG        3,1    5024     311301 /usr/lib/pidgin/gtkbuddynote.so
pidgin     6508   bemorder  mem       REG        3,1   17264     311305 /usr/lib/pidgin/musicmessaging.so
pidgin     6508   bemorder  mem       REG        3,1   12984     311297 /usr/lib/pidgin/convcolors.so
pidgin     6508   bemorder  mem       REG        3,1   18600     311308 /usr/lib/pidgin/pidginrc.so
pidgin     6508   bemorder  mem       REG        3,1   18676     311307 /usr/lib/pidgin/notify.so
pidgin     6508   bemorder  mem       REG        3,1   26816     311313 /usr/lib/pidgin/xmppconsole.so
pidgin     6508   bemorder  mem       REG        3,1   19024     311310 /usr/lib/pidgin/ticker.so
pidgin     6508   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
pidgin     6508   bemorder  mem       REG        3,1  309420    5867447 /usr/lib/libsoftokn3.so.0d
pidgin     6508   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
pidgin     6508   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
pidgin     6508   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
pidgin     6508   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
pidgin     6508   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
pidgin     6508   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
pidgin     6508   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
pidgin     6508   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
pidgin     6508   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
pidgin     6508   bemorder  mem       REG        3,1  152912    5867457 /usr/lib/libssl3.so.0d
pidgin     6508   bemorder  mem       REG        3,1  144328    5867441 /usr/lib/libsmime3.so.0d
pidgin     6508   bemorder  mem       REG        3,1  462004    5867325 /usr/lib/libnss3.so.0d
pidgin     6508   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
pidgin     6508   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
pidgin     6508   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
pidgin     6508   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
pidgin     6508   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
pidgin     6508   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
pidgin     6508   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
pidgin     6508   bemorder  mem       REG        3,1  193772    5867324 /usr/lib/libnspr4.so.0d
pidgin     6508   bemorder  mem       REG        3,1   14332    5867378 /usr/lib/libplc4.so.0d
pidgin     6508   bemorder  mem       REG        3,1    8232    5867379 /usr/lib/libplds4.so.0d
pidgin     6508   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
pidgin     6508   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
pidgin     6508   bemorder  mem       REG        3,1  305520    5866934 /usr/lib/libcamel-1.2.so.10.0.1
pidgin     6508   bemorder  mem       REG        3,1 1038208    5866898 /usr/lib/libdb-4.4.so
pidgin     6508   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
pidgin     6508   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
pidgin     6508   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
pidgin     6508   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
pidgin     6508   bemorder  mem       REG        3,1  147812    5867066 /usr/lib/libedataserver-1.2.so.9.0.1
pidgin     6508   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
pidgin     6508   bemorder  mem       REG        3,1  204152    5866869 /usr/lib/libebook-1.2.so.9.1.0
pidgin     6508   bemorder  mem       REG        3,1  121628    5865736 /usr/lib/libedata-book-1.2.so.2.4.1
pidgin     6508   bemorder  mem       REG        3,1    4636     311303 /usr/lib/pidgin/iconaway.so
pidgin     6508   bemorder  mem       REG        3,1    7036     311298 /usr/lib/pidgin/extplacement.so
pidgin     6508   bemorder  mem       REG        3,1    9240     311311 /usr/lib/pidgin/timestamp.so
pidgin     6508   bemorder  mem       REG        3,1    7840     311312 /usr/lib/pidgin/timestamp_format.so
pidgin     6508   bemorder  mem       REG        3,1   43672     311300 /usr/lib/pidgin/gevolution.so
pidgin     6508   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
pidgin     6508   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
pidgin     6508   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
pidgin     6508   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
pidgin     6508   bemorder  mem       REG        3,1    8316     311306 /usr/lib/pidgin/nautilus.so
pidgin     6508   bemorder  mem       REG        3,1    9308     311304 /usr/lib/pidgin/markerline.so
pidgin     6508   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
pidgin     6508   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
pidgin     6508   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
pidgin     6508   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
pidgin     6508   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
pidgin     6508   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
pidgin     6508   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
pidgin     6508   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
pidgin     6508   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
pidgin     6508   bemorder  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
pidgin     6508   bemorder  mem       REG        3,1  970680    5865600 /usr/lib/libstdc++.so.6.0.9
pidgin     6508   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
pidgin     6508   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
pidgin     6508   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
pidgin     6508   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
pidgin     6508   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
pidgin     6508   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
pidgin     6508   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
pidgin     6508   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
pidgin     6508   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
pidgin     6508   bemorder  mem       REG        3,1   18816    5866908 /usr/lib/libnm_glib.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
pidgin     6508   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
pidgin     6508   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
pidgin     6508   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
pidgin     6508   bemorder  mem       REG        3,1  742360    5866829 /usr/lib/libaspell.so.15.1.4
pidgin     6508   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
pidgin     6508   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
pidgin     6508   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
pidgin     6508   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
pidgin     6508   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
pidgin     6508   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
pidgin     6508   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
pidgin     6508   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
pidgin     6508   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
pidgin     6508   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
pidgin     6508   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
pidgin     6508   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
pidgin     6508   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
pidgin     6508   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
pidgin     6508   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
pidgin     6508   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
pidgin     6508   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
pidgin     6508   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
pidgin     6508   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
pidgin     6508   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
pidgin     6508   bemorder  mem       REG        3,1  741320    5867398 /usr/lib/libpurple.so.0.0.2
pidgin     6508   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
pidgin     6508   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
pidgin     6508   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
pidgin     6508   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
pidgin     6508   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
pidgin     6508   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
pidgin     6508   bemorder  mem       REG        3,1   10548    5867254 /usr/lib/liblaunchpad-integration.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1   18328    5867178 /usr/lib/libgtkspell.so.0.0.0
pidgin     6508   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
pidgin     6508   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
pidgin     6508   bemorder  mem       REG        3,1    7472    5866801 /usr/lib/libXss.so.1.0.0
pidgin     6508   bemorder  mem       REG        3,1  650160    5867153 /usr/lib/libgstreamer-0.10.so.0.12.0
pidgin     6508   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
pidgin     6508   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
pidgin     6508   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
pidgin     6508   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
pidgin     6508   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
pidgin     6508   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
pidgin     6508   bemorder    0r      CHR        1,3               8184 /dev/null
pidgin     6508   bemorder    1w     FIFO        0,6              16950 pipe
pidgin     6508   bemorder    2w     FIFO        0,6              16950 pipe
pidgin     6508   bemorder    3u     unix 0xeda8e380              19967 socket
pidgin     6508   bemorder    4r     FIFO        0,6              19969 pipe
pidgin     6508   bemorder    5w     FIFO        0,6              19969 pipe
pidgin     6508   bemorder    6u     unix 0xeda8e8c0              19970 socket
pidgin     6508   bemorder    7u     IPv4      20178                TCP dhcp-124-211.imt.uwm.edu:37514->oam-d17c.blue.aol.com:aol (ESTABLISHED)
pidgin     6508   bemorder    8r     FIFO        0,6              19974 pipe
pidgin     6508   bemorder    9w     FIFO        0,6              19974 pipe
pidgin     6508   bemorder   10r     FIFO        0,6              19975 pipe
pidgin     6508   bemorder   11w     FIFO        0,6              19975 pipe
pidgin     6508   bemorder   12r     FIFO        0,6              19978 pipe
pidgin     6508   bemorder   13w     FIFO        0,6              19978 pipe
pidgin     6508   bemorder   14u     unix 0xeda8ee00              19979 socket
pidgin     6508   bemorder   15u     unix 0xe96b41c0              20001 socket
pidgin     6508   bemorder   17w     FIFO        0,6              20047 pipe
pidgin     6508   bemorder   18r     FIFO        0,6              20048 pipe
pidgin     6508   bemorder   19u     IPv4      20087                TCP dhcp-124-211.imt.uwm.edu:38107->abe.imt.uwm.edu:xmpp-client (ESTABLISHED)
pidgin     6508   bemorder   20u     IPv4      20115                TCP dhcp-124-211.imt.uwm.edu:58624->64.12.25.161:aol (ESTABLISHED)
pidgin     6508   bemorder   21u     IPv4      20086                TCP dhcp-124-211.imt.uwm.edu:50138->kc-in-f125.google.com:xmpp-client (ESTABLISHED)
pidgin     6508   bemorder   22u     unix 0xec7a2700              20837 socket
pidgin     6508   bemorder   23u     unix 0xec7a28c0              20839 /tmp/orbit-bemorder/linc-196c-0-5160153451661
pidgin     6508   bemorder   25u     unix 0xf1337a80              20842 /tmp/orbit-bemorder/linc-196c-0-5160153451661
gnome-ter  6882   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
gnome-ter  6882   bemorder  rtd       DIR        3,1    4096          2 /
gnome-ter  6882   bemorder  txt       REG        3,1  295224    5865937 /usr/bin/gnome-terminal
gnome-ter  6882   bemorder  DEL       REG        0,9             458765 /SYSV00000000
gnome-ter  6882   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
gnome-ter  6882   bemorder  DEL       REG        0,9             425996 /SYSV00000000
gnome-ter  6882   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-ter  6882   bemorder  mem       REG        3,1 3066060    6096251 /usr/share/fonts/truetype/baekmuk/dotum.ttf
gnome-ter  6882   bemorder  mem       REG        3,1 7770652    6096266 /usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf
gnome-ter  6882   bemorder  mem       REG        3,1  138175    6111313 /usr/share/fonts/type1/gsfonts/n022003l.pfb
gnome-ter  6882   bemorder  mem       REG        3,1   49224    6096351 /usr/share/fonts/truetype/ttf-bitstream-vera/VeraMono.ttf
gnome-ter  6882   bemorder  mem       REG        3,1  278376    6096363 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
gnome-ter  6882   bemorder  mem       REG        3,1  289712    6096366 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
gnome-ter  6882   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
gnome-ter  6882   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
gnome-ter  6882   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
gnome-ter  6882   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
gnome-ter  6882   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-ter  6882   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1    1584    6342332 /usr/share/vte/termcap/xterm
gnome-ter  6882   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-ter  6882   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-ter  6882   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-ter  6882   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-ter  6882   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-ter  6882   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-ter  6882   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-ter  6882   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-ter  6882   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-ter  6882   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-ter  6882   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-ter  6882   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
gnome-ter  6882   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-ter  6882   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-ter  6882   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-ter  6882   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-ter  6882   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-ter  6882   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-ter  6882   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-ter  6882   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-ter  6882   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-ter  6882   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-ter  6882   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-ter  6882   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-ter  6882   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-ter  6882   bemorder  mem       REG        3,1  271716    4735053 /lib/libncurses.so.5.6
gnome-ter  6882   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-ter  6882   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-ter  6882   bemorder  mem       REG        3,1   43552    5867476 /usr/lib/libpangox-1.0.so.0.1704.0
gnome-ter  6882   bemorder  mem       REG        3,1   25524    5867477 /usr/lib/libpangoxft-1.0.so.0.1704.0
gnome-ter  6882   bemorder  mem       REG        3,1   68908    5866783 /usr/lib/libXft.so.2.1.2
gnome-ter  6882   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
gnome-ter  6882   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
gnome-ter  6882   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
gnome-ter  6882   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-ter  6882   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-ter  6882   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
gnome-ter  6882   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
gnome-ter  6882   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-ter  6882   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-ter  6882   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
gnome-ter  6882   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
gnome-ter  6882   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
gnome-ter  6882   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-ter  6882   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-ter  6882   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-ter  6882   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-ter  6882   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-ter  6882   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-ter  6882   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-ter  6882   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-ter  6882   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-ter  6882   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-ter  6882   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-ter  6882   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-ter  6882   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-ter  6882   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-ter  6882   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-ter  6882   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-ter  6882   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-ter  6882   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-ter  6882   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-ter  6882   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-ter  6882   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-ter  6882   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-ter  6882   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-ter  6882   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-ter  6882   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-ter  6882   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-ter  6882   bemorder  mem       REG        3,1  737496    5867496 /usr/lib/libvte.so.9.2.10
gnome-ter  6882   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
gnome-ter  6882   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
gnome-ter  6882   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
gnome-ter  6882   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
gnome-ter  6882   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
gnome-ter  6882   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
gnome-ter  6882   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
gnome-ter  6882   bemorder  mem       REG        3,1   10548    5867254 /usr/lib/liblaunchpad-integration.so.0.0.0
gnome-ter  6882   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-ter  6882   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-ter  6882   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-ter  6882   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-ter  6882   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-ter  6882   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-ter  6882   bemorder    0r      CHR        1,3               8184 /dev/null
gnome-ter  6882   bemorder    1w     FIFO        0,6              16950 pipe
gnome-ter  6882   bemorder    2w     FIFO        0,6              16950 pipe
gnome-ter  6882   bemorder    3u     unix 0xe8c61540              20269 socket
gnome-ter  6882   bemorder    4r     FIFO        0,6              20271 pipe
gnome-ter  6882   bemorder    5w     FIFO        0,6              20271 pipe
gnome-ter  6882   bemorder    6r     FIFO        0,6              20272 pipe
gnome-ter  6882   bemorder    7w     FIFO        0,6              20272 pipe
gnome-ter  6882   bemorder    8r     FIFO        0,6              20273 pipe
gnome-ter  6882   bemorder    9w     FIFO        0,6              20273 pipe
gnome-ter  6882   bemorder   10u     unix 0xe8c61a80              20274 socket
gnome-ter  6882   bemorder   11u     unix 0xe8c61700              20277 socket
gnome-ter  6882   bemorder   12u     unix 0xe96b4700              20279 /tmp/orbit-bemorder/linc-1ae2-0-5990a009c29ce
gnome-ter  6882   bemorder   13u     unix 0xe8c2be00              20282 /tmp/orbit-bemorder/linc-1ae2-0-5990a009c29ce
gnome-ter  6882   bemorder   14u     unix 0xe3dcb1c0              20286 /tmp/orbit-bemorder/linc-1ae2-0-5990a009c29ce
gnome-ter  6882   bemorder   15u     unix 0xe8c2ba80              20283 socket
gnome-ter  6882   bemorder   16u     unix 0xe3dcb380              20298 socket
gnome-ter  6882   bemorder   17u      CHR        5,2               4080 /dev/ptmx
gnome-ter  6882   bemorder   18r     FIFO        0,6              20319 pipe
gnome-ter  6882   bemorder   19u     unix 0xe3dcb700              20306 socket
gnome-ter  6882   bemorder   20w     FIFO        0,6              20319 pipe
gnome-ter  6882   bemorder   21r     FIFO        0,6              20320 pipe
gnome-ter  6882   bemorder   22w     FIFO        0,6              20320 pipe
gnome-pty  6895   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
gnome-pty  6895   bemorder  rtd       DIR        3,1    4096          2 /
gnome-pty  6895   bemorder  txt       REG        3,1   10084    6930434 /usr/lib/libvte9/gnome-pty-helper
gnome-pty  6895   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-pty  6895   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-pty  6895   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-pty  6895   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-pty  6895   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-pty  6895   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-pty  6895   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-pty  6895   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-pty  6895   bemorder    0u     unix 0xe3dcb8c0              20307 socket
gnome-pty  6895   bemorder    1u     unix 0xe3dcb8c0              20307 socket
gnome-pty  6895   bemorder    2r      CHR        1,3               8184 /dev/null
gnome-pty  6895   bemorder    5u      REG       0,16    3840      14207 /var/run/utmp
bash       6896   bemorder  cwd       DIR        3,1    4096    4442372 /home/bemorder/Programs/nvu-1.0/icons
bash       6896   bemorder  rtd       DIR        3,1    4096          2 /
bash       6896   bemorder  txt       REG        3,1  700912    5439493 /bin/bash
bash       6896   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
bash       6896   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
bash       6896   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
bash       6896   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
bash       6896   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
bash       6896   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
bash       6896   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
bash       6896   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
bash       6896   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
bash       6896   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
bash       6896   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
bash       6896   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
bash       6896   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
bash       6896   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
bash       6896   bemorder  mem       REG        3,1  271716    4735053 /lib/libncurses.so.5.6
bash       6896   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
bash       6896   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
bash       6896   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
bash       6896   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
bash       6896   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
bash       6896   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
bash       6896   bemorder    0u      CHR      136,0                  2 /dev/pts/0
bash       6896   bemorder    1u      CHR      136,0                  2 /dev/pts/0
bash       6896   bemorder    2u      CHR      136,0                  2 /dev/pts/0
bash       6896   bemorder  255u      CHR      136,0                  2 /dev/pts/0
su         7093       root  cwd       DIR        3,1    4096    4442372 /home/bemorder/Programs/nvu-1.0/icons
su         7093       root  rtd       DIR        3,1    4096          2 /
su         7093       root  txt       REG        3,1   27140    5439590 /bin/su
su         7093       root  mem       REG        3,1   52088    4735549 /lib/security/pam_unix.so
su         7093       root  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
su         7093       root  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
su         7093       root  mem       REG        3,1    2948    4735527 /lib/security/pam_foreground.so
su         7093       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
su         7093       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
su         7093       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
su         7093       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
su         7093       root  mem       REG        3,1    9768    4735535 /lib/security/pam_mail.so
su         7093       root  mem       REG        3,1   11052    4735525 /lib/security/pam_env.so
su         7093       root  mem       REG        3,1    3484    4735541 /lib/security/pam_rootok.so
su         7093       root  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
su         7093       root  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
su         7093       root  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
su         7093       root  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
su         7093       root  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
su         7093       root  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
su         7093       root  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
su         7093       root  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
su         7093       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
su         7093       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
su         7093       root  mem       REG        3,1    8516    4735079 /lib/libpam_misc.so.0.79
su         7093       root  mem       REG        3,1   30596    4735077 /lib/libpam.so.0.79
su         7093       root  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
su         7093       root  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
su         7093       root  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
su         7093       root  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
su         7093       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
su         7093       root  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
su         7093       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
su         7093       root    0u      CHR      136,0                  2 /dev/pts/0
su         7093       root    1u      CHR      136,0                  2 /dev/pts/0
su         7093       root    2u      CHR      136,0                  2 /dev/pts/0
bash       7105       root  cwd       DIR        3,1    4096    4079628 /home/bemorder/Documents
bash       7105       root  rtd       DIR        3,1    4096          2 /
bash       7105       root  txt       REG        3,1  700912    5439493 /bin/bash
bash       7105       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
bash       7105       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
bash       7105       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
bash       7105       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
bash       7105       root  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
bash       7105       root  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
bash       7105       root  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
bash       7105       root  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
bash       7105       root  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
bash       7105       root  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
bash       7105       root  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
bash       7105       root  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
bash       7105       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
bash       7105       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
bash       7105       root  mem       REG        3,1  271716    4735053 /lib/libncurses.so.5.6
bash       7105       root  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
bash       7105       root  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
bash       7105       root  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
bash       7105       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
bash       7105       root  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
bash       7105       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
bash       7105       root    0u      CHR      136,0                  2 /dev/pts/0
bash       7105       root    1u      CHR      136,0                  2 /dev/pts/0
bash       7105       root    2u      CHR      136,0                  2 /dev/pts/0
bash       7105       root  255u      CHR      136,0                  2 /dev/pts/0
run-mozil  7738   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
run-mozil  7738   bemorder  rtd       DIR        3,1    4096          2 /
run-mozil  7738   bemorder  txt       REG        3,1   80308    5439513 /bin/dash
run-mozil  7738   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
run-mozil  7738   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
run-mozil  7738   bemorder    0r      CHR        1,3               8184 /dev/null
run-mozil  7738   bemorder    1w     FIFO        0,6              16950 pipe
run-mozil  7738   bemorder    2w     FIFO        0,6              16950 pipe
run-mozil  7738   bemorder   10r      REG        3,1   10897    4297130 /home/bemorder/Programs/nvu-1.0/run-mozilla.sh
nvu-bin    7743   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
nvu-bin    7743   bemorder  rtd       DIR        3,1    4096          2 /
nvu-bin    7743   bemorder  txt       REG        3,1   70080    4297146 /home/bemorder/Programs/nvu-1.0/nvu-bin
nvu-bin    7743   bemorder  mem       REG        3,1  104703    6111277 /usr/share/fonts/type1/gsfonts/n019003l.pfb
nvu-bin    7743   bemorder  mem       REG        3,1   17884    4768631 /lib/tls/i686/cmov/libnss_dns-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1    6764    4735068 /lib/libnss_mdns4_minimal.so.2
nvu-bin    7743   bemorder  mem       REG        3,1   18760    4442516 /home/bemorder/Programs/nvu-1.0/components/libfileview.so
nvu-bin    7743   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
nvu-bin    7743   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
nvu-bin    7743   bemorder  mem       REG        3,1   94718    6111280 /usr/share/fonts/type1/gsfonts/n019004l.pfb
nvu-bin    7743   bemorder  mem       REG        3,1  103311    6111283 /usr/share/fonts/type1/gsfonts/n019023l.pfb
nvu-bin    7743   bemorder  mem       REG        3,1   74056    4442512 /home/bemorder/Programs/nvu-1.0/components/libxmlextras.so
nvu-bin    7743   bemorder  mem       REG        3,1    7368    4442444 /home/bemorder/Programs/nvu-1.0/components/libnvuhelpers.so
nvu-bin    7743   bemorder  mem       REG        3,1   56660    4442506 /home/bemorder/Programs/nvu-1.0/components/libspellchecker.so
nvu-bin    7743   bemorder  mem       REG        3,1   21720    4442505 /home/bemorder/Programs/nvu-1.0/components/libtxmgr.so
nvu-bin    7743   bemorder  mem       REG        3,1  204988    6096367 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSerif-Bold.ttf
nvu-bin    7743   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
nvu-bin    7743   bemorder  mem       REG        3,1  815748    4442499 /home/bemorder/Programs/nvu-1.0/components/libeditor.so
nvu-bin    7743   bemorder  mem       REG        3,1   98636    4442403 /home/bemorder/Programs/nvu-1.0/components/libappcomps.so
nvu-bin    7743   bemorder  DEL       REG        0,9             524303 /SYSV00000000
nvu-bin    7743   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   43988    4442435 /home/bemorder/Programs/nvu-1.0/components/libjar50.so
nvu-bin    7743   bemorder  mem       REG        3,1  196416    4442455 /home/bemorder/Programs/nvu-1.0/components/libgkplugin.so
nvu-bin    7743   bemorder  mem       REG        3,1   26936    4442386 /home/bemorder/Programs/nvu-1.0/components/libxremoteservice.so
nvu-bin    7743   bemorder  mem       REG        3,1  805628    4442433 /home/bemorder/Programs/nvu-1.0/components/libuconv.so
nvu-bin    7743   bemorder  mem       REG        3,1  366848    4442527 /home/bemorder/Programs/nvu-1.0/components/libhtmlpars.so
nvu-bin    7743   bemorder  mem       REG        3,1   93540    4442412 /home/bemorder/Programs/nvu-1.0/components/libchrome.so
nvu-bin    7743   bemorder  mem       REG        3,1   89692    4442456 /home/bemorder/Programs/nvu-1.0/components/libcomposer.so
nvu-bin    7743   bemorder  mem       REG        3,1   70328    4442438 /home/bemorder/Programs/nvu-1.0/components/libwebbrwsr.so
nvu-bin    7743   bemorder  mem       REG        3,1  171604    4442417 /home/bemorder/Programs/nvu-1.0/components/librdf.so
nvu-bin    7743   bemorder  mem       REG        3,1  174528    4442513 /home/bemorder/Programs/nvu-1.0/components/libimglib2.so
nvu-bin    7743   bemorder  mem       REG        3,1 5942044    4442411 /home/bemorder/Programs/nvu-1.0/components/libgklayout.so
nvu-bin    7743   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
nvu-bin    7743   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
nvu-bin    7743   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
nvu-bin    7743   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
nvu-bin    7743   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
nvu-bin    7743   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
nvu-bin    7743   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
nvu-bin    7743   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
nvu-bin    7743   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
nvu-bin    7743   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
nvu-bin    7743   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
nvu-bin    7743   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
nvu-bin    7743   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
nvu-bin    7743   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
nvu-bin    7743   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
nvu-bin    7743   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
nvu-bin    7743   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
nvu-bin    7743   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
nvu-bin    7743   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
nvu-bin    7743   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
nvu-bin    7743   bemorder  mem       REG        3,1   29740    4442462 /home/bemorder/Programs/nvu-1.0/components/libpipboot.so
nvu-bin    7743   bemorder  mem       REG        3,1  369796    4442384 /home/bemorder/Programs/nvu-1.0/components/libdocshell.so
nvu-bin    7743   bemorder  DEL       REG        0,9             491534 /SYSV00000000
nvu-bin    7743   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
nvu-bin    7743   bemorder  mem       REG        3,1   27860    5866793 /usr/lib/libXp.so.6.2.0
nvu-bin    7743   bemorder  mem       REG        3,1  361032    4442495 /home/bemorder/Programs/nvu-1.0/components/libgfx_gtk.so
nvu-bin    7743   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
nvu-bin    7743   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
nvu-bin    7743   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
nvu-bin    7743   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
nvu-bin    7743   bemorder  mem       REG        3,1   24100    5932336 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
nvu-bin    7743   bemorder  mem       REG        3,1  235620    4442511 /home/bemorder/Programs/nvu-1.0/components/libi18n.so
nvu-bin    7743   bemorder  mem       REG        3,1  773088    4442408 /home/bemorder/Programs/nvu-1.0/components/libnecko.so
nvu-bin    7743   bemorder  mem       REG        3,1   61388    4442502 /home/bemorder/Programs/nvu-1.0/components/libpref.so
nvu-bin    7743   bemorder  mem       REG        3,1  276344    4442406 /home/bemorder/Programs/nvu-1.0/components/libxpconnect.so
nvu-bin    7743   bemorder  mem       REG        3,1   82876    4442483 /home/bemorder/Programs/nvu-1.0/components/libcaps.so
nvu-bin    7743   bemorder  mem       REG        3,1  172948    4442471 /home/bemorder/Programs/nvu-1.0/components/libembedcomponents.so
nvu-bin    7743   bemorder  mem       REG        3,1  211016    4442468 /home/bemorder/Programs/nvu-1.0/components/libwidget_gtk2.so
nvu-bin    7743   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
nvu-bin    7743   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
nvu-bin    7743   bemorder  mem       REG        3,1  326564    5866803 /usr/lib/libXt.so.6.0.0
nvu-bin    7743   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1   25748    4442383 /home/bemorder/Programs/nvu-1.0/components/libsystem-pref.so
nvu-bin    7743   bemorder  mem       REG        3,1   14508    4297149 /home/bemorder/Programs/nvu-1.0/libgtkxtbin.so
nvu-bin    7743   bemorder  mem       REG        3,1  132568    4297152 /home/bemorder/Programs/nvu-1.0/libgkgfx.so
nvu-bin    7743   bemorder  mem       REG        3,1  121836    4442536 /home/bemorder/Programs/nvu-1.0/components/libnsappshell.so
nvu-bin    7743   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
nvu-bin    7743   bemorder  mem       REG        3,1    9488    5882373 /usr/lib/gconv/UTF-16.so
nvu-bin    7743   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
nvu-bin    7743   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
nvu-bin    7743   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
nvu-bin    7743   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
nvu-bin    7743   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
nvu-bin    7743   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
nvu-bin    7743   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
nvu-bin    7743   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
nvu-bin    7743   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
nvu-bin    7743   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
nvu-bin    7743   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
nvu-bin    7743   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
nvu-bin    7743   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
nvu-bin    7743   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
nvu-bin    7743   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
nvu-bin    7743   bemorder  mem       REG        3,1   68908    5866783 /usr/lib/libXft.so.2.1.2
nvu-bin    7743   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
nvu-bin    7743   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
nvu-bin    7743   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
nvu-bin    7743   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
nvu-bin    7743   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
nvu-bin    7743   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
nvu-bin    7743   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
nvu-bin    7743   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
nvu-bin    7743   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
nvu-bin    7743   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
nvu-bin    7743   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
nvu-bin    7743   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
nvu-bin    7743   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
nvu-bin    7743   bemorder  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
nvu-bin    7743   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1  737416    5867931 /usr/lib/libstdc++.so.5.0.7
nvu-bin    7743   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
nvu-bin    7743   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
nvu-bin    7743   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
nvu-bin    7743   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
nvu-bin    7743   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
nvu-bin    7743   bemorder  mem       REG        3,1   43552    5867476 /usr/lib/libpangox-1.0.so.0.1704.0
nvu-bin    7743   bemorder  mem       REG        3,1   25524    5867477 /usr/lib/libpangoxft-1.0.so.0.1704.0
nvu-bin    7743   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
nvu-bin    7743   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
nvu-bin    7743   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
nvu-bin    7743   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
nvu-bin    7743   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
nvu-bin    7743   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
nvu-bin    7743   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
nvu-bin    7743   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
nvu-bin    7743   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
nvu-bin    7743   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
nvu-bin    7743   bemorder  mem       REG        3,1  209148    4297134 /home/bemorder/Programs/nvu-1.0/libnspr4.so
nvu-bin    7743   bemorder  mem       REG        3,1   16192    4297142 /home/bemorder/Programs/nvu-1.0/libplc4.so
nvu-bin    7743   bemorder  mem       REG        3,1   10092    4297138 /home/bemorder/Programs/nvu-1.0/libplds4.so
nvu-bin    7743   bemorder  mem       REG        3,1  734420    4297148 /home/bemorder/Programs/nvu-1.0/libxpcom.so
nvu-bin    7743   bemorder  mem       REG        3,1  506444    4297131 /home/bemorder/Programs/nvu-1.0/libmozjs.so
nvu-bin    7743   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
nvu-bin    7743   bemorder    0r      CHR        1,3               8184 /dev/null
nvu-bin    7743   bemorder    1w     FIFO        0,6              16950 pipe
nvu-bin    7743   bemorder    2w     FIFO        0,6              16950 pipe
nvu-bin    7743   bemorder    3u     unix 0xe2c968c0              20444 socket
nvu-bin    7743   bemorder    4r     FIFO        0,6              20450 pipe
nvu-bin    7743   bemorder    5w     FIFO        0,6              20450 pipe
nvu-bin    7743   bemorder    6r     FIFO        0,6              20451 pipe
nvu-bin    7743   bemorder    7w     FIFO        0,6              20451 pipe
nvu-bin    7743   bemorder    8r     FIFO        0,6              20452 pipe
nvu-bin    7743   bemorder    9w     FIFO        0,6              20452 pipe
nvu-bin    7743   bemorder   10r     FIFO        0,6              20453 pipe
nvu-bin    7743   bemorder   11w     FIFO        0,6              20453 pipe
nvu-bin    7743   bemorder   12r     FIFO        0,6              20454 pipe
nvu-bin    7743   bemorder   13w     FIFO        0,6              20454 pipe
nvu-bin    7743   bemorder   14u     unix 0xe2c96c40              20455 socket
nvu-bin    7743   bemorder   15u     unix 0xe331a1c0              20457 /tmp/orbit-bemorder/linc-1e3f-0-1de568ff92144
nvu-bin    7743   bemorder   16u     unix 0xe331a380              20460 /tmp/orbit-bemorder/linc-1e3f-0-1de568ff92144
nvu-bin    7743   bemorder   17r      REG        3,1   20934    4456569 /home/bemorder/Programs/nvu-1.0/chrome/tipoftheday.jar
nvu-bin    7743   bemorder   22r      REG        3,1  686031    4456501 /home/bemorder/Programs/nvu-1.0/chrome/en-US.jar
nvu-bin    7743   bemorder   23r      REG        3,1 1425748    4456576 /home/bemorder/Programs/nvu-1.0/chrome/toolkit.jar
nvu-bin    7743   bemorder   24r      REG        3,1 1109622    4456602 /home/bemorder/Programs/nvu-1.0/chrome/classic.jar
nvu-bin    7743   bemorder   25r      REG        3,1 3312414    4456571 /home/bemorder/Programs/nvu-1.0/chrome/comm.jar
nvu-bin    7743   bemorder   27r      REG        3,1    7596    4456570 /home/bemorder/Programs/nvu-1.0/chrome/pinger.jar
nautilus  10012   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
nautilus  10012   bemorder  rtd       DIR        3,1    4096          2 /
nautilus  10012   bemorder  txt       REG        3,1 1271240    5867300 /usr/bin/nautilus
nautilus  10012   bemorder  mem       REG        3,1   24100    5932336 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
nautilus  10012   bemorder  DEL       REG        0,9             753668 /SYSV00000000
nautilus  10012   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
nautilus  10012   bemorder  mem       REG        3,1  134512    6096255 /usr/share/fonts/truetype/freefont/FreeMonoBold.ttf
nautilus  10012   bemorder  mem       REG        3,1    5576    4735047 /lib/libkeyutils-1.2.so
nautilus  10012   bemorder  mem       REG        3,1   27844    5867710 /usr/lib/libkrb5support.so.0.1
nautilus  10012   bemorder  mem       REG        3,1  151488    5867452 /usr/lib/libk5crypto.so.3.1
nautilus  10012   bemorder  mem       REG        3,1  558036    5867547 /usr/lib/libkrb5.so.3.3
nautilus  10012   bemorder  mem       REG        3,1  164504    5867267 /usr/lib/libgssapi_krb5.so.2.2
nautilus  10012   bemorder  mem       REG        3,1   14840    5932327 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
nautilus  10012   bemorder  mem       REG        3,1  111136    5931692 /usr/lib/gnome-vfs-2.0/modules/libhttp.so
nautilus  10012   bemorder  mem       REG        3,1   22428    5932325 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-gif.so
nautilus  10012   bemorder  mem       REG        3,1   12132    5932326 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
nautilus  10012   bemorder  mem       REG        3,1   26700    5931693 /usr/lib/gnome-vfs-2.0/modules/libmapping.so
nautilus  10012   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
nautilus  10012   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
nautilus  10012   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
nautilus  10012   bemorder  DEL       REG        0,9             720899 /SYSV00000000
nautilus  10012   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
nautilus  10012   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
nautilus  10012   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
nautilus  10012   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
nautilus  10012   bemorder  mem       REG        3,1   16220    5866813 /usr/lib/libXxf86vm.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1   17200    5866805 /usr/lib/libXtst.so.6.1.0
nautilus  10012   bemorder  mem       REG        3,1  101608    5867133 /usr/lib/libgstaudio-0.10.so.0.9.0
nautilus  10012   bemorder  mem       REG        3,1   32012    5867145 /usr/lib/libgstinterfaces-0.10.so.0.9.0
nautilus  10012   bemorder  mem       REG        3,1  650160    5867153 /usr/lib/libgstreamer-0.10.so.0.12.0
nautilus  10012   bemorder  mem       REG        3,1  148140    5867135 /usr/lib/libgstbase-0.10.so.0.12.0
nautilus  10012   bemorder  mem       REG        3,1  156452    5963849 /usr/lib/nautilus/extensions-1.0/libtotem-properties-page.so
nautilus  10012   bemorder  mem       REG        3,1   35944    5865759 /usr/lib/libhal-storage.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1    7144    4735000 /lib/libcom_err.so.2.1
nautilus  10012   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
nautilus  10012   bemorder  mem       REG        3,1   46788    5865796 /usr/lib/libhal.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1    8788    5867161 /usr/lib/libgstvideo-0.10.so.0.9.0
nautilus  10012   bemorder  mem       REG        3,1   27964    5964368 /usr/lib/nautilus/extensions-1.0/libgnome-mount.so
nautilus  10012   bemorder  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
nautilus  10012   bemorder  mem       REG        3,1  970680    5865600 /usr/lib/libstdc++.so.6.0.9
nautilus  10012   bemorder  mem       REG        3,1 1643736    5867385 /usr/lib/libpoppler.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1   67624    5865649 /usr/lib/libkpathsea.so.4.0.0
nautilus  10012   bemorder  mem       REG        3,1 1665156    5866917 /usr/lib/libdjvulibre.so.15.4.0
nautilus  10012   bemorder  mem       REG        3,1  339696    5867473 /usr/lib/libtiff.so.4.2.1
nautilus  10012   bemorder  mem       REG        3,1  116108    5867383 /usr/lib/libpoppler-glib.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1  363552    5964528 /usr/lib/nautilus/extensions-1.0/libevince-properties-page.so
nautilus  10012   bemorder  mem       REG        3,1   21908    4768625 /lib/tls/i686/cmov/libcrypt-2.6.so
nautilus  10012   bemorder  mem       REG        3,1  133716    5867333 /usr/lib/liboobs-1.so.3.0.0
nautilus  10012   bemorder  mem       REG        3,1    5108    5931777 /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
nautilus  10012   bemorder  mem       REG        3,1    6772    5964375 /usr/lib/nautilus/extensions-1.0/libnautilus-sendto.so
nautilus  10012   bemorder  mem       REG        3,1   20460    5964369 /usr/lib/nautilus/extensions-1.0/libnautilus-burn-extension.so
nautilus  10012   bemorder  mem       REG        3,1  162888    5867287 /usr/lib/libmetacity-private.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1   54256    5866575 /usr/lib/libpanel-applet-2.so.0.2.21
nautilus  10012   bemorder  mem       REG        3,1  114792    5964525 /usr/lib/nautilus/extensions-1.0/libnautilus-themus.so
nautilus  10012   bemorder  mem       REG        3,1  462136    6096357 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Oblique.ttf
nautilus  10012   bemorder  mem       REG        3,1   17884    4768631 /lib/tls/i686/cmov/libnss_dns-2.6.so
nautilus  10012   bemorder  mem       REG        3,1    6764    4735068 /lib/libnss_mdns4_minimal.so.2
nautilus  10012   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
nautilus  10012   bemorder  mem       REG        3,1   10308    5964370 /usr/lib/nautilus/extensions-1.0/libnautilus-fileroller.so
nautilus  10012   bemorder  mem       REG        3,1    6888    5963851 /usr/lib/nautilus/extensions-1.0/libnautilus-fontilus.so
nautilus  10012   bemorder  mem       REG        3,1   10252    5964374 /usr/lib/nautilus/extensions-1.0/libnautilus-gst-shares.so
nautilus  10012   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
nautilus  10012   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   12272    5865879 /usr/lib/libgnome-window-settings.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
nautilus  10012   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
nautilus  10012   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
nautilus  10012   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
nautilus  10012   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
nautilus  10012   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
nautilus  10012   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
nautilus  10012   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
nautilus  10012   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
nautilus  10012   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
nautilus  10012   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
nautilus  10012   bemorder  mem       REG        3,1   66276    4735016 /lib/libbz2.so.1.0.4
nautilus  10012   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
nautilus  10012   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
nautilus  10012   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
nautilus  10012   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
nautilus  10012   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
nautilus  10012   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
nautilus  10012   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
nautilus  10012   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
nautilus  10012   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
nautilus  10012   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
nautilus  10012   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
nautilus  10012   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
nautilus  10012   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
nautilus  10012   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
nautilus  10012   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
nautilus  10012   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
nautilus  10012   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
nautilus  10012   bemorder  mem       REG        3,1  203840    5866882 /usr/lib/libcroco-0.6.so.3.0.1
nautilus  10012   bemorder  mem       REG        3,1  210652    5867125 /usr/lib/libgsf-1.so.114.0.4
nautilus  10012   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
nautilus  10012   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
nautilus  10012   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
nautilus  10012   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
nautilus  10012   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
nautilus  10012   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1   81488    5866936 /usr/lib/libgnome-menu.so.2.1.13
nautilus  10012   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
nautilus  10012   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
nautilus  10012   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
nautilus  10012   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
nautilus  10012   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
nautilus  10012   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
nautilus  10012   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
nautilus  10012   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
nautilus  10012   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
nautilus  10012   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
nautilus  10012   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
nautilus  10012   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
nautilus  10012   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
nautilus  10012   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
nautilus  10012   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
nautilus  10012   bemorder  mem       REG        3,1  165848    5866956 /usr/lib/libexif.so.12.2.0
nautilus  10012   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
nautilus  10012   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
nautilus  10012   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
nautilus  10012   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
nautilus  10012   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
nautilus  10012   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
nautilus  10012   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
nautilus  10012   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
nautilus  10012   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
nautilus  10012   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
nautilus  10012   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
nautilus  10012   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
nautilus  10012   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
nautilus  10012   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
nautilus  10012   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
nautilus  10012   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
nautilus  10012   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
nautilus  10012   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
nautilus  10012   bemorder  mem       REG        3,1   85152    5865794 /usr/lib/libgnome-desktop-2.so.2.3.10
nautilus  10012   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
nautilus  10012   bemorder  mem       REG        3,1   10548    5867254 /usr/lib/liblaunchpad-integration.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1  192656    5867415 /usr/lib/librsvg-2.so.2.16.1
nautilus  10012   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
nautilus  10012   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
nautilus  10012   bemorder  mem       REG        3,1   26920    5866981 /usr/lib/libgailutil.so.18.0.1
nautilus  10012   bemorder  mem       REG        3,1  554124    5867581 /usr/lib/libeel-2.so.2.19.5
nautilus  10012   bemorder  mem       REG        3,1   29788    5866940 /usr/lib/libnautilus-extension.so.1.1.0
nautilus  10012   bemorder  mem       REG        3,1   82328    5866849 /usr/lib/libbeagle.so.0.0.0
nautilus  10012   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
nautilus  10012   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
nautilus  10012   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
nautilus  10012   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
nautilus  10012   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
nautilus  10012   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
nautilus  10012   bemorder    0r      CHR        1,3               8184 /dev/null
nautilus  10012   bemorder    1w     FIFO        0,6              16950 pipe
nautilus  10012   bemorder    2w     FIFO        0,6              16950 pipe
nautilus  10012   bemorder    3u     unix 0xd02bea80              20982 socket
nautilus  10012   bemorder    4r     FIFO        0,6              20984 pipe
nautilus  10012   bemorder    5w     FIFO        0,6              20984 pipe
nautilus  10012   bemorder    6r     FIFO        0,6              20985 pipe
nautilus  10012   bemorder    7w     FIFO        0,6              20985 pipe
nautilus  10012   bemorder    8r     FIFO        0,6              20986 pipe
nautilus  10012   bemorder    9w     FIFO        0,6              20986 pipe
nautilus  10012   bemorder   10u     unix 0xd02be000              20987 socket
nautilus  10012   bemorder   11u     unix 0xd02be8c0              20989 socket
nautilus  10012   bemorder   12u     unix 0xd02bee00              20991 /tmp/orbit-bemorder/linc-271c-0-178def686aaa0
nautilus  10012   bemorder   13u     unix 0xf0ad8540              20994 /tmp/orbit-bemorder/linc-271c-0-178def686aaa0
nautilus  10012   bemorder   14r     FIFO        0,6              20998 pipe
nautilus  10012   bemorder   15w     FIFO        0,6              20998 pipe
nautilus  10012   bemorder   16u     unix 0xf0ad81c0              20999 socket
nautilus  10012   bemorder   17r      DIR       0,10       0          1 inotify
nautilus  10012   bemorder   18u     unix 0xf0ad8c40              21005 /tmp/orbit-bemorder/linc-271c-0-178def686aaa0
nautilus  10012   bemorder   19u     unix 0xf0ad8e00              21002 socket
nautilus  10012   bemorder   21u     unix 0xea656e00              21006 socket
nautilus  10012   bemorder   22u     unix 0xed469a80              21010 socket
nautilus  10012   bemorder   23u     unix 0xf0557000              21014 socket
nautilus  10012   bemorder   24r      CHR        1,9               4047 /dev/urandom
multiload 12628   bemorder  cwd       DIR        3,1    4096          2 /
multiload 12628   bemorder  rtd       DIR        3,1    4096          2 /
multiload 12628   bemorder  txt       REG        3,1   40240    6214048 /usr/lib/gnome-applets/multiload-applet-2
multiload 12628   bemorder  mem       REG        3,1   27844    5866963 /usr/lib/libfam.so.0.0.0
multiload 12628   bemorder  mem       REG        3,1   22368    4735002 /lib/libacl.so.1.1.0
multiload 12628   bemorder  mem       REG        3,1   13448    4735008 /lib/libattr.so.1.1.0
multiload 12628   bemorder  mem       REG        3,1   47616    5931688 /usr/lib/gnome-vfs-2.0/modules/libfile.so
multiload 12628   bemorder  DEL       REG        0,9             851976 /SYSV00000000
multiload 12628   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
multiload 12628   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
multiload 12628   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
multiload 12628   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
multiload 12628   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
multiload 12628   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
multiload 12628   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
multiload 12628   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
multiload 12628   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
multiload 12628   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
multiload 12628   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
multiload 12628   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
multiload 12628   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
multiload 12628   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
multiload 12628   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
multiload 12628   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
multiload 12628   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
multiload 12628   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
multiload 12628   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
multiload 12628   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
multiload 12628   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
multiload 12628   bemorder  mem       REG        3,1  806656    5866702 /usr/lib/libasound.so.2.0.0
multiload 12628   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
multiload 12628   bemorder  mem       REG        3,1   17192    5866748 /usr/lib/libORBitCosNaming-2.so.0.1.0
multiload 12628   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
multiload 12628   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
multiload 12628   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
multiload 12628   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
multiload 12628   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
multiload 12628   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
multiload 12628   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
multiload 12628   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
multiload 12628   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
multiload 12628   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
multiload 12628   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
multiload 12628   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
multiload 12628   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
multiload 12628   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
multiload 12628   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
multiload 12628   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
multiload 12628   bemorder  mem       REG        3,1  140420    5866837 /usr/lib/libaudiofile.so.0.0.2
multiload 12628   bemorder  mem       REG        3,1   41000    5865875 /usr/lib/libesd.so.0.2.38
multiload 12628   bemorder  mem       REG        3,1  121280    5867242 /usr/lib/libjpeg.so.62.0.0
multiload 12628   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
multiload 12628   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
multiload 12628   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
multiload 12628   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
multiload 12628   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
multiload 12628   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
multiload 12628   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
multiload 12628   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
multiload 12628   bemorder  mem       REG        3,1   86888    5866405 /usr/lib/libbonobo-activation.so.4.0.0
multiload 12628   bemorder  mem       REG        3,1  371976    5866404 /usr/lib/libbonobo-2.so.0.0.0
multiload 12628   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
multiload 12628   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
multiload 12628   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
multiload 12628   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
multiload 12628   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
multiload 12628   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
multiload 12628   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
multiload 12628   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
multiload 12628   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
multiload 12628   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
multiload 12628   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
multiload 12628   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
multiload 12628   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
multiload 12628   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
multiload 12628   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
multiload 12628   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
multiload 12628   bemorder  mem       REG        3,1   85024    5866825 /usr/lib/libart_lgpl_2.so.2.3.19
multiload 12628   bemorder  mem       REG        3,1   27144    4735086 /lib/libpopt.so.0.0.0
multiload 12628   bemorder  mem       REG        3,1  172244    5867077 /usr/lib/libgnomecanvas-2.so.0.1400.0
multiload 12628   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
multiload 12628   bemorder  mem       REG        3,1   95220    5867049 /usr/lib/libglade-2.0.so.0.0.7
multiload 12628   bemorder  mem       REG        3,1   63620    5865790 /usr/lib/libgnome-keyring.so.0.1.1
multiload 12628   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
multiload 12628   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
multiload 12628   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
multiload 12628   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
multiload 12628   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
multiload 12628   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
multiload 12628   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
multiload 12628   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
multiload 12628   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
multiload 12628   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
multiload 12628   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
multiload 12628   bemorder  mem       REG        3,1   85892    5867063 /usr/lib/libgnome-2.so.0.1900.0
multiload 12628   bemorder  mem       REG        3,1  378200    5865788 /usr/lib/libbonoboui-2.so.0.0.0
multiload 12628   bemorder  mem       REG        3,1  574916    5867093 /usr/lib/libgnomeui-2.so.0.1900.0
multiload 12628   bemorder  mem       REG        3,1   85152    5865794 /usr/lib/libgnome-desktop-2.so.2.3.10
multiload 12628   bemorder  mem       REG        3,1   64292    5867180 /usr/lib/libgtop-2.0.so.7.1.0
multiload 12628   bemorder  mem       REG        3,1   54256    5866575 /usr/lib/libpanel-applet-2.so.0.2.21
multiload 12628   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
multiload 12628   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
multiload 12628   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
multiload 12628   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
multiload 12628   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
multiload 12628   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
multiload 12628   bemorder    0u      CHR        1,3               8184 /dev/null
multiload 12628   bemorder    1u      CHR        1,3               8184 /dev/null
multiload 12628   bemorder    2u      CHR        1,3               8184 /dev/null
multiload 12628   bemorder    3u     unix 0xed364c40              21331 socket
multiload 12628   bemorder    4r     FIFO        0,6              21333 pipe
multiload 12628   bemorder    5w     FIFO        0,6              21333 pipe
multiload 12628   bemorder    6r     FIFO        0,6              21334 pipe
multiload 12628   bemorder    7w     FIFO        0,6              21334 pipe
multiload 12628   bemorder    8r     FIFO        0,6              21335 pipe
multiload 12628   bemorder    9w     FIFO        0,6              21335 pipe
multiload 12628   bemorder   10u     unix 0xed364000              21336 socket
multiload 12628   bemorder   11u     unix 0xe96b4000              21338 /tmp/orbit-bemorder/linc-3154-0-17e6274a38b24
multiload 12628   bemorder   12u     unix 0xe96b4a80              21341 /tmp/orbit-bemorder/linc-3154-0-17e6274a38b24
multiload 12628   bemorder   13u     unix 0xe8c2b1c0              21346 /tmp/orbit-bemorder/linc-3154-0-17e6274a38b24
multiload 12628   bemorder   14u     unix 0xe8c61000              21342 socket
multiload 12628   bemorder   15u     unix 0xe8c2b700              21355 socket
multiload 12628   bemorder   16u     unix 0xe8c2bc40              21354 /tmp/orbit-bemorder/linc-3154-0-17e6274a38b24
multiload 12628   bemorder   17u     unix 0xe8c2b540              21357 socket
gnome-sys 12654   bemorder  cwd       DIR        3,1    4096    4079618 /home/bemorder
gnome-sys 12654   bemorder  rtd       DIR        3,1    4096          2 /
gnome-sys 12654   bemorder  txt       REG        3,1  208152    5866835 /usr/bin/gnome-system-monitor
gnome-sys 12654   bemorder  DEL       REG        0,9             917522 /SYSV00000000
gnome-sys 12654   bemorder  mem       REG        3,1  289712    6096366 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
gnome-sys 12654   bemorder  DEL       REG        0,9             884745 /SYSV00000000
gnome-sys 12654   bemorder  mem       REG        3,1   66276    4735016 /lib/libbz2.so.1.0.4
gnome-sys 12654   bemorder  mem       REG        3,1  203840    5866882 /usr/lib/libcroco-0.6.so.3.0.1
gnome-sys 12654   bemorder  mem       REG        3,1  210652    5867125 /usr/lib/libgsf-1.so.114.0.4
gnome-sys 12654   bemorder  mem       REG        3,1  192656    5867415 /usr/lib/librsvg-2.so.2.16.1
gnome-sys 12654   bemorder  mem       REG        3,1    5108    5931777 /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
gnome-sys 12654   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
gnome-sys 12654   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
gnome-sys 12654   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
gnome-sys 12654   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
gnome-sys 12654   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
gnome-sys 12654   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
gnome-sys 12654   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
gnome-sys 12654   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
gnome-sys 12654   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
gnome-sys 12654   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
gnome-sys 12654   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
gnome-sys 12654   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
gnome-sys 12654   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
gnome-sys 12654   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
gnome-sys 12654   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
gnome-sys 12654   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
gnome-sys 12654   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
gnome-sys 12654   bemorder  mem       REG        3,1  219668    4735097 /lib/libsepol.so.1
gnome-sys 12654   bemorder  mem       REG        3,1  325604    5866996 /usr/lib/libgcrypt.so.11.2.3
gnome-sys 12654   bemorder  mem       REG        3,1   11468    5867107 /usr/lib/libgpg-error.so.0.3.0
gnome-sys 12654   bemorder  mem       REG        3,1   60916    5867467 /usr/lib/libtasn1.so.3.0.9
gnome-sys 12654   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
gnome-sys 12654   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
gnome-sys 12654   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
gnome-sys 12654   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
gnome-sys 12654   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
gnome-sys 12654   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
gnome-sys 12654   bemorder  mem       REG        3,1    9696    4768642 /lib/tls/i686/cmov/libutil-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   83516    4735096 /lib/libselinux.so.1
gnome-sys 12654   bemorder  mem       REG        3,1   67408    4768638 /lib/tls/i686/cmov/libresolv-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   59728    5866839 /usr/lib/libavahi-client.so.3.2.2
gnome-sys 12654   bemorder  mem       REG        3,1   41800    5866841 /usr/lib/libavahi-common.so.3.4.4
gnome-sys 12654   bemorder  mem       REG        3,1    9424    5866845 /usr/lib/libavahi-glib.so.1.0.1
gnome-sys 12654   bemorder  mem       REG        3,1  457092    5867103 /usr/lib/libgnutls.so.13.3.0
gnome-sys 12654   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
gnome-sys 12654   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
gnome-sys 12654   bemorder  mem       REG        3,1    5748    5866758 /usr/lib/libXRes.so.1.0.0
gnome-sys 12654   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
gnome-sys 12654   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
gnome-sys 12654   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
gnome-sys 12654   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   42700    4734998 /lib/libgcc_s.so.1
gnome-sys 12654   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1  970680    5865600 /usr/lib/libstdc++.so.6.0.9
gnome-sys 12654   bemorder  mem       REG        3,1   30988    5867369 /usr/lib/libpcrecpp.so.0.0.0
gnome-sys 12654   bemorder  mem       REG        3,1  129736    5867367 /usr/lib/libpcre.so.3.12.0
gnome-sys 12654   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
gnome-sys 12654   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
gnome-sys 12654   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
gnome-sys 12654   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
gnome-sys 12654   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
gnome-sys 12654   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
gnome-sys 12654   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
gnome-sys 12654   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
gnome-sys 12654   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
gnome-sys 12654   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
gnome-sys 12654   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
gnome-sys 12654   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
gnome-sys 12654   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
gnome-sys 12654   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
gnome-sys 12654   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
gnome-sys 12654   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
gnome-sys 12654   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
gnome-sys 12654   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
gnome-sys 12654   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
gnome-sys 12654   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
gnome-sys 12654   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
gnome-sys 12654   bemorder  mem       REG        3,1   10548    5867254 /usr/lib/liblaunchpad-integration.so.0.0.0
gnome-sys 12654   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
gnome-sys 12654   bemorder  mem       REG        3,1   19996    5867436 /usr/lib/libsigc-2.0.so.0.0.0
gnome-sys 12654   bemorder  mem       REG        3,1  353196    5865922 /usr/lib/libglibmm-2.4.so.1.0.24
gnome-sys 12654   bemorder  mem       REG        3,1   91356    5866866 /usr/lib/libcairomm-1.0.so.1.0.0
gnome-sys 12654   bemorder  mem       REG        3,1  180652    5866588 /usr/lib/libpangomm-1.4.so.1.0.30
gnome-sys 12654   bemorder  mem       REG        3,1  277280    5865931 /usr/lib/libatkmm-1.6.so.1.0.30
gnome-sys 12654   bemorder  mem       REG        3,1  297692    5866018 /usr/lib/libgdkmm-2.4.so.1.0.30
gnome-sys 12654   bemorder  mem       REG        3,1 3455940    5866124 /usr/lib/libgtkmm-2.4.so.1.0.30
gnome-sys 12654   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
gnome-sys 12654   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
gnome-sys 12654   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
gnome-sys 12654   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
gnome-sys 12654   bemorder  mem       REG        3,1  354104    5867095 /usr/lib/libgnomevfs-2.so.0.1900.2
gnome-sys 12654   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
gnome-sys 12654   bemorder  mem       REG        3,1  219416    5866859 /usr/lib/libwnck-1.so.22.2.0
gnome-sys 12654   bemorder  mem       REG        3,1   64292    5867180 /usr/lib/libgtop-2.0.so.7.1.0
gnome-sys 12654   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
gnome-sys 12654   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
gnome-sys 12654   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
gnome-sys 12654   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
gnome-sys 12654   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
gnome-sys 12654   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
gnome-sys 12654   bemorder    0r      CHR        1,3               8184 /dev/null
gnome-sys 12654   bemorder    1u      CHR        1,3               8184 /dev/null
gnome-sys 12654   bemorder    2u      CHR        1,3               8184 /dev/null
gnome-sys 12654   bemorder    3u     unix 0xf1337c40              21375 socket
gnome-sys 12654   bemorder    4u     unix 0xed364700              21377 /tmp/gnome-system-monitor.bemorder.2417439404
gnome-sys 12654   bemorder    5r     FIFO        0,6              21379 pipe
gnome-sys 12654   bemorder    6w     FIFO        0,6              21379 pipe
gnome-sys 12654   bemorder    7r     FIFO        0,6              21380 pipe
gnome-sys 12654   bemorder    8w     FIFO        0,6              21380 pipe
gnome-sys 12654   bemorder    9r     FIFO        0,6              21381 pipe
gnome-sys 12654   bemorder   10w     FIFO        0,6              21381 pipe
gnome-sys 12654   bemorder   11u     unix 0xed364380              21382 socket
gnome-sys 12654   bemorder   12u     unix 0xc2a23000              21384 /tmp/orbit-bemorder/linc-316e-0-704935f758b2a
gnome-sys 12654   bemorder   13u     unix 0xc2a23380              21387 /tmp/orbit-bemorder/linc-316e-0-704935f758b2a
gnome-sys 12654   bemorder   14u     unix 0xc26a0000              21421 socket
wpa_suppl 12799       root  cwd       DIR        3,1    4096          2 /
wpa_suppl 12799       root  rtd       DIR        3,1    4096          2 /
wpa_suppl 12799       root  txt       REG        3,1  319140    1261734 /sbin/wpa_supplicant
wpa_suppl 12799       root  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
wpa_suppl 12799       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
wpa_suppl 12799       root  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
wpa_suppl 12799       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
wpa_suppl 12799       root  mem       REG        3,1 1305220    5947677 /usr/lib/i686/cmov/libcrypto.so.0.9.8
wpa_suppl 12799       root  mem       REG        3,1  261004    5947678 /usr/lib/i686/cmov/libssl.so.0.9.8
wpa_suppl 12799       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
wpa_suppl 12799       root    0r      CHR        1,3               8184 /dev/null
wpa_suppl 12799       root    1u      CHR        1,3               8184 /dev/null
wpa_suppl 12799       root    2u      CHR        1,3               8184 /dev/null
wpa_suppl 12799       root    3u     unix 0xc2a23e00              22033 /var/run/wpa_supplicant-global
wpa_suppl 12799       root    4u     sock        0,5              22046 can't identify protocol
wpa_suppl 12799       root    5u     sock        0,5              22047 can't identify protocol
wpa_suppl 12799       root    6u     sock        0,5              22050 can't identify protocol
wpa_suppl 12799       root    7u     unix 0xf79b2700              22052 /var/run/wpa_supplicant/eth3
notificat 12842   bemorder  cwd       DIR        3,1    4096          2 /
notificat 12842   bemorder  rtd       DIR        3,1    4096          2 /
notificat 12842   bemorder  txt       REG        3,1   28660     114689 /usr/lib/notification-daemon/notification-daemon
notificat 12842   bemorder  DEL       REG        0,9             950291 /SYSV00000000
notificat 12842   bemorder  mem       REG        3,1  493320    6096354 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
notificat 12842   bemorder  mem       REG        3,1   15048    5932329 /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
notificat 12842   bemorder  mem       REG        3,1 2611976    6211469 /usr/share/icons/hicolor/icon-theme.cache
notificat 12842   bemorder  mem       REG        3,1 7313432    6211473 /usr/share/icons/gnome/icon-theme.cache
notificat 12842   bemorder  mem       REG        3,1  519412    6096358 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
notificat 12842   bemorder  mem       REG        3,1    6752    5898788 /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
notificat 12842   bemorder  mem       REG        3,1   22880     786525 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    3088     787206 /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    8376     787205 /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1992     787204 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    2040     787203 /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   12424     787202 /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    2736     787201 /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1168     787200 /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    6824     787199 /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    5352     787198 /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    3600     787197 /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    8040     787196 /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   21136     787195 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    7312     787194 /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    6768     787193 /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   30352     787192 /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   20616     787191 /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1624     787190 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    7792     787189 /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   21672     787188 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    9936     787187 /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   13136     786508 /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    5184     786821 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1128     787231 /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    3032     787230 /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1040     787229 /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1504     787228 /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1216     787227 /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    8888     787226 /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   18360     787225 /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    7712     787224 /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    4080     787223 /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    6336     787222 /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    2152     787221 /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   19136     787220 /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   16664     787219 /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   10808     787218 /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   10208     787217 /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    2120     787216 /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    6120     787215 /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   14528     787214 /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   22840     787213 /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1    1400     787212 /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   29360     787211 /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   72492    5931743 /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
notificat 12842   bemorder  mem       REG        3,1 1164328    5866217 /usr/lib/libxml2.so.2.6.29
notificat 12842   bemorder  mem       REG        3,1   60144    5867432 /usr/lib/libsexy.so.2.0.4
notificat 12842   bemorder  mem       REG        3,1    5672     787210 /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   12280     787209 /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   10224     786535 /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
notificat 12842   bemorder  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
notificat 12842   bemorder  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
notificat 12842   bemorder  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
notificat 12842   bemorder  mem       REG        3,1   20276    5964386 /usr/lib/notification-daemon-1.0/engines/libubuntu.so
notificat 12842   bemorder  mem       REG        3,1    5384    5882319 /usr/lib/gconv/ISO8859-1.so
notificat 12842   bemorder  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
notificat 12842   bemorder  mem       REG        3,1      54    5948109 /usr/lib/locale/en_US.utf8/LC_NUMERIC
notificat 12842   bemorder  mem       REG        3,1    2451    5948112 /usr/lib/locale/en_US.utf8/LC_TIME
notificat 12842   bemorder  mem       REG        3,1  880094    5948103 /usr/lib/locale/en_US.utf8/LC_COLLATE
notificat 12842   bemorder  mem       REG        3,1     286    5948107 /usr/lib/locale/en_US.utf8/LC_MONETARY
notificat 12842   bemorder  mem       REG        3,1      52    5948113 /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
notificat 12842   bemorder  mem       REG        3,1      34    5948110 /usr/lib/locale/en_US.utf8/LC_PAPER
notificat 12842   bemorder  mem       REG        3,1      77    5948108 /usr/lib/locale/en_US.utf8/LC_NAME
notificat 12842   bemorder  mem       REG        3,1  139688    5867381 /usr/lib/libpng12.so.0.15.0
notificat 12842   bemorder  mem       REG        3,1  126716    5866959 /usr/lib/libexpat.so.1.0.0
notificat 12842   bemorder  mem       REG        3,1   80536    5866059 /usr/lib/libz.so.1.2.3.3
notificat 12842   bemorder  mem       REG        3,1  450636    5866993 /usr/lib/libfreetype.so.6.3.16
notificat 12842   bemorder  mem       REG        3,1  184672    5867460 /usr/lib/libpangoft2-1.0.so.0.1704.0
notificat 12842   bemorder  mem       REG        3,1   16616    5866773 /usr/lib/libXdmcp.so.6.0.0
notificat 12842   bemorder  mem       REG        3,1    6988    5866762 /usr/lib/libXau.so.6.0.0
notificat 12842   bemorder  mem       REG        3,1   56156    5866777 /usr/lib/libXext.so.6.4.0
notificat 12842   bemorder  mem       REG        3,1    5748    5866758 /usr/lib/libXRes.so.1.0.0
notificat 12842   bemorder  mem       REG        3,1   87440    5866734 /usr/lib/libICE.so.6.3.0
notificat 12842   bemorder  mem       REG        3,1   28092    5866752 /usr/lib/libSM.so.6.0.0
notificat 12842   bemorder  mem       REG        3,1   31308    5867459 /usr/lib/libstartup-notification-1.so.0.0.0
notificat 12842   bemorder  mem       REG        3,1   14128    5866779 /usr/lib/libXfixes.so.3.1.0
notificat 12842   bemorder  mem       REG        3,1  480728    5866972 /usr/lib/libcairo.so.2.11.5
notificat 12842   bemorder  mem       REG        3,1  257644    5867326 /usr/lib/libpango-1.0.so.0.1704.0
notificat 12842   bemorder  mem       REG        3,1    5992    5866771 /usr/lib/libXdamage.so.1.1.0
notificat 12842   bemorder  mem       REG        3,1    6476    5866767 /usr/lib/libXcomposite.so.1.0.0
notificat 12842   bemorder  mem       REG        3,1   32800    5866769 /usr/lib/libXcursor.so.1.0.2
notificat 12842   bemorder  mem       REG        3,1   22136    5866797 /usr/lib/libXrandr.so.2.1.0
notificat 12842   bemorder  mem       REG        3,1   29016    5865495 /usr/lib/libXi.so.6.0.0
notificat 12842   bemorder  mem       REG        3,1    6548    5866787 /usr/lib/libXinerama.so.1.0.0
notificat 12842   bemorder  mem       REG        3,1   28744    5866799 /usr/lib/libXrender.so.1.3.0
notificat 12842   bemorder  mem       REG        3,1  176080    5866965 /usr/lib/libfontconfig.so.1.2.0
notificat 12842   bemorder  mem       REG        3,1   33424    5867327 /usr/lib/libpangocairo-1.0.so.0.1704.0
notificat 12842   bemorder  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
notificat 12842   bemorder  mem       REG        3,1  105088    5866833 /usr/lib/libatk-1.0.so.0.1912.1
notificat 12842   bemorder  mem       REG        3,1   30624    4768639 /lib/tls/i686/cmov/librt-2.6.so
notificat 12842   bemorder  mem       REG        3,1   14456    5866688 /usr/lib/libgthread-2.0.so.0.1306.0
notificat 12842   bemorder  mem       REG        3,1  325216    5866744 /usr/lib/libORBit-2.so.0.1.0
notificat 12842   bemorder  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
notificat 12842   bemorder  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
notificat 12842   bemorder  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
notificat 12842   bemorder  mem       REG        3,1  112355    4768637 /lib/tls/i686/cmov/libpthread-2.6.so
notificat 12842   bemorder  mem       REG        3,1  760620    5866216 /usr/lib/libglib-2.0.so.0.1306.0
notificat 12842   bemorder  mem       REG        3,1   10224    5866226 /usr/lib/libgmodule-2.0.so.0.1306.0
notificat 12842   bemorder  mem       REG        3,1  249360    5866598 /usr/lib/libgobject-2.0.so.0.1306.0
notificat 12842   bemorder  mem       REG        3,1  986540    5866756 /usr/lib/libX11.so.6.2.0
notificat 12842   bemorder  mem       REG        3,1   93516    5867522 /usr/lib/libgdk_pixbuf-2.0.so.0.1105.0
notificat 12842   bemorder  mem       REG        3,1  585448    5867359 /usr/lib/libgdk-x11-2.0.so.0.1105.0
notificat 12842   bemorder  mem       REG        3,1 3882200    5867593 /usr/lib/libgtk-x11-2.0.so.0.1105.0
notificat 12842   bemorder  mem       REG        3,1  219416    5866859 /usr/lib/libwnck-1.so.22.2.0
notificat 12842   bemorder  mem       REG        3,1  200484    5865818 /usr/lib/libgconf-2.so.4.1.2
notificat 12842   bemorder  mem       REG        3,1  203808    5866901 /usr/lib/libdbus-1.so.3.2.0
notificat 12842   bemorder  mem       REG        3,1  110136    5866863 /usr/lib/libdbus-glib-1.so.2.1.0
notificat 12842   bemorder  mem       REG        3,1     155    5948102 /usr/lib/locale/en_US.utf8/LC_ADDRESS
notificat 12842   bemorder  mem       REG        3,1      59    5948111 /usr/lib/locale/en_US.utf8/LC_TELEPHONE
notificat 12842   bemorder  mem       REG        3,1      23    5948106 /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
notificat 12842   bemorder  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
notificat 12842   bemorder  mem       REG        3,1     391    5948105 /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
notificat 12842   bemorder  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
notificat 12842   bemorder    0u      CHR        1,3               8184 /dev/null
notificat 12842   bemorder    1u      CHR        1,3               8184 /dev/null
notificat 12842   bemorder    2u      CHR        1,3               8184 /dev/null
notificat 12842   bemorder    3u     unix 0xf726e000              22104 socket
notificat 12842   bemorder    4u      CHR        1,3               8184 /dev/null
notificat 12842   bemorder    5r     FIFO        0,6              22106 pipe
notificat 12842   bemorder    6w     FIFO        0,6              22106 pipe
notificat 12842   bemorder    7r     FIFO        0,6              22107 pipe
notificat 12842   bemorder    8w     FIFO        0,6              22107 pipe
notificat 12842   bemorder    9r     FIFO        0,6              22108 pipe
notificat 12842   bemorder   10w     FIFO        0,6              22108 pipe
notificat 12842   bemorder   11u     unix 0xf726e540              22109 socket
notificat 12842   bemorder   12u     unix 0xf726e8c0              22111 /tmp/orbit-bemorder/linc-322a-0-436a6cc0ed997
notificat 12842   bemorder   13u     unix 0xf726ec40              22114 /tmp/orbit-bemorder/linc-322a-0-436a6cc0ed997
notificat 12842   bemorder   14u     unix 0xf726ee00              22121 socket
dhclient  12856       dhcp  cwd       DIR        3,1    4096          2 /
dhclient  12856       dhcp  rtd       DIR        3,1    4096          2 /
dhclient  12856       dhcp  txt       REG        3,1  352904    1261632 /sbin/dhclient3
dhclient  12856       dhcp  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
dhclient  12856       dhcp  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
dhclient  12856       dhcp  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
dhclient  12856       dhcp  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
dhclient  12856       dhcp  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
dhclient  12856       dhcp  mem       REG        3,1   11088    4735019 /lib/libcap.so.1.10
dhclient  12856       dhcp  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
dhclient  12856       dhcp    0r      CHR        1,3               8184 /dev/null
dhclient  12856       dhcp    1w      CHR        1,3               8184 /dev/null
dhclient  12856       dhcp    2w      CHR        1,3               8184 /dev/null
dhclient  12856       dhcp    3u     unix 0xc26a0700              22204 socket
dhclient  12856       dhcp    4w      REG        3,1    1034     786872 /var/lib/dhcp3/dhclient.eth3.leases
dhclient  12856       dhcp    6u     IPv4      22243                UDP *:bootpc 
dhclient  12856       dhcp    7u     sock        0,5              22242 can't identify protocol
sh        15677       root  cwd       DIR        3,1    4096          2 /
sh        15677       root  rtd       DIR        3,1    4096          2 /
sh        15677       root  txt       REG        3,1   80308    5439513 /bin/dash
sh        15677       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
sh        15677       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
sh        15677       root    0r      CHR        1,3               8184 /dev/null
sh        15677       root    1w      REG        3,1  252795     786803 /var/log/acpid
sh        15677       root    2w      REG        3,1  252795     786803 /var/log/acpid
sh        15677       root    5u     unix 0xdfb9d8c0              15029 /var/run/acpid.socket
sh        15677       root    6u     unix 0xf2e628c0              15765 /var/run/acpid.socket
lm_batter 15678       root  cwd       DIR        3,1    4096          2 /
lm_batter 15678       root  rtd       DIR        3,1    4096          2 /
lm_batter 15678       root  txt       REG        3,1  700912    5439493 /bin/bash
lm_batter 15678       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
lm_batter 15678       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
lm_batter 15678       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
lm_batter 15678       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
lm_batter 15678       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
lm_batter 15678       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
lm_batter 15678       root  mem       REG        3,1  271716    4735053 /lib/libncurses.so.5.6
lm_batter 15678       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
lm_batter 15678       root    0r      CHR        1,3               8184 /dev/null
lm_batter 15678       root    1w      REG        3,1  252795     786803 /var/log/acpid
lm_batter 15678       root    2w      REG        3,1  252795     786803 /var/log/acpid
lm_batter 15678       root    5u     unix 0xdfb9d8c0              15029 /var/run/acpid.socket
lm_batter 15678       root    6u     unix 0xf2e628c0              15765 /var/run/acpid.socket
lm_batter 15678       root  255r      REG        3,1     181    2572640 /etc/acpi/actions/lm_battery.sh
laptop_mo 15679       root  cwd       DIR        3,1    4096          2 /
laptop_mo 15679       root  rtd       DIR        3,1    4096          2 /
laptop_mo 15679       root  txt       REG        3,1  700912    5439493 /bin/bash
laptop_mo 15679       root  mem       REG        3,1   38416    4768632 /lib/tls/i686/cmov/libnss_files-2.6.so
laptop_mo 15679       root  mem       REG        3,1   34352    4768634 /lib/tls/i686/cmov/libnss_nis-2.6.so
laptop_mo 15679       root  mem       REG        3,1   83712    4768629 /lib/tls/i686/cmov/libnsl-2.6.so
laptop_mo 15679       root  mem       REG        3,1   30436    4768630 /lib/tls/i686/cmov/libnss_compat-2.6.so
laptop_mo 15679       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
laptop_mo 15679       root  mem       REG        3,1    9684    4768626 /lib/tls/i686/cmov/libdl-2.6.so
laptop_mo 15679       root  mem       REG        3,1  271716    4735053 /lib/libncurses.so.5.6
laptop_mo 15679       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
laptop_mo 15679       root    0r      CHR        1,3               8184 /dev/null
laptop_mo 15679       root    1w      REG        3,1  252795     786803 /var/log/acpid
laptop_mo 15679       root    2w      REG        3,1  252795     786803 /var/log/acpid
laptop_mo 15679       root    3r     FIFO        0,6              27380 pipe
laptop_mo 15679       root    5u     unix 0xdfb9d8c0              15029 /var/run/acpid.socket
laptop_mo 15679       root    6u     unix 0xf2e628c0              15765 /var/run/acpid.socket
laptop_mo 15679       root  255r      REG        3,1   53092    5867628 /usr/sbin/laptop_mode
awk       15691       root  cwd       DIR        3,1    4096          2 /
awk       15691       root  rtd       DIR        3,1    4096          2 /
awk       15691       root  txt       REG        3,1   94616    5866144 /usr/bin/mawk
awk       15691       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
awk       15691       root  mem       REG        3,1  153424    4768627 /lib/tls/i686/cmov/libm-2.6.so
awk       15691       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
awk       15691       root    0r      CHR        1,3               8184 /dev/null
awk       15691       root    1w     FIFO        0,6              27380 pipe
awk       15691       root    2w      REG        3,1  252795     786803 /var/log/acpid
awk       15691       root    3r      REG        0,3       0 4026532233 /proc/acpi/ac_adapter/AC/state
awk       15691       root    5u     unix 0xdfb9d8c0              15029 /var/run/acpid.socket
awk       15691       root    6u     unix 0xf2e628c0              15765 /var/run/acpid.socket
lsof      15692       root  cwd       DIR        3,1    4096    4079628 /home/bemorder/Documents
lsof      15692       root  rtd       DIR        3,1    4096          2 /
lsof      15692       root  txt       REG        3,1  106272    5866126 /usr/bin/lsof
lsof      15692       root  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
lsof      15692       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
lsof      15692       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
lsof      15692       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
lsof      15692       root    0u      CHR      136,0                  2 /dev/pts/0
lsof      15692       root    1w      REG        3,1       0    4079976 /home/bemorder/Documents/log.txt
lsof      15692       root    2u      CHR      136,0                  2 /dev/pts/0
lsof      15692       root    3r      DIR        0,3       0          1 /proc
lsof      15692       root    4r      DIR        0,3       0      27404 /proc/15692/fd
lsof      15692       root    5w     FIFO        0,6              27407 pipe
lsof      15692       root    6r     FIFO        0,6              27408 pipe
lsof      15693       root  cwd       DIR        3,1    4096    4079628 /home/bemorder/Documents
lsof      15693       root  rtd       DIR        3,1    4096          2 /
lsof      15693       root  txt       REG        3,1  106272    5866126 /usr/bin/lsof
lsof      15693       root  mem       REG        3,1  238336    5948104 /usr/lib/locale/en_US.utf8/LC_CTYPE
lsof      15693       root  mem       REG        3,1 1339780    4768623 /lib/tls/i686/cmov/libc-2.6.so
lsof      15693       root  mem       REG        3,1   25486    5882378 /usr/lib/gconv/gconv-modules.cache
lsof      15693       root  mem       REG        3,1  109144    4735593 /lib/ld-2.6.so
lsof      15693       root    4r     FIFO        0,6              27407 pipe
lsof      15693       root    7w     FIFO        0,6              27408 pipe

---

### Post by gsiliceo on 2007-07-18
DUde you seriusly think somebody will read all that list, try to keep your request for help friendly, before posting, ask your self would i read it?

---

### Post by digitalbenji on 2007-07-18
7.1 alpha 2 (gutsy tribe 2) is not even in beta stage.  First, I would recommend reposting this in the approrpriate forum (the gutsy forum).  Second, oddities like this are to be expected from alpha stage stuff.  If you are looking for stability, you could try a forced downgrade of nautilus, but I would just recommend using feisty.

---

