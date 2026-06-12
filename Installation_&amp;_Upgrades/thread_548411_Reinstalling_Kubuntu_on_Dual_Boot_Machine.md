---
title: "Reinstalling Kubuntu on Dual Boot Machine"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by teejay17 on 2007-09-11
Can anyone tell me how I can easily reinstall Kubuntu 7.04 on my dual boot machine? 
Something has messed up, and I would like to reinstall Kubuntu on the partition that already contains Kubuntu, without messing the Windows partition up. 
My system is set up pretty generically, as it is set up for dual boot, with one half of the hard drive for Kubuntu and one half for Windows.

---

### Post by Pumalite on 2007-09-11
You can install on top of the old Kubuntu. Make sure you point the installer to the right partition. The installer will do the formatting for you.

---

### Post by teejay17 on 2007-09-11
> **Pumalite said:**
> You can install on top of the old Kubuntu. Make sure you point the installer to the right partition. The installer will do the formatting for you.
Okay, what about the swap file and all that---will that also be formatted too?

---

### Post by Pumalite on 2007-09-11
The swap partition can remain intact if you want to.

---

### Post by teejay17 on 2007-09-11
> **Pumalite said:**
> The swap partition can remain intact if you want to.
The reason I ask is because I don't want to be creating another Kubuntu partition within a partition, thus cutting my partition in half again. 
I want to do a fresh Kubuntu installation over top of the partition already there, without compromising my Windows partition.

---

### Post by Pumalite on 2007-09-11
If you want more control over what you are doing, use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

