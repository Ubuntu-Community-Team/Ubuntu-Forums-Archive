---
title: "Kernel panic when attempting to run Jaunty amd64"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by graysky on 2009-03-28
When I attempt to boot into Jaunty I get a bunch of debug info and a kernel panic - not syncing: Attempted to kill init!  Wish I could see the logs to post here but that's about it.  This happens if I try to boot from the livecd ('try ubuntu without making changes to your computer) or from my HDD.

If I boot into Intrepid and mount the /dev/sdb3 (where jaunty is installed) most of my log files are 0 byte files or contain a single line that reads "(Nothing has been logged yet.)"

Advice?

```
$ ls -lt /mnt/jaunty/var/log
total 864
drwxr-xr-x 2 root   root   4096 2009-03-28 09:43 installer
-rw-r--r-- 1 root   root  32032 2009-03-28 09:41 faillog
-rw-rw-r-- 1 root   utmp 292292 2009-03-28 09:41 lastlog
-rw-r----- 1 root   adm  731566 2009-03-23 20:24 dpkg.log
-rw-r--r-- 1 root   root   2157 2009-03-23 20:18 fontconfig.log
-rw-r--r-- 1 root   root      0 2009-03-23 20:07 pycentral.log
drwxr-xr-x 2 root   root   4096 2009-03-23 20:04 apt
-rw-r--r-- 1 root   root  38839 2009-03-23 19:57 bootstrap.log
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 auth.log
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 daemon.log
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 debug
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 kern.log
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 lpr.log
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 mail.err
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 mail.info
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 mail.log
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 mail.warn
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 messages
drwxr-sr-x 2 news   news   4096 2009-03-23 19:57 news
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 syslog
-rw-r----- 1 syslog adm       0 2009-03-23 19:57 user.log
-rw-r----- 1 root   adm      31 2009-03-23 19:56 boot
-rw-r----- 1 root   adm      31 2009-03-23 19:56 dmesg
drwxr-xr-x 2 root   root   4096 2009-03-23 19:56 fsck
-rw-rw-r-- 1 root   utmp      0 2009-03-23 19:55 btmp
-rw-rw-r-- 1 root   utmp      0 2009-03-23 19:55 wtmp
drwxr-xr-x 2 root   root   4096 2009-03-23 07:55 apparmor
drwxr-xr-x 2 root   root   4096 2009-03-20 17:40 dist-upgrade
drwxr-xr-x 2 root   root   4096 2009-03-19 08:55 gdm
drwxr-xr-x 2 root   root   4096 2009-03-18 22:08 ConsoleKit
drwxr-x--- 2 root   adm    4096 2009-03-16 12:00 samba
drwxr-xr-x 2 root   root   4096 2009-03-10 09:07 cups
drwxr-xr-x 2 root   root   4096 2009-03-02 05:07 unattended-upgrades
```

---

### Post by graysky on 2009-03-28
Cold booted and everything works... can't explain it!

---

