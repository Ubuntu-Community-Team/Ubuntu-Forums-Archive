---
title: "Grub loading Please wait   Error 18"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by Des on 2005-03-04
Hi
When I complete the initial installation of Ubuntu I am asked to remove the CD and boot from the hard driver. When I do this I get the following message.

GRUB Loading, please wait...
ERROR 18

How can I solve this problem? :confused:

---

### Post by illek on 2005-03-04
You will need to create a small /boot partition on your drive(about 50 Megs).  That error indicates that Grub is pointing to a sector on the drive that your BIOS is unable to use at boot time.  During the Ubuntu installation procedure, set your "boot" mount point to your newly created boot partition and your "/" mount point to the larger partition on your drive.

---

### Post by Des on 2005-03-04
Thanx
Will try that

---

### Post by Des on 2005-03-04
How do I create a boot partition?

---

