---
title: "VMware player trouble"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by ambuj123 on 2007-02-10
Hello i installed Vmware-player using the automatix script it installed allright and created menu entry now when i start vmware-player and load vmx file it show following error

Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

now at command line if i issue command /etc/init.d/vmware-player start
it shows following error

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

please help
:(

---

### Post by ciscosurfer on 2007-02-10
> **ambuj123 said:**
> Hello i installed Vmware-player using the automatix script it installed allright and created menu entry now when i start vmware-player and load vmx file it show following error

Could not open /dev/vmmon: No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.

now at command line if i issue command /etc/init.d/vmware-player start
it shows following error

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

please help
:(I keep hearing about this error.  I would suggest going to [http://getautomatix.com](http://getautomatix.com) and posting about it in their forum as this is an anoying issue.  Hopefully they can put out a bug fix for it.

---

