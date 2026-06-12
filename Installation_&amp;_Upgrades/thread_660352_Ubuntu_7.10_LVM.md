---
title: "Ubuntu 7.10 LVM"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by jrlrocks on 2008-01-06
HI There!

New to Ubuntu - Linux but understand LVM, Am a whiz at windows. 

I have 2X 37GB raptor drives that I threw into a AMD 3800 PC. 1GB ram.
Want to learn Ubuntu. For whatever reason. When I setup the hardware RAID on my Asus mobo ubuntu still see's the 2 drives. I wanted to set up RAID zero just to make this system as fast as possible and as in windoz would look like 1 drive to the OS.

OK - so I disabled hardware RAID and installed /root 6GB on SDA and SWAP on the second drive SDB to be 2GB (Probably to big but I'm not bother about the space.) Rather than have 2 partitions with +/-30GB in each I thought LVM may be a solution to create 1 +/- 50GB partition and span it over the balance of both drives.

I utilize another computer on my network that has redundant storage. so I'm not bothered about backup.

If you can let me know what to do. GREAT! If not it would be awesome if you could point me in the right direction as I've spent the best part of 2 hours researching and I'm not sure this is even worth it. But am interested in learning - 

Thanks,
J

---

### Post by jrlrocks on 2008-01-07
Bump - anyone?

---

### Post by bigredradio on 2008-03-06
If you are still interested in LVM, then I would suggest creating a partition on each of the remaining disks. Then use the following commands:

**pvcreate** on partition 1 and 2
**vgcreate **using partition 1 and 2
Then you can slice up the VG using the **lvcreate **command
Finally put a filesystem on the LV using **mkfs** command.

You can use the man (manual) pages for each of these commands to get the exact syntax.

ex. man pvcreate

If the LVM tools do not appear to be on your system, you can get them with:

# apt-get installl lvm2 lvm-common

BTW, if you are unsure how to create partitions on the free space, then look at the fdisk command.

If you google for "LVM2 How-To" you will also get a lot of information on LVM for linux.

---

### Post by zvacet on 2008-03-06
Maybe [this](https://help.ubuntu.com/community/Installation/LVMOnRaid) can help you.

---

