---
title: "Encrypted install dont work - no pw request on boot it just boot"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by twist2 on 2015-09-29
Hallo,

i have a problem with the setup of a new ubuntu install. i selected encrypted then i made a password and on the next screen i made 3 partitions by my own. When i now start my system no pw is needed to start. so i think my drive is not encrypted.
but why? is it not possible to make custom partitions when encrypted is selected on install?

---

### Post by deadflowr on 2015-09-29
> [COLOR=#000000] is it not possible to make custom partitions when encrypted is selected on install?[/COLOR]
As far as I think I know, it's only possible if you have pre-made the partitions for encryption before the installation.
They need to be specially crafted with utilities that are not provided for the user during install.

Otherwise you run into exactly what you have.
If you let the installer run it's automated setup for the encryption and left it as is, then you'd have an encrypted system.
But once you started trying to make your own partitioning scheme, your new partitiosn simply overwrote the installers encryption setup.

---

### Post by twist2 on 2015-09-29
Okay.  When i let the install do his work is there a swap and home partition? ore at least a swap for hibernate?

---

### Post by deadflowr on 2015-09-29
The installer for full-disk-encryption does mostly the same setup that a regular installation setup does.
With the added exception that the encryption setup makes a separate boot partition, they both make a single full root partition and a swap partition.
So no separate home partition.

As far as hibernation goes, that can get tricky.
[https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

---

