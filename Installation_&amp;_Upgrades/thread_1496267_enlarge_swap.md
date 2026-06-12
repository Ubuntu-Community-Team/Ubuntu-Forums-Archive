---
title: "enlarge swap"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2010-05-29
HI
i remarked to have only 2GB swap but my RAM is 4GB. For hybernation etc. i need to increase to 4GB swap? All HDspace is used. Any way to safely increase without loosing any data?
Thanks

---

### Post by lmarmisa on 2010-05-29
You can use Gparted. But this is not a trivial task. You will need to shrink another partition before enlarge your swap partition. And the resize of the swap partition will modify its UUID. So you will need to update the /etc/fstab with the new UUID of the swap partition. 

So, this is feasible but it is not too easy.

---

