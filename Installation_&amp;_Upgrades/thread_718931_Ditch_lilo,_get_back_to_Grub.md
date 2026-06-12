---
title: "Ditch lilo, get back to Grub?"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by mjj808 on 2008-03-08
Hello there!

I am trying to do a clean install of Ubuntu and I am having a bootloader problem.

For whatever reason, I was not able to install Grub the first time I installed Ubuntu. I was using Lilo instead. I think this had something to do with the filesystems of the existing partitions. Windows was already on there and I just put Ubuntu on a new partition.

Now I am ready to start fresh. I formatted the partitions and installed Ubuntu, using the whole disk, totally wiping out the Windows partitions.

But it seems that the computer is still using Lilo (probably the Lilo I installed with the last go-round). During the new, fresh install, it does not seem to go through a bootloader step.

Is there any way I can install Grub and get rid of the old boot section?

Please advise!

Thank you!

Matt

---

### Post by Pumalite on 2008-03-08
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete anything left in your hard drive (if any). Make new large partition of your whole hard drive and format ext3. Now install Ubuntu.

---

