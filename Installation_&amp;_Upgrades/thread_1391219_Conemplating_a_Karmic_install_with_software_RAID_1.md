---
title: "Conemplating a Karmic install with software RAID 1"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by ladasky on 2010-01-26
Hi folks,
 
I'm running a triple-core AMD 32-bit CPU, with two matched hard drives in a software RAID 1 configuration.  The system is single-boot, running Hardy only.  I have no Windoze compatibility issues to impede me.

In some recent posts, I discussed my desire to add a few non-standard applications to Hardy.  Well, it hasn't been working for me.  I've succeeded in breaking my standard Python 2.5 installation, and the Python 2.6 that I was trying to install is also broken.  After asking questions in various Python forums and not getting answers, I'm starting to think about my alternatives.
 
I have backed up all my hard-drive data, and downloaded Karmic.  I'm running from the Live CD.  I am considering a clean install, though of course I would save a lot of time if I could just upgrade.
 
Before I leap, I see one possible problem: Karmic has failed to mount any of my hard drive partitions, as RAID or otherwise.  Should I worry?  When I upgraded from Dapper to Hardy on an older (non-RAID) machine, I recall that my hard disk mounted from the Live CD just fine.
 
Also, am I correct in understanding that Karmic is RAID-aware right out of the box?  I'm wondering if I'll have to set it up manually again.  That took me a while.
 
By the way, I didn't set up separate partitions for boot, root and home (stupid me).  Can I do that after the fact during an upgrade?
 
Thanks for your advice!

---

### Post by darkod on 2010-01-26
I'm no expert in raid but the first thing to know is you need the Alternative Install CD (image), not the standard live cd. Maybe that's why it's not seeing the raid array.

Also, for fakeraid (motherboard raid) maybe this will help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

For software raid, created by the OS itself (no BIOS settings):
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

The software raid sounds like a better option and looks simple as long as you follow few recommendations.

---

### Post by ladasky on 2010-01-26
> **darkod said:**
> I'm no expert in raid but the first thing to know is you need the Alternative Install CD (image), not the standard live cd. Maybe that's why it's not seeing the raid array.
 
Oh, that's right. ](*,)  Starting another download now... 

> Also, for fakeraid (motherboard raid) maybe this will help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
 
No, I'm sure that won't help me.  Linux FakeRAID installations exist for compatibility with Windows RAID.  As I mentioned, I bypassed all of that, and went directly to Linux software RAID.

> For software raid, created by the OS itself (no BIOS settings):
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

The software raid sounds like a better option and looks simple as long as you follow few recommendations.

That's what I did before, when I set up the RAID on Hardy.

---

### Post by darkod on 2010-01-26
I was assuming when you said software raid, but just in case. Some people also call fakeraid software raid because in fact it is software based (as far as I've read about raid). :)

---

### Post by ladasky on 2010-01-26
> **ladasky said:**
> 
By the way, I didn't set up separate partitions for boot, root and home (stupid me).

WRONG, I DID have a separate /home partition, I just forgot about it!  I planned ahead!  :D  (You know you're a total nerd when stuff like this excites you.)
 
I just finished the upgrade to Karmic using the alternate install disk.  I went through the partition process manually, though I'm not sure that I had to do so.  I didn't actually change my partitions.  However I did notice that the mount point information appeared to be missing, so I re-entered it.
 
I have verified that the new installation HAS preserved my RAID 1 intact!  I don't have to restore my data!  The Palimpsest Disk Utility looks nice.

I don't have audio yet.  I understand this is a common issue with Karmic.  I won't clutter up this thread with comments about minor and unrelated issues, so...
 
All in all -- this looks like it was a fairly painless upgrade.  I was not expecting that!

---

