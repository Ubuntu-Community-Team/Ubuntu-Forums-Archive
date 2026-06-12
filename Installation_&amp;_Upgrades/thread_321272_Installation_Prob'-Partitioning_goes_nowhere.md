---
title: "Installation Prob'-Partitioning goes nowhere"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by Trajan47 on 2006-12-18
Ok, Im a total Newbie and ive tried installing Edgy Eft 6.10, several times but basically hit the same wall every time.

Generally, what happens is after selecting a partition size and clicking forward, the mouse icon spins but nothing happens. Several times after clicking forward the mouse starts spinning and the buttons 'fade-out' but it soon returns to the same screen with the same settings, when i click forward again, no luck. The system simply spins away, no progress bar, nothing.

Ive played around with the sizes of my new partition and the smallest one 13GB (18% or so) leads to the same place. The mouse spins but nothing happens. It ran for all of last night to no avail.

I tried the terminal commands checking if Windows was mounted or not but it didnt change anything. All a bit puzzling really.

Im running the install off a Ubuntu 6.10 Live Disc, on a Gateway laptop, Windows XP, 80GB HD - NTFS.

Would appreciate any help. Im itching to get playing with Ubuntu.

Thanks

---

### Post by Sandlst on 2006-12-19
I had the exact problem you're having.  Eventually, I decided to just use the handy 'Alternative Install CD' instead.  To find this, goto [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download"), select the mirror of your choice, and click on 'other installation options', then click on the ubuntu-6.10-alternate-(architecture of choice, i386 probably if you don't know).iso.

It will walk you through text-based installation, which isn't a real problem.  The trickiest part is making sure you don't overwrite your windows partition, but as I remember (been a while since I was dual-booting :P) you should be able to select a 'shrink the current partition' type of option.  If that doesnt show up after "Starting the partitioner" appears on your screen, I would recommend trying to find an alternate method of shrinking the NTFS partition (no need to repartition the extra space as anything until the ubuntu installer does) before installing.   Good luck, post back if you have any problems.

---

### Post by jem7v on 2006-12-19
Indeed! I've sometimes had an issue with trying to partition the HD with the LiveCD as well where it just sits and does nothing... Eventually I just used the Alternate Install CD (aka the text installer) and it worked fine.

---

