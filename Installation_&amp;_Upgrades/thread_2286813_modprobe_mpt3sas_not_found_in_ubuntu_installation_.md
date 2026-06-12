---
title: "modprobe mpt3sas not found in ubuntu installation but should be"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by lz233 on 2015-07-14
[COLOR=#111111][FONT=Ubuntu]I'm trying to install ubuntu server 12.04.4 LTS on SAS drives. I'm booting the installation off of a live install usb. The problem is that ubuntu cannot detect any of these SAS drives. The proper driver that is needed is already part of the kernel. I tried to use the following:
modprobe mpt3sas
and I got a
fatal module not found error
the funny thing is that modprobe mpt2sas works but that's only for SAS-2, I need mpt3sas for SAS-3.
I checked the kernel, and it looks to be 3.13, which should have the mpt3sas module already. I also tried modprobe mpt3sas on my desktop version of ubuntu 12.04 and it worked fine.
Does the 12.04 server version have some sort of restriction on kernel modules? Why can I not access this particular module?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

---

