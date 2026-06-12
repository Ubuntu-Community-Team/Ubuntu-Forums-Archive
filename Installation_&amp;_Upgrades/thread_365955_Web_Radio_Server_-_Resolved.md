---
title: "Web Radio Server - Resolved"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by jorgerosa on 2007-02-20
**Complete visual tutorial (VERY SIMPLE!) to install a complete webradio server.**

Ive lost days on trying, searching, ask for help about this and... nothing!
Of course this tutorial is very basic, but if ive found something like this i could really spent just an hour or two and not lots of days!!!
Now i know is very simple to do this, but im new to UBUNTU (and Linux, only about 15 days of using it) and i had NO idea how to start.
PS: Guys to help the others (like me) try DO NOT comment on the forums (its waste of time and database space :idea: ), just give simple solutions and try to be really helpfull! We (beginners) just thanks.* (sorry my english)  *

[COLOR="Navy"]Software: UBUNTU + ICECAST2 + DARKICE (and DARKSNOW as DARKICE GUI)[/COLOR]

---

### Post by ykanello on 2007-03-26
So compared with other OS's linux SUCKS in this case. I am really really sorry to say but while everyone else can stream anyway they want , we are restricted to the input port of our sound card...
this is soooo damn lame. One week I am trying to stream to ICECAST2 from linux, and I cannot. Meanwhile every tom dick and harry with windows is already streaming.
Xmms doesn't it crashes when I start the streaming:
```
LANG=C xmms       
Message: device: default
Gdk-ERROR **: X connection to :0.0 broken (explicit kill or server shutdown).

```
Not with VLC not with anything. Only ICE2 and darkice,/snow, but IT IS FAR from what I wanted. 

For the first time after 8 years using only linux I am really really disapointed...

---

### Post by jorgerosa on 2007-03-27
hey ykanello,
don´t be! I know that we are **NOT** restricted to the input port of our sound card...
BUT i can´t help you here. The issue here is that is a lack of info ([COLOR="Black"]easy and helpful one[/COLOR]) about this in Linux world.
So, if anyone can explain how to do this (in a step-by-step) **easy** way, please be welcome to post the experience here, to help us all. THX.

---

### Post by ykanello on 2007-04-04
hehehe, don't take me wrong, I would never use another OS other than linux, and to be more specific, other than a debian derrivative. 

I was just really really frustrated because I am having a radio show, and I am forced to go to friends houses that have windows to do my broadcast every week.
And I think this is a shame :(

---

### Post by jorgerosa on 2007-04-04
OK, ykanello.
Im trying to help you (but, like i said, comunity lacks on info about this, and im just a beginner on this stuff too)

So, maybe you can check this: [http://www.dynebolic.org/](http://www.dynebolic.org/) (Its a specific multimedia Linux distro, All-in-one kind of)
And i think this is what you are looking for: [http://www.dynebolic.org/index.php?show=modules](http://www.dynebolic.org/index.php?show=modules) (search in this page for **Soma Suite**)

They say: **"dyne:bolic is shaped on the needs of media activists, artists and creatives as a practical tool for multimedia production: you can manipulate and [COLOR="Red"]broadcast both sound and video[/COLOR] with tools to record, edit, encode and [COLOR="Red"]stream[/COLOR] "** (...)

If you find usefull multimedia software that works for you in this Linux Dynebolic distro, then try to find the same software for your Ubuntu, in the repositories. Please note that, if your problems are with codecs, the new Ubuntu 7, comes with easy and new useful stuff. Sorry cant help you much more about this. - If this fits you,(or not) post feedback here, ok? thx.


**[COLOR="Red"][COLOR="SeaGreen"]NEW POST: I found now a new post in Ubuntu forums that can also be helpfull:[/COLOR][/COLOR]** [http://ubuntuforums.org/showthread.php?t=34359](http://ubuntuforums.org/showthread.php?t=34359)

---

### Post by ykanello on 2007-05-03
Actually after several tries and failures I made it!!
It actually now works better than the commercial OS's :lolflag: 

I used the ubuntu repositories and installed the internet DJ 
[http://www.onlymeok.nildram.co.uk/]("http://www.onlymeok.nildram.co.uk/")

It works fantastic!
So i stop my nagging :)
Long live gnu/linux!

---

### Post by jorgerosa on 2008-02-10
> **ykanello said:**
> Actually after several tries and failures I made it!!
It actually now works better than the commercial OS's (...) installed the internet DJ [http://www.onlymeok.nildram.co.uk/](http://www.onlymeok.nildram.co.uk/) It works fantastic!
Christ! what ive been missing???... just going to install it right now... :)

EDIT:
[COLOR=Navy]OK, so, you need the **icecast2 server** installed first (see image in the first post)
[/COLOR][COLOR=Navy][B]sudo apt-get install icecast2

.....
[/B][/COLOR][COLOR=Navy] then: [B]sudo apt-get install idjc
[/B]after install, go to: [B]"Applications" --> "Internet" -->"Internet DJ Console"
[/B]and let us know the link for your "Ubuntu Radio Live News" server, ok? post it here! ;)[/COLOR]

---

### Post by ykanello on 2008-02-11
I had issues with IDJC running as user. 
I couldnt set the realtime option on jackd, and the performance was horrible.
As a result I was running everything as root. Niot the best idea, but it worked. Maybe the newer updates have resolved this issue.

---

### Post by ibanez on 2008-02-23
this is good but , IDJC only seems to handle .ogg format for me, any .mp3 it will skip..

Im going to stick with ubuntu even though I could be streaming in 10 mins in windows

---

