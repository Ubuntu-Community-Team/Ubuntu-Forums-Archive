---
title: "Dual boot downgrade"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by PartsMan on 2009-12-01
I recently got an old dell 8100 Laptop. (PIIIm 1khz 512mg) It has XP and I need to keep it for work. 
I also installed UNR 9.10. It is a little big and runs slow on this machine. How can I remove/replace UNR 9.10 WITHOUT MESSING UP XP. XP disc is MIA.

---

### Post by oldfred on 2009-12-01
First reinstall windows boot to the MBR. Since it is old windows, supergrub or testdisk (in most repair CDs) will fix the MBR. After you get windows working you can reformat the Ubuntu partition to NTFS and windows then can use it. You could expand the windows partition but that is higher risk. Any change to partitions we recommend you have backup just in case.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB).
[http://www.supergrubdisk.org/wiki/SGD_Howto_make](http://www.supergrubdisk.org/wiki/SGD_Howto_make)

---

### Post by audiomick on 2009-12-01
you could try Xubuntu instead of UNR. It would be a shame to give up on Ubuntu :p

---

### Post by PartsMan on 2009-12-01
> **audiomick said:**
> you could try Xubuntu instead of UNR. It would be a shame to give up on Ubuntu :p

Would I still have to get rid of what I have first. I am already tired of XP again.

---

### Post by PartsMan on 2009-12-03
Never mind :D . I am keeping UNR 9.10.

Backed the resolution down and it runs very smooth!

---

