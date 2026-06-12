---
title: "Disk Setup Suggestions"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by DigitalNoise on 2013-08-03
Greetings,

I'm finally ready to make the plunge and dedicate more than just a small portion of one my HDD's to <insert flavor of Linux here>, but I also have the requirement to still have a Windows 7 install (primarily for gaming).

To this end, I've recently purchased some new HDD's for my system to give me more room to work with, and I had a few questions, but first, here are the HDD's that I have to work with - there are four total, but I can only actually use three at the moment, due to forgetting that one of the SATA connections is being used by my DVD-RW (whoops):

[LIST]
[*]250 GB (Existing, currently has Windows 7)
[*]640 GB (Existing, currently has ~550 GB storage, and remainder for Linux Mint 15)
[*]500 GB (New)
[*]2 TB (New)
[/LIST]
I'm thinking of using the 500 GB, 640 GB, and 2 TB drives off the bat, and keeping the 250 GB in reserve if I ever get a PCI-X SATA card.  Alternatively I suppose I could always disconnect my DVD-RW drive, but I'm not sure I want to do that at the moment.  The original plan was to share the majority of the 2TB drive between both OS's for things like media, etc.

So, with that in mind, I've got the following questions, and would be very interested in seeing what other folks have done in a similar situation:

[LIST=1]
[*]Should Windows 7 and Linux exist on the same disk, or separate?
[*]Should applications and core files for each exist on the same disk as the OS, or separate?
[*]Should user files for each OS exist on the same disk as the OS, or separate?
[/LIST]
Coming from the server world (DB servers), I know that in that world, it's typical for the OS to reside on one disk, and storage to reside on other disks in order to maximize through-put.  Not entirely sure that would hold true in this situation or not.

---

### Post by TheFu on 2013-08-03
The same performance considerations for servers applies to desktop Linux, but I'd add that convenience is also an important consideration. The more you can spread things used concurrently to different physical disks, the better. If most of the performance will be read, then almost any RAID would improve performance.

Unless you really know what you are doing, avoid RAID0 and avoid using LVM to span file systems across multiple disks. Both of these are a good way to lose all the data on both drives.

So, I'd probably do something like this:
* Format any new HDDs with GPT (not MBR). It provides more resilient partition records, support for huge HDDs and nearly unlimited partitions. Read up on the downsides if you need to run OSes older than Vista.
* Win7 - 60G for OS/Apps
* Linux Boot - 500MB
* Linux / - 10-20G this is for the OS and apps only
* Linux Swap 2G or the amount of RAM in the box, which ever is greater.  Actually, I don't go above 2G unless I want hibernate support.
* Linux /home - Big enough for most files, development, things like that - everything except video, music and other media
* NTFS-Data - whatever is left for media files that do not need permissions control, support for softlinks, hardlinks, backups
* Linux /Backups - 2x the amount of primary storage needed; it is important that Linux backups be written to Linux file systems.  A different machine can have this storage, but it should be on the LAN somewhere.
* Linux /var - depends on your needs - if you are a webdev, this might be larger

If there will be multiple Linux machines running the same flavor, you might want to add another partition /var/apt-cacher-ng to store cached APT packages for all the machines on the network.

The main thing is to have a different /home from /, so that OS upgrades don't risk your personal data. Besides that, it might not be useful to have a separate /boot or /var - your needs determine if it makes sense.

I hope that is clear and not overly complex.  I'd also say that an overly complex partitioning scheme like this can suck later. I only do this for the main file server on the network.  Most other machines are extremely simple - some only get 1 partition, zero swap, zero backup storage (network backups rock) ... you get the idea.

---

### Post by DigitalNoise on 2013-08-03
> **TheFu said:**
> The same performance considerations for servers applies to desktop Linux, but I'd add that convenience is also an important consideration. The more you can spread things used concurrently to different physical disks, the better. If most of the performance will be read, then almost any RAID would improve performance.

