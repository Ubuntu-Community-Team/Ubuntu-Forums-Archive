---
title: "weird process on ubuntu 16.04 server"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by paukacang on 2016-08-07
6547 ?        Ss     0:00 whoami
 6548 ?        Ss     0:00 grep "A"
 6551 ?        Ss     0:00 ls -la
 6554 ?        Ss     0:00 ifconfig
 6556 ?        Ss     0:00 route -n
 6559 ?        Ss     0:00 /usr/sbin/cron -f
 6563 ?        Ss     0:00 /lib/systemd/systemd --user
 6566 ?        Ss     0:00 automount
 6568 ?        Ss     0:00 /usr/libexec/gnome-vfs-daemon
 6571 ?        Ss     0:00 klogd -x
 6572 pts/0    R+     0:00 ps x


hello

i just install ubuntu 16.04 server at my office computer. after 2/3 day this process ( 6547/6548/ 6551/6554) going up & make my office network hang. 
can anybody guide me how to solve this problem

---

