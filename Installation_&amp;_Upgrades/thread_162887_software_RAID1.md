---
title: "software RAID1?"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by greyeye on 2006-04-19
Ive setup the vmware machine for test for RAID configuration on linux
RAID1 seems to work ok but I wanted to test recovery of RAID1.

well if i remove the disk IDE0:0 and try to boot from IDE:0:1, it doesnt boot at all. Just sitting at the black screen.
Removing IDE0:1 and booting works perfectly and shows that RAID1 is running with only 1 disk.

its Ubuntu 5.10 and /dev/hda /dev/hdb on the RAID1 for / and swap (two RAID1 partition)

any idea what I may have setup incorrectly?
thank you

---

### Post by greyeye on 2006-04-19
[http://fedoranews.org/mediawiki/index.php/How_to_setup_and_manage_your_disk_software_mirroring](http://fedoranews.org/mediawiki/index.php/How_to_setup_and_manage_your_disk_software_mirroring)

ok found the problem.
GRUB need to be installed on the 2nd IDE drive. manually!

see above, but actual command i used was
grub>root (hd1,4)
grub>setup (hd1)
grub>quit

yay, simple fix. =)

---

