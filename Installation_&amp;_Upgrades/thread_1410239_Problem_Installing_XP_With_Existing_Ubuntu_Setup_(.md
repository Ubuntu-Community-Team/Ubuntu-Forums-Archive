---
title: "Problem Installing XP With Existing Ubuntu Setup (Partitions)"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by bluebledthesea on 2010-02-18
Hi Everyone-

I'm using Ubuntu 9.10 and previously had a separate partition with another distro on it. I decided to delete the other distro's home and swap partitions and install XP in place of it. I've been following these instructions:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3")
and
[http://ubuntuforums.org/showthread.php?t=1389369]("http://ubuntuforums.org/showthread.php?t=1389369")

I have gotten to the point where I am booting to the XP CD and want to install it, but I get the message, "Setup did not find any hard disks installed on your computer" when I should be getting to the screen that asks me to select a partition to install XP on. 

This is what my HDD looks like in GParted:
[IMG]http://imgur.com/9INAP.png[/IMG]

I want to install XP in the unallocated partition, but I have a feeling I screwed up somewhere along the way and probably don't fully understand the whole thing. Even if I try to format the unallocated partition to NTFS I can't make it a primary partition (I assume because it's within sda2).

The very last thing I want to do is delete my Ubuntu partition and start from scratch, but if that's my last option let me know.

---

### Post by darkod on 2010-02-18
You didn't "screw up" anything, but yes, you didn't understand it fully.

1. Windows needs to be on primary partition, so you won't be able to install inside extended, especially XP.

But that is not your main issue.

2. XP can't see SATA disks, it doesn't have sata drivers by default. They were only introduced in vista. While Linux had them ages ago. :)

So that is why it's not showing you the disk.

Additional issue is that it wants the drivers to be supplied on a floppy, so if this is a laptop without one, or desktop, forget about it. Another option is to find the sata drivers for your board and have them "slipstreamed" into XP, with program called nlite for example. It's free and google will give you lots of tutorials to use it, also the website of the software has instructions.
With newly created XP disc like that, it will see your hdd. But don't forget it needs primary partition.

You could shrink /dev/sda2 so that the unallocated space is behind the extended partition instead of inside it. It doesn't matter whether the primary partition will be after an extended, as long as it is primary.

---

### Post by bluebledthesea on 2010-02-18
Wow, that makes so much sense. I totally forgot that my laptop came preinstalled with Vista and I've never made an attempt to put XP on it before. I will see if I can manage that nlite procedure you suggest, but I may have to try something like ReactOS or Vista as a last resort. This laptop has no floppy.

Thanks for the tip on "shrinking" sda2 as well. I knew there had to be a way to get that unallocated space out on its own. Thank you darkod!

---

### Post by bluebledthesea on 2010-02-18
Just wanted to let you know I figured out the slipstreaming with nlite and everything went perfectly! That program is awesome. Thanks again!

---

### Post by darkod on 2010-02-18
No problem, glad it worked out OK. Now you have XP that you can always install on your computer without worrying about SATA. Too bad it won't work on other computers unless the drivers match.

---

