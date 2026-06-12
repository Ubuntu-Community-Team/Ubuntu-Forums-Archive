---
title: "dual boot using 2 hdd"
date: 2022-03-04
forum: Installation &amp; Upgrades
---

### Post by m3t3ors on 2022-03-04
hi i have a samsung np700g7c laptop with 2 internal hdd each are 750g. on the first hdd i have windows 11 but want ubuntu 20.04 on the second hdd. When i try install to the second hdd it says no root option. i cant see anywhere to select root storage or anything.

any help appreciated with this... i have done dual boots before but only to the same hdd, never to seperate hdd

---

### Post by oldfred on 2022-03-04
UEFI or BIOS system and installs?
Both Windows & Ubuntu need to be in same boot mode or both BIOS or both UEFI.
And if UEFI, both drives should be gpt partitioned.

Did you partition in advance & create an ESP - efi system partition on your second drive?
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

If using Something Else you must have or create an ext4 (or other Linux format) partition and tell installer it is / (root). 
Installer will find an ESP, normally on first drive and will find a swap partition if you have one. If no swap partition, it now creates a swap file.

See also links in my signature below.

---

### Post by yancek on 2022-03-05
If the error you are getting is no mount point selected for / (root) filesytem, you need to select a Linux partition if created or free/unallocated space which is explained at the link below in the Edit partition option.  See the explanation at the link below, about half way down the page. 

[https://www.linuxtechi.com/ubuntu-20-04-lts-installation-steps-screenshots/](https://www.linuxtechi.com/ubuntu-20-04-lts-installation-steps-screenshots/)

---

