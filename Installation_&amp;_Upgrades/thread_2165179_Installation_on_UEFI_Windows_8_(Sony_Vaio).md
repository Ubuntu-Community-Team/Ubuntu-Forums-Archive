---
title: "Installation on UEFI Windows 8 (Sony Vaio)"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by laugustogs on 2013-08-03
Well, guys, you see, my problem is that I already tried everything I read on the internet, but I simply can't get a proper dual boot with my new machine. I installed Ubuntu 13.04, and at first, everything seems fine, but when I boot into Windows and then restart the computer, I am not given the option to choose an OS, it just goes to Windows directly. I can only boot into Ubuntu following these intricate steps: I change the option from UEFI to Legacy in the BIOS, try to boot and get an error, go to BIOS and change Legacy to UEFI, and then try to boot, now GRUB opens.

I came here after trying the things in this page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I already disabled both the Secure Boot in the BIOS, and the fast startup in the Control Panel. I also ran the boot-repair on Ubuntu: [http://paste.ubuntu.com/5945243/](http://paste.ubuntu.com/5945243/)
No luck here...

Any help?

---

### Post by patspiper on 2013-08-04
Ubuntu (at least 13.04) can boot in UEFI/secureboot mode.

Does your bios allow you to press a button on reboot in order to select the boot device?

---

