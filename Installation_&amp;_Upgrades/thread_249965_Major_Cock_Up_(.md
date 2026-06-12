---
title: "Major Cock Up :("
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by ChrisSmith on 2006-09-03
Bassically I tried to install ubuntu on a 10gb partition whulst trying to preserve a windows installation on another partition. But then it gave me a warning saying that I should also create a swap. I tried to do this by resizing the 10gb partition leaving 512mb after it. I then tried to create a partition on the 512mb of free space (which seemed to work fine)., But then when I went to install it the new partition was not there. Went back and it loooked like this :(

[[IMG]http://img105.imageshack.us/img105/636/screenshotiu9.th.png[/IMG]](http://img105.imageshack.us/img105/636/screenshotiu9.png)

I tried many a times to make this 512mb chunk into a partition but each time it seemed fine but then was not there when I went to install.

Then to top it off I switch computer the computer off planing to go back into windows and I get this message.

> windows root/system 32/hal.dll missing
.. blah blah cant boot

so it looks like the 10gb partition was being used to boot the windows installation on the other partition.

Is there any way to get the windows on the 70gb partition to boot?
And why does the partition im trying to create for the swap keep screwing up??

Please please help or im gonna be stuck on the live CD for ever :(

Chris

---

### Post by goatflyer on 2006-09-03
Could be your BIOS has protection for the MBR, where all partition info for the 1st 4 partitions are stored... go through your BIOS menus and turn it off.

---

### Post by ChrisSmith on 2006-09-03
do you have any idea on how to get windows working again aswell?

---

### Post by goatflyer on 2006-09-03
If you've already overwritten the contents of your first partition, the old data is gone --- you'll have to reinstall windows.  The good news is your data on the big partition is probably okay.

Before reinstalling anything, use the LiveCD to mount /dev/hda1 and take a peek at what's there.  If you see windows directories perhaps all is not lost.  Boot using windows recovery console and try fixboot or fixmbr.

---

### Post by ChrisSmith on 2006-09-03
looks like theres still stuff on the partition just gotta get that hal.dll file sorted, better start looking for XP disc :-?

---

