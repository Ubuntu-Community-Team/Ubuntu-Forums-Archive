---
title: "modules don't work after kernel upgrade"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by finite9 on 2006-08-21
I have an Acer Aspire 5021 laptop and need to install a tarball for acer_acpi to get my broadcom wireless adapter to work.

When I install this tarbell on kernel version X (e.g. 2.6.15-23 or whatever kernel I have when I install acer_acpi) then all works fine.

When I accept updates from official repos, and my kernel gets upgraded to 2.6.15-26, then the acer_acpi module cannot be modprobed anymore upon reboot.  I run make and make install again  for acer_acpi but still no luck.  Then I read the INSTALL file for acer_acpi and it mentioned that if it had trouble identifying the kernel then you could specify it in the makefile.  Upon doing this and specifying 2.6.15-26, then I could make, make install and modprobe acer_acpi, but it still wont work with my networking!!

It seems like it's not working properly when it's already been installed on a previous kernel and then re-installed on a newer kernel.

I know this is all very specific to acer_acpi but could someone give me any tips about what may need to be done to get modules working again that stop working after a kernel upgrade - like some general tips?

I get the feeling that it's files that exist in one library for the older kernel that should exist in the newer kernel library or that a link is incorrectly set.

I am positive that if I did a new install of Ubuntu 6.06 and upgraded to 2.6.15-26 (via wired net) before installing acer_acpi to get wireless working, then it would all work fine.  (I have already done this for 2.6.15-25--my current kernel).

---

