---
title: "About to take the plunge - from dual boot w XP to single boot Ubuntu"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by tenzindorje on 2007-05-04
I currently have a dual boot setup on two hard drives, where I've migrated all my data from NTFS and FAT32 partitions to EXT3 (and have the Windows EXT3 driver installed, just for migration purposes). The setup looks like this:

Internal 40GB
HDA1 (C : )   Windows XP system
HDA2 (D : )  Windows programs (will be blown away)
HDA3             Ubuntu 7.04
HDA4             Linux Swap
----
External USB 250 GB
SDA1              Documents (EXT3) - the old My Documents folder, with two users
                      |---- Kenny
                      |---- Cheryl
                      |---- Common
SDA2             ITunes (EXT3) -- works Ok with Banshee to download to IPod
SDA3             Windows programs (NTFS - will be blown away)
SDA4             Common (EXT3) -- using it for temporary space now to move things using Gparted

I've got the 7.04 disk and the Gparted disk.

What is the easiest way to 
1) make the system single boot, so that the entire Internal 40GB drve has only Linux and swap; and
2) turn SDA1 (the old My Documents) into the new /Home directory?

I think I can leave SDA1 as one /Home partition with two users, and move the Common stuff to SDA4,
but first blow away SDA3 and SDA4 and then make one big partition - this is where stuff like photos will go.
SDA1              /Home for two users
SDA2              ITunes
SDA3              Common

The tricky part is the first drive. Is it safe to use Gparted to make HDA1 and HDA2 one new Linux partition, then copy the Linux on the old HDA3 to the new big HDA1? It seems that this will confuse both Grub and Linux trying to find its swap partition.

Or would it be better to just reinstall Ubuntu from scratch, telling it to use the entire internal drive for itself (I haven't put much stuff there yet, so it would be easy to reconfigure). Can I tell it to use the SDA1 partition as /Home? Do I need to do anything to SDA1 beforehand?

Thanks --- this is the critical part of the migration.** I am now ready to switch completely to Linux**, but I want to do it with as little downtime for my wife as possible (I don't mind hacking, but she just wants to be able to surf the Internet without any weird error messages).

:KS :KS :KS

---

### Post by thayerw on 2007-05-04
First off, congrats on taking the plunge.  I did it last year and I haven't looked back.  My wife switched just last month too (to be fair, its the second time she's done it) and we're both running Feisty Fawn despite a few glitches along the way.

My suggestion would be to definitely start over from scratch with your 40GB sda. I always like to wipe the entire drive and start with fresh partition tables--its the only way you'll be certain nothing got screwed up by windows or in between installs, etc.

Granted, I have a 100GB sda so yours may vary a bit, but this is how I split mine:

sda:  (100GB SATA Internal)
sda1 Ext3 8GB / (root) 
sda2 swap 2GB
sda3 Ext3 85GB /home

sdb: (160GB USB External)
sdb1 Ext3 160GB /media/external

Of the 8GB for root, only about 3 GB of it is actually used, the other 5 GB is free space.  It's safe to say that I could've made it 5 GB and I would still never fill it.  I have a lot of 3rd party apps installed on my system, so root is about as full as it will ever get.

As for the swap, I probably wasted 1 GB there as well.  I have 2 GB of RAM and as far as I know the system has never had to use the swap space.  Again, if I were you I would consider 1GB at most for swap.  Also, I placed the swap between root and /home because I read somewhere that it could improve seek times, but in all reality it probably doesn't matter.

The rest of my everyday stuff goes to my /home partition, including music, movies, games and even /tmp.  I redirected /tmp to my /home partition so I could cache large DVD ISO's without worrying about the 8GB on root.  This is easily accomplished by doing the following from a terminal:

```
sudo mv /tmp /home/tmp
sudo ln -s /home/tmp /tmp
```

I use the single Ext3 partition on my 160GB external drive to house all my backups and miscellaneous stuff I don't need all the time.  I see no reason to partition it into several smaller parts because then you're limiting what you can do with it.

So... my advice for you would be something like this:

hda1 5GB to root /
hda2 1GB to swap
hda3 34GB  to /home (although you'll really only have about 31GB to /home)

---

### Post by thayerw on 2007-05-04
Re-reading your post again, I see some things I missed... 

I'm not sure that placing the /home partition on an external drive is such a great idea.  I guess it really all depends on your operating environment and your routines.  I remove my external drive from time to time, sometimes to a different location altogether.  That would make your /home folders inaccessible if you tried to use your computer--I'm not even sure if you could log in. And what if the power supply dies on your external?

I try to keep everyday items in /home on my primary drive, and then I just run a backup (rsync) every week or so to mirror my /home/username with a folder on the external drive.  This way if either drive dies, I have the most valuable data backed up.

Obviously though, if you have 200GB of data on your external, you'd have to carefully consider what to put on your HDA and what to leave on the external.

Either way, it sounds like you've done your research and I hope this advice can be of help.

---

