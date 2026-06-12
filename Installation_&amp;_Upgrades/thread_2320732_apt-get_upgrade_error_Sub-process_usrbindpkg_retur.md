---
title: "apt-get upgrade error: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2016-04-16
forum: Installation &amp; Upgrades
---

### Post by manukadesign on 2016-04-16
Hi all I've recently done a clean install of Ubuntu 15.04 on an older i3 series laptop. When I run the sudo apt-get upgrade command I get the following error: 

[snip]
Get:25 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) wily-updates/main libreoffice-sdbc-hsqldb amd64 1:5.0.5~rc2-0ubuntu2 [125 kB]
Get:26 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) wily/main lksctp-tools amd64 1.0.16+dfsg-2 [41.9 kB]
Fetched 48.6 MB in 11s (4,136 kB/s)                                            
Preconfiguring packages ...
Selecting previously unselected package libgif4:amd64.
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'libreoffice-common': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

Several Threads I have read suggested sudo dpkg --clear-avail, sudo apt-get autoclean or   sudo dpkg -- configure -a then running upgrade. This hasn't worked in my case and I still receive the same error.

---

### Post by oldos2er on 2016-04-16
Are you sure you didn't install 15.10 (Wily?) 15.04 is no longer supported.

An [COLOR=#000000]Input/output error may indicate a problem with your hard disk. Can you run the following in a terminal and copy/paste the output here? ```
dmesg | tail
```[/COLOR]

---

### Post by manukadesign on 2016-04-16
Hi, I did install 15.10, not quite sure why I stated 15.04... Output of dmesg | tail are as follows:

```


[87172.956207] tg3 0000:03:00.0 enp3s0f0: EEE is disabled
[87173.075713] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0489-e033.hcd failed with error -2
[87173.075723] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0489-e033.hcd not found
[87173.440819] IPv6: ADDRCONF(NETDEV_UP): enp3s0f0: link is not ready
[87173.605087] IPv6: ADDRCONF(NETDEV_UP): enp3s0f0: link is not ready
[87173.606006] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[87177.864466] tg3 0000:03:00.0 enp3s0f0: Link is up at 1000 Mbps, full duplex
[87177.864497] tg3 0000:03:00.0 enp3s0f0: Flow control is on for TX and on for RX
[87177.864515] tg3 0000:03:00.0 enp3s0f0: EEE is disabled
[87177.864551] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0f0: link becomes ready


```

---

### Post by oldos2er on 2016-04-17
Doesn't seem to be anything relevant there. Do you have SMART enabled for your hard drive, and have you ever run a check on it? 

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

