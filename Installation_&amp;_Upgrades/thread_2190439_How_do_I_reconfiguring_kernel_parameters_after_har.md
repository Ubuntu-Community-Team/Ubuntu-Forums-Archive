---
title: "How do I reconfiguring kernel parameters after hardware change ?"
date: 2013-11-27
forum: Installation &amp; Upgrades
---

### Post by gedizgursu on 2013-11-27
[B]Problem Description : 
[/B]I have installed my system to a Virtual Machine (Ubuntu 12.04 64 bit) ... 
I repartitioned my drive and rsync'ed files from virtual file system to new partition 
chroot 'ed and modified grub and reinstalled 
I have working 2. linux system 
I have installed drivers and utils specific to my hardware (macfanctld, nvidia drivers)
however ist extremely slow (its initial loading is very slow, I wait 5 to 10 seconds after clicking Chrome icon)
My Computer is Laptop MBP 2008  Late (2.4 Ghz C2Duo with 4GB 1033 DDR3) 
My disk is a properly functioning 500 GB Seagate 7200 RPM 2.5''

I assume **these problem constraints equates to changing kernel parameters after hardware change**, I might as well copied it from an very old but compatipble box. 

**My so far not-working treatment :**

I ve changed 
vm.swappiness=5
vm.dirty_background_ratio = 25
vm.dirty_ratio = 40
vm.vfs_cache_pressure=30

Suspected from Virtual file system performance and changed hdd parameters using 
hdparm -B 254 -S 240 -M 254 /dev/sda

What else should I do ?
*obv reason is my usb and cd drive does not boot propperly - assume that they wont boot properly ever...

Thank you.

---

