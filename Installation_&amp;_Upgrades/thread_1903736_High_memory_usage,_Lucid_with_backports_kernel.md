---
title: "High memory usage, Lucid with backports kernel"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by versalar on 2012-01-03
Hi,

I am running Lucid x64 as I am a fan of LTS. To get better performance of my ATI R500 graphic card, I installed backports kernel of 3.0 (backports from oneiric), since AMD/ATI has given up on the proprietary driver for R500 long time ago.

Everything went smooth except one memory usage issue.

With fresh boot, the memory usage is quite low, about 700M without login. But after couple of days running, the memory usage is about 1.2G without login.

I have checked top contributor of memory usage with PS, but not much difference between the two, which bothers me a lot. I can not tell where the memory goes! Same thing with 2.6.38, backports from natty.

But this was never happening with default kernel of 2.6.32.

Could anybody give me some hints on how to debug this.

Memory usage of fresh boot,

output of free,
```

             total       used       free     shared    buffers     cached
Mem:       3993328     769428    3223900          0      60584     497964
-/+ buffers/cache:     210880    3782448
Swap:      4000180          0    4000180

```

output of ps auxf | sort -nr -k 4,
```

oot      1956  1.4  0.4  30256 19484 ?        SNs  18:55   0:04 /usr/sbin/preload -s /var/lib/preload/preload.state
root      1220  0.2  0.4 112172 16948 tty7     Ss+  18:55   0:00      \_ /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-nBSQLH/database -nolisten tcp vt7
gdm       1866  0.0  0.4 197804 16480 ?        S    18:55   0:00      |   \_ /usr/lib/gdm/gdm-simple-greeter
gdm       1691  0.0  0.3 244140 14744 ?        Ss   18:55   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon --gconf-prefix=/apps/gdm/simple-greeter/settings-manager-plugins
gdm       1867  0.0  0.2 167460  8372 ?        S    18:55   0:00      |   \_ gnome-power-manager
gdm       1859  0.0  0.2 205728 10340 ?        S    18:55   0:00      |   \_ metacity
root      1960  0.0  0.1  54348  4344 ?        S    18:55   0:00 /usr/lib/policykit-1/polkitd
root      1077  0.0  0.1  93232  5376 ?        Ssl  18:55   0:00 NetworkManager
gdm       1685  0.0  0.1  46436  5884 ?        S    18:55   0:00 /usr/lib/libgconf2-4/gconfd-2
gdm       1671  0.0  0.1 144596  7468 ?        Ssl  18:55   0:00      \_ /usr/bin/gnome-session --autostart=/usr/share/gdm/autostart/LoginWindow/
108       2030  0.0  0.1  45548  5804 ?        Ssl  18:55   0:00 /usr/sbin/hald
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
syslog    1061  0.0  0.0 120916  2208 ?        Sl   18:55   0:00 rsyslogd -c4
auser     9250  0.0  0.0  60016   896 pts/0    S+   19:00   0:00              \_ sort -nr -k 4
auser     9249  0.0  0.0  15444  1220 pts/0    R+   19:00   0:00              \_ ps axuf
auser     8819  0.0  0.0  44996   528 ?        Ssl  19:00   0:00 sshfs blahblah
auser     8346  0.0  0.0  38604  2708 pts/0    S    18:59   0:00 ssh -X -a -oClearAllForwardings=yes -2 root@ss -s sftp
auser     8333  0.0  0.0  19496  2236 pts/0    Ss   18:59   0:00          \_ -bash
auser     8332  0.0  0.0  87452  1728 ?        S    18:59   0:00      \_ sshd: auser@pts/0
root       990  0.0  0.0      0     0 ?        S<   18:55   0:00  \_ [ext4-dio-unwrit]
root       989  0.0  0.0      0     0 ?        S    18:55   0:00  \_ [jbd2/sda1-8]
root       908  0.0  0.0      0     0 ?        S    18:55   0:00  \_ [scsi_eh_7]
root         9  0.0  0.0      0     0 ?        S    18:54   0:00  \_ [ksoftirqd/1]

```


