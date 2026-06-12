---
title: "problems at instaling ubu 8.04 - partition section"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by pixie1 on 2008-06-09
hi
I tried to install ubuntu 8.04 as the only OP sytem. Everything went fine until step 4 - partitioning. I can't make any, no matter where I click.Nothing happens. I can't go to the next step of installation.
Now I am on live option. Partition Editor is not working- not yet implemented. Please help
(I have pent, 512 RAM, 1,3 Ghz)

---

### Post by Rallg on 2008-06-09
My guess (it is only a guess) is that you are trying to install Ubuntu within a non-Linux file system. So, let's start from the beginning:

You say that you want Ubuntu as your only operating system. So, you are willing to erase anything that is already on your hard drive? If so:

Use the live CD. Do not install yet. Run Ubuntu live. Launch the partition editor GParted. If the partition editor completely fails to launch or refuses to show you anything about your hard drive, then you may first need to wipe the drive by some other means. (If this is the case, come back here for further advice from those who know how to wipe a drive. However, I am reluctant to show the code, since it is dangerous for others to use.)

But if GParted launches and can show you something useful, even if it says "not implemented" for part of your hard drive, then you might be OK. In this case, use GParted to delete any existing partition. That will change the partition(s) to unallocated space, and will make the "not implemented" problem go away.

Then, you can use GParted to build new partitions. First, select all available unallocated space, and format it as a primary partition, of type ext3. You may also need to mark it with the "boot" flag (not sure if this is essential if you don't have Windows).

After that, shrink the primary partition, and create an extended partition in the freed space. How large is your hard drive? If it is very small by today's standards (say, 10Gb) then the extended partition should be only 1Gb (twice the size of your RAM). Format it to linux-swap type.

If your hard drive is much larger (say, 20Gb or more) then you might want to consider creating a partition where you can install a future version of Ubuntu (or any Linux) for testing purposes. Typically 6Gb (type ext3) is more than adequate for testing. You still need the 1Gb linux-swap, which would be common to several Linux partitions. In summary, with a sufficiently large hard drive you would have most of it formatted as primary ext3, plus an extended partition with 6Gb as ext3 and 1Gb as linux-swap.

So far, so good? If so, you are ready to install Ubuntu.

Launch the installer. Put Ubuntu on the primary ext3 partition. Be sure to use it as "/" with format ext3. Also be sure to use the linux-swap partition as swap. If you created an extra ext3 partition, it is not used here (reserved for possible future use).

In your case, the installer will automatically choose to install the boot loader in the correct location, (hd0,0).

---

### Post by zvacet on 2008-06-09
Try alternate CD.Use manual way to be able to make separate home partition.It should look like this

1. root = 10GB                                   mountpoint /
2. swap = _2xram
3. home = rest of free space                     mountpoint /home

When you came to the partition stage make partitions in this order:root,home,swap and put swap on the end of disc.

---

### Post by pixie1 on 2008-06-09
yes, I have windows on. forgot to mention, sorry.
yes, no problem at deleting everything. I made back-ups.
Gparted is not working. all I can click is: refresh devices, show features and quit. help is not working either.
In win, I have on c: about 40 or 50 GB disc, free is if I remember ok, about 14 gb free, d: 100 GB size
I don't know hot to use gparted if I can't click anything.

---

### Post by pixie1 on 2008-06-09
> **zvacet said:**
> Try alternate CD.Use manual way to be able to make separate home partition.It should look like this

1. root = 10GB                                   mountpoint /
2. swap = _2xram
3. home = rest of free space                     mountpoint /home

When you came to the partition stage make partitions in this order:root,home,swap and put swap on the end of disc.
so I should download ubuntu 8.04 alternative? I have desktop version.

sorry to ask so stupid questions, but I am confused.

---

### Post by zvacet on 2008-06-09
Download [Gparted live CD.]("http://gparted.sourceforge.net/")With it you can keep windows if you want and format rest as ext3 which is Ubuntu default filesystem format,or you can delete everything and leave it as unallocated space.You will make partitions with Ubuntu live CD.

---

