---
title: "Can Ubuntu read NTFS natively?"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by miketootall on 2010-02-26
I am thinking about switching my home server from Windows 2003 Server to Ubuntu.  I have four hard drives in the server, one system drive and three that have all of my stuff (music, photos, backup etc) that are all formatted to NTFS.  My question is, when I convert to Ubuntu, is there any way I can leave the three backup hard drives the way they are?  Or is it recommended that I reformat them to whatever file system Ubuntu prefers.

Thanks!

---

### Post by darkod on 2010-02-26
Yes, it can read it. I have a partition to share between windows and ubuntu. It doesn't mount them automatically though, you'll have to set it up yourself.
You can mount a partition occasionally, or if you need it regularly there is a way to set up auto mounting on start.

I'm fairly new to linux, but I believe ext3/ext4 would offer better performance than ntfs. It would also allow you other things if you don't need dual booting, for example I would definitely consider using LVM.

However, leaving them as ntfs for a start is no problem at all.

---

### Post by miketootall on 2010-02-26
Another question, will I be able to write to the NTFS partition?  I know NTFS has some security built into it, will this keep me from writing to it?

---

### Post by darkod on 2010-02-26
> **miketootall said:**
> Another question, will I be able to write to the NTFS partition?  I know NTFS has some security built into it, will this keep me from writing to it?

As far as I know, 9.10 is good with ntfs read/write. Not sure about earlier versions, but these days linux is OK for ntfs read/write.

---

### Post by Objekt on 2010-02-26
Yes, you can access NTFS volumes from within Ubuntu.  

In the past, there were some problems with the NTFS implementation in Ubuntu, ntfs-3g.  However, supposedly the performance, error handling, and everything else are just as good with ntfs-3g now as they would be with ext3 volumes.  So it probably doesn't really matter which filesystem you use.

---

### Post by recluce on 2010-02-26
I have not used NTFS with Karmic, so anybody correct me if what I write, based on Jaunty, is outdated.

NTFS works fine mostly, reading and writing is possible and reliable, the performance penalty by using a fuse-based filesystems is small with a half-way decent CPU.

But there are a few drawbacks:

- error checking of NTFS volumes is basic at best, you need Windows to do more complex repairs of NTFS volumes

- Ubuntu causes errors in the volume bitmap that Windows detects and corrects, also you get frequent index errors, that can be corrected by Windows without issue. 

- Linux does not offer a defragmenter, NTFS is extremly prone to fragmentation. So long-term performance will suffer

Best approach would be to convert the drives to ext3. ext4 still may have issues with large file transfers in certain Linux kernels, but an ext3 volume can later be converted to ext4 without reformatting, so once Lucid is out and no more reports about file corruption surface, it would be easy to convert the filesystem.

While you are at it: why not use a Linux soft-RAID for added peace of mind?

---

### Post by miketootall on 2010-02-26
I have never heard of soft-RAID, what is it?

I'll probably just convert the drives to ext3, I want this to be a reliable server.  Its an old computer, about 7 years old, p4-3.0ghz, 2gb ram.  I am thinking about going RAID, can you guys recommend a good RAID controller card that works well with Ubuntu?

---

### Post by DawieS on 2010-02-26
If you are going to use NTFS in Karmic, and don't want to type in your password each time to mount a partition, see [this]("http://ubuntuforums.org/showthread.php?t=1409347") thread.

---

### Post by HalfWord on 2010-02-26
> **miketootall said:**
> I have never heard of soft-RAID, what is it?
...
I am thinking about going RAID, can you guys recommend a good RAID controller card that works well with Ubuntu?

Soft-RAID means that linux kernel driver manages the RAID array (in software) instead of a RAID controller (in hardware).

 Two notes here, first, some (most) cheap (i.e. not prohibitively expensive) raid controllers are actually simple storage controllers which also include software raid management in their drivers and BIOS, in which case the linux soft-raid is actually a safer bet. Some of those chips do offer some raid acceleration in hardware, but those are mostly XOR calculations required for RAID-5 and similar levels, but even that wouldn't make much of a difference if the server doesn't experience very heavy loads, and none if you use only levels 0 and 1. If the card has cache memory it helps in any case, but I doubt you'll find an affordable card with that option...

The second concern is if you use any RAID level other then 1 (mirroring), you could have problems reconstructing the RAID to get your data in case the controller fails, and you cannot obtain another one.

---

### Post by miketootall on 2010-02-27
Very interesting, thanks for the info!  I'll keep that in mind as I build this Ubuntu server.  I was going to get a controller card, because the motherboard I am using is old and doesn't have it built in.  Soft-RAID sounds like it might be a viable alternative.

---

