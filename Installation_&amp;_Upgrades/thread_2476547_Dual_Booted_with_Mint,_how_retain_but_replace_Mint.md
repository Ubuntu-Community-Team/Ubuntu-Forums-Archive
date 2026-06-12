---
title: "Dual Booted with Mint, how retain but replace Mint with Ubuntu?"
date: 2022-06-29
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2022-06-29
Up Date: I think the easier solution is to simply delete anything on drive for Mint, so will everything for Mint be contained within the one partition name as Mint, or are will there be a few others?

I've dual booted Win and Mint. I now want to replace Mint with Ubuntu without erasing Win.  How do I proceed?  I started the install, and it can see only LinuxMint, which I want to over write and leave Win alone.

(Already downloaded latest Ubuntu on USB.)

---

### Post by tea for one on 2022-06-29
Is Windows (unknown version) hibernating?
Is Windows (unknown version) encrypted?
One disk and two systems?
Two disks each with an OS?
Ubuntu version?

You will need to provide more details so that help can be forthcoming?

Why not run boot-repair so that many questions can be answered without an interminable question and answer session?

Can you boot into an Ubuntu live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread.

---

### Post by mawil10132 on 2022-06-29
I'm taking a new direction, to simply delete Mint off drive, which leads me to the question; is all of Mint be in the one partition marked as Mint? or are there a few other partitions that will need to be deleted also. If you can answer that I would be grateful. 


> **tea for one said:**
> Is Windows (unknown version) hibernating?
Is Windows (unknown version) encrypted?
One disk and two systems?
Two disks each with an OS?
Ubuntu version?

You will need to provide more details so that help can be forthcoming?

Why not run boot-repair so that many questions can be answered without an interminable question and answer session?

Can you boot into an Ubuntu live session and download the boot-repair utility.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
2nd option – Create boot-repair summary and post the pastebin link to the report in this thread.

---

### Post by guiverc on 2022-06-29
How Linux Mint was installed will control what exists on your drive; ie. what release you used, and what options you used with installing it.  That may contain one or more partition(s) depending on a number of factors you've not provided, including details of your hardware (is it uEFI or *legacy*). 

The box I'm using had Linux Mint on it; as when I purchased it (*it was second hand*), I always use a system for a few weeks with another OS to confirm the hardware works as expected; including some stress testing of it, then I usually  clean install the actual OS I wish to permanently use.  I decided to use  Linux Mint as my *test OS* so I could look at it awhile.  This system was setup dual boot too, though not with windows. 

In my own case; I decided I liked some of the things from Linux Mint, so I cleaned up the system & **didn't *clean*** install Ubuntu onto it; I just manually deleted what I didn't want to survive, then just installed Ubuntu Desktop over it (*without format, so what I wanted to survive the install did survive; having manually deleted what I didn't want to survive; or may have impacted the type of install I was going to use*).

You'd need to ask whomever installed your Linux Mint as to what was installed on the system, otherwise look at the system itself.  The person who installs it dictates how it gets installed, and thus what you have on your system.

---

### Post by yancek on 2022-07-01
If you have only some version of windows and Linux Mint installed, boot Mint or the Ubuntu USB and from a terminal run:  sudo parted -l which will list the partitions and show the filesystem type.  If you see ext4 under Filesystem, it is Mint.  If you see ntfs it is windows.  If you have a fat32 partition with the Name EFI system partition, don't delete it, just the ext4.  You could also simply install Ubuntu to the Mint partition(s).l

---

