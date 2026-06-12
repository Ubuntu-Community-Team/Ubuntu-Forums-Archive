---
title: "Edgy Installer Freezes When Starting Partitioner"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by nuclear_eclipse on 2006-12-03
I would like to start by noting that I am a fairly competent Linux/Unix user.  I've been running Debian and Ubuntu distros on 4 PCs in my home for multiple years, I use Solaris and Fedora systems at work, and BSD flavor for my router, so I'm pretty sure my problem is not stemming from me, but rather from either a hardware or driver problem that I just can't find a quick fix for, and I don't have the time to spend hours and hours combing the entire internet for answers.  Anyways, on to the problems....

I can install Edgy perfectly fine on every other computer I own, but on my wife's Dell Inspiron 1100 notebook, the installer freezes when trying to bring up the partition editor.  The installer makes its way (slowly) through the initial phases just fine, and gets to the point of asking how I want to deal with existing partitions.  I have a couple extra partitions I dont want it to remove or change, so I need to choose the "I will manually edit the partitions" option, and it starts loading the Gparted partition editor, and halfway through loading that (at 15%), the system hits a hard freeze, and becomes completely unresponzie, requiring a hard reset.

Now, I've tried booting the LiveCD with the 'noapic' and 'nolapic' options, but that has no changed anything, and I have previously used the alternate CD image to install Edgy before, but I really don't want to use that again, as I had problems with sound from the alternate install (that I didnt have with the Dapper LiveCDs), not to mention I'm wanting to install a custom LiveCD with my own default packages.  However, the freeze does *not* happen with just the custom LiveCD, it freezes even on all official LiveCDs, including Kubuntu.

If you have any ideas for what might be causing this problem, or an idea of what might be a solution, I would appreciate any input you can offer me.  Thanks.

---

### Post by syrleb on 2006-12-03
that happened on my laptop, use a different cd

---

### Post by nuclear_eclipse on 2006-12-03
> **syrleb said:**
> that happened on my laptop, use a different cd
I've tried many times with many different burns of Edgy, each one does the same thing, it can't be the CD (or DVD in two the latest cases).

---

### Post by syrleb on 2006-12-03
hmmm, go to windows and use partitionmagic to create a partition, then just autocreate with the installer

---

### Post by nuclear_eclipse on 2006-12-03
I've tried removing all partitions but the one I wish to keep, and then have the installer autocreate partitions in the free space, but it still freezes when "checking for existing partitions" (or something like that).

I really think the problem lies in an issue with either the controller or the driver.  Could DMA be an issue, either not turned on, or is and shouldn't be?  How would I go about checking this from the LiveCD, and what boot options would I use to turn it on or off?

---

### Post by syrleb on 2006-12-03
i am very sorry, but im not exactly a ubuntu genius more like a regular user so i cant really help you with that, for some reason using a new disk fixed all my problems, and are you sure its frozen not just slow because mine took a whole hour to partition, dont know why

---

### Post by davidkazuhiro on 2008-02-08
I am having the exact same problem. I got a box from my friend with freebsd on it, but it freezes when Ubuntu goes through the partitioning process. I do the default of wiping the entire machine, but it freezes at 5 percent. I added and extra 512 mb of RAM and still the same problem. I downloaded the gparted live cd and that freezes too once it detects the processor. Did you guys figure out the problem on your end? I'm starting to get frustrated here...

---

