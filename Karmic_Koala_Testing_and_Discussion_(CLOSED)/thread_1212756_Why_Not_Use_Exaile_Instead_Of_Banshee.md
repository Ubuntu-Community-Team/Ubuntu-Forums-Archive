---
title: "Why Not Use Exaile Instead Of Banshee?"
date: 2009-07-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by woodbj on 2009-07-14
If people are concerned about having Banshee as default and the fact that it's a Mono app why can't Exaile be default?

---

### Post by Joe_Bishop on 2009-07-14
I like it, but it doesn't have inotify support.

---

### Post by Swarms on 2009-07-14
Banshee using mono is not the rational reason people are opposed to it. It is because they are afraid to use anything with that sort of connection to Microsoft.

The reason some people are opposed is that they are not satisfied with the features of Banshee yet. Folderwatching and gapless playback are features some want before a switch is made, some people want the memory footprint to be smaller. (Though it is better than Rhythmbox's when handling large libraries). And the devs of Ubuntu have made a list of stuff that shall be done before a certain deadline, before Banshee can be included.

But when Banshee is in such a fast development, those features and more should be met, the question is when. Read [Jo Shields blog]("http://www2.apebox.org/wordpress/rants/153/") on the subject.

---

### Post by buzzmandt on 2009-07-14
I prefer exhaile too.  
I just wish if we were to keep rythmbox it would get a face lift and equilizer.  What is default it what will be displayed, rythbox looks.... dated.  looks like winamp from 20 years ago (not exactly, just a point to make)

---

### Post by directhex on 2009-07-14
Exaile needs lots of love before it'd be able to take up the "default player" mantle - not least of which is library migration.

Oh, and Exaile is heavier than Banshee, RAMwise. FYI.

---

### Post by zekopeko on 2009-07-14
After abock's post on p.g.o banshee is the only real alternative to rhythmbox.

---

### Post by Joe_Bishop on 2009-07-14
> After abock's post on p.g.o banshee is the only real alternative to rhythmbox.
Banshee in my opinion doesn't have any significant advantage over RB, only huge disadvantages like lack of inotify support, etc. But exaile has - it's amarok inspired interface is very convenient.

---

### Post by descendent87 on 2009-07-14
All 3 have the same library and playing the same song (not doing anything else like importing/scanning directories)
Exaile - 10% CPU - 161MB RAM
Banshee - 10% CPU - 72MB RAM
Rhythmbox - 3% CPU - 45MB RAM
Exaile uses over twice as much RAM as banshee (and nearly 4 times as much as rhythmbox) also the UI looks as bad as rhythmbox

---

### Post by gnomeuser on 2009-07-14
Banshee simply is a much more impressive application and platform in this space and any competitors. While it is not perfect and unlike most people I am not going to whine about wrong features like inotify monitoring (which should be dependent on an indexer instead.. one solution that is easy to tune rather than hacking this functionality into every single application that might benefit from knowing about such metadata but this is a matter for a whole different thread).

The big issues remaining are definitely a11y and documentation. Luckily documentation is something anyone can help with but the accessibility problems are showstoppers for two simply reasons:

1) We should cater to everyone, even the differently abled, this should be a moral and ethical obligation.
2) It's a strict requirement for deployments in places like major enterprises and governments

Doing this in time for Karmic might require a short term solution such as bundling the code plus required changes with Banshee. We have done this before, e.g. I believe f-spot does this frequently as features are slow to merge upstream.

That being said, with everything Banshee has given us and promises to give us I think it would be shameful not to switch now and trust that these issues will be worked out in time for release. Development is swift as it is and progress on a number of the issues raised has progressed (the last time I did a check 25% of the reported concerns from the UDS list were addressed with an additional 50% being in well in progress). 
We should also remember that in the grand scheme Karmic isn't the release to worry about, it is the next LTS. These are the releases we encourage people to deploy in large scale and getting applications changed early would be beneficial. This is not to say that Karmic isn't important, lots of people will run it, but a plea not to expect it to be perfect, to let us live with small temporary regressions. 

Consider it me imploring everyone to look at the great amount we gain rather than the fairly small set of regressions we might have to suffer temporarily as the features trickle into Banshee. They have shown good faith in taking up every issue pointed out to them and have worked hard not just on addressing these issues but continuing the stream of exciting new work as well.

