---
title: "Mplayer config HEADS-UP!"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2007-11-24
A recent upgrade to mplayer changed a few things, but most noticably the use in side the config file of "vop" which appears to be no longer allowed and is replaced by the pre-existing "vf"

I specifically use a deinterlacing and deblocking filter for dvb tv playback anbd recording and video playback as follows:
```
vop=pp=x20077
```
this is a line in the config file in the .mplayer directory in my /home. if you have similar you may find that mplayer won't start. If you run mplayer in a terminal it will tell you that vop cannot be used and to use vf instead.

Closest replacement I can find at present is:
```
vf=pp=lb
```
which certainly deals with deinterlacing. This can be combined with deblocking and deringing filters:
```
vf=pp=hb/vb/dr
```

for more help on post processing filters (pp), open a terminal and type:
```
mplayer -pphelp
```

---

