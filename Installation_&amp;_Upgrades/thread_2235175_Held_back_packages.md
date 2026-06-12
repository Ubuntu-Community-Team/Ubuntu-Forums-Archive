---
title: "Held back packages"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2014-07-19
I just ran ' sudo apt-get update && sudo apt-get upgrade -y' and I got

The following packages have been kept back:
  duplicity linux-headers-generic-lts-raring linux-headers-generic-lts-trusty
  linux-image-generic-lts-raring linux-image-generic-lts-trusty


I tried Clean and auto-remove; no changes.


Any ideas? I'm not sure if its a problem...

---

### Post by chick2 on 2014-07-19
you will need to run 'sudo apt-get dist-upgrade' to get the help back packages

---

### Post by ian-weisser on 2014-07-19
New kernels, and packages the depend on them, are not installed on a normal apt-get upgrade.
This is to protect you. Apt may not know about customizations that rely upon a specific kernel - video drivers, specialized applications, etc.

It's not a problem.

Chick2 is right about how to install those kernel packages...if you want to.
I run no proprietary drivers or other kernel-specific software, so I install them.

---

### Post by grahammechanical on 2014-07-19
I have found that held back packages do get download and installed in time as the packages (dependencies) they are waiting for catch up with them. Apt-get will sometimes say that certain packages have been downloaded but not installed. It must be part of the same process.

[http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)

Regards.

---

