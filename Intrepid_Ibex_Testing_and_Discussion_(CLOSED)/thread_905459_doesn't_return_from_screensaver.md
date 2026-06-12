---
title: "doesn't return from screensaver"
date: 2008-08-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by orduek on 2008-08-30
since last update i noticed my laptop can't return from screensaver.
when I see it in black screen i can't make it work again. has to turn it off physically.

---

### Post by vishalrao on 2008-08-30
if powersaving/suspend is enabled you might need to disable it and just use screensaver plus screen blanking thats all

---

### Post by ronacc on 2008-08-30
you mean your screensaver actualy works ? it hasn't for me simce alpha1 . see this bug   [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/256586/](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/256586/)

---

### Post by vikrant82 on 2008-08-30
Screensaver (blank screen) was working for me also.

This one is really scary. Physically powering off seems to be only option. The entire X hangs, even Caps lock etc. 

However, the machine is running fine, as I can see behind the hanged X, the music playing fine, downloads running fine etc

The only way to reboot safely from SSH remotely.

OFFed the screensaver for now.

Anyone raised a bug for this one ?

---

### Post by plun on 2008-08-30
> **vikrant82 said:**
> Screensaver (blank screen) was working for me also.

This one is really scary. Physically powering off seems to be only option. The entire X hangs, even Caps lock etc. 



I am always using **Ctrl-Alt-Backspace**   for X-restarts and
to be able to shut down a PC when Gnomes GUI is broken.
[COLOR="Red"]
Never,Never do a power off.....[/COLOR]

If a PCs is hanged use "**Magic SysRq**"

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

> To perform a safe reboot of a Linux computer which has otherwise locked up, the QWERTY (or AZERTY) mnemonic "Raising Skinny Elephants Is Utterly Boring" or "Raising Elephants Is So Utterly Boring", the more sensible "Reboot Even If System Utterly Broken" or simply remembering the word "BUSIER" backwards, is often useful. It stands for

     unRaw (take control of keyboard back from X),
      tErminate (send SIGTERM to all processes, allowing them to terminate gracefully),
      kIll (send SIGKILL to all processes, forcing them to terminate immediately),
       Sync (flush data to disk),
       Unmount (remount all filesystems read-only),
    reBoot. These keystrokes should be entered a few seconds apart. 

:)

---

### Post by orduek on 2008-08-30
> **plun said:**
> I am always using **Ctrl-Alt-Backspace**   for X-restarts and
to be able to shut down a PC when Gnomes GUI is broken.
[COLOR="Red"]
Never,Never do a power off.....[/COLOR]

If a PCs is hanged use "**Magic SysRq**"

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)



:)

