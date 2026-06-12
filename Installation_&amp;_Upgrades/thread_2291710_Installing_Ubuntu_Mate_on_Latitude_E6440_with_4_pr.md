---
title: "Installing Ubuntu Mate on Latitude E6440 with 4 primary partitions"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by ken64 on 2015-08-22
Hi. My employer lends me a dell 6440 latitude laptop. It has 1TB hard-drive w. two windows partition ( OS + D: for data and sort)

So I decided to play around and install the newest mate. Upon installing I found out there was 4 partitions already (primaries).

the 3rd one is Windows Loader
the 4th one is FAT 16 w. no labels at all.

[ATTACH=CONFIG]263989[/ATTACH]

I could have removed the FAT 16. If it were just some dell softwares, I thought..
And recreate the partition from there.

But I was worried, as it could be dell system software / even bios like / crititical for the running of the laptop &/ windows.


I surely dont want to ruin the laptop. And spend lots / hard time recovering /reconfiguring from the old windows in case of failure.

Anyone has similar experience of having same laptop etc...
and installing Ubuntu

Thanks

---

### Post by Mark Phelps on 2015-08-22
THIS has me concerned: > Hi. My employer lends me a dell 6440 latitude laptop. 

DId they lend it to you for work; or did they lend it to you to play around with it?

Installing a new OS always comes with risk of trashing the existing system.  So BEFORE you do that, it would be best to check with your employer and find out (1) it's OK to play around with installing other OSs on THEIR machine, and (2) if you do trash it, they'll recover it.

---

### Post by ken64 on 2015-08-22
Well, I dont I am gonna get a straight easy answer for that for sure.. not likely one...

well it seems like from google : fat16 partition dell latitude laptop
It's only a dell utility tool, nothing like BIOS etc. It's just a tool that can be booted from BIOS menu.. which i will try to find out ltr perhaps.

Also from : [http://windowssecrets.com/forums/showthread.php/128027-How-can-I-delete-Dell%27s-OEM-partition](http://windowssecrets.com/forums/showthread.php/128027-How-can-I-delete-Dell%27s-OEM-partition)
it somewhat give many details about the dell partition and also the Windows loader partition which they all say can be deleted.

But again it's unsafe perhaps to risk it / null the warranty and have my employer really pissed.

---

### Post by ken64 on 2015-08-22
also from google : is it safe to delete win7 loader partition

i found this thread :[http://ubuntuforums.org/showthread.php?t=1899295](http://ubuntuforums.org/showthread.php?t=1899295)
which says that it's safe since I am gonna use the grub to boot from anyway...

--Well from : [http://www.howtogeek.com/192772/what-is-the-system-reserved-partition-and-can-you-delete-it/](http://www.howtogeek.com/192772/what-is-the-system-reserved-partition-and-can-you-delete-it/)
it says not to do that..

---

### Post by yancek on 2015-08-22
I'm not sure what you are referring to with "loader partition".  windows 7 usually has a small (100-200MB) partition marked active at the beginning of the disk.  This partition is the boot partition and if you delete that, you won't be able to boot windows.

---

### Post by ken64 on 2015-08-30
Well i decided to install on my older laptop and not to mess w. my work laptop.  Tried the mate 15.04.. it's not that great to be honest imo. I like my Xubuntu 14 better: stable, lighter, more powerful. W. mate my older laptop run bit hott.. Security wise seems like Xubuntu is better also.. being a more stable release. Not sure..  But it's not that bad, other than my laptop Core2Duo runs hot under linux... which a bit weird That's bout it.

---

