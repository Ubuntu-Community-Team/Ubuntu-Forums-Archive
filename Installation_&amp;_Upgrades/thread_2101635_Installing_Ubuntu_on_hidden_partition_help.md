---
title: "Installing Ubuntu on hidden partition help?"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by dorruk on 2013-01-05
This is a cross platform issue so I didn't know where to post this.
That is my current disk status. Thing is, Windows says you can't split one hard drive more than 4 primary partitions. So I can't give a drive letter to that unallocated space at the moment.

I want to install Ubuntu on that unallocated space. So right now, all my hopes are on GParted. Is there a way to hide that unallocated space from Windows but to boot from it and use it seamlessly with Ubuntu? In other words, I just want to bypass the 4 partition limit for multibooting as much OS's as I want.

Also GRUB must be able to read that partition.

Currently dual booting Win 7 and 8 in the following configuration:
25 GB partition: I dunno what it is.
C drive: Windows 7 + Apps + Data
D drive: Apps + DATA
G drive: Windows 8 + Data

---

### Post by dorruk on 2013-01-05
Bump? Please?
If I converted drive D to logical, would that free up a primary slot in MBR?

---

### Post by darkod on 2013-01-05
Wow, the partitions are quite a mess. You can't hide partitions, the limitation of 4 primary or 3 primary + 1 extended is from the msdos table, not from windows. It doesn't matter if a partition is hidden, if it's still primary.

And the logical partitions need to be together next to each other. You create a logical partition with primary after it so effectively you can't create more logical now to be joined to the first one because there is no unalllocated space next to it.

Also, look at the partitions list at the top. What is the Samsung H: partition? It says 930GB but your hdd is 500GB. How can that be?

A perfect example how windows partitioning tools can really mess up your hdd sometimes. If you have the possibility to move your data on some external hdd, do it so you have backup of it. Then I would try deleting all non-system partitions to try and sort out the issue.

If you are sure you are not using that 25GB partition, you can try deleting it too.

In any case, this will be tricky to sort out. It's best if the D: data partition was before the logical, not after it. You should always try to keep primary partitions at front, logicals at back so they can be all together in the extended partition. But windows is not really smart.

Look at the current partition list at top. It says you have 4 primary and 1 logical which is impossible. You can either have 4 primary, or 3 primary + logical partitions.

---

### Post by grahammechanical on 2013-01-05
Just a small point for completeness.

Logical partitions should be inside an Extended partition. The way around the four Primary partition limit is to have one of the primary partitions as an Extended partition. Then a number of Logical partitions can be created inside the Extended partition. Of course, there will be space limitations according to the size of the hard disk.

> The total data storage space of a PC hard disk can be divided into at most four primary partitions, or alternatively three primary partitions and an extended partition. These partitions are described by 16-byte entries that constitute the Partition Table, located in the master boot record.

> A hard disk may contain only one extended partition; the extended partition can be subdivided into multiple logical partitions. 

