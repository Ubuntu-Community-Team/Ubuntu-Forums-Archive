---
title: "Vista Overwrites MBR or partition table"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by jdjacobs on 2007-08-11
I have a Asus G1s which comes factory installed with approx. 8 gig partition of a Vista restore image and the remainder of the 160 gig hard disk partitioned for the Vista boot.  I reduced the Vista partition to 60 gig with the Vista partition manager.  I then used the alternate Fiesty disk to install a 15 gig /, 15 gig /home, and 500 meg /boot logical partitions.

Every thing works fine until after the first reboot from Vista.  The computer shows look for "Grub Loading stage1.5" and then reboots.  I can rewrite the master boot record and the partition table with the alternate Fiesty disk.  But once again when I reboot after being in windows I do not see the Grub menu.

Any help how to prevent Vista from apparently overwriting the master boot record or the partition table.

Regards,

---

### Post by Pumalite on 2007-08-11
I don't know much about Vista, but I can contribute with this: [http://neosmart.net/blog/2006/easybcd-15-multidual-boot-vista-linux-mac-os-x-bsd/](http://neosmart.net/blog/2006/easybcd-15-multidual-boot-vista-linux-mac-os-x-bsd/)
[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)
You could also use Super Grub to investigate the situation and make the changes necessary: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
You could also use a Knoppix Live CD and see if you can post here: cat /boot/grub/menu.lst
And sudo fdisk -l (small)
That would help to help you.
Knoppix: [http://www.knoppix.org/](http://www.knoppix.org/)

---

### Post by jdjacobs on 2007-08-11
Thanks for the suggestions.  I will give them a try and report back.

Regards,

---

### Post by Computer Guru on 2007-08-12
Here's the full documentation/how-to link for getting EasyBCD to boot linux: [http://neosmart.net/wiki/dislay/EBCD/Linux](http://neosmart.net/wiki/dislay/EBCD/Linux)

---

### Post by jdjacobs on 2007-08-12
Thank you for the lead.  It looks terrific.  I will report back on my success (or failure).

Regards,

---

