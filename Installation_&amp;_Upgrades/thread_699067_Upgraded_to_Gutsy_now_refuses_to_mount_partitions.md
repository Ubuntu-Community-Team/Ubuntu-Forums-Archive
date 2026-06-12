---
title: "Upgraded to Gutsy now refuses to mount partitions"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Geryon on 2008-02-17
I recently upgraded to Gutsy and on a fresh reboot none of my other partitions would mount.  Pretty much if I try to mount another partition it tells me the device is already mounted or the mount point is busy.  I can boot the system in to single user mode just fine and have confirmed that the mount point is not the problem.  However, due to a convoluted partition scheme I do not have access to '/usr' at this time so I am severely limited in what I can test.  I have had '/usr' located on a separate partition for some time now, is it a possibility that this needs to be located on the main root partition at not be mounted later?  It didn't used to have to be.  I can also confirm that the other partitions are not mounted but can not confirm why 'mount' is reporting they are 'busy' when I try to mount them.  When I boot up to my previous kernel (2.6.20-22-386) everything comes up fine (except my nVidia drivers, as the version for my current kernel tries to load).  I have also noticed that my standard IDE drives, formally hda and hdd are now recognized as sda, and sdb.  In my grub 'device.map' they are still listed as 'sdX' and I no longer have '/dev/hd*'.  

Any suggestions or ideas would be great appreciated, thank you.

---

### Post by Geryon on 2008-02-18
I managed to resolve this issue by removing the evms (Enteprise Volume Management System) packages.   apt-get --purge remove evms emvs-ncurses did the trick.  I don't fully understand why this fixed it but it did.  I will have to dig deeper in to evms to find out more but everything is up and running fine.

---

