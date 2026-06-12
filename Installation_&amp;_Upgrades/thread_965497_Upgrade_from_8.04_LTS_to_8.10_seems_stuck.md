---
title: "Upgrade from 8.04 LTS to 8.10 seems stuck"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by woody7 on 2008-10-31
I started an upgrade from 8.04 LTS to 8.10 via the Update Manager (took forever to download the packages due to server congestion, I suspect) on Thursday early evening. All seemed to go well, except for download speeds.  This morning, I looked at the server, and it's stuck cleaning up, removing obsolete packages.  It is stating that it's removing landscape-client.  There's a lot of disk activity (as per the indicator on the front of the server).

HP NetServer E50, PII-333, 128 MB RAM (yeah, I know), 8 GB HD.

This is the current version on this server.
```

root@superserver:~# uname -a
Linux superserver 2.6.24-21-server #1 SMP Wed Oct 22 00:18:13 UTC 2008 i686 GNU/Linux

```

It seems to be stuck (has been for at least the last 10 hours), and I'm not sure if I can kill it and have a successful restart or not.

Here's a screen shot of top:
```

top - 17:00:34 up 1 day,  4:04,  3 users,  load average: 2.14, 2.00, 1.98
Tasks: 106 total,   1 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  3.3%sy,  0.0%ni,  0.0%id, 96.4%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    125668k total,   123136k used,     2532k free,     7700k buffers
Swap:   361420k total,   306324k used,    55096k free,    15404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2585 root      15  -5     0    0    0 D  2.3  0.0  21:46.52 kjournald
 6454 root      20   0  327m  65m 4740 D  1.3 53.5  36:48.50 intrepid
18246 root      20   0  2304 1104  856 R  1.3  0.9   0:00.21 top
 4750 mysql     20   0  124m 1192  424 S  0.3  0.9   7:46.62 mysqld
 5555 andy      20   0 49352 3280 2672 S  0.3  2.6   5:24.15 nm-applet
    1 root      20   0  2712  288  284 S  0.0  0.2   0:05.49 init
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 kthreadd
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.41 watchdog/0
    6 root      15  -5     0    0    0 S  0.0  0.0   0:03.67 events/0
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 khelper
   39 root      15  -5     0    0    0 S  0.0  0.0   0:01.92 kblockd/0
   60 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod
   99 root      15  -5     0    0    0 S  0.0  0.0   1:09.81 kswapd0
  142 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1364 root      15  -5     0    0    0 S  0.0  0.0   0:07.19 ata/0

```

x86, IDE drives, 32 bit.

Help?

Thanks in advance.

---

### Post by woody7 on 2008-11-01
OK, by using top, I was able to renice the intrepid process to escalate it to the most important process on this server.  Then I stopped the apache and mysql services.  It was then able to provide me the pop-up to continue the removal process of obsolete packages.  I was then able to allow it to finish on it's own.
Later last night, it had completed, and I was able to shutdown the server.
This morning, I restarted it, and it prompted me to continue with the upgrade (partial upgrade).  It has re-downloaded all upgrade packages, and is now in the process of installing the upgrades.

I'll keep you posted.

---

