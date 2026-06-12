---
title: "Buffer i/o error on device loop0 logical block xxxxxx"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2009-10-25
Have been receiving this error on reboot with Vista/WUBI 9.10 Karmic since Alpha stages.
Sometimes if fsck before rebooting it will reboot without interruption, sometimes. 
Uninstalled [lupin-support] and seems to be rebooting fine without fsck before every reboot. Do not know consequences of removal of [lupin-support].
Anyone that knows anything about this I would appreciate your input.

Can have 10 or more Buffer I/O error on device loop0 logical block  xxxxxxx
at any given reboot  and need to alt/sys rq/b  to reboot.

[lupin-support] being WUBI support function is it detrimental in long run???
2.28.1 (Ubuntu 2009-10-23)
2.6.31-14-generic
4.4.1 (x86_64-linux-gnu)
Ubuntu 9.10 (karmic rc)
Intel 82945G
Intel 82801G PCI Bridge
Drivers all generic

---

### Post by ppb1701 on 2009-10-25
I'm having the same thing happen with 2 notebooks. vistas/9.10 beta and xp/9.10 beta (both installed from 9.04 wubi installer).  Boots fines, but hangs on shutdown/reboot with errors.  I'm also just using generic drivers.  Doesn't do it on my box with just it installed.  I forced fsck to run last night and it found nothing, I've forced scandisk to run on the the other side and found nothing.   Freaked me out first time I saw it cause I'd just reloaded one from a corrupt file system.

---

### Post by garvinrick4 on 2009-10-25
Not a lot of action here just the two of us. If I find anything out I will let you know.

I have reinstalled [lupin-support] and will fsck and sudo reboot from Terminal until
fixed.  Found same problem back in 2008 in launchpad but nothing more recent. I am
sure there are a lot of us out there. 

I myself have a 80 year old father who lives with me who needs his Windows. I just got
him started a few years ago and Linux gives him the Willy's. He deserves what he wants to
use so I dual boot. WUBI does have a value. Got me started, my next purchase will be laptop with only Linux.  For now will try to get this Vista/Ubuntu WUBI dual boot in order.

---

### Post by battmanux on 2009-10-26
Same for me
I upgraded to ubuntu 9.10 from a WUBI install and the computer does that on shutdown...

I am having  look at it.

---

### Post by poo706 on 2009-10-26
I'm having what appears to be the same issue too.  Ubuntu 9.04 installed via Wubi on XP never hand any issues rebooting.  Then I did an update to 9.10 beta via "update-manager -d" and now I often (but now always) get buffer i/o errors on device loop0 when rebooting.  I got them to mostly go away by stopping BOINC from starting up, but they still happen, seeming randomly.  I found this lengthy bug report from last year: [https://bugs.launchpad.net/wubi/8.04/+bug/204133](https://bugs.launchpad.net/wubi/8.04/+bug/204133) .  However, I'm having trouble making a whole lot of sense of it.  I'm not new to linux, but I'm no guru either.

[poo]

---

### Post by kikejulia on 2009-10-26
Same problem here... seems to be random.

I've just upgraded to Ubunto 9.10 after using a 9.04 installation from Wubi. Never had this problem with Jaunty, only appeared after upgrading to Karmic.

---

### Post by ppb1701 on 2009-10-26
mine happens every reboot/shutdown. only semi random is how many it claims to find.

---

### Post by garvinrick4 on 2009-10-26
Upgrade Oct. 26th 2009  Karmic 9.10 rc of [lupin-support] seems to have fixed issue.

Check Synaptic to make sure you have .27 the new upgrade from .25

So far so good.

---

### Post by poo706 on 2009-10-27
I upgraded lupin-support to .27, but I'm still getting the loop0 buffer errors.  When I'm getting the errors, if I hit ctrl-alt-del, it'll abandon the journaling and the loop0 errors will keep coming.  But, if I hit C-A-D after that, it says something about hwclock-save being aborted.  Every C-A-D after that gives me the same message about hwclock-save.  Is that what everyone else is seeing?  Did simply upgrading lupin-support fix everyone else's problem?  Ugh, my next Ubuntu install will not be through Wubi!

[poo]

---

### Post by kikejulia on 2009-10-27
Updating lupin-support to .27 did not solve the problem here... I'm geting the same behaviour as poo706

---

### Post by poo706 on 2009-10-27
I'm glad I'm not the only one.  I was starting to think I had a unique problem.  Even though it's the beta, I find it odd that I'm not seeing anything else about this issue around the net.  This seems to be a problem with an earlier version of Ubuntu installed via Wubi, then upgraded to 9.10.  I would think there would be a lot more of us.

[poo]

---

### Post by headmower on 2009-10-27
I upgraded 9.04 to 9.10 beta rc and keep getting error messages upon reboot or shutdown. Only works by using power button. Boots up fine. Updated lupin as adviced in this forum but still have same problem. This never happened with 9.04 Will release on 10/29/09 be the same???

---

### Post by poo706 on 2009-10-28
Headmower, did you install 9.04 with Wubi as well?  If I remember right, I installed 8.10 with Wubi, then upgraded to 9.04 beta, then upgraded to 9.04, then upgraded to 9.10 beta, which is where my problems started.

[poo]

---

### Post by usagetta on 2009-10-28
I see that the thread is signed as "solved" but I don't see any solutino in the replies, please can anybody tell me the solution?:(

---

### Post by kikejulia on 2009-10-28
The issue is not solved so far, so the topic should be edited...

---

### Post by poo706 on 2009-10-28
I've started looking at hwclock-save that's being executed during shutdown/ reboot.  When things hang and I eventually hit ctrl-alt-delete, hwclock-save is what's being aborted, over and over again every time I hit C-A-D.  I'm still not fully understanding exactly what hwclock even does or if I really need it or not.  Just for grins, I thought I'd try to disable hwclock-save that's executed during shutdown (but not hwclock that's executed during startup).  After figuring out that the new-to-Karmic Upstart was handling the execution of hwclock and hwclock-save, I moved hwclock-save.conf from /etc/init to a temp folder.  The first reboot test was successful!  I'm not going to call it a complete success at this point because I've been tricked several times already with this issue.  I finally noticed that I have successful reboots when Ubuntu has only been up and running for a few minutes.  But after a little bit of use for 15-30 minutes, I'd get the shutdown hang every time (I'm pretty sure).  The successful reboot after taking out hwclock-save was after about 30 minutes of use.  I'll try throughout the night and report back later.

[poo]

---

### Post by poo706 on 2009-10-28
Never mind, jumped the gun on that one.  The two following reboots hung.  However, the hwclock-save messages didn't come up after hitting C-A-D this time.  In fact, hitting C-A-D brought up nothing at all this time.  Does anyone know specifically which shutdown job is the one hanging?

[poo]

---

### Post by Papajerry on 2009-10-29
THE FINAL RELEASE IS NOW OUT!!!!  How do I reinstall the final over the beta?

---