I have every bit of confidence in the Banshee teams ability to bring us what we need. In addition making this switch we get the ability to easily implement additional interfaces (according to Aaron the standard Banshee interface is but a mere 850 lines of code) so if users prefer a different presentation then they can have it with quite little work on their part. Already there is a Muine looking ui, the minimal ui and now Cubano the flashy new netbook deployment style interface. So if someone prefers the Exaile UI then I am sure it can be implemented quite easily on top of Banshee and thus also gain access to a great number of exciting features.

---

### Post by buzzmandt on 2009-07-14
well said,

I really do like banshee. I especially like it more than rythmbox.  It looks much better.  What I think it needs is an equilizer, If it had an 8 or 16 band eq it would be my player of choice.

---

### Post by Joe_Bishop on 2009-07-14
> **gnomeuser said:**
> Banshee simply is a much more impressive application and platform in this space and any competitors. While it is not perfect and unlike most people I am not going to whine about wrong features like inotify monitoring (which should be dependent on an indexer instead.. one solution that is easy to tune rather than hacking this functionality into every single application that might benefit from knowing about such metadata but this is a matter for a whole different thread).

The big issues remaining are definitely a11y and documentation. Luckily documentation is something anyone can help with but the accessibility problems are showstoppers for two simply reasons:

1) We should cater to everyone, even the differently abled, this should be a moral and ethical obligation.
2) It's a strict requirement for deployments in places like major enterprises and governments

Doing this in time for Karmic might require a short term solution such as bundling the code plus required changes with Banshee. We have done this before, e.g. I believe f-spot does this frequently as features are slow to merge upstream.

That being said, with everything Banshee has given us and promises to give us I think it would be shameful not to switch now and trust that these issues will be worked out in time for release. Development is swift as it is and progress on a number of the issues raised has progressed (the last time I did a check 25% of the reported concerns from the UDS list were addressed with an additional 50% being in well in progress). 
We should also remember that in the grand scheme Karmic isn't the release to worry about, it is the next LTS. These are the releases we encourage people to deploy in large scale and getting applications changed early would be beneficial. This is not to say that Karmic isn't important, lots of people will run it, but a plea not to expect it to be perfect, to let us live with small temporary regressions. 

Consider it me imploring everyone to look at the great amount we gain rather than the fairly small set of regressions we might have to suffer temporarily as the features trickle into Banshee. They have shown good faith in taking up every issue pointed out to them and have worked hard not just on addressing these issues but continuing the stream of exciting new work as well.

I have every bit of confidence in the Banshee teams ability to bring us what we need. In addition making this switch we get the ability to easily implement additional interfaces (according to Aaron the standard Banshee interface is but a mere 850 lines of code) so if users prefer a different presentation then they can have it with quite little work on their part. Already there is a Muine looking ui, the minimal ui and now Cubano the flashy new netbook deployment style interface. So if someone prefers the Exaile UI then I am sure it can be implemented quite easily on top of Banshee and thus also gain access to a great number of exciting features.

omg. Please don't make this bloatware the default one.

---

### Post by gnomeuser on 2009-07-14
> **buzzmandt said:**
> well said,

I really do like banshee. I especially like it more than rythmbox.  It looks much better.  What I think it needs is an equilizer, If it had an 8 or 16 band eq it would be my player of choice.

Banshee does have an equalizer (bring it up from the Show menu or by pressing ctrl+e). If there is a problem with it then please file a bug.

---

### Post by ranch hand on 2009-07-14
> **gnomeuser said:**
> Banshee simply is a much more impressive application and platform in this space and any competitors. While it is not perfect and unlike most people I am not going to whine about wrong features like inotify monitoring (which should be dependent on an indexer instead.. one solution that is easy to tune rather than hacking this functionality into every single application that might benefit from knowing about such metadata but this is a matter for a whole different thread).

The big issues remaining are definitely a11y and documentation. Luckily documentation is something anyone can help with but the accessibility problems are showstoppers for two simply reasons:

1) We should cater to everyone, even the differently abled, this should be a moral and ethical obligation.
2) It's a strict requirement for deployments in places like major enterprises and governments

