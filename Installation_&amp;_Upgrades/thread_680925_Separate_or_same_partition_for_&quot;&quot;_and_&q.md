---
title: "Separate or same partition for &quot;/&quot; and &quot;/home&quot; for install?"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by dirk_diggler on 2008-01-28
Hi All

I will be installing Ubuntu 7.10 for the first time on my comp.  I am a complete novice with this, but I have been reading up in the forums about it.  

I just want to pick your brains regarding whether I should mount the "/" and "/home" on separate partitions? or the same?  I'm just not too sure what the advantages are.  It seems that having them separated will allow me to keep my current settings, but it looks like there is still a lot of manual tweaking to be done for this to be true.  If I keep them separated, and in the future upgrade from my current version (7.10) will it be better if I just keep them separated?

I ask because I will be partitioning my new hd and need to know how many partitions to create (and what sizes).  I want to install Ubuntu, OpenSUSE, and maybe Fedora, so I am somewhere between 3 and 6 ext3 partitions (plus one more for the swap).  If / and /home on the same partition, then I will make 3 ext3 partitions, and if separate, then I will make 6 ext3 partitions.  I have a 250 GB hd, and would like to keep the rest open for file-sharing for Linux and XP.  XP is already installed on the current (and separate) hd.  

I was thinking of making 6 partitions, each 20 GB, and one 1GB for swap (approximately).  Are these too small, or large?  I have enough room on the hd.

The alternative is a hybrid between the two, where I will have separate / but the same /home mount.  Is this at all possible?  I've read where folks have done this, but I don't know if it is at all feasible.  

Thanks. :)

---

### Post by dreamer.redeemer on 2008-01-28
As far as i know, the benefit of having / and /home on separate partitions is so that you don't fill your drive to the point of making the OS unable to function. I'm new at this too though.

---

### Post by mocoloco on 2008-01-28
For what you list it would be perfect to share one /home partition among them all.  I also like having a separate /home so it I end up doing a fresh install it's easy as pie, all my stuff is just fine.  The real trick is deciding how much space to give each, which is kind of an art in itself.  If it helps, I have 20GB for my root partition, and the rest of my 120 GB drive is /home (and 1.5GB or so for swap I think).  So far even after installing tons of apps I'm only using 12GB on /, so I think it was a good set up.

---

### Post by zvacet on 2008-01-28
If you want to install different distros it is better  to make root and home for each of them,because if thay share same home strange and unwanted things can happened.I think 10GB for root is enough and you want home to be bigger.

---

### Post by perixx on 2008-01-28
I agree to zvacet. I can also confirm the usefulness for separate /home partitions in order to prevent corruption of the root-partition due to a 'HDD overflow' from my own experience... 
Btw.: tried to have several /home-subfolders in the /home partition once, but that was a really ridiculous effort ^^  

If you like to give i a try, here are two references:

**Professionals.**
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
**My own solution with some additional info.**
[http://ubuntuforums.org/showpost.php?p=3706455&postcount=11]("http://ubuntuforums.org/showpost.php?p=3706455&postcount=11")

Be prepared to backup and recover from a mess, though, especially when doing it the first time! 
Oh, and, regarding the root-size: I couldn't do with just 10GB. Installed some gaming clients (UT2004, Doom3, etc.) and do manual compilations  - currently, I got 16GB (6 in use). Space can get scarce during installations (tempfiles), so best take a few more Gig's. But with 20 you should be really out of trouble, I guess.

perixx

---

### Post by bliffle on 2008-01-28
This is verrrry interesting!

But I am a little down the road already.

I have a kinda new IBM T60 that I setup about 6 months ago. It has a 80g HDD and 2G RAM.

These are the partitions:

-sda1 : 10gb XP ("/media/sda1") partition (I use it about once a month)
-sda2 : 4gb linux swap partition
-sda3 : 10gb ubuntu ("/") partition, about 1gb unused
-sda4 : 20gb ext3 ("/media/sda4") about 19.5gb unused
-unallocated 30gb

I guess I screwed up because I wanted to get the "/home" directory on that sda4 partition in order to separate system files from user files. But somehow I didn't do it right so I ended up with all the sys files and user files crowding onto sda3.

I DID leave that 30gb unallocated space for another system, however. So I was half right.

Now I want to put a "mythTVR5F27" system on that 30gb unallocated space and try it out.

Maybe I can fixup my allocation to get the "/home" onto the sda4 partition. Is that possible? Do I just use "mv" or "cp", or should I use something else?

Can I install the MythTV system on that 30gb space, and what should I call it? If it's the 5th partition does that mean it can't be a primary partition? Does that mean I can't use it as a system?

Do I have to change some partition from primary to logical?

---

### Post by perixx on 2008-01-29
Hello...

> But somehow I didn't do it right so I ended up with all the sys files and user files crowding onto sda3. Well, I don't know what exactly you've done, so I can't judge. If you used 'sudo cp' to COPY your /home folder onto sda4 and back to the root of sda3, you can sort out everything by hand, comparing the files/folders with those in /home. Then you can delete stuff you've moved to root by accident. I recommend to use 'gksudo Thunar' for that purpose, NOT 'sudo rm -r/f' or similar(!), for you'll have more feedback on what you're doing. Don't delete any system files/folders, though! 

Should you've 'sudo mv'-ed /home to hda3 and back to '/' of sda3, it's really the best to pick what you need for a backup and re-install the system.  

> Do I just use "mv" or "cp", or should I use something else? I strongly recommend using the 'rsync -au' method described in my post - it preserves all the file permission...

> Do I have to change some partition from primary to logical? As long as you're not gonna have more than 4 partitions all in all, you're fine with primary partitions. But you have to count in EVERYTHING, even 'swap'! I use primary partitions only where really needed when having several partitions: e.g. hda1 primary for XP, hda2 primary containing all other LOGICAL partitions, starting from hda**[COLOR="Red"]5[/COLOR]** (used 2 primaries out of 4).

greetz,
perixx

---

### Post by bliffle on 2008-01-29
So, "swap" can be logical?

And a partition with "/home" can be logical?

Does each bootable system have to be primary?

Does a logical exist within a primary?

If I put the XP in a primary, then the old Ubuntu into a primary, and the new MythTV in a primary, can I put swap in a logical? Where?

---

### Post by perixx on 2008-01-30
Well, 

I don't know the program MythTV, but I see that there are two options: installing it on a Linux or Windows system. I'd say installing it on your Ubuntu system is a good idea - anybody please complain, if having more experience here...
If you install it under Windows, you'll have to record to a NTFS or FAT32 partition, under Ubuntu onto any Linux-compliant file system. MythTV looks interesting... I wonder if it works with a Hauppauge TVR-1300 card... :)
  
XP demands to be on a primary partition. Ubuntu can be completely on a logical partition (including it's swap partition and /home partition). Just start 'Gparted' from a live-CD or 'systemrescue'-CD (that's the name), create an 'extended' partition and then you can create 'logical' partition within that one.

I'd recommend: > 1) primary (hda1) NTFS for XP (at least 20 GB)
2) primary (hda2) VFAT/FAT32 (as much space as you need for games / recorded films / hiberfile.sys and pagefile.sys - at least 80GB)
3) primary/extended (hda3) - (as much space as you need for your Ubuntu + swap system + /home partition - perhaps at least 15+2+25GB)
4) logical partitions in hda3:
logical (hda5) ext3 - Ubuntu
logical (hda6) - swap
logical (hda7) ext3 - /home

