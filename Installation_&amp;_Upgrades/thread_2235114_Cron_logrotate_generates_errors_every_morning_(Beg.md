---
title: "Cron logrotate generates errors every morning (Beginner)"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by Rocketeer on 2014-07-19
Every morning I recieve the same error messages from my headless server. I already tried to reinstall the packages, but without luck. Currently ps3mediaserver and squid are deinstalled. Upstart is not deinstallable (used for system suff I guess).

```

Subject: Cron <root@rocketserver> test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
/etc/cron.daily/logrotate:
error: error accessing /var/log/ps3mediaserver: No such file or directory
error: ps3mediaserver:1 glob failed for /var/log/ps3mediaserver/*/*.log
error: found error in /var/log/ps3mediaserver/*/*.log , skipping
error: error accessing /var/log/squid: No such file or directory
error: squid:4 glob failed for /var/log/squid/*.log
error: found error in /var/log/squid/*.log , skipping
error: error accessing /var/log/upstart: No such file or directory
error: upstart:1 glob failed for /var/log/upstart/*.log
error: found error in /var/log/upstart/*.log , skipping

```

---

### Post by steeldriver on 2014-07-19
How did you install / desinstall ps3mediaserver and squid? (from repositories, or from PPA? or source?) - it sounds like some files got left behind. 

What are the contents of your /etc/cron.daily directory?

---

### Post by Rocketeer on 2014-07-20
Following are my contents for cron.daily

I now used dpkg --purge ps3mediaserver - so maybe there are 3 messages less next time in the error log.

```

drwxr-xr-x 147 root root  12K Jul 20 12:25 ..
-rwxr-xr-x   1 root root  633 Apr  1  2009 apache2
-rwxr-xr-x   1 root root  219 Apr 10  2012 apport
-rwxr-xr-x   1 root root  16K Jun 15  2012 apt
-rwxr-xr-x   1 root root  314 Feb 10  2009 aptitude
-rwxr-xr-x   1 root root   77 May  1  2011 apt-show-versions
-rwxr-xr-x   1 root root  502 Nov  4  2008 bsdmainutils
-rwxr-xr-x   1 root root  256 Sep 20  2009 dpkg
-rwxr-xr-x   1 root root  372 Oct  4  2011 logrotate
-rwxr-xr-x   1 root root 1.4K Mar 31  2012 man-db
-rwxr-xr-x   1 root root  539 Apr 28  2011 mdadm
-rwxr-xr-x   1 root root  606 Mar 24  2010 mlocate
-rwxr-xr-x   1 root root  249 Feb 21  2011 passwd
-rw-r--r--   1 root root  102 Nov 12  2008 .placeholder
-rwxr-xr-x   1 root root 2.4K Jul  1  2011 popularity-contest
-rwxr-xr-x   1 root root  383 Mar 27  2009 samba
-rwxr-xr-x   1 root root 2.9K Apr  2  2012 standard
-rwxr-xr-x   1 root root 1.3K Jan 23  2009 sysklogd
-rwxr-xr-x   1 root root  214 May 23  2012 update-notifier-common

```

---

