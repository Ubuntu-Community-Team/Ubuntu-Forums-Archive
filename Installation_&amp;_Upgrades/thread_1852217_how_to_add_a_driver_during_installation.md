---
title: "how to add a driver during installation ?"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by electronico_nc on 2011-09-29
Hi all,

I'm not a Linux newbie, but when it comes to advanced things like that I'm a bit lost.

Well, I need to install 10.04.3 server on a P8P67 Pro motherboard with 3 HDs in RAID1.
10.04.3 doesn't recognize the Intel e1000e onboard NIC, so install fails because (from what I understand) mdadm needs postfix that needs a NIC.

I have the Intel e1000e drivers and I can install them from a Live session by doing :
```
tar -xvzf e1000e-1.2.2.tar.gz
cd e1000e-1.2.2
make
make install
```I would like to insert them at the network discovery step.
I can CTRL ALT F1 but then I'm lost with the mount points.

Would someone assist a bit with this ?
Thanks in advance for your time.

---

