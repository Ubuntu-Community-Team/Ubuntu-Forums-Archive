---
title: "Upgrade from 5.10 to 6.06 not working...."
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by jdavidw13 on 2007-02-03
Hi all,

I've got Ubuntu 5.10 up and running on a virtual machine.  When I try to do the 6.06 update in the update manager it gives me this:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)

Anyone have any insight as why it is failing?

---

### Post by taurus on 2007-02-03
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** in front of all the repos in there.  Then, try it again.

---

### Post by jdavidw13 on 2007-02-04
That seemed to do it.  Thanks alot =)

---

