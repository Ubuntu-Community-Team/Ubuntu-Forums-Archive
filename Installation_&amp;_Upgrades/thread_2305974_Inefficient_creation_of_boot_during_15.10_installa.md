---
title: "Inefficient creation of boot during 15.10 installation"
date: 2015-12-11
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2015-12-11
While waiting for the upgrade to 15.10 to complete I watched the scrolling console as it repeated a set of steps for EVERY linux image already present on the system.  Now I suppose I should have cleaned up that list before running the upgrade, but that was not one of the recommended preparation steps.  The upgrade would announce that it was going to remove some old image.  It would then complain that it couldn't find some parts of the kernel, which is probably explained by the fact that it had just deleted them!  It would then rebuild the boot menus, explicitly listing all of the images it claimed it had deleted!  And then it would do it again for the next old image.

---

### Post by howefield on 2015-12-11
Are you asking a question or relating your experience ?

---

### Post by grahammechanical on 2015-12-11
It is not actually deleting kernels but deleting and rebuilding kernel video driver modules for each kernel. It then runs grub-mkconfig to rebuild the boot menu. It runs this process one kernel at a time and then it searches for the existence of another kernel.

Be glad that you do not have several additional installations of Ubuntu or its flavours in other partitions because the process of reconfiguring the boot menu has to include what is on other partitions and in this case it can make the process drawn-out.

Something similar happens if we use Additional Drivers to change video drivers. It is one reason why changing video drivers can take a long time. The other reason is the need to download the new driver in the first place.

Regards.

---

