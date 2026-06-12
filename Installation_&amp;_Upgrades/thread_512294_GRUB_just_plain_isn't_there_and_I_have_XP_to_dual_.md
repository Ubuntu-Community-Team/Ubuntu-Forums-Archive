---
title: "GRUB just plain isn't there and I have XP to dual boot?"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by JoJo on 2007-07-29
<edit> So I realized this post is long.  I want to dual boot Windows and Ubuntu and Grub is missing. </edit>

Okay so my computer is kinda complicated.  This is what I want: a partition for Ubuntu, its corresponding swap space,  a partition for XP x64, another partition formatted in NTFS for my media, and on a separate drive, an old install of XP which isn't correct for my hardware and will just be used as slave.

The properties of the partitions are as follows:
hda1- (old incorrect for hardware version of XP) - 111 gb - NTFS - boot flag
sda1- (Ubuntu) - 18 gb - ext3 - Operating System
sda2- (swap) - 2.00 gb - linux-swap
sda3- (media) - 320 gb - NTFS - boot flag
sda4- (extended) - 125.75 gb - extended - lba flag
sda5- (XP x64) - 125.75 gb - NTFS - Operating System


The master boot record is written to the old drive cause it's not a SATA drive and it has something to do with the hierarchy of hardware.  

What I've done with my computer is this: Assembled it, put in the 500 gb SATA drive.  Installed 20 gb of Ubuntu and corresponding swap space.  Then I decided to use XP and installed another 20 gb of that.  When I booted my computer now, there was no sign of Ubuntu.  I left it this way for 6 months.  Then I stuck the old drive in from another computer.  Then came 400 gb of slave media space.  I left the last bit of space unpartitioned.  Then I ran out of room on my XP partition.  I took and shrank the media space down to 300.  I copied my XP install over to where the media partition ended.  I deleted the original.  I enlarged the media space to engulf the 20 gb that the original XP partition left behind.  I enlarged the new copy to fill up the rest of the drive.  I screwed up the the operating system by trying to mod protected system files, and needed to reinstall it.  I did so with a friend, turning off my old drive which was first in the drive hierarchy so the master boot record did not get written to it.  The master boot record was written to the media space.  Then, the very next week, trying to modify more protected system files, I reinstalled XP again, but this time I forgot to turn off the old drive, so then the master boot record was now written to it.

And that is the story of the partitions on my computer.  Now I am trying to reinstall Ubuntu, but GRUB simply is not there at all and it just boots into Windows.  Well, the first time it rebooted, it gave me that screen saying something has messed with Windows and do I want to boot into safe mode and I can say yes, safe mode, or no boot Windows normally.  So I boot windows normally.  Then I restart again, and that screen doesn't come up at all.  It's as if Ubuntu isn't even there.

So I install GRUB again per instructions I found in a thread on here.  (I tried to find the thread again, but I've been using the live cd and don't have my bookmarks.)  And I restart and I get the same screen asking me if I want to start Windows in safe mode.  GAH!!!!

All I want to do is dual boot Windows and Ubuntu.  :neutral:

---

### Post by rillip on 2007-07-29
I recommend you google for the supergub live cd, boot that and install from there

---

### Post by manndani on 2007-07-29
If you've got a live cd  look at this thread (compliments to "Catlett") 
[http://tinyurl.com/2kmugw](http://tinyurl.com/2kmugw)
Great instructions for re-doing grub from the live CD, really good instructions & easy to follow.
I've used it and I'm greatly in "Catletts" debt, saved me a heap of hassle.

---

### Post by Pumalite on 2007-07-29
Or you can use Super Grub which is a more powerful tool:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

