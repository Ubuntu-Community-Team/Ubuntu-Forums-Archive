---
title: "Upgrade failure and problems"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2010-01-18
I read the "manual" I searched the forum, I read another "manual", I searched another forum. I searched "documentation" I searched Google and I read and I read and I read.
Confidence is low.

I previously had Jaunty 9.04 installed which got screwed up during an attempted install of Mediabuntu. I do not know how or why.
 
 I have burned CDs for both Jaunty and Karmic (2) run the all of the various installs which fail at one point or another and then the system locks.
I tried doing an MD5sum - and there was a match. Yet it appears there are 4 files missing or corrupted.
 I used a Live Cd to try the package manager upgrade - no luck. System locked up
 I am in the system now with a live CD and can use the terminal the above e2fsck info is where I am at this point.

Here's what I have tried so far:

In terminal I entered fsck
the response was: util-linux-ng 2.16
I could not find what that meant - anywhere.

In terminal  under "Emergency Help" I entered fsck -p (automatic repair "no questions" )
The response was: command not found

I then tried **e2fsck** and got:

[-panyrcdfvtDFV] [-b superblock] [blocksize] ;-I inode _buffer_blocks] [-P process_inode_size] [-some sort of squiggly L l | -L bad_blocks_file] [-C fd] [-j external_journal] [-E extended-options] device

I then tried **e3fsck** and the response was:
Segmentation fault (core dumped)



I am stuck. I don't care if I have to wipe the drive or throw it in the river. If there is a fix through Ubuntu I will try it first. 
I would appreciate it if someone could give an answer that a newbie can understand.

Thank you

P.S. I am not on that machine, which is why I can't post the output.
I also replied to a post in Absolute Beginners with a version of this, but then figuered here would be best. Sorry if that's a no-no

---

### Post by tachuela on 2010-01-18
I suspect that at this point your 9.04 is toast. But is it is not; try to save whatever you can; reformat the drive ext4 and try again with a bootable, non corrupted Live CD

---

