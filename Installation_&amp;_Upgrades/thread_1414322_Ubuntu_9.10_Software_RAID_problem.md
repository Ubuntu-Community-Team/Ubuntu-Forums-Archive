---
title: "Ubuntu 9.10 Software RAID problem"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by diosney on 2010-02-23
Hi!

    I recently installed Ubuntu Server 9.10 with RAID software partitions and every works fine, but when I rebooted, the system drop me in a BusyBox shell(initfrms) with a "the disk with UUID="XXXXXXXXXX dont exist" ...etc..." message.

    Searching in the forums I find a solution: 

1-Type "exit" at the Busybox shell to continue booting.
2-Edite the "/etc/default/grub" file and adding "rootdelay=90"before the "quiet splash" parameter.
3-Run the "sudo update-grub" command to update the "/boot/grub.cfg" file.

    After that the system booted fine.

    Someone can explain me why this solved the problem?

Thanks in advance!

---

### Post by darkod on 2010-02-23
Even if you don't use raid, sometimes it takes longer for grub to find the root partition. You just added a delay to give it more time to find it. And it worked fine, because now it can locate it within the timeframe and starts up OK.

---

### Post by diosney on 2010-02-23
Hi Darkod!!
   That sounds pretty much convincing to me :D.

   Thanks a lot.

---

