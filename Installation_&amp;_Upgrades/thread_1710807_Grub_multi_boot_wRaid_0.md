---
title: "Grub multi boot w/Raid 0"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by jeliocranch on 2011-03-20
Hi,
There have been many postings on doing Raid 0 setups, and it seems the best way looks like softRaid, but there were some arguments for fakeRaid in dual boot situations.  I've seen some posts on dual boot windows/linux in Raid 0, but I was hoping to do a multi-boot using a grub partition, with several Linux distros and Windows 7.
There will also be a storage disk for data, but not in the array.

From what I gather, I'll need a grub partition which can only reside on one of the two disks, one swap partition on each disk, then the rest I can stripe.  

I've got two 73GB WD raptor drives to use for the OS's and programs.  I'm just getting my feet wet with the terminal in linux (Ubuntu makes it way too easy to stay in GUI), and the inner workings of the OS, so I have several questions: 

Is this going to be worth the effort?  Obviously I'm trying to boost performance in boot and run times, but with Grub on a single drive, will I see much gain?

Does this sound like the right methodology (softRAID)?  I only have two spare PCI slot's, which don't seem like they would be condusive to hardware raid, but someone who knows more could convince me otherwise.

My system is:
Biostar A880G+
1090T phenom II
Radeon HD4850
4 gb ddr3 1333
seagate 7200.12 500GB storage drive (currently the main drive, will convert after raid install)
2X WD740ADFD raptor drives
optical drive.

Any (constructive) suggestions are greatly appreciated.

---

### Post by Hedgehog1 on 2011-03-20
Wow - lots of folks trying RAID just lately.

Here are two threads about this in the last week:

[http://ubuntuforums.org/showthread.php?t=1706499]("http://ubuntuforums.org/showthread.php?t=1706499")

[http://ubuntuforums.org/showthread.php?t=1710394]("http://ubuntuforums.org/showthread.php?t=1710394")

One of the very real limitations of software RAID is you cannot boot from RAID from anything other than RAID 1.  In the first thread the OP tried booting from software RAID 0.  The second link the OP is trying to use RAID 5 as part of the boot path to get to a RAID 1 partition with '/boot'.  This thread is still active.

I would also add the running RAID 0 is very risky; if either drive fails, all data is lost.  *But that is just me...*

***The Hedge***

:KS

---

### Post by ronparent on 2011-03-20
To share raid partitions with windows requires that you use FakeRAID. You do not need a separate /boot partition. Depending on which Ubuntu distribution you will be using will determine whether or not grub will install properly. 10.10 generally works best but still has some quirks. I believe, for the most part, that the partitioner will not work properly during the install unless you boot to the live cd/dvd, install kpartx to the session, and start the install from within from within the same live cd session. If for some reason a fatal error is indicate in the grub insttall be aware that it is not fatal. You can reinstall grub from a live cd session using the two step method outlined here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

During the fix just keep in mind that the partition you have to mount is the raid partition you just installed to and the raid boot loader has to be installed to the device name of your raid, not a raid partition.

Raids are definitely a more advanced topic so do post if you are unclear about any thing. Good luck.

---

### Post by jeliocranch on 2011-03-20
So, two very helpful responses so far...

To Hedge,  the first thread you pointed me to indicates *faster* read times from raid1?  It was my impression that my system speed will increase most dramatically from increasing read times for executing programs.  With the exception of backups and moving files (weekly or bimonthly), I'm not writing large files.  I am compiling and encoding.  To my mind, that is active processing and executing, which from reading the first thread sounds more like I'd want raid 1 for. 

 I always thought to save critical data, use raid 1 for the redundancy, while one would choose raid 0 for increased performance.  Further, raid 0 makes you more (most) vulnerable to failure (why I was thinking OS's only in the raid, where I have hard copy duplicates) and Raid 1 did nothing to increase performance.  Perhaps I'm wrong?

Also, I did understand that most of the time, grub won't work in raid, but I thought by having grub live on only one of the two raid 0 drives, that would take care of that issue.  Just the OS's would be in Raid 0.

For Ronparent:  I think I read a response of yours from another previous raid post, because it mentioned the same kpartx utility.  reading that post made it sound like it was fairly specific to dual boot, where grub is living in the same partition as the linux disro.  With grub in its own, non-striped partition so I can add and subtract distro's as I find and test them, it seemed to eliminate the need for that.  Am I wrong?  Your system post seems to show two linux + a windows, so you're doing multiboot that way.

I hate getting scared off, but I think I need to get multi-booting with a separate grub partition first, get that understood a bit better, then try the raid.  I've done a couple of dual boot setups, but they all suffered from issues when changing distro's or upgrading windows (can't wait until I don't need to have windows any longer, life will be easier).  

Thanks to both of you for your help.

---

### Post by Hedgehog1 on 2011-03-20
> **jeliocranch said:**
>  
 I always thought to save critical data, use raid 1 for the redundancy, while one would choose raid 0 for increased performance.  Further, raid 0 makes you more (most) vulnerable to failure (why I was thinking OS's only in the raid, where I have hard copy duplicates) and Raid 1 did nothing to increase performance.  Perhaps I'm wrong?


RAID 0 gets its reading speed because you can read data from 2 places at once.  This assumes the data you need at the same time is on separate drives:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/RAID_0.svg/100px-RAID_0.svg.png[/IMG]

As long as you are reading one odd (A17) and one even (A10), you get twos read at once.  However, if you need two evens (A16) & A10), you have to wait for A16 before you can read A10.

RAID 1 has two complete sets of data:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/RAID_1.svg/100px-RAID_1.svg.png[/IMG]

When reading reading one odd (A17) and one even (A10), you get twos read at once.  If you need two evens (A16) & A10), you still get two reads at once because both drives have a complete copy of your data.

For writing, a RAID 1 is slower than RAID 0 because you have to write everything out to both disks, rather than to every other disk.

If you are getting scared off, consider real hardware RAID, The ***Hedgehogs Preferred Choice***.  It is getting very affordable, and offers hot swappable disks and other goodies.  One example: [Sans Digital TowerRAID 5-Bay]("http://www.amazon.com/gp/product/B003YDZE0Q/ref=s9_simh_gw_p23_d0_i1?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-2&pf_rd_r=1JWGGFFF6NQVKVCCRXF3&pf_rd_t=101&pf_rd_p=470938631&pf_rd_i=507846")

***The Hedge***

:KS

p.s. Would an SSD rather than RAID0 be a less complex option for you?  Better performance that an HDD, less install complexity then software raid.

---

### Post by jeliocranch on 2011-03-21
Thanks for the explanation of Raid 1.  I knew it was a duplicate drive scenario, but didn't realize the drives could be accessing different information simultaneously.  I thought each drive was reading the same info at the same time, similar to how the drives are written to.

Raid 1 sounds like the way to go for OS's execution on with two drives.  Its just so many talk about Raid 0 for speed.
I was thinking of an SSD, but they are way more costly than the refurb raptors i bought for similar disk volume, especially considering its recommended to run SSD's at not more than 2/3rds volume.  I'm figuring I need 15GB for windows, 15 each for Ubuntu and Fedora, and I'm looking at Mint and several supersmall destros (slitaz, puppy, etc).  yes, refurbs can be problematic, but I'm playing and learning on this machine, so if things go wrong I can abort.

As for hardware raid, I think I need at least a PCI-e X1 slot available for any performance gain.  My understanding is PCI cards won't have enough bandwidth.  My only empty slots are PCI's.

Finally, I'm not fully scared off, just delaying the raid install for a couple weeks while I sort the details of Multi-boot.

---

