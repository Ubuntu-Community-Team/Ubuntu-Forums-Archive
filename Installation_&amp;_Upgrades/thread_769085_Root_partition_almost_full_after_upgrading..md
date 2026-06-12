---
title: "Root partition almost full after upgrading."
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Sivan on 2008-04-26
After upgrading from Gutsy to Hardy my / partition is almost full.

I checked around and noticed my /usr/lib is using 830 Megabytes and /usr/share is using 530 Megabytes.

Isn't this a little excessive? If not, I may have to resize my root partition (again).

Anyone know how I can free up space on the / partition?

Thanks

---

### Post by Pumalite on 2008-04-26
Clean the garbage can. Also:
sudo apt-get clean

---

### Post by Sivan on 2008-04-26
> **Pumalite said:**
> Clean the garbage can. Also:
sudo apt-get clean

There is only 13 Megabytes in the apt cache.

Is there a reason there is so much in the /usr/lib and /usr/share directories?

Did hardy increase in size that much?

---

