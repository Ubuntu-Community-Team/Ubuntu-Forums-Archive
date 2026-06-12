---
title: "installation error and addtional question"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by symb1ont on 2007-05-24
I went to install Ubuntu last night and recieved a complete system lockup when the Linux Floppy module went to install/load during the install process. I do not have a floppy drive and everything floppy related is disabled in BIOs.  System completely  froze and I had to cold boot.  I realize it could be a million different things but any suggestions would be appreciated.

Also, I'm trying to install this dual boot.  My system has 2 Sata drives on which the first I have XP installed so it's my C drive.  I also have two IDE drives and the first IDE is what i want to dedicate to Ubuntu.  Dual boot with installs on completely seperate drives.  During the Ubuntu install there is an advanced option to choose where to install the bootloader and by default it says (hd0) - do I have to change this to something like (sd0) since the first sata is where my windows boot partition is?  Still kinda new to this.

Thanx

---

### Post by jerrylamos on 2007-05-24
There is a partitioner in Install, but it is somewhat limited in function.  And by the way, Microsoft likes (if not demands) to be the first partition on the first hard drive.  Best leave it alone if you are set up that way.

I get the best results for myself if I boot CD Live and then do System Administration Gparted.  Depending on which Ubuntu you have, there may not have been enough room for Gparted on the CD, in which case still on CD Live do Applications Add/Remove Search Gparted and install the package, yes it's installing on CD Live which is good until shutdown.

Bring up Gparted and in the upper right corner are arrows so you can select which drive you want for Ubuntu.  You'll need a swap of about 512 MB to 1 GB, and a Ubuntu partition of 4 GB at least on up to end of disk.  Usually on the desired drive, you delete any partitions (including all the data!) and then create a new partition of desired size (leaving room for a swap), select ext3 format.  You then create a partition for swap, select swap format.

Just to be safe, to install reboot CD Live.  On Boot Selections, push F1 and then F6.  You should see options like "noapic nolapic".  Push escape to get the boot options screen, then F6 so you can edit the Boot Options.  Add noapic nolapic to the end of the line.  It is sometimes informative to remove the word "quiet" in which case expect a snowstorm on the screen as Ubuntu tries all possible configurations to see which work.

FYI, this is a two hard disk four boot system, Windoze + three different versions of Ubuntu.  Edgy 6.10, Feisty 7.04, and parts of Gutsy 7.10.  I allow about 20G for each Linux which gives me lots of room for downloading Linux CD's either new versions of Ubuntu or comparison competitive Linux's.  I try a new one out before committing myself, and on the same system it's easy to copy over all your files & bookmarks & graphics drivers & such.

If you are using Ubuntu Feisty 7.04, there can be some race conditions as Ubuntu tries to speed up boot by doing things in parallel.  Post back here if you have difficulties, perhaps one of us will have seen your situation.  

By the way, I recommend "The Official Ubuntu Book" for people new to Ubuntu from your bookseller or Amazon.  Also, do a Google search on "Ubuntu user guide" depending on how much stomach you have for plowing thru "helpful" on-line info.

Cheers, Jerry

---

