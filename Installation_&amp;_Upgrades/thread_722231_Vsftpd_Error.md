---
title: "Vsftpd Error"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Daoism on 2008-03-12
I can't install Vsftpd at all.

Its gave me this error

sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporari                                                                              ly unavailable)
E: Unable to lock the download directory

```
  ps -ax
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00 [migration/0]
    4 ?        SN     0:00 [ksoftirqd/0]
    5 ?        S<     0:00 [watchdog/0]
    6 ?        S<     0:00 [events/0]
    7 ?        S<     0:00 [khelper]
   26 ?        S<     0:00 [kblockd/0]
   27 ?        S<     0:00 [kacpid]
   28 ?        S<     0:00 [kacpi_notify]
   87 ?        S<     0:00 [kseriod]
  110 ?        S      0:00 [pdflush]
  111 ?        S      0:00 [pdflush]
  112 ?        S<     0:00 [kswapd0]
  164 ?        S<     0:00 [aio/0]
 1810 ?        S<     0:00 [ata/0]
 1811 ?        S<     0:00 [ata_aux]
 1813 ?        S<     0:00 [scsi_eh_0]
 1814 ?        S<     0:00 [scsi_eh_1]
 1837 ?        S<     0:00 [scsi_eh_2]
 2080 ?        S<     0:00 [kjournald]
 2238 ?        S<s    0:01 /sbin/udevd --daemon
 3066 ?        S<     0:00 [kpsmoused]
 3598 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 3599 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 3605 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 3608 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 3611 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 3612 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 3648 ?        Ss     0:00 /sbin/syslogd -u syslog
 3667 ?        S      0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 3669 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 3695 ?        Ssl    0:00 /usr/sbin/named -u bind
 3717 ?        Ss     0:00 /usr/sbin/sshd
 3771 ?        S      0:00 /bin/sh /usr/bin/mysqld_safe
 3811 ?        Sl     0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking
 3812 ?        S      0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
 3887 ?        Ss     0:00 /usr/sbin/atd
 3898 ?        Ss     0:00 /usr/sbin/cron
 3952 ?        Ss     0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
 4943 ?        Ss     0:00 /usr/sbin/apache2 -k start
 5340 ?        S      0:00 /usr/sbin/apache2 -k start
 5341 ?        S      0:00 /usr/sbin/apache2 -k start
 5342 ?        S      0:00 /usr/sbin/apache2 -k start
 5343 ?        S      0:00 /usr/sbin/apache2 -k start
 5344 ?        S      0:00 /usr/sbin/apache2 -k start
 5366 ?        S      0:00 /usr/sbin/apache2 -k start
 5626 ?        S      0:00 /usr/share/webmin/software/install_pack.cgi
 5649 ?        S      0:00 sh -c yes Yes | apt-get -y --force-yes -f install vsftpd 2>&1 2>/dev/null
 5650 ?        S      0:00 yes Yes
 5651 ?        S      0:00 apt-get -y --force-yes -f install vsftpd
 5653 ?        S      0:00 /usr/lib/apt/methods/cdrom
 5675 ?        Zs     0:00 [dpkg] <defunct>
 6145 ?        Ss     0:00 sshd: user1 [priv]
 6147 ?        R      0:00 sshd: user1@pts/0
 6148 pts/0    Ss     0:00 -bash
 6304 pts/0    R+     0:00 ps -ax

```

Does anyone know how to fix this problems. Im using 7.10 + installed mysql, php5, bind9, webmin, apach2...Everything as 7.10 server but i can't install vsftp.

Thanks,
Daoism

---

