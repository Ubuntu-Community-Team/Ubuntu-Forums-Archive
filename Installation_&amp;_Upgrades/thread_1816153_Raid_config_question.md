---
title: "Raid config question"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by elguapo159 on 2011-08-01
Hi,

I have a ubuntu 10.10(Meerkat) and want to configure a raid 5 with 4 2TB disks. But the question is if i configure the raid 5 and my linux install(on other disk, not on one of the four) would need a reinstall or something goes wrong at a certain point in time, can a new linux install see the raid or will i lose all data?

Regards,
Elguapo

---

### Post by YesWeCan on 2011-08-01
Should be fine. The critical info is stored in the metadata blocks on the disks. So the new mdadm on the new linux will be able to scan these and reassemble the array. :)

---

