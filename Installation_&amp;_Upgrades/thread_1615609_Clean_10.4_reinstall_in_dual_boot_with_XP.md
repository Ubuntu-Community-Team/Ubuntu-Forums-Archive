---
title: "Clean 10.4 reinstall in dual boot with XP"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by birdfeedr on 2010-11-07
I had a 100% XP machine, installed 9.10 into a dual boot a while ago, and eventually upgraded to 10.4 LTS.

Current partitions

/dev/sda1 ntfs
/dev/sda2 extended
---- /dev/sda5 ext4
---- /dev/sda6 linux-swap

Currently, dual boot is working and both OSes are working as expected (although there's that bit of inconsistency with intel 845 graphics).

I want to do two things in a major re-install: move Home to a new, separate partition, and do a clean 10.4 install while still retaining XP dual boot. If possible leave sda1 untouched, but that can be reinstalled if necessary.

Only things in Home that need to be moved are documents and mozilla seamonkey prefs and emails. Those items I can save and restore manually, so I have no problems with backup needed files, then clean install, then manually restore.

I know enough to be willing to try suggestions, but also know enough to recognize I can get into trouble. So that's why I'm asking here first. Thanks for any suggestions. How would *you* approach this?

---

### Post by thejeswi.nk on 2010-11-07
Hello birdfeedr,
I think you are doing it the easiest way.
Go ahead and manually back up your files in a partition other than sda5 or any other external storage.
Then put in the Ubuntu 10.04 CD or how ever you want to install it; then during the installation when you come to the window which says prepare partitions, choose Specify Partitions manually and choose to format and install on the sda5 partition (the one with the ext4 filesystem).

That should do the job :)

---

