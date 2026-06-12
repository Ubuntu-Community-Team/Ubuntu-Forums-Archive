---
title: "LVM during 14.04 Install - can set up only 1 VG...?"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by uzee007 on 2014-08-25
Hi All,
I'm installing a new VM with Ubuntu server 14.04. When I get to the partitioning, based on this: [https://help.ubuntu.com/10.04/serverguide/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/advanced-installation.html), I set up /boot and swap space. Then I wanted to set up the remaining disk with LVM including the root partition.
The problem is when I select the free space within the installer and select 'configure lvm' it asks for a vg name which I provide and then asks to select a partition and rightly shows the 3 partitions, I choose the available partition (leaving the ones for /boot and swap) and then it created the VG on the entire partition. What I would like is to be able to specify multiple VGs instead of just one. But at installation time it is not giving me an option to create more than one VG..??? am I doing something wrong? I really want to have my root partition under lvm

Thanks

---

### Post by steeldriver on 2014-08-25
Your root filesystem (i.e. / ) will end up as a single VG, which will  contain everything except for /boot which will be on a separate  traditional partition (and swap of course)

You can combine multiple physical volumes (read: partitions) into a single volume group, but as far as I know you can't share a single physical volume between multiple volume groups - you would need to split the free space into separate partitions first and assign each PV (partition) to a different VG

Of course you can have multiple *logical volumes* within a single VG

---

### Post by uzee007 on 2014-08-25
> **steeldriver said:**
> Your root filesystem (i.e. / ) will end up as a single VG, which will  contain everything except for /boot which will be on a separate  traditional partition (and swap of course)

You can combine multiple physical volumes (read: partitions) into a single volume group, but as far as I know you can't share a single physical volume between multiple volume groups - you would need to split the free space into separate partitions first and assign each PV (partition) to a different VG

Of course you can have multiple *logical volumes* within a single VG

hrmm... thanks for replying steeldriver. I'm however confused. I have configured LVM on a running system in the past a few times and don't recall that I wasn't able to do what I asked. For example, say I have a running machine and I add a 50 GB hdd, then I rescan the scsi bus so that the disk appears in fdisk. After that I can run pvcreate, vgcreate, etc. and in vgcreate I could specify the size of the VG and the remaining disk was available so I could create another VG. I will try to do this on a test system to make sure...

Please let me know if I'm missing something...

Thanks

---

### Post by steeldriver on 2014-08-25
... it sounds like you know more about it than me - I've only done a couple of LVM based installs

---

