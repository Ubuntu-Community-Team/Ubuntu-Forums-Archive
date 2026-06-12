---
title: "How to assign partitions?"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by burgerearl on 2009-11-18
I tried ubuntu with some success back in 7.10 (dual booting alongside XP) and eventually got stuck with a non-functioning installation (can't remember exactly why - I think it was an X issue. [_Here_]("http://ubuntuforums.org/showthread.php?t=641609") is a thread for some of what I did with this machine's partitioning, although I don't even know what I'm talking about for part of it). I never got around to clearing out the old installation, so all of those partitions are still in place and I still boot XP through GRUB.

I'm now trying to give it another shot and have downloaded the 9.10 image. I was trying to use unetbootin's ability to run the live CD from the hard drive in order to install since at present I neither have a blank CD nor a sufficiently large USB key.

The "live CD" booted fine and I started the installation, only to become stuck at partitioning. I seem to remember the process being more automated, and need some help to move forward.

The partitions listed were as follows:

Name  Format  Size
/dev/sda1  fat16  82mb
/dev/sda2  ntfs   32210
/dev/sda7  fat32  51728
free space        8
/dev/sda6  ext3   30721
/dev/sda5  swap   2048
/dev/sda4  fat32  3224

I know that when I set up the original dual boot I created a partition that I intended to be for sharing documents between the two OS's. I believe that's what sda7 is. The install utility told me that it was running from sda2, which leads me to believe that's my Windows partition (maybe that's obvious to everyone else...). If there are other unexpected partitions there, see the above thread - I tried to get clever with booting and I understood better back then what partitions I have and why.

I gather that I should assign sda6 as / and format as ext4. I would also assume that I should maintain sda5 as swap. I noticed that /windows is a mounting option for fat32 partitions. Do I need to do anything with that vis a vis my Windows partition at install time?

Other than that, I have no clue. I don't know what sda1 or sda4 are for.

I do *not* care about maintaining the special boot function in the above thread, if ditching that would simplify the way forward.

Thanks!

---