Doing this in time for Karmic might require a short term solution such as bundling the code plus required changes with Banshee. We have done this before, e.g. I believe f-spot does this frequently as features are slow to merge upstream.

That being said, with everything Banshee has given us and promises to give us I think it would be shameful not to switch now and trust that these issues will be worked out in time for release. Development is swift as it is and progress on a number of the issues raised has progressed (the last time I did a check 25% of the reported concerns from the UDS list were addressed with an additional 50% being in well in progress). 
We should also remember that in the grand scheme Karmic isn't the release to worry about, it is the next LTS. These are the releases we encourage people to deploy in large scale and getting applications changed early would be beneficial. This is not to say that Karmic isn't important, lots of people will run it, but a plea not to expect it to be perfect, to let us live with small temporary regressions. 

Consider it me imploring everyone to look at the great amount we gain rather than the fairly small set of regressions we might have to suffer temporarily as the features trickle into Banshee. They have shown good faith in taking up every issue pointed out to them and have worked hard not just on addressing these issues but continuing the stream of exciting new work as well.

I have every bit of confidence in the Banshee teams ability to bring us what we need. In addition making this switch we get the ability to easily implement additional interfaces (according to Aaron the standard Banshee interface is but a mere 850 lines of code) so if users prefer a different presentation then they can have it with quite little work on their part. Already there is a Muine looking ui, the minimal ui and now Cubano the flashy new netbook deployment style interface. So if someone prefers the Exaile UI then I am sure it can be implemented quite easily on top of Banshee and thus also gain access to a great number of exciting features.
I don't really care what they use for default, there are a lot of choices.

That said, this is a well written and reasoned post.  I really thank you for that.

buzzmandt
I did not realize that winamp went back to 1989.

---

### Post by ronacc on 2009-07-14
as an app ,I like banshee (my personal loathing of mono not withstanding) , my main functional concern is that it seems , like many mediaplayers , trying to please eveyone and thus will end up pleasing nobody .

---

### Post by Merk42 on 2009-07-14
Since the Banshee thread is closed, I guess I'll ask it here.  Does Banshee have, or plan to have, a graphical way of navigating albums? iTunes has cover-flow and Windows Media Player has its gridded structure where the albums from the same artist are piled (don't know the name)

> **ronacc said:**
> as an app ,I like banshee (my personal loathing of mono not withstanding) , my main functional concern is that it seems , like many mediaplayers , trying to please eveyone and thus will end up pleasing nobody .

Well that can be said of any application, or any, I guess 'thing', like even the theme.

While I agree that you can't expect to please everyone, I disagree that it ends up pleasing no one.  If you believe this is the case, then how do you decide who to please?

---

### Post by zekopeko on 2009-07-14
> **Merk42 said:**
> Since the Banshee thread is closed, I guess I'll ask it here.  Does Banshee have, or plan to have, a graphical way of navigating albums? iTunes has cover-flow and Windows Media Player has its gridded structure where the albums from the same artist are piled (don't know the name)

Well that can be said of any application, or any, I guess 'thing', like even the theme.

While I agree that you can't expect to please everyone, I disagree that it ends up pleasing no one.  If you believe this is the case, then how do you decide who to please?

[http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0](http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0)

---

### Post by vinutux on 2009-07-14
Exaile is copy crap of Amarok 1.xx version

The main goal of that app is GTK version of amarok v.1xx

Banshee is the best gtk app for muisic exaile is not an option current rhythembox is much more better than exaile.....

