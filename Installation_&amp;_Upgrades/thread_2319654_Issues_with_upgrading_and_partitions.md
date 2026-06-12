---
title: "Issues with upgrading and partitions"
date: 2016-04-06
forum: Installation &amp; Upgrades
---

### Post by sophy_m on 2016-04-06
Hello,

I have a number of issues that may or may not be related.

I'm running a dual boot with Windows and 14.04, and recently upgraded from Win7 to Win10 (with a fresh install, after much trial and tribulation). 

Now I want to upgrade 14.04 to 15.10 but running into problems. Initially I went for a fresh install from a live USB but it just stuck after selecting the download as you ugrade/install repositories options and pressing continue. Then I tried to upgrade from my current OS using system updater, which terminated because of an error (I'll go back and screenshot the details in a minute). 

My system partition has been getting quite full lately so I thought that might be having an impact. So my next idea was to open GParted and move things around a bit.  

Alas, GParted is now showing my entire disk as unallocated. Al my partitions open fine both in Windows and Ubuntu, so it doesn't seem like there's a problem with the partitions themselves - but maybe my partition tables have been messed up? I'm not sure if this is related to the Windows upgrade though as it's been some time since I looked at GParted.

Anyone have any ideas? Thanks...

---

### Post by slickymaster on 2016-04-06
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by sophy_m on 2016-04-07
Ok so I finally managed to upgrade from my 14.04 desktop with Software Updater after I cleared a bit of space. But now my system is very slow and several things seem broken. I couldn't use GParted at all so I uninstalled and tried reinstalling - it won't do it. Synaptic tells me there are dependencies (which also won't install when I try to via terminal) and won't install it.

Here's a screenshot of the GParted issue I was having originally, and the results of fdisk:

[ATTACH=CONFIG]268221[/ATTACH]

I tried fixing the partition tables using a method that I found online, using the live USB to install GPart and guessing the partitions - but this hangs halfway through the partition scan process. Now I'm wondering if I shouldn't just wipe all my partitions from Windows and start again. Everything is backed up anyway.

---

