---
title: "Inaccurate reporting in Windows Disk Management screen"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Quackers on 2011-01-25
This is the first time I have noticed this (and I've been in this screen several times). I am wondering whether I have missed it previously, or whether something has changed in Windows 7.
Could others confirm whether the same thing is happening in their system please? 
As you can see from the screenshots below, gparted reports the partition structure on my /dev/sda drive correctly.
ie 1 primary partition and 1 extended partition, containing 5 logical partitions.

However, as you can see from screenshot 2, Windows disk management screen shows that Disk 0 (/dev/sda) contains 6 partitions.
However, all 6 partitions are shown as primarys! 
Firstly, they are not primarys (as detailed in the other screenshot) and secondly, this is an impossibility on an mbr partitioned disc! :---)

Any comments please?

---

### Post by srs5694 on 2011-01-25
I've seen reports of this before, but I've not seen it myself. Given the reports of Windows converting logical partitions into primary partitions and therefore causing endless grief, it doesn't surprise me.

IMO, the Windows disk management tool should be used only when absolutely necessary (such as when resizing a Windows boot partition).

---

### Post by Quackers on 2011-01-25
I know what you mean srs5694!
I just thought that if it looked that way the last time I was in there I would have noticed. In fact, I'm almost sure there was a green surround to the logical partitions last time I looked, which declares them as logical, obviously. 
I'm thinking something has changed recently in Win 7.

---

### Post by coffeecat on 2011-01-25
Oo-er, you're right. I'd not noticed that before. :| My screenshots below. Like yours, the colour coding of my logical partitions is wrong in Windows 7 Disc Management, but the unallocated space is OK.

Also - My sda comes out as Disk 1 and sdb as Disk 0. What a mess. :-s

---

### Post by Quackers on 2011-01-25
Aha! That's interesting!
Your disk management screen shows no extended partition either, but it does show "free space", which is a Windows term for unused space within an extended partition! In Windows, unused space outside any partition is called "unallocated space", and is displayed with a thick black line (not light green).
So, it appears that Windows recognises that you have an extended partition on that drive, but doesn't show it. An extended partition in W7 should have a darker green surround than the "free space" green.
Very odd indeed :-)

---

### Post by coffeecat on 2011-01-25
Well - even more interesting. Vista makes a pig's ear of it as well. (Nothing new there then! :)) But what was showing as 'free space' in W7 is 'unallocated' in Vista. :-k

---

### Post by Quackers on 2011-01-25
One is unused space inside an extended partiton and one isn't (even if Windows doesn't show the extended partition).
And still toooooooooooo many primarys :-)  Dodgy Windows!

---

### Post by coffeecat on 2011-01-25
> **Quackers said:**
> One is unused space inside an extended partiton and one isn't (even if Windows doesn't show the extended partition).

Yes, you're quite right. I don't know how I came not to make the extended extend up to the end of the disc in the Vista machine. Ah well, that explains the discrepancy between Vista and Windows 7. But they're both describing logical partitions as primary, so at least they're consistent (ly wrong). :roll:

---

### Post by Quackers on 2011-01-25
They are indeed, but I'm sure Win 7 wasn't doing this a couple of weeks ago.
"Something is rotten in the state of Denmark" I fear :-) to quote the Bard.

---

### Post by Mark Phelps on 2011-01-27
Well ... I checked my Win7 machines -- and the Disk Management display is no different than it was months ago.  It still shows the same Primary and other partitions as it did back then.

I would hate to think that we're running different versions of Disk Management -- but then, stranger things than that have happened in MS Windows!

---

### Post by coffeecat on 2011-01-27
> **Mark Phelps said:**
> I would hate to think that we're running different versions of Disk Management -- but then, stranger things than that have happened in MS Windows!

Have you applied Windows updates recently? Both the Vista and W7 systems I checked were (reasonably) up-to-date. Perhaps an update has changed something in Disk Management because I'm sure I would have noticed all those "primary" partitions before, and Quackers was wondering whether something had changed.

---

### Post by coffeecat on 2011-01-29
I think I may have found the answer. All the logical partitions that Windows is reporting as primary ones are formatted with Linux filesystems - at least the ones screen-shotted in this thread so far. I have a laptop with Win7 and Natty and with a logical NTFS partition which Windows sees as E: See my new screenshot.

I haven't bothered with a Gparted screenshot, but the partitions, from left to right are:

