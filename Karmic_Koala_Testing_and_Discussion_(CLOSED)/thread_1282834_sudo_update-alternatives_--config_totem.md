---
title: "sudo update-alternatives --config totem"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-10-04
This no longer works for me in Karmic.

I have installed totem-xine but it won't launch from a terminal, and does not show up when trying to make it the default as above.

What am I doing wrong here?

---

### Post by FuturePilot on 2009-10-04
totem-xine has been deprecated from what I've heard. The totem-xine package is just a dummy package now.

---

### Post by mc4man on 2009-10-04
Hopefully for totem users there will be a decent functioning totem in place by release.
It works here to some extent, though some things with dvd playback are borked ( playlist area is wrong, doesn't detect/show additional audio streams in 'sound' and no substreams in 'view'

It is possible now and barring any significant change to totem-common, to build and replace the existing transitional totem-xine package with a functional one. 
Atm it works quite fine

( I have found that the current totem works well with local files (excluding dvd video in file or .iso form
And the user-agent patch  for quicktime works well also (apple trailers for instance

---

### Post by crjackson on 2009-10-04
> **FuturePilot said:**
> totem-xine has been deprecated from what I've heard. The totem-xine package is just a dummy package now.

Dammit! It works so sweet with the remote control for my laptop. I don't think I can live without that.  I may be forced to drop back to Hardy, since Jaunty won't work on my Intel Video Powered laptop.

---

### Post by crjackson on 2009-10-04
> **mc4man said:**
> Hopefully for totem users there will be a decent functioning totem in place by release.
It works here to some extent, though some things with dvd playback are borked ( playlist area is wrong, doesn't detect/show additional audio streams in 'sound' and no substreams in 'view'

It is possible now and barring any significant change to totem-common, to build and replace the existing transitional totem-xine package with a functional one. 
Atm it works quite fine

( I have found that the current totem works well with local files (excluding dvd video in file or .iso form
And the user-agent patch  for quicktime works well also (apple trailers for instance

would you be willing to post a HOWTO for me?  I love totem-xine and it may be a deal breaker if I can't have it.

---

### Post by mc4man on 2009-10-06
I think that may  be a bit premature, though I'd point you in right direction if you wish.

To maybe clarify some things first

Running totem-xine in 9.04 would depend on the continued compatibility of totem-common 2.28.X with the 2.26.X totem-xine and that is not a given.

Totem-xine in 9.10 can't be set as the 'default' totem, nor is there any reason to do so, it would only reduce functionality, not improve

For the most part totem 2.28 works well, though some things still need fixing and improvement ( whether that's achieved remains to be seen

The use of totem-xine in 9.10 would only be as an alternate player for local files and dvd media and there are as good or better players available

The one thing totem-xine does have on other dvd media players is that it uses it's own dvdnav version which can work with some structured protected titles that dvdnav4 fails on ( fairly rare

It also plays more formats than the current totem will, (and some other players) due to it's full use of libxine1-ffmpeg and w32codecs

so let me know if you want to try  ( at some point you'll need to move on to other media players

---

### Post by mdurham on 2009-10-06
My wife is a teacher and needs to do lots of fast forward/reverse(ing) of film clips. Totem doesn't like this, it turns grey and locks up a lot. Totem-xine works fine, so we obviously need the xine version or another player that doesn't lock up when the position button is dragged rapidly back and forth. Any ideas?
Cheers, Mike

---

### Post by mc4man on 2009-10-07
> another player that doesn't...
Why don't you give vlc or mplayer with a smplayer frontend a try.

As far as mplayer/smplayer you could go with the repo versions or add the 2 ppa's ( smplayer and the rvm mplayer ppa


edit: also noticed that kaffeine seems to also work well and like totem-xine uses it's own dvdnav (Using dvdnav version 1.1.16.3 from [http://xine.sf.net](http://xine.sf.net)



I don't normally suggest adding ppa's to your sources but these 2 are very well done and actively supported by the developer on these forums. ( if you have an issue with smplayer just start a thread - smplayer blah, blah and you should get help fairly soon.

main info page
[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

smplayer ppa
[http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

the add. mplayer ppa
 [https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

If unsure how to add a ppa(s), please ask first

---

