---
title: "How to setup new RAID 1 with existing drive?"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by momist on 2013-09-04
Hi,

I have a system currently running Lubuntu 13.04 from a SATA HDD.  I tend to change flavours often, and I suppose this question would apply to any *buntu flavour.  

I have bought a similar SATA3 1TB drive that I want to install in RAID 1 format for security, as the old drive now has 3 bad sectors and is too big for me to back-up.  The new drive says it is compatible with SATA 1.  The current MoBo, Asus A8V Deluxe, has both a "Promise RAID chipset" which can handle two SATA drives and one Parallel, and "onboard VIA RAID drivers" which can only serve SATA drives, both setup through the BIOS.   I'm not sure which I should be using?

Also, should do I need to do anything extra in software, other than using the RAID solution offered by the MoBo?

Thanks for any guidance here, I've never used RAID before.

---

### Post by TheFu on 2013-09-04
RAID is for HA, not backups.  A corrupted file will be corrupted faster with RAID.  Viruses get written to all disks in a RAID set too.  Versioned backups - like 30 days - will probably give the owner enough time to notice the issue and restore from a non-corrupted backup.

Ok, so if you are set on RAID, use Linux software RAID for home.  The ability to migrate between distros shouldn't be an issue. I've done it from 8.04 to 10.04 and to different machines with the same external array.  I do NOT use RAID on the / partition.  Booting under RAID used to be an issue and with good backups, it becomes a non-issue.

Do not use the RAID capability of the MB - even if you can. Fake-RAID sucks. It ties your storage to the hardware, just like a dedicated RAID card does.  For a home, hardware RAID is probably too expensive, since a quality RAID card is $300+.  Plus, if you are tied to any controller hardware, you won't be able to move the disks to new hardware easily.

I hope you will setup a backup disk, NOT RAID, but it is your system.  You might want to check out the links in my signature.

---

### Post by momist on 2013-09-04
> **TheFu said:**
> RAID is for HA, not backups. 

HA?  Does not compute for me.  Sorry, I just don't recognise the terminology, can you elaborate please?

> **TheFu said:**
> 
Do not use the RAID capability of the MB - even if you can. Fake-RAID sucks. It ties your storage to the hardware, just like a dedicated RAID card does.  For a home, hardware RAID is probably too expensive, since a quality RAID card is $300+.  Plus, if you are tied to any controller hardware, you won't be able to move the disks to new hardware easily.


So, you are saying that if I use the RAID capability of my current motherboard, I can't move the disks to a new system with a new motherboard and use the RAID capability of that to continue the system.  OK, that seems a distinct possiblity, but not expected.
If you are right, then of course I should not do this, and I can simply install the new hard drive, and mirror my existing one to it as a backup.  Maybe that would be a good idea anyway, as I'm hoping to build a new system with MoBo, processor and RAM in about 6 weeks time.  That does depend somewhat on my success on eBay, getting the stuff used at a good price.  Meanwhile, I'm nervous of the existing HD failing and leaving me without all my music, photos, video of family, genealogy records and such, which is too much even for a raft of DVDs.

I _will_ check out the links in your sig, before I commit to anything.  Meanwhile, I'd still like to know why you regard the MoBo RAID feature as "Fake-RAID", and also whether to set up such RAID on Ubuntu would need any changes in the Ubuntu system, over and above the setting up of RAID in the BIOS.  Just so I know . . . .


P.S. There are no active viruses in Linux, so far as I know.  
        /home is on a separate partition that is backed up.
       / does not need backing up as I change it with the wind.
       /data,   /music,    /pictures,    are all on separate partitions also, but too big to back up with what I have.

---

### Post by TheFu on 2013-09-04
Do whatever you like, It is your project.

Different motherboards will have different disk controllers, different raid controllers - that means incompatible.  Heck, I've seen RAID controllers from the same vendor, same model, with a "lot" be incompatible. In a business, always buy 2 identical RAID controllers together. At home, use JBOD and softwareRAID - if you need it for HA.

Googled "fake raid" and found this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) This is a tech that should be avoided. Linux people use mdadm for software RAID. Much more flexible and your data is accessible from any other computer running Linux with enough disk ports.

HA - High Availability - the only reason to use RAID1-20 - RAID0 is a special case that very few people should ever contemplate - video editors are about the only people I know who *might* have a good reason for it.

Backups are what you need and not just a simple mirror. rdiff-backup is what I use.
someting like
```
$ sudo rdiff-backup  /etc /usr/local /home /backup
```

Just remember to tell rdiff-backup to delete backups over X days old - I like 60 days.
```
$ sudo rdiff-backup --remove-older-than 60D --force  /backup
```

Simple.  You might want some extra options, but start with that for now.

