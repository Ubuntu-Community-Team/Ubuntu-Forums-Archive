---
title: "ATI Driver didn't upgrade (Dapper-&gt;Edgy)"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by SigmaX on 2006-10-28
Just thought I'd put this out there in case somebody else has the same problem.

I upgraded my Dapper box to Edgy today, and for some reason my ATI driver didn't get upgraded along with.  The Dapper version of the driver was for Xorg 7.0, and doesn't work wiht Edgy's Xorg 7.1, leastwise not with my card (Radeon 7500), so X was fried.

I didn't keep the logfile, but the error I was getting was something along the lines of:
```
(EE) module ABI major version (0) doesn't match server's version (1)
```

The package for the driver is called "xserver-xorg-driver-ati" in Dapper, but "xserver-xorg-video-ati" in Edgy.  Maybe that has something to do with it.

Anyway, the simplistic solution:
```
$ sudo apt-get remove xserver-xorg-driver-ati
$ sudo apt-get install xserver-xorg-video-ati
```

SigmaX

---

### Post by rfruth on 2006-10-28
I had to apt-get install xserver-xorg-video-ati for my ATI X300 video card also but didn't realize it at first ...

---

### Post by greew on 2006-10-29
This did the trick for me too.

Thanks a lot!

---

### Post by yalding on 2006-10-29
My bad luck, my ati X300 does not work anymore with edgy. After struggling for one day, I format my disk and have a fresh install of dapper.

byebye edgy. It ruined my weekend and holiday. The poll in this forum indicates that 30% upgrades end up with mess. How comes ubuntu releases edgy breaking up some many machines in the world, including my poor working machine, :(

Let me just stick with dapper for another year.

---

