---
title: "Issue using gparted to partition correctly"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by NBrepresent on 2007-04-09
Hi. I'm loving Ubuntu, everything's starting to get set up nicely. 

My problem is that I've resized my XP partition (hda2) and left allocated space, which I would like to use with my ext3 partition (hda5) which is in an extended partition (hda4). You can disregard the fat16 and fat32 partitions, it's a Dell machine and so there are hidden system restore partitions (which is why I had to use the extended partition for my ext3 and swap).

So, how do I get that unallocated space somehow at the end of my root (hd5)?

Here's a screen:

[IMG]http://i19.tinypic.com/2dgnvd1.png[/IMG]

---

### Post by laidback on 2007-04-09
I think you'll need to:-
Move hda5 left into grey area. Delete swap, extend hda5 into unallocated area which will now be on the right, then add a new swap onto the end. You'll have to do all this with the hdd/partitions unmounted as you cannot resize a partition whilst mounted.
Use the Ubuntu Live CD if you don't have a version of the Gparted Live CD, which is available off the net.

---

