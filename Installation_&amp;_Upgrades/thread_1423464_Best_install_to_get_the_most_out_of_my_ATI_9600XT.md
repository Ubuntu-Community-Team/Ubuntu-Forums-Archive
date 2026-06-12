---
title: "Best install to get the most out of my ATI 9600XT ?"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2010-03-06
I want to know what is the installation type I have to do to get the most out of my ATI Radeon 9600XT which ATI's driver have been dropped since 9.3 ?

I currently have Xubuntu 9.10 but the drivers are not right.

I am thinking of getting back to 8.10 or 8.04.  Should I ?

Or should I somehow install some special ATI drivers on top of my 9.10 ?

I know about Cedega but am looking at other solutions.

I want this so I can run one the few games I have on it and be able to use OpenSim, Hippo, SecondLife and the likes on it without graphic lagging + I want to move away from Windows.  I don't care about special desktop effects and can live without them.  I want maximum graphic performances out of my ATI card. Can't afford for anything else (no money).

---

### Post by Timothy Taylor on 2010-03-06
The upgrade to 9.10 unleashed a whole torrent of problems for me, which I suspect are related to issues with my Radeon 9200.

See [_this_]("http://ubuntuforums.org/showthread.php?t=1419284") thread.

9.04 seemed to work perfectly before, but now only works in "safe graphics mode" for some reason.

---

### Post by Mark Phelps on 2010-03-06
There are no "special drivers" that will work with any recent Ubuntu version and your card.  As you already know, ATI dropped Linux driver support for your card a while back.  

All that is available now is the open source drivers -- and those are installed by default.

---

### Post by immerohnegott on 2010-03-07
I'm using Kubuntu 8.04 (KDE3) on my old desktop, which has a 9600Pro. This is about as new as you're going to get and still be able to use the ATI driver, as you need a kernel older than like 2.6.28 or some mess like that.

You may be able to get it up and running on 8.10, but I haven't tested it.
Suffice it to say, you're S.O.L with getting FGLRX/Catalyst running on anything newer than that.

You may also want to go with an even lighter environment as well. XFCE hasn't really been great in my experience, especially compared to more bare-bones stuff like the *Box WMs, or E17. This might eke some more performance out of your system.

---

