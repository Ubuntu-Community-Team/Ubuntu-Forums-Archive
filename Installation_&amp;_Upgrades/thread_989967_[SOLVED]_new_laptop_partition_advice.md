---
title: "[SOLVED] new laptop partition advice?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Donalb on 2008-11-22
Hi all, 
I've been dual-booting XP & 8.04 for the past 9 months on my 5 yo Dell laptop. 90% time Ubuntu/10% XP.

I finally took the plunge and got a new Dell latitude. (no Ubuntu option from Dell in Ireland I'm afraid).

Anyway, I've got a 120 hdd with Vista (didn't want Vista but that's another story). Sent incorrect size hdd, waiting for 200 GB replacement, but I assume general partition layout will be the same, so lets work on the basis of the 120gb.

Currently the Hdd comes with 3 partitions:
1: Fat16 133 MB initial partition /dev/sda1   ( i dunno what it is maybe diagnostics??)
2: ntfs 10GB <RECOVERY> partition /dev/sda2
3: Main ntfs Vista partition 101.65GB, boot flag.

From my previous Ubuntu experience, (not a power user but comfortable trying/following most instructions), I'd like to put in a Shared ext3 home&data partition (ala Psychocats reccommedation, [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)),
However with already 3 partitions I don't how to do this as it would mean 5 primary partitions which isn't possible (according to GParted).

I'd like some suggestions from the mavens out there.

In GParted I can reduce the 10GB RECOVERY partition to 5 GB. This will create a new 5 empty partition between the new 5GB RECOVERY, before the current VISTA partition. I can create a ext3 /home partition on this.
However that's 4 partitions so I can't then split the main remainig large VISTA partition to VISTA & Ubuntu.
Also in GParted, I don't if the sequence of partitions that hows in the main window is in any way relevant.

Any suggestions? if I'm not clear on any of this sorry. I can explain further as necessary.

Regards
Donal
Ireland

---

### Post by habtool on 2008-11-22
Use gparted to Split the large vista partition.

Use the free space made from that into a extended partition with gparted.

Then in the extended partion make:
A swap space
a root/ubuntu partition
and leave the rest in maybe as fat32 or ntfs if you need to share data with vista.

Home this makes sense

---

### Post by Donalb on 2008-11-22
Cheers Habtool! 
Yes. it does make sense. Making it an extended partition solves the primary partition restriction. Thanks.

Looking a the current large partition VISTA & apps take up 34GB!!!!!! With no data yet. So I'm giving it 44GB approx, leaving 59 approx for the extended  Ubuntu & Shared partitions.

Ok so I've put 2GB for the swap? Valid size? (New laptop has 4GB RAM..yahoo, but that VISTA pig seems to need it).

What about 10GB ext3 for the Ubuntu partition?
And the remaining 40gb as the ext3 /home (and therefore VISTA shared also)?


Any
Regards
Donal
Ireland

---

### Post by Bucky Ball on 2008-11-22
There is a bit to say about all this bit getting tired. As for the recovery partition, it should be the case that you can make a recovery cd/dvd to back that up. It has the Vista installer so good idea to make that cd! Really dumb idea on the part of manufacturers in my opinion. Rather than send a recovery cd, they let you burn one off yourself. Ta.

Anyway, if you reckon you don't want Vista, wipe the lot and start from scratch; cup of tea, piece of paper and pencil and you might come up with something like this:

/
/boot
/home
/music
/video
/pics
/documents
/swap 2Gb (with that much ram you probably won't even need this - once RAM gets over a couple of gig, former rules don't apply)

You choose the sizes and partition names and take it from there. Just remember, if the drive crashes and you have OS, apps and personal data mixed together on the same partition, you have little hope of recovery (although some). You can retrieve more effectively from undamaged partitions naturally. Also, if you want to install new OS, you can kill the OS partition and that's it. The stuff you want to keep is on different partitions entirely. :)

ps: and yes, they give Vista that amount on my HP also, 34Gb, but I don't reckon it needs that. I have removed a lot of the rubbish that bloats it and have it down to about 27Gb. I am rejigging things over christmas so gonna find out what I can squeeze with the bare minimum.

---

### Post by habtool on 2008-11-22
If you going to keep Vista, then don't make the new shared partition ext3.

Also I would not share my home with Vista.

I would say you must make at least:
Swap
Root (you can have a / and a home in ext3)
Shared (I would say fat32 or NTFS)

Not sure the size of the swap, i think i read that if you suspend/hibernate, then it may need to be the size of the physical memory, but I am not 100% on this.

---

### Post by Lars Noodén on 2008-11-22
I'd strongly recommend a separate /home partition.  Otherwise, as habtool said.  

If you have to retain Windows, at least upgrade to XP to improve performance and maintenance.

---

