---
title: "network autoconfig failed"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by c3sundog on 2008-11-26
Hi,I just installed ubuntu studio 8.10 as dual boot with windowsxp mce on an acer aspire 5100-3583. during install network auto configuration failed.
as a result dhcp not recognized.only loopback interface is present.
As far as i can tell everything else is working o.k., except for the networking of course. i have one of those infamous atheros 2413 802.11 wifi cards causing so much trouble i'm sure. hardware detection lists the atheros driver as activated and in use, but it does not work. cant get network manager or ndiswrapper from disk. i get a message saying hardware is not supported. lshw -C network command, shows all network devices disabled.
Help anyone?:(

---

### Post by lemming465 on 2008-11-28
On a Toshiba Satellite laptop with an AR2007EG chip I had to use newer madwifi drivers.  Try [these directions]("http://ubuntuforums.org/showthread.php?t=964331"), which helped me.  There is hope for Ubuntu 9.04 next spring; this week's Fedora 10 managed to configure my Atheros chip out of the box.

---

