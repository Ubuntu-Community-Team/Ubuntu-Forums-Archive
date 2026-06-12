---
title: "Grub Install Error"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by 64mgb on 2006-11-01
I'm trying to do a fresh install of Edgy (brand new hard disk) and every time it gets to the end of the install process where it tries to install Grub on hd0 it fails.  I've installed Dapper on several machines and had no problems.  Any ideas?

I am trying to create 4 partitions...one is a swap partition, one for the root, one for home and a large one for MythTV.  When it asks where to install Grub I leave it at (hd0).  Should I be changing it to (hd0,1) (the first partition is for root).

Thanks,
Rich

---

### Post by thoolihan on 2006-11-01
hd0 installs it to the master boot record which is probably where you want it.  You could try running it by hand.

open a terminal
#assuming root is hda2 and is mounted on /mnt/root
chroot /mnt/root 
sudo grub
>root (hd0,0)

I would double check all that in the docs [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by 64mgb on 2006-11-01
> **thoolihan said:**
> hd0 installs it to the master boot record which is probably where you want it.  You could try running it by hand.

open a terminal
#assuming root is hda2 and is mounted on /mnt/root
chroot /mnt/root 
sudo grub
>root (hd0,0)

I would double check all that in the docs [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
Thanks thoolihan - I'll see if I can do that but I suspect not, because the system never really finishes installing, so I don't think I can start a terminal session.  The only way I can boot at all is with the installation CD.

I'll take a look through the docs you referenced.

Thanks,
Rich

---

### Post by thoolihan on 2006-11-01
You can run those commands from the install cd.  I'm including the chroot command in order to make the commands run on the partially installed system.

---

### Post by 64mgb on 2006-11-01
I think I may have found the problem...I hadn't created a disk label.  The install is running now, so I'll let you know later if that solved the problem.

Thanks,
Rich

---

### Post by 64mgb on 2006-11-01
Yep...that was it...I'm up and running!

Rich

---