Unless you really know what you are doing, avoid RAID0 and avoid using LVM to span file systems across multiple disks. Both of these are a good way to lose all the data on both drives.
This is primarily my daily home desktop system, and secondarily a place for media storage (hence the 2TB disk).  Because the sizes of the disks aren't uniform, I think I would have to go the JBOD route for any kind of RAID setup (unless something has changed?), and I'm not even sure that my motherboard supports JBOD as a RAID option.  It's definitely something I'll do on my eventual new build.
> * Format any new HDDs with GPT (not MBR). It provides more resilient partition records, support for huge HDDs and nearly unlimited partitions. Read up on the downsides if you need to run OSes older than Vista.The oldest Windows OS I'll be running is Windows 7 Ultimate Ed. 64bit, so I'm guessing I should be ok.  That brings up the question though - does either Windows 7 or Linux support formatting a disk as GPT vs. MBR out-of-the-box, or is that something that needs to be handled separately before installation?
> * Win7 - 60G for OS/AppsMy current Windows 7 install is much bigger than 60G, though a large portion of that is Steam and items in my user profile.  Moving those to a separate disk is probably wise - I'm just not sure how much space to set aside for it.
> * Linux Boot - 500MB
* Linux / - 10-20G this is for the OS and apps onlyWould you recommend that these be on the same disk as the Windows 7 install or even on the same disks with each other, or separate?  And I seem to recall, at least in the past, that there were issues if the Linux bootloader didn't reside on the same disk as the actual OS, but those may have been resolved.
> * Linux Swap 2G or the amount of RAM in the box, which ever is greater.  Actually, I don't go above 2G unless I want hibernate support.I would assume that for performance reasons this should be on a different disk than the OS and user data, to allow for faster swap performance.
> * Linux /home - Big enough for most files, development, things like that - everything except video, music and other mediaDefinitely on a separate disk.
> * NTFS-Data - whatever is left for media files that do not need permissions control, support for softlinks, hardlinks, backupsThis is what I was planning on using the 2TB disk for.  Will Linux interefere with NTFS file sharing permissions?
> * Linux /Backups - 2x the amount of primary storage needed; it is important that Linux backups be written to Linux file systems.  A different machine can have this storage, but it should be on the LAN somewhere.What's this "backup" of which you speak? ;)
> * Linux /var - depends on your needs - if you are a webdev, this might be largerThis is one of those directories that I've never really seem to understand what it's used for.  I'm really looking to learn some different programming languages that are cross platform, but primarily looking to develop under Linux, so I'm not sure if that would fall into the same distinction or not.

Based on your suggestions here, this is what I've gotten a vague idea of - implementing it, of course, is a different matter entirely:

**HDD 1 - 500 GB**
[LIST]
[*]P1 - Windows 7 60 GB
[*]P2 - Linux Boot 500 MB
[*]P3 - Linux OS/Apps 60 GB
[*]P4 - Profit? ~ 350 GB or so unused.
[/LIST]
**HDD 2 - 640 GB**
[LIST]
[*]P1 - Windows 7 User Data 320 GB (NTFS)
[*]P2 - Linux User Data 320 GB
[/LIST]
**HDD 3 - 2 TB**
[LIST]
[*]P1 - Linux Swap 4 GB (may push to 8 GB as I plan to stuff more RAM in the box eventually)
[*]P2 - Windows/Linux shared storage 1.2 TB (NTFS)
[/LIST]
Currently about 90% of my media is on the 640 GB drive, so I'll need to drop the 2 TB disk in and move the data over before I'll be able to re-purpose it.

---

### Post by TheFu on 2013-08-03
Seems like a reasonable plan, though even 20G is overkill for / (OS/Apps) on linux.  I don't have any idea what you'll do with 60G.  My entire desktop - OS, Apps, AND home use 14G today.  2 years ago, it was just 10G.

I hope when you say "linux user data", you really mean /home/ . 320G is overkill - like I don't know how much today overkill. Even Java developers only need 60G or so and Java is a disk space *****.  For Python, Perl, Ruby, 5G will let you have multiple, complete, development environments.  I think you've been warped by Windows bloat on your storage ideas.

If you don't know about backups, don't worry. You'll never need it. ;)  Of course, I really think that backups are a cornerstone of system security - I don't buy storage unless I also can back it up.  Disk failures never happen when it is convenient. They always wait until hours before a project is due and take multiple drives down at once.  2TB is too large for online backups - just sayin'

Software RAID does not require identical disks be used, it just requires identical sized partitions be used.  But since you don't care about backups, I won't bother saying that RAID is not a backup here either.

---

### Post by DigitalNoise on 2013-08-03
> **TheFu said:**
> Seems like a reasonable plan, though even 20G is overkill for / (OS/Apps) on linux.  I don't have any idea what you'll do with 60G.  My entire desktop - OS, Apps, AND home use 14G today.  2 years ago, it was just 10G.
Well, I plan on running WoW under Wine, and WoW's install alone is 20-30GB depending.  Of course they may have shrunk that quite a bit as well.  And while I suppose I could pull it from the shared media drive, my research suggests that keeping the Wine/Linux version separate is preferable to help avoid file corruption.  What I can't figure out is what I'm going to do with the remaining disk space on HDD 1 - though I suppose I can always hold it in reserve, as it's generally not an issue to expand a partition.

