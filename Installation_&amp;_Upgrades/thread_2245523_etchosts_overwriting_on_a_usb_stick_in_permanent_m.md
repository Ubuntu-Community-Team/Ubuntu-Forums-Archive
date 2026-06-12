---
title: "/etc/hosts overwriting on a usb stick in permanent mode"
date: 2014-09-24
forum: Installation &amp; Upgrades
---

### Post by cloc3 on 2014-09-24
I'm using a kubuntu original usb stick, with an overlay partition, labeled casper-rw, in permanent mode, so I'm able to preserve all modification to my stick after reboot (new documents and new packages are both preserved).

instead, the /etc/hosts file is always overwitten after reboot, and I'm not able to find the service responsible of that.
Who is ti?
How may I avoid this issue?

---

### Post by cloc3 on 2014-09-25
to debug my problem, I've changed attributes on /etc/hosts in this way:
```

~ # chattr +i /etc/hosts

```
after reboot, I have this error in logs:
```

ubuntu ~ # grep -rH "\/etc\/hosts" /var/log/
/var/log/casper.log:/scripts/casper-bottom/18hostname: line 25: can't create /root/etc/hosts: Permission denied
/var/log/boot.log:/scripts/casper-bottom/18hostname: line 25: can't create /root/etc/hosts: Permission denied

```
may it be this a bug of casper?

---

### Post by ubfan1 on 2014-09-25
You have discovered a limitation of the "persistent" live media.  The fstab file from the static part gets used, then ignored, so a subsequent new fstab file (from the casper-rw filesystem) is just ignored.

---

### Post by cloc3 on 2014-09-25
> **ubfan1 said:**
> **... fstab** ...

sorry. why are you talking about of *fstab*, instead of *hosts*?
is it just a typo?

---