I tried both. none worked. only hard physical power off :(

---

### Post by plun on 2008-08-30
> **orduek said:**
> I tried both. none worked. only hard physical power off :(

Well...  strange

The SysRq key can be tricky and F-functions must often be turned off

Alt-SysRq-b   or u   never fails for me.

---

### Post by ronacc on 2008-08-30
@ plun I occcasionaly get lockups so complete that the keyboard doesn't work at all even alt SysReq , keystrokes of anykind just dont get through , this is usualy accompanied by flashing numlock and caplock leds .

---

### Post by yellerKat on 2008-08-30
Weird, on both the laptop (i386) and desktop (AMD64), the ESC button brings them out of screensaver (and not the mouse, obviously!)

---

### Post by mattduckman on 2008-08-30
i get this issue whenever the screen is locked. i'm on a laptop, and both the mouse and keyboard don't do anything, but if i plug in a external keyboard, i can use ALT-CTRL-DEL to safely reboot the computer, but nothing else works (like restarting X). i noticed that if the keyboard is already plugged in, i need to unplug it and plug it again before i can reboot my computer.

weird stuff. has anyone filed a bug yet?

---

### Post by ketk on 2008-08-31
I've my laptop configured to do nothing when I close the screen (just shut down screen). But if I close it long time (just if long time) happends the same described here.
I found no way to return to my desktop, 'REISUB' or Ctrl+Alt+Backspace doesn't work.
Graphic card: intel GM965
Intrepid 64bit updated.

---

### Post by Starks on 2008-08-31
I am also experiencing this problem. It also happens if I use the screen locking function.

---

### Post by Nullack on 2008-08-31
I cant replicate the issue:

1. Are you all sure youve synched to the repos?
2. Are you all sure that your repo mirror isnt out of date?
3. Have you got some configs in xorg.conf that is causing conflicts? e.g. Many so called tweaks to xorg.conf breaks things and really a minimal conf is the way to go.

---

### Post by ntetreau on 2008-09-01
I have an Intel GMA965 video card, 2200 wifi card and I can replicate the issue everytime the screen locks.  Has anybody submitted a bug report yet? If not, I'll do it.

---

### Post by zombiepig on 2008-09-01
Another one here with an intel 965 which locks on screensaver - no key combinations can safely resurrect the machine, only hard powering off works.

---

### Post by Nullack on 2008-09-01
Is these machines actually powering down / hibernating / suspend to disk or is it just locking on the screensaver itself?

---

### Post by RAOF on 2008-09-01
This sounds like a mesa/3d issue.  Someone said that setting the screensaver to "blank screen" didn't exhibit this behaviour?  Does setting the screensaver to one of the following
```

/usr/lib/xscreensaver/abstractile
/usr/lib/xscreensaver/cwaves
/usr/lib/xscreensaver/deco
/usr/lib/xscreensaver/distort
/usr/lib/xscreensaver/fiberlamp
/usr/lib/xscreensaver/fuzzyflakes
/usr/lib/xscreensaver/galaxy
/usr/lib/xscreensaver/m6502
/usr/lib/xscreensaver/metaballs
/usr/lib/xscreensaver/penrose
/usr/lib/xscreensaver/popsquares
/usr/lib/xscreensaver/ripples
/usr/lib/xscreensaver/shadebobs
/usr/lib/xscreensaver/slidescreen
/usr/lib/xscreensaver/sonar
/usr/lib/xscreensaver/swirl
/usr/lib/xscreensaver/xlyap

```
exhibit this behaviour? (that's the set of screensavers that don't link to libGL)

Are you using Compiz?  If so, does it happen with compiz disabled?  Is 'unredirect fullscreen windows' checked in ccsm?  If so, does unsetting it work?

---

### Post by ntetreau on 2008-09-01
> **RAOF said:**
> This sounds like a mesa/3d issue.  Someone said that setting the screensaver to "blank screen" didn't exhibit this behaviour?  Does setting the screensaver to one of the following
```

/usr/lib/xscreensaver/abstractile
/usr/lib/xscreensaver/cwaves
/usr/lib/xscreensaver/deco
/usr/lib/xscreensaver/distort
/usr/lib/xscreensaver/fiberlamp
/usr/lib/xscreensaver/fuzzyflakes
/usr/lib/xscreensaver/galaxy
/usr/lib/xscreensaver/m6502
/usr/lib/xscreensaver/metaballs
/usr/lib/xscreensaver/penrose
/usr/lib/xscreensaver/popsquares
/usr/lib/xscreensaver/ripples
/usr/lib/xscreensaver/shadebobs
/usr/lib/xscreensaver/slidescreen
/usr/lib/xscreensaver/sonar
/usr/lib/xscreensaver/swirl
/usr/lib/xscreensaver/xlyap

```
exhibit this behaviour? (that's the set of screensavers that don't link to libGL)

Are you using Compiz?  If so, does it happen with compiz disabled?  Is 'unredirect fullscreen windows' checked in ccsm?  If so, does unsetting it work?

Yes I am using compiz, disabling compiz fixes the problem.  Also, unchecking 'unredirect fullscreen windows' when using compiz also fixes the problem.  All these tests were done using Blank as screensaver, 1min, and lock.

So should I submit a bug report for compiz?
Thanks RAOF!

---

### Post by grumpymole on 2008-09-02
Same here.  Intrepid amd64, Intel onboard graphics adapter.

Regards

---

### Post by Nullack on 2008-09-02
Well I installed compiz, tried to get it to show the bug with CTL ALT L to lock, waited a few mins, came to gnome lock screen via mouse and then keyboard worked fine for logging in with pwd

Im on nvidia 177.70

---

### Post by Starks on 2008-09-02
Solution is to use xscreensaver instead of gnome-screensaver

---

### Post by mattduckman on 2008-09-02
> **Nullack said:**
> Well I installed compiz, tried to get it to show the bug with CTL ALT L to lock, waited a few mins, came to gnome lock screen via mouse and then keyboard worked fine for logging in with pwd

Im on nvidia 177.70

if you're using a binary nvidia driver, i don't think it would use mesa, would it?

---

### Post by vikrant82 on 2008-09-04
> **Nullack said:**
> Is these machines actually powering down / hibernating / suspend to disk or is it just locking on the screensaver itself?

The machine is running fine behind the hanged X. All the programs are running fine, in the background. So mostly, I SSH from one of other machines and reboot the machine. Just that, locally you can't do anything with the machine.

---

### Post by joakim2 on 2008-09-07
Did anyone submit a bug report for this? I'm suffering from the same problem on my Dell Latitude D505. Unchecking "unredirect fullscreen windows" in ccsm helped some, it doesn't always get stuck at the blank screen now, just most of the time :)

---

### Post by Josh04 on 2008-09-07
Same issue here, Intel 965. Is there a bug report?

---

### Post by avb on 2008-09-07
same here. i965

---

### Post by Foaming Draught on 2008-09-08
> **Starks said:**
> Solution is to use xscreensaver instead of gnome-screensaver

You're right insofar as xscreensaver has a "disable screensaver" checkbox :wink: , otherwise Intel Graphics still freeze and can only be recovered by shutting down and re-starting power (and in the case of a laptop, disconnecting and re-connecting the battery).

Thank the Lord for Firefox' "Do you want to resume previous session?"

FD

---

### Post by napsy on 2008-09-08
It's the same for me but don't know if it's a gnome-screensaver or a gnome-power-manager issue. Can't find any related bug reports.

---

### Post by BC7333 on 2008-09-08
I submitted this bug a while back but seems to be 'stuck'..

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212514](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212514)