[http://en.wikipedia.org/wiki/Disk_partitioning]("http://en.wikipedia.org/wiki/Disk_partitioning")

Could it be that somehow these partitions/disks have been converted into Dynamic disks?

[http://technet.microsoft.com/en-us/library/cc731274.aspx]("http://technet.microsoft.com/en-us/library/cc731274.aspx")

[http://technet.microsoft.com/en-us/library/cc755238.aspx]("http://technet.microsoft.com/en-us/library/cc755238.aspx")

That could (I do not really know) give the impression that the four primary partition limit has been broken.

Regards.

---

### Post by darkod on 2013-01-05
I thought about Dynamic but if you look at the Disk Management screenshot it says Disk 0 is Basic.

Do you maybe have another 1TB disk that you didn't include in the screenshot crop? That would explain a single 930GB primary partition since 1TB is approx 930GiB. And it would also explain a total of 4 primary + 1 extended partitions.
3 primary + 1 extended on the disk 0 we can see.
1 primary of 930GB on disk 1 that we can't see.

That still doesn't solve the badly planned layout of disk 0. You still have to find a way to move the logical partition to the end, so that you can combine it with the unallocated space there. One option is maybe trying Fixparts from ubuntu live mode. Fixparts can swithc primary partition to logical if the position on the disk allows it. In case of the D: partition, the position allows it to be converted to logical since it's next to the only logical partition on the disk. But make sure you have a full backup of the data in any case before trying this.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

---

### Post by darkod on 2013-01-05
Two things I would also address, but they don't seem urgent:
1. If you really don't use that 25GB partition, why don't you delete it? And why did you create it and left it there anyway? That would not only release one primary spot but it would also make those 25GB available to be included inside C: by expanding C: to the left.
2. The win8 partition has only 5% free space. That is usually very low for windows and it will probably start giving you problems. This might be urgent, or not, but it's good to be addressed. You need that partition to be bigger, or clear up some space on it. For example you can lower the size of the swap file which windows makes the same size as RAM. If you have loads of RAM, the swap file will be huge and that's bad if you have limited space. The same goes for the hibernation file but I'm not sure whether you plan to use it or not, and whether you can turn hibernation off in win8 like you can in win7.

---

### Post by oldfred on 2013-01-05
I think the 25GB is just the unformatted space, so not yet a partition.

More concern about why partition sizes do not match. That should be resolved first.

But you may be able to  convert primary partition to logical in an extended and then possibly move some things around.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by dorruk on 2013-01-07
I think I need to clarify a couple of things :D

That 930 GB Samsung is a separate hard drive than the computer's internal HDD. The C, D, G drives are in the internal. I use H: Samsung for external storage. But I don't always have it with me, and I may lose it, so I need to have my operating systems in the internal Disk 0 which is 596 GB.

I have considered merging C and D but I have this programs in D:/Program Files and C:/Program Files if I just create a single drive letter C from both, then the paths will be broken and apps that depend on drive D may stop working.

I took this screenshot from Win8. Previous one was Win7. All drive letters may have changed but everything is the same.

Could you explain a little further on the logical/extended partition workaround? How many operating systems may I install on a single hard drive with this technique? And what does the order of drives change? eg. Drive C comes after D?

---

### Post by darkod on 2013-01-07
Windows calls the system partition C: so when you check from win7, its system partition is C:. When you look from win8, its partition is C:.

What I would do in this case:
Delete that 25GB partition. It looks empty anyway. That will "release" one primary partition and give you a chance to install ubuntu.
If you use the auto install method, it will create the ubuntu partitions as logical by default.
If you use the manual method, don't forget to create the partitions as logical yourself when it asks you.

---

### Post by oldfred on 2013-01-07
Use gparted from live CD/DVD/Flash and post screenshot. I still think Windows is calling the unallocated a partition when it is not.

You can have an unlimited number of logical partitions in the one extended. The one extended partition is one of the four primary partitions allowed in MBR. Windows only boots from a primary partition, but will install or use logical partitions for second installs or data. But if you install Windows to a logical it can only ever boot from the first install, in cannot be repaired to boot on its own.

You can install almost all Linux systems in logical partitions and boot from them. I have many in my 640GB drive.

---

### Post by dorruk on 2013-01-08
Sorry for late response, oldfred. Had to install Ubuntu on a thumb drive.

Guess I'll delete the RECOVERY partition, remove Win7 (labeled OS) and completely switch to Win8 so I will have room for 2 more operating systems, right?

---

### Post by oldfred on 2013-01-08
You will have to reinstall Windows 8 as Windows only boots from a primary partition. And right now it is in a way too small logical partition. So Windows 8's boot files actually are in your Windows 7 partition.

If you might ever want to go back to Windows 7, best to make a backup before deleting.

And if ever wanting to totally restore to as purchased you should use recovery to make a set of DVDs to restore system. If you later sell system it may need to have original system installed.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by darkod on 2013-01-08
Why are you linking the number of OSs with the number of partitions? The relation is not direct.

It all depends first of all, which two more OSs you want to install. If they are linux, they can work perfectly fine from logical partitions so you don't have to delete any windows.
Even windows can work from logical partition once you have one primary with the boot flag to hold the boot files. Your current win8 is best example of that.

I have to go back to my advice: Just delete the empty 25GB partition and that will let you start creating logical partitions. Install as many linux versions as you want.

---

### Post by dorruk on 2013-01-11
Sorry for resurrecting an old thread. Just wanted to note that I got it working, thanks a lot!

---

