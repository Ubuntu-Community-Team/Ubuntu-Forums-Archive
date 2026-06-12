---
title: "resizing windows and ubuntu partitions"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by keegs454 on 2007-08-17
Okay, here's my problem. I just installed Ubuntu on a dual-boot system (I was already running Windows XP), and when I was installing, I resized the Windows partition to make room for Ubuntu. The problem is, I misread it and thought I was selecting the size of the new partition (for Ubuntu), not the new size of the old one (with Windows), and I ended up making the Windows partition much smaller than I wanted to. It's not so small that anything was deleted (that I know of), but I really need it bigger than it is.
So, is there a way to shrink the Ubuntu partition somewhat, and increase the size of my Windows partition?
I've looked around the forums, and I saw mention of a GParted live CD, but in every case it was for making the Ubuntu partition bigger. Will that CD also work to take space from my Ubuntu partition and add it back to Windows?
Thanks.

---

### Post by merlinus on 2007-08-17
You can use gparted live cd to shrink the size of your ubuntu partition, and then add that space to windows.

Just be sure to shrink ubuntu from left to right so that space is freed up at the beginning of the partition, not at the end.

-merlin

---

### Post by Gnub_Daemon on 2007-08-17
Another way would be to just get the ext2ifs drivers and you can read/write directly to the linux partition.

---

### Post by keegs454 on 2007-08-17
> **merlinus said:**
> You can use gparted live cd to shrink the size of your ubuntu partition, and then add that space to windows.

Just be sure to shrink ubuntu from left to right so that space is freed up at the beginning of the partition, not at the end.

-merlin

What do you mean "from left to right"? I take it this will make sense once I start using gparted?
Thanks both for your help.

*Update* Turns out I DID delete things from Windows: system32\hal.dll for example. Apparently, Windows can't start without it. I'm going to see if I can fix that somehow, but it looks like I might have to reinstall windows. Ugh.

---

### Post by mikewhatever on 2007-08-17
Before you go reinstalling, check out this link [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#hal.dll_is_missing_or_corrupt)
It may also help to run a search for hal.dll to make sure it is there, because it seems highly improbable that specific file out of thousands would be deleted.

---