Meomory usage after couple of days of running,
output of free,
```

             total       used       free     shared    buffers     cached
Mem:       3993328    3036036     957292          0     232332    1818296
-/+ buffers/cache:     985408    3007920
Swap:      4000180        188    3999992

```

output of ps auxf | sort -nr -k 4,
```

root      3959  0.4  0.4  30256 19564 ?        SNs  Jan01  11:06 /usr/sbin/preload -s /var/lib/preload/preload.state
root      3704  0.0  0.4 112180 16928 tty7     Ss+  Jan01   0:07      \_ /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-na1jCO/database -nolisten tcp
gdm       3736  0.0  0.4 197804 16476 ?        S    Jan01   0:11      |   \_ /usr/lib/gdm/gdm-simple-greeter
gdm       3732  0.0  0.3 244136 14740 ?        Ss   Jan01   0:05 /usr/lib/gnome-settings-daemon/gnome-settings-daemon --gconf-prefix=/apps/gdm/simple-greeter/settings-manager-plugins
gdm       3737  0.0  0.2 167460  8372 ?        S    Jan01   0:02      |   \_ gnome-power-manager
gdm       3735  0.0  0.2 205712 10456 ?        S    Jan01   0:01      |   \_ metacity
auser    31359  0.0  0.1 139368  4976 ?        Ssl   2011   0:01 sshfs blahblah
root      4242  0.0  0.1  55140  5172 ?        S     2011   0:01 /usr/lib/policykit-1/polkitd
root     30213  0.0  0.1  93360  5508 ?        Ssl   2011   1:29 NetworkManager
gdm       3729  0.0  0.1  46448  5892 ?        S    Jan01   0:01 /usr/lib/libgconf2-4/gconfd-2
gdm       3726  0.0  0.1 144596  7472 ?        Ssl  Jan01   0:00      \_ /usr/bin/gnome-session --autostart=/usr/share/gdm/autostart/LoginWindow/
gdm      10693  0.0  0.1 148144  6888 ?        S    Jan01   0:00 /usr/bin/gnome-screensaver --no-daemon
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
syslog    3693  0.0  0.0 185396  1436 ?        Sl   Jan01   0:03 rsyslogd -c4
auser     8660  0.0  0.0  60016   892 pts/0    S+   18:53   0:00              \_ sort -nr -k 4
auser     8659  0.0  0.0  15444  1208 pts/0    R+   18:53   0:00              \_ ps auxf
auser     8189  0.0  0.0  19504  2236 pts/0    Ss   18:50   0:00          \_ -bash
auser     8186  0.0  0.0  87452  1728 ?        S    18:50   0:00      \_ sshd: auser@pts/0
auser     3956  0.0  0.0  19548  2152 pts/1    Ss    2011   0:00  \_ /bin/bash
auser     3949  0.0  0.0  25372  1228 ?        Ss    2011   0:00 SCREEN
auser    31273  0.0  0.0  38948  2832 ?        S     2011   0:01 ssh -X -a -oClearAllForwardings=yes -2 root@ss -s sftp
rtkit    25006  0.0  0.0  39592  1264 ?        SNl   2011   0:09 /usr/lib/rtkit/rtkit-daemon
root       916  0.0  0.0      0     0 ?        S     2011   0:00  \_ [scsi_eh_7]
root       909  0.0  0.0      0     0 ?        S<    2011   0:00  \_ [hd-audio0]
root         9  0.0  0.0      0     0 ?        S     2011   0:22  \_ [ksoftirqd/1]

```

---

### Post by snowpine on 2012-01-03
Looks normal to me. You have plenty of free RAM for applications/tasks.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by versalar on 2012-01-03
But why is this only happening with backports kernel? And I do see more memory usage with same apps opened after couple days of running...

---

### Post by versalar on 2012-01-05
When upgrading to 3.0.0-15 from 3.0.0-14, things were getting much better.

---

### Post by versalar on 2012-02-02
It turned out that I was using Gallium3D ppa (xorg-edgers) before upgrade to backport kernel.
Not only the mix of gallium3D and new kernel gave me constant X crash, it also consumed lot of memory.

After purge the ppa and revert to standard repository, everything works like a charm as it should be.

---

