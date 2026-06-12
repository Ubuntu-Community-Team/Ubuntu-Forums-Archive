---
title: "linux-image update broke my system"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by GMWeezel on 2007-09-01
Last night I downloaded the linux-image-2.6.20-16-generic 16.31 update moving me from 16.29. When I woke up and rebooted my system, everything was very choppy and beryl no longer functioned properly. I looked at my system resource usage to see that only 1 "core" of my hyper threaded system was recognized. My boot settings were still the same so I have no clue what to do. Below is my commit log:

> Commit Log for Sat Sep  1 01:46:01 2007


Upgraded the following packages:
linux-image-2.6.20-16-generic (2.6.20-16.29) to 2.6.20-16.31
linux-libc-dev (2.6.20-16.29) to 2.6.20-16.31
linux-source-2.6.20 (2.6.20-16.29) to 2.6.20-16.31

---

### Post by Gremlinzzz on 2007-09-01
Dont know what happen to your system but if all else fails you can go higher
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by GMWeezel on 2007-09-01
That was much worse but thanks though. Wouldn't boot saying "Device lookup failure" over and over. Anyone know how I can downgrade back to 16.29? I know apt keeps packages saved on the system somewhere but I don't know what folder. Maybe I could install it from the cached deb package?

---

### Post by Seisen on 2007-09-01
Do you still have the old kernel 2.6.15 installed and on your grub menu?

---

### Post by quixote on 2007-09-01
I had the same issue.

In my case, it was fixed by editing /boot/grub/menu.lst (process described in[ this thread]("http://ubuntuforums.org/showthread.php?t=540408")).

The reason it's not finding the device is because for some reason the update numbers the partitions incorrectly for grub.  So grub is looking for boot information in a place that doesn't have it.  :(

---

### Post by GMWeezel on 2007-09-02
Quixote, I don't have the same problem as you. I get device not found _after_ my system begins to boot into ubuntu and also I checked my grub menu just to be certain and HD numbers are the same on the one I can boot into but is choppy.

> **Seisen said:**
> Do you still have the old kernel 2.6.15 installed and on your grub menu?

Sadly, no. If I did, I would use it. Couldn't find the deb online and I don't know where synaptic caches packages so I could see if one of the older kernel images is still in there.

UPDATE: Silly me; hadn't realized the *.15 image was still available from the download channel but sadly the *.16-29 image isn't.

UPDATE #2: Ok got the new kernel image working without the chopiness; I stand corrected on what I said about my boot options being the same; whenever my menu gets updated, it uses the options I had to use to install 6.06 (Because of my computer, the only way I can get Feisty Fawn is by installing 6.06 and upgrading twice; for some reason Edgy Eft and Feisty Fawn refuse to install; I'm sure it's the ATi chipset) and so I had a few extra options on there. Sadly, *.22 kernel still won't work but I'll save working on that for later.

---

