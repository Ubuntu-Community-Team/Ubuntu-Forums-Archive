---
title: "xbmc"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-10-17
has anyone figured out how to install xbmc ( a cool media player and more in 9.10) if so could you share

---

### Post by Gourgi on 2009-10-17
> **rburkartjo said:**
> has anyone figured out how to install xbmc ( a cool media player and more in 9.10) if so could you share

this is the ppa i currently use for xbmc and it runs fine
```
deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu karmic main
```

enjoy :popcorn:

---

### Post by rburkartjo on 2009-10-18
tks gourgi worked like a charm. appreciate it

---

### Post by e-Gee on 2009-10-18
Not working for me I instald xbmc like that on Acer Aspire One (UNR Karmic) but won't start .

---

### Post by rburkartjo on 2009-10-18
e good luck i just followed gourgi advise and it worked for me

---

### Post by jbernardo on 2009-10-18
I would advise to stay away from the svn ppa, as xbmc is going through a major merge and large instability. The latest versions won't play non-h264 videos properly on my media centre (a P4 HT), with lots of skips and loss of sync between video and sound, with over 10 sec. lags. The xbmc-live cd shows those properly, no skips at all - so I am going back to the "regular" version.

---

### Post by Tompalaz on 2009-10-18
> **e-Gee said:**
> Not working for me I instald xbmc like that on Acer Aspire One (UNR Karmic) but won't start .

this is a bug in the SVN PPA. Go to ~/-xbmc/skin/whateverskin_you_use
open the skin.xml. Go to the <version> tag where it sais 2.11, change that to 3.0.

---

### Post by briancb on 2009-10-19
I use the ppa for karmic but xbmc does not show up in synaptic so I installed it by the following instructions

[http://xbmc.org/wiki/?title=HOW-TO_compile_XBMC_for_Linux_on_Debian/Ubuntu](http://xbmc.org/wiki/?title=HOW-TO_compile_XBMC_for_Linux_on_Debian/Ubuntu)

This works fine, videos play but cannot get any sound at all. Tried every option but get the message audio device failed to initialize. :(

---

