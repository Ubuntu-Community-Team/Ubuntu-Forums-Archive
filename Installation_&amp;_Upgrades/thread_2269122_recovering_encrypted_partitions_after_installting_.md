---
title: "recovering encrypted partitions after installting W7"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by bnm555 on 2015-03-13
Hi

I've reinstalled Windows 7 on my dual-boot machine. The linux partition was encrypted with LVM.

After installing W7 the machine only boots to W7. I've tried using boot repair disk, but it seems it couldnt access the encrypted partitions.

Any suggestions please?

boot repair disk has generated this url: paste.ubuntu.com/10591353

Thanks

---

### Post by oldfred on 2015-03-14
I do not know LVM nor encryption.
It looks like both sda4 &  sdb2 as encrypted LVM partitions.

Did you try Boot-Repairs suggestion. You may have to both install LVM drivers and manually mount the encrypted partitions so it asks for your pass phrase.You may want to retry after decrypting your partitions. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))

To install LVM drivers in live CD/flash drive:
sudo apt-get install lvm2

With two drives often better to fully have Windows on one drive and Linux on the other drive. And each drive with that install's boot loader so each drive can work without the other.

---

