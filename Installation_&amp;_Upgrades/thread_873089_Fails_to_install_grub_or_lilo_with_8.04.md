---
title: "Fails to install grub or lilo with 8.04"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by davesbedroom on 2008-07-28
SuperMicro 6014H-82B server with
ADAPTEC 2015S Raidport w/48MB ecc cache(CTR153)
Adaptec RAID I20 bios v001.62 11/06/2002
Adaptec RAID Setup Utility V1.12/79I 11/22/2002
Running two drives in RAID 1

System was running great for two years with Ubuntu 6.06, but now I want to upgrade to Ubuntu 8.04 and it fails to install grub or lilo.

I have tried whipping the drives clean.  Tried deleting the raid array and installing it on no array and only one hard drive.

What can I do?  It appears that Ubuntu 8.04 fails to install grub or lilo every time.  I don't want to be stuck with Ubuntu 6.06.

When I install Ubuntu 6.06, I get no problems with my setup and it installs grub automatically.  What changed with Ubuntu 8.04?

---

### Post by davesbedroom on 2008-07-28
I think I have come up with a solution and would like some input.

I will simply install Dapper Drake 6.06 again.  Update it and then upgrade to Hardy Heron 8.04 using the Upgrade Manager.

Only problem.  Is there a way to upgrade without the Upgrade Manager, it looks like the Upgrade Manager needs X and I don't roll with X.

---

### Post by Sef on 2008-07-29
> What can I do? It appears that Ubuntu 8.04 fails to install grub or lilo every time. I don't want to be stuck with Ubuntu 6.06.

When I install Ubuntu 6.06, I get no problems with my setup and it installs grub automatically. What changed with Ubuntu 8.04?

Sounds like a problem during the upgrade.  Get [Super GRUB Disk]("http://www.supergrubdisk.org/") and use that to install GRUB.

---

