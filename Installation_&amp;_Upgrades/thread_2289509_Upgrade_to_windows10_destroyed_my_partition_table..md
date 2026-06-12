---
title: "Upgrade to windows10 destroyed my partition table."
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by moonsky219 on 2015-08-04
Hello all!

I had  Ubuntu 15.04 alongside with windows 8.1, my laptop is an old laptop and  used mbr. When I tried to upgrade windows8.1 to windows10, it seems that  the upgrade process of windows rewrite my disk partition table which  broke grub and the part of Ubuntu. When I boot my computer it shows:

error: no such partition.
Entering rescue mode...
grub rescue>

I guess that's because it can neither find bootmgr of windows nor find  grub which is broken. Here at grub rescue, the file system of all  (hd0,msdosX) is unknown, Just do set, prefix, normal...... doesn't work.

So my plan is using testDisk to restore my partition table and using  boot-repair to make grub works again. Before I use testDisk, boot-repair  give me this report: [http://paste.ubuntu.com/12001221](http://paste.ubuntu.com/12001221).

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   766,029,732   765,822,885   7 NTFS / exFAT / HPFS
/dev/sda3         766,029,824   767,055,871     1,026,048  27 Hidden NTFS (Recovery Environment)
/dev/sda4         767,057,918   976,771,071   209,713,154   5 Extended
/dev/sda5         966,774,784   976,771,071     9,996,288  82 Linux swap / Solaris

So that's exactly what windows upgrade process had done to my partition   table. It seems the end of sda4 is wrong. Sda4 should be the part of   Ubuntu. Surprisingly It also seems after sd2(which is windows) there is a   hidden ntfs (recovery environment), I have no idea what is that for, I   think that may be just useless.

-------------------------------------------------------------------------------------------------------------------------
After testDisk deep analyze, I rewrite the partition table, fdisk shows:

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 766029823 765822976 365.2G  7 HPFS/NTFS/exFAT
/dev/sda3       767057920 966774783 199716864  95.2G 83 Linux
/dev/sda4       966774784 976771071   9996288   4.8G 82 Linux swap / Solaris

There is a gap between sda2 and sda3 (which is originally hidden NTFS), I  just leave it here and hope that's fine, I see some bootmgr file in  sda1, sda2 is windows, sda3 is ubuntu 15.04 and sda4 is swap. Actually I  don't know where grub should be installed. Can someone explain me about  this please? Also at this moment, I can see the file of this two part  (windows and Ubuntu) from usb live ubuntu, they are lie in there so far.
--------------------------------------------------------------------------------------------------------------------------------------------------------------

I ran boot-repair again and got this report: [http://paste.ubuntu.com/12002363/](http://paste.ubuntu.com/12002363/)
It seems something is messed up with Sda3, boot sector info is different  with testDisk. Am I doing something wrong with testDisk? Please guide  me, Thank you for any help!
OK, I recheck the hidden ntfs, there are files created on the date I  upgrade windows! I will run testDisk again to recover this partition.  But I am still not sure what should I do next after that.

---

### Post by ruzekle on 2015-08-04
Can you mount the disk and manipulate your Ubuntu file system using a liveCD? I know that Microsoft can destroy Linux partitions and usually does.

---

### Post by moonsky219 on 2015-08-04
Yes, I can do that. Now I am trying to do deep analysis again to bring that hidden NTFS back.

---

### Post by oldfred on 2015-08-04
Your original list of partitions showed the gap inside the sda4 extended partition. The extended was a container for your two logical partitions, your Linux & swap.
The sda4 was not your Linux partition but it was in the gap between the start of the extended partition and the start of the swap partition.
All you had to do was restore the one missing logical partition by changing the D to L.

But now you did something to the original sda3 partition which was your recovery partition. That should not be changed from its original size and location on drive. But if you do not need the recovery partition then you system should work. You should have made a set of DVD from original recovery partition when you first got system. Then you can delete recovery partition.

If you try to bring recovery partition back as a primary partition then both the Linux partition and swap have to be logical. It will automatically create the extended partition to include all logical partitions.

And you converted you logical partitions to primary partitions. MBR has a limit of 4 primary partitions. But if you do not want recovery back it is ok. But I do not know why partition header says NTFS, it should say Linux & swap should say swap.

Partition table looks correct, but data in partition does not.

---

### Post by moonsky219 on 2015-08-04
> **oldfred said:**
> Your original list of partitions showed the gap inside the sda4 extended partition. The extended was a container for your two logical partitions, your Linux & swap.
The sda4 was not your Linux partition but it was in the gap between the start of the extended partition and the start of the swap partition.
All you had to do was restore the one missing logical partition by changing the D to L.

But now you did something to the original sda3 partition which was your recovery partition. That should not be changed from its original size and location on drive. But if you do not need the recovery partition then you system should work. You should have made a set of DVD from original recovery partition when you first got system. Then you can delete recovery partition.

If you try to bring recovery partition back as a primary partition then both the Linux partition and swap have to be logical. It will automatically create the extended partition to include all logical partitions.

And you converted you logical partitions to primary partitions. MBR has a limit of 4 primary partitions. But if you do not want recovery back it is ok. But I do not know why partition header says NTFS, it should say Linux & swap should say swap.

Partition table looks correct, but data in partition does not.

Thank you for your help!

I find a wired thing that TestDisk would say Structure Bad if I change any partition to Logical, it seems only allowed to change it to Primary. I don't know why this would happen......

---

### Post by oldfred on 2015-08-04
All logical partitions have to be next to each other.
I wish testdisk used sectors as then it would be easy to tell which is which.

If you changed partitions several times testdisk finds all the alternatives and you have to select the set of partitions that do not overlap. And should match your first partition list but with one more logical for the Linux partition.
Window sda1 must be the bootable (*) one, sda2 is primary, sda3 is primary, and then sda5 & sda6 are logical (L).

```
 /dev/sda4 [COLOR=#ff0000]767,057,918[/COLOR] 976,771,071 209,713,154 5 Extended
/dev/sda5 [COLOR=#ff0000]966,774,784[/COLOR] 976,771,071 9,996,288 82 Linux swap / Solaris


```

Your Linux partition started one or two sectors after the start of the extended partition, and ended one or two sectors( but could vary) before the start of the swap partition.
The extended partition started a little less than 100 sectors after the end of the NTFS recovery partition.

There is a way to calculate Testdisks CHS values back to sectors, then you would know for sure which is which:
 Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

### Post by moonsky219 on 2015-08-04
> **oldfred said:**
> All logical partitions have to be next to each other.
I wish testdisk used sectors as then it would be easy to tell which is which.

If you changed partitions several times testdisk finds all the alternatives and you have to select the set of partitions that do not overlap. And should match your first partition list but with one more logical for the Linux partition.
Window sda1 must be the bootable (*) one, sda2 is primary, sda3 is primary, and then sda5 & sda6 are logical (L).

```
 /dev/sda4 [COLOR=#ff0000]767,057,918[/COLOR] 976,771,071 209,713,154 5 Extended
/dev/sda5 [COLOR=#ff0000]966,774,784[/COLOR] 976,771,071 9,996,288 82 Linux swap / Solaris


```

Your Linux partition started one or two sectors after the start of the extended partition, and ended one or two sectors( but could vary) before the start of the swap partition.
The extended partition started a little less than 100 sectors after the end of the NTFS recovery partition.

There is a way to calculate Testdisks CHS values back to sectors, then you would know for sure which is which:
 Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

Thank you OldFred!

But I am a little confused of your statement.

This is the original table:

Partition  Boot  Start Sector    End Sector  # of Sectors      Id       System

/dev/sda1    *          2,048       206,847         204,800          7 NTFS / exFAT / HPFS
/dev/sda2             206,848      766,029,732   765,822,885   7 NTFS / exFAT / HPFS
/dev/sda3         766,029,824    767,055,871   1,026,048     27 Hidden NTFS (Recovery Environment)
/dev/sda4         767,057,918    976,771,071   209,713,154   5 Extended
/dev/sda5         966,774,784    976,771,071   9,996,288     82 Linux swap / Solaris,800   7 NTFS / exFAT / HPFS

So sda1 (Windows, Bootable), sda2 (Windows, Primary), sda3 (Windows recovery, Primary) is correct, and sda4 should become sda4 (Linux, Logical) and sda5 (Swap, Logical), then what is the remaining original sda5 here?

---

### Post by oldfred on 2015-08-04
Not quite. 
The fourth primary sda4 is the extended partition which includes all logical partitions inside it. 
All primary partitions are sda1 thru sda4.
And all logical partitions start at sda5 even if you have not used all 4 primary. 

You could but not recommended have one primary that is the extended as sda1 and then all logicals starting at sda5.

So sda4 is the extended as shown in your original partition table. And swap is inside that extended. But from the start of the extended to the start of the swap is a large gap that was your Linux partition. It probably was sda5 and swap sda6, but now that Ubuntu uses UUIDs the partition number is not critical.

In testdisk you should see all the existing partitions and a screen with deleted partitions. If your repartioned several times then you may have several deleted partitions. But you need to find one deleted that starts after the sda3 and ends before the sda5 and is set as logical so then the extended will include both sda5 & sda6.

Post this, preferably after you have recovered all partitions, but if not whatever you can:
       sudo sfdisk -d /dev/sda

---

### Post by moonsky219 on 2015-08-05
> **oldfred said:**
> Not quite. 
The fourth primary sda4 is the extended partition which includes all logical partitions inside it. 
All primary partitions are sda1 thru sda4.
And all logical partitions start at sda5 even if you have not used all 4 primary. 

You could but not recommended have one primary that is the extended as sda1 and then all logicals starting at sda5.

So sda4 is the extended as shown in your original partition table. And swap is inside that extended. But from the start of the extended to the start of the swap is a large gap that was your Linux partition. It probably was sda5 and swap sda6, but now that Ubuntu uses UUIDs the partition number is not critical.

In testdisk you should see all the existing partitions and a screen with deleted partitions. If your repartioned several times then you may have several deleted partitions. But you need to find one deleted that starts after the sda3 and ends before the sda5 and is set as logical so then the extended will include both sda5 & sda6.

Post this, preferably after you have recovered all partitions, but if not whatever you can:
       sudo sfdisk -d /dev/sda

Thank you so much, OldFred, you really help me get through this mess.

Actually I was kind of give up yesterday before your last reply. So I apply the partition table given by the quick search result of testDisk, which delete the missing Ubuntu partition, only leave sda1 (windows boot), sda2 (windows), sda3 (windows recovery) and sda4(linux swap). After ran boot-repair, I booted into windows directly and finished my upgrading. I think that's pretty lucky and I want to get my Ubuntu back. After deep analysis, I am pretty sure that I had found the correct Ubuntu partition, it's just before swap partition and after windows recovery partition, I am sure there is no any gap or overlapping between Linux and swap, there is a little gap between windows recovery partition and Linux. 

However the weird thing happened again, I cannot set Linux and Swap partition both as logical. Bad structure it said. 

Finally I deleted windows recovery partition, and set Linux and Swap partition both as primary. Surprisingly it worked! I got windows 10 and Ubuntu both on Today's morning. And the grub menu showed two windows options (both windows 8, weird but worked and is windows 10 actually) on sda1 and sda2.

I think I have made it and leave my laptop syncing Onedrive (BTW, I have two onedrive icon on left panel of windows 10 both point to the same position. Also, although I already have onedrive folder and files on my disk, onedrive just ignore it and open a new folder also named onedrive and download another copy, I can't even tell the difference between these two folders, same direction same name......). My point is onedrive suck during the upgrade process.

Anyway, when I go home in the afternoon, I found my laptop is turned off, after booted into windows, it took me to restoring back to old version of windows!!! I really want to know why this happened. The 502MB windows recovery partition is deleted, aka unallocated. Was that triggered windows to restore old version by using windows.old folder in sda2 (windows partition)?

Now I get windows 8.1 along with Ubuntu, exactly go back to the start point!!! I guess I will not upgrade windows 10 directly from windows 8.1. Maybe someday I will just install it from flash disk after I get iso file. 

Thank you OldFred again! You really helped me a lot!!!

---

### Post by Mark Phelps on 2015-08-05
I feel for you -- really!  I made the mistake of believing the Win10 Upgrade checker when it said my HP laptop had no hardware or software issues, and accepted the update.  What I ended up with was a trashed machine that would not boot.  I was able to get it booting again but it's still in bad shape.

What MS has not told folks is that the in-place upgrade AUTOMATICALLY changes the partition structure on your drive! I ended up with a System Reserved partition (that did not work) and a Recovery partition (that I did not need).

Right now, you can NOT do a clean install from Win10 media because it will not accept any activation keys -- period. You can only do an Upgrade from an existing Win7/8/8.1 installation.

I'm hoping down that road, that they will provide a way to do a clean install and activate by entering an existing key, but they've not indicated they ever intend to support that.

So basically, if the Upgrade doesn't work, then you're stuck.

---

### Post by QIII on 2015-08-05
Actually, you can do a clean install as I did. After upgrading you can do a clean install with the utility [here]("https://www.microsoft.com/en-us/software-download/windows10").  You just can't do it with the .iso without a key.

Using the download tool, you can create a USB installer.  Once you have upgraded and activated Windows 10, you can use the installer to do a clean install as often as you need to on any device which already has been upgraded.

You'll have to be careful and choose the right partition, then select to reformat it.  Your activation should persist.

Anyway, since that's a full-on clean install, the problems may go away.



And you can also get rid of the annoying "tiles" in the start menu by right-clicking and unpinning them...

[ATTACH=CONFIG]263669[/ATTACH]

---

### Post by VMC on 2015-08-06
> **QIII said:**
> Actually, you can do a clean install as I did. After upgrading you can do a clean install with the utility [here]("https://www.microsoft.com/en-us/software-download/windows10").  You just can't do it with the .iso **without a key**.


That's because now your Windows 10 uses [HWID]("http://www.webopedia.com/TERM/H/HWID.html"). So be careful changing HD, DVD drives, and most *definitely*  motherboards.

---

