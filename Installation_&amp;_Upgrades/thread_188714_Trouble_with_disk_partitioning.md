---
title: "Trouble with disk partitioning"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by NSIMPSON on 2006-06-04
I'm trying to get the 6.06 LiveCD to install on my old XP box. The hardware is pretty basic by today's standards:

1.9GHz P4 on VIA chipset motherboard
Two IDE drives on the primary IDE channel
DVD & CDRW drives on secondary channel
NVidia Geforce 2 AGP Graphics
Audigy Sound card

In the process of repeated attempts to install I've seen a number of problems:

When booting from liveCD my graphics are sometimes recognized & sometimes not. When they aren't recognized the system boots into a VGA graphics mode, when in this mode it is impossible to install Ubuntu because the install menus don't resize and are too big to be able to reach the buttons at the bottom of the screen. When the system boots from LiveCD correctly everything seems good, graphics & sound work etc. 
[LIST=1]
[*]My first attempt to install to the local hard drive seemed to go well, I partition 50GB of space on the primary hard drive into a "/" partition and a swap partition in addition to the original Windows boot drive and let the install run. When the system rebooted it could find the "/" partition which seems to be problem that a number of people are experiencing.

[*]My second attempt to install had problems partitioning. I was expecting it to let me use the partitions I'd created in the first attempt, and the partition system did see them, but wouldn't let me do anything with them except delete them. So deleted them, they were marked for delete but there didn't seem to be anyway to commit those changes except to the button to the next stage in setup before I'd created the new partitions so I had to then go back and create the new partitions, whereupon the installer crashed. But at least I was back with a 50GB space to try and install a third time...

[*]Third attempt and it's back in partition manager again. Select the unallocated space and create my two partitions again. Now partitions changes are ready, one partition is to formatted with EXT3, the other as linux-swap. PArtition & format appears to work, but then the installer crashed *again.* Maybe the partitions will work for a fourth attempt, can't hurt to try!

[*]Sadly fourth attempt is still a no go, the partitions are there but show up as unknown with no option but to delete them and start all over again.
[/LIST]

---

### Post by christhemonkey on 2006-06-04
Try partitioning before launching the installer by running Gnome Partition Manager from the system menu.
Then running the partitioner and seeing whether they are detected correctly.


Note, make sure to allocate at least 2 GB for / and some room for swap.

---

### Post by rcarring on 2006-06-04
Swap should be set to 2x system ram:

e.g. installed ram 256mb, swap set to 512mb.

---

### Post by NSIMPSON on 2006-06-04
>Swap should be set to 2x system ram:

>e.g. installed ram 256mb, swap set to 512mb.

Really? You mean if I have 512MB of memory I can't have more than 1GB of swap, that seems strange.

---

### Post by NSIMPSON on 2006-06-04
[QUOTE=christhemonkey]Try partitioning before launching the installer by running Gnome Partition Manager from the system menu.
Then running the partitioner and seeing whether they are detected correctly.


Note, make sure to allocate at least 2 GB for / and some room for swap.[/QUOTE]
I'll try that, but on the two occasions now that I've made it sucessfully all the way through the install I just get a system that hangs trying to boot and complains that it can't find the partition.

---

### Post by NSIMPSON on 2006-06-04
[QUOTE=NSIMPSON]I'll try that, but on the two occasions now that I've made it sucessfully all the way through the install I just get a system that hangs trying to boot and complains that it can't find the partition.[/QUOTE]
I'm done with this, not only will Ubuntu not install it's managed to trash my Windows install as well. If this is supposed to be the state of the art for Linux on the PC, then the art if far from perfected!

---

### Post by odysseus.lost on 2006-06-15
Dude first of all chill,

try installing from the alternate version rather than the live-install. Hope you have done text-install before (you know winxp have that)....

Now just one question... I hope you choose to format the partition that you are going to put your / dir at least....

Secondly ubuntu didn't wipe out your winxp partition, you did.... Ubuntu will only change your boot loader... but they will include the xp boot...

---

