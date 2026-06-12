---
title: "proftpd debacle"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by MG5thAve on 2007-02-19
So I was a moron and did something stupid. I accidentally deleted the /etc/init.d/proftpd script. Now, I am unable to manage the package correctly (install, remove, purge, etc). I've tried a few things like repairing the install, (apt-get -f install proftpd), but that doesn't work correctly. I've tried replacing the script file with a general script, but that doesn't work either. I've looked around a bit but I feel like I'm starting to waste my time. Does anybody know how to fix this issue? My ultimate goal is to just purge the thing completely from my system (config, install, etc).. and start from square one to reinstall it again. Any help would be appreciated. Thanks.

---

### Post by taurus on 2007-02-19
```
sudo aptitude --purge remove proftpd
sudo aptitude update
sudo aptitude install proftpd gproftpd
gksudo gproftpd
```

---

### Post by MG5thAve on 2007-02-19
Hey thanks Taurus... that seemed to get the thing installed. Unfortunately, now I'm unsure about how to get the ftp server started up because there's no script in /etc/init.d for proftpd. The package manager does show that proftpd, the common files, and the gdk configuration tools are installed however.

---

### Post by taurus on 2007-02-19
What's the output of this command then?

```
ls -la /etc/init.d
```

---

### Post by MG5thAve on 2007-02-19
Sorry for the delay.. working on another machine. Here's the directory read out:

