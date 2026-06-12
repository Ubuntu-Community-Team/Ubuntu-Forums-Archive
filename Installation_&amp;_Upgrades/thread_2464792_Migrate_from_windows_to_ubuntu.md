---
title: "Migrate from windows to ubuntu"
date: 2021-07-12
forum: Installation &amp; Upgrades
---

### Post by farbodkain on 2021-07-12
hi, I'm new to Linux and ubuntu and want to migrate from windows 10 to ubuntu. just have one question. My laptop has two hard disks and one of them is SSD and both of them formatted with NTFS. I want to install Ubuntu on SSD and use the another hard disk which is full of data inside ubuntu with format it.
is it possible? is it effect on performance?

---

### Post by CatKiller on 2021-07-12
> **farbodkain said:**
> I want to install Ubuntu on SSD and use the another hard disk which is full of data inside ubuntu with format it.
I'm guessing from context that you mean *without* formatting it. Yes, that's possible. Installing on the SSD will format that (obviously), but there's no reason why you'd need to format your other data drive. You can choose to set up automatic mounting of that drive during the install process, or do it later. Linux can read NTFS OK, but long term you'll want to switch to a native format since NTFS tends to eventually eat itself and can only be repaired by using Windows tools.

---

### Post by farbodkain on 2021-07-12
> **CatKiller said:**
> I'm guessing from context that you mean *without* formatting it. Yes, that's possible. Installing on the SSD will format that (obviously), but there's no reason why you'd need to format your other data drive. You can choose to set up automatic mounting of that drive during the install process, or do it later. Linux can read NTFS OK, but long term you'll want to switch to a native format since NTFS tends to eventually eat itself and can only be repaired by using Windows tools.
thank you so much .

---

### Post by Impavidus on 2021-07-12
I would expect somewhat poorer performance when using NTFS and it will get worse over time if you write to that partition. Further, if you don't fully shutdown Windows before wiping it (that is, disable fast startup), Ubuntu will be unable to write to the NTFS partition from day one. Otherwise, the day that Ubuntu cannot write to the NTFS partition will come later. So eventually you have to convert that disk to a native Linux filesystem, which means formatting the drive and restoring the files from your backups.

---

