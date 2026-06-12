---
title: "Upgrade error  X.org"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by zuidema on 2008-01-18
Below is error message I get when doing a update


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)
  403 Forbidden

---

### Post by jeffus_il on 2008-01-18
Are you using the Update Manager on the Gnome desktop?

---

### Post by jtuchscherer on 2008-01-18
I had the same problem. Refreshing the list of updates solved it for me.

---

### Post by NilsE on 2008-01-18
Known problem.  There is a lock on the upgrade since there is a bug in it that impacts Java and maybe a few other things.

---

### Post by p_quarles on 2008-01-18
There are 8 other threads on this issue on the first page of this sub-forum alone. ;)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

---

