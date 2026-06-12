---
title: "Mplayer hide and seek?"
date: 2009-06-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-06-09
I just noticed in my ubuntu box, mplayer disappeared..It will not show up in the menus, won't run with alt-f2, but it shows its status installed.
Strange.
anybody else having this problem?

---

### Post by Vanishing on 2009-06-09
I tried using terminal to fire up mplayer with a media file, it worked, but without any UI like before, just the video shows up.
Seems like only the core is left, but the UI is gone...o.o

---

### Post by taavikko on 2009-06-09
What does ```
dpkg -l mplayer\*
```
print?

have you tried re-installing mplayer (mplayer-nogui is the one without the GUI)

---

### Post by Vanishing on 2009-06-09
output:
> vanishing@Vanishing:~$ dpkg -l mplayer\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mplayer        2:1.0~rc3+svn2 movie player for Unix-like systems
un  mplayer-386    <none>         (no description available)
un  mplayer-586    <none>         (no description available)
un  mplayer-686    <none>         (no description available)
un  mplayer-amd64  <none>         (no description available)
un  mplayer-custom <none>         (no description available)
un  mplayer-doc    <none>         (no description available)
un  mplayer-g4     <none>         (no description available)
un  mplayer-k6     <none>         (no description available)
un  mplayer-k7     <none>         (no description available)
ii  mplayer-nogui  2:1.0~rc3+svn2 movie player for Unix-like systems
un  mplayer-powerp <none>         (no description available)
un  mplayer-skin   <none>         (no description available)
ii  mplayer-skin-b 1.6-2          blue skin for mplayer
ii  mplayer-skins  2-7            Skins for the Ubuntu mplayer Package
un  mplayerplug-in <none>         (no description available)


Seems I have mplayer-nogui installed..but I have no idea how it got installed. I tried to reinstall mplayer, same result.
Should I remove the nogui package?
Thanks.

---

### Post by taavikko on 2009-06-09
I would purge the nogui version.
(personally I use the nogui version & smplayer frontend)

You seem to have some PPA in use cause the extra lines from the prinf of dpkg? Might cause some of the problems.

---

### Post by Vanishing on 2009-06-09
I tried to remove mplayer-nogui in synaptic, but that will remove all mplayer related..

---

### Post by NCLI on 2009-06-09
> **Vanishing said:**
> I tried to remove mplayer-nogui in synaptic, but that will remove all mplayer related..

Do that, then "apt-get install smplayer"

---

### Post by BwackNinja on 2009-06-10
'gmplayer' opens up mplayer with a gui interface, 'mplayer' is just the command line version.

---

### Post by Vanishing on 2009-06-10
Ok..
uninstalled mplay-nogui, apt-get"ed" smplayer.
I think I LOVE IT..lol
thanks for tha tip man..

---

### Post by NCLI on 2009-06-10
> **Vanishing said:**
> Ok..
uninstalled mplay-nogui, apt-get"ed" smplayer.
I think I LOVE IT..lol
thanks for tha tip man..

My pleasure :KS

---

### Post by Vanishing on 2009-06-10
A lot of thinks seem to work on my machine now which didn't b4..
such as svn with "http/https", smplayer :), conky etc etc..
Im grateful..

---

