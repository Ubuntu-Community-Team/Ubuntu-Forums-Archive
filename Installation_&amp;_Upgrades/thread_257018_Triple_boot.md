---
title: "Triple boot?"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by radj2 on 2006-09-13
I installed dapper drake off the cd,it worked fine except for the fact that it hung up on shut.

Then I re-installed breezy badger and it works fine, I did all this on a second drive. The primary drive has 98se on it.

I would like to install dapper drake on the second drive and leave breezy on it as well,is that possible and will grub allow triple boots?

I would like to use dapper but the shut down problem is a real pain even if hard shut downs are no big deal

---

### Post by K.Mandla on 2006-09-14
> **radj2 said:**
> I would like to install dapper drake on the second drive and leave breezy on it as well,is that possible and will grub allow triple boots?
Definitely. Make sure you keep your partitions straight in your head, but if you're careful it will work like a champ.

As for the hang at shutdown, you might try adding acpi=off to your boot line. It sounds like a recent workaround for [this bug]("https://launchpad.net/products/linux/+bug/43961") ... but as always, depending on the hardware. ;)

---

