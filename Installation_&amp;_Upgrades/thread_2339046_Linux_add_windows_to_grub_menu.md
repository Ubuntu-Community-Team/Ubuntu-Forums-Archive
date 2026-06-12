---
title: "Linux add windows to grub menu"
date: 2016-10-04
forum: Installation &amp; Upgrades
---

### Post by merchu on 2016-10-04
Hi,

Yesterday I made a dualboot with my windows 8 but after the installation I enter the grub boot menu and only the linux boot option is listed, windows (8) isn't in the menu.

I installed linux on my D:/ drive with a 40GB partition, windows is installed on C:/ (2 ssd's in raid0)

I tried updating the grub with "sudo update-grub" but that doesn't seem to be doing anything..

Any idea how I can solve this problem?

- Merchu

---

### Post by yancek on 2016-10-04
Some of the questions which need to be answered would be:

Was windows 8 installed using UEFI?
Did You also install Ubuntu UEFI?  Both systems must be UEFI or MBR, no mixing allowed.
The above discussed at the Ubuntu site below, read it:

** **[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Best to leave unallocated space as no Linux system will install and function on an ntfs proprietary filesystem  and since windows systems are incapable of formatting with a Linux filesystem, you will have to format during the install anyhow.  More info needed which you can get by running the boot repair software which you can get from the site below.  Be sure to read through the page carefully and only select the option to Create BootInfo Summary.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

