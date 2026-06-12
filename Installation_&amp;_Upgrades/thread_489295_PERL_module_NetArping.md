---
title: "PERL module Net::Arping"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by artlion on 2007-07-01
Hi, I have problem with compiling code and installing module for PERL -> Net::Arping

Can someone help me, I try to install modeule for lunch Nagios Arping

Log of compilation :

root@orasoft-desk:/home/artur/download/Net-Arping-0.02# make
cc -c   -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"0.02\" -DXS_VERSION=\"0.02\" -fPIC "-I/usr/lib/perl/5.8/CORE"  INC Arping.c
cc: INC: No such file or directory
Arping.xs: In function ‘XS_Net__Arping_send_arp’:
Arping.xs:124: warning: passing argument 1 of ‘libnet_select_device’ from incompatible pointer type
Arping.xs:124: error: too many arguments to function ‘libnet_select_device’
Arping.xs:130: warning: assignment makes pointer from integer without a cast
Arping.xs:140: error: ‘LIBNET_IP_H’ undeclared (first use in this function)
Arping.xs:140: error: (Each undeclared identifier is reported only once
Arping.xs:140: error: for each function it appears in.)
Arping.xs:148: warning: passing argument 1 of ‘libnet_get_hwaddr’ from incompatible pointer type
Arping.xs:148: error: too many arguments to function ‘libnet_get_hwaddr’
Arping.xs:148: warning: assignment from incompatible pointer type
Arping.xs:153: error: dereferencing pointer to incomplete type
Arping.xs:156: warning: passing argument 6 of ‘libnet_build_ethernet’ from incompatible pointer type
Arping.xs:156: error: too few arguments to function ‘libnet_build_ethernet’
Arping.xs:161: warning: passing argument 12 of ‘libnet_build_arp’ from incompatible pointer type
Arping.xs:161: error: too few arguments to function ‘libnet_build_arp’
make: *** [Arping.o] B&#322;&#261;d 1
root@orasoft-desk:/home/artur/download/Net-Arping-0.02# make > bad.log
cc: INC: No such file or directory
Arping.xs: In function ‘XS_Net__Arping_send_arp’:
Arping.xs:124: warning: passing argument 1 of ‘libnet_select_device’ from incompatible pointer type
Arping.xs:124: error: too many arguments to function ‘libnet_select_device’
Arping.xs:130: warning: assignment makes pointer from integer without a cast
Arping.xs:140: error: ‘LIBNET_IP_H’ undeclared (first use in this function)
Arping.xs:140: error: (Each undeclared identifier is reported only once
Arping.xs:140: error: for each function it appears in.)
Arping.xs:148: warning: passing argument 1 of ‘libnet_get_hwaddr’ from incompatible pointer type
Arping.xs:148: error: too many arguments to function ‘libnet_get_hwaddr’
Arping.xs:148: warning: assignment from incompatible pointer type
Arping.xs:153: error: dereferencing pointer to incomplete type
Arping.xs:156: warning: passing argument 6 of ‘libnet_build_ethernet’ from incompatible pointer type
Arping.xs:156: error: too few arguments to function ‘libnet_build_ethernet’
Arping.xs:161: warning: passing argument 12 of ‘libnet_build_arp’ from incompatible pointer type
Arping.xs:161: error: too few arguments to function ‘libnet_build_arp’
make: *** [Arping.o] B&#322;&#261;d 1


B&#322;&#261;d = Error (in English) :(

---

### Post by jfdill_2 on 2007-09-12
Darnit, I have just run into a similar problem installing Net::Arping but on Debian.  I did find there were a couple -dev packages that needed to be installed, libnet1-dev and libpcap-dev, maybe it depends on a different version of libnet.

Ah, got it, I installed libnet0-dev instead and then Net::Arping compiled correctly.

---

