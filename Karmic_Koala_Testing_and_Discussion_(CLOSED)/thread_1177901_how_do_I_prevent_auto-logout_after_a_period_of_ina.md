---
title: "how do I prevent auto-logout after a period of inactivity?"
date: 2009-06-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-06-03
This has only started for me within the last few days. If I start a long download and walk away, on return, I find that I'm logged out and have to start the download again. I would guess the logout happens after about 15 mins, but that's just a guess.
Is there any way to prevent this 'feature'?
Cheers, Mike

---

### Post by hexsel on 2009-06-03
you sure the computer is not rebooting while you're not looking?

maybe you've found a bug... or your cables are loose :)

---

### Post by tad1073 on 2009-06-04
have you enabled "Put Computer to sleep when inactive for:" in powder management?

---

### Post by mdurham on 2009-06-04
> **tad1073 said:**
> have you enabled "Put Computer to sleep when inactive for:" in powder management?

No tad1073, I haven't done that but, I've found it's something to do with the screen-saver. I have screen-saver = Blank screen, and Activate when idle. This somehow logs me out and I get the login screen.
It didn't do this several days ago, so something has changed. I'll disable the screen-saver and see what happens.
Cheers, Mike

P.S. It seems that it was the screen-saver. If I disable it, no logout.

---

### Post by Foaming Draught on 2009-06-04
Do you have an [Intel graphics]("http://ubuntuforums.org/showthread.php?t=1177517") card?

---

### Post by pressureman on 2009-06-04
I just noticed this last night also. I don't think it's intended behaviour, because Xorg log shows a backtrace. I've disabled screensaver for now too. 

Screensavers are pretty moot on LCD panels - unless you're using them as a privacy lock, or a power saver (which most of the screensavers aren't, as they're CPU hogs).

I have a Thinkpad T500 with ATI HD3650 and Intel integrated gfx.

---

### Post by mdurham on 2009-06-04
> **Foaming Draught said:**
> Do you have an [Intel graphics]("http://ubuntuforums.org/showthread.php?t=1177517") card?

Yes I do 945/950 as far as I remember.

---

### Post by cdEWoozy on 2009-06-04
See [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/383129](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/383129).

---

### Post by macroshaft on 2009-06-04
So is this actually logging out or rebooting? I was beginning to think I was going mad!

p.s. got intel x3100 graphics here

---

### Post by meeples on 2009-06-04
its the same issue as here [http://ubuntuforums.org/showthread.php?t=1177517]("http://ubuntuforums.org/showthread.php?t=1177517")

i think its been fixed now though but im not sure.

---

### Post by caryb on 2009-06-04
I had the same problem with KDE4/Kubuntu & I had to fix mine by opening the power manager & deselecting the logout after 15 mins inactivity. 

BTW I Have a Nvidia 140 mobility graphics chipset.


Cary

---

