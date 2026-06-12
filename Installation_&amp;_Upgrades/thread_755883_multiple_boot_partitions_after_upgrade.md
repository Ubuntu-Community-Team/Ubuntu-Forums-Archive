---
title: "multiple boot partitions after upgrade?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by maddanio on 2008-04-15
Hi,

It seems that after the last dist upgrade (always bleeding edge :)) I have two boot partitions: one contains all the kernels before the upgrade and is seen at boot time, and  another is used by synaptic to install new kernels. Now ubuntu is using the devmapper, which blows my head. Basically I miss the paradigm of mountpoints (i.e. where in my fs can I find the data on partition x?). 

fdisk -ls:

/dev/sda1               1       19452   156248158+   5  Erweiterte
/dev/sda5   *           1          31      248944+  83  Linux
/dev/sda6              32       19452   155999151   8e  Linux LVM


Ubuntu-swap_1	(254, 5)
Ubuntu-root	(254, 4)
sda6	(254, 0)
lvm2|Ubuntu|swap_1	(254, 2)
lvm2|Ubuntu|root	(254, 1)


there used to be an sda5 there also, but I removed it in an attempt to manually mount the supposed "real" boot partition, which failed. Even after the removal can I see the new kernels under /boot, strengthening my suspicion that /boot is not at sda5, but sda5 is loaded at boot time.

Has anyone had this, or can anyone tell me how to fix this? I am kinda lost here...:confused:

---

### Post by dstew on 2008-04-15
> Now ubuntu is using the devmapper, which blows my head.From your fdisk output, you only have logical volumes, so devmapper will be needed. Your only primary partition is sda1, which seems to be an extended partition. Then you have logical partitions sda5 and, sda6, which seems to be broken up into several logical volumes. It is a strange setup. What are you trying to do? You can boot a live CD, mount /dev/sda5, and see what is in there.

---

### Post by maddanio on 2008-04-16
Hi,

The setup came by autmatically, I never made it like that. I know what is on sda5: the old boot stuff, i.e. all the kernels before the upgrade, which grub feeds off at boot time (I did check it with a live cd before).

How can I fix this "strange" setup?

What I am "trying to do" is simply reconcile the boot partition grub uses at boot time with the one synaptic installs all the new kernels to. Because right now I refrain from updating because otherwise my actual kernel version will digress further and further from what synaptic thinks it is.

---

