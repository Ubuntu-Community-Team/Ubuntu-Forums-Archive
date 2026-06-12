---
title: "Upgrade stops due to loss of internet, can't continue"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Jonny87 on 2010-10-17
I was running an upgrade and was about half way through the downloading of the new packages when my internet droped out. Stupid Router!!!!!
I've replaced the Router but now when I try to go back and continue the downloading the upgrade packages, Updat manager doesn't even recognize that 10.10 is available. When I click "check", it starts checking then at the end comes up with the following error.
> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Is there a quick fix? 
Please!!!

---

### Post by Jonny87 on 2010-10-17
Ok I've got it going now, used;
```
update-manager -d
```
from the run box.
It seems that it is contiuing the download from where it dropped out. Thank goodness. Now to ring the ISP and demand that they replace their faulty router.

---

