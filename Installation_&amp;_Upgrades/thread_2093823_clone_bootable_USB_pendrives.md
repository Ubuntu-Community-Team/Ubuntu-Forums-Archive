---
title: "clone bootable USB pendrives"
date: 2012-12-11
forum: Installation &amp; Upgrades
---

### Post by JayIyer on 2012-12-11
I tried ubuntu(12.04) on a 32GB USB stick. Love it. Have now put more stuff on it and running out of space. So I wish to expand to 64GB (or more) USB stick. (plus maybe have another USB stick as a backup). So, how do I go about cloning to avoid having to start from scratch and configure and install everything yet again on bigger usb stick. ( I have installed numerous packages and software etc)
Will "dd" work ? (I need to be able to have the extra space usable when I go from 32GB to 64GB stick; somewhere I read it is "unallocated" so it got me worried).
Thanks a lot

---

### Post by C.S.Cameron on 2012-12-11
I have had good success using dd to clone USB drives.
I have used gparted to expand the partition afterwards.
The only problem with dd is that it can take a long time and does not have a monitor to let you know it is still working.

Edit:

Alternate 1, you can use the unallocated space to make a separate home partition and rsync your home data to it. Grsync is a good rsync GUI.

Alternate 2, you can shuffle stuff around and make the first partition FAT32 or NTFS so the data on it can be read by Windows. You might need to reinstall grub which is easy using the Live CD or Live USB.

---

### Post by oldfred on 2012-12-11
I have never used dd to clone a drive.

       from caljohnsmith post #7
> I would recommend using "dcfldd", which is basically dd with more features; it has the really useful feature of showing the copying progress
[http://ubuntuforums.org/showthread.php?t=1033712](http://ubuntuforums.org/showthread.php?t=1033712)
[http://www.anti-forensics.com/disk-wiping-with-dcfldd](http://www.anti-forensics.com/disk-wiping-with-dcfldd)


I prefer a clean install, copy /home and export list of installed apps & reinstall. 



If you happen to have both flash drives plugged in at same time that are the clones you will have issued with duplicate UUIDs. You can only use one at a time after cloning.

---

### Post by G._Artigue on 2013-10-22
I've just had the most bizarre experience. I've been using Xubuntu 10.10 in a live, persistent, bootable pendrive for around three years now. On my desktop PCs and laptop I use a myriad of OSs, like Ubuntu 13 with KDE, Xubuntu 9, Linux Mint 15 with KDE, Linux Mint 15 with Cinnamon, but also W. Vista and 8. The installed OS in my external USB drive never gave me a single problem, so I stuck to version 10.10 and never attempted an upgrade.
Never in my life have I cloned a hard disk or partition.
Recently I begun learning some Clonezilla. All my attempts to clone internal hard drives have been major failures, I can't understand why. But hey, just for the heck of it, I tried to clone my three-year-old USB with a live, persistent, bootable Xubuntu 10.10. Not only did I succeed in making the image, I succeeded also in restoring it into a pendrive. The pendrive is bootable, it is an exact copy of the old OS just as it was before taking a picture of it. Even my passwords were restored. All which was meant to happen, naturally.
Except for one weird feature. The bootable pendrive used to start with a menu asking for the language, followed by other menu asking the user if they wanted to boot from the pendrive, to install Xubuntu to the internal hard disk, to check for memory errors, or to boot from hard disk. Well, what do you know, now after the cloning with Clonezilla those two menus are gone, or rather seem to be black (black text on black background) because I still can navigate through those menus, only blindly.
What happened?
How could I restore those menus?
I'd like to stress that the cloning succeeded in all other respects.
Thank you very much.

---

