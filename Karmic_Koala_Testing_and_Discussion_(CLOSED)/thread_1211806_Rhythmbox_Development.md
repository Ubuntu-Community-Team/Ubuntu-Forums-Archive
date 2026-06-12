---
title: "Rhythmbox Development"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by b3n87 on 2009-07-13
Theres been a lot of talk about replacing Rhythmbox with Banshee.

But Rhythmbox seems to be going through a lot of development at the moment, especially with GoS 2009:

[Rhythmbox: Media Player Synchronization ]("http://socghop.appspot.com/student_project/show/google/gsoc2009/gnome/t124022403900")
[Rhythmbox Contextual Information Pane]("http://socghop.appspot.com/student_project/show/google/gsoc2009/gnome/t124022403331")

And theres been a few releases since 0.12.0:

[Rhythmbox 0.12.3 News File]("http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.12/rhythmbox-0.12.3.news")

Have these been taken into account, is there still time for Rhythmbox to stay as the default music player?

UPDATE:

Actually, quite a lot of work has been done since 0.12.0 which is the version Ubuntu currently has:

[0.12.1 NEWS]("http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.12/rhythmbox-0.12.1.news")
[0.12.2 NEWS]("http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.12/rhythmbox-0.12.2.news")
[0.12.3 NEWS]("http://ftp.gnome.org/pub/gnome/sources/rhythmbox/0.12/rhythmbox-0.12.3.news")

---

### Post by FarJumper on 2009-07-13
I fully agree with you. I personally love banshee player, but IMHO it's a bit early to include mono-based application to distributive. The only reason is: it's not efficient to include mono runtime for a couple of application depended on it.

---

### Post by b3n87 on 2009-07-13
I dont want to start a Mono flame war so lets end it now :-D

But from a technical point-of-view rhythmbox is a lot smaller in file size and runs quicker as its written in C i believe.

There seems to be a lot of new features being added and the releases are becoming more often which is good.

I personally would like to see if the could make it have a "album cover" view like iTunes. Its more interesting to look at when looking for your music, rather than reems of text in a list display.

If it was up to me, Id hold off switching to Banshee until Karmic+1 and review it again.

---

### Post by Jay_Bee on 2009-07-13
Rhythmbox and Banshee are the same size (in MB) and mono dependencies are already included for tomboy and F-spot.
Banshee seems to have a huge development momentum, as opposed to Rhythmbox whose lead developer announced that he won't develop new features for it.
So looking at things long-term Banshee seems to be the better choice, although it is still not decided that it will be the default in Karmic (there are some blockers that are being worked on AFAIK).
Anyway, no matter which player is the default, the other will be available to install so it's no big deal.

---

### Post by Joe_Bishop on 2009-07-13
Without inotify support banshee can't be any better then RB. Love manually check your library - use it. Leave RB in the default install for people who don't like to do things themselves which computer does the best.

---

### Post by b3n87 on 2009-07-13
Intersting stuff.

I wonder if they finish the Banshee "blockers" you speak of in time. Im guessing your talking about missing features that Banshee must have before it can replace Rythmbox?

---

### Post by Swarms on 2009-07-13
> **b3n87 said:**
> Intersting stuff.

I wonder if they finish the Banshee "blockers" you speak of in time. Im guessing your talking about missing features that Banshee must have before it can replace Rythmbox?

It is, and I now the team are very focussed on meeting those requirements. That was why they released 1.5, which is a beta. They wanted to show how far they have come.

I personally hope they meet the requirements, the development of RB has been near nonexistant.

---

### Post by directhex on 2009-07-13
> **b3n87 said:**
> Intersting stuff.

I wonder if they finish the Banshee "blockers" you speak of in time. Im guessing your talking about missing features that Banshee must have before it can replace Rythmbox?

At the current rate, Rhythmbox will remain the default for Karmic. The question will be re-evaluated for Karmic+1. I'll blog about the remaining blockers in a little bit.

---

### Post by Joe_Bishop on 2009-07-13
> At the current rate, Rhythmbox will remain the default for Karmic. The question will be re-evaluated for Karmic+1. I'll blog about the remaining blockers in a little bit.
nice!