> I hope when you say "linux user data", you really mean /home/ . 320G is overkill - like I don't know how much today overkill. Even Java developers only need 60G or so and Java is a disk space *****.  For Python, Perl, Ruby, 5G will let you have multiple, complete, development environments.  I think you've been warped by Windows bloat on your storage ideas.Yes, that's precisely what I meant.  320 GB may be overkill, but I'm not sure what else to do with it.

> If you don't know about backups, don't worry. You'll never need it. ;)  Of course, I really think that backups are a cornerstone of system security - I don't buy storage unless I also can back it up.  Disk failures never happen when it is convenient. They always wait until hours before a project is due and take multiple drives down at once.  2TB is too large for online backups - just sayin'Well, it's not that I don't care about backups, it's just that I've been lucky so far - and I tend to back up what I consider to be "critical" files in other ways.  I've never really seen the use in backing up stuff that can be re-installed (programs, etc.) or things that can be reconfigured.

> Software RAID does not require identical disks be used, it just requires identical sized partitions be used.  But since you don't care about backups, I won't bother saying that RAID is not a backup here either.
Ah, I thought you were referring to hardware RAID - I've never really used software RAID, and in the past I've never heard much good about it - mainly that it's buggy - but I'm perfectly willing to consider it.

---

### Post by TheFu on 2013-08-03
> **DigitalNoise said:**
> Well, I plan on running WoW under Wine, and WoW's install alone is 20-30GB depending.  Of course they may have shrunk that quite a bit as well.  And while I suppose I could pull it from the shared media drive, my research suggests that keeping the Wine/Linux version separate is preferable to help avoid file corruption.  What I can't figure out is what I'm going to do with the remaining disk space on HDD 1 - though I suppose I can always hold it in reserve, as it's generally not an issue to expand a partition.

WoW will not be installed system wide - it will be under your $HOME - that 320G. Further, apps and data are not stored together in Linux, so even if an app is installed under /usr, the data will be stored under your $HOME.  Honestly, I don't know where WoW will be installed, but I assume you run it under WINE and THAT definitely is under your $HOME.

> **DigitalNoise said:**
> Yes, that's precisely what I meant.  320 GB may be overkill, but I'm not sure what else to do with it.
Well, I'd start with 20G for /home and leave the other amounts available. Increasing the size of partitions later is not a big deal at all, though having a good backup BEFORE doing it is a good idea. I've never lost any data moving partitions around or resizing partitions with Linux tools.

> **DigitalNoise said:**
> Well, it's not that I don't care about backups, it's just that I've been lucky so far - and I tend to back up what I consider to be "critical" files in other ways.  I've never really seen the use in backing up stuff that can be re-installed (programs, etc.) or things that can be reconfigured.

We are all lucky for some period of time, until we aren't.  Then is sucks.  If you think about this for a little bit, you'll see how much data you have at risk now.  The OS and every App fits in 20G - **everything else** is data.  That's about 3TB of data at risk that you have.

I work in IT professionally and didn't think I had anything important stored at home. I backed up only the "*critical data*" too.  Then it happened, HDD failure. Lost 80% of the data that day. It wasn't the end of the world, but it sucked. Got **Backup Religion** that day.  A year later, my server was cracked.  I'd been doing weekly backups and was able to determine exactly what the cracker modified on the system, thanks to the backups. Without those backups, I would have needed to rebuild the entire machine from scratch to be sure.  After all, **nuke the entire site from orbit. It's the only way to be sure.**

You know all that extra space on the different drives? Perhaps those can be backup areas for alternate drives?
/backups
  /p1
  /p2
  /p3
  /p4
Then you can rsync or rdiff-backup stuff from each disk to the next - the p1 ... p4 are mount points below the /backups/ directory.  Just a thought. I do something like this for my internal household websites.  

> **DigitalNoise said:**
> Ah, I thought you were referring to hardware RAID - I've never really used software RAID, and in the past I've never heard much good about it - mainly that it's buggy - but I'm perfectly willing to consider it.

Strange - I and probably millions of others have been using Linux software RAID for years without **any** issue whatsoever.  I've had more issues with HW-RAID cards failing and losing all the data. With Linux Software RAID, I've moved between completely different systems, different disk controllers, 3 times and never had any issues at all.  I did have a few drives failures - replaced the disk, the RAID rebuilt itself and ran fine for another 5+ yrs. Just replaced those disks last fall - they were 6yrs old and I was afraid. 2 of those disk are used for scratch storage still - haven't failed or showed any issues at all.  Anyway, RAID probably isn't all that important for your needs.

---

