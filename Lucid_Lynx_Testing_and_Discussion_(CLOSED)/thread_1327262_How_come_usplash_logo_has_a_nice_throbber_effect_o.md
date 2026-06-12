---
title: "How come usplash logo has a nice throbber effect only on livecd"
date: 2009-11-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-11-15
Once installed just looking at white ubuntu logo is boring.

For newbies it looks like nothing is happening.

---

### Post by VMC on 2009-11-15
Aren't you getting the text messages below the "white ubuntu logo"? That should tell someone that it's alive.

Are you wanting the "white ubuntu logo" to pulsate or something?

---

### Post by Vanishing on 2009-11-15
> **VMC said:**
> Aren't you getting the text messages below the "white ubuntu logo"? That should tell someone that it's alive.

Are you wanting the "white ubuntu logo" to pulsate or something?

that is if you turned off the "quiet"..
some animation will be nice tbh...

---

### Post by erkiha on 2009-11-15
strange thing is that it does pulsate when running live cd, but not when installed.

---

### Post by fluteflute on 2009-11-15
I wondered this too actually. I think the glow/throb would be nice on every startup.

---

### Post by philinux on 2009-11-15
> **VMC said:**
> Aren't you getting the text messages below the "white ubuntu logo"? That should tell someone that it's alive.

Are you wanting the "white ubuntu logo" to pulsate or something?

No text, and yes pulsate as on livecd would be nice. Agree with other posters it just looks dead.

---

### Post by Squonk07 on 2009-11-15
I noticed this, too. I imagine it was made to throb for the LiveCD version because the usplash remains on the screen for longer than it does on a full install; I suppose this is to reassure new users that their computer hasn't locked up.

---

### Post by phrizek on 2009-11-15
> **Squonk07 said:**
> I noticed this, too. I imagine it was made to throb for the LiveCD version because the usplash remains on the screen for longer than it does on a full install; I suppose this is to reassure new users that their computer hasn't locked up.

That makes a ton of sense.

Anyhoo, aren't we ditching the usplash with lucid entirely?

---

### Post by autocrosser on 2009-11-15
> **philinux said:**
> No text, and yes pulsate as on livecd would be nice. Agree with other posters it just looks dead.

Have you tried to pull the usplash off of the LiveCD?

---

### Post by Starks on 2009-11-15
Keybuk said a few weeks ago that the lack of pulsation for an install is quite intentional and in line with plans to completely do away with the need for usplash.

---

### Post by celticbhoy on 2009-11-15
> **Starks said:**
> Keybuk said a few weeks ago that the lack of pulsation for an install is quite intentional and in line with plans to completely do away with the need for usplash.

That may be so, but when will we lose usplash?

I am with phil on this, on slower hardware usplash can sit for a while, it would be nice if it animated even slightly.

---

### Post by inportb on 2009-11-16
We will not lose usplash, as it's still needed in certain situations.

---

### Post by wilee-nilee on 2009-11-16
The pulse is to distract you because live boots are slow. you getting sleepy sleepy sleepy. ;)

---

### Post by Starks on 2009-11-16
> **inportb said:**
> We will not lose usplash, as it's still needed in certain situations.

I understand that. What irks me though is that Keybuk didn't believe that there was a single Ubuntu user, who in either Karmic or Lucid, that was staring at the logo for more than 5 seconds during boot. When I told him that I was at Usplash for 10 seconds, he didn't believe me and said that even if that was true, it wasn't worth adding the pulse for installed machines even if it would help reassure Linux newbies that their machine hasn't crashed.

---

### Post by philinux on 2009-11-16
> **Starks said:**
> I understand that. What irks me though is that Keybuk didn't believe that there was a single Ubuntu user, who in either Karmic or Lucid, that was staring at the logo for more than 5 seconds during boot. When I told him that I was at Usplash for 10 seconds, he didn't believe me and said that even if that was true, it wasn't worth adding the pulse for installed machines even if it would help reassure Linux newbies that their machine hasn't crashed.

12.5 seconds here. Seems like an eternity. Some people get longer too.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453337](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453337)

---

### Post by philinux on 2009-11-16
> **autocrosser said:**
> Have you tried to pull the usplash off of the LiveCD?

Unsquashed and install the usplash /usr/lib/usplash/usplash-theme-ubuntu-livecd.so 

Done the up[date alternatives and sudo update-initramfs -u.

Still no throb. lol

---

### Post by Locke_99GS on 2009-11-16
No throb on Karmic either. Disappointing after seeing it throb on the LiveCD.

---

### Post by Starks on 2009-11-16
From the UDS boot experience panel:

```
<LLStarks> so, in laymans terms. what's happening with xsplash, usplash, and plymouth specifically?
<robbiew> usplash is going away
<robbiew> xsplash may remain
```

Furthermore, Plymouth is definitively replacing usplash.

---

### Post by inportb on 2009-11-16
That is quite interesting. At any rate, Kubuntu users still aren't seeing any xsplash action and usplash throbs just fine.

---

