---
title: "i cant install anything. VPS UBUNTU SERVER"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by saqib4 on 2014-04-22
hi, i am new to ubuntu, i am connected to my vps through ssh. I am facing a problem and cant install anything  on my server. error I am receiving on every installation is

> 

dpkg: unrecoverable fatal error, aborting:
 fork failed: Cannot allocate memory
E: Sub-process /usr/bin/dpkg returned an error code (2)



after that when I try to install anything it shows me
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

when i run this command "sudo dpkg --configure -a", it starts installing and abort in the middle with the above error (2).


top:
> top - 10:36:59 up 2 days,  3:09,  2 users,  load average: 0.00, 0.01, 0.05Tasks:  89 total,   1 running,  88 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.3%us,  0.0%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    244648k total,   215860k used,    28788k free,     2128k buffers
Swap:        0k total,        0k used,        0k free,    43160k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1867 openvpn_  20   0 25008 1044   44 S  0.0  0.4   7:48.07 openvpn
 1844 root      20   0  264m  39m 1164 S  0.0 16.5   3:05.73 python
 1848 openvpn_  20   0  146m  29m  672 S  0.0 12.3   1:27.46 python
    1 root      20   0 24476 1180  136 S  0.0  0.5   1:01.12 init
  689 root      20   0 50040  696   92 S  0.0  0.3   0:47.38 sshd
  794 root      20   0  231m 7548 1528 S  0.0  3.1   0:39.90 NetworkManager
 1857 root      20   0  100m  10m  208 S  0.0  4.2   0:30.13 python
11120 root      20   0 20992 1216  692 S  0.0  0.5   0:29.71 bash
  883 whoopsie  20   0  195m 2908 1244 S  0.0  1.2   0:23.50 whoopsie
  439 avahi     20   0 32312  968  608 S  0.0  0.4   0:20.00 avahi-daemon
  389 syslog    20   0  243m 1072    0 S  0.0  0.4   0:19.23 rsyslogd
 1847 root      20   0  129m  18m  264 S  0.0  7.8   0:05.64 python
  408 messageb  20   0 24100 1060  500 S  0.0  0.4   0:05.03 dbus-daemon
   25 root      20   0     0    0    0 S  0.0  0.0   0:04.88 kswapd0
   23 root      20   0     0    0    0 S  0.0  0.0   0:04.34 kworker/0:1
    3 root      20   0     0    0    0 S  0.0  0.0   0:03.97 ksoftirqd/0
   10 root      20   0     0    0    0 S  0.0  0.0   0:03.56 rcu_sched





free -m:
>              total       used       free     shared    buffers     cachedMem:           238        210         28          0          2         42
-/+ buffers/cache:        166         72
Swap:            0          0          0




Please help me with this.. Thanks :)

---

### Post by Danger_Monkey on 2014-04-22
It would appear that there are only 256 megs of ram available, and no swap.  With that small amount of ram, you might have to allocate some disk to swap just so you can operate efficiently.  This is done by building a file, say one gig bit, then tell the system to use it a swap.

You will use dd to build the file, mkswap to format it, and swapon to tell the OS to use it.  In this example, "swampy" is the name of the file

```

[COLOR=#111111][FONT=Consolas]dd if=/dev/zero of=/swampy bs=1024 count=[/FONT][/COLOR]1048576
[COLOR=#111111][FONT=Consolas]mkswap /swampy[/FONT][/COLOR]
[COLOR=#111111][FONT=Consolas]swapon /swampy
[/FONT][/COLOR]
```[COLOR=#111111][FONT=Consolas]

You'll want to add it to /etc/fstab so it will be used next time you reboot:

```

/swampy swap swap defaults 0 0

```

Once that is done, post back errors.


[/FONT][/COLOR]

---

