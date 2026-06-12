---
title: "mdadm Troubles After Upgrade"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by hostile on 2006-07-23
Hello,

After an otherwise smooth upgrade from Breezy to Dapper on one of my servers, mdadm has taken a left turn on me.

Here is my mdadm.conf:

DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b044d4e3:770c1103:b887fe3f:26db27c0 devices=/dev/hde5,/dev/hdg5
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=4858ee49:5d90aa2b:55c2b58b:a8748d65 devices=/dev/sda5,/dev/sdb5

Here are the lines in question in my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

/dev/md0        /home           ext3    defaults        0       2

/dev/md1        /srv/ftp        ext3    defaults        0       2



The problem is that for some reason, /home (/dev/md0) is being mounted on /srv/ftp and /srv/ftp (/dev/md1) is being mounted as /home!

So, for some reason, after the upgrade, my RAID devices are being mounted on their opposite mount points in the file system.

I know the easy way to fix this would be to simply move one to the other in my fstab, but this is a kludge, considering how everything is clearly, and accurately defined.

Any insight would be greatly appreciated.

---

### Post by ZoltanPatay on 2006-07-28
One of the raid array is on PATA (Paralell ATA) the other array is on SATA (Serial ATA).

In the old kernel the ATA driver got loaded first now the SATA does (this is why the RAID gets initiated first on the SATA now).

Mos likelly cause is the order of the PCI card initiation got switched in some kernel version. It used to be from AGP down, now it is the other way around. (This was done by the kernel developers, I remember reading some posting from Linus explaining why it was better)

You are not the only one experiencing this. The other effect it has is if you have several network cards, and you are running a router, the cards get numbered the other way around.

When you run 'lspci' under the different kernels it will show a different order, that is old kernel ATA before SATA, nwe kernel SATA before ATA.

Try to add the 'try ide=reverse' boot parameter in your grub after the kernel (to the end after 'ro quiet splash').

Besides the PCI initization loading one module before the other (in case they are not compiled into the kernel) will also make sure that certain order is followed. However this would include looking into the kernel config and see that the said IDE and SATA drivers are not compiled in, then edit the initrd config files to load the modules in the correct order, then recreate the initrd image.

Much simpler is to edit the fstab, but the reason for the switch up of ATA/SATA order is given above.

---

