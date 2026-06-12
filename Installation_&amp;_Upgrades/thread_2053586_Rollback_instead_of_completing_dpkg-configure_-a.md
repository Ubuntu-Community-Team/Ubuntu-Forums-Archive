---
title: "Rollback instead of completing dpkg-configure -a?"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by mfpompadour on 2012-09-05
On a new VPS, aptitude dist-upgrade hangs during /usr/sbin/grub

Now, aptitude is in a bad state:

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

I can't successfully complete this command, because of /usr/sbin/grub hanging.

Can I rollback instead?

(This is on 12.04)

---

### Post by Mark Phelps on 2012-09-06
If by "rollback" you mean restore your setup to an earlier date, sorry, there is no such capability in Ubuntu.

---

