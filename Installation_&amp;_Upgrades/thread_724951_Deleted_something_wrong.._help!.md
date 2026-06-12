---
title: "Deleted something wrong.. help!"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Thijmen on 2008-03-15
Hello,

After I cleaned up ubuntu, i've deleted something wrong in /etc/init.d/
After reinstalling postfix and postfix-admin, i'm getting this error:

update-rc.d: /etc/init.d/postfix: file does not exist

I've created the same map, but it wouldn't help.

Maybe can you help me?!

Thnx!

---

### Post by Thijmen on 2008-03-15
How do i solve this?

---

### Post by Lord Landis on 2008-03-16
Okay, first things first, why were you deleting things from '/etc/init.d'?

If you've reinstalled postfix, have you verified that '/etc/init.d/postfix' actually exists?  And if it does, is it executable?

---

