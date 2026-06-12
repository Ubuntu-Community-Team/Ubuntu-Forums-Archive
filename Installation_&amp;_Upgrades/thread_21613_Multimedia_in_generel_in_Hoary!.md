---
title: "Multimedia in generel in Hoary!"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by madzzoni on 2005-03-23
To the Developers!

On my Dell Latitude D600 Centrino Laptop, Ubuntu Warty works perfect, incl, multimedia as Mplayer, Realplayer, DVD.

Here is my first and second  experience with Hoary Preveiw:
Archieves = main, universe, multiverse, all ubuntu. + marillat (only w32 codecs, flashplyer)

Installation = Fine

Applications:
CD-player = Fine.

Totem-gstreamer = Start up and then freeze.
- then replace to Totem-Xine and it plays DVDs, but there is no working plugin for Firefox.

Mplayer (Ubuntu-versions) = NOT Working with mplayerplug-in for streaming video/audio ([www.apple.com/trailers)](www.apple.com/trailers)). tried Mplayer-386 + 585 + mplayer-custum (Most pick-up *libavcodec2* from warty!) 

VLC = Plays DVD fine but the mozilla-plugin isn't reconized, when visiting websites with Streaming video. (message: no plugin found)

Xine = Fine, Play DVDs, but no useful browser-plugin found.

RealPlayer = Not working! tried RealPlayer10GOLD.bin + HXplayer.bin + realplay-10*.bin (from ubuntuguide.org)
- Shows up in the menu, but will not launch! Browser-plugin added, but can launch player.

How can it be, i got all this trouble with Hoary, when theres allmost none with warty?

Is it a issue about user-rights?

I was looking very much forward to Hoary, but think i will wait until the Final Hoary, to use it on my Laptop. 

A hopefull Ubuntu-user!

---

### Post by titus1950 on 2005-04-09
I have the same problems ,plus Xine is jerky playing DVD,so I have to use (hdparm) to enable DMA.
PLEASE DEVELOPERS DEVELOP  MULTIMEDIA,To be able to enjoy this great O.S.in it's full capacity

Thank you.

---

### Post by Omnios on 2005-04-15
real player requires a few files to be cut and paited plus a sybolic link for realplay script in your path as on moz web site I just havent figured it out yet as a matter of fact I havent found the firefox file yet lol.

---

### Post by Stormy Eyes on 2005-04-15
[QUOTE=titus1950]I have the same problems ,plus Xine is jerky playing DVD,so I have to use (hdparm) to enable DMA.
PLEASE DEVELOPERS DEVELOP  MULTIMEDIA,To be able to enjoy this great O.S.in it's full capacity

Thank you.[/QUOTE]

It's not the developers' fault that DVD playback is jerky if you don't enable DMA on your drive. Data transfer without DMA just isn't fast enough; that's the nature of the beast. Also, Ubuntu doesn't enable DMA on optical drives by default, due to the possibility of borking the system by enabling DMA on a drive that doesn't support it.

---

### Post by jmather on 2005-04-15
Has anyone solved the realplayer issue yet?  I have the same problem....

JM

---

### Post by jmather on 2005-04-15
I found the answer for me in this thread:

[http://www.ubuntuforums.org/showthread.php?t=24331&page=2&pp=10&highlight=realplayer](http://www.ubuntuforums.org/showthread.php?t=24331&page=2&pp=10&highlight=realplayer)

Turning off the sound server did it....

---

### Post by sic on 2005-04-15
I have been having trouble with Real player as well...I get the following error when attempting to view video streams:

Unsupported document type. (file:///tmp/x6it0ki9.ra)

I am running the latest version of RealPlayer on warty.

Any help is much appreciated!

---

### Post by wolovids on 2005-04-15
Yeah, I turned off the sound server too and it does work.  However, Realplayer 10 likes to take over the entire sound device.  So, attempting to have sound in another application simultaneously does not work.  This happens even when I disable/remove esound and use dmix (which works really well BTW).  

The problem is Realplayer, apparently.  It just doesn't have sound server support 100% working yet.  Hopefully, they will have the next versions up to par.

---

