---
title: "maverick gmplayer missing"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by TheSqueak on 2010-10-11
So, i've just upgraded from lucid to maverick, and it appears that the mplayer version shipped is shipped without the gui compiled in.

Does anyone know where I can get the mplayer-gui package for maverick x86?


Aside from that, everything went brilliantly, and the upgrade caused me to be offline for 5 minutes in total :)

---

### Post by andrew.46 on 2010-10-11
Hi thesqueak,

The default gui for MPlayer is slowly being cut loose by the MPlayer developers, you might do better by installing SMPlayer:

```

sudo apt-get install smplayer smplayer-themes qt4-qtconfig

```

All the best,

Andrew

---

### Post by jimmycourge on 2011-02-12
SMPlayer only plays **one video at a time** which is a major difference - actually a design flaw since my hardware and pretty much everyone else's is capable of showing more than one when not using crippled software.
In contrast mplayer gui will play as many videos as you have the hardware for also the UI doesn't compare to gmplayer IMHO. It's unresponsive even though it only has one window to keep track of. 

The only reason I can see to use SMplayer is when gmplayer is down. Ever used OS X and Quicktime? It has had multi video capability for years and also makes SMplayer look sad in comparison. Apple seems to set the standard here in pay operating systems, why would anyone want to go from a multi video capability to a single video capability and significantly less responsive UI???

---

### Post by andrew.46 on 2011-04-25
Oddly enough it looks like the old GMPlayer has been receiving a liitle attention from a new MPlayer developer. It will be very interesting to see if it roars into life again :).

---

### Post by SeijiSensei on 2011-04-25
Well, for those of us who watch only one show at a time so we can concentrate on what's happening, smplayer is a fine choice.  I suppose I can see professional reasons to play simultaneous streams, but I don't see that as a feature that the vast majority of people are going to care about.

If you really need to display multiple videos simultaneously, just run multiple instances of mplayer in the background from the command prompt:

```

mplayer /path/to/file1.mkv &
mplayer /path/to/file2.mkv &
[etc.]

```

---

