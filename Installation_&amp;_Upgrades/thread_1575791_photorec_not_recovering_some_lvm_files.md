---
title: "photorec not recovering some lvm files?"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by whoops2010 on 2010-09-16
In a fit of stupidity (and being new to Linux) I accidentally re-formatted an LVM2 partition (/dev/sda5) of an Ubuntu 10.04 installation as ntfs.

Luckily it was a fairly new machine but there were a few files I didn't have backups for and I tried running photorec on the drive to see if I could recover them.

My question is, some of the files were little Unix shell scripts I'd written, with the ".sh" extension, but looking at the files photorec recovered (doing greps in them on things I know should match since the file names are different), I'm not finding them.

I did another grep through all the recovered files (not just the .sh ones) and it seemed like maybe at least parts of those wound up in the middle of what photorec recovered as .gz files(?)  Does that sound possible?  That it incorrectly recovered these files with the wrong type/content/size/everything?

If that were to happen would you think it means I'd chosen some bad options when I ran photorec?  

Running photorec, I took the default choice of "Intel" since I didn't see LVM2 listed - but since I'd reformatted the LVM2 partition to ntfs am I confusing it?  Could it be thinking the partition is ntfs when I really need it to be finding the original LVM2 files?

So new to this not sure if what I've gotten is the best I can do or if I'm doing something wrong.

---

