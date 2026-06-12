---
title: "w32codecs install issue"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by gazza01 on 2010-07-06
Hello , I know I installed some funny stuff trying to get wmv files to work , please assist me to install w32codecs , here is my error I am getting


After this operation, 49.5MB of additional disk space will be used.
(Reading database ... 213209 files and directories currently installed.)
Unpacking w32codecs (from .../w32codecs_1%3a20100303-0.0medibuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/w32codecs_1%3a20100303-0.0medibuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/codecs/wmv8ds32.ax', which is also in package mplayer-codecs-extra 0:20061022-2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/w32codecs_1%3a20100303-0.0medibuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Fire_Chief on 2010-07-06
> trying to overwrite '/usr/lib/codecs/wmv8ds32.ax', which is also in package mplayer-codecs-extra 0:20061022-2

It seems you already have some of the codecs installed through the mplayer-codecs-extra package. You can uninstall this and then install the w32codecs package if you like. I'm not sure right off hand which is preferrable though.

Cheers!

---

### Post by gazza01 on 2010-07-07
i , thank you for your quick response , 
I am mot sure how to remove this , as I can not find it in synaptic. I have tried del it alt-f2 : Naultilus , I scanned it with Klam to make sure it isn't a virus , 

any other advice

---

### Post by Fire_Chief on 2010-07-07
It may show up in Synaptic if you just search for mplayer.

---

### Post by andrew.46 on 2010-07-07
Actually I am a little curious about this one:

```
Unpacking w32codecs (from .../w32codecs_1%3a20100303-0.0medibuntu1_i386.deb) ...
```

I note that Medibuntu calls this a 'new upstream release' but I cannot see such a release on the MPlayer website. Anybody know where this new codec release is coming from?

Andrew

---

### Post by gazza01 on 2010-07-07
Hey , solved I removed the mplaye- extra codecs i managed to install in synaptic the installed w32 codecs, thanx guys for the quick responses.

---

### Post by gazza01 on 2010-07-07
> **Fire_Chief said:**
> It may show up in Synaptic if you just search for mplayer.

You were right , i found it under mplayer other codecs , i removed them and was able to install w32codecs thank you, Solved

---

### Post by andrew.46 on 2010-08-31
Hi,

> **andrew.46 said:**
>  Anybody know where this new codec release is coming from?

Hmmm.... just shows how closely I look at things:

[http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20100303.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20100303.tar.bz2)

Mind you I suspect this is a repackaging and reassembling rather than an assembly of new codecs. Interesting to make a comparison, obviously there is a 7 meg difference for starters with [the previous pack]("http://www.mplayerhq.hu/MPlayer/releases/codecs/all-20071007.tar.bz2")...

Andrew

---

