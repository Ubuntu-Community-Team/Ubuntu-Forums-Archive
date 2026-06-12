---
title: "Hardware raid not detected while installation"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by dos_killer on 2012-02-27
i have two hard disks on my server and a raid controller...
i have configured it to work as raid 0 for my purpose and during the boot process it shows that it 1 logical volume has been created

now im trying to install ubuntu server 11.10 on it but when it asks to partition disks, it shows the disks separately ? ... 
should they not appear the same ? why is my RAID not detected ??

im using HP Proliant Server ml110 g6...and there is no other OS installed on the system...this is a fresh installation on a new server
details of the raid controller - HP Embedded Smart Array B110i SATA RAID Controller (RAID 0/1/10)

---

### Post by walcab on 2012-03-15
Did you fix this?? Im Having the same problem with ML110 G5.

---

### Post by darkod on 2012-03-15
Have you searched for drivers in case it doesn't recognize the controller?

Also, lots of these controllers these days are not a true hardware raid, but instead a fakeraid. I would also do a research on that topic, and if it shows that it is fakeraid, it's better to use software raid with mdadm.

On top of all that, I have to ask: raid0 for server? Even if it's only a home server, why raid0? If one disk goes, everything is gone.

---

