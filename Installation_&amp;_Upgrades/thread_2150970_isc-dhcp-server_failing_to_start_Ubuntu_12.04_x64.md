---
title: "isc-dhcp-server failing to start Ubuntu 12.04 x64"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by basicfreak on 2013-06-02
Okay, I cannot figure this out nor find any useful information on this for the past two hours.

I am having issues starting isc-dhcp-server.

my dhcpd.conf:
```
option domain-name "test.net";option domain-name-servers 10.0.0.2;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
subnet 10.0.0.0 netmask 255.0.0.0 {
  range 10.1.0.1 10.254.254.2;
  option routers 10.0.0.1;
  option subnet-mask 255.0.0.0;
  option broadcast-address 10.255.255.255;
  default-lease-time 600;
  max-lease-time 7200;
}
```

output of dhcpd -t:
```
Internet Systems Consortium DHCP Server 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Segmentation fault
```

running service isc-dhcp-server start:
```
start: Job failed to start
```

/var/log/syslog:
```
Jun  2 21:52:18 NetServer kernel: [ 7203.183595] dhcpd[9924]: segfault at 7f12b8e4d000 ip 00007f12b971554d sp 00007ffff1e8b2d8 error 7 in libc-2.15.so[7f12b9689000+1b5000]
Jun  2 21:52:18 NetServer dhcpd: Internet Systems Consortium DHCP Server 4.1-ESV-R4
Jun  2 21:52:18 NetServer dhcpd: Copyright 2004-2011 Internet Systems Consortium.
Jun  2 21:52:18 NetServer dhcpd: All rights reserved.
Jun  2 21:52:18 NetServer dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 21:52:22 NetServer kernel: [ 7206.528792] dhcpd[9925]: segfault at 7fd22df30000 ip 00007fd22e7f854d sp 00007fffa5478988 error 7 in libc-2.15.so[7fd22e76c000+1b5000]
Jun  2 21:52:38 NetServer kernel: [ 7222.878797] dhcpd[9934]: segfault at 7fee1b754000 ip 00007fee1c01c54d sp 00007fff9dba6098 error 7 in libc-2.15.so[7fee1bf90000+1b5000]
Jun  2 21:52:38 NetServer dhcpd: Internet Systems Consortium DHCP Server 4.1-ESV-R4
Jun  2 21:52:38 NetServer dhcpd: Copyright 2004-2011 Internet Systems Consortium.
Jun  2 21:52:38 NetServer dhcpd: All rights reserved.
Jun  2 21:52:38 NetServer dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 21:52:41 NetServer kernel: [ 7226.145906] dhcpd[9935]: segfault at 7f610f88f000 ip 00007f611015754d sp 00007fffd997d8f8 error 7 in libc-2.15.so[7f61100cb000+1b5000]
Jun  2 21:52:45 NetServer dhcpd: Internet Systems Consortium DHCP Server 4.1-ESV-R4
Jun  2 21:52:45 NetServer dhcpd: Copyright 2004-2011 Internet Systems Consortium.
Jun  2 21:52:45 NetServer dhcpd: All rights reserved.
Jun  2 21:52:45 NetServer dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 21:52:48 NetServer kernel: [ 7232.499824] dhcpd[9936]: segfault at 7fb950440000 ip 00007fb950d0854d sp 00007fffe434d068 error 7 in libc-2.15.so[7fb950c7c000+1b5000]
Jun  2 21:53:39 NetServer kernel: [ 7283.605684] dhcpd[9942]: segfault at 7f162e2be000 ip 00007f162eb8654d sp 00007fff3dda5738 error 7 in libc-2.15.so[7f162eafa000+1b5000]
Jun  2 21:53:39 NetServer dhcpd: Internet Systems Consortium DHCP Server 4.1-ESV-R4
Jun  2 21:53:39 NetServer dhcpd: Copyright 2004-2011 Internet Systems Consortium.
Jun  2 21:53:39 NetServer dhcpd: All rights reserved.
Jun  2 21:53:39 NetServer dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Jun  2 21:53:42 NetServer kernel: [ 7286.865343] dhcpd[9943]: segfault at 7f1ff8a0b000 ip 00007f1ff92d354d sp 00007ffff3617c98 error 7 in libc-2.15.so[7f1ff9247000+1b5000]
```

Any help is greatly appreciated
 -- BASICFreak

P.S. I don't have any idea if this will effect it but I have the following packages installed:
```
openssh-server
openssh-client
mysql-client
mysql-server
php5
php-pear
php5-gd
php-DB
php5-mysql
apache2
libapache2-mod-php5
libapache2-mod-auth-mysql
phpmyadmin
freeradius
freeradius-utils
freeradius-mysql
postfix
make
gcc
bcc
g++
perl
nasm
samba
bind9
isc-dhcp-server
elinks
```

---

### Post by Doug S on 2013-06-02
Try a smaller sub-net, much smaller.

---

### Post by basicfreak on 2013-06-02
Wow, such a simple issue.
range 10.1.0.1 10.254.254.2; -> range 10.0.1.1 10.0.254.254;

Well I guess I should have tried to host less than a whole class A subnet. 16 million IPs is far more than anyone would need at least today. (65k is still a lot)

Anyways thanks for the help.

---

### Post by Doug S on 2013-06-02
Glad you got it working. My suggestion was only a guess, and I have been trying to figure out how much memory is used verses sub-net size, but haven't gotten anywhere (i'm only using "dhcpd -t" because I don't want to mess up the real stuff.)

---

