---
title: "Accidentally deleted partition table on my lvm physical volume."
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by HighInBC on 2010-07-18
I was trying to remove the physical volume from an old drive. So I opened gparted and told it to rewrite the partition table. The only problem is I targeted the wrong volume, I wiped the partition table on my 4tb raid5 array

This 4tb array has everything! All my movies, tv shows, music. The only things I have backup up off site are my smaller files like documents. I was about to lose my whole media collection.

I did some research and found a solution that I will post here in the hopes that someone will google "I deleted the partition table on my lvm" and be find the solution.

You should find in your filesystem a /etc/lvm/backup folder. LVM puts a copy of the crucial lvm information there every time you change the the volume group.

In this folder you will find a file for each volume group. In this file you will find the uuid for all of the physical volumes that make up that group.

The first step is to recreate each physical volume with their original uuids. In my case I had only 1 physical volume, which was my raid5 array. My recreation command looked like this:

pvcreate --uuid cLrY02-zrVi-D0Vi-cIPB-6fF5-ed0c-XFF0os /dev/md0

Now I have a physical volume with the same uuid it had before. It is essential that you correctly match up the uuids with the correct physical deviecs.

The recreated pv is empty, the volume group needs to be recovered. This is done by using a special tool and the backup file. For me the command looked like this:

vgcfgrestore --file /etc/lvm/backup/raid5 raid5

This tells it to recreate the volume group using the information in the backup file. The backup files looks for the uuid of the PV, which now matches the correct volume. The coordinates in the backup file match up to the data on the array an suddenly everything is back!

When I deleted my LVM partition table I did not damage any of the actual volumes on the volume group, I just wiped out the table of contents. The backup file had the information needed to rewrite this table of contents.

I was worried for a while, but everything is fine now.

---

### Post by dannytherocker on 2010-12-26
I do appreciate your post: had your same problem and got fixed thanks to you!!!!
This is the power of community
Thanks again.
Bye

---

### Post by littlebeaver on 2012-06-23
Thank you - this just saved me a lot of angst too. 

I also had to run the following commands to get the data on the volume group accessible again:


# vgchange -a y {activates the volume}

# mount <mount point> {you should be able to get this from /etc/fstab}


Thanks again.

---