Recovery 11.72 GB = sda1
100MB System Reserved = sda2
100Gb C: = sda3

Then there's the sda4 extended partition, in which:

3GB = swap = sda5
123.27GB NTFS = sda6
15GB = Natty root ext4 = sda7

Then 45 GB unallocated

As you can see, I didn't notice that Windows was pestering me to install some updates when I took the screenshot so, in view of my earlier comment, I shall do so and post back if it makes any difference. Whatever, if the updates don't change things it seems that Windows is so confused by a Linux formatted logical partition that it calls it a primary one.

Linux 40; Windows love, I think. :) Or perhaps, Quackers, one could say that Windows has been caught lbw! :wink:

**EDIT**: Updates applied, W7 rebooted and Disk Management still showing drivel.

---

### Post by Quackers on 2011-01-29
lbw indeed! Lol!
I think you may be right cc. That's not very good is it? Windows reports the wrong partition type because of the file system inside it! Strange!

Just before I took the screenshots I did run a couple of Windows updates. So, again, you might be right there too :-)

Well spotted, Inspector Clouseau :-)

Actually, thinking about it, I seem to remember Windows failing to recognise any Linux partitions at all previously. If that's right, something has definitely changed in Windows.

---

### Post by srs5694 on 2011-01-29
This could be related to the situation a few people have reported where the Windows installer tends to convert a logical partition into a primary partition, without adjusting the extended partition to match, when asked to install to the logical partition. If Windows thinks it's dealing with a primary partition, or if it thinks that the extended partition is surrounded by primaries, it might convert the logical partition to a primary without adjusting the extended partition.

If I'm right, that's very very buggy and very very bad.

---

### Post by coffeecat on 2011-01-29
> **srs5694 said:**
> If I'm right, that's very very buggy and very very bad.

Thanks for that thought. It may explain when I tried to get the Windows XP installer to convert a logical partition into a primary one, it wouldn't do so. But I was presenting it with a logical NTFS partition and so long as there was a primary NTFS partition for the boot files it was happy. I never thought to try to give it a logical partition formatted ext4 or whatever.

I smell another experiment coming on, :) but for another thread if I find anything worth reporting.

---

### Post by Quackers on 2011-01-29
All very interesting - but not good, methinks.

---

### Post by coffeecat on 2011-02-17
In the interests of completeness, and in my never-ending quest to try to reproduce the problem whereby the XP installer is allegedly "converting" logical partitions to primary ones, I have a screenshot from XP's Disk Management.

This is from a fresh install of XP Home edition from a service pack 2 install disc (genuine Microsoft), and no updates yet applied. Screenshots are from Gparted in the Lucid live session where I created the partitions and from XP's Disk Utility after I had installed XP to sda1. Interesting that XP identifies logical partitions correctly, even though it is mystified enough to call Linux ones 'unknown partition'. Better than in Vista and W7 but that leaves two questions still unanswered:

1 - Was it some update in Vista and W7 that caused this Disk Utility regression?

2 - If XP was fully updated, would it show what W7 and Vista have been showing?

---

### Post by Quackers on 2011-02-17
Your tireless efforts deserve credit sir!
If memory serves, the disk management fiasco occurred after a couple of small updates. Previous to those, the disk management screen failed to recognise any Linux partitions at all.
In any event my Win 7 installation has not been touched or re-installed in between the 2 different outputs for disk management. I can only conclude that those updates amended the utility in this way.

---

### Post by coffeecat on 2011-02-17
> **Quackers said:**
> If memory serves, the disk management fiasco occurred after a couple of small updates. Previous to those, the disk management screen failed to recognise any Linux partitions at all.
In any event my Win 7 installation has not been touched or re-installed in between the 2 different outputs for disk management. I can only conclude that those updates amended the utility in this way.

Possibly in Windows 7, but....

I happened to have a Vista Home Premium install DVD (as you do), so I installed it to the 20GB partition that XP was on. That was a struggle! Vista had to take a deep breath in and slide in sideways. :) Anyway, screenshot below to correspond to the two that I posted in post #17. That's a fresh install - no updates - from a service pack 1 Vista DVD.

Six primary partitions, indeed. :-s

---

### Post by Quackers on 2011-02-17
Maybe Vista had the same updates? Just thinking out loud here :wink:

oops, my bad, you already said no updates! I must learn to read!

---

