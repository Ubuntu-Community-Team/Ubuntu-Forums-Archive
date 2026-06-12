---
title: "Noob trying to install 10.10 on a new HD."
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by ions82 on 2011-03-10
I'm not the most savvy when it comes to dealing with the intricacies of all things binary.  I work at a place that "refurbishes" donated computers, and I am hoping to make Ubuntu our main OS (instead of the XP that has been the standard up until now).  We created an install disc and put it on a couple systems.  It went smoothly for the first two, but I've run into a problem on the last one that I've tried to load.  It started to boot (from the disc) but then displayed an error.  I did a basic search in the forum and found that others have had a similar problem, but all of those described the problem on a system that already had the OS installed.

Anyway, here is what I'm getting.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


I have no clue what any of that means.  Is it an issue with the new hard drive?  I tried creating partitions and formatting them in ext3 (as suggested by a more tech-savvy coworker).  If anyone can tell me what in the heck I'm doing wrong, please post!  I really don't want to install any more copies of Win-blows XP.

---

### Post by ions82 on 2011-03-11
Oh, man.  60 views and no replies.  If anyone can at least tell me where to go to look for a solution, it would be helpful.  I have no idea what to do with this situation.

---

### Post by oldos2er on 2011-03-11
Did you check the CD integrity? What are the system specs of the computer?

---

### Post by ions82 on 2011-03-11
> **oldos2er said:**
> Did you check the CD integrity? What are the system specs of the computer?

The instructions (for creating the boot CD) said that I just had to check to make sure there were multiple files/folders on the disc after it burned.  I made two copies.  The one I had originally made seemed to work fine, but my coworker took it home and never brought it back.  I saw another thread in which someone had posted the "script output" from an issue they had.  Is that something that would be helpful for this situation?  I'll have to try and figure out how to do that.

The system is a 3.0 GHz P4 with 2Gb 533MHz RAM, 2Mb cache, 800MHz bus...

---

### Post by Hedgehog1 on 2011-03-11
ions82

I think you are getting bitten by the lack of any partition table on the new hard drive.

Depending on how the drive was quality tested, is may or may not have a partition table on it.

Here is thread that explains it nicely: [READ POST #5]("http://ubuntuforums.org/showthread.php?t=1704895")

You can use gparted on the LiveCD/LiveUSB and create the parition layout on the drive.

I suggest 3 partitions:

1) 30 gig for '/' (Your OS and boot)
2) swap partiton about 1.1 times the size of your ram
3) the rest of the drive as your '/home'

***The Hedge***

:KS

---

### Post by oldos2er on 2011-03-11
There should be an option on the LiveCD menu to check the disc integrity, or you can check the md5sum: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

What video card does it have?

---

