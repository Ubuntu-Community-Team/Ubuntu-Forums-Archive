---
title: "Maverick Freezes at Login"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by _hezekiah_ on 2010-10-31
I've recently upgraded to Ubuntu 10.10. Yesterday I installed a few updates and it has frozen at the login screen ever since.

Grub gives me 2 kernels to boot with, but it happens with both. Booting into recovery mode stops at
```
Begin: Running /scripts/init-bottom ... done.
```

I'm using a Dell Studio 1558 laptop.

---

### Post by P4man on 2010-10-31
Sounds like the same issue described here:
[https://bugs.launchpad.net/ubuntu/+bug/398214](https://bugs.launchpad.net/ubuntu/+bug/398214)

Although thats an old bug, you could try the same workaround. Boot a live cd, mount your harddrive, locate the /etc folder (on your harddrive, not the  one on your livesystem so something like  /media/yourdrive/etc and NOT /etc) and remove the .dpkg-new file extension on any files there.

---

### Post by _hezekiah_ on 2010-11-01
Thanks, but it doesn't work.

---

### Post by _hezekiah_ on 2010-11-30
I've decided to reinstall Ubuntu. I still get an occasional freeze, but it works.

---

