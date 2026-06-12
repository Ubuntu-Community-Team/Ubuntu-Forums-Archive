---
title: "Installation of 18.04.2 wants to format all existing swap partitions, can I prevent ?"
date: 2019-02-22
forum: Installation &amp; Upgrades
---

### Post by nurber3 on 2019-02-22
Hi Forum.  I have a host with multiple OS installations and several drives including some Software RAID1 mirrored with LVM on top.  I have a dedicated drive for this Ubuntu installation, but when I run the installer and specify to edit partitioning myself so as to ensure the correct end results installer informs me it wants to format all existing swap partitions.  I understand that I should be safe formatting swap, but I really don't want the installer touching anything on the mirrored or LVM drives.  I've inlined a photo below if it helps.  Any way short of disconnecting other drives to ensure that nothing else is touched ?  Thank you,  Sven
[ATTACH=CONFIG]282610[/ATTACH]

---

### Post by oldfred on 2019-02-22
I do not have LVM, but multiple installs, some that created swap on drive.
My new installs, I click on every swap partition and choose do not use.

I have had swap reformatted & it then changes UUID. Then any install still using that swap will not boot until fstab updated with new UUID.

---

### Post by Tadaen_Sylvermane on 2019-02-22
I use lvm. Why do you need multiple swaps. I routinely have 2+ distros installed. They share a swap partition.

---

### Post by nurber3 on 2019-02-26
> **oldfred said:**
> I do not have LVM, but multiple installs, some that created swap on drive.
My new installs, I click on every swap partition and choose do not use.

I was not aware of facility in installer to explicitly not use.  In my case the LVM partitions shown in original inlined image as going to be formatted were not checked on the previous display where I choose what happens.   That the installer wants to do something that I haven't explicitly asked for seems wrong.

> I have had swap reformatted & it then changes UUID. Then any install still using that swap will not boot until fstab updated with new UUID.

Good point, my other installations are just using /dev names so not of concern.

Thanks for replying.

---

### Post by nurber3 on 2019-02-26
> **Tadaen_Sylvermane said:**
> I use lvm. Why do you need multiple swaps. I routinely have 2+ distros installed. They share a swap partition.

Certainly don't need, just cruft from previous installs that seems safest not to try to clean up.  Thanks for replying.

---

