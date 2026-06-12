---
title: "Grub problem after creating a second external hard drive"
date: 2023-02-10
forum: Installation &amp; Upgrades
---

### Post by foxylady337 on 2023-02-10
I've set up an external hard drive with Ubuntu 22.04 to run an archival copy of a website offline on a Windows 11 laptop booting Ubuntu when required.

This is (mostly) working correctly after a lot of trial and error, and I decided to try a clean install of Ubuntu 22.04 and the LAMP stack on another external hard disc, and work systematically through the various combinations of php etc to get it to work fully.

Since I did this, I can no longer boot Ubuntu from the original external disc, all I get is a grub prompt.

Here is the link to my boot-repair report:

[https://paste.ubuntu.com/p/JQbgV4bRdZ/](https://paste.ubuntu.com/p/JQbgV4bRdZ/)

Thanks for your help in advance!

---

### Post by ubfan1 on 2023-02-10
See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379) Grub installs to
wrong disk. Do add yourself to the "Does this affect me?" list on the bug.
There are workarounds/solutions in the bug comments. Another problem is
that your host system probably will not boot without the external device (since
needed grub files are on it).

---

### Post by oldfred on 2023-02-10
Look at line 218.
Your install in sda5 is booting from the ESP - efi system partition in the mmc drive.
You need it to boot from ESP on sda or sda2. Not sure what sda1 which also is FAT32 but not an ESP?

You should be able to change fstab in sda5 to use sda2's ESP. Then totally reinstall grub & kernel so booting from sda2.
Note that external drives all boot from the UEFI : XXXX entry in UEFI boot menu, not an "ubuntu" entry which is for internal drives or in your case a internal drive boot, but rest of system on external drive. Actual boot is /EFI/Boot/bootx64.efi, not the /EFI/ubuntu/shimx64.efi. 
I think with UEFI Secure Boot on bootx64.efi, is just a copy of shimx64.efi, but may not be identical to one on internal drive.

---

