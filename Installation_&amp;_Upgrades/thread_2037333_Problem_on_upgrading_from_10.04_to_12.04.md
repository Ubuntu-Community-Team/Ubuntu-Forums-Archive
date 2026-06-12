---
title: "Problem on upgrading from 10.04 to 12.04"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by manosonem on 2012-08-04
Hi,

yesterday i decided to upgrade from 10.04 (32-bit) to 12.04 (32-bit) but after rebooting i get the following error(s):

** (plymouthd:317) : WARNING **: Command line 'dbus-launch --autolunch=ca673ea319228ac3ae5ce7964e2eab4a --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolunch error: X11 initialization failed.\n udevd[341]: specified group 'colord' unknown

[   5.831191] sd 4:0:0:0 [sdc] Assuming drive cache: write through
[   5.831191] sd 4:0:0:0 [sdc] Assuming drive cache: write through
[   5.831191] sd 4:0:0:0 [sdc] Assuming drive cache: write through

And in the next 3 lines there is a message that i can not read well because of the encoding(greek) but it says something about pressing "S" or "M" but if i press any of these buttons, nothing changes.

This message appears after the post screen and it does not reach to enter the grub.

---

### Post by El Potro on 2012-08-06
Hi,

GRUB has already booted, but it's menu is set to be hidden with no timeout.

Do you have any pen drive or external hard disk plugged in? 

It seems there's a problem with sdc, which means the third hard disk (it could be a pen drive too).

S is to skip and M to manually repair, this usually appears when you face a disk problem.

You can try booting from a live cd and doing fsck on all the partitions, (/dev/sdc1, /dev/sdc2, etc) also you can edit the grub.cfg or re-build it with this live cd to have a timeout.

I hope this helps.

---

