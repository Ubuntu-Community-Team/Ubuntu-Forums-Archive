---
title: "Are Ubuntu partitions at risk when Windows updates?"
date: 2018-02-20
forum: Installation &amp; Upgrades
---

### Post by Clopper Almon on 2018-02-20
In a helpful article at [https://turbofuture.com/computers/Dual-Boot-Ubuntu-1604-LTS-and-Windows-10](https://turbofuture.com/computers/Dual-Boot-Ubuntu-1604-LTS-and-Windows-10) Nico Wells warns not to use the Ubuntu disk partitioner when installing 16.04 alongside Windows 10 “as when Windows updates it may interfere with the Ubuntu installation.” Instead, she advises using the Windows 10 shrinker to shrink the Windows C drive before the installation of Ubuntu. This Windows method, however, will do much less shrinking than the Ubuntu  partitioner. In my case, Windows would release only about one third of the 1 terabyte hard disk. I then used the Ubuntu partitioner to give Ubuntu about 65% of the available space. Am I at risk whenever Windows 10 updates?

---

### Post by Topsiho on 2018-02-20
As far as I know you should let Windows do the repartitioning of the hard disk, before installing Ubuntu. And after the repartitioning (in Windows), reboot Windows and see whether it recognizes the new situation.
If you let Ubuntu (Gparted) do the repartitioning, and then install Ubuntu in the empty space, risk is that Windows doesn't boot, as it is confronted with a situation it doesn't know. Or it checks the entire hard disk,
which can take a very long time, and only seems not booting at all. If it finally boots, you are in luck.
So you are not only at risk during Windows updates. (Can't you control these updates yourself? I don't use Windows for maybe a decade now, don't miss it at all, but this sounds crazy to me).
Gparted is a perfect partitioner, but does some things in a way that is different from Windows partitioners. I know that from my Windows days, using a very expensive commercial partitioner, Partition Magic.

Topsiho

---

### Post by ajgreeny on 2018-02-20
You should **ALWAYS USE WINDOWS UTILITIES TO MAKE CHANGES TO WINDOWS PARTITIONS.**

Windows XP was probably the last Windows system on which you could safely use gparted (with care, and only moving the end point, not the start) with safety; I did it many times when I first started using Ubuntu and gparted, and never had a problem.

Windows unfortunately is not clever enough to understand or realise that Ubuntu's partitions are needed for the Ubuntu OS, so whilst it does not actually damage the partitions, it does remove them from the disk's partition table whenever it carries out major updates, meaning that you can not boot to Ubuntu without first repairing the partition table.

I have never needed to do this (I have no Windows OS any more) but you need to use sgdisk to backup and restore the PT.

---

### Post by Clopper Almon on 2018-02-20
Thanks. The problem is that the Windows partitioner keeps at least 2/3 of a terabyte disk for 
Windows. I would like 2/3 for Linux.

---

### Post by ubfan1 on 2018-02-20
Did you defrag the filesystem before trying to shrink the partition?  Maybe there's data there preventing the partition from shrinking, since the filesystem cannot shrink.

---

### Post by Topsiho on 2018-02-21
+1 for ubfan1

I second his suggestion.

Windows places it's data randomly all over the place in the partitions on the hard disk. Just wherever it finds a location in the partition where it fits in. So you need to defrag the disk once in a while.
By defragging the partitions the data are placed in a more compact manner, in one place of the partition.
In Linux this defragging is not necessary, as the disk is kept defragged all the time.

Time and time again Linux is the superior operating system.

Topsiho

---

### Post by Autodave on 2018-02-21
I have had Windows' updates twice wipe my Ubuntu system. Keep good backups.

---

### Post by Clopper Almon on 2018-02-22
Yes, I did run the defrager before attempting the shrink. It was a new new computer and the defrager showed zero fragmentation.

---

### Post by Mark Phelps on 2018-02-22
Windows 10 forced periodic HUGE updates on folks, known now as Version Upgrades (since MS is not using the Win 8.n notation anymore) -- and it keeps the old files around for a while, which fills up the drive over time.

In Windows, open an elevated command window and run this:

> Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase

That will clean out the duplicate and no longer needed Windows Update files.

After you do that, you should be able to reclaim more free space and shrink the partition more.

---

### Post by oldfred on 2018-02-24
Also:
 Resize Vista partition, similar for newer Windows.
If problems, try temporarily disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

---

