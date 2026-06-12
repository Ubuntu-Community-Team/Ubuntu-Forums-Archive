---
title: "problems with eject button on dvd drive"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2009-10-09
is anyone still having problems with the eject button on dvd drive.

bug #397734 says that fix released but still having problems i have updated the bug but just wondered if anyone else is still having problems. 

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397734]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/397734")

---

### Post by emarkay on 2009-10-09
Yes, I am.  I presumed the "fix" wasn't available yet.

I wonder how long it takes from "Released" to Repository?

---

### Post by terry_gardener on 2009-10-10
it has already been released it was package devicekits-disks version 007-1ubuntu1, and i have 007-2 installed. 

did some tests to find out what worked or not here my results copied from the bug comment #24

in the test i used an audio-cd, dvd-video, dvd-data disc (win 7 disc), and cd data disc (ubuntu 9.10 & ubuntu 9.04 discs)

this is the behaviour of these discs.
-the audio cd will mount and play in app and then unmount and eject with the eject drive button.
-dvd-video once mounted does not respond at all to the eject button press and needs to unmount/eject from nautilus.
-dvd-data disc will mount and allow you to navigate the data on the disc, when you press the eject button it does eject but leaves itself mounted, so when you but in another disc it doesn't mount, until you have unmounted this disc in nautilus.
-cd data discs works the same as dvd data discs.

---

### Post by mc4man on 2009-10-10
Noticed the same thing with some variations that only point out that this patch may be hardware and hardware configuration dependant.

Actually on one machine, one drive works as expected, the other doesn't. On another, neither of the drives works as expected with slight variations between them.
( haven't tested an external, will later

We'll see if there is any response back to your post on LP

---

### Post by terry_gardener on 2009-10-11
have been asked on the above bug to raise new bug. 

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/448921]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/448921")

---

