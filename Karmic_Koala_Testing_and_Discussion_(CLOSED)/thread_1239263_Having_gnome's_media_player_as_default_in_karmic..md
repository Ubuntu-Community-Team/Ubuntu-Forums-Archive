---
title: "Having gnome's media player as default in karmic."
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-08-13
Hi

I find the gnome mplayer much much better than totem,why cant we have that as default in karmic.It uses the mplayer backend.What i like about it is that its much simpler and less cluttered than mplayer itself.

Its really nice,i used it throughout in 9.04 and generally found it much better.

Please give your thoughts on this.

---

### Post by hysteresis on 2009-08-13
I like totem better because avi videos I make with acidrip do not play properly in gnome mplayer. The audio is out of sync and the video will not expand to full screen.

---

### Post by taavikko on 2009-08-13
totem offers far more, than just a movie player.
integration with browser and internet's multimedia content...

mplayer isn't developed as extensively as totem on whole.
AFAIK some mplayer source code is closed? if that's true, it will never be default in ubuntu.

Put it in brainstorm, so one day this might be real.
For now it's a little too late for karmic.

---

### Post by rajeev1204 on 2009-08-13
> **taavikko said:**
> totem offers far more, than just a movie player.
integration with browser and internet's multimedia content...

mplayer isn't developed as extensively as totem on whole.
AFAIK some mplayer source code is closed? if that's true, it will never be default in ubuntu.

Put it in brainstorm, so one day this might be real.
For now it's a little too late for karmic.

Mplayer played videos inside a browser much better than totem ever did.Now of course totem(since hardy) is on par or better maybe.But remember during dapper,it was mplayer who sailed through all those media codecs.

What do you mean it isnt developed as extensively? Its gnome default , so i believe all applications in gnome get equal treatment.Mplayer can play almost everything you throw at it like vlc does,so i dont understand this point.

But yes,its a little late for karmic now i guess.See you in karmic +1 :)

---

### Post by ronaldprettyman on 2009-08-13
> **rajeev1204 said:**
> Hi

I find the gnome mplayer much much better than totem,why cant we have that as default in karmic.It uses the mplayer backend.What i like about it is that its much simpler and less cluttered than mplayer itself.

Its really nice,i used it throughout in 9.04 and generally found it much better.

Please give your thoughts on this.

Totem downloads the codecs easier imo

---

### Post by Mr. Picklesworth on 2009-08-13
Mplayer doesn't use GStreamer (naturally). Therefore, you:

* Lose auto codec install
* Have a default program with completely different compatibility details than the others
* Lose GStreamer's centralized preferences

---

### Post by slakkie on 2009-08-13
I only use mplayer or vlc. I don't use any other media player.

As for mplayer, I think it is older then totem, but not sure.

Regarding the auto-download, there is a point, but you can download them easily of mplayer's website: [http://www.mplayerhq.hu/design7/dload.html#binary_codecs](http://www.mplayerhq.hu/design7/dload.html#binary_codecs). I think it can be easily scripted to fetch them or the codecs can be packaged, making it even simpler.

This not a subject I'm worried about, since I will override the defaults straight away (and not using gnome, so totem is not my default mediaplayer to begin with).

---

### Post by Starks on 2009-08-13
I will never will use Totem so long as it can't use advanced subtitle formats that every other player can handle.

---

### Post by dentaku65 on 2009-08-13
I'm using mediaplayer only for internet streaming with gecko-mediaplayer (removing totem-mozilla) because rocks.
For the local video viewing I'm using kaffeine (has dvb-t too); evenf if kaffeine is for KDE I don't have any problem to use under Gnome.

---

### Post by zekopeko on 2009-08-13
> **Starks said:**
> I will never will use Totem so long as it can't use advanced subtitle formats that every other player can handle.

That has nothing to do with Totem. Blame Gstreamer.

---

### Post by Starks on 2009-08-14
I blame Totem and its lack of implementation because gstreamer already has the requisite code. I had personally made sure of that.

---

### Post by jocko on 2009-08-14
> **taavikko said:**
> totem offers far more, than just a movie player.
integration with browser and internet's multimedia content...
So does mplayer and vlc, and both does it much better than totem (in my experience). You just need to install mozilla-mplayer or mozilla-plugin-vlc (and get rid of totem-mozilla).
> **taavikko said:**
> mplayer isn't developed as extensively as totem on whole.Where do you get that idea from? New versions may not be released as often as new versions of totem, but development is still active. It's just not tied to any other release cycle (like totem is to the rest of gnome), so new versions are released when they need to be. You can still use development versions of mplayer and update it regularly from the svn repo...
> **taavikko said:**
> AFAIK some mplayer source code is closed? if that's true, it will never be default in ubuntu.[mplayer is open source (gpl 2)]("http://www.mplayerhq.hu/design7/info.html").

---

### Post by jocko on 2009-08-14
> **ronaldprettyman said:**
> Totem downloads the codecs easier imo
mplayer and vlc already have all codecs. But I guess if any of them would make it into the main repos, they would have to be stripped down to leave out dvd support and some other codecs that may be illegal in the US. But if it's possible to have add/remove open up and search for the codecs whenever totem encounters a missing codec, it should be possible to do the same if mplayer or vlc is missing a codec... So this point is pointless.

Totem and gstreamer just don't have any usable configuration options.
Both mplayer and vlc can be configured to play videos on another display than the one you start the program from (nice if you want to see movies on your tv and use a dual screen or twinview setup).
Both mplayer and vlc can be set to pass through dolby or dts directly to an external surround reciever instead of decoding it (there's an option in totem for this, but it has never worked for me in the four years I've been using Ubuntu).
vlc has an equalizer (mplayer too, but at least mine doesn't work), I haven't seen any gstreamer equalizer anywhere.
And: As mplayer and vlc are stand-alone applications I can configure them individually the way I want them, with totem you will affect all other gstreamer applications which is not always desirable.

---

