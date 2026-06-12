---
title: "Help! Ubuntu Server Install, dual boot - n00b"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by RockOut on 2011-10-26
I had Ubuntu Server isntalled, in an unfavorable way on my first hard drive. However unsatisfactory this setup was, it worked for my purposes.

I found a 1TB harddrive, and decided to put it to use as a second hard drive, and thus second install of Ubuntu server, this time configured in a way that was more favorable for what I need at my homeoffice.

Now, I can't get either HDD to boot. I'm ready to just start fresh, from scratch. I have a pretty awesome i5 processor, the both HDD are new.

Any help? Basically, this is a new Ubuntu Server Install. I don't have meaningful data on either drive, so I'm OK with just using one of the HDDs to hose the /home folder or as a separate storage drive.

---

### Post by MAFoElffen on 2011-10-27
> **RockOut said:**
> I had Ubuntu Server isntalled, in an unfavorable way on my first hard drive. However unsatisfactory this setup was, it worked for my purposes.

I found a 1TB harddrive, and decided to put it to use as a second hard drive, and thus second install of Ubuntu server, this time configured in a way that was more favorable for what I need at my homeoffice.

Now, I can't get either HDD to boot. I'm ready to just start fresh, from scratch. I have a pretty awesome i5 processor, the both HDD are new.

Any help? Basically, this is a new Ubuntu Server Install. I don't have meaningful data on either drive, so I'm OK with just using one of the HDDs to hose the /home folder or as a separate storage drive.
When you did the second install, what drive did you install Grub to?  sda or sdb?

Please post the results of the Boot Info Script (link in my Sig Line). Please remember to put the result within CODE tags when posting.

---

### Post by MAFoElffen on 2011-10-27
> **MAFoElffen said:**
> When you did the second install, what drive did you install Grub to?  sda or sdb?

Please post the results of the Boot Info Script (link in my Sig Line). Please remember to put the result within CODE tags when posting.
-OR
In this time you could have done a fresh install.  If it where me (since you expressed it already), I would do a fresh install with all previous gone.

You have seemed to learn with each install and noted what you would do different. This is always a good thing.  Besides, what good is 2-3 installs of server on the same box?

---

### Post by RockOut on 2011-10-28
That's the thing... I just want to use the second HDD as network storage. I also know I need to reinstall.

This is where I encounter the problem: When I try to install Ubuntu Server from the USB stick, it gets stuck at the "CD-ROM check" around the beginning of the installation.

I've burned a CD instead, and the CD works as a live CD, but then, I don't see both HDDs show up. When I boot up and login to the BIOS, I DO see both HDD reflected there.

---

### Post by MAFoElffen on 2011-10-28
> **RockOut said:**
> That's the thing... I just want to use the second HDD as network storage. I also know I need to reinstall.

This is where I encounter the problem: When I try to install Ubuntu Server from the USB stick, it gets stuck at the "CD-ROM check" around the beginning of the installation.

I've burned a CD instead, and the CD works as a live CD, but then, I don't see both HDDs show up. When I boot up and login to the BIOS, I DO see both HDD reflected there.
What did yo use to install on the 1TB before (USB or CD)? I know it saw it before you installed it to it when it borked, right? Is it not seeing the 1TB now?

Lets get you to form a plan... I was thinking with your first post, that what I would have done was install server on the small drive, with the small drive as sda.  In the partitioner, use the 1TB as your separate /HOME.  That way you automatically and easily (for a new user) have things setup "for you."  You could limit the first disk's sda1 partition to 20 GB's to install the system to and leave the rest unused / unallocated. Later the rest of the unused space on that disk could be partititioed EXT4 for DATA (more data space) and added to fstab to be mounted at boot... 

But it's your machine.  What are you thinking might be a plan for you?

On the disks... One way would be to have you post the results of the boot info script in my sig line. That would tell us what went on with the install and if Grub2 got installed/where.

It sounds like maybe the second disk got borked somehow. I'm thinking that since you "are" getting into this and learning from it. 
- Download a current Gparted LiveCD... burn it to CD on the lowest speed.
- Boot it on your server.
- If GParted see's your 1TB drive > Delete the partitions > delete the partition table > add a partition table > partition the drive as ext4. (You'll have to "Apply" between each step of that...) 
- Shutdown

Boot from the Server Install Disk and see if it see's both disks... I'll stop there for the moment.

---