---

### Post by momist on 2013-09-05
> **TheFu said:**
> 
Googled "fake raid" and found this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) 
Backups are what you need and not just a simple mirror. rdiff-backup is what I use.


Thanks for that TheFu, especially that link about FakeRaid.  I can see now that my intentions were unsuitable.

Given that the my new disk is SATA3 and the old one not, and the new board I will be using is likely to be SATA3 capable, my best bet is to clone the old disk on to the new one, and then re-use the old one for backups.  I have a 500GB, mostly full, external disk with old backups on it, that really, really, needs editing to make it useful again, and given what does _not_ need to be backed up from the TB drive, some housekeeping might mean I can use it for some of my data to get it out of the machine.

So the plan now is: Install the new disk, clone the old one to it (Clonezilla), swap them, check the integrity of the new one, blank the old disk, set up a backup regime to use the old disk, spend time editing the external disk and then move some of the backup onto it.  I think I'll be busy for a while.  


First I'm going looking for a tutorial on rdiff-backup, and comparing it to backintime which I've used before.


BTW @TheFu, I looked at the links in your sig, and didn't get on with the presentation.  It was too big, too loud and too transient for my slow mind to keep up with.  Some of the screens were cropped off the screen, and the html magic used stopped me re-sizing it.   I tried to email the address given there, to find it bounced due to being listed as a spam source.  ???

---

### Post by TheFu on 2013-09-05
SATA1 or SATA3 - doesn't really matter in the real world.  Having a huge bus that the spinning drive cannot keep up with - what's the difference? It only matters for SSDs.

**Backintime** is fantastic for user backups - easy to understand, but not so efficient with different versions or for backing up complete systems. I used this on Mom's Linux box, but only for her HOME.  For the OS, I used **rdiff-backup** for a few yrs before she passed in July.

**rdiff-backup** is more efficient in storage and bonehead to restore a single file from the most recent backup. It is a copy.  B-i-Time is like that too, which drew my towards it.  I looked at many months of backups for each and rdiff-backup was about 20% more efficient in real-world use than Backintime.  For 60 days of backups, less than 20% more storage than a mirror needs is used here. Your results might be different, on my servers, I usually see only 10%.  So if a server is 10G, then 60 days of backups are around 11G-12G.  If I get smart and backup just the things to actually recreate the server (not restore it), then storage becomes much less - removing 2-4G for the OS and apps. Why backup packages and programs when we can just backup the list of packages with ```
dpkg --get-selections > ~/list_of_packages.txt
``` . As long as that file is in the backups, we can restore all the programs, right?  There is a flaw. I can't restore programs from 50 days ago, only the current versions. I will have settings and data from 50 days ago, however.

The presentations don't need javascript. Disable that to see everything on 1 page or use the hidden controls in the lower right hand corner (press the ZERO).  Honestly, I try to make the presentations good as reminders for people who attended, not as How-Tos. I want to cover the "why" aspects.  To loud?  Was there sound?  The size is made for rooms with 20+ people.  Using the <cnt> + and  <cnt> - doesn't work? Guess not. 

I can't help you with the email issue. Some providers allow spammers. We block them dynamically based on a service. Sometimes gmail is on that list, so it isn't just the small guys.

**Which backup tool that you choose really isn't too important as long as it works and you can restore a system.**
Anyway, your plan seems reasonable to me.

---

### Post by momist on 2013-09-05
Thank you again TheFu.

Too loud - no, not sound, the strident bold oversized fonts.  I realised it was for a big screen before an audience, but it comes across badly to a single pc screen.  Maybe I'm oversensitive.

So maybe SATA 3 is wasted on a HD, I wouldn't know.  The newer drive may, or may not, be more efficient or reliable.  The old one was a low-power design that doesn't get too hot, while the new one is a standard workhorse type that might.  Who knows what might kill a hard drive?  We can't predict the future.  Backups are necessary, I always knew that, but it can be hard work to keep them in order and to initiate them in the first place.

My wife uses an Apple machine, and the backup solution was provided.  Just plug in a suitable USB device, and away it goes on it's own.  Great if you have the (expensive) hardware to do it.  My machine is a hobby, and I keep the cost as low as possible.  Maybe I should invest more in the _necessary_ things like backup hardware, but then that would steal funding from my proposed re-build to make it better.  I'm on Lubuntu now because the hardware won't support the full Ubuntu any longer.

Anyway,  I will mark this thread solved, as I have now settled on NOT doing the RAID 1 architecture.  Anyone else reading the thread will see why, and that the better solution for those contemplating it under other circumstances should pick out that the software RAID in Ubuntu is a better way to go than the "FakeRaid" provided in some hardware.

Thanks for the help.

---

