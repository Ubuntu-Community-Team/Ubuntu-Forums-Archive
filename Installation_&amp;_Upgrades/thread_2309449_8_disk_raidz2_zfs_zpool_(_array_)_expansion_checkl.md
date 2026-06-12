---
title: "8 disk raidz2 zfs zpool ( array ) expansion checklist check ( wanted ) pls"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by elmatthijs on 2016-01-10
LS,
I have an 8 disk server, consisting of 8 2TB Western Digital RE4-GP disks.
It is configured in 1 raidz2 zpool under Kubuntu, with the zfs file system.
If I understand correctly, zfs should be able to run on a number of disks that are different sizes, and still be able to maintain the raidz2 data security.

Is this correct ?
Can I just replace 1 2TB WD RE4-GP with 1 WD 6TB Red ?

If so, pls continue reading, to check if my MO is correct, or if I am skipping an important step somewhere.
If not, pls email me, to tell me so, and there is no need to read the last part of the text.

Thanx,
lucas.

( Amsterdam, the NL )


***

My plan:

- create as much free space on the zpool as possible by copying data to another zpool ( to reduce repair and resilver times and perhaps the process would work more smoothly when the   zpool is not maxed out )
- scrub the zpool
- shut down server
- remove 1 2TB disk and put it in the eSATA diskdock
- put 1 6TB disk in the empty drive bay
- start the server up
- enter the RAID card's BIOS
- attach the 6TB disk to the "array"
- reboot server
- under Kubuntu check the status of the zpool ( which should show up a degraded )
- add the 6TB to the zpool
- resilver the zpool
- scrub the zpool

This should work, but the data on the 6TB needs to be recalculated; which wil take some time...
I am not sure how, but if I can attach the mounted  "old" 2TB disk via eSATA, that data could be copied, and thus resilvering would go much faster.

And I am not sure how to expand the zpool so it will use the x-tra +/- 4TB...

I might want to redo this trick in a few months time, once I have saved enough money to replace a 2nd 2TB with a 6TB.

I am relatively new to Lunix, so pls "be gentle with me" ;-)


All help is welcome !!!


Thanx,
lucas.

---

### Post by andiz on 2016-01-12
Hello Lucas,
joined the forums to answer your questions.

1. You may create a zfs-vdev containing different sized disks, but the total usable space depends on the size of the smallest disk in the array. So in case of replacing a 2TB HDD against a 6TB HDD in a RAID-Z2 vdev, this 6TB HDD will behave like a 2TB HDD until you have exchanged all other 2TB HDDs against 6TB drives. 

2. Caution: If you'd replace a 2TB disk against a 6TB disk only temporarily in case of a disk failure and later would want to replace ist against a 2TB disk, without further partitioning or shrinking the whole disk by a special program like MHDD: This is not possible! ZFS partitions the whole space of added or replacement devices and will refuse to exchange against a smaller disk, even if the amount of used space would be small enough. 

3. Caution: Don't "add" a single HDD as additional vdev to your ZFS pool to gain space! In your setup (RAID-Z2) all data in your pool will be lost, if the added HDD fails.

4. Short answer: Your plan will not work.

I hope this helps.

Best regards from Dortmund, Germany,
Andreas

---

### Post by lukeiamyourfather on 2016-01-12
If you replace a 2TB drive in a VDEV with a 6TB drive then it will still act like a 2TB drive in the existing VDEV. You won't gain any additional capacity by swapping out one drive. In other words ZFS will use the smallest drive in the VDEV as the size for all of the drives.

If you are wanting to upgrade the capacity of the VDEV by replacing **all** of the drives this is possible by replacing one at a time. Before replacing any drives you'll want to enable auto expansion so it will take advantage of the new space once **all** of the drives have been replaced.

In your planned steps you mention a RAID card BIOS and adding a drive to the array. This has nothing to do with ZFS since ZFS is both a file system and a volume manager. Can you clarify what the RAID card BIOS has to do with the setup?

