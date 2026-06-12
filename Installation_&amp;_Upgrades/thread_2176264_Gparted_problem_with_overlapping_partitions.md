---
title: "Gparted problem with overlapping partitions"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by Dospanes on 2013-09-23
Hello friends,

I encounter some difficulties when trying to resize my Ubuntu Partition with gparted. 
i have Ubuntu running on a SSD with 120 GB (dev/sdb3) where I still have a Windows 7 Partition. 

I followed the instructions provided [here ]("http://askubuntu.com/questions/51272/how-do-i-repartition-with-gparted")and logged in with Ubuntu from a Pendrive.
Shrinking the Windows Partition was no problem but when trying to increase the Ubuntu partition I encountered the following error:

```

GParted 0.12.1 --enable-libparted-dmraid

 Libparted 2.3
 [TABLE]
[TR]
[TD="colspan: 2"] **Move /dev/sdb3 to the left and grow it from 13.95 GiB to 40.31 GiB**  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] calibrate /dev/sdb3  00:00:00    ( SUCCESS )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]path: /dev/sdb3
start: 220,817,406
end: 250,068,991
size: 29,251,586 (13.95 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] move partition to the left and grow it from 13.95 GiB to 40.31 GiB  00:00:00    ( ERROR )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] [I]old start: 220,817,406
old end: 250,068,991
old size: 29,251,586 (13.95 GiB)[/I][/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] [I]requested start: 165,521,408
requested end: 250,066,943
requested size: 84,545,536 (40.31 GiB)[/I][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] libparted messages    ( INFO )[/TD]
[/TR]
[TR]
[TD][/TD]
[TD] [TABLE]
[TR]
[TD="colspan: 2"] *Unable to satisfy all constraints on the partition.*[/TD]
[/TR]
[/TABLE]
 [TABLE]
[TR]
[TD="colspan: 2"] *Can't have overlapping partitions.*[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
 ========================================



```

The situation is similar as described [here]("http://askubuntu.com/questions/223381/error-in-using-gparted-to-add-unallocated-space"), but still I couldn't find any further instructions how to solve this...Most people just simply switched to other tools mainly MS Software solutions...

Has anybody expirienced similar problems?

---

### Post by Quackers on 2013-09-23
It is good practise to use Windows tools for shrinking Windows partitions and rebooting twice after to make sure its file system is happy. If your Windows still boots it's probably ok.
I would imagine that it would be all the more important if you have a raid system.

Normally I would suggest downloading [Fixparts]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.8.7/fixparts-binaries/") .deb file for your architecture (32bit/64bit) and install and run it following the guide below. 
[http://www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")

However I'm not sure it can handle raid setups. If you try it please be very careful and in any event you should backup everything you wouldn't want to lose first.

---

### Post by varunendra on 2013-09-24
A big +1 to using windows tools (preferably windows' own partition manager) for shrinking windows partition.

Since you seem to have already done that anyway, can you boot into windows? If you can, let it do any repairs it may want, then reboot 'Twice' into windows. Then try Gparted again and post back if there are still problems.

---

### Post by Dospanes on 2013-09-24
thanks for your replies. 

Yes, windows worked just fine and now I was also abled to fix the problem like this:

1. Enter in gparted from USB  
2. Delete the Linux Swap partition 
3. Resize the  extendet partition
4. Resize the logical partition containing Ubuntu
5. Recreate the Linux Swap
6. Poweroff
7. Boot Ubuntu normally
8. Activate the new Swap partition again by changing the UID in fstab as described [here]("https://help.ubuntu.com/community/SwapFaq").
9. Reboot and check if changes apply.


I was somehow "inspired" by [this post]("http://askubuntu.com/questions/82669/overlapping-partitions-problem") (similiar problem) that statet that:

> 
In order to understand the problem here it is necessary to know how  disk partitioning works. A classic DOS partition table can only contain four entries. To  circumvent this restriction while staying compatible, one partition type  was defined to be a so-called extended partition which can itself  contain additional "logical partitions".

 On your drive, there is a "hole" in the extended partition where no *logical* partition is defined. Instead a primary partition overlaps the extended partition and fills that hole exactly. So no *data* is really overlapping, and there is no immediate danger of data loss.



Still... when I rethink this I don't quite get it why this should apply in my case and be solved by temporarly deleating the Swap (since I thought swap is "containered" inside the extendet partition. Therefore it should not show up as a fourth partition in the  DOS partition table...?). 


Anyway it worked :)

---

### Post by gedakc on 2013-09-25
I suspect that you encountered one of the following bugs:

[Bug 686668 - Growing logical partition overlaps end of extended partition]("https://bugzilla.gnome.org/show_bug.cgi?id=686668")
This was fixed in GParted 0.14.1

or
[Bug 678831 - Partition End Overlap when Resizing Extended Partition]("https://bugzilla.gnome.org/show_bug.cgi?id=678831")
This was fixed in GParted 0.13.0

---

