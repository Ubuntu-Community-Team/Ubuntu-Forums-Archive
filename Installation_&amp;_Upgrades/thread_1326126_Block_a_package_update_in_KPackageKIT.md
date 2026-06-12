---
title: "Block a package update in KPackageKIT"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by gianvito on 2009-11-14
Hi all,
I need to block the update of a package in KPackageKIT. 
I used wajig hold <package-name> to block it in APT, but the updates still appear in KPackageKIT...is there a way to lock them there too?

Thanks

---

### Post by gianvito on 2009-11-14
no solution?

---

### Post by ocarinahuff on 2010-10-16
KPackageKIT doesn't respect dpkg hold, or even aptitute hold.

It will recognize pinning from APT, though.  Check out this how to for APT pinning.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

