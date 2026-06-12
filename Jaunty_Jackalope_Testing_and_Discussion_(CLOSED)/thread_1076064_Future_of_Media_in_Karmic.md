---
title: "Future of Media in Karmic"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2009-02-20
Rhythmbox, my favourite	Music player, is dying.
Jonathan Matthew said on the **[Rhythmbox mailinglist]("http://mail.gnome.org/archives/rhythmbox-devel/2009-February/msg00023.html")**, on Monday:
> I hope to be able to make a new release in the next month or so.  This
will probably be numbered 0.12.0.  After that, I'm not planning to do
much new development work on the rhythmbox project as it currently
exists.  I'll still fix (some) bugs and review patches, but it's too
much of a dead end for me to do more than that.
Why?
> ... the underlying data model is too rigid
and limited:
- the set of query-able entry properties is fixed
- entry properties can't have multiple values
- albums don't exist, they're synthesized from whatever
  entries happen to match the album name
- file metadata, observed user data (play count, etc.), and user provided data
  (ratings) are all stored together when they'd be more useful separate
- the database is designed specifically to support implementation of the
  genre->artist->album browser and doesn't work so well for other
  things.
- it doesn't always make sense that sources are completely distinct from
  each other

These things are pretty much baked into every aspect of rhythmbox.
Rhythmbox is fine for what it is, but I don't think I can make it into
what I want it to be.

I'm sad to hear this ... 
But while Rhythmbox's core innovation slows, most new functionality coming in the form of plugins, Banshee development forges on ahead. 

I've said before that I think Rhythmbox is superior at the moment, that Banshee was quickly bridging that feature gap: 
So I don't know if Rhythmbox will be able to compete with Banshee (or any other player) in six months to a year if no one picks up the project.

It's been suggested for a while that Banshee be made default, perhaps now is the time.

Discuss

Edit: I should have said, I would likely remove Banshee if it were default, install Rhythmbox myself ... but would probably support the decision. See it from the point of new users, etc.

---

### Post by ronacc on 2009-02-20
I have never been a fan of rythymbox , I usualy use banshee or BMP , but with that said I am always sad to see a project die , diversity strengthens all .

---

### Post by Nullack on 2009-02-21
Yep, by being objective to the applications weaknesses improvements will come with diversity.

---

### Post by olskar on 2009-02-21
> **mc4100 said:**
> Rhythmbox, my favourite	Music player, is dying.
Jonathan Matthew said on the **[Rhythmbox mailinglist]("http://mail.gnome.org/archives/rhythmbox-devel/2009-February/msg00023.html")**, on Monday:

Why?


I'm sad to hear this ... 
But while Rhythmbox's core innovation slows, most new functionality coming in the form of plugins, Banshee development forges on ahead. 

I've said before that I think Rhythmbox is superior at the moment, that Banshee was quickly bridging that feature gap: 
So I don't know if Rhythmbox will be able to compete with Banshee (or any other player) in six months to a year if no one picks up the project.

It's been suggested for a while that Banshee be made default, perhaps now is the time.

Discuss

Edit: I should have said, I would likely remove Banshee if it were default, install Rhythmbox myself ... but would probably support the decision. See it from the point of new users, etc.

I have had a feeling about that for a time..

