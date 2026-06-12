---
title: "ati radeon 9500 install help"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by potato_head on 2010-03-01
hi 
i am tring to get this driver working ati-driver-installer-9-3-x86.x86_64.run

and this is the command in the temmanl i put in
sh ati-driver-installer-9-3-x86.x86_64.run

 and this is what i get

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-14-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.1r3l5a
please help.....:D

---

### Post by khelben1979 on 2010-03-02
Try with: ```
sudo sh ati-driver-installer-9-3-x86.x86_64.run
``` to see if it gets better.

---

### Post by Mark Phelps on 2010-03-02
If you're running Ubuntu 9.04 or newer, there is no current ATI driver that will work with your card -- no matter HOW you try to install it.

While some of the "older" (Catalyst 9.2, 9.3) drivers WERE designed to work with your card, they will not work with the X-server in the newer Ubuntus.

To make them work, you have to downgrade and lock your X-server -- something I would recommend you NOT do.

---

