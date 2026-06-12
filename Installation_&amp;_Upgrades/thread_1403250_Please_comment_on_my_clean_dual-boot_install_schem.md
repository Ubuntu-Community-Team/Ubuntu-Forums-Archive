---
title: "Please comment on my clean dual-boot install scheme"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by jimwsea on 2010-02-10
Hello, and thanks for the forum.

I have a older Dell Inspiron 8600 with an 80 gig hdd and 2 gb memory.  I plan to reformat and start a Ubuntu/Win Xp dual boot system from scratch.  It will be used mostly for document writing, mail and web surfing, and photo editing.  Below is my plan to partition the single hard disk....I invite comments.[-o<

Some questions.  
1. Do I need a separate Linux boot partition, or will install place boot in root directory? (I may want to upgrade to a newer Ubuntu when it is released.)
2. Do I need three primary partitions, or just make the Win XP partition primary only?
3. Are the Linux partition sizes about right?
4. Still not up to speed on ext3 vs ext 4....Is ext 4 safe enough for home partition?

primary.......win xp..............."win".........25gb.........ntfs.......for OS and programs
primary.......win page file..."pagefile"......4 gb.........ntfs......win page file/swap file
primary.......Ubuntu root.......... / ...........15gb.........ext4......boot/root
*extended*
                ..................Ubuntu swap......swap.........2 gb........swap    
                ..................Ubuntu home.... /home .......15gb........ext 3.....Linux programs
                ..................ALL files...............................18gb........ntfs.....     shared files (pix, music)

Thanks
[SIZE=2]
[/SIZE]                       [SIZE=2]
[/SIZE]

---

### Post by jocko on 2010-02-10
1. Ubuntu does not need to have any /boot partition (/boot is on the / partition by default).
2. Windows is the only thing that needs to be on a primary partition, so you can make all the other partitions in one big extended partition.
3. The sizes look ok to me.
4. I've used ext4 since jaunty and have never had any problem (but others have had some problems, so someone else will probably know more than me on this subject).

---

### Post by murderslastcrow on 2010-02-10
Ext4 has had extensive work since Jaunty's release, so if you're installing Karmic there should be no more risk involved than with Ext3. Also, I've tested it personally on a wide range of computers, low and high specs, new and old hard drives, and never experienced an issue even with lazily done hard-resets.

I trust would trust Ext4's stability far above that of NTFS. Then again, I guess this isn't saying much.

---

### Post by jimwsea on 2010-02-10
Thanks for the quick replies.  I now have my next weekend project!

---

