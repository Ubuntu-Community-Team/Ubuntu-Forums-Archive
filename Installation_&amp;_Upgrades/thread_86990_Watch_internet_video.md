---
title: "Watch internet video?"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by BLTicklemonster on 2005-11-07
winamp has this thing where you can watch internet tv and stuff. Is there some equivalent thing in ubuntu for like xmms?

---

### Post by parktownprawn on 2005-11-07
there is an xmms plugin (in the multiverse repositories)

xmms-xmmplayer

that uses MPlayer to play video files.

to install ```
sudo apt-get install xmms-xmmplayer
```.

never used it so i don't know how well it works

---

### Post by BLTicklemonster on 2005-11-07
I can watch videos, I mean shoutcast videos over the internet. like music videos. it's like streamtuner, but instead of audio, it's video. Heck, most people I know who have winamp don't know it does this for free.

But thanks for taking the time to answer.

---

### Post by kimabrandt on 2006-06-16
[QUOTE=BLTicklemonster]... I mean shoutcast videos over the internet. like music videos. it's like streamtuner, but instead of audio, it's video. ...[/QUOTE]

Yeah, this is what I want.

Talking about [Streamtuner]("http://www.nongnu.org/streamtuner/")...
I am searching for a plugin like the **SHOUTcast**-plugin which fetches the **radio-stationlist** from [http://www.shoutcast.com/]("http://www.shoutcast.com/").

What I am thinking of is a **SHOUTcast-Video**-plugin which fetches the **video-stationlist** similarly to the radio-plugin.

***1) Does anyone know about such a video-plugin for Streamtuner? Anyone working on it, or who can get me started creating one?***

[Tunapie]("http://tunapie.sourceforge.net/") *works great*, but for me it is more like second-rate quality since it is *not extensible and still under development* (not stable).

I look forward for your responses.


Here is what you can do in your browser (without any program):

a) fetch genrelist/stationlist (save it as xml, don't panic if it's not showing in the browser)

b) find a genre/id you like and use it to fetch the stationlist/playlist (which can be loaded directly by eg. [XMMS]("http://www.xmms.org/"))

```

a) VIDEO
--------
1) stationlist: [www.shoutcast.com/sbin/newtvlister.phtml]("www.shoutcast.com/sbin/newtvlister.phtml")
2) playlist:    www.shoutcast.com/sbin/tunein-tvstation.pls?id=648141

   [playlist]
   numberofentries=1
   File1=http://69.9.180.91:8500;stream.nsv
   Title1=(#1 - 125/200) Lost Season 2
   Length1=-1
   Version=2

b) RADIO
--------
1) genrelist:   [www.shoutcast.com/sbin/newxml.phtml]("www.shoutcast.com/sbin/newxml.phtml")
2) stationlist: www.shoutcast.com/sbin/newxml.phtml?genre=All
3) playlist:    www.shoutcast.com/sbin/tunein-station.pls?id=792933

   [playlist]
   numberofentries=1
   File1=http://207.234.224.189:8000
   Title1=(#1 - 0/251) monkeysuit Radio: monkeysuit Radio
   Length1=-1
   Browser1=http://www.winamp.com/bin/sc/sccontext.php?host=207.234.224.189:8000&title=monkeysuit Radio: monkeysuit Radio&slots=0&genre=Rock Pop 80s 90s&url=http%3A%2F%2Fwww.monkeysuit.ca
   Version=2

```

I also want to know more about ESS.TV, SALTWATERCHIMP.COM and of course any matter which is related to licensing agreements aso.

c ya

---

### Post by BLTicklemonster on 2007-04-08
I can't get tunapie to play any video. Can you elaborate on the second method you mentioned? I've no idea what you mean.

---

