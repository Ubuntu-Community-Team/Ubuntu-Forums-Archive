---
title: "tough time with festival"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by bulls_eye on 2010-06-27
hi

i've installed festival on my ubuntu 9.10 desktop environment by following this link

[http://ubuntuforums.org/showthread.php?t=751169](http://ubuntuforums.org/showthread.php?t=751169)

i've installed the standard festvox diphone voices.

i am having hard time in running this program

for eg if i type festival i get the error

SIOD ERROR: unbound variable : voice_awb_us_clb_arctic_clunits
closing a file left open: /usr/share/festival/init.scm
festival: fatal error exiting.

this one was resolved by typing festival -q

but then 

festival> SayText "hello"
SIOD ERROR: unbound variable : SayText

festival> (voice.list)   
SIOD ERROR: unbound variable : voice.list

irrespective of what command i give i get the same error...

any ideas??

---

