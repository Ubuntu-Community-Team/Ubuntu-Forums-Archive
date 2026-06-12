---
title: "Ubuntu's GRUB"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2006-12-31
After installing Ubuntu it's GRUB entries consist of 2 Ubuntu ones, memtest86 and Windows XP. This would be fine aside from the fact I also have Fedora Core 6 installed on this machine. There is no entry for it in Ubuntu's GRUB. I know Fedora Core is still there because I used the "install in largest continuous free space" and Fedora's LVM partition is still on my drive.

Before I blame Ubuntu for this disappearance, as it very well might not be Ubuntu's fault ( it could be PartitionMagic's ), has anyone else had "vanishing" OS's after installing Ubuntu ( meaning from GRUB )?

---

### Post by bulldog on 2006-12-31
It's not 'vanished' if you have set up the partitions the right way.
You can add the entry for Fedora manually into GRUB,take a look at the ubuntu entry and make a similar one for the fedora using the right vmlinuz and set the partitions as they should be.

Your two ubuntu's aren't quite the same,one is for recovery mode.
It's not a good idea to use partition magic to partition your disk.
Use gparted instead or rather the gparted live cd,which have a GUI like PM.
It's known PM can't deal very well with Linux partitions and often messes things up.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Installing a new OS is something to do very carefully,certainly when you have to resize partitions with data on it.
Some reading and understanding what you're about to do is a must,otherwise you can lose your data when you make a little mistake

---

### Post by Wight_Rhino on 2006-12-31
Have you tried: 

> $ sudo update-grub

sometimes catches it.

---

