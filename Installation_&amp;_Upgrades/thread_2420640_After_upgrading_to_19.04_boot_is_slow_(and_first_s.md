---
title: "After upgrading to 19.04 boot is slow (and first ssd access)"
date: 2019-06-08
forum: Installation &amp; Upgrades
---

### Post by robbe1 on 2019-06-08
Hello,
booting my machine is very slow after upgrading to 19.04. Any ideas what has changed?

```
$ systemd-analyze blame
          9.352s apt-daily.service
          5.273s NetworkManager-wait-online.service
          2.547s apt-daily-upgrade.service
          1.678s man-db.service
          1.396s networking.service
           867ms dev-sda1.device
           834ms virtualbox.service
           764ms udisks2.service
           595ms networkd-dispatcher.service
           478ms postfix@-.service
           472ms accounts-daemon.service
           453ms ModemManager.service
           386ms logrotate.service
           367ms snapd.service
           357ms dev-loop1.device
           345ms systemd-logind.service
           335ms dev-loop3.device
           334ms dev-loop2.device


dmesg:
[    7.735225] Adding 5625152k swap on /dev/sda2.  Priority:-2 extents:1 across:5625152k SSFS
[    8.458507] RTL8211E Gigabit Ethernet r8169-200:00: attached PHY driver [RTL8211E Gigabit Ethernet] (mii_bus:phy_addr=r8169-200:00, irq=IGNORE)
[    8.674038] r8169 0000:02:00.0 enp2s0: Link is Down
[   10.211041] r8169 0000:02:00.0 enp2s0: Link is Up - 100Mbps/Full - flow control rx/tx
[   10.211051] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[   13.630119] kauditd_printk_skb: 19 callbacks suppressed
```



Linux version 5.0.0-16-generic (buildd@lgw01-amd64-060) (gcc version 8.3.0 (Ubuntu 8.3.0-6ubuntu1)) #17-Ubuntu SMP Wed May 15 10:52:21 UTC 2019

And I also have a problem that when I open a file selector, the first access is very slow (10 seconds). SDD smart values are ok.

Any help is appreciated :-)

---

### Post by &amp;wP*!) on 2019-06-10
[A very similar problem in an old version]("https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service").

HTH

---

