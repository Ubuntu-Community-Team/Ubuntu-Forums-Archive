---
title: "Updates"
date: 2019-12-22
forum: Installation &amp; Upgrades
---

### Post by albert-redditt on 2019-12-22
Failure when installing updates.

When an update , contains a new kernel , it doesn't remove all the obsolete older kernels..

The boot partition gets full of old kernels , and it results in an upgrade failure..

Using Ubuntu 16.04 LTS.

---

### Post by Bashing-om on 2019-12-22
albert-redditt; Hello -

The system does not presume what you want. By the default old kernels are kept in the event that you might want to keep them around.
You can change that behavior in unattended-upgrades:
 [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

my bit to try and help

---

### Post by Impavidus on 2019-12-23
As Bashing-om says, you can configure Ubuntu to remove old kernels, but it doesn't remove them immediately by default. It's a while ago that I used 16.04, so I don't remember exactly what 16.04 can and can't do automatically.

If your package manager already got stuck because of a full /boot partition, you may need some manual cleanup first. Can you first try```
sudo apt update
sudo apt autoremove --purge
```and then, if you've still got a problem, show us the output of```
uname -r
df -h /boot
dpkg --list | grep linux-
```

---

### Post by rsteinmetz70112 on 2019-12-23
You might also want to show us the contents of /boot so we can see how many kernels are there.

---

