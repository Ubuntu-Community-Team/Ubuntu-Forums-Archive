---
title: "Vista Dual Boot Problem"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by crispylego on 2010-12-29
I've dual booted Ubuntu on two or three other computers before, but this time I can start Ubuntu just fine but not Windows Vista. I'm not sure if the partitions for Windows were resized incorrectly or what but I'm not sure how or if it can be fixed. I found other similar forums but none that were of any help to me. I'm pretty much a n00b with Ubuntu though so any detailed instructions and help would be appreciated. Just ask for any additional info!

---

### Post by crispylego on 2010-12-29
Oh and I'm using an HP Pavillion dv6000.

---

### Post by David D. on 2010-12-29
I also dual boot Vista and Ubuntu.  After resizing the Windows Vista partition I found that Vista would boot, but there were problems with the OS such as not being able to download and install updates to Vista.

I ended up contacting Microsoft and obtaining an install disk (Vista came pre-installed on my laptop) and reinstalling Vista to make Vista work.  Of course this wiped out Grub 2 and my ability to boot Ubuntu (10.04 at the time).  Since I did not have the foresight to back up Grub, I ended up having to reinstall Ubuntu, which was no big deal since files I want to keep are in a separate data partition.

Changing the partition size for Vista may have created the problem on that computer (as it did for me on my computer).  If you have no files you want to save, I suggest a re-install of Vista into the resized partition followed by a new install of Ubuntu into the partition(s) you have set up for it.

---

### Post by crispylego on 2010-12-29
Alright thanks I don't really have any files I want to save as the computer's brand new so maybe I'll try getting a Vista install disc.

---

