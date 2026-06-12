---
title: "Local repo for Xenial"
date: 2022-07-15
forum: Installation &amp; Upgrades
---

### Post by p-johnson on 2022-07-15
Hi. I'm setting up a local repo for an offline Xenial server. The instuctions here: [https://help.ubuntu.com/community/AptGet/Offline/Repository/](https://help.ubuntu.com/community/AptGet/Offline/Repository/), under "download the online repository", third paragraph, item 1, indicates to download "Packages.bz2". However, I'm not able to find it at [http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/](http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/). Can you tell me where to find "packages.bz2"?

---

### Post by deadflowr on 2022-07-15
> Can you tell me where to find "packages.bz2"?
Nowhere.
That help page was last edited over a decade ago and things have changed since then.

I would just try it with the two Packages.XX files that are in there.

---

### Post by guiverc on 2022-07-15
Also don't forget Ubuntu 16.04 LTS completed it's *standard support* life some time ago now, thus ESM is required for upgraded packages after April-2021 (*as well as now some packages are supported now only via snap packages*).  You may not be using those *snap only *support packages (*they were mostly desktop packages*), but they do require a very different procedure.

[https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

---

