---
title: "[SOLVED] How Would YOU Configure This System?"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by Therion on 2007-11-02
I have a dual-hard drive system consisting of one WD 120GB **PATA** HDD and one Maxtor 200GB **SATA** HDD.  Currently, XP is installed on the SATA drive, Ubuntu on the PATA drive.  This situation is far from ideal.  What I'm considering is reformatting the SATA drive, and reinstalling both WinXP and Ubuntu on it; partitioning the HDD right down the middle and giving each OS roughly equal room on the one SATA drive.  Then I'd reformat the secondary IDE drive (most likely using FAT32); using it for backups and general storage purposes.

My question is... is this the best all around configuration, with both OS'es on the same drive?  Would having one OS per drive be better for some reason?  Also, is there anything I'm not thinking of, or an easier way to achieve what I want?  I don't mind doing a full-blown reformat and reinstall of both OS'es on the one drive.  I've done so many WinXP installs I can about do them in my sleep; and Ubuntu installs are just a one-hour walk in the park by comparison.

So, in short, what I'm asking is... What would be the most awesomest dual-boot (considering the mixed drives) set up EVARRR??

---

### Post by Pumalite on 2007-11-02
The ideal is ALL SATA or ALL IDE. If that is not possible, then I have a couple of links that might help you get oriented:

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by timcredible on 2007-11-02
i would do this:

sata: 20GB for Windows in first partition
          10GB as ext3 for ubuntu
          1GB as swap partition
          169GB as ext3 for /home
pata: all of it ext3 for /data

---

### Post by Therion on 2007-11-02
> **Pumalite said:**
> The ideal is ALL SATA or ALL IDE. If that is not possible, then I have a couple of links that might help you get oriented...
Ahhh... Most excellent.  This is going to be easier than I thought. The first link led me to [[color=blue]this tutorial[/color]]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu") which makes things look like a cakewalk.

My only remaining question:  XP has most all of its file-structure at the beginning of the drive, but there are some small "chunks" hanging out in the middle to end of the drive.  Will the Ubuntu partitioning tool put everything together in the XP partition so the Ubuntu install has as much free space as possible for its own partition?

Thanks for your input, by the way... That's a great tutorial!

> **timcredible said:**
> i would do this:

sata: 20GB for Windows in first partition
          10GB as ext3 for ubuntu
          1GB as swap partition
          169GB as ext3 for /home
pata: all of it ext3 for /data
I'd like the PATA drive accessible by both Linux and XP and it's my understanding XP doesn't play nicely with ext3.  
I've heard of apps (Linux Reader, i think) that allow for that, but I don't know if it's stable, reliable, etc.  Still, the more I think about it, the only reason I'm really keeping the XP install around is for gaming.  No other reason.  I'm ready to make the switch for everything else.

---

### Post by Pumalite on 2007-11-02
I think you have to go some place in XP and set File Paging to '0'. Later return it to set value.

---

### Post by Steve1961 on 2007-11-02
I woud suggest that you defrag throughly before you start.  Once you've done that you can either use the Ubuntu CD to shrink the XP partition or, and this has always been my preference, use a windows tool such as Acronis disk director to shrink the partition.  Then just install Ubuntu to the free space. (You can probably download a trial version of Acronis)

---

### Post by stchman on 2007-11-02
> **Therion said:**
> I have a dual-hard drive system consisting of one WD 120GB **PATA** HDD and one Maxtor 200GB **SATA** HDD.  Currently, XP is installed on the SATA drive, Ubuntu on the PATA drive.  This situation is far from ideal.  What I'm considering is reformatting the SATA drive, and reinstalling both WinXP and Ubuntu on it; partitioning the HDD right down the middle and giving each OS roughly equal room on the one SATA drive.  Then I'd reformat the secondary IDE drive (most likely using FAT32); using it for backups and general storage purposes.

My question is... is this the best all around configuration, with both OS'es on the same drive?  Would having one OS per drive be better for some reason?  Also, is there anything I'm not thinking of, or an easier way to achieve what I want?  I don't mind doing a full-blown reformat and reinstall of both OS'es on the one drive.  I've done so many WinXP installs I can about do them in my sleep; and Ubuntu installs are just a one-hour walk in the park by comparison.

So, in short, what I'm asking is... What would be the most awesomest dual-boot (considering the mixed drives) set up EVARRR??

Does your system work?  If yes then I would not change the configuration.

If you have the entire 120G drive for Ubuntu consider partitioning using the following numbers.

120GB hdd
Ubuntu 30G (ext3)
Ubuntu storage 90G (ext3)

200GB hdd
Win XP 30GB (ntfs)
WinXP storage 90GB (ntfs)
Shared storage 80GB (fat32)

You can use gparted on the LiveCD to do all this.  You can install ntfs-3g to read/write to th ntfs partitions in Ubuntu and install the ext read/write software on XP to read the Linux stuff.

---

### Post by Therion on 2007-11-02
> **Steve1961 said:**
> I woud suggest that you defrag throughly before you start.  Once you've done that you can either use the Ubuntu CD to shrink the XP partition or, and this has always been my preference, use a windows tool such as Acronis disk director to shrink the partition.  Then just install Ubuntu to the free space. (You can probably download a trial version of Acronis)
d'oh, I forgot to mention I do have Partition Magic.  Would that be able to shrink my XP partition?  I'd like to do that to give Ubuntu as much room as possible for it's own install.

> **stchman said:**
> Does your system work?  If yes then I would not change the configuration.
Well, yes ... and no.  Right now, if I want to boot into XP, I have to physically switch drives.  Mixing PATA and SATA drives, I have found out, is a tricky thing.  My preference, unless there are compelling reasons to do otherwise, is both OS'es on the same SATA drive and keeping the PATA drive soley for data-storage.  I have this "thing" about having a drive that's *physically isolated* from the OS, or OS'es, that I use for backups and storage.

Thanks for the input everyone!  Some good ideas and things to consider!!!

---

### Post by Steve1961 on 2007-11-02
> d'oh, I forgot to mention I do have Partition Magic. Would that be able to shrink my XP partition? I'd like to do that to give Ubuntu as much room as possible for it's own install.

Yep, that should do the job fine

---

### Post by Therion on 2007-11-02
> **Steve1961 said:**
> Yep, that should do the job fine
Great.  Thank you.

Plan formulated, thread "Solved".  Thanks again everyone!!

---

### Post by Fantomäs on 2007-11-03
Hi all,

Same subject but I want to do a clean install of Ubuntu Studio 7.10 64bit on this system:

Q6600 2GB RAM. First HD 75GB Raptor with Xp and a second WD Sata 500GB data only.

I'm thinking of using 20/25GB for Studio on the first HD, including the swap area and  /home partition for future update. How big should the swap area and /home be? 

Thank you

---

### Post by Pumalite on 2007-11-03
10 GB for '/'
1 gb /swap
The rest for /home

---