I guess this would be more then reason enough to have Banshee instead (or something else, I haven't tried a lot. But looking on the forum the choice seems to be between Banshee and Rhythmbox)

---

### Post by tgpraveen on 2009-02-21
although i too liked rythmbox as the default but always felt it was not developed well adn looked ugly and was too simplistic taht it doesnt make a good impression on users being the default player /

banshee is under active development and the plugin model is good. so it would be good to make it default in 9.10. it would make a good impression for new users on the power of oss.

---

### Post by kaivalagi on 2009-02-21
I too use Rhythmbox, I like the fact it is written in python. I have written python tools for it and like the dbus interface. For me it does the job right now.

If it is soon to be dead in the water I would like to see another python/gtk based player take over rather than one based on mono...what about further development of exaile? 

Or maybe someone should right a feature rich front end for xmms2....xmms2 has enough plugins for everything you could want and is light on resources. It is easily developed against too...

Admittedly I want a music player rather than something that handles all media though. I prefer using alternative apps for video etc so just need a decent music player.

---

### Post by zekopeko on 2009-02-21
> **kaivalagi said:**
> 

If it is soon to be dead in the water I would like to see another python/gtk based player take over rather than one based on mono...what about further development of exaile? 


please don't be one of those "I hate mono" people that scream microsoft technology but have no idea at all.

---

### Post by directhex on 2009-02-21
Banshee has a very fat dependency tree - it would need a bunch of fiddling to fit onto the CD in a rational manner

---

### Post by olskar on 2009-02-21
> **directhex said:**
> Banshee has a very fat dependency tree - it would need a bunch of fiddling to fit onto the CD in a rational manner

And I guess going over to DVD isn't topical this time around either :)


EDIT:

Installing rhythmbox gets 3396kB of packages and installing banshee including dependencies (banshee, libboo2.0-cil, libmono-zeroconf1.0-cil, libtaglib2.0-cil, podsleuth) gets 3686kB

Not a lot difference, or have I done something wrong?

---

### Post by directhex on 2009-02-21
> **olskar said:**
> And I guess going over to DVD isn't topical this time around either :)


EDIT:

Installing rhythmbox gets 3396kB of packages and installing banshee including dependencies (banshee, libboo2.0-cil, libmono-zeroconf1.0-cil, libtaglib2.0-cil, podsleuth) gets 3686kB

Not a lot difference, or have I done something wrong?

You likely already have a bunch of Banshee's deps installed - e.g. assorted gstreamer-foo packages

---

### Post by kaivalagi on 2009-02-21
> **zekopeko said:**
> please don't be one of those "I hate mono" people that scream microsoft technology but have no idea at all.

I won't be, don't get me wrong, I am a developer by trade and mostly write .net code professionally. I don't hate Microsoft, I don't love Linux....but I do like Linux a lot and wish I could find a decent development job working with Python, but in my neck of the woods that's not going to happen easily.

As much as I think mono is good for Linux, Python is more suited IMHO. There are more easily accessible libraries for Python and as such better plugin development is achievable by novice and expert.

[COLOR="Navy"]Edit: just tried v.1.4.2 of Banshee, and it's okay...I prefer Rhythmbox :)
Banshee gripe: The app thinks it's a good idea to download all the cover art for all my music library in one go..all 7000+ mp3's of it. What's wrong with downloading as and when necessary
[/COLOR]

---

### Post by glasen on 2009-02-21
> **directhex said:**
> You likely already have a bunch of Banshee's deps installed - e.g. assorted gstreamer-foo packages

Which are also needed for Rhythmbox.

---

### Post by Mazza558 on 2009-02-21
The mono argument doesn't really work any more, because (IIRC) F-spot also uses mono and that comes built-in anyway.

---

### Post by olskar on 2009-02-21
> **Mazza558 said:**
> The mono argument doesn't really work any more, because (IIRC) F-spot also uses mono and that comes built-in anyway.

Tomboy also, I think?

---

### Post by steeleyuk on 2009-02-21
> **kaivalagi said:**
> I too use Rhythmbox, I like the fact it is written in python. I have written python tools for it and like the dbus interface. For me it does the job right now.

If it is soon to be dead in the water I would like to see another python/gtk based player take over rather than one based on mono...what about further development of exaile? 

Or maybe someone should right a feature rich front end for xmms2....xmms2 has enough plugins for everything you could want and is light on resources. It is easily developed against too...

Admittedly I want a music player rather than something that handles all media though. I prefer using alternative apps for video etc so just need a decent music player.

Rhythmbox is written in C. Some of the plugins might be in Python but the actual app itself is definitely C.

Exaile, Quod Libet and Listen (no longer regularly developed) are all written in Python and GTK.

I agree with you about the player just handling music though. Thats one thing that bothers me about Banshee, it breaks the UNIX way of do one thing and do it well. For me Totem handles all video, for others its VLC or Mplayer.

---

### Post by Merk42 on 2009-02-21
What's Songbird written in? That player seems to have come a long way in a short time.

---

### Post by fut21 on 2009-02-21
> **steeleyuk said:**
> 
Exaile, Quod Libet and Listen (no longer regularly developed) are all written in Python and GTK.


Exaile are still in develoment:
[http://www.exaile.org/](http://www.exaile.org/)
[https://launchpad.net/~exaile-devel](https://launchpad.net/~exaile-devel)

---

### Post by UbuWu on 2009-02-21
> **steeleyuk said:**
> Listen (no longer regularly developed) 

Looking at the trac timeline, it seems that 0.6 will be released soon... :-)

---

### Post by steeleyuk on 2009-02-21
> **fut21 said:**
> Exaile are still in develoment:
[http://www.exaile.org/](http://www.exaile.org/)
[https://launchpad.net/~exaile-devel](https://launchpad.net/~exaile-devel)

I know Exaile is still in development, I never said it wasn't. I said Listen wasn't being regularly developed. Though there have been a few patches and updates recently which is good to know.

---

### Post by kaivalagi on 2009-02-21
> **steeleyuk said:**
> Rhythmbox is written in C. Some of the plugins might be in Python but the actual app itself is definitely C.

Exaile, Quod Libet and Listen (no longer regularly developed) are all written in Python and GTK.

I agree with you about the player just handling music though. Thats one thing that bothers me about Banshee, it breaks the UNIX way of do one thing and do it well. For me Totem handles all video, for others its VLC or Mplayer.

Yeah you're right, I guess what I mean is Python friendly and python extendible. The point I am trying to make is that plugin development in python lends itself more to Linux with a large range of libraries available to do all sorts of stuff simply. Mono is okay but I don't think there is quite the library support found there...(maybe I'm wrong?)

I like exaile (not as much as rb), it's a player just for music and has quite a range of plugins. And it is written in Python :)

I spent some time using xmms2, the music daemon, and used esperanza (qt based :( ) for the front end. It was okay, good on resources etc. If only a really nice front end was created for that.

[COLOR="Green"]Voted to keep Rhythmbox, it works and I don't see any reason to ditch it...if it has to go I will probably use exaile.[/COLOR]

---

### Post by mc4100 on 2009-02-21
Added Poll. :)

---

### Post by tretle on 2009-02-21
Maybe you should update the post with the news that rhythmbox development is to cease with the release of 0.12.0.

---

### Post by directhex on 2009-02-21
> **Merk42 said:**
> What's Songbird written in? That player seems to have come a long way in a short time.

Songbird is written in... Well, that's hard to specify. Essentially, it's written in "Xul", the same language as Thunderbird and Firefox. The underlying Xulrunner engine is C++. Songbird also leverages GStreamer (C)

---

### Post by zekopeko on 2009-02-21
i think you can rule out songbird. it's just too big. they use patched xulrunner thats not compatible with the one firefox uses so thats just too much space used. banshee would be a far better candidate.

---

### Post by wedderburn on 2009-02-21
the other thing with Songbird is it doesn't have very good gtk integration by default.

if Rhythmbox is slowing down in its development then banshee is the way to go, don't get caught up in what its written in, to the end user its meaning less.

the thing with banshee is if the plugins from totem get ported over(dvb, youtube, bbc) we may be able to remove that too since banshee can do video as well as audio.

---

### Post by karlmp on 2009-02-21
listen has too many bugs right now but if the developers hurry up, then it would be great to have it by default

---

### Post by tawmas on 2009-02-22
I guess we'll get Banshee by default in a release or two.

Which is not that bad -- in fact it's shaping up quite well -- but right now has got a couple of showstoppers.

First it doesn't support gapless playback, which is awful for listeners of Classical music (and I guess other genres with which I'm not familiar).

Second, the initial collection indexing is way too much CPU intensive, and I didn't find a way to add music I have on disk without reindexing the whole collection, and risking to burn my CPU in the process...

Ah... I guess music players is one of the fields that need a lot of love!

---

### Post by tgpraveen on 2009-02-22
> **tawmas said:**
> I guess we'll get Banshee by default in a release or two.


Ah... I guess music players is one of the fields that need a lot of love!

+1 on both those points

---

### Post by SKLP on 2009-02-22
IMO, Banshee has been better since the 1.0 release, so I'd welcome this change :)
The mono argument is just silly: mono implements an open standard (CLI and C#...) just like gcc implements an open standard (C, C++). Just because Microsoft was the original author doesn't mean Mono is evil. Both mono and gcc are freely available...

---

### Post by Phreaker on 2009-02-22
Another vote for Banshee

I never liked Rhytmbox

---

### Post by tgpraveen on 2009-02-22
> **phreaker said:**
> another vote for banshee

i never liked rhytmbox

+1

---

### Post by uBeer on 2009-02-22
I like Rhythmbox over Banshee for it's performance, but the plugin structure of Banshee is indeed awesome.

The interface of Banshee is nice, but a little less responsive than Rhythmbox, but since the 1.4 series it ain't that bad, but there is still room left for improvement.

And Rhythmbox is still better in album artwork/information, hope that they work that magic from Rhythmbox to Banshee!

---

### Post by steeleyuk on 2009-02-22
I've just installed Banshee. Its better than it used to be except for one thing, why won't it import my MKV files? (MPEG video with Theora audio).

---

### Post by RAOF on 2009-02-22
> **steeleyuk said:**
> I've just installed Banshee. Its better than it used to be except for one thing, why won't it import my MKV files? (MPEG video with Theora audio).

Probably a taglib bug.  Banshee uses taglib# to read out the metadata from files, and won't import them unless taglib supports them.

It could, perhaps, do with a gstreamer fallback path.  It used to read metadata from gstreamer, but taglib was some ten times faster or so.

---

### Post by MadsRH on 2009-02-22
I've always loved Rythymbox, but it seems Banshee is evolving where Rythymbox is mostly bugfixing.

Also, Banshee just looks more slick ;-)


+1 for Banshee

---

### Post by Triggerhapp on 2009-02-22
gmpc + mpd, this setup is so much better than anything before :)

---

### Post by Maduroutmb on 2009-02-22
I greatly prefer exaile, since it supports a variety of music organization schemes.  I also like the plugin availability (alarm clock, etc.).  The 0.3 release is supposed to be great, though I see the absence of support for video as a drawback.

Is the goal a unified ripping/burning/decoding/encoding application for both audio and video, or is that so far in the future as to have no effect on current decisions?  I ask because that question really informs the decision between Exaile and Banshee for me.

---

### Post by kyleabaker on 2009-02-23
I'm open to using banshee. Exaile was just terrible the last time I gave it a try. Rhythmbox is my main audio player for now though and I'm sad to see it getting phased out. I love the simple player and it's never had a problem with interacting with my ipod.

---

### Post by directhex on 2009-02-23
Rhythmbox never sat comfortably for me - Banshee's much closer the mark despite the similarities.

However, it's sad to see a loss of upstream interest in such a popular project. I hope someone competent takes over & gives it some TLC

---

### Post by kyleabaker on 2009-02-23
> **directhex said:**
> i hope someone competent takes over & gives it some tlc

+1

---

### Post by ace214 on 2009-02-23
I like Banshee, but I don't think I can make the permanent move until it supports browsing by genre.

I currently use Quodlibet, but am open to using Rhythmbox. I will always use ExFalso for tagging though, until someone creates something just as good.

---

### Post by directhex on 2009-02-23
> **ace214 said:**
> I like Banshee, but I don't think I can make the permanent move until it supports browsing by genre.

I currently use Quodlibet, but am open to using Rhythmbox. I will always use ExFalso for tagging though, until someone creates something just as good.

I lost a lot of respect for QL upstream after the whole "bucket of cocks" incident

---

### Post by ace214 on 2009-02-23
> **directhex said:**
> I lost a lot of respect for QL upstream after the whole "bucket of cocks" incident
I actually don't know what happened to the upstream. Care to share?
The only thing I saw was the site being dumped and code continuing on Google.

But regardless, I still like the way the player works.

---

### Post by CarpKing on 2009-02-23
Not sure which way to vote... I like Rhythmbox, but certain aspects of Banshee's look do appeal to me.  I tried it out a long time ago and didn't like it as much, and I heard that it doesn't support monitoring directories for changes, which is a function I use.  I should give it a try again, though.  My impression of the zeitgeist suggests that if anything replaces Rhythmbox, it will be Banshee.

---

### Post by directhex on 2009-02-23
> **ace214 said:**
> I actually don't know what happened to the upstream. Care to share?
The only thing I saw was the site being dumped and code continuing on Google.

But regardless, I still like the way the player works.

[http://bugs.debian.org/477454](http://bugs.debian.org/477454)

---

### Post by RAOF on 2009-02-23
> **Maduroutmb said:**
> ...
Is the goal a unified ripping/burning/decoding/encoding application for both audio and video, or is that so far in the future as to have no effect on current decisions?  I ask because that question really informs the decision between Exaile and Banshee for me.

Yes, and no.  The focus at the moment in Banshee is certainly on audio, but it's a not-totally terrible video library at the moment as well.  I'd certainly love it to handle DVD rips in the same way as it handles CDs, and there's nothing much stopping that from happening.

---

### Post by hockeyhead019 on 2009-02-23
hmm so i assume we're not allowing any KDE stuff? cuz i use amarok and think it's great but i guess that would be a bad idea to have to get all the KDE dependencies installed with the ubuntu release haha... but out of that list i like rhythmbox the most because it works the best in my opinion but banshee seems to look nicer and shows potential

---

### Post by RAOF on 2009-02-23
> **hockeyhead019 said:**
> hmm so i assume we're not allowing any KDE stuff? cuz i use amarok and think it's great but i guess that would be a bad idea to have to get all the KDE dependencies installed with the ubuntu release haha... but out of that list i like rhythmbox the most because it works the best in my opinion but banshee seems to look nicer and shows potential

Indeed.  There's absolutely no way amarok would fit on the CDs, as it'd have to pull in a large chunk of the KDE stack.

---

### Post by hockeyhead019 on 2009-02-23
yea that's what i figured... o well i'll just install all that on my own haha :D but yea banshee looks nice but rhythmbox works the best of the options

---

### Post by lamalex on 2009-02-23
+1 for banshee, been using it since 1.0 and it rules. Beautiful UI, friendly, active, intelligent developers, and strong GNOME integration; basically it's awesome.

---

### Post by knocte on 2009-02-23
> **kaivalagi said:**
> Yeah you're right, I guess what I mean is Python friendly and python extendible. The point I am trying to make is that plugin development in python lends itself more to Linux with a large range of libraries available to do all sorts of stuff simply. Mono is okay but I don't think there is quite the library support found there...(maybe I'm wrong?)


You're wrong. There are a lot of libraries out there made in .NET, specially because you're not tied to a language to make them. So you can use any C#/VB.NET/Nemerle/F#/Java#/Boo/IronRuby/IronPython library in your Mono programs.

And you would ask "IronPython"? Exactly, you can use Python language with Mono. And with IronClad you can use Python libraries as well (more info here: [http://tirania.org/blog/archive/2009/Jan-30.html](http://tirania.org/blog/archive/2009/Jan-30.html)). So, Mono is not just another "language", it's a whole platform where all can be merged and used altogether.


> **kaivalagi said:**
> 
I spent some time using xmms2, the music daemon, and used esperanza (qt based :( ) for the front end. It was okay, good on resources etc. If only a really nice front end was created for that.


If you like players a-la-XMMS2, Audacious is the successor of this one and the successor of BitMediaPlayer too.


> **mc4100 said:**
> Added Poll. :)

URL?


> **tawmas said:**
> 
Which is not that bad -- in fact it's shaping up quite well -- but right now has got a couple of showstoppers.

First it doesn't support gapless playback, which is awful for listeners of Classical music (and I guess other genres with which I'm not familiar).


It's [http://bugzilla.gnome.org/show_bug.cgi?id=440952](http://bugzilla.gnome.org/show_bug.cgi?id=440952) if anyone is interested...


> **tawmas said:**
> 
Second, the initial collection indexing is way too much CPU intensive, and I didn't find a way to add music I have on disk without reindexing the whole collection, and risking to burn my CPU in the process...


What version are you using? Banshee has been overhauled in the 1.x series to fix performance issues like these. Could you try again and, if it's still an issue, file it in [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/) ? Thanks.


> **SKLP said:**
> 
The mono argument is just silly: mono implements an open standard (CLI and C#...) just like gcc implements an open standard (C, C++). Just because Microsoft was the original author doesn't mean Mono is evil. Both mono and gcc are freely available...

Exactly.


> **RAOF said:**
> Probably a taglib bug.  Banshee uses taglib# to read out the metadata from files, and won't import them unless taglib supports them.

It could, perhaps, do with a gstreamer fallback path.  It used to read metadata from gstreamer, but taglib was some ten times faster or so.

Could you guys report the bug in [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/) ? The maintainers are pretty responsible about this kind of things and I'm sure they'll care about it.


> **ace214 said:**
> I like Banshee, but I don't think I can make the permanent move until it supports browsing by genre.


I think you're referring to this:
[http://bugzilla.gnome.org/show_bug.cgi?id=538005](http://bugzilla.gnome.org/show_bug.cgi?id=538005)

You could add yourself to the CC list and know when it's fixed (maybe I contribute a fix some time because I think it's a cool feature as well).

Anyway, there's an easy workaround: create a Smart Playlist for every Genre you have.


> **ace214 said:**
> 
I currently use Quodlibet, but am open to using Rhythmbox. I will always use ExFalso for tagging though, until someone creates something just as good.

Have you really tried the tagging capabilities of Banshee? It's getting better and better.


> **CarpKing said:**
>  I tried it out a long time ago and didn't like it as much, and I heard that it doesn't support monitoring directories for changes, which is a function I use.  

You're talking about this:
[http://bugzilla.gnome.org/show_bug.cgi?id=385965](http://bugzilla.gnome.org/show_bug.cgi?id=385965)

You could add yourself to the CC list and know when it's fixed (it's a pretty requested feature and it seems it will be fixed soon).

---

### Post by Stochastic on 2009-02-23
I love QuodLibet, but I know beginners will just whine about its looks, so I've placed my vote elsewhere.

---

### Post by deathsshadow77 on 2009-02-23
just tried out listen and I have to say im very impressed. I love the interface so many good features available with one click.

---

### Post by BwackNinja on 2009-02-23
I personally like mpd with sonata as a frontend, fast, compact, and light on resources, but I wouldn't expect that by default. I'd go with Rhythmbox now, Banshee later. Though it would probably be odd for a short while for people installing ubuntu and not being able to find Rhythmbox in the default install :P

The last music player I really liked before using sonata + mpd, was xmms (not xmms2, yes, the gtk1.2 app) and supplemented it with MethLab as my music library and I still use it in my gutsy install. Somehow though, I never really liked using Audacious...

So many music players, and all of them have a following :D

---

### Post by ace214 on 2009-02-23
> **directhex said:**
> [http://bugs.debian.org/477454](http://bugs.debian.org/477454)
Holy moly...

Well, yes, that does make me lose a little respect for QuodLibet's dev team, but I still like the player...

---

### Post by ace214 on 2009-02-23
> **knocte said:**
> I think you're referring to this:
[http://bugzilla.gnome.org/show_bug.cgi?id=538005](http://bugzilla.gnome.org/show_bug.cgi?id=538005)

You could add yourself to the CC list and know when it's fixed (maybe I contribute a fix some time because I think it's a cool feature as well).

Anyway, there's an easy workaround: create a Smart Playlist for every Genre you have.

Have you really tried the tagging capabilities of Banshee? It's getting better and better.
Thanks for pointing out the playlist workaround. This actually works better than I thought it would as it saves some horizontal space in the browser.

As far as tagging goes, it is missing two essential things for me in dealing with filenames: guessing tags from directory and filename and renaming files based on tags. I do like the interface though. Also, although there are enough fields in the Banshee, but, ideally, all the supported fields by the file would be available.

---

### Post by knocte on 2009-02-24
> **ace214 said:**
> 
As far as tagging goes, it is missing two essential things for me in dealing with filenames: guessing tags from directory and filename and renaming files based on tags. I do like the interface though. Also, although there are enough fields in the Banshee, but, ideally, all the supported fields by the file would be available.

I *think* that the rename file is already done. Check the last versions, and don't forget to file your ideas in Bugzilla. Thanks.

---

### Post by phoogkamer on 2009-02-24
Shouldn't we concentrate on Jaunty first, since this is a Jaunty Jackalope Testing and Discussion forum. I think announcing Karmic Koala is good for marketing, but not good for focus on the current developing version.

Although I vote for Rhytmbox.

---

### Post by kaivalagi on 2009-02-24
> **knocte said:**
> You're wrong. There are a lot of libraries out there made in .NET, specially because you're not tied to a language to make them. So you can use any C#/VB.NET/Nemerle/F#/Java#/Boo/IronRuby/IronPython library in your Mono programs.

And you would ask "IronPython"? Exactly, you can use Python language with Mono. And with IronClad you can use Python libraries as well (more info here: [http://tirania.org/blog/archive/2009/Jan-30.html](http://tirania.org/blog/archive/2009/Jan-30.html)). So, Mono is not just another "language", it's a whole platform where all can be merged and used altogether.

I still prefer python and it's libraries only :)

> **knocte said:**
> If you like players a-la-XMMS2, Audacious is the successor of this one and the successor of BitMediaPlayer too.

xmms2 is not xmms...it is a daemon based music player more akin to mpd. Rewritten from the ground up by one of the xmms developers I think. [http://wiki.xmms2.xmms.se/wiki/Features](http://wiki.xmms2.xmms.se/wiki/Features)

---

### Post by burnetbj on 2009-02-24
I run Gnome but immediately remove the audio player, torrent, ripper and install Amarok,Ktorrent, K3B ....theres just no match out there for me any how...I hope what ever they make default identical to Amarok heh. I am getting worried about Amarok2 the interface is nasty.

My 2 bits

---

### Post by CarpKing on 2009-02-24
Voted Rhythmbox for now, but I think Banshee is the logical successor if it comes to that.

---

### Post by tawmas on 2009-02-24
> **knocte said:**
> (About Banshee not supporting gaples playback)

It's [http://bugzilla.gnome.org/show_bug.cgi?id=440952](http://bugzilla.gnome.org/show_bug.cgi?id=440952) if anyone is interested...

Well, I'm interested. I'm subscribed to the Launchpad bug which is tracking the upstream bug above. Doesn't look like there's much activity though... Feel free to prove me wrong -- I'd really love to be proven wrong, actually! :-)

> **knocte said:**
> (About Banshee burning my CPU on initial collection indexing and all subsequent reindexings)

What version are you using? Banshee has been overhauled in the 1.x series to fix performance issues like these. Could you try again and, if it's still an issue, file it in [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/) ? Thanks.

That was a couple of months ago, with the latest Jaunty packages available at the time (1.4.something). I recall posting a screenshot of top showing Banshee using an unbelievable amount of CPU (it was like 169%, I didn't know it could go over 100%).

I will try again and post a bug if it's still the case. I'm quite interested in Banshee.

> **knocte said:**
> (About monitoring directory changes)

You're talking about this:
[http://bugzilla.gnome.org/show_bug.cgi?id=385965](http://bugzilla.gnome.org/show_bug.cgi?id=385965)

You could add yourself to the CC list and know when it's fixed (it's a pretty requested feature and it seems it will be fixed soon).

That's really good to know! I'm going to subscribe to that bug.

Thanks a lot for your feedback and suggestions!

---

### Post by Simian Man on 2009-02-24
> **tawmas said:**
> That was a couple of months ago, with the latest Jaunty packages available at the time (1.4.something). I recall posting a screenshot of top showing Banshee using an unbelievable amount of CPU (it was like 169%, I didn't know it could go over 100%).


It can if you have more than one CPU and the app uses multithreading or multiprocessing.

---

### Post by QwUo173Hy on 2009-02-24
I don't know why more people didn't vote for Quod Libet. The interface is very configurable and can be as simple or detailed as you like. The tagging capabilities are second to none and it runs just as smoothly with a very large library.

I have to admit, that I'd never heard of it even though I had tried Rhythmbox, Banshee and Exaile. It was a thread on the forums that put me on to it and boy was I impressed.

Of course everyone has their personal preference but it seems to me that whatever feature someone likes in another application.. Quod Libet can do it.

---

### Post by directhex on 2009-02-24
> **Simian Man said:**
> It can if you have more than one CPU and the app uses multithreading or multiprocessing.

I wouldn't expect that level of CPU consumption unless the Mirage plugin is installed - at which point it's normal behaviour for first-run

---

### Post by tawmas on 2009-02-24
> **directhex said:**
> I wouldn't expect that level of CPU consumption unless the Mirage plugin is installed - at which point it's normal behaviour for first-run

Ok, I've just tried. This was a fresh reinstall (I had previously removed and purged the Banshee package). I don't have the Mirage plugin installed, and I have the "Disable features requiring Internet access" preference ticked, so it didn't download cover art for albums.

CPU stayed mostly above 100%, and it went as high as (approximately) 156%. CPU temperature went as high as 70.9C, which is not safe for my CPU.

My collection is 6425 files, and the effective time reported by top at the end of the scan is about 7:30.

Please, let me know what kind of information you would like to see in the bug report, and I'll file one.

---

### Post by ace214 on 2009-02-24
> **jarlath said:**
> I don't know why more people didn't vote for Quod Libet. The interface is very configurable and can be as simple or detailed as you like. The tagging capabilities are second to none and it runs just as smoothly with a very large library.

I have to admit, that I'd never heard of it even though I had tried Rhythmbox, Banshee and Exaile. It was a thread on the forums that put me on to it and boy was I impressed.

Of course everyone has their personal preference but it seems to me that whatever feature someone likes in another application.. Quod Libet can do it.
Agreed. In fact, most of the features that I seek in other applications come from using them in QuodLibet. People seem to want more eye-candy than functionality...

---

### Post by hockeyhead019 on 2009-02-24
> **burnetbj said:**
> I run Gnome but immediately remove the audio player, torrent, ripper and install Amarok,Ktorrent, K3B ....theres just no match out there for me any how...I hope what ever they make default identical to Amarok heh. I am getting worried about Amarok2 the interface is nasty.

My 2 bits

agree ^^ except i use deluge bittorrent haha completely off topic sorry haha

---

### Post by scaine on 2009-02-24
Yep, off topic, but Deluge is awesome.  I love that it can run on a server as a daemon, then you just connect to your server - all from the same GUI interface, just by ticking boxes.  Very well done.

On topic, I voted Banshee - although I despite their products, too many of my mates love Apple and their iPods.  Banshee seems to have the best support by far, succeeding in syncing the later models where Rhythmbox fails.

About Quod Libet, I enjoyed reading that thread.  And this has to be best changelog I've seen in a while :
> Ship modified upstream tarball, removing insulting source code, and put a note in README.Debian to explain why we're doing this (closes: #[477454]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=477454")).
Childish, but amusing and I thought that the target of the insult who posted on the bug did so with great restraint and aplomb!  :lolflag:

---

### Post by medeshago on 2009-02-24
I like Banshee, but Rhythmbox can scrobble the songs from my ipod to last.fm, monitor the directories I have my music in and it's amazingly fast. I prefer Banshee's UI, but the lack of features that Rhythmbox has makes me want to stay with Rhythmbox.

---

### Post by knocte on 2009-02-24
> **kaivalagi said:**
> I still prefer python and it's libraries only :)


So, you have platform X that lets you do A, and platform Y that lets you do A, B, C, D, and still prefer platform X? This is complete irrationality!

---

### Post by knocte on 2009-02-24
> **tawmas said:**
> Ok, I've just tried. This was a fresh reinstall (I had previously removed and purged the Banshee package). I don't have the Mirage plugin installed, and I have the "Disable features requiring Internet access" preference ticked, so it didn't download cover art for albums.

CPU stayed mostly above 100%, and it went as high as (approximately) 156%. CPU temperature went as high as 70.9C, which is not safe for my CPU.

My collection is 6425 files, and the effective time reported by top at the end of the scan is about 7:30.

Please, let me know what kind of information you would like to see in the bug report, and I'll file one.

If you include the exact version you're using (and where did you get it), and paste the log of what do you see in the console when that happens (launching banshee from the console, that is), that's enough for a bug report. You may have to answer more questions from the developers later on, though.

Thanks for testing!

---

### Post by kaivalagi on 2009-02-25
> **knocte said:**
> So, you have platform X that lets you do A, and platform Y that lets you do A, B, C, D, and still prefer platform X? This is complete irrationality!

Sorry, I don't mean to go too far off topic but, it's not really irrational to stick to one language. Why write applications that use several different languages under the hood? sounds like a maintenance headache. Why not just use one language that works for everything...

And if the choice of language is python then mono isn't warranted. If the choice is c#/vb then Python isn't warranted. The only exception to this would be when lower level development is required, such as in the case of C based games engines, where python or alike is used for rapid dev of system areas around it, where performance isn't a necessity.

In Banshee's case it is using mono so I would expect vb/c# to be used, even for plugin development.

The only situation I can see that would benefit from mono's support of Python through IronPython is where system integration work is necessary...

Just my opinion :) Each to their own and all that.

---

### Post by knocte on 2009-02-25
> **kaivalagi said:**
> Sorry, I don't mean to go too far off topic but, it's not really irrational to stick to one language. Why write applications that use several different languages under the hood? sounds like a maintenance headache. Why not just use one language that works for everything...

And if the choice of language is python then mono isn't warranted. If the choice is c#/vb then Python isn't warranted. The only exception to this would be when lower level development is required, such as in the case of C based games engines, where python or alike is used for rapid dev of system areas around it, where performance isn't a necessity.

In Banshee's case it is using mono so I would expect vb/c# to be used, even for plugin development.

The only situation I can see that would benefit from mono's support of Python through IronPython is where system integration work is necessary...

Just my opinion :) Each to their own and all that.

I still don't get it.

If you use IronPython, nobody forces you to use *other* languages. Only thing is that you will have the **possibility** in case you need it. So, that being said, your decision just restricts you, nothing more.

---

### Post by knocte on 2009-02-25
> **knocte said:**
> I still don't get it.

If you use IronPython, nobody forces you to use *other* languages. Only thing is that you will have the **possibility** in case you need it. So, that being said, your decision just restricts you, nothing more.

Besides, it's not only the possibility for you to use a wide range of things, it's a possibility for *others* to use the libraries you develop. For example if you develop an IronPython lib, an IronRuby user will be able to use it. This way you create ecosystem, a very similar concept to how open source works in the end.

---

### Post by tretle on 2009-02-25
The subject of python or iron python is a different one. It is up to the individual to determine which language suits them best. This thread is not about using any particular language, its about media in karmic so try and keep it relevant and to the point.

---

### Post by kaivalagi on 2009-02-25
> **tretle said:**
> The subject of python or iron python is a different one. It is up to the individual to determine which language suits them best. This thread is not about using any particular language, its about media in karmic so try and keep it relevant and to the point.

Apologies

@knocte, I accept your arguments for, they make sense, personal preference is the only difference here :)

Getting back on the subject of Rhythmbox then...just because development is slowing/stopping, is that a valid reason to not use it as the default player? It has all my required features as a "music player" and from what I have read any nasty bugs (if there are any that really matter now) will probably still get addressed by the developer.

Also, why couldn't Ubuntu or other developers around take on the support if the original developer loses all interest?

---

### Post by directhex on 2009-02-25
> **kaivalagi said:**
> Getting back on the subject of Rhythmbox then...just because development is slowing/stopping, is that a valid reason to not use it as the default player? It has all my required features as a "music player" and from what I have read any nasty bugs (if there are any that really matter now) will probably still get addressed by the developer.

If there's no scope for improvement, ever, then what next? An app with active developers is more likely to adapt to users' changing needs

> Also, why couldn't Ubuntu or other developers around take on the support if the original developer loses all interest?

Is it a good use of resources, if more actively maintained alternatives exist?

---

### Post by kaivalagi on 2009-02-25
Fair points, although I think I'll still use it as long as it's in the repos - until the alternatives are as good IMHO.

It does what a music player needs to do......until a new music format takes over that is :)

---

### Post by directhex on 2009-02-25
> **kaivalagi said:**
> Fair points, although I think I'll still use it as long as it's in the repos - until the alternatives are as good IMHO.

Entirely reasonable

Use whichever player you like - the question is over which player should be given to new users as standard

> It does what a music player needs to do......until a new music format takes over that is :)

If a different app gets a better GUI or better performance or more powerful searching or whatever, would you consider that a reasonable reason to change?

---

### Post by kaivalagi on 2009-02-26
> **directhex said:**
> If a different app gets a better GUI or better performance or more powerful searching or whatever, would you consider that a reasonable reason to change?

Yep, all of the above

Right now though I find rhythmbox does everything well for me

I did try Banshee but didn't like the time it took to sort itself out with a new music collection. And Exaile is okay except I prefer the search results layout of rhythmbox.

---

### Post by KhaaL on 2009-02-26
i'm quite fond of lsiten! but it havent been developed since... ever?

otherwise, i'd say go for songbird. its slowly becoming the cross-platform amarok.

---

### Post by karlmp on 2009-02-26
listen will kill banshee in the future, probably by November if the developers hurry up

listen is by default in xubuntu 8.10

[http://www.listen-project.org/](http://www.listen-project.org/)

---

### Post by tawmas on 2009-02-26
I've just filed a bug regarding my problem with high CPU usage:
[http://bugzilla.gnome.org/show_bug.cgi?id=573319](http://bugzilla.gnome.org/show_bug.cgi?id=573319)

Since I prefer Launchpad, I opened a bug there too and added a watch for the upstream bug. It's [LPBUG]#335174[/LPBUG].


... and I'm impressed with Listen! :-) I didn't know it, so I was quite surprised. Too bad that the version in the repositories doesn't have the equalizer... I really like it, but it doesn't seem to support gapless playback either, so I'm staying with Rhythmbox a little more.

---

### Post by scaine on 2009-02-26
You know, I could have sworn that gapless playback was a GStreamer .10 feature.  How come Banshee, Listen, etc don't have gapless playback if they use Gstreamer backends?

Or don't they use Gstreamer backends?

---

### Post by tawmas on 2009-02-26
> **scaine said:**
> You know, I could have sworn that gapless playback was a GStreamer .10 feature.  How come Banshee, Listen, etc don't have gapless playback if they use Gstreamer backends?

Or don't they use Gstreamer backends?

Yes, they use Gstreamer (well, I'm sure about Bashee, and I think so about Listen). But this is not enough.

At the application level, you need, at the very least, to schedule the next song for playing before the current song ends, so that an uninterrupted music stream can reach the sound card.

This is with lossless audio formats, and lossy formats designed to support gapless playback out of the box (like OGG). Other compression formats introduce encoder-induced gaps at the beginning and the end of the track, which you have to account for to have gapless playback.

Actually, to the best of my knowledge, not even Rhythmbox supports gapless playback of such formats (MP3, AAC, etc.). But gapless playback for OGG and FLAC is enough for me. :-)

---

### Post by ace214 on 2009-03-01
So, with the recent Python upgrades temporarily knocking out my QuodLibet (yeah, I decided to remove it anyway), I went looking for an alternative music tagger that would do similar and found a great app. Thought some people in this thread might be interested in this. It's command line, not GUI, and is a little complicated with variables, but it appears to be quite powerful.
>  lltag takes a list of music files on the command line and tries to automatically understand their filenames and guess their associated tags. It uses an internal format database to do so. For each file, it will try each format until one matches the current filename, extract the corresponding fields from the filename and set the music tags.

lltag also allows to pass one or several format strings like "%a - %A/%n. - %t", so that the user may help the program when the filenames are too strange, complex or damaged.

It is also possible to set some fields by hand or edit some. And finally, lltag may use these fields to rename the file according to a user-given filename format.
TrackType.org

lltag also provides a interface to access an online CDDB (TrackType.org) and retrieve tags from there. It makes it possible to tag/rename a file from scratch. 

Here's the [website]("http://home.gna.org/lltag/"). It's in the repos.

---

### Post by Arlanthir on 2009-03-01
About tagging and the players: I love rhythmbox, because of it's simplicity and powerful text-based library browser.

However, the ratings get saved on a xml file instead of the actual id3 tags. That's a drag for me. Is this normal among music players?

---

### Post by Simian Man on 2009-03-01
I tried out Banshee and had many problems.
[LIST]
[*]The Last.fm plugin wouldn't let me sign in
[*]When copying music to my iPod the art files were 3 gigs large
[*]Copying music to my iPod took over twice the time of Rhythmbox
[*]The album art was wrong quite a few times
[/LIST]

It is definitely sexier than Rhythmbox, but until it is as stable, there should be no change in the default.

---

### Post by gnomeuser on 2009-03-01
> **scaine said:**
> You know, I could have sworn that gapless playback was a GStreamer .10 feature.  How come Banshee, Listen, etc don't have gapless playback if they use Gstreamer backends?

Or don't they use Gstreamer backends?

Gapless requires the playbin2 element which isn't default yet. The Rhythmbox implementation is not a standard gstreamer feature instead it's their own homebrew.

---

### Post by tretle on 2009-03-01
> **Simian Man said:**
> I tried out Banshee and had many problems.
[LIST]
[*]The Last.fm plugin wouldn't let me sign in
[*]When copying music to my iPod the art files were 3 gigs large
[*]Copying music to my iPod took over twice the time of Rhythmbox
[*]The album art was wrong quite a few times
[/LIST]

It is definitely sexier than Rhythmbox, but until it is as stable, there should be no change in the default.

Any chance of posting what version? I have no problems with the last.fm plugin here. As for copying music to my ipod I cant really do a comparison because although rhythmbox gives the illusion of the music being copied over when I actually take a look at the ipod afterwards I soon realise that rhythmbox never updated the database.  In fact I am extremely happy with the ipod support for banshee, offering to restructure the database when itunes messes it up is a great feature. A whole lot better than just simply not working like rhythmbox. The only complaint when it comes to the ipod would be the album art. Sometimes it mixes up the album art with the other tracks being synced but I find it a hell of allot better than not uploading the album art at all like rhythmbox does, in fact last time i checked you have to play a track in order for rhythmbox to grab the album art and store it in the cache, this was incredibly annoying for fresh installs when you might not have played that track on that installation yet.

Allot of people think its time to get a new theme for ubuntu but my personal opinion is that the music player is much more important. Rhythmbox just doesn't work very well. Back when I was backing rhythmbox I had several private messages from these threads one of which was a guy asking me how they can get their children's ipods working with it, Its a pain to to try and get working well. Maybe not for the older gen models but 3rd gen nano on is just horribly supported. Ipods are popular, they are one of the most popular mp3 players out. Ubuntu should be in a situation where these players are supported out of the box. 
And this is only one aspect in which rhythmbox doesn't handle very well. I have a great respect for moch and the guys but a rewrite is needed. 
And unfortunately one should ask themselves should ubuntu be held back in terms of functionality and having an audio player that "Just Works" the way its supposed to until this rewrite is completed(it hasn't even been started yet) or should they just switch to a well maintained alternative which is similar enough in terms of layout that people would not be uncomfortable about the change(banshee).
My personal opinion is no, if banshee has already proven itself then why not switch to using it as default, people shouldn't let their reservations about a programming language influence their opinion on having open source software that just works and I feel that is one of the main reasons people were against it before. 
As hard as I find it to say rhythmbox doesn't just work.

---

### Post by scaine on 2009-03-01
Bit harsh to say "Rhythmbox doesn't work" just because it doesn't handle the ridiculously proprietary iPod format, isn't it?

I like Banshee's support of iPods - it didn't get every track over, and failed utterly on album art, but it did the trick.  But I've never moved over Banshee full time, because completely contrary to what you've just posted, I find that Rhythmbox does "just work".

I voted Banshee, because I like to see continual development on the software I use - it keeps me interested to see progress.  But better iPod support is no reason to slag Rhythmbox.

Let's not forget that out of the box, Ubuntu doesn't support MP3!  As a free distribution, it has absolutely zero interest in the MP3-only Apple player... although, I concede that as a distribution that wants to appeal to the masses, it probably should.

---

### Post by tretle on 2009-03-01
I wasn't slagging rhythmbox, I was being realistic. Even the current maintainer is realistic about rhythmbox in its current form. It was good for its time but is a pain in the *** to maintain and as a result doesn't get as much developer interest which in turn affects its users. 
Rhythmbox does a great job of giving one the illusion that it just works but if you take a closer look its failing in places. The database needs a rewrite, the ipod support needs love, the visualization code kinda sucks, Even things like modifying the ui are incredibly hard to do at the moment.. 
I'm not sure if you noticed but extra padding was added to the top of the album art a while ago. The original goal was to add the extra padding at the top but unfortunately there was no way of doing this without adding padding to the bottom which kinda sucked because the status bar already provided padding. 
Anyway's I have great respect For all the guys working on rhythmbox, they have done a great job trying to keep it going but I also wouldn't like to be in their situation because the underlying structure of the code would just depress me.
There will most likely be a rewrite but a rewrite will take time. Banshee and rhythmbox are on par in features at the moment, yet I have been using banshee from svn and testing the visualizations from openvp which are really cool and the openvp stuff is finished so as soon as the now playing code gets updated it will make it into trunk. Once visualizations are done the only thing which is missing is gapeless which is also planned.
Even after the first new version of the rewrite comes probably in a year or two at the least it wont have half of the features of banshee.
So lets be realistic instead of complacent here.

---

### Post by Simian Man on 2009-03-01
It seems that iPod support for both is a little hit or miss regardless of the app.  I find that Rhythmbox does a better job, but if you say Banshee handled yours well, then that's good.  I know that Rhythmbox's development is stagnating at the moment whereas Banshee is progressing rapidly.  I just fell that *right now* Rhythmbox is a better media player, at least as default.

I truly hope that Banshee can get its features stable and working well, because it is a lot better in theory.

---

### Post by hockeyhead019 on 2009-03-01
banshee does seem better in theory but i think it kinda goes back to stupid apple for being idiots and making their stuff so hard to communicate and work with for the guys doin the open source stuff which is why i think it's so hit or miss, with all the different ipods and so on and so on

---

### Post by LiquidMeson on 2009-03-01
Despite Banshee already being well known and fairly stable on the linux platform I believe songbird would be the best choice. I mainly say this be cause we need a media player that runs on all platforms, encouraging development from all sides. Also if one is already familiar with an application on osx or windows, it will be easier for them to switch to ubuntu knowing how it works. ++ the Mozilla team has already done a great job, and continue to do so with firefox.

---

### Post by cszikszoy on 2009-03-02
> **LiquidMeson said:**
> Despite Banshee already being well known and fairly stable on the linux platform I believe songbird would be the best choice. I mainly say this be cause we need a media player that runs on all platforms, encouraging development from all sides. Also if one is already familiar with an application on osx or windows, it will be easier for them to switch to ubuntu knowing how it works. ++ the Mozilla team has already done a great job, and continue to do so with firefox.

Banshee runs on osx and I don't think a windows port is too far off.

---

### Post by directhex on 2009-03-02
> **LiquidMeson said:**
> Despite Banshee already being well known and fairly stable on the linux platform I believe songbird would be the best choice. I mainly say this be cause we need a media player that runs on all platforms, encouraging development from all sides. Also if one is already familiar with an application on osx or windows, it will be easier for them to switch to ubuntu knowing how it works. ++ the Mozilla team has already done a great job, and continue to do so with firefox.

Am I the only one who found Songbird totally unusable on Windows?

---

### Post by puccaso on 2009-03-02
WHEN THE doooodaaaaaaaaaaaaa:@:@ WILL banshee get genre support?!? 

what kind of ice-age music player doesnt play music by genre... and please dont tell me that i can go and make a super-duper-playlist with the genre i want... i guess i could hold a light-bulb to my bread to make toast too... 

i love the video playback in rhythmbox... i dont like the fact that banshee doesnt allow multiple folders to be watched... and it should have a seperate system to manage videos and music... i add new videos and i have to rescan the whole collection.....


just my 2c.. or 2p seeing as i'm from the UK.. or 2 tk seeing as i'm living in turkey at the mo..

---

### Post by tretle on 2009-03-02
Genre support was in trunk a few releases back but they decided not to release it yet as they were not 100% happy with it and wanted to get it perfect. And last time I checked rhythmbox didn't support videos. 
For anyone arguing about stability and banshee can you be a bit more specific on what is unstable and what version you are using rather than saying randomly its unstable and thus not actually helping to debug the issues and release fixes.
I don't think songbird will make it in, its not a gtk app and its not affiliated with mozilla which is a common misconception.

---

### Post by knarf on 2009-03-19
Now here lies a field where Canonical can make a visible, tangible difference... I'd say the best solution is a client with a separated front- and backend so my current vote goes to mpd. The available frontends for mpd are OK but they probably do not live up to the expectations of those looking for the bling and featuritis associated with this type of software. What mpd has got right is more important though:

a) speed, b) stability and c) interoperability. Here at home music (local files, internet radio stations or files shared by networked machines) is streamed from the 'server under the stairs (a BP6 with 2 x 466 MHz Celeron processors...)' to whatever machine on the network I happen to work on using pulseaudio (but not rtp as that crashes dd-wrt-based routers...), I can change tunes using anything from a simple command line client to a full-fledged, album-art-and-lyrics-including player application (gmpc) or even my phone. Of course you can also run the daemon and client on the same machine to get something similar to the more traditional media players. The opposite is usually not the case.

So IMnsHO mpd already fits the bill but if more bling & features are wanted Canonical could put some people on building a client which provides those. There are many projects which something like this can be based on... just take the good features from all of them (eg. Rhythmbox's search) and combine them in something lightweight, stable and snappy.

---

### Post by Reiger on 2009-03-19
I may be stupid but at bootup I get this "Musicplayer Daemon" startup text (mpd) ;)

---

### Post by jblackhall on 2009-04-21
Looks like Banshee's going to be proposed for Karmic at UDS Barcelona: [http://www.apebox.org/wordpress/rants/74/](http://www.apebox.org/wordpress/rants/74/)

---

### Post by ghindo on 2009-04-21
> **jblackhall said:**
> Looks like Banshee's going to be proposed for Karmic at UDS Barcelona: [http://www.apebox.org/wordpress/rants/74/](http://www.apebox.org/wordpress/rants/74/)I saw this article too.  Quite interesting.  The inevitable Mono debates, however, are growing a bit tiresome :(

---

### Post by Hyper Tails on 2009-04-21
I just voted rhythm box 
I use vlc media player

---

### Post by ronacc on 2009-04-21
> **ghindo said:**
> I saw this article too.  Quite interesting.  The inevitable Mono debates, however, are growing a bit tiresome :(

while I would welcome seeing banshee as the default media player the rationale justifying it disturbs me , I would rather see it accepted as a better media player ( ofcourse thats a personal judgement and subject to debate) than because it might save a few MB disk space.

---

### Post by biji on 2009-04-23
okay... i voted songbird
but then i try to install banshee.. and impressed ( last time i tried banshee is a year ago)
i think banshee is better now in term of stability and feature
PS: banshee seems backed up by novell now

---

### Post by Merk42 on 2009-04-23
> **ronacc said:**
> while I would welcome seeing banshee as the default media player the rationale justifying it disturbs me , I would rather see it accepted as a better media player ( ofcourse thats a personal judgement and subject to debate) than because it might save a few MB disk space.

Well that's probably why they voted Banshee
Disk space is **objective**
Quality is **subjective**

---

### Post by matthewbpt on 2009-04-23
> **tretle said:**
> Any chance of posting what version? I have no problems with the last.fm plugin here. As for copying music to my ipod I cant really do a comparison because although rhythmbox gives the illusion of the music being copied over when I actually take a look at the ipod afterwards I soon realise that rhythmbox never updated the database.  In fact I am extremely happy with the ipod support for banshee, offering to restructure the database when itunes messes it up is a great feature. A whole lot better than just simply not working like rhythmbox. The only complaint when it comes to the ipod would be the album art. Sometimes it mixes up the album art with the other tracks being synced but I find it a hell of allot better than not uploading the album art at all like rhythmbox does, in fact last time i checked you have to play a track in order for rhythmbox to grab the album art and store it in the cache, this was incredibly annoying for fresh installs when you might not have played that track on that installation yet.

Allot of people think its time to get a new theme for ubuntu but my personal opinion is that the music player is much more important. Rhythmbox just doesn't work very well. Back when I was backing rhythmbox I had several private messages from these threads one of which was a guy asking me how they can get their children's ipods working with it, Its a pain to to try and get working well. Maybe not for the older gen models but 3rd gen nano on is just horribly supported. Ipods are popular, they are one of the most popular mp3 players out. Ubuntu should be in a situation where these players are supported out of the box. 
And this is only one aspect in which rhythmbox doesn't handle very well. I have a great respect for moch and the guys but a rewrite is needed. 
And unfortunately one should ask themselves should ubuntu be held back in terms of functionality and having an audio player that "Just Works" the way its supposed to until this rewrite is completed(it hasn't even been started yet) or should they just switch to a well maintained alternative which is similar enough in terms of layout that people would not be uncomfortable about the change(banshee).
My personal opinion is no, if banshee has already proven itself then why not switch to using it as default, people shouldn't let their reservations about a programming language influence their opinion on having open source software that just works and I feel that is one of the main reasons people were against it before. 
As hard as I find it to say rhythmbox doesn't just work.

I don't know what you're on about with Rhythmbox not supporting new iPod models well, it does so FAR better than Banshee. I have a new Generation Ipod Classic and Rhythmbox transfers files to it perfectly, including the album art, and does so very fast, while Banshee corrupts the database and takes ages to transfer the files. This is a known bug in Banshee (and ipodslave too i think), Banshee cannot handle the database of the newer iPods.

---

