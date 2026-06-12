---
title: "Are GPT and LVM a suitable for this installation?"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by El Potro on 2012-07-18
Hello everybody!

I just bough a new 2 TB hard disk and I'm wondering, would it be a very wild idea to use GPT instead of MBR? Is there any real advantage? (my BIOS is a regular one, not a UEFI)

And the second part is that I'd like to try some distributions now that I have plenty of space. (I use Ubuntu). Is using LVM a good idea for this? I read that using LVM you can resize your partitions on the fly, and I want to know more about this.

Let's suppose I use the following partitioning method with the old MBR partition table:

```

sda1   ext4      /           30 GB
sda2   ext4      /home     1925 GB

```

How would that be with GPT + LVM?

Would it be possible to resize sda2 whenever I want (even if it has many GB in use but a few unused) to create other partitions that I'd use with other distributions (Arch, Gentoo, Debian, Ututo)? And if I'm tired of them, give the GBs back to sda2?

Any advice and suggestion is accepted, thank you very much in advance!

---

### Post by darkod on 2012-07-18
First of all, don't forget that with gpt you need the small bios_grub partition so that grub2 can install properly. It shouldn't have any filesystem, so I find it easiest to create it with parted (which means you need to do it from live mode in advance).

To create new blank gpt table on the new disk, and create this partition, it would be like:
```
sudo parted /dev/sda
unit MiB
mklabel gpt
mkpart GRUB 1 2
set 1 bios_grub on
quit
```

That should change the units to MiB, make a new gpt table, make a partition named GRUB starting at 1MiB and ending at 2MiB, and set the bios_grub flag on it.

If you want to, you can continue creating partitions with parted. For LVM you can use the lvm flag.
It would be better to create /boot partition outisde the LVM although it seems it's no longer necessary (with earlier versions it was necessary for LVM to work).

So, except for the small bios_grub partition and the /boot partition, you can allocate the rest of the disk for the LVM.
Then you will have the flexibility to resize the LVs. Not sure how it would work for other distros and whether some of them would need separate /boot too, because you can't use the same /boot partition across distros.

---

### Post by El Potro on 2012-07-22
Hola **darkod**, thank you for your help. Anyway I'm still not sure what to choose.

What would be the benefits of using GPT over MBR on this < 2 TB disk? Is there any real advantage? Remember, I don't know either if I need to use LVM.

> It would be better to create /boot partition outside the LVM although it seems it's no longer necessary (with earlier versions it was necessary for LVM to work).


Do I have to create a single /boot partition for all the distributions (let's say I want to install Ubuntu, Arch and Gentoo) or I have to create a /boot partition for each distribution? Should it be inside or outside the LVM partition?

This is all very hard to guess for me, perhaps somebody with experience could advice.

Thank you

---

### Post by darkod on 2012-07-22
As far as I know, the 2TB disks are the maximum you can use with MBR (msdos) table. So, you could use MBR.

For the /boot partition, you can't share it between distributions, they all have to have separate, or none (you can have /boot for some, and not for others).

I don't know how it would work with more linux systems. But you can give it a shot.

Another option is to use small 15-20GB root partitions for all systems, and then have one large partition for data that all of them can read.

---

### Post by oldfred on 2012-07-22
I am now using gpt for all new drives, but the one I bought a couple of years ago was just before I started using gpt and is still MBR. 

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Only if you ever want Windows on the drive would I still do MBR, but the advantages of gpt are not huge. After converting drives I really do not notice any difference. I did have to create the bios_grub partition. And on my newest drive I also added the efi partition as the first as it is difficult to add a first partition later and that drive may get moved to a new system that will be UEFI.

When I got my new Large (640GB) drive a couple of years ago, I allocated a couple of data partitions and installed Ubuntu in 25GB and let the rest unallocated. I since kept installing new versions of Ubuntu and each release for testing in 25GB. I still have some space but soon will have to start deleting some old ones.

I do not use LVM. It adds a level of complexity for the flexibility, but some have posted that if you plan partitions in advance there is little practical advantage to LVM. Others seem to use it a lot.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

