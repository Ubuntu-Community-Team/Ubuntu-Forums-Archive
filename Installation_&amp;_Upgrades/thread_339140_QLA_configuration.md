---
title: "QLA configuration"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by vincent71 on 2007-01-15
I just installed ubuntu server on one of our HP DL 580. 

The QLA2300 is detected but I failed to configure it. 

In redhat I write config in /etc/modprobe.conf file :
options qla2xxx  ql2xmaxqdepth=16 qlport_down_retry=30 ql2xloginretrycount=16 ql2xfailover=1 ql2xlbType=1 ql2xautorestore=0x80

I tried to add this line to /etc/modprobe.d/aliases but it is not taken into account by system. The qla do not work in failover mode...

In which file may I add qla module configuration ?

---

### Post by vincent71 on 2007-01-22
I added the option in
 /etc/modprobe.d/qla2xxx.modprobe

But the QLA card is still in non redonctant mode. Each LUN is detected twice.

I tried to recompile QLA moduel. But I still have the same issue.

---

