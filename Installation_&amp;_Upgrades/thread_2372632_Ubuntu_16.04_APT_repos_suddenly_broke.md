---
title: "Ubuntu 16.04 APT repos suddenly broke"
date: 2017-09-27
forum: Installation &amp; Upgrades
---

### Post by Drenriza on 2017-09-27
I have installed a 16.04 Ubuntu server which works as my firewall very well.

Now suddenly APT can no longer run updates due to timeouts

> $ apt-get update
0% [Connecting to dk.archive.ubuntu.com (91.189.91.26)] [Connecting to security.ubuntu.com (91.189.88.161)]

> 
cat /etc/apt/sources.list|grep -v ^#
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial main restricted
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

But i can reach the destinations just fine
> 
$ ping dk.archive.ubuntu.com
PING dk.archive.ubuntu.com (91.189.88.162) 56(84) bytes of data.
64 bytes from yukinko.canonical.com (91.189.88.162): icmp_seq=1 ttl=58 time=39.4 ms
64 bytes from yukinko.canonical.com (91.189.88.162): icmp_seq=2 ttl=58 time=31.2 ms
^C
--- dk.archive.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 31.290/35.375/39.461/4.089 ms
$ ping 91.189.91.26
PING 91.189.91.26 (91.189.91.26) 56(84) bytes of data.
64 bytes from 91.189.91.26: icmp_seq=1 ttl=58 time=110 ms
^C


$ ping security.ubuntu.com
PING security.ubuntu.com (91.189.91.26) 56(84) bytes of data.
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=1 ttl=58 time=118 ms
64 bytes from hanger.canonical.com (91.189.91.26): icmp_seq=2 ttl=58 time=111 ms
^C
--- security.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 111.786/115.140/118.494/3.354 ms
$ ping 91.189.88.161
PING 91.189.88.161 (91.189.88.161) 56(84) bytes of data.
64 bytes from 91.189.88.161: icmp_seq=1 ttl=55 time=39.4 ms
^C


How can i fix this?

Other installations i have with the exact same server build and same content of sources.list
can run updates just fine.

Thanks in advance

---

### Post by Drenriza on 2017-09-29
Anyone?

---

