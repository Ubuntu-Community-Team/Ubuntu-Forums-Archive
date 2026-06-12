---
title: "Is the GParted Live CD safe for 64-bit Gutsy users"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Dark Aspect on 2008-01-22
Would the Live CD of Gparted be safe with Gutsy and would the 64-bit thing have a complication?I need to resize my ext3 drive by two GBs.I was waiting to use my SATA hard drive (which is where ubuntu is) for the pagefile for windows on an IDE for speed.Any thoughts to make sure I don't end up with a brick.

I already plan on backing up the extremely important stuff.I was just wanting to avoid the pain of reinstalling an OS.

---

### Post by imT on 2008-01-22
you didn't say how big is your hard but i suggest a clean install instead of resize because it takes hours....:confused: as for the x64 i don't know.:popcorn:

---

### Post by Dark Aspect on 2008-01-22
> **imT said:**
> you didn't say how big is your hard but

I am sorry but that made no sense at all to me........I am amusing you mean Hard Drive,Its 320 GB.Times not really an issue in computers to me I can just leave it up all night or go eat something while the application it running.

---

### Post by imT on 2008-01-22
:D i resized a 60 GB partition a few weeks ago and believe me if you're planing on eating you'll gonna be a chubby man next time you reply... :D
you can leave it over night but 4 me, after my similar incident, is much easier to reinstall (plus i can browse during the installation.

---

### Post by Herman on 2008-01-22
It's generally no problem if you're resizing a Linux partition from the right, or the 'end' of the partition. That's pretty quick and easy, it only takes a minute or two.
Partitions containing a FAT32 file system, also, are quick to resize from either end of the partition or move around on the hard disk.

The left-hand end of a partition containing a Linux file system is not simple or easy to move. It contains all the important file system blocks. Until not so long ago it was not considered practical to try to move those, or maybe impossible even. Nowadays, GParted can do it.  If you decide you need to resize your Linux partition to the left it will take a long time, but at least it's possible now, and some people need to sometimes.

If you need to move the start blocks of a Linux file system another way to do it is to copy and paste the whole partition. It's faster to do that if you remove all the data first, (back up onto some other media). 
Then shrink the partition as small as you can and copy+paste it to a second location, somewhere else on your hard disk out of the way. (Temporarily).
Delete the original partition containing the operating system.
Copy the temporary copy of the partition and paste it to a third location, this time make sure it's where you finally want it to remain.
Resize the partition to the size you want and put whatever data back in that you need.
If you use this method your partition will have the same partition number again as it had originally, so you won't need to go editing any files, such as /boot/grub/menu.lst. It should still be correct.
I can't remember if you will need to re-install GRUB again, I think maybe not, I'm not sure.

It takes about ten minutes probably to copy the empty operating system each time, (two times), and about half an hour to re-install anyway. 
It depends if you have a lot of installed software and have invested a lot of time and careful thinking into getting everything set up and configured how you like. 
For some it might be easier to re-install, for others it might be better to copy the partition and paste it, for others it might be better to let GParted move it, even if it takes overnight.

GParted is quite fast though, if you're only resizing from the right. Most of the time that's all most people need to do.

Regards, Herman :)

---

