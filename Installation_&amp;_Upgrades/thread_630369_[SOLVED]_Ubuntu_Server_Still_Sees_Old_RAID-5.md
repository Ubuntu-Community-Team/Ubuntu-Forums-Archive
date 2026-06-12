---
title: "[SOLVED] Ubuntu Server Still Sees Old RAID-5"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by bigwayne on 2007-12-03
Hello!

Failing an answer on other forums, and after three days of scouring the Internet looking for help, I've run completely out of ideas on how to solve this problem:

**History (this is important :???:):**

I've got a 16-disk SAN I'm setting up at work, running Ubuntu Server (7.10). There were originally two RAID-5 arrays: one 7-disk array, and one 8-disk array. First array was /dev/sdb through /dev/sdh. Second was /dev/sdi through /dev/sdp

Software RAID, managed through mdadm.

Long-story short, the configuration was scrapped and I need to remake this system.

**The here and now:**

We're setting up the system to boot from a RAID-1 configuration, split between the first disk on the first raid controller, and the first disk on the second raid controller. That part is fine, until I get to the part in the Ubuntu installation where I set up the RAID configuration:

[COLOR="RoyalBlue"]Despite what I've tried (see below), when I configure the disks that used to be in an array, the installer sees the old RAID-5 array that the disk used to belong to, and I'm unable to use the disk for my own purposes.[/COLOR]

**Things to note (things I've tried, caveats):**

[LIST]
[*]The RAID arrays aren't detected until I try configuring software RAID, then it detects them and I'm unable to get rid of them
[*]I'm unable to destroy the RAID-5 array, the partitioner says it can't do it, the array "might be in use." It's not
[*]I'm able to create/destroy OTHER meta disks in the installer, just not the RAID-5
[*]I'm unable to trick it by swapping a physical disk from the first array with the disk I want to use for the new array, the RAID-5 array messes up its component configuration but is still there
[*]*cont'd:* I've tried just ignoring it when it messes up and releases the disk I want, but the RAID-1 I try making with it freezes during "package verification," presumed that something happened during RAID building, though I got no error or indication (except that the machine itself is now using the two disks pretty steadily, can I assume it's scanning behind the scenes?) Additionally, the meta disks arrays can't be dismantled ("array in use" again)
[*]I've tried scrubbing the MBR of anything it knows (via "dd" in a knoppix session)
[*]I've utterly hosed the original installation disk beyond recovery, so I can't go back and demote the drives from the array the proper way
[*]I'm a very, very, very new Linux user. If you have any suggestions, please provide some command-line instructions, or links to sites where I can find what I'm looking for (short of taking a few days and zero-ing the drives, we need this SAN this week, haha)
[/LIST]

I thank you in advance, and I apologize if this turns out to be a dumb question with a beyond-simple answer.

---

### Post by bigwayne on 2007-12-03
Just an update for you, I appear to have fixed this.

Boot into Knoppix, run "mdadm --zero-superblock <device>" over all the drives, and it fixed it.

---

