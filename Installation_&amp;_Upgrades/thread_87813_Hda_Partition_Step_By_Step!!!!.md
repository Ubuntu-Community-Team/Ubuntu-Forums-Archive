---
title: "Hda Partition Step By Step!!!!"
date: 2005-11-08
forum: Installation &amp; Upgrades
---

### Post by eyebrowman92 on 2005-11-08
Ok Heres The Deal. I Havent Gotten The Windows Installation Cd Yet, But When I Do I Want To Be Ready. I Want To Put Aside A Small Amount Of My Harddrive Or Whatever To Hold Windows When It Comes. I Want The Majority To Be Linux. Can Someone Please Tell Me How To Do This Step-by-step. Thanks.

---

### Post by aysiu on 2005-11-08
Do you already have Ubuntu installed and you're trying to add Windows? What's your current set up? What are your specifications (hard drive space, for example)? Any reason all of your words are capitalized? Something funky going on with your keyboard?

P.S. Moved you to a more appropriate forum.

---

### Post by eyebrowman92 on 2005-11-08
i was typing in caps by accident. and all i want to do is make my linux partition (which is right now the entire 40 gb disk) smaller. i want to make it about 30 bg and leave 10 gigs of free space.

---

### Post by aysiu on 2005-11-08
[QUOTE=eyebrowman92]i was typing in caps by accident. and all i want to do is make my linux partition (which is right now the entire 40 gb disk) smaller. i want to make it about 30 bg and leave 10 gigs of free space.[/QUOTE] So you want to shrink the 40 GB partition down to 30 GB and then put Windows on the 10 GB of free space? Well, you're going to have to do this:

1. Back up everything. Everything.

2. Shrink the partition (a good live CD like Knoppix, which has QTParted on it, will help for this--make sure the partition you want to shrink is *not* mounted)

3. Install Windows, picking the new 10 GB partition.

4. [Restore Grub to the MBR.](http://ubuntuforums.org/showthread.php?t=24113)

Is your Windows going to be XP, 2000, or NT? If so, it's probably NTFS. Were you planning to share files between OSes, [because NTFS could pose some difficulties for you.](http://www.psychocats.net/essays/linuxguide.php#partitioning)

---

### Post by eyebrowman92 on 2005-11-09
i know how to do everything except shrink the pertition. the ubuntu live cd doesnt have gparted or qtparted on it i dont think. do you know if the 5.10 cd has it? i havent got my cds yet. i heard somewhere you can resize the partition from the install cd also.

---

### Post by SickTwist on 2005-11-09
If you have only one hard disk:

1. Back up any important data.
2. Download and burn a live CD that has a partition utility that you would like to use. If you want a GUI utility, [SystemRescue]("http://www.sysresccd.org/") includes QtParted
3. Boot the computer from the live CD.
4. Make sure no HDD partitions are mounted. (mount command with no options will list all mounts).
5. Run the partition utility to move and resize the partitions. (I think XP can be installed in a logical partition but I'm not 100% sure. Hopefully someone else can confirm or deny this.)
6. If you make drastic changes to the partition table you may need to edit /etc/fstab and /boot/grub/menu.lst so that Ubuntu will boot correctly. You can edit these files by mounting the appropriate partitions and using an editor from the live CD.

EDIT: Ooops, just noticed that aysiu beat me to this. :)

---

### Post by eyebrowman92 on 2005-11-10
alright thanks

---