**The advantage here:** 
You can store your films from either OS (XP or Ubuntu, where you install it to) and access it without any trouble from either OS, also you can share files between the two OS's). Of course, you could as well use 'ntfs-3g' under Ubuntu (NTFS write-support) and the XP-pendant (filefs or similar, I forgot) to access Ubuntu partitions to spare that 'buffer'-partition hda2. Additionally, you can outsource the XP pagefile.sys ('XP-swap') and hiberfile.sys (hibernation cache) to hda2, protecting the system partition from excessive fragmentation. It's also said to be a little faster/secure - can't say. 

perixx

---

### Post by dirk_diggler on 2008-01-31
Hi bliffle.  I'll take a stab at this...

> **bliffle said:**
> So, "swap" can be logical?
Yes.  That is how I have my system configured.

> And a partition with "/home" can be logical?

Does each bootable system have to be primary?

Does a logical exist within a primary?

Yes, "/home" can be mounted to a logical ext3 partition.  

With linux, you can boot from a logical partition within an extended partition.  An extended partition counts as a primary partition.  You can create **4 Primary Partitions** -OR- **3 Primary and 1 Extended Partition** and in the extended partition you can have up to 64 Logical Partitions (or is it 63?) in extended partition in a single HD. 

So a logical partition exists within an extended partition, which counts towards the limit of 4 primary partitions per single HD (IDE or SATA).  

And, logical partitions always start from /dev/sda5.  I found this out on the fly, where I created 2 primary partitions and one extended, and wondered where sda3 and sda4 went.  

> If I put the XP in a primary, then the old Ubuntu into a primary, and the new MythTV in a primary, can I put swap in a logical? Where?

Yes.  You can put swap anywhere in extended as logical.  For example, here is my HD setup:

/dev/sda1 (disk image copy of WinXP on second HD)
/dev/sda2 ntfs (data storage; read/write by XP and linux, read-only by MacOS)
/dev/sda3 fat32 (data storage; read/write by XP, linux, and MacOS)
/dev/sda4 extended
[INDENT]  /dev/sda5 ext3 20 GB (logical; mount of ubuntu /root)
  /dev/sda6 ext3 25 GB (logical; moung of ubuntu /home)
  /dev/sda7 linux-swap 1 GB
  /dev/sda8 ext3 20 GB (...for fedora /root) 
  /dev/sda9 ext3 25 GB (...for fedora /home)
  /dev/sda10 ext3 20 GB (...for opensuse /root)
  /dev/sda11 ext3 25 GB (...for opensuse /home)[/INDENT]
unallocated unallocated

Good luck, and have fun!

---

### Post by perixx on 2008-01-31
> You can create [...] 1 Extended Partition Thx, Dirk, for pointing that out. I wasn't sure about it anymore, so I didn't want to give a comment on that. Thought the rest should be pretty much self-explanatory, but good you described it a little closer...

perixx

---

### Post by bliffle on 2008-02-02
Thanks guys!

So Windows is really the only OS that ought to go in it's own logical partition and it also has to be the first one.

What I can do is create a linux extended (logical) partition and put my 'daily driver' old Gutsy sytem in that and then put my experimental MythTV partition system there too, or in a new extended partition, perhaps to confine the damage in case of explosions.

Since I misallocated partitions the first time around I may have to do some large-scale data movement, so I suppose I should use 'dd' or 'pcopy' for that. In the past I've even moved XP partitions successfully after a LOT of 'dskchk' runs on the XP system.

---

### Post by perixx on 2008-02-02
> So Windows is really the only OS that ought to go in it's own logical partition and it also has to be the first one.
Partly true *g* 
Windows needs to be on a PRIMARY partition and it needs to be on the first partition, unless you've got another windows system (including nt-bootloader) sitting on the first partition. Thus, Windows is a No.1 OS ^^) 

Besides, why don't you install MythTV on your Ubuntu system? It's simply a program... 
oh, and you could check out 'ntfsclone.org' for backing up XP partitions...

perixx

---

