---
title: "Where is vmware-server-kernel-modules-2.6.24-16 ?"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by realruntime on 2008-04-30
aptitude cannot find vmware-server-kernel-modules-2.6.24-16

Has the packet naming scheme changed in 8.04? What's the name for it now? I tried with vmware-server-kernel-modules, but that does not install or update anything.

With apt-cache search I cannot find anything suitable, too...

---

### Post by sultanoswing on 2008-04-30
Try this:

[http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29](http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29)

---

### Post by realruntime on 2008-05-01
Thanks. This would probably work.

But apt is not managing vmware any more after that (especially updates), because it is "installing vmware by yourself".

It can't be true that Ubuntus vmware does not work any more in Hardy...

---

### Post by BDNiner on 2008-05-01
I am having the same issue, vmware is no longer in the repositories. I downloaded the install file from vmware.com and it said that there are no modules for my kernel 2.6.24-16-generic. I also tried downloading the rpm and converting it with alien. It installs but will not run.

---

