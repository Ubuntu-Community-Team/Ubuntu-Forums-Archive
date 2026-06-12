---
title: "dual boot setup on new pc"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by tanndo on 2011-04-14
Hi,

I'm setting up a new PC with one hard drive: so far I've installed windows XP (need for school) in a 70GB ntfs partition.

Now on my old PC I had a multi boot system working ok:
XP installed first then added other distros e.g. ubuntu in 
extended logical partition. I seem to remember I created these
partitions myself in gparted and then when I installed a distro
from a live cd/dvd I told it to install to one of them e.g. to /dev/sda6. After that everything seems to just work e.g. the grub boot menu was updated so I can choose which os to boot.

Now I had my old PC with ubuntu set up just right with all updates and extra software I've added so I don't want to install from scratch on my new PC.

So my question is can I copy / clone the relevant partitions
from the old PC to the new PC e.g. using clonezilla or gparted 
(I'm thinking I could plug in old sata drive onto new motherboard
to access it).

Not sure how I would setup grub though (manually?)

Any advice / ideas appreciated.

Thanks
T

---

### Post by zvacet on 2011-04-14
You can also try [remastersys]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html") and if you need to reinstall grub follow [this]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD") instructions.

---

### Post by tanndo on 2011-04-17
Thanks,

still a bit confused as I'm not reinstalling grub: it doesn't
exist on my new PC. Anyway done a bit more research and my plan now is:
1. use gparted to create ext4 and swap partition on new drive
2. use clonezilla to copy over ext4 partition from old to new drive
3. install grub to manage the dual boot

Is this likely to work?

Step 3 is the one I'm worried about as
i don't want to mess my windows XP install up and I've never worked with grub before. Perhaps I will back
XP up with clonezilla before I start experimenting!

Also read about possible issues with uuids. Could this affect me? If anyone has any other good links / tutorials about grub that may help me before I give it a whirl? 
Cheers
T

---

