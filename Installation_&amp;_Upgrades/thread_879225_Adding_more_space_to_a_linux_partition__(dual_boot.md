---
title: "Adding more space to a linux partition?  (dual booting windows with linux)"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by cex on 2008-08-03
Okay, so I recently was experimenting with Wine, (getting close to the great migration from windows)  and I was going to install Call of Duty 4:  Modern Warfare.  I have all the system requirements and everything, except the HD space.  I have over 250 gb left on my Windows partition, but not thinking straight, when I made my linux partition I only gave it 10 gb of hard drive space.  Now when I try to install Call of Duty 4, I can't because of the lack of space.

So I was wondering, is there any way to add more space to my linux partition without having to completely delete the partition and make a new partition with larger space and reinstalling linux?  

If so, could anyone give me a decently-detailed description of how to do so?

Your time is much appreciated,



John

---

### Post by ibuclaw on 2008-08-03
Boot into the Ubuntu LiveCD and open up the Partition Manager.
Then shrink the NTFS and grow the ext3 drive as fits, then apply the changes.

That is all it takes.

Oh, and it is probably best to [check the compatibility]("http://appdb.winehq.org/") of the app first before you try it.

Regards
Iain

---

### Post by cex on 2008-08-03
How do you open up the partition manager from the live cd?  I booted in from the live cd, and on the desktop the only thing that's there is install, and I don't want to reinstall, I just want to make my linux installation have more space...

Thank you for replying :)

---

### Post by ibuclaw on 2008-08-03
Hi, sorry to keep you waiting.

If you are using Ubuntu, as opposed to it's variants.
Go into "System -> Administration" in the Gnome menu and you'll see it.

Else, press **Alt+F2** and type in
```
gparted
```
in the run app textbar.

To resize is very simple. The GUI interface is more than enough for you to see what you are doing.

Regards
Iain

---

### Post by Pumalite on 2008-08-03
Don't forget to BACKUP everything before you start. I'd use Gparted Live CD that works with unmounted drives/partitions.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn iso to disk and boot from it.

---

### Post by xen-uno on 2008-08-03
That's where Win has it over Linux IMO ... the ability to easily direct application installs to any drive. You can keep your system drive lean & clean that way. I've got a ton of apps installed in XP but since they're on a different drive, I've used only 5.5 GB of the 60 available. Appears as you would have to alter the app's install script to do same for Ubuntu apps. Correct me if I'm wrong ...

---

### Post by dharmaturtle on 2008-08-08
The 60Mb of unallocated space issue is what's troubling me. I, too, have some discontinuous blocks of data on my drive, with a lot of space unused. I've tried defragging this NTFS drive several times, but there is a large set of blocks deep into my hard drive that I am unable to move, no matter how much I defrag, compact, or whatever. (I'm using UltraDeFrag 1.4)

I've made the virtual memory size as small as possible (2Mb), but that changed nothing.

Any ideas? Can it be that Microsoft has deliberately done something to insure that no one can install Linux on part of a drive? I want to use at least half of my 80 Gig drive for Ubuntu, but I can't create a decent-sized partition for installation. (I *don't* want to wipe out Windows and start again; that would entail days of rebuilding Win 2000, reloading programs, then getting upgrades again -- you know the drill!)

---

### Post by Pumalite on 2008-08-08
Boot a Live CD and post a screenshot of Gparted

---

