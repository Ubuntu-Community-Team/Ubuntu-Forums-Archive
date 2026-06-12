---
title: "Boot parameters are ignored"
date: 2014-02-27
forum: Installation &amp; Upgrades
---

### Post by yzord2 on 2014-02-27
Since a few years i am new into Linux, mostly Debian/Ubuntu, and since a  few months my boss wants me to move to the Linux department. He gave me  a "special" mission (for me it is).

We have hundreds of RHEL servers of which we use kickstart for and  Puppet after that to deploy packages. But now one of the teachers wants a  Ubuntu (small) farm of which he can order and deployed within a day. My  boss asked me to find a way to deploy Ubuntu on VM's trough kickstart  or preseed. Well, that part has been realized....sort off. I have  managed to kickstart Ubuntu without any error, but with a small annoying  detail. The ks.cfg file is located in the image (.iso). And thats a  problem, because the .cfg contains information about static IP  configuration. That means i have to extract the iso every time when they  order a new Ubuntu VM.

So, of course i have thought about it to finalize the IP settings before the CD starts in vSphere. Tried many ways, but now i'm stuck. I am out of ideas. What i want is a submission to the line like:

> file=/cdrom/preseed/ubuntu-server.seed initrd=/install/initrd.gz netcfg/disable_autoconfig=true network --bootproto=static --ip=xxx.xxx.xxx.xxx --netmask=255.255.255.0 --gateway=xxx.xxx.xxx.xxx --nameservers=xxx.xxx.xxx.xxx --device=eth0 ks=http://location.of.ks.cfg

It pushes dhcp disabling ok, but the other networksettings are totally ignored and i have to fill it in personally. What am i doing wrong?

---

