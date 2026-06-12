---
title: "Totem can't play DVDs"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lxowle on 2009-10-05
Before I submit a bug report, I want to check I haven't done any thing stupid. (I'm testing 9.10 beta)

I followed the instructions here, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and installed libdvdcss2. (these instructions were well written BTW)

I can see the dvd file system, so it's mounted correctly. I start totem, and get the following error message: > Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc

That's a bug right? It should work or have I done something wrong?

---

### Post by ikt on 2009-10-05
if you try it in another media player does it work?

---

### Post by phenest on 2009-10-05
Have you installed libdvdread4 and libdvdnav4?

---

### Post by terry_gardener on 2009-10-05
i have similar problems check following for details. 

[http://ubuntuforums.org/showthread.php?t=1283142]("http://ubuntuforums.org/showthread.php?t=1283142")

---

### Post by dalonso on 2009-10-05
> **lxowle said:**
> Before I submit a bug report, I want to check I haven't done any thing stupid. (I'm testing 9.10 beta)

I followed the instructions here, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and installed libdvdcss2. (these instructions were well written BTW)

I can see the dvd file system, so it's mounted correctly. I start totem, and get the following error message: 

That's a bug right? It should work or have I done something wrong?

That's strange. For the first time of all Ubuntu versions I have tried, that Karmic didn't need to enable the Medibuntu repository. For me it "almost" worked out of the box. (By the way, I believe that Medibuntu has not yet been updated to the gstreamer version that Karmic is using, so I imagine there's no gain on enabling it).

The only thing I needed to fix DVD playback in Karmic was installing gstreamer-plugins-bad from universe, as it is including libresindvd, the new gstreamer plugin supporting DVD playback.

So I recommend you to revert changes introduced by enabling Medibuntu, and try going this way instead.

I'm talking a bit from memory, but I think it was the only thing I did.

---

### Post by lxowle on 2009-10-06
Hi - thanks everyone for your feedback and help - I really appreciate it and I'm working through your suggestions now.

> **phenest said:**
> Have you installed libdvdread4 and libdvdnav4?

Yeah, these are installed.

---

### Post by Grimhound on 2009-10-06
I have a similar issue. Even after following the comprehensive media guide (after manually installing everything I could find related), still DVD (and CD for that matter) playback was not operating correctly. I believe it's currently an issue with 9.10 beta, but I have no idea on if there's even a fix being worked on. There was also an issue where attempting to play media files would cause Ubuntu to crash back to login, but I haven't tested if this was resolved yet.

---

### Post by lxowle on 2009-10-06
> **ikt said:**
> if you try it in another media player does it work?

Thanks, I didn't think to try this. I tried it in mplayer, and the DVD starts to play (although with bad interlacing issues, and then it stops, sometimes crashing.) If I press FF, it crashes with the following error: "Mplayer crashed with bad usage of CPU/FPU/RAM" and then a further message saying the problem either caused by: MPlayer code, my drivers or my gcc version.

---

### Post by Hated On Mostly on 2009-10-06
There is an update showing in Update Manger/Synaptic that supposedly fixes this bug.

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/438065/comments/34](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/438065/comments/34)

---

### Post by Grimhound on 2009-10-06
Currently as well Rhythmbox can't process cdda (audio CDs).

---

### Post by lxowle on 2009-10-06
> **terry_gardener said:**
> i have similar problems check following for details. 

[http://ubuntuforums.org/showthread.php?t=1283142]("http://ubuntuforums.org/showthread.php?t=1283142")

Thanks for this - I followed the instructions to remove brasero, and it fixed the stability problem in mplayer - it now doesn't crash (and the cd/dvd player behaves much better - the eject button doesn't work though).

I still get exactly the same error message for totem though.

---

### Post by lxowle on 2009-10-06
> **Grimhound said:**
> Currently as well Rhythmbox can't process cdda (audio CDs).

Thanks for your comments, I think given all the problems people are having, I might just sit tight for a week and see it the problem remains. I'm having the exact problems you are (same error for rhythmbox too)

---

### Post by cor2y on 2009-10-19
Is this issue fixed i just tried to play a dvd within totem and i got that exact same error.
As far as i can tell from the brasero bug i have the latest one with the fix.
If it is brasero then i guess its back to k3b for me.
Of course it seems i will lose rhythmbox when i remove libbrasero

---