ONLY happens to me when the power is plugged in and when I'm typing something.

Anyone notice the same?

---

### Post by yelo3 on 2008-09-09
The hard lock is present in my case even if I use the black screensaver. So are you sure that it is caused by gnome-screensaver and not by gnome-power-manager?

---

### Post by avb on 2008-09-09
just thoughts before fill a bug:

avb: the problem is that gnome-screensaver locks up machine when its running on pc with intel videocard
avb: accourding to forum users have it only with i965 chipsets
avb: [http://ubuntuforums.org/showthread.php?t=905459](http://ubuntuforums.org/showthread.php?t=905459)
avb: so, there is few things
avb: 1. bug goes away when u disable 'Unredirect Fullscreen windows'
avb: in compiz settings
avb: so, probably bug in compiz
avb: 2. $ glxinfo|grep render 
avb: direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
avb: thats a second issue. why for now compiz for i965 starts with LIBGL_ALWAYS_INDIRECT and there is no DRI
avb: so probably a bug in mesa
avb: 3. probably a bug in intel driver
avb: so maybe one of maintainers is here?
avb: and we can find a sence of bug togeather?

---

### Post by ntetreau on 2008-09-09
> **avb said:**
> just thoughts before fill a bug:

avb: the problem is that gnome-screensaver locks up machine when its running on pc with intel videocard
avb: accourding to forum users have it only with i965 chipsets
avb: [http://ubuntuforums.org/showthread.php?t=905459](http://ubuntuforums.org/showthread.php?t=905459)
avb: so, there is few things
avb: 1. bug goes away when u disable 'Unredirect Fullscreen windows'
avb: in compiz settings
avb: so, probably bug in compiz
avb: 2. $ glxinfo|grep render 
avb: direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
avb: thats a second issue. why for now compiz for i965 starts with LIBGL_ALWAYS_INDIRECT and there is no DRI
avb: so probably a bug in mesa
avb: 3. probably a bug in intel driver
avb: so maybe one of maintainers is here?
avb: and we can find a sence of bug togeather?

Stupid mistake on my part, I' m having this issue, now intermittently, on my laptop with intel 855GM, not 965 as I wrote before.

---

### Post by Borlag on 2008-10-26
Not the exact same issue, but is it an intentional change that simply moving the mouse doesn't remove the screensaver anymore? Same happens when the screen is locked. I can get it functioning again by clicking the mouse button, or any key from the keyboard.

---

### Post by ktp on 2008-10-26
I have seen the same things...have to click or type.

---

### Post by olavjunior on 2008-10-29
I'm having this problem now, but haven't had it earlier in the testing stage! If I look screen and screensaver starts, or if it just start from it self, I have to do a hard power off. I'm gonna try the compiz trick though! But odd I haven't gotten this bug until now

---