I want to repeat what has been said about not adding a single drive VDEV to an existing pool. This negates any redundancy you have with ZFS. Always add drives to a pool in the form of a VDEV with some level of redundancy (like RAID Z2 or at least a mirror).

---

### Post by elmatthijs on 2016-01-20
Thanx !
That clears up a lot for me.
Was going to buy a single 6TB WD Red disk, but will now start a completely new set on a different machine with several 2TB WD RE4 disks.

It is running under windows though, so no zfs L
Or I must make it dual boot, but my ssd does not have enough capacity for that...
Would need to buy a bigger one...
( will consider that though; next month&#8217;s pay check is nearby, and they are not really THAT expensive&#8230; )

When my server starts up, I need to "register" any hdds with the RAID card via its BIOS ( McRAID with Areca ), and then mark them as "pass through" disks ( effectively completely by-passing the on-board RAID-engine on the card ).
I then let Kubuntu create a zpool of the disks attached to the RAID card ( read: PCI sot ), and once done, create a zfs file system on the zpool.
 
I think I&#8217;ll buy a larger ss next month, stick my then old one in my dad&#8217;s PC, and create a dual-boot system with both Windows for downloading and BD editing, and use Kubuntu for the zfs backup of the data.
 
I have 3 8-disk zpools on a 24-bay server, but have run out of space&#8230;
Need a new zfs zpool, and start to decide what data to copy from the 24-bay to the new ( 4[SUP]th[/SUP] ) zpool.
( am I correct that when I start with a 4 disk zpool, I can not add a 5[SUP]th[/SUP] disk at a later stage ? If so, RAID5 under Windows might be a &#8220;beter&#8221; option for storing my backup of my DVDs ( I have boxed up in the attic ); and a lot less hassel. ).
 
Thanx, and sorry for my late reply,
lucas.

---

### Post by MAFoElffen on 2016-01-21
@ Mods: Server Section...
> **elmatthijs said:**
> Thanx !
That clears up a lot for me.
Was going to buy a single 6TB WD Red disk, but will now start a completely new set on a different machine with several 2TB WD RE4 disks.
...
( am I correct that when I start with a 4 disk zpool, I can not add a 5[SUP]th[/SUP] disk at a later stage ? 

The usual strategy with raidz is blow it away, redefine, start on new disks, restore the backup. But Raidz3 (triple parity) was developed for 6-10 TB disks. In a raidz3 repair on big disks, I think their estimates was that it might take a week to repair. ZFS does not have fschk, but rather scrub, which takes a bit longer. Oracle recommends that instead of running weekly, to run scrub once a month.

On differing sizes, you all are thinking inside the matchbox... raidz is software RAID. Same basic concepts as mdadm. The disks do not have to be the same size. The partitions that you are using need to be the same size... So use you imagination. a 6 tb disk is 3 x 2TB partitions(?).
> 
If so, RAID5 under Windows might be a &#8220;beter&#8221; option for storing my backup of my DVDs ( I have boxed up in the attic ); and a lot less hassel. ).

Why??? Really??? What about RAID6 in what you are running already (an Ubuntu core) using mdadm? mdadm, you can add members, shrink or grow... Or dump raid and do just LVM? No problem there with different sized disks. That is what i converted many of my Virtual Host Servers to. When they were Raid. If a problem, it was faster to also take the ZFS strategy, that try to repair. So if I was restoring backups anyways, why not on LVM where it was more flexible. With 20TB, it is light-years faster to get up with LVM, than assembling a RAID array. (on the same hardware config)

I do both Win Server and Ubuntu Server. I am biased to Ubuntu Server for a reason. Win is still trying to catch up on software raid and logical volume managers. That and they can not boot from either (full system in a native system volume).

---

### Post by lukeiamyourfather on 2016-01-21
> **elmatthijs said:**
> I have 3 8-disk zpools on a 24-bay server, but have run out of space…

You can add more VDEV to a pool whenever you want. That's the point of pooled storage. So if you have one RAID Z2 type VDEV in the pool you can just add another RAID Z2 type VDEV and it will extend the usable space in the pool seamlessly and it will automatically balance new data between the new VDEV and the old VDEV.

---

