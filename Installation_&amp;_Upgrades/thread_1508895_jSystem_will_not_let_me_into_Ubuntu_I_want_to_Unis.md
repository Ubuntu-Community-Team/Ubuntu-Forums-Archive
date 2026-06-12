---
title: "jSystem will not let me into Ubuntu I want to Unistall it Completely"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by tgaston34 on 2010-06-13
Ok I have decided to completely remove Ubuntu 10.04 from my system how do I unistall it I was primarly using for myself and had not tried to load my vista program but it won't load either so I just want to completely remove everything and start over from scratch. Pls help I am so new to ubuntu that I don't have a clue on how to do this. Thanks

---

### Post by quixote on 2010-06-14
when you start booting, do you have a choice of operating systems, but then when you choose one, it won't boot?  Or do you never get a choice?  Just no option to boot into anything?

If the latter, some problem overwrote your Master Boot Record (MBR) which is very easy to recover from.  If your first concern is to get Vista working, then boot from their recovery disk, and choose the option to fix the MBR.  In the good old DOS days, that was "fixmbr" typed at the command prompt.  I did a search for "fix mbr vista" (without quotes), and found this link [http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/](http://www.lancelhoff.com/how-to-fix-vista-mbr-repair-broken-vista/) which has instructions with screenshots.  It's still fixmbr, just after several layers of easy graphical menus... :rolleyes:  If you don't have an install dvd, just recovery disk, your instructions will look different, but somewhere in there you should have the option to use fixmbr.

If your ubuntu was unstalled as wubi, ie under vista, without making any separate partitions, then you'd just get rid of it from within vista, I think.  (I don't have any experience with wubi.)  

If it's on a separate partition, you could boot from an ubuntu livecd, start System > Admin > parted (or gparted, don't remember what they're calling it now), *be sure you select the right partition* (it'll have the size of your ubuntu partition and be formatted "ext3" or "ext4").  And delete the partition.  It's then "free" or "unallocated".  If you want to give it back to vista, I think, but I could be wrong, that that's best done from inside vista.

If you want to format it as a data partition readable by vista or linux, you could format it as "ntfs".  If you also wanted it to be readable by winxp, use "vfat".

If you want to try ubuntu again with a clean install, then there's no need to do anything now.  When you reinstall, just be sure to select the old ubuntu partition (and make sure no other partitions are selected for formatting!) and the reinstall will wipe out anything that was on there.

---

### Post by tgaston34 on 2010-06-23
I deleated the partition with 10.04 but now when I select the recovery mode for Vista it doesn't do anything what do I do, please help I have no idea of how to fix this and it has all my kids photos and music on it. Thanks

---

### Post by bcbc on 2010-06-24
Post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

The instructions are in the link. I mention this as you said that vista wasn't booting before.

If you've deleted the ubuntu partition without putting back the windows bootloader, this makes nothing bootable - but it doesn't affect the data on your windows partition. You should be able to see this by booting from an ubuntu live CD (you might consider plugging in an external and taking a backup before you start repairing it too).

---

