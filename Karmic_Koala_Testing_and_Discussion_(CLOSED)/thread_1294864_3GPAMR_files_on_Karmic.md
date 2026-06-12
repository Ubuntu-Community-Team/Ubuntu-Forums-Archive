---
title: "3GP/AMR files on Karmic"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by snivek on 2009-10-18
How can I configure Karmic to play AMR?  I have tried installing libamrwb3 and libamrnb3, along with mplayer but it still does not work.  I have also tried ffmpeg/ffplay and realplayer.  I have not found a way to play these files.  Thanks!

---

### Post by mc4man on 2009-10-18
> How can I configure Karmic to play AMR?

you need to build or install a player that supports it, none in the karmic repos will.

If the player uses libavcodec to decode then you'll need both a shared libavcodec that's enabled and the player built off  enabled ffmpeg libs. (and the proper amr libs, either the nonfree or opensource

In the case of mplayer you just need an enabled mplayer build and again the libs installed which for karmic may as well be the open source ones (libopencore-amrnb0, libopencore-amrwb0, which **are** available in the karmic repo 

Your easiest solution if you don't wish to build would be a ppa install of mplayer, I'm sure there are some for karmic built with amr support.

I'd be careful of a ppa that has a lot of various  karmic packages, if used don't leave enabled after mplayer install

list of some possibles
[https://launchpad.net/ubuntu/+ppas?name_filter=karmic+mplayer](https://launchpad.net/ubuntu/+ppas?name_filter=karmic+mplayer)

A good, well built mplayer only would be here (supports amr
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
goes with well with smplayer

The only possible downside of the rvm is that it may conflict with any repo app that has a dependency on mplayer-nogui

In karmic the actual mplayer is named mplayer-nogui and the mplayer package is just a gui for it. (gmplayer

The rvm ppa uses mplayer for the name and conflicts (removes) mplayer-nogui

So far I've only seen one app that depends on mplayer-nogui, devede, which if installed will remove the rvm mplayer 

( there are workarounds to that, if there are any other apps I don' know

---

### Post by andrew.46 on 2009-10-19
Hi mc4man,

> **mc4man said:**
> you need to build or install a player that supports it, none in the karmic repos will. 

I would imagine that the Lucid Lynx in April 2010 would have a version of MPlayer compiled against libopencore-amr, this will save a bunch of pain for those not keen on compiling their own.

Andrew

---

### Post by snivek on 2009-10-19
I tried building mplayer after pulling down the libopen_amr packages but the configure did not detect them.  Do you know if I have to do anything special to enable mplayer to see these codecs on my system?

---

### Post by snivek on 2009-10-19
Never mind I discovered that the headers were missing form my include dir.  After pulling down libopencore-amrnb-dev and libopencore-amrwb-dev the headers were there and configure included the codecs.  Thanks!

---

### Post by vinutux on 2009-10-19
Install **[Realplayer 11]("www.real.com/linux")** from official site...

realplayer is the only hope for 3gp/amr without compiling from source............

---

