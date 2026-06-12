---
title: "Persistent usb live Linux larger than 4GBs with Ubuntu doesn't recognize casper-rw"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by blau2 on 2016-01-11
A persistent usb live Linux larger than 4GBs with Ubuntu doesn't recognize casper-rw partition. 

I proceeded to configure boot (fat32, 2GB) and casper-rw (ext2, 30GB) partitions on the pendrive. Then I install with Netbootin the iso image checking the persistence option. Then I delete the casper-rw file, so that the OS recognizes the casper-rw 30GBs partition as the persistent space, but this doesn't happen. The system boots without any issue, but the disk manager doesn't show the 30GBs partition as a part of the OS, but it just recognizes the 2GBs boot partition. As a proof, a 2.5GBs file download ends up in a "insufficient space" alert. I even did a chmod to change the owner of the casper-rw partition from root to Ubuntu, with the same unsuccessful result. Any hint of what might be happening? Any solution?

---

### Post by ubfan1 on 2016-01-11
What version of Ubuntu?  Is this a UEFI machine?  Bug 1159016 fixed by 15.10 I think.

---

### Post by blau2 on 2016-01-11
Sorry, I missed this important data: my PC is a UEFI machine, and I'm currently installing Ubuntu 15.10. Any solution? Thx.

---

### Post by ubfan1 on 2016-01-11
Not sure unetbootin got the fix.  Look at file (partition 1) /EFI/ubuntu/grub.cfg and see if the word "persistent" got added to the kernel boot line.  Add it yourself if it's missing.

---

### Post by sudodus on 2016-01-12
Try mkusb, it can create persistent live drives with a casper-rw partition automatically. See these links

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

