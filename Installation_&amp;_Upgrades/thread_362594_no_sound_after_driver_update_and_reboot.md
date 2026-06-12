---
title: "no sound after driver update and reboot"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by myname on 2007-02-15
Hello all...

I am running Ubuntu Edgy with the KDE desktop,
ATI Radeon X1600 graphics card
SB Audigy card

Everything was working fine a couple hours ago, playing WoW, no problem.

I was checking some settings on the system with my other Kubuntu Edgy system, so I logged off my U-Edgy KDE session and logged into Gnome.  The system told me I needed to reboot in order for the updates to take effect.  Ok, it's been awhile since I rebooted.  I rebooted.  Logged into KDE like normal, and went to play WoW.  I got a message sayin WoW could not start 3d.  I checked the ATI control panel and it said I was using the MESA drivers.  WTF?  I didn't do anything with my drivers.

I re-installed the ATI drivers, all is good, got that back, but now my sound is GONE.  I have no sound.

I don't know what to check, b/c I don't know what that system message reboot did.

I checked alsamixer, and it appears to be on, but not sure how to get my sound back.

Anyone have any ideas on where to look?


--Kevin

---

### Post by Kateikyoushi on 2007-02-15
Must have been the kernel update I would recommend to follow these steps to pinpoint what went wrong. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
I guess the module is not loaded in that case you can solve it in few minutes.

---

### Post by myname on 2007-02-16
No go on this... Tried everything, even a re-install of the Alsa,and nothing (had to reinstall the GDM Ubuntu-desktop too).

any ideas, short of a re-install of Ubuntu?

---

### Post by myname on 2007-02-16
> **Kateikyoushi said:**
> Must have been the kernel update I would recommend to follow these steps to pinpoint what went wrong. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
I guess the module is not loaded in that case you can solve it in few minutes.

I went to the link above, and got down to the following steps:
"Getting the ALSA drivers from a *fresh* kernel"

I performed that, even had to reinstall the ubuntu desktop.  When I restarted, the sound still wasn't there.  However, when Ubunutu is loading up, I can hear the "pop" of the speakers/subwoofer kicking in/getting a signal to them, but no sound, and I do have my volume is turned up.

any idea?  I may be doing a fresh install when I get home from work, but I would hate to do that.

--Kevin

---

### Post by Kateikyoushi on 2007-02-16
What is the output of this command ?
```
aplay -l
```

---

### Post by myname on 2007-02-16
I reinstalled the alsa twice, and everything is now working.

Thanx for everyone's help.

now on to my video driver problem on my second machine, recently converted to Kubuntu.

--Kevin

---

### Post by jean noel on 2007-10-05
This could have been my message....It took me three Ubuntu reinstallatios to find that some updates were interfering with Ubuntu recognizing my sb audigy . In despair, I presently download. :- updates one by one to find out the culprit :-)

---

