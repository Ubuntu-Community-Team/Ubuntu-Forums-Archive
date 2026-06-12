---
title: "Grub/hard drive error after re-partitioning"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by HumbleGod on 2007-05-15
Here's the short version: I was trying to shrink my / partition and grow my /home partition using the gparted live cd. Gparted apparently gave up halfway through. Now grub won't start when I boot my system, and most of my / partition seems corrupted. My question is: now what?


Long version:
I'm a relative newbie with Ubuntu, having only used it for a couple of months. I recently set up a new partition for /home and was planning to move my various media files to that partition, but I needed to juggle the free space from / to /home.  Here was my hda setup before running gparted:
*NTFS partition (storage for XP)* *EXT partition for /home* *EXT partition for /* *Logical partition for swap*

My goal was to shrink the / partition by about 19 gb (36 gb were free) and move the filesystem to the right, then expand the /home partition to use this new space. As I'd done similar work before when transferring files from the NTFS partition to the / partition (this was before I setup a separate partition for /home), this seemed like a cakewalk. I told the gparted live cd gui to do this, then left it running and went to work.

When I returned eleven hours later, the readout said it was still "moving the filesystem to the right" and had six hours to go. This seemed odd to me, but it said it was doing 64kb clusters (I think), so I just turned off the monitor and went to bed.

When I woke up this morning, the gparted program was closed though the live cd gui was still up (showing options like Exit, etc.). I hoped this meant everything was successful--it had done this before after successful re-partitioning. I rebooted, but when it tried to start grub, it just sent me to the cmd line warning that a minimal amount of BASH editing could occur there.

I'm on my XP system now (booting from a different hard drive). Thanks to ext2IFS, I can see that my /home partition on hda looks okay, as does the NTFS partition. / looks buggered, though. Some files are accessible, but most seem corrupted--folders that I know were brimming with files (such as /usr/share/pixmaps) are now empty, and most remaining files in other directories don't have extensions showing.

So my question as a newbie is now, what can I do? What program can I run to try to recover everything? Or is it too late for me to do anything but move the few recoverable files, reformat the / partition, and reinstall Feisty?

---

