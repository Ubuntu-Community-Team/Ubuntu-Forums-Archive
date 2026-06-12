---
title: "Some broken stuff in Alpha 2"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-07-13
I'm not actually using my laptop all that much at the moment (as I use one at work that runs XP >_>, which I have to use), so I thought I'd join the testing a bit early.

Turns out the one thing I really was hoping would be fixed was totally crippled - my Intel Wireless (3945) is completely bricked, so that's my first little bug report to submit tomorrow (or today, as it's passed midnight):

NetworkManager reports that the killswitch is off when it's on, therefore attempting (and still failing) to use my wireless. And even when it is off, wireless still fails to function. NetworkManager reports "Network is down".
Luckily my wired is working fine and I have a wireless ethernet adapter, so here I am ;).

Second major problem is FBconfig fails, so Compiz doesn't work - and this is (obviously) a major problem for someone such as myself. This is on an Intel 945, running whatever Intrepid's X server is defaulting to (which should be 'intel' as that's all there is). I'll be recompiling my DRI drivers for my alternate X server tomorrow so I can see if it's still working.

So, I've got to go, but that's my bug report IIa2 at the moment.
Good night ;)

---

### Post by caryb on 2008-07-13
Try this....

[http://ubuntuforums.org/showthread.php?t=844261&highlight=intel+wireless]("http://ubuntuforums.org/showthread.php?t=844261&highlight=intel+wireless")

---

### Post by klange on 2008-07-13
After morally beating myself up, I installed linux-restricted-modules-common and my wireless appears to be working.

However, I have a few more things to report:
1. X seems to have major problems on startup/shutdown giving ugly repeated patterns (I know this is actually a driver issue)
2. Shutdown just stops on what seems to be pretty close to the end, however...
3. Framebuffer has problems. On startup, the progress bar does some weird things. I don't have any virtual terminals, and they're at the wrong resolution anyway (GRUB ignoring my default settings? I'll look into that one)
4. When I switch between a non-existent virtual terminal and my X session I get some nasty crap coming out of my speakers. Same thing happens on login. I'm checking if it's just a sound problem, but as GDM's noises work fine I don't think so. **e**: It would appear my audio is messed up. While I can still hear what I'm supposed to be hearing, it's through a thick layer of static.

And the FBconfig problems will always be critical to me. I'll get some official bug reports sent in through the proper channels some time today.

---

### Post by psyke83 on 2008-07-13
[Edit: accidental double-post]

---

### Post by psyke83 on 2008-07-13
> **WindowsSucks said:**
> After morally beating myself up, I installed linux-restricted-modules-common and my wireless appears to be working.

However, I have a few more things to report:
1. X seems to have major problems on startup/shutdown giving ugly repeated patterns (I know this is actually a driver issue)
2. Shutdown just stops on what seems to be pretty close to the end, however...
3. Framebuffer has problems. On startup, the progress bar does some weird things. I don't have any virtual terminals, and they're at the wrong resolution anyway (GRUB ignoring my default settings? I'll look into that one)
4. When I switch between a non-existent virtual terminal and my X session I get some nasty crap coming out of my speakers. Same thing happens on login. I'm checking if it's just a sound problem, but as GDM's noises work fine I don't think so. **e**: It would appear my audio is messed up. While I can still hear what I'm supposed to be hearing, it's through a thick layer of static.

And the FBconfig problems will always be critical to me. I'll get some official bug reports sent in through the proper channels some time today.

3. Same problem here, may be due to the new sysvinit version, a usplash bug or kernel problem.

4. That problem is already known, and it's because PulseAudio is choosing the wrong PCM device. Please search this subforum for "snd_pcsp".

---

### Post by klange on 2008-07-13
Blacklisting and rmmod'ing snd_pcsp seems to have cleared everything up in the sound department. Thanks for pointing me in the right direction there.

So, that leaves crapped up framebuffer, no VTs, and one hell of a screwed up Mesa. Luckily the last one is a known bug from what I've heard.

---

### Post by psyke83 on 2008-07-13
> **WindowsSucks said:**
> Blacklisting and rmmod'ing snd_pcsp seems to have cleared everything up in the sound department. Thanks for pointing me in the right direction there.

So, that leaves crapped up framebuffer, no VTs, and one hell of a screwed up Mesa. Luckily the last one is a known bug from what I've heard.

Ah, perhaps your point number 1. is related to compiz, I didn't realize from your description. Lots of people are having trouble with it at the moment. I can personally get compiz working on my Intel 855GM system if I invoke compiz like this:
```
$ LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```... but others do not have such luck. Hopefully it'll get fixed soon, but in the meantime keep "Desktop Effects" off.

---

### Post by klange on 2008-07-13
Well, it would seem the virtual terminal problems / framebuffer anomalies were because someone made the decision to switch to uvesafb. Well that's all fine and dandy, but it'll destroy configurations that have a vga= line.

Also, now that I can see what's happening on my boot, sendmail freezes on startup. (I used to just see a black screen with no CPU activity for a while, then my display would flash a few times and GDM would start)
(I also can't get the recommended video= options to work with uvesafb, why'd we have to switch in the first place?)

Why are we using rc1 of this Mesa branch when rc3 is out?
Forcing INDIRECT seems to be fine for me, but the decreased framerate will drive me crazy.
Also, I need to put in a bug report for mag...

---

### Post by Nullack on 2008-07-13
My main issue is the broken install from grub failing to set root properly. Also the gnome file roller bug I reported is an annoyance along with the no vga= setting on boot with the framebuffer issue.

---

### Post by klange on 2008-07-13
It seems, even with the vga= option removed uvesafb will sometimes (read: randomly) not load, leaving you with no framebuffer. Seems X doesn't want to show up whenever this happens, leaving me with a blank screen and a flashing CPU-activity light.
Sendmail is still being a pain in the ***, I'm going to go disable it completely...

acpid also incorrectly stops at startup, leaving me without much of anything. I can successfully restart it after logging, though.

---

### Post by RAOF on 2008-07-14
> **WindowsSucks said:**
> ...
Forcing INDIRECT seems to be fine for me, but the decreased framerate will drive me crazy.
Also, I need to put in a bug report for mag...

Unless something's changed quite recently, you've never had a direct-rendered Compiz.  I'm not sure what's happened with the wrapper script, but it would previously set that variable for you on ati and intel cards.  Maybe the new mesa is confusing the script?

---

### Post by klange on 2008-07-14
> **RAOF said:**
> Unless something's changed quite recently, you've never had a direct-rendered Compiz.  I'm not sure what's happened with the wrapper script, but it would previously set that variable for you on ati and intel cards.  Maybe the new mesa is confusing the script?
The newest Mesa has direct rendering, but the exact build being used in Intrepid has some problems. I've very much so used [direct-rendered Compiz on Intel](http://www.youtube.com/watch?v=4SoyuG4ygmI&feature=user) before ;)
And there is a decreased framerate when you force it like this. (50 vs. 60)
And really, it's [not that big of a deal](http://www.youtube.com/watch?v=BrK4c7iFJLs).

---

### Post by plun on 2008-07-14
> **WindowsSucks said:**
> The newest Mesa has direct rendering, but the exact build being used in Intrepid has some problems. I've very much so used [direct-rendered Compiz on Intel](http://www.youtube.com/watch?v=4SoyuG4ygmI&feature=user) before ;)
And there is a decreased framerate when you force it like this. (50 vs. 60)
And really, it's [not that big of a deal](http://www.youtube.com/watch?v=BrK4c7iFJLs).

Nice videos !

[SIZE="1"]Intel for next PC.. ;)[/SIZE]

I think for your level of knowledge you must read Debians list
[http://lists.debian.org/debian-x/2008/07/threads.html](http://lists.debian.org/debian-x/2008/07/threads.html)

You can also find Ubuntus maintainer among XstrikeForce 


[SIZE="1"](Compiz-GIT works just fine on nVidia)[/SIZE]

---

### Post by ASULutzy on 2008-07-14
Going to bump this talk about the mesa bug with compiz, just to keep it up there... It's a really the only dealbreaker stopping me from using Intrepid a lot more. I'm experiencing the same white screen/keyboard breaks bug mouse works/have to vulcan nerve pinch it.

Hopefully this gets fixed soon! Wish I knew more about how driver coding goes :'(

---

### Post by klange on 2008-07-15
> **ASULutzy said:**
> Going to bump this talk about the mesa bug with compiz, just to keep it up there... It's a really the only dealbreaker stopping me from using Intrepid a lot more. I'm experiencing the same white screen/keyboard breaks bug mouse works/have to vulcan nerve pinch it.

Hopefully this gets fixed soon! Wish I knew more about how driver coding goes :'(

Mesa's actually been borked like this for a while. I just remembered that my DRI2-enabled server has this same bug (I first discovered it for myself when not setting the "DRI2" option properly in my xorg.conf, leaving me with classic DRI and white windows in Compiz).

Instead of a direct fix, I'd like to see more attention put towards DRI2. Of course, that won't happen until the GEM vs. TTM debate dies (GEM seems to be out front considerably, though, but DRI2 currently uses TTM). Speaking of TTM, the performance issues I've noticed may be related to Mesa / X 's apparent reliance on it. It continually complains that's it's "falling back to classic" because we don't have TTM.

---

### Post by psyke83 on 2008-07-15
> **WindowsSucks said:**
> Mesa's actually been borked like this for a while. I just remembered that my DRI2-enabled server has this same bug (I first discovered it for myself when not setting the "DRI2" option properly in my xorg.conf, leaving me with classic DRI and white windows in Compiz).

Instead of a direct fix, I'd like to see more attention put towards DRI2. Of course, that won't happen until the GEM vs. TTM debate dies (GEM seems to be out front considerably, though, but DRI2 currently uses TTM). Speaking of TTM, the performance issues I've noticed may be related to Mesa / X 's apparent reliance on it. It continually complains that's it's "falling back to classic" because we don't have TTM.

That has something to do with missing libdrm headers during compile of the intel driver. When configuring the intel driver, if it says:

```
Checking for DRI_MM... no
```

Then you're missing necessary files. Debian (and Ubuntu) don't include these files in the libdrm2/libdrm-dev package, but you can get them from git.

---

### Post by RAOF on 2008-07-16
> **WindowsSucks said:**
> The newest Mesa has direct rendering, but the exact build being used in Intrepid has some problems. I've very much so used [direct-rendered Compiz on Intel](http://www.youtube.com/watch?v=4SoyuG4ygmI&feature=user) before ;)
And there is a decreased framerate when you force it like this. (50 vs. 60)
And really, it's [not that big of a deal](http://www.youtube.com/watch?v=BrK4c7iFJLs).

Oh, you mean building all sorts of stuff from git branches.  Yeah, that'll give you direct-rendered compiz.  But it hasn't (and seems unlikely to, for Intrepid) been with Ubuntu packaged/stable releases.

The Great GPU Memory Manager Wars suck, but there you go.  It's worth getting right :).

---

