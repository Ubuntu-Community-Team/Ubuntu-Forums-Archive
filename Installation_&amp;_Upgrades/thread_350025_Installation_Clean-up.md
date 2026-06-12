---
title: "Installation Clean-up"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by nycoroner on 2007-01-31
Hey all,
First time Ubuntu/Linux user, 4th day and loving it so far. I installed Unbuntu from a Live DVD that came with some Linux mag (6.10) on a spare 2.5gb hd, hdb1,  that i had sitting around. I installed Ubuntu after a virus destroyed my windows XP installation and I had no media to reintall from without having to wipe clean first (OEM XP was on desktop). The main HD is a 100gb, hda1, that still has all my old documents, photos, and music on it (which is why I installed Linux, so I could still salvage them, have successfully mounted this hd as /media/windows per the instructions I found in a search of this forum). The 2.5 gig i installed Ubuntu on is completely full now thanks to the install. My questions:
What can I delete that is left over from the install to have more space on hdb1? Can I install programs to hda1 which is a  windows vfat partition (40gb free) and keep all my old files there also? The add/remove utility doesnt give me an option of directories to install to. :confused: 
Thanks in Advance,
Chris

---

### Post by taurus on 2007-01-31
It's not a good idea to install Ubuntu on fat32 filesystem.  Bad things can happen and will happen.  If you want to clear out some space, boot into recovery mode from GRUB and run

```
aptitude clean
df -h
```
The second command will tell you how much space you have left on /.

---

### Post by nycoroner on 2007-01-31
Thanks for the quick reply. During the installation of Ubuntu, the 2.5 was formatted at partitioned by Ubuntu to whatever filesystem it uses (not NTFS, but nDfs?). So as far a ubuntu is concerned was it basically a clean install? or will the file system of the bigger, master hd (which ubuntu does nothing with except allow me to access files on it) conflict with the install on an essentially "new" hard drive?
Free space on the hard drive Ubuntu is on is 1.36 mb...less than a floppy!

---

### Post by taurus on 2007-01-31
If you picked the default, the filesystem Ubuntu is on would be ext3.  And yes, 2.5 is probably how much it needed to install Gnome.  So, you can either reinstall it on a bigger harddrive/partition or start removing a bunch of apps to free up some space.

---

