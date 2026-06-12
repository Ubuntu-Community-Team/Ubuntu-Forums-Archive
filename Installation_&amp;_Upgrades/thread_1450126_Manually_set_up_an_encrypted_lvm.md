---
title: "Manually set up an encrypted lvm"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by komputes on 2010-04-08
How can I set up an encrypted LVM without using the "Guided - Use entire disk" option of the alternate installer.

My drive is quite big and I would like to be able to have my encrypted LVM as well as an extra LUKS encrypted partition which I could mount whenever needed. Unfortunately the options in the alternate installer do not allow me to do this without using up the entire disk.

---

### Post by Colt45 on 2010-05-01
This thread appears to be what you're looking for.  However, I am using this guide running into an issue when booting from a fresh install of Ubuntu 10.04.

This guide did work for 8.10 - 9.10 although it was missing information on how to proceed for some additional steps added since the guide was created.

[http://ubuntuforums.org/showthread.php?t=1205372](http://ubuntuforums.org/showthread.php?t=1205372)

---

### Post by lilpiggie on 2010-05-01
Select: Partition disks
Select: Manual

or if you find it easier, the alternate installer gives you the option to execute a shell. Use cfdisk or fdisk and do it yourself +lvm etc. then exit back to the installer set the mountpoints etc. and continue with the installer.

---

