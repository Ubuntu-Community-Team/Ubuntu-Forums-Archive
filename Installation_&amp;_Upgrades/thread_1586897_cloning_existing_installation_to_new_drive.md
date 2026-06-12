---
title: "cloning existing installation to new drive"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by wickyman on 2010-10-02
I would like to replace my old 100gb boot drive in my server with a new SSD...for obvious reasons. 

So what is the best way to clone the existing installation (10.04 desktop) from the old boot drive onto the new SSD? I have read some guides online that suggest using the live CD and various software packages but most of them say it will only work if you are cloning to a disk of the same size or larger, nobody seems to address taking an installation from a larger volume down to a smaller one - in my case a 100gb IDE onto a 30gb SATA SSD.

As this is a datadump, the only drives I really care about are the various 1.0/1.5tb drives that actually store the data, the OS drive contains nothing more than the standard OS, samba/webmin and a few monitoring tools. So I guess it's not the end of the world for me to start fresh and install 10.10 next week, but I would like to know for the sake of this upgrade and future ones if anyone can be of assistance.

basic specs if needed:
Athlon64 X2 3800, 2gb DDR500, Asus A8N SLI Premium (Nforce 4/Silicon Image 3114R RAID controller). OS is on a 100gb IDE (WD1000BB-00C) and I would like to toss it on a Kingston 30gb SSD (SNV125-S2/30).

---

### Post by SaintDanBert on 2010-10-02
Check out Clonezilla [http://clonezilla.org/](http://clonezilla.org/).

~~~ 0;-Dan

---

### Post by wickyman on 2010-10-02
Thanks for the reply Dan, but on the description page it also says: "The destination partition must be equal or larger than the source one."

That's the problem I've seen with most routes so far, my source disk is 100gb and my destination disk is 30gb. Would I be better off shrinking the OS partition down to the smallest possible size so my source partition is less than 30gb?

---

### Post by SaintDanBert on 2010-10-03
There is always a risk if you resize an existing partition.  I can be more help if you provide drive and partition details.  My laptop reports this:
```

[color=green]prompt$[/color]**sudo fdisk -l /dev/sda**  #list partitions

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe11595f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       16700    11261565   12  Compaq diagnostics
/dev/sda3           16701       60801   354241282+   5  Extended
/dev/sda5           52516       60801    66557295    7  HPFS/NTFS
/dev/sda6           16701       24602    63472752   83  Linux
/dev/sda7           24603       24845     1951866   83  Linux
/dev/sda8           24846       26061     9767488+  83  Linux
/dev/sda9           44613       52514    63472783+  83  Linux
/dev/sda10          26062       38809   102398278+  83  Linux
/dev/sda11          38810       39307     4000153+  82  Linux swap / Solaris

Partition table entries are not in disk order
[color=green]prompt$[/color]

```
(The warning tells me that the starting cylinder numbers do not match the partition number order 1-4 then 5-11. Primary partitions are 1-4. Logical partitions are 5-up.)

I've usually done something like the following.
[list]
[*]new **drive** larger than the olde drive regardless of how I plan to partition things.
[*]make a thorough backup of your olde drive.
[*]clone olde drive onto the new drive.  You will have **un-allocated space** on the larger new drive. Your olde drive now becomes a failsafe archive should things go wrong. *I've cloned a dual boot drive. Installed the new drive, and booted without any tinkering sizes.*
[*]I start tinkering with sizes and placement (Hence the fdisk warning) equipped with a failsafe backup.
[/list]

Bonne chance,
~~~ 0;-Dan

---

### Post by wickyman on 2010-10-03
my boot drive details are as follows:

```

Disk /dev/sde: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f8004b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       11661    93666951   83  Linux
/dev/sde2           11662       12161     4016250    5  Extended
/dev/sde5           11662       12161     4016218+  82  Linux swap / Solaris

```

The drive was just formatted using the default settings during installation. I have some spare drives kicking around from the server upgrade that I can use to backup my installation - Most of them are 250/300/320gb drives - so I can safely do that. But it would seem then that the only way to get my existing installation onto the new 30gb SSD is to shrink that partition down....or just start from scratch with the new drive.

---

### Post by SaintDanBert on 2010-10-03
If I read your fdisk report correctly, your "extended partition" is exactly the size of your swap partition a the end of the drive. You've a single large partition for root and everything else.  Is that your intent?

You should be able to tell CloneZilla to take Px from the olde drive and put it onto P1 on this drive ... so long as P1 is larger than Px.

If your olde drive has a separate /home and /var and /boot or whatever, you will need to use **tar** or **cp --archive --verbose** or similar to move that content.

Given your fdisk report, install the new drive, boot the install media, select manual partition, point your install into the new P1 as mount point "/" (root file system), point to your swap partition, and let-her-rip.

One caution, your swap partition size needs to be at least as large as your physical ram.  SLEEP and HIBERNATE need the swap space to do their work. If you are using the 32-bit edition, 4 Gbytes or fewer is your RAM limit.  The 64-bit edition can use much more.  

Bonne chance,
~~~ 0;-Dan

---

