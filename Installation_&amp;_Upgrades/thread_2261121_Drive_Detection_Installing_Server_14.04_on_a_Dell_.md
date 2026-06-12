---
title: "Drive Detection Installing Server 14.04 on a Dell Optiplex 360"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by john_kim on 2015-01-16
Hi everyone,

I was trying to install a USB stick image onto an old Optiplex but the only drive that the installer detects is the USB stick itself.*

lspci reports the controller as an ICH7 variety and dmesg shows that the Hitachi 2gb disk is detected as /dev/sda.

Can someone please help?

Thanks in advance!
PS: Sorry for the cross-post with the server mailing list.

---

### Post by john_kim on 2015-01-16
Fixed by installing CentOS.  Maybe the older versions of stuff they're using is more compatible...who knows.

Thanks to everyone who may have been thinking about this issue!

---

### Post by MAFoElffen on 2015-01-16
Please visit back top this thread, use the thread tools in theupper left hand corner > Mark as solved. 

-OR- Investigate the why and not have problems later. Centos 7's kernel is 3.10, Ubuntu 14.04LTS is 3.13.43... (Testing 3.19rc3 now on 15.04) I think if you gave it an ACHI option on boot, you might have been fine.  The ICH7 (Base) and ICH7-U (Ultra-mobile) chipset did not support AHCI.

---