and ubuntu people cleared their mono polocy -**[ https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000584.html")**

.

---

### Post by ronacc on 2009-07-14
perhaps no one is a bit too broad , but adding "this" to please A often displeases B because he/she finds it to be wastefull bloat . Using myself as an example I have exactly 0% use for syncronization ( with anything) , playlists , or visualizations (music/podcasts is "background noise" for me not the center of my existance) , I do not want my "collection" organised (much of it is listened to once and then deleted) .

---

### Post by zekopeko on 2009-07-14
> **ronacc said:**
> perhaps no one is a bit too broad , but adding "this" to please A often displeases B because he/she finds it to be wastefull bloat . Using myself as an example I have exactly 0% use for syncronization ( with anything) , playlists , or visualizations (music/podcasts is "background noise" for me not the center of my existance) , I do not want my "collection" organised (much of it is listened to once and then deleted) .

well you aren't a typical user then. and your needs are fulfilled with totem.

---

### Post by ronacc on 2009-07-14
> **zekopeko said:**
> well you aren't a typical user then. and your needs are fulfilled with totem.

nah totem is way too bloated for me , I use MOC :guitar:

---

### Post by elliotn on 2009-07-14
Rythmbox looks like an outdated windows media player lol, it should be skinnable, and ubuntu must crash having 2 default players, make one good looking  player.

---

### Post by buzzmandt on 2009-07-14
I stand corrected, thank you...  hmmm, how'd i miss that?
ummm, nevermind...  I like banshee now, looks good, sounds good, must be good

---

### Post by skierkyles on 2009-07-14
> **zekopeko said:**
> [http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0](http://abock.org/2009/07/14/exciting-updates-on-the-road-to-banshee-2-0)

Ummm I think the banshee devs might be influenced by a certain Microsoft media player....

although it does look really good.

---

### Post by zekopeko on 2009-07-14
> **skierkyles said:**
> Ummm I think the banshee devs might be influenced by a certain Microsoft media player....

although it does look really good.

i just tried the zune software and it's really nice. beautifully themed and just works. the nice thing about banshee is that this new UI is just one of a few. so you can still use the old one. and on the plus side some of the sexiness is going to leak from the new ui to the old ui.

---

### Post by Joe_Bishop on 2009-07-14
Skins? UI inconsistencies? Listen me guy: **default** player **must** looks like the rest of the apps. It's the default player purpose. But this only proves you better use windows, they usually don't take care about consistency, there are many fancy apps ;)

---

### Post by gnomeuser on 2009-07-14
> **buzzmandt said:**
> I stand corrected, thank you...  hmmm, how'd i miss that?
ummm, nevermind...  I like banshee now, looks good, sounds good, must be good


Well I think the fact that you were able to miss that feature despite it being clearly in the menu, has a short cut assigned and was touted in the release note along with screenshots when it was introduced back in.. I believe 1.2 I think says more about the general problem of discoverability in software than it does of you specifically.

Any given piece of software has a great number of features, exposing them correctly is hard so some information is bound to get lost. I think the best way around this is to make the interface fun and simple to navigate so people will go exploring. This is one of the things I like about the Cubano interface, it looks to be very elegant and attractive, something people would be inclined to explore with joy. It is also about doing the right things by default, something I think Banshee generally does well but naturally we can improve. 

In other words, maybe it is our bad. Maybe the equalizer doesn't belong in Banshee but in the volume control applet where one might go looking (as we well to apply the settings to all sound or per stream, or sound card or whatever). Maybe it needs to be in Banshee but exposed in another context. Maybe the correct thing is to have the user be able to define a number of preset eq settings then automatically apply them based on the genre tag, bpm and mirage spectrum analysis so that rock music sounds extra rocky and audiobooks have those perfectly crisp and clear voices. Endless ideas spring to mind on how to make such a small subject be all it can be in the best possible manner.

Don't look at it as your failure, don't look at it as a missing feature. Look at what we could do and try coming up with a proposal for making that come true.

---

### Post by descendent87 on 2009-07-14
> **buzzmandt said:**
> I stand corrected, thank you...  hmmm, how'd i miss that?
ummm, nevermind...  I like banshee now, looks good, sounds good, must be good
haha yeah I've been using banshee for ages and never noticed it had an equalizer, from now on I'll have to make sure I look at all menu's for stuff I've missed on other programs

---

### Post by descendent87 on 2009-07-14
> **skierkyles said:**
> Ummm I think the banshee devs might be influenced by a certain Microsoft media player....

although it does look really good.
yeah but the zune media player is the nicest thing microsoft have ever made, looks really good.

---

### Post by buzzmandt on 2009-07-14
> **descendent87 said:**
> haha yeah I've been using banshee for ages and never noticed it had an equalizer, from now on I'll have to make sure I look at all menu's for stuff I've missed on other programs
Ha...Glad I'm not the only one, I don't feel so bad now. lol
Gnome user, you make some good points.  I was looking for it setting/preferences etc controls, that and I quit using it a little bit of time ago in favor of exhaile and it's eq.  

> **ranch hand said:**
> 
buzzmandt
I did not realize that winamp went back to 1989.
Yeah, kinda why I put not exactly but just to make a point.  I'll be more clear and precise and make sure to put references from now on and also ammend my statement to 1997.

Ref:  [http://en.wikipedia.org/wiki/Winamp](http://en.wikipedia.org/wiki/Winamp)


Edit:  Actually now that I look at the wiki, the original winamp actually looked better than rythmbox does now.... lol, my wording still applies even if not accurate:
[http://en.wikipedia.org/wiki/Winamp#Initial_releases](http://en.wikipedia.org/wiki/Winamp#Initial_releases)

looks like winamp 2 was 2004, looks much better.

Ok, I digress.  not a winamp thread....lol

---

### Post by vinutux on 2009-07-15
> **buzzmandt said:**
> Ha...Glad I'm not the only one, I don't feel so bad now. lol
Gnome user, you make some good points.  I was looking for it setting/preferences etc controls, that and I quit using it a little bit of time ago in favor of exhaile and it's eq.  


Yeah, kinda why I put not exactly but just to make a point.  I'll be more clear and precise and make sure to put references from now on and also ammend my statement to 1997.

Ref:  [http://en.wikipedia.org/wiki/Winamp](http://en.wikipedia.org/wiki/Winamp)


Edit:  Actually now that I look at the wiki, the original winamp actually looked better than rythmbox does now.... lol, my wording still applies even if not accurate:
[http://en.wikipedia.org/wiki/Winamp#Initial_releases](http://en.wikipedia.org/wiki/Winamp#Initial_releases)

looks like winamp 2 was 2004, looks much better.

Ok, I digress.  not a winamp thread....lol

nope...winamp is just a audio player not a music managing app on that days... like audacious did now a days in linux...but apps like banshee, amarock, rhythmbox, itunes are considered music management softwares....

.

---

### Post by BwackNinja on 2009-07-15
For banshee to be included by default, I'd wait until [http://bugzilla.gnome.org/show_bug.cgi?id=520516](http://bugzilla.gnome.org/show_bug.cgi?id=520516) is sorted out in addition to what is already there.

---

### Post by vinutux on 2009-07-15
> **BwackNinja said:**
> For banshee to be included by default, I'd wait until [http://bugzilla.gnome.org/show_bug.cgi?id=520516](http://bugzilla.gnome.org/show_bug.cgi?id=520516) is sorted out in addition to what is already there.

yeh...itz not default in ubuntu 9.10 Karmarik.....hopes 10.4 did it

---

### Post by directhex on 2009-07-15
> **BwackNinja said:**
> For banshee to be included by default, I'd wait until [http://bugzilla.gnome.org/show_bug.cgi?id=520516](http://bugzilla.gnome.org/show_bug.cgi?id=520516) is sorted out in addition to what is already there.

It's got 1.6 as a target milestone, so it should be fixed, well, before 1.6.0

---

### Post by SushiR on 2009-07-31
Exaile 0.3 looks VERY promising. It should used as default player.

---

### Post by directhex on 2009-07-31
> **SushiR said:**
> Exaile 0.3 looks VERY promising. It should used as default player.

Does it support library migration from Rhythmbox? ([hint: no](http://www.exaile.org/wiki/Exaile:Faq#Can_I_import_my_database_from_.3Cinsert_player_here.3E.3F))

---

### Post by wayne_cat on 2009-07-31
> **directhex said:**
> Does it support library migration from Rhythmbox? ([hint: no]("http://www.exaile.org/wiki/Exaile:Faq#Can_I_import_my_database_from_.3Cinsert_player_here.3E.3F"))

a little bit (only rating and play count):

[http://developer.gauner.org/bifroest/](http://developer.gauner.org/bifroest/)

---

### Post by Regenweald on 2009-07-31
> **directhex said:**
> Does it support library migration from Rhythmbox? ([hint: no]("http://www.exaile.org/wiki/Exaile:Faq#Can_I_import_my_database_from_.3Cinsert_player_here.3E.3F"))

When you say library migration, do you mean something more than rescanning a collection ? I don't really meddle with podcasts/online radio and such so if that is a part of library migration i can't really contradict you.

Edit: Well Exaile is back to being my default player, that latest version has shaved at least 30 megs off it's memory consumption and although it still can't compare to rhythmbox's 28megs, 87 is not too bad for all the features it offers as compared to 120-130something. Integration with notifyOSD is there and the player is much more responsive. All in all great work by the Exaile team.

---

### Post by zekopeko on 2009-07-31
> **SushiR said:**
> Exaile 0.3 looks VERY promising. It should used as default player.

Exaile 0.3 looks very promising for more then a year now...

---

### Post by hetx on 2009-07-31
I was unable to reproduce the test results given early in this thread. On my computer Exaile uses less CPU AND less memory running a single song than Banshee doing the same. Maybe I'm just looking in the wrong place, top wont do?

Either way I don't mind Banshee, I've grown attached to it. Exaile put me off back when creating and modifying playlists was as hard as quantum physics upside down. I think Banshee is a good choice, but I'll still have Exaile on my computer as well, just in case Microsoft goes Evil Empire on us.

---

### Post by zekopeko on 2009-07-31
> **Regenweald said:**
> When you say library migration, do you mean something more than rescanning a collection ? I don't really meddle with podcasts/online radio and such so if that is a part of library migration i can't really contradict you.

He means that every rating/play-count/etc are imported from one player into another.

---

### Post by gnomeuser on 2009-07-31
> **Regenweald said:**
> When you say library migration, do you mean something more than rescanning a collection ? I don't really meddle with podcasts/online radio and such so if that is a part of library migration i can't really contradict you.

actual migration. It should parse the existing database and convert it without metadata loss. You should experience no loss of information by switching, meaning your existing podcast subscriptions, ratings, play counts and so on should be migrated.

Not having library migration support from major players (I would say importing from rhythmbox, amarok and banshee on the Linux side and iTunes on the Windows side, songbird would be a nice addition) the player represents a massive regression for users. It also makes it infinitely harder for distributions to seriously consider replacing their existing defaults with them as it would mean severe dataloss for their users when the switch happens.

Not supporting migration is a sign of the developer not caring about the user.

---

### Post by wayne_cat on 2009-07-31
> **gnomeuser said:**
>  
not supporting migration is a sign of the developer not caring about the user.

+1

---

### Post by Katalog on 2009-07-31
I'm still not so sure why there is still such a fuss going on over this since, as far as I know, they still haven't thrown dirt into Rhythmbox' grave yet. And FWIW, Mono or not, I really have no love for either of these players.

---

### Post by zekopeko on 2009-07-31
> **Katalog said:**
> I'm still not so sure why there is still such a fuss going on over this since, as far as I know, they still haven't thrown dirt into Rhythmbox' grave yet. And FWIW, Mono or not, I really have no love for either of these players.

Looks like Banshee won't be included since Banshee devs postponed fixing a11y in 1.6 (a bug in atk# that would break API for other app using it). But I could be wrong (fingers crossed).

---

### Post by Regenweald on 2009-07-31
I have to disagree. It's not a sign that the developer does not care, it's a sign that it has not been done yet. I for one do not need migration, I perfer a fresh start and the fun of rebuilding, but that is just me and i appreciate how important migration is to many users.

I am sure that Banshee has missing features, do they not care or are they working hard to put the best product possible out there ? that sword swings both ways.

---

### Post by directhex on 2009-07-31
> **Regenweald said:**
> I have to disagree. It's not a sign that the developer does not care, it's a sign that it has not been done yet. I for one do not need migration, I perfer a fresh start and the fun of rebuilding, but that is just me and i appreciate how important migration is to many users.

I am sure that Banshee has missing features, do they not care or are they working hard to put the best product possible out there ? that sword swings both ways.

Without migration, an app will not be considered as a replacement for a task by the Desktop Team.

With migration, it becomes a case of objective review and comparison, arguing regressions versus additions.

---

### Post by Regenweald on 2009-07-31
> **directhex said:**
> Without migration, an app will not be considered as a replacement for a task by the Desktop Team.

With migration, it becomes a case of objective review and comparison, arguing regressions versus additions.

I totally see your point. The best player that fits the bill should be included. At the end of the day it's about the user majority isn't it :)

---

### Post by gnomeuser on 2009-07-31
> **zekopeko said:**
> Looks like Banshee won't be included since Banshee devs postponed fixing a11y in 1.6 (a bug in atk# that would break API for other app using it). But I could be wrong (fingers crossed).

This could be fixed by shipping an internal copy of atk# but with that would come things like glib# and other things, a dangerous path to walk down even for a limited time. The responsibly thing there is what the Banshee developers are doing and doing the work now that can be done now and focusing on other matters. 1.6 still represents a lot of improvements.

I think the Banshee team has shown responsibility and good faith, many of the problems have been fixed or has work progressed to such a stage that it will be shortly. The internal design is solid.

Being disabled myself I wouldn't take lacking a11y support lightly but I think it's a limited time regression, we often have those in releases. Karmic is not an LTS (where the rules definitely change). Now is a good time to switch, it would put the media player strategy for Ubuntu is a sweet spot for upcoming releases from the (not yet released) Moblin based release to the default desktop. It would mean an additional 6 months worth of hammering on the software before the next LTS and the community around Banshee will as usual provide updated builds during the lifetime of Karmic.

---

### Post by zekopeko on 2009-07-31
> **gnomeuser said:**
> This could be fixed by shipping an internal copy of atk# but with that would come things like glib# and other things, a dangerous path to walk down even for a limited time. The responsibly thing there is what the Banshee developers are doing and doing the work now that can be done now and focusing on other matters. 1.6 still represents a lot of improvements.

Shipping internals copies might not be a bad idea but that should be up to packagers. Disk space could also be an issue in that case.

---

### Post by dentaku65 on 2009-07-31
I "still" like (and use) Amarok 1.4, in Karmic too with Gnome.
I really have a big problem to choose a different player/music manager; I tried both Banshee and Exaile, they are incomplete compared to Amarok, but promising, expecially Exaile. Banshee seems continuously updated and developed (Exaile is not updated very often); I follow both of them anyway. For sure I'll not use Amarok 2.x :-)

---

### Post by SushiR on 2009-07-31
> **dentaku65 said:**
> Banshee seems continuously updated and developed (Exaile is not updated very often)

[http://www.vimtips.org/2009/07/24/exaile-development-update-july-24-2009/](http://www.vimtips.org/2009/07/24/exaile-development-update-july-24-2009/)
[http://www.vimtips.org/2009/07/27/exaile-might-be-new-xubuntu-default-player/](http://www.vimtips.org/2009/07/27/exaile-might-be-new-xubuntu-default-player/)

---

### Post by dentaku65 on 2009-08-01
> **SushiR said:**
> [http://www.vimtips.org/2009/07/24/exaile-development-update-july-24-2009/](http://www.vimtips.org/2009/07/24/exaile-development-update-july-24-2009/)
[http://www.vimtips.org/2009/07/27/exaile-might-be-new-xubuntu-default-player/](http://www.vimtips.org/2009/07/27/exaile-might-be-new-xubuntu-default-player/)

Interesting links.
But on their site the time for Exaile 0.3 from alpha 1 to alpha 3 takes from 01/09 to 07/09
In any case I like very much Exaile.

Just a question. I've installed the exaile-devel using
```
deb http://ppa.launchpad.net/exaile-devel/ubuntu karmic main
```
but if I do
```
apt-cache policy exaile-devel
```
the output is:
> exaile-devel:
  Installed: 0.2.99.3~bzr1~karmic0
  Candidate: 0.2.99.3~bzr1~karmic0
  Version table:
 *** 0.2.99.3~bzr1~karmic0 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status

Is this version the last 0.3?
:confused:

---

### Post by SushiR on 2009-08-01
> **dentaku65 said:**
> Is this version the last 0.3?
:confused:
It is the latest alpha (0.3.0a3), as you can read on their homepage

---

### Post by Foolishgrunt on 2009-10-08
> **dentaku65 said:**
> Interesting links.
But on their site the time for Exaile 0.3 from alpha 1 to alpha 3 takes from 01/09 to 07/09
I'm not a programmer, so I don't know how relevant this is. But version 0.3 was a complete re-write from version 0.2.14, designed to make future development easier. I'd guess that would make development time for version 0.3 much longer than for regular releases.

Also, the devs said not all of the features from 0.2.14 would be reimplemented in 0.3.0. Some of them would have to wait until 0.3.1, so it might be fairer to reserve final judgment on Exaile's candidacy until after that release.

---

