---
title: "Prevent LTS upgrading but keep updates going"
date: 2024-09-14
forum: Installation &amp; Upgrades
---

### Post by digisystem on 2024-09-14
Hi all, for a certain period of time I am obliged to keep my Ubuntu 22.04.5 LTS not upgrade to the 24.04.1 LTS.

I would like to keep my packages and stuff updated, but I do not want accidentally upgrade my system to the next LTS version.

How to block LTS upgrades but keep other updates going?

Thank you

---

### Post by Dennis N on 2024-09-14
When completing any updates, just don't click the "Upgrade" Button (see image attached). Other updates will still continue. Even if you did accidentally click it, there are options to abort the procedure without harm.

---

### Post by deadflowr on 2024-09-14
Change the line in the file /etc/update-manager/release-upgrades from Prompt=lts to Prompt=never and save it.
You'll never see the Upgrade option again.

Can also be done in Software and Updates by changing the entry in Updates > Notify of me of new Ubuntu version: and toggle it from For Long Term Support Version to Never.

You can do one or the other as they'll both change together.
 

When it's time to upgrade to the next release, reverse it and reset it back.

---

### Post by digisystem on 2024-09-15
Thank you ! Exactly what I was looking for

---

