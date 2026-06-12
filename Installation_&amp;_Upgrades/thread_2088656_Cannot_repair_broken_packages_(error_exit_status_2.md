---
title: "Cannot repair broken packages (error exit status 2)"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by NaturalSizma on 2012-11-27
Hi,

I would like to install stuff, but I cannot since I always get this broken packages report.
With apt-get,I tried to update, autoremove and clean but it did not work.
Since it concerns libc6, I am not sure whether I should reinstall the packages. Maybe this is insecure due to all its dependencies.
It would be great if somebody could help me out.

I am using ubuntu 12.04, and get this message:

E: /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb: subprocess new pre-installation script returned error exit status 2
E: /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb: subprocess new pre-installation script returned error exit status 2

---

### Post by slickymaster on 2012-11-27
You should take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=2073770&page=2").

---

### Post by wojox on 2012-11-27
Try these two commannds:```
sudo dpkg --configure -a
sudo apt-get -f install

```

---

