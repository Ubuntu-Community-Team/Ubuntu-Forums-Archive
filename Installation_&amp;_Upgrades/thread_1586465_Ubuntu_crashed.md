---
title: "Ubuntu crashed"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-10-02
I was updating the security updates in my deskptop. It did not executed successfully even after 7 hours. It remain just like hang up. So I switched off the PC and rebooted. Then it is showing the error:
" udevadm trigger is not permitted while udev is unconfigured.
Gave up waiting for root device."
Now my Lucid Linx is almost dead. There is also no 'Repair' option while booting from Ubuntu 10.04 CD.  Pl help to restore it. Thanks.

---

### Post by mörgæs on 2010-10-02
What happens if you boot the machine and run

```
sudo apt-get update
sudo apt-get upgrade
```?

---

### Post by P4man on 2010-10-02
Looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/358654)

First post also has a solution.

---

