---
title: "RAID1 Question"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by patrick17 on 2015-02-01
Hey there,

I am trying to do a new setup with Ubuntu 14.04. I have 15 drives in a RAID6 hardware array and is already all setup and ready to go. I am now trying to get my 2 SSDs in a RAID1 configuration using a software array.

My goal is to have the OS run from one of the SSDs while the other mirrors it so if one of the SSDs fail I can use one of the others as a replacement until a new one comes in. I have tried installing it and I get a grub-install failure when it tries to install it to the /sdb. I have tried changing it to the /md1. I've been following this guide [here]("https://help.ubuntu.com/lts/serverguide/advanced-installation.html"). Neither works as I get a grub-install failure. 

The question is, do I need to first install Ubuntu on one of the drives and then setup the mirror? If so, is there a good tutorial I can follow?

Thanks,
Pat

---

### Post by TheFu on 2015-02-02
Do you want the SSDs to be mirrored from time to time or do you want them as RAID1? 
There is a difference, mainly in complexity and safety.

Plus, you still need backups RAID is never a replacement for good backups. RAID is only about high-availability, nothing else.

---

### Post by patrick17 on 2015-02-02
Ya, I guess you are right. I don't know what I was thinking. The SSDs are not going to hold anything but the OS and a few applications. I mean, honestly, it wouldn't be bad losing my OS. I have my data on my RAID6 configuration. I was just trying to make my server as high-availability as possible. So if the SSD with the OS went down, the other SSD could kick on.

---

### Post by MAFoElffen on 2015-02-02
+1 with FU...

You misunderstood what he said, so I will expand on that, to support an understanding of what he said.

With 2 drives (whether ssd or anything else), you have the choice to do RAID 1 Mirror, or use the second to backup your primary drive intermittently. A Mirror is safer, An incremental rsync is overall faster.

What he said about backups... I have agreed with him for years about-- That "RAID is not a substitute for backups." That was not said to dissuade you from doing RAID. It means that even with the redundancy of RAID, you should have a good recovery plan. A Server's main job and primary mission depends on uptime-- That it remain up & if not, that it be back up and running quickly.

RAID parity, and mirrors help with those promises, and guarantees. But there is no faster and safer way to guaranty that you have a copy of what was there than by good backups. True that you can reload a fresh system in less than an hour, with app installs, but what about configs, users and groups? Wouldn't you at least not want to have to recreate the wheel?

To me, RAID1 is simple to config, and forget. The other way is easier for some folk. But as a Server, I plan for failures, recoveries, duplication of my resources to support each other. Redundancy and mutual support. And a recovery plan that you can keep to. Not saying you need to run clusters, but the the cost/benefit of a backup can save you a lot of stress and grief. (not just on your data RAID6)

You know how many come here for help trying to recover a failed RAID that never had any type of backup? No complaints on that, but if they did have at least one...

I've read enough of Fu's posts to know that we have a similar respect and philosophies on backups-- for multiple versions of backups and multiple copies of backups kept in multiple physical locations. I try to learn from my mistakes, and hopefully not have to relive them...

---

### Post by gordintoronto on 2015-02-03
If you make an image of your OS drive onto an external drive from time to time, you can just restore the image onto a new device when you need to. The Macrium Reflect "Restore CD" can do both sides of this, although it means your system is offline while you are making the image.

---

### Post by TheFu on 2015-02-03
> **gordintoronto said:**
> If you make an image of your OS drive onto an external drive from time to time, you can just restore the image onto a new device when you need to. The Macrium Reflect "Restore CD" can do both sides of this, although it means your system is offline while you are making the image.

So can F/LOSS tools like fsarchive, dd, clonezilla, partimage and others. All require the partition be off-line during the image process.

I would be more inclined to NOT use RAID1 for the OS since I don't work with RAID every day. I would mirror that partition weekly to another disk - like a manual, delayed mirror, then if anything bad happened, just modify the fstab on the good drive to boot off it by uuid and swap the sata cable (or change the boot drive in the BIOS). 5 min to get online.

I do have RAID running here and use it daily, but haven't setup a new RAID partition in years. Every time I need to do something with it, I haven't to look up the commands.  If you do RAID stuff daily across a few hundred systems, then your RAID skills will become 2nd nature. I prefer having a known solution to the need-to-boot-now issue. RAID would just get in the way of the fix for me.

And I'd have good, versioned, backups too.

---

### Post by MartyBuntu on 2015-02-03
I'll go even further on the RAID debate by saying that most casual, home-users *don't need* RAID1, other that saying "Oh yeah...I got skillz...RAID1, check it out...pretty sweet, huh?"
I see stuff like RAID1 on HTPC's (simple movie and music file serving) with NO backups...I scratch my head...

---

### Post by TheFu on 2015-02-03
> **MartyBuntu said:**
> I'll go even further on the RAID debate by saying that most casual, home-users *don't need* RAID1, other that saying "Oh yeah...I got skillz...RAID1, check it out...pretty sweet, huh?"
I see stuff like RAID1 on HTPC's (simple movie and music file serving) with NO backups...I scratch my head...

Yeah.  My media collections are not RAID anything.  I don't even use LVM to merge file systems. Plex can merge different partitions for a central view, so why bother? In the old days, I used symbolic links rather than screwing around with odd file systems. Use rsync to slow USB storage on another machine as a mirror-only backup, no versioning. It isn't automatic, just did a manual sync today. That happens about once a week and takes 1-5 min.

The RAID here is used only for a few VMs (20 or so) that provide services for a few small companies for friends.  Daily, versioned, backups for those VMs are completely automatic, but no RAID.  I use the excess RAID storage for crap - because it is there, not because it is RAID.

RAID has 1 purpose - HA.
Versioned backups have 1000+ purposes.

---

