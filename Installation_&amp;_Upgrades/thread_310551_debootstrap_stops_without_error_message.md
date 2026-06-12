---
title: "debootstrap stops without error message"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by kleb on 2006-12-01
I'm trying to install Ubuntu on an old laptop that has no CD drive. I'm following [these instructions]("https://help.ubuntu.com/community/Installation/WithFloppies").

For debootstrap, I've downloaded debootstrap-udeb_0.3.3.1ubuntu1_i386.udeb

When I come to the step where it says:

```
/usr/sbin/debootstrap --arch i386 hoary /target http://ftp.bit.nl/ubuntu/
```

(I replaced "hoary" with "edgy" and the ftp server with archive.ubuntu.com), the method fails. debootstrap just stops working after printing:

```

I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
~ #
```

Obviously this is incomplete and I can't continue chrooting into the environment. What am I doing wrong?

---

