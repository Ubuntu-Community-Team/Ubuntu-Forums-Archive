---
title: "Restoring a NTFS partition after cancelled reformat to Ext3"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by JSchoeck on 2007-11-14
Hello,

after searching the forum and reading many threads I still have a problem.

I wanted to install the latest Ubuntu as dual boot on my XP system (and since the "guided partitioning" didn't show up for some reason I screwed up). Instead of resizing my NTFS data partition (D:) I started to reformat it with the Ext3 file system. After about 10 seconds I realized what I was doing and hit cancel. The installer / GParted (don't know what exactly) crashed and D: wasn't mountable any longer. When booting XP (from C:) it's not recognized either. Even chkdsk can't run on it and pretty much every program I've tried tells me that there's a broken/missing file structure.

Maybe I'm doing something wrong, but even TestDisk and GParted don't seem to help me.

What I want it ideally to restore the partition in its entirety. If that doesn't work then at least restore a part of the files.

Any ideas?
Thanks in advance,
Johannes

PS: With FS-driver I can actually access D: under XP and it shows only an empty "Lost & Found" folder. Would it be a good idea to reformat it to NTFS and use a regular file restoring program?

---

### Post by bulldog on 2007-11-14
Don't think you can reverse the operation,but maybe there's software available to get some data from the disk.

But I have to say I'm not very confident you can do it your self.

---

### Post by JSchoeck on 2007-11-14
Well after trying several programs to fix the partition table somehow I decided that the data is not important enough to waste so much more time on it, considering that it's probably not possible to restore the partition as a whole anyways.
So I reformatted it to NTFS (which was really quick, about 2s) and am now using a regular "post format" recovery tool which is finding files.

Thanks for your post bulldog.
@Mods: This topic can be closed.

---

