---
title: "How do i setup raid (need help on config)"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Ace2016 on 2008-04-04
i have a laptop with 2 hard drives

problem is that i wan to go from 120GB (non raid) to a 120GB and 250GB setup with 120GB from each in raid1. My plan is to setup a raid1 on the 250GB hard disk of 120GB then use the parted livecd to copy the 120GB hard drive to the 120GB raid1 partition, then wipe the 120GB hard disk and copy the raid array over from the 250GB hard disk to the 120GB hard disk. so i should end up with 120GB raid1 on each disk, then free space on the 250GB hard disk for vista to be restored onto (i can sort out the problems vista will cause its fine, its partition is being coppied directly from hard disk 3)

Start:

120GB: [XFS /home and /] [swap]
120GB: [Vista] [Recovery Partition]
250GB: empty

Finish:

120GB:  [120GB Raid1: XFS /home and / ]
250GB:  [ Vista ] [Recovery Partition] [Swap] [120GB Raid1: XFS /home and / ]

120GB: unused

So my question is, how do i make a raid1 array with just 1 disk? what livecd do i need for that? i use parted magic for most of my partition copying work, but i've never setup a raid this way

---

### Post by stefangr1 on 2008-04-04
A good tutorial for how to set up raid 1 is here: [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

You can't make a raid 1 array with only one disk, you can however format the remaining space as a normal ext3 partition.

However, normally 2 exact similar disks are used for raid 1, I'm not sure if it works the way you want. It could slowdown performance, if one disk is faster than the other. I'm not sure if it could also have more harmful side effects.

---

### Post by Ace2016 on 2008-04-04
> **stefangr1 said:**
> A good tutorial for how to set up raid 1 is here: [http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

You can't make a raid 1 array with only one disk, you can however format the remaining space as a normal ext3 partition.

However, normally 2 exact similar disks are used for raid 1, I'm not sure if it works the way you want. It could slowdown performance, if one disk is faster than the other. I'm not sure if it could also have more harmful side effects.

Well the whole reason for getting the 250GB disk was to do a raid array, i've setup a raid on my desktop but for my laptop i need to make a raid with 1 disk somehow

---

