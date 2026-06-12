---
title: "RAID 1 with Windows and Linux"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by H4rm0ny on 2010-10-04
Hi,

I'm doing a complete re-build of my system. I want to create a couple of RAID-1's of two disks each. I've read a lot about this but I'm *still* not sure what is the best approach.

I have an ASUS M47A9XTD EVO motherboard which according to the manual has the SB750 chipset which supports RAID 1. It has six internal SATA ports.

I want to install both Windows 7 and Ubuntu. I have a 64GB SSD, two 500GB HD and two 160GB HD (all SATA, obviously). I want to partition the SSD to be the Windows C:/ and the Linux / . I want to put the two 160GB into a RAID 1 and format as NTFS for extra Windows space (but I'll want the Linux system to be able to mount it as well). I want to put the two 500GB drives into a RAID 1 and partition them for /home, /var and /srv .

Sorry for the lengthy intro, I want to make it clear what I'm after as my questions might not be well-phrased due to my lack of knowledge. What I want to know is:

1. Which will give me the best performance? Enabling RAID on the motherboard or leaving it to the O/S?
2. I've read that the motherboard's RAID actually hands most of it off to the O/S, so will there be any problems if a RAID is sometimes managed by one O/S and sometimes by another?
3. Same as 2 but what if I leave it entirely in the hands of the O/S? Will the two O/S's conflict?
4. Does the motherboard's RAID functionality do anything "funny". I've read horror stories of proper RAID cards mangling everything up in some unrecoverable proprietary format and that's the last thing that I want.
5. Does it make any difference which SATA ports I plug the disks into? E.g. should two disks in a RAID go into ports 1 & 3, or 2 & 3 or is it all irrelevant?

Sorry if the questions are a bit odd. I have no experience with RAID. If there's anything I've missed or misunderstood, please let me know.

Thanks,

Harmony.

---

### Post by pricetech on 2010-10-04
> **H4rm0ny said:**
> 
1. Which will give me the best performance? Enabling RAID on the motherboard or leaving it to the O/S?
Hardware RAID is always best.
> **H4rm0ny said:**
> 
2. I've read that the motherboard's RAID actually hands most of it off to the O/S,
Renders the rest of the discussion pretty much moot.  The fakeraid will not work under Linux, so software RAID is your only choice.  Linux will not be able to see your proposed NTFS RAID volume since it's not actual RAID.

---

### Post by psusi on 2010-10-04
> **pricetech said:**
> 
Renders the rest of the discussion pretty much moot.  The fakeraid will not work under Linux, so software RAID is your only choice.  Linux will not be able to see your proposed NTFS RAID volume since it's not actual RAID.

Yes, it will.  The fake raid is not as well supported and reliable as software raid, but it is the only way to work under both windows and linux.

---

### Post by ronparent on 2010-10-04
Enabling raid on the mother board is the only way for Windows and Ubuntu to both access the same raid partition - primarily for accessing data on a compatible files system for both. That is a fakeraid. Both fakeraid and software raid are primarily software based. A pure linux software based raid partition is not usable by Windows because Windows has no drivers or programs to support it.

This statement is completely wrong.
> The fakeraid will not work under Linux, so software RAID is your only choice. Linux will not be able to see your proposed NTFS RAID volume since it's not actual RAID.

NTFS fakeraid partitions created by windows are fully accessible to linux through the linux dmraid program. The MB raid (fakeraid) has to be activated in bios. The mdadm based software raid is usable only to linux based OS's.

A true hardware raid is usually on a separate board and is mountable on any OS for which the drivers are available.

---

### Post by pricetech on 2010-10-04
I guess I"m using old information then.  My apologies.

But at I got the OP some responses.

---

### Post by H4rm0ny on 2010-10-06
> **pricetech said:**
> I guess I"m using old information then.  My apologies.

But at I got the OP some responses.

That you did. ;)

Thanks for all the replies. For the sake of those that Google into this thread, I'll just post what I've ended up doing. For now, I used the motherboard's own "fakeraid" and both Windows 7 and Ubuntu picked them up fine. Windows 7 was actually more confusing because although it correctly saw just the one disk (at least after I'd installed the RAID drivers from the ASUS website), there were still options to create a software RAID on top of that. But I just created a "Simple Volume" and it's working great. Very zippy! The Ubuntu install helpfully picked up that there was something RAIDey going on and asked if I wanted to roll with that (not the precise phrasing). I said yes and thereafter the partitioning and install went okay. I haven't used it enough yet to say if performance increase is significant due to the RAID, but it's looking good.

Currently I can't see the "Windows" RAID from Ubuntu so I'm going to have a bit more of a fiddle with that this weekend and see if I can mount it. Hence I'm not going to mark this thread "Solved" today.

Thanks for all replies.

---

### Post by ronparent on 2010-10-06
Glad to hear you are getting results. If you go to the menu bar Places>Computer you should see all of your raid partitions listed a separate drives. Simply click on each one you want to mount and it will thereafter for the extent of the session appear as an icon on the desk top. 

To think of it, I'm not sure if dmraid is automatically installed when  Ubuntu is installed to a non-raid drive. That can be fixed by 'sudo apt-get install dmraid'. Once installed you should see the Windows raid's automatically on boot. Will watch to see how you make out.

---