```
root@InfernalContraption:/home/mgeorges# ls -la /etc/init.d
total 396
drwxr-xr-x   2 root root 2416 2007-02-19 15:29 .
drwxr-xr-x 106 root root 5856 2007-02-19 15:30 ..
-rwxr-xr-x   1 root root 2442 2005-09-15 14:30 acpid
-rwxr-xr-x   1 root root  867 2006-03-28 11:26 acpi-support
-rwxr-xr-x   1 root root 9282 2006-05-29 08:03 alsa-utils
-rwxr-xr-x   1 root root 1015 2005-05-02 22:10 anacron
-rwxr-xr-x   1 root root 4705 2006-05-28 21:55 apache2
-rwxr-xr-x   1 root root 1386 2005-05-23 18:15 apmd
-rwxr-xr-x   1 root root 1387 2006-05-08 17:44 atd
-rwxr-xr-x   1 root root 5298 2006-03-20 00:52 bluez-utils
-rw-r--r--   1 root root 2553 2006-05-23 06:39 bootclean.sh
-rwxr-xr-x   1 root root 1788 2006-05-23 06:39 bootlogd
-rwxr-xr-x   1 root root 2030 2006-05-23 06:39 bootmisc.sh
-rwxr-xr-x   1 root root  881 2006-04-20 05:28 brltty
-rwxr-xr-x   1 root root 1984 2006-05-23 06:39 checkfs.sh
-rwxr-xr-x   1 root root 8831 2006-05-23 06:39 checkroot.sh
-rwxr-xr-x   1 root root 5979 2006-01-23 11:50 console-screen.sh
-rwxr-xr-x   1 root root 1159 2006-06-08 04:27 courier-authdaemon
-rwxr-xr-x   1 root root 2267 2006-06-08 04:27 courier-imap
-rwxr-xr-x   1 root root 1739 2005-11-15 07:42 cron
-rwxr-xr-x   1 root root 1949 2006-07-10 18:55 cupsys
-rwxr-xr-x   1 root root 2557 2006-05-15 15:40 dbus
-rwxr-xr-x   1 root root 5277 2006-04-05 16:44 displayconfig-hwprobe.py
-rwxr-xr-x   1 root root  795 2006-02-23 11:37 dns-clean
-rwxr-xr-x   1 root root  923 2006-05-16 04:41 evms
-rwxr-xr-x   1 root root 6175 2006-05-21 14:46 glibc.sh
-rwxr-xr-x   1 root root 1404 2006-05-23 06:39 halt
-rwxr-xr-x   1 root root 5137 2005-04-21 06:10 hdparm
-rwxr-xr-x   1 root root  992 2006-05-23 06:39 hostname.sh
-rwxr-xr-x   1 root root 2245 2006-04-29 15:09 hotkey-setup
-rwxr-xr-x   1 root root 4213 2006-04-27 08:39 hplip
-rwxr-xr-x   1 root root 3634 2006-05-15 21:43 hwclock.sh
-rwxr-xr-x   1 root root 3503 2006-06-13 20:26 kdm
-rwxr-xr-x   1 root root 3170 2005-11-25 15:30 keymap.sh
-rwxr-xr-x   1 root root 1840 2006-04-24 14:36 klogd
-rwxr-xr-x   1 root root 1153 2006-05-06 11:45 laptop-mode
-rwxr-xr-x   1 root root  748 2006-01-23 13:47 loopback
-rwxr-xr-x   1 root root 2867 2005-11-08 03:30 lvm
-rwxr-xr-x   1 root root  822 2005-11-25 10:16 makedev
-rwxr-xr-x   1 root root 1124 2006-05-16 08:41 mdadm
-rwxr-xr-x   1 root root 1059 2006-05-16 08:41 mdadm-raid
-rwxr-xr-x   1 root root  921 2006-05-05 11:47 module-init-tools
-rwxr-xr-x   1 root root 2069 2006-05-23 06:39 mountall.sh
-rwxr-xr-x   1 root root 1256 2006-05-23 06:39 mountdevsubfs
-rwxr-xr-x   1 root root 1384 2006-05-23 06:39 mountvirtfs
-rwxr-xr-x   1 root root 2290 2006-05-23 06:39 mtab
-rwxr-xr-x   1 root root 4926 2006-06-16 07:51 mysql
-rwxr-xr-x   1 root root 1548 2006-06-16 07:51 mysql-ndb
-rwxr-xr-x   1 root root 1472 2006-06-16 07:51 mysql-ndb-mgm
-rwxr-xr-x   1 root root 1685 2006-05-11 02:54 networking
-rwxr-xr-x   1 root root 6773 2006-06-15 11:04 pcmcia
-rwxr-xr-x   1 root root 3386 2006-03-23 15:40 pcmciautils
-rwxr-xr-x   1 root root 2894 2006-06-08 04:22 postfix
-rwxr-xr-x   1 root root 3629 2006-05-08 13:46 powernowd
-rwxr-xr-x   1 root root  177 2006-05-08 13:46 powernowd.early
-rwxr-xr-x   1 root root 1061 2006-02-23 11:32 ppp
-rwxr-xr-x   1 root root  281 2006-02-23 11:32 pppd-dns
-rwxr-xr-x   1 root root 1234 2006-01-23 11:10 procps.sh
-rw-------   1 root root  177 2007-02-19 14:45 proftpd.save
-rwxr-xr-x   1 root root 6897 2006-05-23 06:39 rc
-rwxr-xr-x   1 root root  522 2006-05-23 06:39 rc.local
-rwxr-xr-x   1 root root  188 2006-05-23 06:39 rcS
-rwxr-xr-x   1 root root 1424 2006-02-24 08:31 readahead
-rwxr-xr-x   1 root root 1883 2006-02-24 08:31 readahead-desktop
-rw-r--r--   1 root root  866 2006-05-23 06:39 README
-rwxr-xr-x   1 root root  732 2006-05-23 06:39 reboot
-rwxr-xr-x   1 root root 1226 2006-05-23 06:39 rmnologin
-rwxr-xr-x   1 root root 2924 2006-05-05 10:41 rsync
-rwxr-xr-x   1 root root 2033 2006-07-11 08:40 samba
-rwxr-xr-x   1 root root  452 2006-04-26 17:39 screen
-rwxr-xr-x   1 root root 1081 2006-05-23 06:39 sendsigs
-rwxr-xr-x   1 root root 1126 2006-05-23 06:39 single
-rwxr-xr-x   1 root root 2679 2006-05-23 06:39 skeleton
-rwxr-xr-x   1 root root 2016 2006-05-17 20:43 ssh
lrwxrwxrwx   1 root root    8 2006-07-15 14:41 stop-bootlogd -> bootlogd
-rwxr-xr-x   1 root root  864 2006-02-24 08:31 stop-readahead
-rwxr-xr-x   1 root root 1669 2006-04-24 14:36 sysklogd
-rwxr-xr-x   1 root root 2539 2006-05-22 10:24 udev
-rwxr-xr-x   1 root root 1588 2006-05-23 06:39 umountfs
-rwxr-xr-x   1 root root 1989 2006-05-23 06:39 umountnfs.sh
-rwxr-xr-x   1 root root  912 2006-05-23 06:39 umountroot
-rwxr-xr-x   1 root root 1965 2006-05-23 06:39 urandom
-rwxr-xr-x   1 root root 2192 2006-02-22 22:50 usplash
-rwxr-xr-x   1 root root  820 2006-06-19 06:52 vbesave
-rwxr-xr-x   1 root root 1967 2006-05-23 06:39 waitnfs.sh
-rwxr-xr-x   1 root root 1091 2006-04-24 13:53 x11-common

```

---

### Post by MG5thAve on 2007-02-19
and oh.. that "proftpd.save" is that crap file I tried replacing the original script with. That wasn't originally there.

---

### Post by taurus on 2007-02-19
Just copy it over as

```
sudo cp /etc/init.d/proftpd.save /etc/init.d/proftpd
sudo chmod 755 /etc/init.d/proftpd
```

---

### Post by MG5thAve on 2007-02-20
Oh... sorry, I don't think I explained it correctly. That script file wasn't the original. It was one I grabbed off the net that doesn't actually work. Also, the purging and re-installation of proftpd didn't create a new script file. So, while the program is installed on my machine now, I don't have a script in place to start it up. Is there a way to recreate this file that I accidentally deleted?

---

