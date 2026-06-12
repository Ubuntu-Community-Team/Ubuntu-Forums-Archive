---
title: "Problem with mouse pointer using LiveCD"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by joelsy on 2008-07-12
Long time windows user trying to give Ubuntu a shot.  I have Vista installed on my Dell XPSM1530.  Burned CD of Ubuntu 8.04 LTS Desktop Edition.  Trying to use the LiveCD option before I install to hard drive.

After a ton of CD drive activity, I get to the main screen.  I try using the laptop mouse pad and the pointer just goes crazy - jumps all over the place.  Unable to select anaything.

Can be seen in action here:
[http://www.youtube.com/watch?v=kEWxJYX907U]("http://www.youtube.com/watch?v=kEWxJYX907U")

If anybody has any suggestions, that would be appreciated.

---

### Post by Pumalite on 2008-07-12
Burn a new CD. Do md5sum, burn at 4x or less. Do not use CD-RW.

---

### Post by joelsy on 2008-07-12
Thanks for the quick suggestion.

I verified I had a good download with the winMd5Sum.  I burned another CD with the slowest speed my Roxio app has which is 10.x - same result with the LiveCD/mouse pointer.

I installed the free InfraRecorder for a slower burn speed option.  InfraRecorder couldn't detect my CD/DVD drive.

The free ISO Recorder v3 (Vista edition) notes the following as known issues for its v3 release:

*4) Burn properties (max speed, etc) do not work - disabled in this build.*

So I didn't bother trying that app for a program that will burn an iso at a 4.x speed.

:lolflag:

---

### Post by Pumalite on 2008-07-13
Try ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install. Mode>ISO>Burn. Selext 1x

---

### Post by joelsy on 2008-07-13
Thank you.

I installed ImgBurn. ImgBurn detected my optical drive which is good.  I attempted to burn at a 1x speed, but noticed in the cd drive profile that ImgBurn displays my drive's minimum write speed as 10x.

I did go ahead and burn CD #3 with ImgBurn's write speed at 1x.   ImgBurn's log showed a write speed of 1x whilst burning.

I booted from this latest disc, verified via the Ubuntu menu option the CD had no defects, same result - no control over mouse pointer.

So far I've:

* verified with winMd5Sum my download of ubuntu-8.04.1-
desktop-i386 is good.

* burned 3 cds including one at 1x

* verified via the Ubuntu menu option all 3 CDs had no defects

still no success using ubuntu LiveCD.

---

### Post by Pumalite on 2008-07-13
Is your mouse USB?

---

### Post by joelsy on 2008-07-13
I'm using the laptop's touch pad.

Dell Touchpad
Version: 7.1.102.7

Per Windows Device Manager, plugged into PS/2 mouse port

:confused:

---

### Post by Pumalite on 2008-07-13
This might help:
[http://ubuntuforums.org/showthread.php?p=5119058](http://ubuntuforums.org/showthread.php?p=5119058)

---

### Post by joelsy on 2008-07-13
No help in that thread.  I actually found that post on an initial search of the forum for my issue.  That post was from a new user that installed to their hard drive and were having similar issues.  I don't think the same troubleshooting would apply using the LiveCD, but I could be mistaken.

I appreciate your time though.

---

### Post by Sakian on 2009-03-23
I know this is kinda resurrecting an old thread, but I just wanted to say that I'm having the same problems with the Live CD.  I also happen to have the Dell XPS m1530 and it's probably not a coincidence.  If it helps at all, it went away for me once I installed Ubuntu (as opposed to using the live CD).

---

