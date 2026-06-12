---
title: "RAID1 + multiple OSes"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by strm on 2010-08-31
Hi,
I have a setup with two 1TB drives which I would like to run in RAID1. I would also like to to have both Ubuntu Server and Windows Server on this box all residing on this 1TB array.

Is this possible and reliable? Is making Ubuntu Server run on "hardware RAID" (on-board controller) reasonable? Or does dmraid, LVM take care of the array better making it a software RAID? In which case, perhaps I can run Windows Server in a VM?

I setup the array using the controller BIOS and just added both drives to one single RAID1 array, then partitioned approximately as follows:
sda1 200gb ntfs (unused atm)
sda2 32gb swap
sda3 1gb /boot
sda5 767gb logical, rest of linux ext4
--various sizes for / /home /usr etc.

At the moment I can't seem to get Ubuntu to boot following installation.

What do you think? Hard of soft raid? Windows in VM?

---

### Post by Grenage on 2010-08-31
If it's a real hardware RAID card, use it.  If it's onboard 'fakeraid', I'd pass.

---

### Post by strm on 2010-09-01
i've opted to use the linux software raid config to setup a simple partition scheme that looks something like

1gb   /boot
199gb /usr
200gb /var
600gb /

with homes NFS mounted.

i've been advised to use reiserfs for performance on linux partitions and xfs for a VM mount point that will be used for a vm running windows. Any opinions on this around here?

Thanks!

---

