---
title: "SSH timed out during apt-get dist-upgrade"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by will81 on 2011-08-24
Hi,

I ran apt-get dist-upgrade (after apt-get update, of course) on our server then left it for a bit.  I returned periodically, usually to answer a question (keep old / use new, etc).  When I came back this time, the SSH session had timed out but I can see there is a script still waiting for me to answer a question.  I'm using the server edition so don't have a GUI.

ps aux yields:

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2532  1432 ?        Ss   Jun01   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   Jun01   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   Jun01   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        R<   Jun01   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   Jun01   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S<   Jun01   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   Jun01   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S<   Jun01   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kintegrityd/0]
root        12  0.0  0.0      0     0 ?        S<   Jun01   0:10 [kblockd/0]
root        13  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kacpid]
root        14  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kacpi_notify]
root        15  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kacpi_hotplug]
root        16  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ata/0]
root        17  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ata_aux]
root        18  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ksuspend_usbd]
root        19  0.0  0.0      0     0 ?        S<   Jun01   0:00 [khubd]
root        20  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kseriod]
root        21  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kmmcd]
root        22  0.0  0.0      0     0 ?        S<   Jun01   0:00 [bluetooth]
root        23  0.0  0.0      0     0 ?        S    Jun01   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S<   Jun01   1:09 [kswapd0]
root        27  0.0  0.0      0     0 ?        S<   Jun01   0:00 [aio/0]
root        28  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   Jun01   0:00 [crypto/0]
root        33  0.0  0.0      0     0 ?        S<   Jun01   0:00 [scsi_eh_0]
root        34  0.0  0.0      0     0 ?        S<   Jun01   0:00 [scsi_eh_1]
root        35  0.0  0.0      0     0 ?        S<   Jun01   0:00 [scsi_eh_2]
root        37  0.0  0.0      0     0 ?        S<   Jun01   0:00 [scsi_eh_3]
root        40  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kstriped]
root        41  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kmpathd/0]
root        42  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kmpath_handlerd]
root        43  0.0  0.0      0     0 ?        S<   Jun01   0:00 [ksnapd]
root        44  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kondemand/0]
root        45  0.0  0.0      0     0 ?        S<   Jun01   0:00 [kconservative/0]
root        46  0.0  0.0      0     0 ?        S<   Jun01   0:00 [krfcommd]
root       316  0.0  0.0      0     0 ?        S<   Jun01   4:29 [kjournald]
root       352  0.0  0.0   2580  1184 ?        S    Jun01   5:44 mountall --daemon --tmptime=0
root       367  0.0  0.0   2156   612 ?        S    Jun01   0:00 upstart-udev-bridge --daemon
root       632  0.0  0.0      0     0 ?        S<   Jun01   0:00 [i915/0]
104        764  0.0  0.1   2716  1284 ?        Ss   Jun01   0:00 dbus-daemon --system --fork
root       882  0.0  0.0   1708   500 tty4     Ss+  Jun01   0:00 /sbin/getty -8 38400 tty4
root       888  0.0  0.0   1708   504 tty5     Ss+  Jun01   0:00 /sbin/getty -8 38400 tty5
root       896  0.0  0.0   1708   500 tty2     Ss+  Jun01   0:00 /sbin/getty -8 38400 tty2
root       897  0.0  0.0   1708   496 tty3     Ss+  Jun01   0:00 /sbin/getty -8 38400 tty3
root       899  0.0  0.0   1708   504 tty6     Ss+  Jun01   0:00 /sbin/getty -8 38400 tty6
root       932  0.0  0.0   5364  1040 ?        Ss   Jun01   0:00 /usr/sbin/sshd
root      1160  0.0  0.2  79704  3520 ?        Sl   Jun01  13:01 /opt/avg/avg8/bin//avgd 
root      1174  0.0  0.2  57632  2620 ?        Sl   Jun01   0:00 /opt/avg/avg8/bin/avgavid 
root      1201  0.0  0.2  58968  2808 ?        Sl   Jun01   0:06 /opt/avg/avg8/bin/avgsched 
root      1568  0.0  1.0  17312 12992 ?        Ss   Jun01   0:18 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root      1570  0.0  0.0   1708   504 tty1     Ss+  Jun01   0:00 /sbin/getty -8 38400 tty1
root      1594  0.0  0.2   5600  3092 ?        S    13:44   0:00 /bin/bash
root      1821  0.0  1.5  24184 20164 ?        S    13:54   0:02 apt-get dist-upgrade
root      3651  0.0  0.0   2180   644 ?        S<s  14:00   0:00 udevd --daemon
root      7803  0.0  0.1  19300  2424 ?        Ssl  Jun02   0:00 /usr/sbin/console-kit-daemon
root     10354  0.0  0.0   5364  1036 ?        Ss   Jul29   0:00 /usr/sbin/sshd -o PidFile=/var/run/release-upgrader-sshd.pid -p 9004
root     22928  0.0  0.0   2376   900 ?        Ss   14:25   0:00 cron
syslog   23210  0.0  0.1  23280  1380 ?        Sl   14:25   0:00 rsyslogd -c4
root     23452  0.0  0.0   1936   544 ?        Ss   14:25   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
daemon   23525  0.0  0.0   2248   432 ?        Ss   14:25   0:00 atd
107      23800  0.0  0.0  14080  1268 ?        Ss   14:25   0:00 /usr/sbin/exim4 -bd -q30m
root     24389  0.0  0.2   5644  3272 pts/1    Ss+  14:23   0:00 /usr/bin/dpkg --status-fd 25 --configure libc6-i686 libck-connector0 libdbus-glib-1-2 libeggdbus-1-0 libpolkit-gobject-1-0 libxau6 libxdmcp6 l
root     26163  0.0  0.0      0     0 ?        S    Aug23   0:00 [pdflush]
root     29375  0.0  0.2   8792  3008 ?        Ss   15:50   0:00 sshd: will [priv]
will     29388  0.0  0.1   8792  1532 ?        S    15:50   0:00 sshd: will@pts/2 
will     29389  0.0  0.2   5576  2912 pts/2    Ss   15:50   0:00 -bash
will     29480  0.0  0.0   1832   548 pts/2    S    15:50   0:00 /bin/sh /etc/bastille-tmpdir-defense.sh 29389
will     29510  0.0  0.0   3236   640 pts/2    S    15:50   0:00 sleep 7200
root     29543  0.0  0.2   5568  2908 pts/2    S    15:51   0:00 /bin/bash
root     29639  0.0  0.2   8792  3012 ?        Ss   16:04   0:00 sshd: will [priv]
will     29653  0.0  0.1   8792  1532 ?        S    16:05   0:00 sshd: will@pts/3 
will     29654  0.0  0.2   5576  2912 pts/3    Ss   16:05   0:00 -bash
will     29745  0.0  0.0   1832   552 pts/3    S    16:05   0:00 /bin/sh /etc/bastille-tmpdir-defense.sh 29654
will     29788  0.0  0.0   3236   640 pts/3    S    16:05   0:00 sleep 7200
root     29790  0.0  0.2   5580  2960 pts/3    S+   16:05   0:00 /bin/bash
ntp      30856  0.0  0.1   4416  1360 ?        Ss   16:15   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 109:119
root     31146  0.0  0.6  10784  7756 pts/1    S+   16:15   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/mysql-server-5.1.postinst configure 5.1.37-1ubuntu5.5
root     31156  0.0  0.1   4316  1504 pts/1    S+   16:15   0:00 /bin/bash -e /var/lib/dpkg/info/mysql-server-5.1.postinst configure 5.1.37-1ubuntu5.5
root     31234  0.0  0.0   3796  1092 pts/1    S+   16:15   0:00 start mysql
root     31824  0.0  0.0      0     0 ?        S    04:02   0:00 [pdflush]
root     32170  0.0  0.0   1832   508 ?        Ss   16:22   0:00 /bin/sh -e /dev/fd/13
root     32175  0.0  0.0   1772   444 ?        S    16:22   0:00 sleep 1
root     32176  0.0  0.0   2716  1044 pts/2    R+   16:22   0:00 ps aux
```

I thought processes were killed with expired SSH sessions but it looks like processes 1821 ... 31234 may be something to do with my old session - particularly 24389, whose whole line reads:

```
root     24389  0.0  0.2   5644  3272 pts/1    Ss+  14:23   0:00 /usr/bin/dpkg --status-fd 25 --configure libc6-i686 libck-connector0 libdbus-glib-1-2 libeggdbus-1-0 libpolkit-gobject-1-0 libxau6 libxdmcp6 libxcb1 libx11-data libx11-6 libexpat1 dbus consolekit module-init-tools libdevmapper1.02.1 dmsetup hdparm libpcre3 net-tools libbz2-1.0 libgdbm3 perl perl-modules bzip2 libperl5.10 netbase libpng12-0 libklibc klibc-utils busybox-initramfs cpio xkb-data makedev libusb-0.1-4 procps libgmp3c2 libmpfr1ldbl cpp-4.4 mime-support libncursesw5 readline-common libreadline6 libsqlite3-0 python2.6 libpython2.6 python python-support python-simplejson python-httplib2 python-central python-pkg-resources python-lazr.uri python-wadllib python-zope.interface python-lazr.restfulclient python-launchpadlib python-twisted-bin python-twisted-core mawk libntfs-3g75 ntfs-3g wireless-crda linux-image-2.6.32-33-generic linux-image-2.6.32-33-generic-pae mktemp libdbi-perl libmysqlclient16 libdbd-mysql-perl mysql-client-core-5.1 libwrap0 mysql-client-5.1 psmisc mysql-server-core-5.1 mysql-server-5.1 mysql-server ubuntu-serverguide x11-common apt-utils libsigc++-2.0-0c2a libcwidget3 libxapian15 libept0 aptitude console-terminus console-setup kbd cron dhcp3-common dhcp3-client dmidecode eject libmagic1 file gpgv gnupg libgpg-error0 libgcrypt11 libtasn1-3 libgnutls26 libkeyutils1 libkrb5support0 libk5crypto3 libkrb5-3 libgssapi-krb5-2 libidn11 libsasl2-2 libsasl2-modules libldap-2.4-2 libcurl3-gnutls gnupg-curl iproute iputils-ping laptop-detect less libatm1 libcap2 libsub-name-perl libclass-accessor-perl libfribidi0 libgpm2 liblockfile1 libnewt0.52 python-newt libtimedate-perl libparse-debianchangelog-perl libpopt0 lockfile-progs logrotate lsb-release make netcat-openbsd ntpdate openssl ucf rsyslog sudo tasksel tasksel-data ubuntu-keyring locales ureadahead vim-common vim-runtime vim vim-tiny whiptail ubuntu-minimal apparmor libterm-readkey-perl liburi-perl libhtml-parser-perl libwww-perl libxml-parser-perl libxml2 libxml-sax-perl libxml-libxml-perl librpc-xml-perl libapparmor1 libapparmor-perl apparmor-utils apt-transport-https at bash-completion libgeoip1 libisc60 libdns64 libisccc60 libisccfg60 libbind9-60 liblwres60 bind9-host cpp bsdmainutils busybox-static python-apt command-not-found-data python-gdbm command-not-found dnsutils dosfstools ed libpq5 exim4-config exim4-base exim4-daemon-heavy exim4 friendly-recovery ftp geoip-database gettext-base groff-base info iptables iputils-arping iputils-tracepath libcap-ng0 irqbalance iso-codes language-selector-common libbsd0 libedit2 libelf1 libgc1c2 libmailtools-perl libpcap0.8 libpci3 pciutils libxext6 libxmuu1 usbutils lshw lsof ltrace man-db manpages memtest86+ mlocate mtr-tiny nano openssh-client openssh-server libparted0debian1 parted plymouth-theme-ubuntu-text powermgmt-base ppp pppoeconf python-gnupginterface rsync strace tcpdump telnet time wget ubuntu-standard ufw update-manager-core uuid-runtime w3m xauth xml-core libapr1 libaprutil1 libaprutil1-ldap libaprutil1-dbd-sqlite3 apache2.2-bin apache2-utils apache2.2-common apache2-mpm-prefork apache2 python-problem-report python-apport apport apport-symptoms awstats libcurses-perl bastille bc binutils-static bsd-mailx screen byobu gcc-4.3-base cpp-4.3 cpu-checker libcurl3 curl dbus-x11 defoma dovecot-common dovecot-imapd dovecot-pop3d libfreetype6 ttf-dejavu-core fontconfig-config libfontconfig1 grub-common grub installation-report python-pycurl python-pexpect python-smartpm python-dbus libffi5 python-gobject landscape-common mlock libc-client2007e php5-common php5-cli libapache2-mod-php5 php5-imap libmcrypt4 php5-mcrypt php5-curl php5-xmlrpc libjpeg62 libxpm4 libgd2-xpm libt1-5 php5-gd php5-mysql libapt-pkg-perl libauthen-pam-perl libcarp-clan-perl libbit-vector-perl libcompress-raw-bzip2-perl libcompress-raw-zlib-perl libio-compress-perl libcompress-zlib-perl libio-compress-base-per
l libio-compress-zlib-perl libdate-calc-perl libdb4.6 libdb4.7 libfile-copy-recursive-perl libglib2.0-data libio-pty-perl libjs-jquery libltdl7 libnl1 libpam-ck-connector libpcsclite1 libpolkit2 libpolkit-dbus2 libpolkit-grant2
```

Should I just kill this process and rerun it, or is there a tidier way to recover?

Thanks in advance.

---

