---
title: "Failed upgrade to 18.04"
date: 2019-03-02
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-03-02
I ran a release upgrade from 16.04 to 18.04 and encountered a bunch of werrors. There are a lot of packages unconfigured and because of them I have a lot of dependancy. I tracked back the dependencies and found udev is unconfigured. When I try to configure it using```
 # dkg --configure udev 
I get this 
```
```
root@thelma:/run# dpkg --configure udev
Setting up udev (237-3ubuntu10.13) ...
Failed to connect to bus: No such file or directory
Failed to connect to bus: No such file or directory
invoke-rc.d: could not determine current runlevel
Failed to connect to bus: No such file or directory
Failed to connect to bus: No such file or directory
Failed to connect to bus: No such file or directory
invoke-rc.d: initscript udev, action "restart" failed.
Failed to connect to bus: No such file or directory
dpkg: error processing package udev (--configure):
 installed udev package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 udev
```

```
dpkg --configure -a
```  fails with similar errors to a lot of packages as does ```
apt install -f
```

It appears dbus is running, but something is obviously wrong. 

```
root@thelma:/run# ps -ef|grep dbus
message+  1082     1  0 13:24 ?        00:00:02 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
lp        1250  1050  0 13:24 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus://
lp        1251  1050  0 13:24 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus://
lightdm   2103     1  0 13:24 ?        00:00:00 /usr/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
lightdm   2116  2111  0 13:24 ?        00:00:00 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 3
message+  4010     1  0 14:04 ?        00:00:00 dbus-daemon --system
root      6450  3796  0 14:18 pts/8    00:00:00 grep dbus
lp       21062  1050  0 13:32 ?        00:00:00 /usr/lib/cups/notifier/dbus dbus://
```

---

### Post by rsteinmetz70112 on 2019-03-02
I think I've solved it apparently /vr/run and /run were not properly linked. I redid the links an almost everything is fixed.

---

