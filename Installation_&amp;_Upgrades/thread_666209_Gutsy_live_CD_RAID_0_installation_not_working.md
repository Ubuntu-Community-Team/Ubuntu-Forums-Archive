---
title: "Gutsy live CD RAID 0 installation not working"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by jolx on 2008-01-13
Hi, I've been using ubuntu for about 2 months now and i want to install it using the RAID 0 striping that is on the motherboard (gigabyte GA-P35-DS3P rev. 1.1). Does anyone know an *easy* way of doing this?? i've already had a look at some tutorials but none of them are working.

I'm using: C2D E6750
Gigabyte GA-P35-DS3P (rev 1.1)
2 x Seagate Barracuda 7200.10 320GB SATA2
2GB Corsair 800MHz DDR2 RAM

---

### Post by jolx on 2008-01-17
Ok, its working now, i just had to use the alternate cd. easy. :)

---

### Post by trancephorm on 2008-01-26
You attached the disks to violet or orange sata connectors... Using which controller? And while installing, did you see just one logic disk (RAID set)?

---

### Post by jolx on 2008-01-29
I have my drives connected to the orange ports (Intel ICH9R), but i dont have the RAID option turned on in the BIOS settings. So im not absolutely sure its working.

Anyways wat i did was, i used the alternate cd and when it came the partitioning i chose the manual option, set up partitions for /boot & swap on (my) hda, then i created a 4 GB partition and instead of choosing ext3, etc..., i chose the 'physical volume for raid' option. then i did the same but i used the rest of the drive. now with my other drive (i only have 2), i set up a 4 GB raid  and then the same for the rest of the drive. then i went up to configure raid devices, or something similar, make raid array, selected the two 4 GB partitions. then i did it again but with the other two.

But im not sure about it and im thinking i might try lvm

---

### Post by trancephorm on 2008-01-29
I don't think you used that "fake-raid" available on the board. Finally I made software raid, which by the way, as far as I know, is consuming the same amount of cpu, as a fake on board raid...

---

