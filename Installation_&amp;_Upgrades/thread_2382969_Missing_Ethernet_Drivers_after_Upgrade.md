---
title: "Missing Ethernet Drivers after Upgrade"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-01-19
I'm running 16.04 LTS and recently upgraded my install after a pretty long time of not upgrading.
After the upgrade my wired ethernet did not work.
Looking for the cause I discovered tha the appropriate driver had not been installed with the new kernel.
The former kernel was 4.4.0-103
The new kernel is 4.4.0-109
The drivers is r8169
In the 103 kernel it is located in /lib/modules/4.4.0-103-generic/kernel/drivers/net/ethernet/realtek
In the 109 kernel there isn't a directory named /lib/modules/4.4.0-103-generic/kernel/drivers/net/ethernet

Doing a package search it appears it should be in linux-image-extra but the package search did not list 4.4.0-109 (although 104 was listed)

What package is that driver located in? Why wasn't it loaded?

---

### Post by ubfan1 on 2018-01-19
Looks like you forgot the /net/ part of the path, just after ...drivers/

---

### Post by rsteinmetz70112 on 2018-01-20
That was a typo in my post. I actually ran a find looking for the driver.  It wasn't there. I've edited the post to reflect the correction.

---

### Post by ubfan1 on 2018-01-20
The driver should be in the linux-image-extras:
$ dpkg -S r8169.ko
linux-image-extra-4.4.0-109-generic: /lib/modules/4.4.0-109-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
linux-image-extra-4.4.0-104-generic: /lib/modules/4.4.0-104-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
Try reinstalling that ... 109 package.

---

### Post by rsteinmetz70112 on 2018-01-20
I will try it.

---

### Post by rsteinmetz70112 on 2018-01-20
That was the problem. Somehow during a kernel upgrade linux-image-extras was not installed. Not sure what happened but I've got some other problems with this machine.

---

