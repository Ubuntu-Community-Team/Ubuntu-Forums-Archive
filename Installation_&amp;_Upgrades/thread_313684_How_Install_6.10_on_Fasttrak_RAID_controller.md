---
title: "How? Install 6.10 on Fasttrak RAID controller?"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by IntuitiveNipple on 2006-12-06
I'm hoping to switch my primary server/workstation that currently runs Windows 2003 Server Enterprise to Edgy Eft 6.10 Desktop.

I have the Desktop CD and am currently running 'live' from it, checking for any issues before attempting the install.

I've discovered that the Promise Fasttrak TX2000 RAID controller isn't supported by drivers on the LiveCD and haven't been able to discover any articles describing:

a) What drivers I need, and where to get them
b) How to install/load them in the LiveCD environment (so I can resize the partitions to make space for Linux)
c) How to have them loaded so that Grub will be able to boot correctly

Does anyone know how this should be done?

Notes: Device Manager correctly recognises the "PDC 20271 (FastTrak TX2000)" controller. I've read that dmraid is required but not sure how to go about installing/loading that. The array is a 0/1 (mirror/stripe) consisting of four 60GB drives presenting a logical disk of 120GB.

---

### Post by IntuitiveNipple on 2006-12-06
Okay, found out my solution might be the Alternate CD image so downloading that now in the hope it will successfully burn to CD from the Live environment - hopefully the unionfs will have sufficient space!

---

### Post by IntuitiveNipple on 2006-12-06
Unfortunately the Alternate CD install doesn't appear to solve this issue, either.

Are there any detailed instructions on installing on a software 'fake' RAID controller?

I also found 2 bugs on the Alternate installer CD which I'm going to check/report now...!

---

### Post by davemc on 2006-12-07
I've also got Promise TX2 controllers in my front line servers.

They work well under Windows.

However in researching using them on Linux, I read some scary stuff about controllers writing random bits of data in BIOS upper memory, and also the poor linux driver support.  The people trying to get open source drivers working on them found the underlying bios code too flakey & random and gave up.

Also, being fake RAID, there didnt seem much benefit in using the TX2 as a RAID controller.  It's restore/rebuild/management tools are absolutely minimal, it gets really scary when having to image valuable data to a replaced disk. It relies on the processor to do the work, so is adding little or no value.

Looking at the card, there's not much on it, definitely no cache memory, processor etc, so it's really thin fake raid.

Ubuntu seems happy to see the drives as two seperate drives, ignoring any RAID setups on the card. Many people have reported this.

So I decided to setup the RAID Array's on the card as two seperate arrays, each in span mode, each with a single disk.  This essentially means the RAID side of the Promise will do nothing clever or silly with the disks.

The from the alternate install CD, I defined software RAID and LVM from this excellent HOWTO [https://help.ubuntu.com/community/FileServerOnLVMOnRAID1?highlight=%28raid%29](https://help.ubuntu.com/community/FileServerOnLVMOnRAID1?highlight=%28raid%29)

This means I can use all the good and reliable software RAID tools on Linux, use LVM, and all the experience and knowledge people have, and dont have a performance drop.  I also avoid the grief of dodgy drivers, and can run up to 4 IDE drives in my box, each on it's own channel. (2 onboard, 2 from Promise).

I investigating going to proper RAID, but the ones with the best linux drivers, 3Ware, start at $US500, and want Operton boxes etc. None available on eBay second hand. So software RAID will suit just fine, gives me the data security, performance and reliability I'm looking for in a reasonable budget.

Would I buy another Promise controller? No of course not. But I have to use what I've got for it's useful life, while I transition. Now most of my fleet is Ubuntu, I look at hardware from a completely different angle. Linux driver compatibility is top of the list. It means a change in brands in many cases.  Great brands like Asus, Adaptec, nVidia that I've used for years have to be looked at in a different light. Some models are ok, others forget it.  That's fine, I'm really happy to support other vendors who put a lot of effort into their linux drivers. There's a lot of linux hardware compatibility lists around, but few with real opinions. Like, I want to read, "This card/company has awesome, fresh linux drivers, better than all the rest, the gear goes really well, use it!"

---

### Post by IntuitiveNipple on 2007-01-08
I made some progress on this but am currently dealing with a GRUB issue now. The latest is in my article [Edgy: GRUB install fails with Error 6: Mismatched or corrupt version of stage1/stage2](http://www.ubuntuforums.org/showthread.php?t=333708)

Also, there is a related issue with FakeRAID stripes as well:   [Kernel Bug during IDE / hd probing](http://www.ubuntuforums.org/showthread.php?t=329995)

---

