---
title: "Grub changes boot HDD at every kernel upgrade"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by barney_1 on 2008-07-17
Hi Folks,

With my current setup I have both a SATA drive and an IDE drive in my box.  My OS is located on the SATA drive which is (HD0,0).

Every time I upgrade to a new kernel the /boot/grub/menu.lst file is updated so that it points to the kernel at (HD1,0) which then results in a "file not found" error next time I reboot.  This is not difficult to change by hand but I'm wondering two things:

1. Is there a workaround for this?
2. Should I file a bug report on this?  If so, what kind of log data should I include in the bug?

Thanks!

---

### Post by billrad1 on 2008-07-17
same here - linux on sata, windows on ide

rewrites my menu.lst with UIDs instead of drive locations.

I wouldn't mind if it worked, but it always fails to find the drives.

I though I had read where there is an fstab command to correctly determine the UIDs, but I could have imagined that....?

This, and the fact that I alway shave to reinstall my nvidia driver from a command line root session to get it to work, are the only two issues I never have with new kernels/headers, or whatever.

help folks, help!

Billrad1

---

