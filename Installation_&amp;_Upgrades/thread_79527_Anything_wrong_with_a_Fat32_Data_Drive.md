---
title: "Anything wrong with a Fat32 Data Drive?"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by bradroger on 2005-10-20
I was reading a thread about having your /home directory as a fat32 drive and that there were problems with it (namely permissions).  Instead of this I was thinking it might be nice to keep all my data mounted separately on a fat32 partition for easy access in windows but I was wondering if there were any problems with linux and fat32.  I was going to make my ubuntu partition about 10gigs, then a data partition of about 70gigs for music, movies, documents...basically everything.  Does linux have any issues with large files in fat32?  Would it be slower or less efficient?  I've heard of things like journalling in ext3...does this come into account at all?  Linux has to have its own file system for a reason...what's wrong with fat32?

Thanks for the help!

---

### Post by stuporglue on 2005-10-20
As you mentioned Fat32 doesn't handle permissions. It also can't handle files over 2GB, which may be a problem depending on the size of your videos. There's no journalling, which makes it slightly easier to become corrupted if your computer crashes while accessing it. 

If it's for the purpose of sharing with Windows though, it's probably the best way.

---

### Post by matthew on 2005-10-20
For what you want to do Fat32 would be a very good choice.

---

### Post by bradroger on 2005-10-20
Well, I'm switching from XP to ubuntu today...I was hoping I won't need to access anything from windows!!  I was looking at windows ext3 support...since I (hopefully) won't be accessing it all that much from windows maybe I'll just leave it ext3.  Whatever...doesn't seem like too big of an issue.

Thanks for the replies!  Wish me luck with my install today!

---

### Post by SickTwist on 2005-10-20
If you're starting from scratch, it is a good idea to put /home on a separate partition. Use reiser or ext3 for /home but *not* fat32.

There are many problems with fat32 but unfortunately it is the only common read/write link (as far as filesystems go) between Windows and Linux at the moment. So if you use fat32, use it on a separate partition that is just for data to be shared between both operating systems. As others have said, it is easier for data to become corrupted if it is stored on a fat32 filesystem.

Best of luck with the install!! :D

---

### Post by audax321 on 2005-10-20
I would recommend against FAT32 if you are making a *permanent* switch to Linux. I had my computer running WinXP and Ubuntu and the FAT32 drive was a huge help in sharing files. BUT, when I got rid of XP everything went downhill. Right now the drive is an undefragmented pile of crap. Now, I have to sit down this weekend and backup almost 150GB of data and reformat it to ReiserFS. I would recommend just using either rfstools or the ext3 utility for Windows and giving the drive a Linux partition if you think you will be making a more or less permanent switch to Linux.  That way you still have access to the drive if you need anything while in Windows (which I personally never do anymore since switching to Ubuntu) and don't need to worry about defragmenting (and storage drives get defragmented horribly fast since you're constantly storing/removing things).

---

