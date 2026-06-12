---
title: "Unable to mount root fs... driving me NUTS!"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by StormCrow667 on 2011-05-11
Hi folks

Was using 10.04 and decided to upgrade to 10.10 with a view to upgrading to 11.04. No dice. 

That was a few days ago so forget about that bit, no traces of 10.04 left now...

Downloaded the LiveCD version of 11.04 (twice, in case it was a faulty image) and install.

Every time I boot I get the "unable to mount root fs on unknown block (0,0)" error - no matter what I do.

I've tried reinstalling the system totally from the CD a number of times...
Tried purging and reinstalling Grub2...
Tried messing about with the grub bootloader settings...
And much more besides!

The system will boot perfectly off the LiveCD, which indicates to me that the 'system' is compatible with the computer?

I've done most of the things that a simple Google search on these forums suggests, with reinstalls in between but still can't get the PC to boot.

Please please someone give me a clue! Usually a clean install will fix pretty much everything, not in this case!!


BTW - I have got and run the boot info script, although I'm in the middle of a complete reinstall AGAIN so will post the new version when it's done - for now though any ideas?

---

### Post by StormCrow667 on 2011-05-11
Just got home from work to find the installer waiting for me to click 'finish'.

Done that, rebooted and still won't boot - this must the 10th time I've tried reinstalling in the last few days or so. Also tried Ubuntu 10.04 and 10.10 so something must be up with the partition tables?

Went through GParted this time and removed the boot flags from all but the boot drive (/dev/sdb in this case, two partitions (154Gb main EXT3 partition as / and 6Gb swap partition). There are several drives on the system, one of which is partitioned twice (both NTFS) with Windows 2000 and Windows XP but I've no idea if they boot as I haven't used them in a few months since Ubuntu! Grub still picks them up though...

Done a 'boot info script' but can't work out how to open / paste it? gedit says that the character encoding isn't recognised (although I can open it in vi using the Terminal) - not been my day with Ubuntu today?!

---

### Post by StormCrow667 on 2011-05-11
Right - I'm off to bed - although I know I'm going to have partition tables running through my head!

Have set the BIOS SATA drives (of which this particular drive is one) to non RAID (I forget the actual designation but it's acting like a 'normal' hard drive now rather than detecting it later) and am trying ANOTHER reinstall in the vain hope that it might get it running - I doubt it will though. 

Have also disabled 'download updates on install' as well as the network connection in case it's an update that's causing the problem - again I'd be surprised but am willing to try just about anything at this point.. have spent three days trying to get it to work and it's costing me a lot of non grey hairs!

Might have to junk Ubuntu and move on to another distribution - shame :(

---

### Post by StormCrow667 on 2011-05-11
OK - think its better now...

As simple as adding acpi=off into the flippin' boot config... managed to get it to boot in once at least...

Will see how it progresses - I'm not going to want to turn the computer off!!

---

