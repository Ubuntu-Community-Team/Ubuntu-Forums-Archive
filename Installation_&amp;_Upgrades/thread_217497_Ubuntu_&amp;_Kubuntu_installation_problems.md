---
title: "Ubuntu &amp; Kubuntu installation problems"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by tong on 2006-07-17
_My Hardware_
-Celeron 1.7
-RAM 256 MB
-HDD 80 GB,ATA 
  (hda1->fat32,hda5->ntfs,hda6->/boot,hda7->swap,hda8->gentoo,will install at  hda9 with same swap& /boot with gentoo)

-Nvidia GeForce2 MX 200 32MB Ram
-Mainboard 4PM266AM/N
-Sound Onboard (VIA82Cxxx ... not sure..)
-CDRW LiteOn 52x32x52
----------------------------------------
I used Kubuntu 6.06 Desktop live CD . It's boot OK .I can use it from live CD environment. When I installed it to my HDD .Every things is ok until it's go to 94 % process  it's stop installation but it's not hang or stop.I cstill can use liveCD environment but it's show install process at 94 % for very long time.I don't know why?  

when...
$ ps -ef
root     12320  6578  0 17:43 ?        00:00:03 /usr/bin/perl -w /usr/bin/debconf-communicate -fnoninteractive ubiquity
root     12324  6578  7 17:43 ?        00:04:21 /usr/bin/python /usr/share/ubiquity/install.py
root     17443 12324  0 17:54 ?        00:00:03 /usr/bin/perl -w /usr/sbin/dpkg-reconfigure -fnoninteractive linux-image-2.6.15-23-386
root     17455 17443  0 17:55 ?        00:00:00 /usr/bin/perl /var/lib/dpkg/info/linux-image-2.6.15-23-386.postinst configure 2.6.15-23.39

When, I use this CD install at another machine (C700,Sis6326) , it can install and use with no problems.

With Ubuntu 6.06 Desktop CD
Every things same as kubuntu but it's show installing system at 95% for a long time.When....
$ps -ef
root     12320  6578  0 17:43 ?        00:00:03 /usr/bin/perl -w /usr/bin/debconf-communicate -fnoninteractive ubiquity
root     12324  6578  7 17:43 ?        00:04:21 /usr/bin/python /usr/share/ubiquity/install.py
root     17443 12324  0 17:54 ?        00:00:03 /usr/bin/perl -w /usr/sbin/dpkg-reconfigure -fnoninteractive linux-image-2.6.15-23-386
root     17455 17443  0 17:55 ?        00:00:00 /usr/bin/perl /var/lib/dpkg/info/linux-image-2.6.15-23-386.postinst configure 2.6.15-23.39


I'm very very confuse. Because I can install Ubuntu 5.10 with same hardware. Will you help me?  ... please.. I like *buntu very much.

**My CD is Good.I check it with md5sum and no error and write it at 4x**

Thank you very much

tong
:D

---

