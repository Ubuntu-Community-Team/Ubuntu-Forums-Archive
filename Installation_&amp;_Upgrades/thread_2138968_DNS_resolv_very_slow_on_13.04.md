---
title: "DNS resolv very slow on 13.04"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by Tres_Iqus on 2013-04-25
any idea?

---

### Post by simi24 on 2013-04-28
The same problem here.
nslookup [www.cpan.org]("http://www.cpan.org")     is instant
but when I am trying to fetch a web page
wget [www.cpan.org]("http://www.cpan.org")
 there is a delay of 5 (!!!) seconds. Using strace I can see the process is doind the following loop

```
sendto(3, "\20\313\1\0\0\1\0\0\0\0\0\0\3www\4cpan\3org\0\0\1\0\1", 30, MSG_NOSIGNAL, NULL, 0) = 30
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [48])                = 0
recvfrom(3, "\20\313\201\200\0\1\0\1\0\0\0\0\3www\4cpan\3org\0\0\1\0\1\300\f"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.0.1")}, [16]) = 48
poll([{fd=3, events=POLLOUT}], 1, 4999) = 1 ([{fd=3, revents=POLLOUT}])
sendto(3, "w\276\1\0\0\1\0\0\0\0\0\0\3www\4cpan\3org\0\0\34\0\1", 30, MSG_NOSIGNAL, NULL, 0) = 30
poll([{fd=3, events=POLLIN}], 1, 4999)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [76])                = 0
recvfrom(3, "w\276\205\200\0\1\0\1\0\0\0\0\003118\003177\003117\003212\7in-"..., 2000, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.0.1")}, [16]) = 76
poll([{fd=3, events=POLLIN}], 1, 4998)  = 0 (Timeout)
close(3)                                = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.0.1")}, 16) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
```

---

### Post by sanderstuurwold on 2013-05-27
me too. Something with driver? 

Intel 82566DM-2 on

---

