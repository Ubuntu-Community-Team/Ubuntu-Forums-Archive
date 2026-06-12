---
title: "Xubuntu Install Partitioning"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by jerrylamos on 2007-05-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				A number of posts ask about partitioning with Xubuntu Feisty 7.04.  Here's my suggestions:

There is a partitioner in Install, but it is somewhat limited in function.  In particular on Xubuntu Feisty 7.04, the install partitioner can't delete or new or resize.  It can edit however.

By the way, Microsoft likes (if not demands) to be the first partition on the first hard drive.  Best leave it alone if you are set up that way.  It can be resized smaller if in Windows you do Start Programs Accessories System Disk Clean, and then Defrag.  (that's from memory, I don't boot Windows much).  It also helps to make paging 0 if you have enough memory.

I get the best results for myself if I boot CD Live and then do System, Administration, Gparted.  Depending on which Ubuntu you have, there may not have been enough room for Gparted on the CD, in which case still on CD Live do Applications, Add/Remove, Search, Gparted and install the package, yes it's installing on CD Live which is good until shutdown.

Bring up Gparted and in the upper right corner are arrows so you can select which drive you want for Ubuntu.  You'll need a swap of about 512 MB to 1 GB, and a Ubuntu partition of 4 GB at least on up to end of disk.  Usually on the desired drive, you delete any partitions  from the end of any Microsoft partition to the end of the disk, and then create a new partition of desired size (leaving room for a swap), select ext3 format.  You then create a partition for swap, select swap format.

Just to be safe, reboot CD Live.  On Boot Selections, push F1 and then F6.  You should see options like "noapic nolapic".  Push escape to get the boot options screen, then F6 so you can edit the Boot Options.  Add noapic nolapic to the end of the line.  It is sometimes informative to remove the word "quiet" in which case expect a snowstorm on the screen as Ubuntu tries all possible configurations to see which work.

FYI, this is a two hard disk four boot system, Windoze + three different versions of Ubuntu.  Edgy 6.10, Feisty 7.04, and parts of Gutsy 7.10.  I allow about 20G for each which gives me lots of room for downloading Linux CD's either new versions of Ubuntu or comparison competitive Linux's.  I like having at least two Linux partitions, one for a Linux that I'm familiar with, and one to test a new (or new to me) Linux.   One swap can be shared between them.

If you are using Ubuntu Feisty 7.04, there can be some race conditions as Ubuntu tries to speed up boot by doing things in parallel.  Post back here if you have difficulties, perhaps one of us will have seen your situation.  

By the way, I recommend "The Official Ubuntu Book" for people new to Ubuntu from your bookseller or Amazon.  Also, do a Google search on "Ubuntu user guide" depending on how much stomach you have for plowing thru "helpful" on-line info.

Cheers, Jerry

---