---

### Post by steeleyuk on 2009-07-13
I've been really impressed with Rhythmbox development in the last few months. The lead developer quitting seems to have actually helped the project (at least in the short term), more updates and some neat changes.

The change I've loved more than any other is the ability to remove the notification area icon. Yes, I'm sad. :p

Seriously though, I expect Banshee to be the way forward but I don't think its worth or necessary to change at the moment.

---

### Post by ajackson on 2009-07-13
It will be nice to see two apps attempting to gain/hold top spot as competition can be very good for getting new features but hopefully not at the expense of existing bugs (ie bug fixes should always be a priority).

Can we leave any attempts at Mono-wars out of this thread and just concentrate on how Rhythmbox is changing.

---

### Post by ghindo on 2009-07-13
> **directhex said:**
> At the current rate, Rhythmbox will remain the default for Karmic. The question will be re-evaluated for Karmic+1. I'll blog about the remaining blockers in a little bit.With Karmic+1 being an LTS, would Banshee be seriously considered for inclusion?  It seems that switching the default music player for an LTS would cause some problems.

---

### Post by buzzmandt on 2009-07-13
It might be included in testing and if it tests good why not with LTS?
Personally I'll exchange either one for exaile anyway.  but I do like banshee better than rythbox.

---

### Post by Kow on 2009-07-13
Here is how I see it: As long as there are other dependencies on the mono libs (f-spot and tomboy just to name a couple) then the extra dep argument against including banshee is void. Personally, I have nothing against rhythmbox or banshee.... both have served me well. Rhythmbox is much further into it's development than banshee is, ie rhythmbox will generally be more stable for at least a little while longer. However, banshee has seen very notable progress especially with the current 1.5.x/1.6 beta development. The main deciding factor will probably come down to features between the two applications. I don't depend on too many features (both banshee and rhythmbox provide those that I use/want/need) so I can't elaborate too much on it. A good (valid) argument against banshee is it's slowness. I'm guessing this has to do with c#/mono.

---

### Post by Swarms on 2009-07-13
> **directhex said:**
> At the current rate, Rhythmbox will remain the default for Karmic. The question will be re-evaluated for Karmic+1. I'll blog about the remaining blockers in a little bit.

Sorry for being misinformed, but wasn't the plan to include Banshee if it could meet those blockers? You make it sound like they are not nearing to squash those blockers. Is that correct?

---

### Post by directhex on 2009-07-13
> **Swarms said:**
> Sorry for being misinformed, but wasn't the plan to include Banshee if it could meet those blockers? You make it sound like they are not nearing to squash those blockers. Is that correct?

