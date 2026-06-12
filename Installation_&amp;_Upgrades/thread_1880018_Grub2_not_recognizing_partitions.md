---
title: "Grub2 not recognizing partitions"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by rpgen on 2011-11-12
Hi,
I have 3 hard drives: 1 which has windows 7, two for storage, and I recently sectioned one of the latter for a Ubuntu 11.10 partition. When I boot into grub, I get the "Error: no such partition. Grub Rescue>". When I type ls, all that shows up is (hd0) (hd0,msdos1) (hd1) (hd1,msdos1) (hd2) (hd2,msdos1). Ubuntu was installed on sda5. And when I check with set, "Prefix=(hd0,msdos5)/boot/grub/"   and  "Root=(hd0,msdos5)"

[http://paste.ubuntu.com/736037/](http://paste.ubuntu.com/736037/)
I've tried reinstalling Ubuntu, Grub2, and using Boot-Repair to no avail. Although my hardware is relatively new, I'm wondering if the problem is with Grub or something else like my bios.
Any help would be appreciated.

---

### Post by oldfred on 2011-11-12
You have it installed to sda5 and for some reason script did not show all the boot files in sdb nor any of the boot of sdc.

The boot in sda seems to be looking for a config file in a partition that does not exist. Have you tried booting sdc? That may work even though install is in sda. But you should get grub2's boot loader reinstalled to sda. 

What options did boot-repair give you? Usually that will repair and reinstall grub correctly.

You also have grub2's boot loader in the PBR partition boot sector of sda5, but that should never be used.

Sometimes this will boot an otherwise good install and let you reinstall grub from a working Ubuntu.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by rpgen on 2011-11-12
Thanks for the reply.
Still haven't been able to get it to work though.

I tried booting from sdc. I get "Error: no such device: 5c87ffce-6478-44de-8aa9-6a68c1e8ff93    grub rescue>"

For boot-repair, I've tried Recommended repair. I've also tried the advanced options with 'reinstall grub' checked, 'OS to boot by default: sda5(Ubuntu 11.10)', 'place grub into: sda', and I left the entries in the Grub Options tab unchecked. I also tried it a separate time with 'Purge and reinstall Grub of: sda5(Ubuntu 11.10)'. I still the same error when loading Grub2 though.

I also tried Super Grub2 Disk, but I don't think it's working correctly for me. I placed it onto a usb and was able to boot it, but only two menu entries show up: 'Default' and 'List devices/partitions'. Both of them don't do anything.

I don't know if this caused the problem, but when I was initially installing Ubuntu, the installer crashed when it was installing Grub2. I deleted the partition Ubuntu was on, and reinstalled it and the installation went smoothly. However, I've been getting that error when loading Grub2 ever since.

---

### Post by rpgen on 2011-11-12
I updated my BIOS and everything works fine now. Kinda speechless that this was the problem after 12+ hours of troubleshooting. Thanks anyway for the help.

---

### Post by oldfred on 2011-11-12
Glad you managed to figure out the issue. Sometimes it just takes a little perseverance.

---

