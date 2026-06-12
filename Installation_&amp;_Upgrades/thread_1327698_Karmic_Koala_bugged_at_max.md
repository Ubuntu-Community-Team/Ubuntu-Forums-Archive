---
title: "Karmic Koala bugged at max"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by realn on 2009-11-15
Hello

 Just installed Kubuntu KK on my new laptop. Weird problems started to appear:

BUG1) After installing firefox and the flash plugin non free (Adobe) I started to get a message about "inconsistency in ld.so" every time I  launched firefox and thunderbird

After uninstalling the flash-nonfree package the problem went away. I reinstalled the package - the problem is gone.

BUG2) After hibernating, most (or rather ALL) applications fail to launch with a segmentation fault message: firefox. thunderbird, kdevelop, even a hibernate command (sudo /etc/acpi/hibernate/sh).
This behavior started to occur after a couple of days of usage of the system (and after installation of additional packages), it didn't occur from the beginning.

Please, can someone help with some suggestions, as I cannot keep KK with all the instabilities.
 
PS1) There might be some chances come from some hardware faults?
PS2) I suspect these problems (at least the second one) come from the fact I have a SSD drive with the system on a ext4 partitions. Quite new things, not tested on a large mass scale, I suppose.

 Thank you all!

---

### Post by realn on 2009-11-18
The list is growing

BUG3) sudo rmmod snd_hda_intel
Computer freezes, hard reset is needed

---

### Post by realn on 2009-11-23
I got rid of the ext4 partitions and went back to ext3. Until now ALL the problems previously reported didn't appear. I will use my system for a month or so, then I will mark the thread as "solved".
 Anyhow, the conclusion is: beware of the EXT4.

---

### Post by realn on 2009-12-13
Well, the problems reappeared. I will dump KK asap and go back to HH. Or maybe I'll dump the whole of ubuntu.
 Very dissapointed:icon_frown:

---

### Post by realn on 2010-07-20
Solved - fallback to Kubuntu Hardy Heron waiting for a real LTS release.

---