[http://www2.apebox.org/wordpress/rants/153/](http://www2.apebox.org/wordpress/rants/153/) should explain the blockers in more detail, and the effect they have

---

### Post by directhex on 2009-07-13
> **ghindo said:**
> With Karmic+1 being an LTS, would Banshee be seriously considered for inclusion?  It seems that switching the default music player for an LTS would cause some problems.

It'd be possible - but harder - if that makes sense - i.e. Banshee would have more to prove to make the cut for an LTS

---

### Post by directhex on 2009-07-13
> **Kow said:**
> A good (valid) argument against banshee is it's slowness. I'm guessing this has to do with c#/mono.

Depends on which slowness you mean specifically. Slowness when scrolling is a feature, not a bug (no really) as it ties into Banshee's better scalability with large databases

---

### Post by Tibuda on 2009-07-13
> **directhex said:**
> [http://www2.apebox.org/wordpress/rants/153/](http://www2.apebox.org/wordpress/rants/153/) should explain the blockers in more detail, and the effect they have

Amazon integration would rock. Too bad they don't want it.

---

### Post by Swarms on 2009-07-13
> **directhex said:**
> [http://www2.apebox.org/wordpress/rants/153/](http://www2.apebox.org/wordpress/rants/153/) should explain the blockers in more detail, and the effect they have

Thank you for the blog entry, can I ask, if you good give a guess when Banshee would overcome those requirements?

> **danielrmt said:**
> Amazon integration would rock. Too bad they don't want it.

Only available to US customers anyway. :(

---

### Post by fluteflute on 2009-07-13
> **Swarms said:**
> Thank you for the blog entry, can I ask, if you good give a guess when Banshee would overcome those requirements?



Only available to US customers anyway. :(
and the UK :)

---

### Post by morryis on 2009-07-13
And Germany ;-)

---

### Post by Swarms on 2009-07-13
Oh you cocksuckers! (Sorry have been watching too much Deadwood lately).

Well, I can see why they should support Amazon store, but only if Amazon tried to emerge in more areas and made an API that was easy to work with. (Jo said in her blog it was a bad API).
Why don't they make it easy for others to earn money for them?

---

### Post by KingNeil on 2009-07-13
If Rhythmbox has iPod sync built in, that's all that's needed. That will make it as good as iTunes for 99% of users.

DEVELOP IPOD SYNCHRONISATION!

---

### Post by directhex on 2009-07-13
> **Swarms said:**
> Thank you for the blog entry, can I ask, if you good give a guess when Banshee would overcome those requirements?

I expect it soon - but not within the required 6 weeks. More than that, hard to say.

"Sooner if you help"!

---

### Post by Swarms on 2009-07-13
> **directhex said:**
> I expect it soon - but not within the required 6 weeks. More than that, hard to say.

"Sooner if you help"!

Sadly I can't code, but I will maybe look into documentation. :)

---

### Post by zekopeko on 2009-07-13
> **Swarms said:**
> Oh you cocksuckers! (Sorry have been watching too much Deadwood lately).

Well, I can see why they should support Amazon store, but only if Amazon tried to emerge in more areas and made an API that was easy to work with. (Jo said in **[SIZE="7"]her[/SIZE]** blog it was a bad API).
Why don't they make it easy for others to earn money for them?

lol.
that is all.

---

### Post by Swarms on 2009-07-13
> **zekopeko said:**
> lol.
that is all.

Oh my mistake, isn't it a [feminine]("http://www.behindthename.com/name/jo") name?

---

### Post by ghindo on 2009-07-13
> **zekopeko said:**
> lol.
that is all.Don't turn this into another LaRoza

---

### Post by zekopeko on 2009-07-13
> **ghindo said:**
> Don't turn this into another LaRoza

not even close. Jo is a dude. Google said so!

P.S. Jo sucks at speed building computers from scratch under pressure and watchful eye of 10's of people ;).

---

### Post by directhex on 2009-07-13
> **zekopeko said:**
> not even close. Jo is a dude. Google said so!

P.S. Jo sucks at speed building computers from scratch under pressure and watchful eye of 10's of people ;).

Now, I think I should point something out.

Some models of Epia have colour-coded headers, and others do not.

If one were, for the sake of argument, building an Epia-based PC in a hurry, then it helps if you know how to turn it on - something you won't know if the headers are not labeled.

And, carrying on that hypothesis, if there were some kind of competition against Spode's Abode, then it wouldn't exactly be fair if two different Epia boards were in use - and that the competition had colour-coded labels whilst you did not.

That is all.

---

### Post by zekopeko on 2009-07-13
> **Swarms said:**
> Oh my mistake, isn't it a [feminine]("http://www.behindthename.com/name/jo") name?

apparently his parents didn't have access to Google at the time :P

---

### Post by directhex on 2009-07-13
> **zekopeko said:**
> apparently his parents didn't have access to Google at the time :P

Jo is my own choice, based on the efficiency savings compared to bloated names like Joe.

Oh, and this is getting grossly off-topic. RHYTHMBOX, ladies!

---

### Post by zekopeko on 2009-07-13
> **directhex said:**
> Jo is my own choice, based on the efficiency savings compared to bloated names like Joe.

Oh, and this is getting grossly off-topic. RHYTHMBOX, ladies!

Yes ma'm, i mean sir!

---

### Post by ronacc on 2009-07-13
theres no topic like an off topic .

---

### Post by ghindo on 2009-07-13
> **directhex said:**
> Jo is my own choice, based on the efficiency savings compared to bloated names like Joe.Tell me about it.  My name is Michael, but I go by "Mi," or "M" for short.  If at all possible, I like to shorten it down to a grunt.  Who has time for the bloat and excess of a full first name?

---

### Post by b3n87 on 2009-07-14
> **KingNeil said:**
> If Rhythmbox has iPod sync built in, that's all that's needed. That will make it as good as iTunes for 99% of users.

DEVELOP IPOD SYNCHRONISATION!

Read the first post....

---

### Post by soapytheclown on 2009-07-14
i did a clean install yesterday to see if this was because of some config setting, but does anyone else have a problem in the latest RB where when changing a song the system volume gets muted?? if i let the track play out and change by itself then its fine but using the media keys or the forward button instantly mutes the volume, ive tested in totem to see if it replicates there but doesnt repeat there.

---

### Post by Craigy90 on 2009-07-14
> **soapytheclown said:**
> i did a clean install yesterday to see if this was because of some config setting, but does anyone else have a problem in the latest RB where when changing a song the system volume gets muted?? if i let the track play out and change by itself then its fine but using the media keys or the forward button instantly mutes the volume, ive tested in totem to see if it replicates there but doesnt repeat there.

Confirmed, but for me it does not mute the volume, it just lowers it way, way down (almost to 0). Could you file a bug report?

---

### Post by quazi on 2009-07-14
My biggest issue with Rhythmbox right now is, for some absurd reason, there's no way to sort playlists within Rhythmbox other than by dragging and dropping songs.  For large playlists this is a pain in the ***.  I can't think of another media player off the top of my head which doesn't let you sort by a few tagged fields.

---

### Post by b3n87 on 2009-07-15
Video of some work being done on the context menu at GoC:

[http://www.youtube.com/watch?v=4fKFQEr3KSs]("http://www.youtube.com/watch?v=4fKFQEr3KSs")

[http://mail.gnome.org/archives/rhythmbox-devel/2009-July/msg00040.html]("http://mail.gnome.org/archives/rhythmbox-devel/2009-July/msg00040.html")

Automatic iPod syncing status:
[http://mail.gnome.org/archives/rhythmbox-devel/2009-July/msg00039.html]("http://mail.gnome.org/archives/rhythmbox-devel/2009-July/msg00039.html")

---

### Post by SushiR on 2009-07-15
> **b3n87 said:**
> Video of some work being done on the context menu at GoC:

[http://www.youtube.com/watch?v=4fKFQEr3KSs]("http://www.youtube.com/watch?v=4fKFQEr3KSs")

Wow, that looks very promising. Any (simple) way to install this version of rhythmbox?

---

### Post by descendent87 on 2009-07-15
looks good, if we could get that and [this](http://www.youtube.com/watch?v=xlPMu8gncfY) added it would be a huge improvement to rhythmbox

---

### Post by Joe_Bishop on 2009-07-16
Omg. The main reason I heard about banshee to replace RB is "banshee looks better". It's ridiculous! And these things make RB slow to start, so I think they are not needed.

---

### Post by b3n87 on 2009-07-16
> **descendent87 said:**
> looks good, if we could get that and [this](http://www.youtube.com/watch?v=xlPMu8gncfY) added it would be a huge improvement to rhythmbox

[http://code.google.com/p/rhythmboxcoverflow/]("http://code.google.com/p/rhythmboxcoverflow/")

---

### Post by b3n87 on 2009-07-16
> **SushiR said:**
> Wow, that looks very promising. Any (simple) way to install this version of rhythmbox?

I dont know if Im honest. You'd have to have a look on the GNOME mailing list

---

### Post by Guillaume86 on 2009-08-06
> **SushiR said:**
> Wow, that looks very promising. Any (simple) way to install this version of rhythmbox?
well if you really want a context pane, i did develop one as a plugin for Exaile 3.x, more like the amarok 1.4 one ;), available in trunk on launchpad...

---

### Post by Enigmatic on 2009-08-19
I find Banshee a bit clunkier to use, though the interface does offer more to the user.

Is there any way to have it highlight the currently playing song? It seems absurd that if I skip to a new song via my keyboard media key it doesn't highlight it and bring it up into view on the library listing. The song progress bar is also painfully small.

Just a few observations from playing with it for a short time.

---

