---
title: "Replace Totem with VLC 1.0 in Karmic?"
date: 2009-05-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-05-19
Hi folks,
Now that VLC 1.0 is soon out and is so much better than Totem (in my case including startup time) - are we going to continue shipping Totem by default and continue calling its win95 interface and lack of medium and advanced features the virtues that a default media player must have?

Or is it something else like maybe some licensing issue?

---

### Post by super.rad on 2009-05-19
Don't think totem will ever be replaced on ubuntu, and if it was I dont think it would be with VLC as that would mean having to fit QT on the CD aswell

---

### Post by binbash on 2009-05-19
It will not happen.

---

### Post by Starks on 2009-05-19
Totem needs to implement the gstassrender plugin that overhauls its subtitle renderer

---

### Post by binbash on 2009-05-19
There is also a bug totem that you can not add a .sub subtitle, i guess it should be fixed first

---

### Post by kerry_s on 2009-05-19
i would rather see gnome-mplayer+gecko-mediaplayer, it works far better than both totem and vlc.
plus with vlc moving to qt4 it would be a huge install for the gnome gtk2 based system.

---

### Post by cl333r on 2009-05-19
mplayer imo would do fine too.
I raised this question also because the users mostly come from windows, and there they have windows media player 11 or 12 by default with a gorgeous/professional interface and when they look into Ubuntu they feel like traveling in time to the stone age when the see the totem interface and it's features. And when they ask me why is it the default player and why is it so *******, well, I mostly say that the Linux crowd likes what is dead simple, but I know it's a lame excuse, at least for the windows newcomers.

---

### Post by Swarms on 2009-05-19
> **cl333r said:**
> mplayer imo would do fine too.
I raised this question also because the users mostly come from windows, and there they have windows media player 11 or 12 by default with a gorgeous/professional interface and when they look into Ubuntu they feel like traveling in time to the stone age when the see the totem interface and it's features. And when they ask me why is it the default player and why is it so *******, well, I mostly say that the Linux crowd likes what is dead simple, but I know it's a lame excuse, at least for the windows newcomers.

Is there an app that is on par with VLC and uses GTK?

---

### Post by super.rad on 2009-05-19
I would prefer to have gnome-mplayer installed by default but doubt it'll happen.
Totem doesn't look that bad and don't think I've ever had a problem with it though

---

### Post by super.rad on 2009-05-19
> **Swarms said:**
> Is there an app that is on par with VLC and uses GTK?
Mplayer with a GTK front end (gnome-mplayer being my favourite)

---

### Post by Starks on 2009-05-19
gnome-mplayer is incredibly bare.

SMPlayer is the way to go.

---

### Post by Gourgi on 2009-05-19
> **super.rad said:**
> 
Totem doesn't look that bad and don't think I've ever had a problem with it though
+1 here
only if totem had a 'choose color' dialog for the displaying subs.
i like yellow more than white in the subs.

---

### Post by DLG102282 on 2009-05-19
+1 I think gecko-mediaplayer is the way to go. I always uninstall totem and install it anyway because totem is a joke.

---

### Post by kj74 on 2009-05-19
No, vlc is crap.

---

### Post by SuperSonic4 on 2009-05-19
> **Starks said:**
> gnome-mplayer is incredibly bare.

SMPlayer is the way to go.

SMplayer is a QT interface to mplayer so it would also require the QT libs that VLC does

---

### Post by syko21 on 2009-05-19
> **DLG102282 said:**
> +1 I think gecko-mediaplayer is the way to go. I always uninstall totem and install it anyway because totem is a joke.

gecko-mediaplayer is a web browser plugin, not a standalone media player.

---

### Post by super.rad on 2009-05-19
> **Starks said:**
> gnome-mplayer is incredibly bare.

SMPlayer is the way to go.

I agree SMPlayer is a lot better but again it would need QT.
Does anyone know a good GTK front end for mplayer which is as full featured as SMPlayer?

---

### Post by miwaypet on 2009-05-19
I am for the gecko-mediaplayer/gnome-mplayer combo. Works great. Allows pre-caching. Can choose your audio. Only one that works with Opera browser.

---

### Post by BwackNinja on 2009-05-19
Totem stays, integrated too well. Totem-video-thumbnailer, uses gstreamer, etc. I'm sure it fits better on the cd than any other video player could. Plus it has some nice plugins like the youtube plugin. It does most of what you need it to do, but there's a list of things just as "to do." I personally use SMPlayer and find it best for my needs and like it better than VLC, but there are some of the usual characters that always come to play. VLC can do 5.1 audio into pulseaudio now, which is nice and something MPlayer has been able to do, but VLC has dvd menus working wonderfully - in MPlayer it works (if you build it right of get it from the right source) but it currently just has a transparent square to highlight where you have selected not a big deal, but "could be better." Otherwise, their media playback is pretty much the same - everything.

---

### Post by Starks on 2009-05-19
Totem needs A.S.S. subtitle rendering, nuff said.

---

### Post by Nullack on 2009-05-19
Your all dreaming in a fantasy world where software patents dont exist :)

The reason Windows 7 and the like have so many demuxers and decoders is because you pay for the software, and some of that money goes to patent pool holders who hold the rights for the media technology. It is licensed for use.

What the FOSS community did was reverse engineer these technologies without licence which in most developed countries is illegal.

If Canonical did something like this, they'd be bankrupted in court.

---

### Post by zekopeko on 2009-05-19
> **Starks said:**
> Totem needs A.S.S. subtitle rendering, nuff said.

anime junkie :P

---

### Post by Reiger on 2009-05-20
> Your all dreaming in a fantasy world where software patents dont exist
And some of us don't live in the US, but rather in some place ideas are not and only implementations are patentable. :P

---

### Post by Nullack on 2009-05-20
The Berne convention ensures most developed countries adhere to IP protection.

---

### Post by Reiger on 2009-05-20
Ah but software falls in the category literary works in the Berne convention. ... Not patentable.

---

### Post by Nullack on 2009-05-20
So United Kingdom, USA, Canadian and Australian software patents dont exist??? Id like to think that, but I know that claim to be untrue :)

---

### Post by Merk42 on 2009-05-20
> **Reiger said:**
> And some of us don't live in the US, but rather in some place ideas are not and only implementations are patentable. :P

But Ubuntu is available in the US and therefore has to follow its rules.

*See: no mp3 codec installed by default*

---

### Post by Reiger on 2009-05-20
> **Merk42 said:**
> But Ubuntu is available in the US and therefore has to follow its rules.

*See: no mp3 codec installed by default*

For shipping to the US, yes. Incidentally there's another very similar problem with encryption: US being somewhat more restrictive in what you are allowed to ship/export [outdated encryption methods] and what not [cryptographically secure methods]. 

And yes there are patents outside the little fantasy world of the EU. ;) However strictly speaking Canonical is allowed more than they take advantage of; but there is of course the question: _should_ they take advantage of _everything_ they are allowed? 

Anyways I think this dicussion has gone OT enough.

---

### Post by JohnJackson on 2009-05-26
[http://www2.apebox.org/wordpress/linux/105/]("http://www2.apebox.org/wordpress/linux/105/")

> Totem will remain default “file” player in Karmic.

---

### Post by ghindo on 2009-05-26
No surprises here.

---

### Post by 23meg on 2009-05-26
This is not going to happen, for the obvious reasons cited here and elsewhere many times, so no use in wasting time discussing it any further.

---

