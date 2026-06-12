---
title: "Segmentation fault on multiple applications when upgrade from 16.04LTS to 18.10"
date: 2018-12-02
forum: Installation &amp; Upgrades
---

### Post by denis14 on 2018-12-02
I'm receiving "Segmentation fault" on multiple applications when trying to start them. All of them works regularly before upgrade. Any idea how to proceed?

Many thanks in advance.

---

### Post by ubfan1 on 2018-12-02
I'd get/make an install media and from it, run a memory check, and fsck the root filesystem. Did the upgrade involve removing/changing any hardware, like memory cards?  If so, try re-seating them.

---

### Post by oldos2er on 2018-12-02
> **denis14 said:**
> I'm receiving "Segmentation fault" on multiple applications when trying to start them. All of them works regularly before upgrade. Any idea how to proceed?

Many thanks in advance.

How did you upgrade? And which applications?

---

### Post by Impavidus on 2018-12-03
Are those applications from the official repositories or from somewhere else, like home made? Because in the latter case, you may have to recompile them to make them work with the newer libraries of your new Ubuntu release.

---

