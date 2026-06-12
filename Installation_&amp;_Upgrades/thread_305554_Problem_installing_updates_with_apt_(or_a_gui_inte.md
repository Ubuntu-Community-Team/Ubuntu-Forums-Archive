---
title: "Problem installing updates with apt (or a gui interface)"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by MadMasta on 2006-11-23
When I try to update my computer, I get a dialogue box that says

```

"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first."

```

I have been unable to find those programs in top.  It keeps giving me this message even if I restart my computer.  Here is the output from top...

Sorted by command from A~H
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4396 root      15   0 86236  33m  12m S  6.4  4.5   0:21.14 Xorg
 3930 root      16   0  2156 1212  648 S  0.0  0.2   0:00.00 acpid
  147 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 4778 daemon    23   0  1800  392  296 S  0.0  0.1   0:00.00 atd
 5472 mad       15   0  5688 3376 1360 S  0.0  0.4   0:00.35 bash
 4951 mad       16   0  6264 2924 2220 S  0.0  0.4   0:00.19 bonobo-activati
 5024 mad       16   0 23860  10m 8116 S  0.0  1.4   0:00.24 clock-applet
 4791 root      16   0  2120  836  684 S  0.0  0.1   0:00.00 cron
 5264 cupsys    26  10  4200 1752 1300 S  0.0  0.2   0:00.03 cupsd
 4500 messageb  16   0  2192  856  668 S  0.0  0.1   0:00.08 dbus-daemon
 4944 mad       16   0  2196  948  772 S  0.0  0.1   0:00.00 dbus-daemon
 4943 mad       16   0  2716  648  520 S  0.0  0.1   0:00.00 dbus-launch
 4044 root      15   0  1684  500  412 S  0.0  0.1   0:00.01 dd
 3585 dhcp      14  -2  2460  596  296 S  0.0  0.1   0:00.00 dhclient3
 5050 dhcp      14  -2  2336  760  460 S  0.0  0.1   0:00.00 dhclient3
 4957 mad       16   0  6008 4532 1432 S  0.0  0.6   0:00.06 esd
 4959 mad       15   0  3020  448  224 S  0.0  0.1   0:00.00 esd
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 events/0
 5102 mad       15   0  166m  52m  20m R  0.0  6.9   0:39.98 firefox-bin
 5092 mad       16   0 73420  15m  10m S  0.0  2.0   0:03.88 gaim
 4946 mad       16   0  6060 3660 1808 S  0.0  0.5   0:00.82 gconfd-2
 5421 root      16   0  5936 3476 1784 S  0.0  0.4   0:00.23 gconfd-2
 4370 root      15   0 10912 1784 1212 S  0.0  0.2   0:00.00 gdm
 4371 root      16   0 11264 2520 1884 S  0.0  0.3   0:00.00 gdm
 4876 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4877 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4878 root      16   0  1564  496  424 S  0.0  0.1   0:00.00 getty
 4879 root      16   0  1560  492  424 S  0.0  0.1   0:00.00 getty
 4880 root      16   0  1560  488  424 S  0.0  0.1   0:00.00 getty
 4881 root      16   0  1560  488  424 S  0.0  0.1   0:00.00 getty
 5416 mad       15   0 59268 9.8m 6608 S  0.0  1.3   0:01.38 gksu
 4999 mad       15   0 54448 8288 6772 S  0.0  1.1   0:00.22 gnome-cups-icon
 4949 mad       17   0  2340  728  532 S  0.0  0.1   0:00.00 gnome-keyring-d
 5026 mad       15   0 61808 8864 6860 S  0.0  1.1   0:00.13 gnome-netstatus
 4970 mad       15   0 66344  14m  10m R  0.0  1.9   0:02.19 gnome-panel
 5019 mad       15   0 18040 5900 4416 S  0.0  0.8   0:00.09 gnome-power-man
 5471 mad       19   0  2288  684  580 S  0.0  0.1   0:00.00 gnome-pty-helpe
 5044 mad       15   0 14616 2776 1852 R  0.0  0.4   0:00.25 gnome-screensav
 4953 mad       15   0 27112 8912 6928 R  0.0  1.1   0:00.52 gnome-settings-
 5470 mad       16   0 84760  16m 9984 R 12.9  2.1   0:07.33 gnome-terminal
 4988 mad       15   0  8616 3812 3000 S  0.0  0.5   0:00.07 gnome-vfs-daemo
 4977 mad       16   0 17472 5732 4432 S  0.0  0.7   0:00.84 gnome-volume-ma
 4515 haldaemo  16   0  6880 5472 1556 S  0.0  0.7   0:01.28 hald
 4521 haldaemo  17   0  2008  796  696 S  0.0  0.1   0:00.00 hald-addon-acpi
 4576 haldaemo  15   0  2008  796  692 S  0.0  0.1   0:00.04 hald-addon-keyb
 4590 haldaemo  16   0  2008  820  716 S  0.0  0.1   0:00.02 hald-addon-stor
 4591 haldaemo  16   0  2008  816  716 S  0.0  0.1   0:00.02 hald-addon-stor
 4516 root      16   0  2716  988  848 S  0.0  0.1   0:00.02 hald-runner


```

Sorted from Z~H

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4713 root      18   0  2212  788  656 S  0.0  0.1   0:00.00 xinetd
 4898 mad       16   0 19708   9m 7272 S  0.0  1.3   0:00.73 x-session-manag
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
 4983 mad       15   0 63812  11m 8144 S  0.0  1.5   0:00.48 update-notifier
 5417 root      15   0 79808  19m  10m S  0.0  2.6   0:00.64 update-manager
 2179 root      17  -4  2544 1024  368 S  0.0  0.1   0:00.08 udevd
 4990 mad       15   0 70304 8828 6840 S  0.0  1.1   0:00.25 trashapplet
 5552 mad       16   0  2200 1128  868 R  0.1  0.1   0:00.90 top
 5368 syslog    26  10  1768  712  584 S  0.0  0.1   0:00.00 syslogd
 4940 mad       16   0  4332  684  444 S  0.0  0.1   0:00.00 ssh-agent
 4661 root      16   0  8524 2108 1468 S  0.0  0.3   0:00.00 smbd
 4728 root      18   0  8524  928  288 S  0.0  0.1   0:00.00 smbd
 2957 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 4719 root      18   0  1616  452  384 S  0.0  0.1   0:00.00 sdpd
 1952 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 reiserfs/0
 4428 hplip     15   0  9408 4680 1104 S  0.0  0.6   0:00.00 python
 4637 root      21   5  1552  260  192 S  0.0  0.0   0:00.00 powernowd
  144 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  145 root      15   0     0    0    0 S  0.0  0.0   0:00.07 pdflush
 3159 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3160 root      19   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 5034 mad       15   0 60192 9832 6592 S  0.1  1.3   0:00.81 notification-da
 4659 root      16   0  5772 1416  928 S  0.0  0.2   0:00.01 nmbd
 4972 mad       15   0  102m  13m  10m S  0.0  1.8   0:01.48 nautilus
 5028 mad       15   0 64428  11m 8320 S  0.0  1.5   0:00.29 mixer_applet2
 4965 mad       15   0 15396 9444 6548 S  0.7  1.2   0:05.72 metacity
 4743 root      16   0  1628  300  232 S  0.0  0.0   0:00.00 mdadm
 5010 mad       16   0  2288  804  700 S  0.0  0.1   0:00.00 mapping-daemon
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
  146 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
  734 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod
 4730 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 4046 klog      17   0  2424 1348  388 S  0.0  0.2   0:00.05 klogd
 1832 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0
   10 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid-work-0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
 3163 root      10  -5     0    0    0 S  0.1  0.0   0:00.10 ipw2200/0
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.16 init
 4413 hplip     16   0 12876  920  696 S  0.0  0.1   0:00.00 hpiod
 4714 root      18   0  1968  712  616 S  0.0  0.1   0:00.00 hcid
 4516 root      16   0  2716  988  848 S  0.0  0.1   0:00.02 hald-runner
 4590 haldaemo  16   0  2008  820  716 S  0.0  0.1   0:00.02 hald-addon-stor
 4591 haldaemo  16   0  2008  816  716 S  0.0  0.1   0:00.02 hald-addon-stor
 4576 haldaemo  15   0  2008  796  692 S  0.0  0.1   0:00.04 hald-addon-keyb
 4521 haldaemo  17   0  2008  796  696 S  0.0  0.1   0:00.00 hald-addon-acpi

```

Any help would be appriciated!

---

### Post by Joe_CoT on 2006-11-23
It could be that one or the other locked your sources and then never unlocked them (your system crashed, etc). First, restart, to make sure neither is really running. Then do this from a terminal/console:
```
cd /var/cache/apt/archives
sudo rm lock
```

Then try starting your apt program of choice.

---

### Post by MadMasta on 2006-11-23
Your right on the money, I think it crashed or something happened right in the middle of an update/install.  I tried what you told me and that didn't work.

Thanks for the help!

---

### Post by Joe_CoT on 2006-11-23
Try removing /var/lib/dpkg/lock ; if that doesn't work, try running "gksudo synaptic" to see what error it gives on startup.

---

### Post by MadMasta on 2006-11-23
No that didn't work.  The dialog I get from Synaptic is...


```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```


When I run dpkg --config -a , my computer gives me the following output...

```
mad@madlaptop:~$ sudo dpkg --configure -a
Password:
Setting up setiathome (3.08-4) ...
setiathome-3.08.i686-pc-linux-gnu.tar not found in /tmp.
--16:01:30--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
           => `/tmp/fileLcR1fE'
Resolving alien.ssl.berkeley.edu... 128.32.18.176
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:04:40--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 2) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:07:51--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 3) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:11:03--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 4) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:14:16--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 5) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:17:30--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 6) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:20:45--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 7) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21... failed: Connection timed out.
Retrying.

--16:24:01--  ftp://alien.ssl.berkeley.edu/pub/setiathome-3.08.i686-pc-linux-gnu.tar
  (try: 8) => `/tmp/fileLcR1fE'
Connecting to alien.ssl.berkeley.edu|128.32.18.176|:21...

```

It never connects to the servers.  I was having this problem before (and it's the same reason why I crashed my updater).  I think it has something to do with my router.  I can ping the servers allright, but it just doesn't  connect when trying to upgrade.  

Thanks!

---

### Post by Joe_CoT on 2006-11-23
do:
```
dpkg -r setiathome
```

then run 'dpkg --configure -a' again

---

### Post by MadMasta on 2006-11-23
Thank you!  It seems to work now.

---

