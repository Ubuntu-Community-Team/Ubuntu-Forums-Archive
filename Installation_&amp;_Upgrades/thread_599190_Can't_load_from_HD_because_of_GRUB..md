---
title: "Can't load from HD because of GRUB."
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by samcarton on 2007-11-01
I installed Ubuntu on a USB drive to test it, but I now need it as a normal storage device (Ubuntu is no longer on the device.) When I go to load Windows, It comes up loading grub, error loading grub :21.:confused:

---

### Post by louieb on 2007-11-01
When you installed Ubuntu you also replaced **ntldr** with GRUB for the boot loader/manager. Very normal dual boot setup. Now you need to alter the MBR of the hard drive to point back to **ntldr**. Heres how: [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

