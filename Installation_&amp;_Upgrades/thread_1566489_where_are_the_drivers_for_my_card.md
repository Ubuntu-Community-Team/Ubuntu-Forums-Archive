---
title: "where are the drivers for my card"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by gt8ost4l on 2010-09-02
i have a atheros ar5b93 card and i was wondering were you got the driver i asked around and none knew where its located

---

### Post by 2New on 2010-09-02
You may find this thread useful:

[http://ubuntuforums.org/showthread.php?t=1477565](http://ubuntuforums.org/showthread.php?t=1477565)

As chili555 suggests, from the command prompt run:

```
dmesg | grep -i ath
```If you get the same output that harry003 did, specifically
```

Atheros Communications Inc. AR928X  Wireless Network Adapter
```then the same advice Chili555 gave Harry003 will perhaps work for you, run:

```
sudo modprobe ath9k
iwconfig
```

and post your results here.

Plan B:

I just read abit more and found that someone had luck installing a package called linux-backports-modules-wireless-karmic-generic.


I've located this package at: [http://packages.ubuntu.com/karmic/linux-backports-modules-wireless-karmic-generic](http://packages.ubuntu.com/karmic/linux-backports-modules-wireless-karmic-generic)


Follow the instructions carefully in order to download it, hopefully that same package will solve your issue.

---

### Post by gt8ost4l on 2010-09-05
```
dmesg | grep -i ath
```
negative for this i got this

dmesg | grep -i ath
[    1.554384] device-mapper: multipath: version 1.1.0 loaded
[    1.554440] device-mapper: multipath round-robin: version 1.0.0 loaded


```
sudo modprobe ath9k
iwconfig
```

sudo sudo modprobe ath9k
WARNING: All config files need .conf: /etc/modprobe.d/madwifi, it will be ignored in a future release.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

