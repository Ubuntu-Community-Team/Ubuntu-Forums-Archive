---
title: "Ubuntu does not boot when on battery (after 17.10 upgrade)"
date: 2017-12-06
forum: Installation &amp; Upgrades
---

### Post by Steve_Hicks on 2017-12-06
After upgrading to Ubuntu 17.10 my laptop does not boot (stalls on start up flash page) UNLESS I plug my battery in.

This only happened after upgrading from 17.04 to 17.10

Once booted it works OK on battery power only

---

### Post by pm-texs on 2017-12-10
> **Steve_Hicks said:**
> After upgrading to Ubuntu 17.10 my laptop does not boot (stalls on start up flash page) UNLESS I plug my battery in.

This only happened after upgrading from 17.04 to 17.10

Once booted it works OK on battery power only

+1

Any resolution ?

I had no problem with 17.04 Ubuntu Gnome with this laptop and one other.  Both Asus, one B400A and one U47A.  Clean install on both. No upgrade.

---

### Post by jboesche on 2018-01-14
The same issue here (lenovo b5400, on kernels 4.11 and 4.13, ubuntu 17.10). Any ideas?

---

### Post by domakistan on 2018-02-10
Same problem with dell xps 13 (9343).
I've filed a bug [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1748639](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1748639)
Feel free to add information.

Christophe

---

### Post by domakistan on 2018-02-12
With [FONT=courier new]acpi=off[/FONT] (see [https://wiki.ubuntu.com/DebuggingKernelBoot](https://wiki.ubuntu.com/DebuggingKernelBoot)), my system boots completely.

---

### Post by jboesche on 2018-02-12
Worked for me too, except for non-working wifi ;(

---

### Post by jboesche on 2018-04-03
Looks like it's been fixed by today's updates (at least my laptop booted up 3 times without AC power).
Might have been:
linux-image-4.13.0-38-generic:amd64
linux-tools-4.13.0-38:amd64
(and related)

---

