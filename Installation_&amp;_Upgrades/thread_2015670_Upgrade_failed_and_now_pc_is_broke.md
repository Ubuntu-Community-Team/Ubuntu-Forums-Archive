---
title: "Upgrade failed and now pc is broke"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by DCheck2 on 2012-07-03
I recently tried to upgrade to ubuntu 12.04 from 11.10, the upgrade froze in the middle of the night (fell asleep during download). It stopped halfway through the install, far enough that 11.10 was gone and not far enough that a base of 12.04 was on. I restarted it to a black screen with a "_" blinking. From there I loaded my plop boot manager and booted from usb to try to reinstall 11.10 the first time it failed on the language packs, this happened a couple of times, from there the reinstall failed when "removing conflicting install files." Then i reformatted the partitions and got an error message stating that it was the hdd was either faulty, old, or overheating, i placed a fan on it, and the next time i tried to install it reported that it could not setup the partitions... So what this leaves me at is, do i need a new install copy on my usb? or do i need a new hdd? or is there another workaround.

---

### Post by msammels on 2012-07-04
OK DCheck2,

Here is a simple solution: download Ubuntu 12.04 from the website, and install it on a USB flash drive using something like UNetbootin or Pen Drive Linux. Once you have done this, run it.

Once in your USB copy, run "gparted" and blank the hard drive. Then try to install again. If it fails, it could be a HDD error, depending on the error message you get back from the system.

---

