---
title: "how to install dom0 on ubuntu 14.04"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by emrah6 on 2016-04-24
Hi there, I am trying to install Xen hypervisor 4.4 on ubuntu 14.04 for days. Finally, I found a tutorial and did some part of it but stuck at some point again.

I followed the instructions at [here ]("http://ubuntuforums.org/showthread.php?t=2008795")but I learned that the "xm" is not valid anymore, and there is a new tool, "xl", instead of it. And it is not working:

xl create -f xm-debian.cfg -c install=true install-kernel="/root/xensucks/vmlinuz" install-ramdisk="/root/xensucks/initrd.gz" install-mirror="http://ca.archive.ubuntu.com/ubuntu" install-arch=amd64 install-method=network
The above line returns the "how to use" page of "xl"

Can anyone tell me what to do? Thanks in advance.

---

