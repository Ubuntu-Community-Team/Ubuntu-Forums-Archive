---
title: "FakeRAID for 10.04 or 10.10 to Dual Boot Windows 7 or Other Backup?"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by setheey on 2010-12-20
:KS Hi all-

I've spent the last day reading all of the RAID threads and I think I have a few options to choose from, but I need some recommendations and/or solutions. So here's my situation:

I have 3 WD Caviar SATA2 HDs - one 500GB for Windows 7 and two 1TB drives I would like to array in RAID 1 for backup. I will probably use Windows 7 as my main drive for most things (iPod, Starcraft2, Office...) but want Ubuntu on the data drives just in case. The 500GB disk currently has all my data and I am free to play around with the TB drives.

I am running on a Dell XPS 420 Intel Core 2 duo machine with a BIOS integrated fakeraid available. My copy of Win7 is a student upgrade version that I bought for $15 from my college :cool: which I used to do a full/custom install with the double install registry edit trick. (I must say Win7 has dramatically increased the performance and stability of my computer and needed very little help with drivers. Definitely worth the upgrade from Vista.)

I always manage to screw something up or need a specific tool on one OS or the other, so I like being able to switch around, so I want all my drives bootable and editable by the other OS. Partitioning disks gets messy, especially when infected by a virus, or just tainted by n00beration, so I like to keep one OS per physical disk. This summer I had a drive simply die and make a horrible clicking noise the freezer trick simply could not repair, so I am now sufficiently scared into backing up (thank goodness it was not my data drive). 

So. To have the drives mutually editable by Windows 7 and Ubuntu, I believe I need to either use a dedicated hardware RAID controller, or the motherboard's fakeraid. 

All the previous threads strongly warned against hardware controllers because if/when they fail they must be replaced with an identical device or the data is unreadable. The performance boost by a dedicated raid controller is probably minimal with today's multicore processors, however hot swapping capabilities are very convenient, but not critical since this is a home machine, not a server. They also said that you get what you pay for, and my budget for a spare part would be around $25-50, not $300+, so hardware is probably not the way to go - unless you can recommend an extremely reliable cheap card. Most of the Newegg reviews were very polarized...

Software raid is certainly in my budget (free), but I don't think that either Windows 7 or Ubuntu can read/edit the other's softraid, which makes dual booting useless.

Fakeraid is also free. I am a little worried about the motherboard breaking and losing the data, but if the motherboard dies, it's time to buy a new computer altogether since it's just turning 3 years old. (Though if I used a hardware raid, the drives would survive a mobo fail.) How much longer should I expect this board to last? The how to seems very complicated to set up for a command line n00b like me - and the instructions are for 9.10. Is there an easy way to get fakeraid to install Ubuntu 10.04 or 10.10? Is there any advantage to the newer versions, or should I revert to 9.10 and attempt to follow :confused: the [FakeRaidHowTo ]("https://help.ubuntu.com/community/FakeRaidHowto") instructions? 

Or should I not even bother with RAID at all? Some threads said that RAID 1 is not a good backup solution, but I am not worried about fire or theft, and I have an APC backup battery/surge protector. Maybe I should take the spare TB disk, get an eSata enclosure, and turn it into an external drive and do a regular dual boot with the other two drives, one for each OS. I could also keep the fakeraid 1 setup for Windows 7 I have now and put Ubuntu on the 500 GB disk, but then I lose the performance boost and minimal virus risk of keeping the OS and data separate, and would mostly be wasting the 500gb disk.

If I were to back up on an external drive, what programs or software do you recommend for backups that would emulate a RAID 1 setup? Do you have any recommendations for the enclosure (preferably with lots of blue lights, hehe)? I guess an external would have less a need to be bootable. Is there a way to automate backup and have it only update the new or modified files to save time? Is there a good automatic solution for external backup in Windows or Linux? 

I just want the least headache ](*,), maintenance, and risk I can get for cheap that will still perform. :/

Let me know what option or configuration you think I should choose. If your solution involves command lines, please be explicit with the line by line. Thanks in advance! :D

---

### Post by setheey on 2010-12-22
Well... None of these options seemed optimal. After a ton more research and consideration I am going with Clonezilla. At least I learned a ton in the process about dual booting, raid, file systems, and disk cloning.

I stumbled on disk cloning and I think this is what I am going to use. Clonezilla seems like the best free option. The live CD is going to be a pain in the butt to do regularly so I think I will just have to rely on monthly backups, but it meets all my other requirements of being able to dual boot, and create bootable drives and be cross platform. I can also remove the extra drive to keep somewhere safe so it won't be vulnerable to electrical surges (but probably still fire).

I wish there was an automated utility that seemed trustworthy and worked with Linux and creates bootable drives and only modifies new or updated files to save time. I think I ask too much of my system sometimes. Essentially I want RAID 1 disk cloning without the raid hardware and hangups of the software.

I looked into Windows' software raid which looks decent, but it doesn't allow for bootable drives, so that's no good. It's backup is great too, but I don't want just files since that wouldn't be bootable, and I don't want a system image because that is also not instantly bootable. I also checked out the dd command line copy, sbackup which apparently is slow, and Paragon backup and recovery, and Easeus disk copy, none of which were just right.

Well I think Goldilocks is done futzing around and is going to dual boot regularly with separate drives for Windows and Linux and try to stay on top of the disk cloning. :-|

---

