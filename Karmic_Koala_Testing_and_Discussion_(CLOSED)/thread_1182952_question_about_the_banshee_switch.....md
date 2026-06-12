---
title: "question about the banshee switch...."
date: 2009-06-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rainstride on 2009-06-09
i know we are supposed to switch from rhythmbox to banshee in 9.10, but banshee also handles video. so are we removing totem as well to make banshee our all in one media player?  and also, does anyone know if you will be able to play dvds with it? (that would be awesome, plug-in maybe?;))

---

### Post by super.rad on 2009-06-09
No as far as I know totem is staying.
I don't like using banshee for videos, the libary looks really messy

---

### Post by Incognito-Here on 2009-06-09
Is it final decision to switch? Don't they think about people who want it just works? They want these people to flood this forum with a question: "why tracks don't add to my library", but get some useless features and eyecandies? This player is full of minor glitches and only well suit to geeks who agree to manually add tracks and wait for infinite startup.

---

### Post by Rainstride on 2009-06-09
> **super.rad said:**
> No as far as I know totem is staying.
I don't like using banshee for videos, the libary looks really messy

same here. i wish the videos had thumbnails and a way to group them. so i can group them by show. and have my movies separate from my other stuff.

im not much of a fan of the way the radio page is setup ether.

---

### Post by Incognito-Here on 2009-06-09
Banshee sucks. Other players show only one album: 100% Capolavori.
[[IMG]http://img-fotki.yandex.ru/get/3607/denis-cheremisov.9/0_29303_bace9904_orig[/IMG]]("http://img-fotki.yandex.ru/get/3607/denis-cheremisov.9/0_29303_bace9904_orig")

---

### Post by Rainstride on 2009-06-09
> **Incognito-Here said:**
> Is it final decision to switch? Don't they think about people who want it just works? They want these people to flood this forum with a question: "why tracks don't add to my library", but get some useless features and eyecandies? This player is full of minor glitches and only well suit to geeks who agree to manually add tracks and wait for infinite startup.

it doesn't customise well either. im hopping that the devs will do so work on it before release maybe add the ability to watch folders.  i know they are supposed to work on the major bugs. 

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-default-media-player-choice](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-default-media-player-choice)

i think we will be losing totem though if they go with banshee, it doesn't make since to have two video players by default.

---

### Post by Rainstride on 2009-06-09
this is what i found on the spec page. [https://wiki.ubuntu.com/DesktopTeam/Specs/Karmic/DefaultMediaPlayerChoice](https://wiki.ubuntu.com/DesktopTeam/Specs/Karmic/DefaultMediaPlayerChoice)
they will keeping totem, from what it says anyway.
-------------------------------------------------------------------------

The following feature have to be confirmed in banshee before switching:

* working accessibility ([http://bugzilla.gnome.org/show_bug.cgi?id=533030](http://bugzilla.gnome.org/show_bug.cgi?id=533030))
* support for magnatune
* use the current GNOME libraries (gtkbuilder, gio, etc)
* the rhythmbox importer has to work correctly
* the close and exit behaviour has to be changed to be consistent with the current rhythmbox behaviour or be an option
* the resource usage should be in the same order of magnitude than the rhythmbox one 

Those options would be nice to have:

* library watching
* crossfading effect
* jamendo

-----------------------------------------------------------------------------------------
# Having a small video player is useful, totem will still be used for that
# Rhythmbox and banshee are both good players but banshee has people working full time on it, is moving faster and has feature users expect from a modern music playing applications which rhythmbox doesn't have yet
# Karmic will switch to banshee if the issues which have been listed during the discussion are fixed before the feature freeze, otherwise we will revisit the decision next cycle

---

### Post by sloggerkhan on 2009-06-09
Doesn't matter much. I don't think I can name anyone who uses the default video players out of the box anyhow.

Someone should add proper subtitle support to the list: user scaling and turning on/off of ssa/*** support, custom *** styles.

---

### Post by olskar on 2009-06-09
> **Incognito-Here said:**
> Is it final decision to switch? Don't they think about people who want it just works? They want these people to flood this forum with a question: "why tracks don't add to my library", 

That will probably get added in time for Karmic.

> Banshee sucks. Other players show only one album: 100% Capolavori.

You should edit the ID3-tag so it is correct, then Banshee will show it correct ;)

Add an albumartist to all songs that are shown that way, perhaps "Various Artist".

A lot of music is tagged correctly already and is therefore shown correctly in Banshee.

---

### Post by Amaranth on 2009-06-09
Incognito-Here: You need to calm down. You assume we're going to ignore all the problems and switch because "ooh, shiny!".

The fact is Rhythmbox does not handle albums with multiple artists any better and Banshee is at least still being actively developed so you're more likely to see it fixed there.

As for other problems, if certain problems (mentioned above) are not fixed the change will not happen.

You seem to be comparing Banshee to Amarok 1.4 instead of Rhythmbox, you can't complain Banshee does not have a certain feature when Rhythmbox doesn't have it either. That is not a valid excuse for not switching.

---

### Post by Rainstride on 2009-06-09
im testing banshee 1.5 and so far ill say it could use a pretty good amount of work, but it does have potential. its unable to handle some of my radio stations(they run through xml or something of the sort.). the gui could use a little tweaking.

---

### Post by zekopeko on 2009-06-09
> **Rainstride said:**
> im testing banshee 1.5 and so far ill say it could use a pretty good amount of work, but it does have potential. its unable to handle some of my radio stations(they run through xml or something of the sort.). the gui could use a little tweaking.

file bugs.

---

### Post by zekopeko on 2009-06-09
> **Amaranth said:**
> Incognito-Here: You need to calm down. You assume we're going to ignore all the problems and switch because "ooh, shiny!".

The fact is Rhythmbox does not handle albums with multiple artists any better and Banshee is at least still being actively developed so you're more likely to see it fixed there.

As for other problems, if certain problems (mentioned above) are not fixed the change will not happen.

You seem to be comparing Banshee to Amarok 1.4 instead of Rhythmbox, you can't complain Banshee does not have a certain feature when Rhythmbox doesn't have it either. That is not a valid excuse for not switching.

i'm affraid that incognito-here isn't here to point out banshee's lack/surplus of features/regressions/bugs. he's here to bash banshee because it uses mono. simple as that.

---

### Post by zekopeko on 2009-06-09
totem is still going to be the default video player. but banshee/ubuntu devs could build another interface for banshee to use it as a simple video player without the library component. long term that could be a nice goal and could unify media management in ubuntu.

---

### Post by Rainstride on 2009-06-09
> **Amaranth said:**
> Incognito-Here: You need to calm down. You assume we're going to ignore all the problems and switch because "ooh, shiny!".

The fact is Rhythmbox does not handle albums with multiple artists any better and Banshee is at least still being actively developed so you're more likely to see it fixed there.

As for other problems, if certain problems (mentioned above) are not fixed the change will not happen.

You seem to be comparing Banshee to Amarok 1.4 instead of Rhythmbox, you can't complain Banshee does not have a certain feature when Rhythmbox doesn't have it either. That is not a valid excuse for not switching.

i listed the requirements for switching above. i mainly made this thread to find out weather or not we will be keeping totem. (turns out to be in the specs:D)

while your here though, any opinions on the subject that aren't in the specs? 

i love that banshee has an active community from the start and a setup for plugins, especially since RB seems to be run by one guy at the moment:). ill be interested to see what the plans for the future are if the switch does go through.

---

### Post by Rainstride on 2009-06-09
> **zekopeko said:**
> file bugs.

will do:D.

---

### Post by Amaranth on 2009-06-09
I don't think it would make sense for banshee to be the app that opens when you double click a video file. There is a reason OS X has Quicktime Player even though iTunes plays video. :)

One is for playing a video once, the other is for managing a media library and playing it.

---

### Post by psyke83 on 2009-06-09
I'm confused... where/when/who decided that Banshee has been approved to replaced Rhythmbox (or Totem)? The specification was approved, but I don't see any explicit details. Can someone point me in the right direction?

> **zekopeko said:**
> i'm affraid that incognito-here isn't here to point out banshee's lack/surplus of features/regressions/bugs. he's here to bash banshee because it uses mono. simple as that.

Can't we have a civil discussion here? The fact that Banshee uses Mono is an issue that should be investigated, but indirectly so. Most tests seem to indicate that Banshee uses approximately twice the memory compared to Rhythmbox (with the default plugins loaded by default in each application), and startup time is slightly longer (I haven't benchmarked this myself, but perhaps somebody else has).

This is a concern because Ubuntu has official recommended system requirements. The current recommendation is 384MB of RAM for a "comfortable" experience - will we need to increase that recommendation to account for the higher requirements when using Banshee?

---

### Post by Rainstride on 2009-06-09
> **Amaranth said:**
> I don't think it would make sense for banshee to be the app that opens when you double click a video file. There is a reason OS X has Quicktime Player even though iTunes plays video. :)

One is for playing a video once, the other is for managing a media library and playing it.

sounds right to me.


> **psyke83 said:**
> I'm confused... where/when/who decided that Banshee has been approved to replaced Rhythmbox (or Totem)? The specification was approved, but I don't see any explicit details. Can someone point me in the right direction?



Can't we have a civil discussion here? The fact that Banshee uses Mono is an issue that should be investigated, but indirectly so. Most tests seem to indicate that Banshee uses approximately twice the memory compared to Rhythmbox (with the default plugins loaded by default in each application), and startup time is slightly longer (I haven't benchmarked this myself, but perhaps somebody else has).

This is a concern because Ubuntu has official recommended system requirements. The current recommendation is 384MB of RAM for a "comfortable" experience - will we need to increase that recommendation to account for the higher requirements when using Banshee?

i posted the spec requirement for the switch along with a link in a different post on the first page. as long as it is ready and good enough there supposed to switch it. if not then we keep rhythmbox. 

as for ram:
rhythmbox = 30.7mb while paused and 30.4 while playing(odd..)
banshee   = 36.2mb while paused and 37.8 while playing

so it seems to use a few megs more ram but not really enough to make a big difference.

---

### Post by zekopeko on 2009-06-09
> **Amaranth said:**
> I don't think it would make sense for banshee to be the app that opens when you double click a video file. There is a reason OS X has Quicktime Player even though iTunes plays video. :)

One is for playing a video once, the other is for managing a media library and playing it.

if you re-read my post you will see that banshee can have a number of frontends. creating a simple totem-like player could be done. and i'm guessing that it would have a smaller size on the liveCD.
i'm not saying that banshee should start if you open a movie but a simple player that would use banshee's code/libs.

---

### Post by zekopeko on 2009-06-09
> **Rainstride said:**
> sounds right to me.

i posted the spec requirement for the switch along with a link in a different post on the first page. as long as it is ready and good enough there supposed to switch it. if not then we keep rhythmbox. 

as for ram:
rhythmbox = 30.7mb while paused and 30.4 while playing(odd..)
banshee   = 36.2mb while paused and 37.8 while playing

so it seems to use a few megs more ram but not really enough to make a big difference.

you have to take into account that banshee better manages memory when larger libraries are in question. rhythmbox uses more ram as your library grows while banshee has a better why of managing your library list.

---

### Post by Amaranth on 2009-06-09
I believe the plan was to have Banshee replace Rhythmbox as of Alpha 2 so it would get plenty of testing then if, by Feature Freeze, the required features were not added to Banshee we would switch back.

That may have changed now, I'm not sure.

---

### Post by CarpKing on 2009-06-09
> **zekopeko said:**
> if you re-read my post you will see that banshee can have a number of frontends. creating a simple totem-like player could be done. and i'm guessing that it would have a smaller size on the liveCD.
i'm not saying that banshee should start if you open a movie but a simple player that would use banshee's code/libs.

Don't they both use Gstreamer anyway?  And Totem mostly uses stuff that Gnome needs anyway.  I can't imagine that the Totem-specific parts are much bigger than the hypothetical extra Banshee frontend.

---

### Post by Rainstride on 2009-06-09
> **zekopeko said:**
> you have to take into account that banshee better manages memory when larger libraries are in question. rhythmbox uses more ram as your library grows while banshee has a better why of managing your library list.

i have 1300 songs in my list in rhythmbox...so i guess take what you will from that. 10mb isn't enough to catch my attention, if it was a 30mb difference then i might be a little concerned (my friend only has 192mb of ram:D)

---

### Post by super.rad on 2009-06-09
> **Amaranth said:**
> I believe the plan was to have Banshee replace Rhythmbox as of Alpha 2 so it would get plenty of testing then if, by Feature Freeze, the required features were not added to Banshee we would switch back.

That may have changed now, I'm not sure.

Just did a fresh install from the daily images, still has rhythmbox as default.

---

### Post by bekind2thenoob on 2009-06-09
> **Rainstride said:**
>  (my friend only has 192mb of ram:D)

just because its the default you dont have to use it

I like Banshee btw!

---

### Post by directhex on 2009-06-09
> **Amaranth said:**
> I don't think it would make sense for banshee to be the app that opens when you double click a video file. There is a reason OS X has Quicktime Player even though iTunes plays video. :)

One is for playing a video once, the other is for managing a media library and playing it.

Absolutely. And my feelings mirror yours - a "file" player and "library" player are different apps with different use-cases. If they can share a backend, then great - but the experience is key, and a library player is a poor fit for ad-hoc file playback (just as F-Spot makes no sense as a "replacement" for EOG.

In reply to whomever asked it: the choice for media player was discussed at the Ubuntu Developer Summit in Barcelona, and the general feeling was that Banshee as a library app was most likely to be "best" at some point. The question really is *when*, and that question of when determines whether or not the switch happens in Karmic. If Banshee still has blocker bugs, then the Desktop team will be 100% justified in using Rhythmbox instead - and I think that's the best decision. The right decision is for the "best" app.

---

### Post by gnomeuser on 2009-06-09
I know the Banshee developers have been doing a great deal of work prioritizing the bugs requested in the initial review. I am thus thankful that the switch will be made early so we might unearth little problems on the way.

One thing to keep in mind though, the 1.5.x series is a development release, it is expected to be a touch unstable especially in it's current state. It is however where the focus is right now and commits are happening daily.

Hyperair has set up a ppa with daily git snapshots, that way people can stay onboard and shorten the cycle between bug submission and bug testing. This will hopefully speed up the process of getting problems solved.

I am personally very happy with Banshee 1.5.x so far and I absolutely love the improvements they have done.

---

### Post by bekind2thenoob on 2009-06-09
I was just transfering some music to an mp3 player in banshee while i was reading this thread i copied some flac files across by accident and banshee transcoded them to mp3 ownage! :D

---

### Post by super.rad on 2009-06-09
> **bekind2thenoob said:**
> I was just transfering some music to an mp3 player in banshee while i was reading this thread i copied some flac files across by accident and banshee transcoded them to mp3 ownage! :D

Yeah thats a great feature, found out about it the other day.
All my music on my pc is flac so it was a pain having to convert it to mp3 before putting on my mp3 player

---

### Post by Rainstride on 2009-06-09
> **bekind2thenoob said:**
> just because its the default you dont have to use it

I like Banshee btw!

true, but im not going to stick with rhythmbox if there is no support or development. I like banshee in a lot of ways, but the GUI bothers the hell out of me.(hmm... maybe that can be modded with a plugin...)

---

### Post by olskar on 2009-06-09
Has the fact that banshee takes up less space on the CD been mentioned? :)

---

### Post by Rainstride on 2009-06-09
> **olskar said:**
> Has the fact that banshee takes up less space on the CD been mentioned? :)

true, but that is because there is no documentation of any kind(personally i don't really care, but i know it is doing to piss someone off).

---

### Post by super.rad on 2009-06-09
*waits for mono trolls....* :p

---

### Post by directhex on 2009-06-09
> **olskar said:**
> Has the fact that banshee takes up less space on the CD been mentioned? :)

Much as I'm responsible for that detail getting coverage, it was never really my main argument (merely that space was not an issue). Others have correctly pointed out that the space advantage vanishes to 0 when you add in documentation

---

### Post by sertse on 2009-06-09
Totem is also needed for totem-mozilla, the browser plugin to play media in firefox. I don't think Banshee has that?

---

### Post by Rainstride on 2009-06-09
> **sertse said:**
> Totem is also needed for totem-mozilla, the browser plugin to play media in firefox. I don't think Banshee has that?

your right, i forgot all about that.

---

### Post by olskar on 2009-06-09
> **directhex said:**
> Much as I'm responsible for that detail getting coverage, it was never really my main argument (merely that space was not an issue). Others have correctly pointed out that the space advantage vanishes to 0 when you add in documentation

Ah, I didn't know that. 

However I think it's still a pretty common misunderstanding that Banshee will take more space than Rhythmbox because of it's monodeps. I guess that isn't true at least :)

---

### Post by Rainstride on 2009-06-09
> **olskar said:**
> Ah, I didn't know that. 

However I think it's still a pretty common misunderstanding that Banshee will take more space than Rhythmbox because of it's monodeps. I guess that isn't true at least :)

doesn't tomboy use a few of the same monodeps? or do they completely different sets?

---

### Post by psyke83 on 2009-06-09
In a way, it may be an advantage that Banshee uses Mono (as we have the core libraries in a default installation already). As long as newer versions of Banshee have reduced memory usage, I think it's worth considering it for inclusion as the default audio player. 

However, to replace Banshee with Totem seems pretty silly, IMHO. As someone else said, even Apple recognises the need to keep QuickTime Player and iTunes distinct, as these applications serve different core purposes.

---

### Post by directhex on 2009-06-09
> **Rainstride said:**
> doesn't tomboy use a few of the same monodeps? or do they completely different sets?

They share a bunch, which accounts for some of the space savings. But they also both have some of their own.

---

### Post by zekopeko on 2009-06-09
> **psyke83 said:**
> In a way, it may be an advantage that Banshee uses Mono (as we have the core libraries in a default installation already). As long as newer versions of Banshee have reduced memory usage, I think it's worth considering it for inclusion as the default audio player. 

However, to replace Banshee with Totem seems pretty silly, IMHO. As someone else said, even Apple recognises the need to keep QuickTime Player and iTunes distinct, as these applications serve different core purposes.

wait, did nobody understood what i meant by a new frontend for banshee?
banshee uses gstreamer. therefore it can play all formats of audio/video that gstreamer can. banshee is also modular. there is already a different UI for it out there and another (based on clutter/or perhaps moonlight?) is being developed.
creating a new UI just for video playback could "easily" be done.
so it would have a common backend but not a common interface. and library wouldn't even be used if it's to replace totem.
i would love something along the lines of the new quicktime x player. minimalistic with sharing/basic editing and perhaps youtube/bbc integration that totem has that could be used by both this new video UI and the good old banshee.

---

### Post by psyke83 on 2009-06-09
> **zekopeko said:**
> wait, did nobody understood what i meant by a new frontend for banshee?
banshee uses gstreamer. therefore it can play all formats of audio/video that gstreamer can. banshee is also modular. there is already a different UI for it out there and another (based on clutter/or perhaps moonlight?) is being developed.
creating a new UI just for video playback could "easily" be done.
so it would have a common backend but not a common interface. and library wouldn't even be used if it's to replace totem.
i would love something along the lines of the new quicktime x player. minimalistic with sharing/basic editing and perhaps youtube/bbc integration that totem has.

I know this, but you seem to have missed my point. iTunes uses the same QuickTime presentation layer as Quicktime Player, but they kept the Player application separate for a reason.

---

### Post by olskar on 2009-06-09
> **psyke83 said:**
> In a way, it may be an advantage that Banshee uses Mono (as we have the core libraries in a default installation already). As long as newer versions of Banshee have reduced memory usage, I think it's worth considering it for inclusion as the default audio player. 

However, to replace Banshee with Totem seems pretty silly, IMHO. As someone else said, even Apple recognises the need to keep QuickTime Player and iTunes distinct, as these applications serve different core purposes.

It's funny how you say "even apple", they aren't exactly noobs in the field of usability ;)

---

### Post by psyke83 on 2009-06-09
> **olskar said:**
> It's funny how you say "even apple", they aren't exactly noobs in the field of usability ;)

Heh. I said "even", because the analogy of iTunes vs Quicktime has a direct equivalence in regards to Totem/Banshee using GStreamer; i.e. there is an underlying framework that is shared.

---

### Post by Rainstride on 2009-06-09
> **psyke83 said:**
> I know this, but you seem to have missed my point. iTunes uses the same QuickTime presentation layer as Quicktime Player, but they kept the Player application separate for a reason.

he is saying that we basically do the same thing. where we make a second front end that would be just like totem, and separate from banshee, but they would use the same back end and parts to work. (might save space to.)

---

### Post by psyke83 on 2009-06-09
> **Rainstride said:**
> he is saying that we basically do the same thing. where we make a second front end that would be just like totem, and separate from banshee, but they would use the same back end and parts to work. (might save space to.)

Why? Totem is lightweight, Banshee is not. The advantage of Totem is that it starts fast and it has a specific purpose (to play media, with optional playlists and a few extra features, but to hell with more advanced features). Creating a "lighter" interface for Banshee will not make the application as a whole more lightweight - it will make it even more bloated.

Note: I'm not criticizing Banshee or Mono, just pointing out that it's a more complex application (and geared more towards management of an audio collection, let's be honest).

---

### Post by zekopeko on 2009-06-09
> **Rainstride said:**
> he is saying that we basically do the same thing. where we make a second front end that would be just like totem, and separate from banshee, but they would use the same back end and parts to work. (might save space to.)

what s/he said :D

---

### Post by zekopeko on 2009-06-09
> **psyke83 said:**
> Why? Totem is lightweight, Banshee is not. The advantage of Totem is that it starts fast and it has a specific purpose (to play media, with optional playlists and a few extra features, but to hell with more advanced features).

consider that banshee pulls a lot of stuff that the new UI wouldn't have to. no library, only minimal set of plugins.

---

### Post by Rainstride on 2009-06-09
> **psyke83 said:**
> Why? Totem is lightweight, Banshee is not. The advantage of Totem is that it starts fast and it has a specific purpose (to play media, with optional playlists and a few extra features, but to hell with more advanced features). Creating a "lighter" interface for Banshee will not make the application as a whole more lightweight - it will make it even more bloated.

Note: I'm not criticizing Banshee or Mono, just pointing out that it's a more complex application (and geared more towards management of an audio collection, let's be honest).

agreed, totem is pretty much my favourite video player. 

but your still slightly misunderstanding what he was saying. it would not be banshee playing the video, the program would use ONLY the audio/video playback framwork that banshee uses, and NOTHING ELSE. it would not load the plugins, or the normal front-end for banshee. 

it would be about the same as changing totem to use the libs and parts that enable video playback in banshee. 

the point would be to make it so you would only need the stuff for banshee to do both jobs. witch would probably save space. 

(kind of like two themes using the same engine;))

---

### Post by mc4100 on 2009-06-09
> **Rainstride said:**
> It would not be banshee playing the video, the program would use ONLY the audio/video playback framwork that banshee uses, and NOTHING ELSE.
I think I must be missing something: you're describing exactly the functioning of the gstreamer. Which doesn't need banshee to run. And already has a near-perfect video implementation with totem.
How is banshee even involved?
The best I can think of is moving all of the totem UI and features into banshee, whilst separating it from the music stuff and then giving it a name. What's the point in that?

---

### Post by psyke83 on 2009-06-09
> **Rainstride said:**
> agreed, totem is pretty much my favourite video player. 

but your still slightly misunderstanding what he was saying. it would not be banshee playing the video, the program would use ONLY the audio/video playback framwork that banshee uses, and NOTHING ELSE. it would not load the plugins, or the normal front-end for banshee. 

it would be about the same as changing totem to use the libs and parts that enable video playback in banshee. 

the point would be to make it so you would only need the stuff for banshee to do both jobs. witch would probably save space. 

(kind of like two themes using the same engine;))

Totem uses the GStreamer framework to do the heavy lifting with regards to audio and video playback; so does Banshee. I didn't misunderstand anything that he said. Banshee is already pretty modular (take a look at the range of features provided by plugins), but it's still a lot more complex than Totem when all of these plugins are disabled.

---

### Post by zekopeko on 2009-06-09
> **mc4100 said:**
> I think I must be missing something: you're describing exactly the functioning of the gstreamer. Which doesn't need banshee to run. And already has a near-perfect video implementation with totem.
How is banshee even involved?

banshee also uses gstreamer. you would simply build upon the foundations of banshee to create this totem-like interface. and with it you get plugins and tighter media integration.

know i don't know if banshee's foundation can be used as i imagined this new UI so this is simply hypothetical at this point (until a banshee dev comes and shoots it down :D).

you would use this UI to open video and audio files from nautilus. it would provide all of totems abilities (but i hope in a far sexier interface) and you could have some basic plugins like youtube/BBC/some-streaming-service. 
so let's say you load a rather nice movie and like it so much that you decide that you would add it to banshee's library. you can simply click a button in the UI and it would load the rest of banshee and auto add it to your library.

the point that shouldn't be forgotten is that banshee 1.x isn't a music player. it's a media player. it's geared toward audio for now but it can easily be extended to consolidate all your media files in one location.

imagine at one point having your anime/movies/series loaded in banshee. it would automatically fetch all metadata like actors/summary/genre from the net.

that's what i'm thinking and the new UI to replace totem could be a step in this direction.

---

### Post by Rainstride on 2009-06-09
> **mc4100 said:**
> I think I must be missing something: you're describing exactly the functioning of the gstreamer. Which doesn't need banshee to run. And already has a near-perfect video implementation with totem.
How is banshee even involved?
The best I can think of is moving all of totem into banshee, separating it from the music stuff and giving it a name. What's the point in that?

hmm...i think i slightly mistyped... i was talking about the libs and things that take advantage of the gstreamer framework and run the program it self. as far as i know totem uses completely different libs and deps than banshee(i could be wrong, i don't tabs on this stuff..) the point would be to make it so you only need the banshee libs and other files. 

hmm...im having to explain quite a bit of something i never suggested:D.

---

### Post by zekopeko on 2009-06-09
> **Rainstride said:**
> hmm...i think i slightly mistyped... i was talking about the libs and things that take advantage of the gstreamer framework and run the program it self. as far as i know totem uses completely libs and deps than banshee(i could be wrong, i don't tabs on this stuff..) the point would be to make it so you only need the banshee libs and other files. 

hmm...im having to explain quite a bit of something i never suggested:D.

well i guess the "mistake" is mine since this only popped in my head yesterday. i don't know how feasible all of this is or if it can be done the way i imagined it since i have practically no knowledge how banshee's internals work.

---

### Post by Rainstride on 2009-06-09
> **psyke83 said:**
> Totem uses the GStreamer framework to do the heavy lifting with regards to audio and video playback; so does Banshee. I didn't misunderstand anything that he said. Banshee is already pretty modular (take a look at the range of features provided by plugins), but it's still a lot more complex than Totem when all of these plugins are disabled.

your talking about loading banshee without plugins, im talking about not having the librarys or anything like that load. it would be just the playback area and playlist just like totem. as stripped as can be. completely minimal.

---

### Post by directhex on 2009-06-09
Here's an idea:

Why not leave out talk of replacing Totem until there's a viable alternative? Whether that's a new Banshee client to ship alongside Nereid, or something totally different, Totem is the best app in its class right now, and there isn't a line of code at the Banshee end which threatens that. If anyone wants to code something in any direction for this task, give it a shot!

---

### Post by Rainstride on 2009-06-09
> **zekopeko said:**
> well i guess the "mistake" is mine since this only popped in my head yesterday. i don't know how feasible all of this is or if it can be done the way i imagined it since i have practically no knowledge how banshee's internals work.

i wish we had a banshee dev in here, this would be easier. :D

---

### Post by Rainstride on 2009-06-09
> **directhex said:**
> Here's an idea:

Why not leave out talk of replacing Totem until there's a viable alternative? Whether that's a new Banshee client to ship alongside Nereid, or something totally different, Totem is the best app in its class right now, and there isn't a line of code at the Banshee end which threatens that. If anyone wants to code something in any direction for this task, give it a shot!

its called brainstorming. its not like this is going to cause totem to change any time soon, or ever for that matter. we're just looking at future possibility's at what COULD be made maybe.

---

### Post by Incognito-Here on 2009-06-10
> You should edit the ID3-tag so it is correct, then Banshee will show it correct 
no id3v2, it's flac ;)
And I said other players, rhythmbox for example, shows only one album. I don't  want to edit metadata myself because of the buggyware ;)

---

### Post by Incognito-Here on 2009-06-10
<snip> 
Banshee is a library manager? Hahaha!
It even can't watch it's directory.

---

### Post by 23meg on 2009-06-10
Please refrain from personal/mass attacks and keep on topic.

---

### Post by Incognito-Here on 2009-06-10
Read this: [http://celettu.wordpress.com/2008/06/15/banshee-beyond-the-first-looks/]("http://celettu.wordpress.com/2008/06/15/banshee-beyond-the-first-looks/")
Nothing has changed since that time, it's as yet half-ready.

---

### Post by Incognito-Here on 2009-06-10
For example: the fact the tags are "improper" doesn't prevent rhythmbox to show this album as ONE album
[[IMG]http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_29330_16ce3301_orig[/IMG]]("http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_29330_16ce3301_orig")

---

### Post by ranch hand on 2009-06-10
Well, I like RB quite a bit.  Use it on my KDE OSs.

That said, I hope it is on 9.10alph2 so I can play with it.  I am on 9.04 right now and may install it here.

RB has its limitations but it is easy to use and set up the way I like.  As has been pointed out, if we don't like banshee we don't have to use it.

We so have a lot of choice here and a new default would really not be earth shattering.

---

### Post by zekopeko on 2009-06-10
> **Incognito-Here said:**
> For example: the fact the tags are "improper" doesn't prevent rhythmbox to show this album as ONE album
[[IMG]http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_29330_16ce3301_orig[/IMG]]("http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_29330_16ce3301_orig")

i'm gonna guess that you didn't report this as a potential bug/wishlist...

and just because you think a improperly tagged album should be presented in a way a properly tagged one would be doesn't mean you are correct.

---

### Post by Incognito-Here on 2009-06-10
No, I did. Several times, but they replied something similar to the guy in this thread.

---

### Post by tom56 on 2009-06-10
> **Incognito-Here said:**
> For example: the fact the tags are "improper" doesn't prevent rhythmbox to show this album as ONE album
[[IMG]http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_29330_16ce3301_orig[/IMG]]("http://img-fotki.yandex.ru/get/3503/denis-cheremisov.9/0_29330_16ce3301_orig")

Then Rhythmbox is buggy. Because the way it does it means if I have two albums with the same name but are correctly tagged as having different Album Artists it will show them as one. Banshee thinks something is one album if all the tracks have the same "Album Artist" and "Album Title". Note that "Album Artist" is separate from "Track Artist".

---

### Post by ushimitsudoki on 2009-06-10
I put my thoughts down on this here:
[http://meandubuntu.wordpress.com/2009/06/10/disinformation-disinfected-pt-3-banshee-in-ubuntu/](http://meandubuntu.wordpress.com/2009/06/10/disinformation-disinfected-pt-3-banshee-in-ubuntu/)

Read the whole thing if you like (and point out flaws in my arguments), but the jist of it is I think this whole Banshee push is based on 3 major lies:

1. Banshee saves space.
2. Rhythmbox is dead.
3. Rhythmbox doesn't scale.

And a few dishonest arguments:

1. Rhythmbox isn't a good media player.
2. Banshee has more features.
3. All pro-Rhythmbox messages are FUD.

---

### Post by Incognito-Here on 2009-06-10
Oh thank god, one smart people here!

---

### Post by Incognito-Here on 2009-06-10
> Then Rhythmbox is buggy. Because the way it does it means if I have two albums with the same name but are correctly tagged as having different Album Artists it will show them as one. Banshee thinks something is one album if all the tracks have the same "Album Artist" and "Album Title". Note that "Album Artist" is separate from "Track Artist".
*<snip>* The situation "One album, different artists" is very widespread. But I've never met two different albums with a same name. If I met, I just use filter by artist ;)
So, rhythmbox approach is the best, as well as any amateurish stuff on mono should be thrown from the default install.

---

### Post by zekopeko on 2009-06-10
> **ushimitsudoki said:**
> I put my thoughts down on this here:
[http://meandubuntu.wordpress.com/2009/06/10/disinformation-disinfected-pt-3-banshee-in-ubuntu/](http://meandubuntu.wordpress.com/2009/06/10/disinformation-disinfected-pt-3-banshee-in-ubuntu/)

Read the whole thing if you like (and point out flaws in my arguments), but the jist of it is I think this whole Banshee push is based on 3 major lies:

1. Banshee saves space.
2. Rhythmbox is dead.
3. Rhythmbox doesn't scale.

And a few dishonest arguments:

1. Rhythmbox isn't a good media player.
2. Banshee has more features.
3. All pro-Rhythmbox messages are FUD.

3 major "lies":

1. the point of the post was to say that if you take RB out of the liveCD and put banshee you get basically no difference. what it does is point out that banshee is no more "bloated" as RB

2. RB is frozen "in time". there are some improvements that are being made but the lead developer said it him self that some bad design decisions limit RB. i'm talking here about the core stuff upon which plugins are built. banshee on the other hand was rewritten from scratch with a look toward future. it's highly modularized, it has excellent foundations, it plays video and is marginally heavier on resources. not to mention that by looking banshee's bugzilla you can see that the activity is far greater on banshee's page then RB's. not to mention that there are 11 devs working on banshee while only 4 are listed on RB's page.

3. Banshee also scales. the point of the scaling argument is that banshee has to load all of your library metadata into RAM to work with it's item list widget, while banshee just displays the currently seen songs/videos +10 in either direction for nicer scrolling while not having a larger RAM footprint depending on the size of your library

"few dishonest arguments":

1. RB isn't a media player. it's an audio player. banshee is a media player. why? well because media isn't just audio but also video. and banshee plays that. from my perspective RB is a decent audio player.

2. this is one is hard to argue since one man's feature is another man's bug. but i will say that banshee provides a richer media experience. recommendations are one of the selling points. i think that the new 1.6 will have wiki look-up for artists. a youtube plugin was announced on the mailing list. it handles video. also audio and video podcasts. has a nice iPod/DAP support etc.

3. RB shortcomings should be exposed and judged. but also it's merits. the point is that the end user should be provided with a better ubuntu experience. if it's RB so be it. but my money is on banshee.

---

### Post by Rainstride on 2009-06-10
there's a whole lot of love in this thread:D.

the change has not and may not happen. so lets not bother with a flame war just yet.;)

---

### Post by xebian on 2009-06-10
No wonder Fedora11 does not have banshee???

---

### Post by directhex on 2009-06-10
> **xebian said:**
> No wonder Fedora11 does not have banshee???

[https://admin.fedoraproject.org/pkgdb/packages/name/banshee](https://admin.fedoraproject.org/pkgdb/packages/name/banshee)

---

### Post by super.rad on 2009-06-10
> **xebian said:**
> No wonder Fedora11 does not have banshee???
Fedora 11 doesn't include mono or any programs using it, not sure if it's due to space or other reasons

---

### Post by psyke83 on 2009-06-10
> **super.rad said:**
> Fedora 11 doesn't include mono or any programs using it, not sure if it's due to space or other reasons

Oddly enough, the Fedora Live CD doesn't even include OpenOffice (they ship with Abiword instead). The fact that they don't ship with Banshee may have nothing to do with objections to Mono (other than its size on the CD).

I get the impression that the Fedora Live CD is more of a toy (but a useful toy nonetheless) - they seem to put more effort into the traditional installation DVD.

---

### Post by zekopeko on 2009-06-10
> **super.rad said:**
> Fedora 11 doesn't include mono or any programs using it, not sure if it's due to space or other reasons

probably because red hat uses fedora as a testing ground for its future enterprise desktop. and red hat doesn't like to risk it. dumb argument but meh...
little "gossip": that's why gnomeuser (aka David Nielsen) defected. 'cause fedora didn't like mono. those monophobs!

---

### Post by super.rad on 2009-06-10
> **psyke83 said:**
> Oddly enough, the Fedora Live CD doesn't even include OpenOffice (they ship with Abiword instead). The fact that they don't ship with Banshee may have nothing to do with objections to Mono (other than its size on the CD).

I get the impression that the Fedora Live CD is more of a toy (but a useful toy nonetheless) - they seem to put more effort into the traditional installation DVD.

I love the fact they include abiword and not OO, first thing I do on anyother install is remove OO and install abiword

---

### Post by psyke83 on 2009-06-10
> **super.rad said:**
> I love the fact they include abiword and not OO, first thing I do on anyother install is remove OO and install abiword

Yes, but it's not a complete Office suite - you need to include Gnumeric and other applications to get feature parity. Having a complete suite for all users seems more appropriate...

---

### Post by directhex on 2009-06-10
> **psyke83 said:**
> Yes, but it's not a complete Office suite - you need to include Gnumeric and other applications to get feature parity. Having a complete suite for all users seems more appropriate...

I wouldn't use Gnumeric. It's from that evil Mono guy. It's probably full of patents.

---

### Post by ghindo on 2009-06-10
> **directhex said:**
> I wouldn't use Gnumeric. It's from that evil Mono guy. It's probably full of patents.Yeah, I heard about that.  I also heard that he worked on GNOME too, so we should all probably stay away from that.

---

### Post by psyke83 on 2009-06-10
> **directhex said:**
> I wouldn't use Gnumeric. It's from that evil Mono guy. It's probably full of patents.

Let's not even *joke* about Mono anymore, it's getting ridiculous. There are enough [anti-Mono trolls]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-June/008447.html") out there already ;).

By the way, I wasn't aware that Gnomeric used Mono and that's not why I mentioned it. Abiword and Gnomeric are fine applications, but OpenOffice has their functionality *in addition* to presentation and database applications. I think that Fedora's DVD distribution uses OpenOffice by default, so it was probably a space issue on their Live CD. Anyway, this is off topic as it's got nothing to do with the Banshee switch.

---

### Post by super.rad on 2009-06-10
> **psyke83 said:**
> Yes, but it's not a complete Office suite - you need to include Gnumeric and other applications to get feature parity. Having a complete suite for all users seems more appropriate...

yeah I understand why OO is installed, just that I don't need a full suite as I don't often use a word processor but nice to have one just incase which is why I just use abiword
but yeah lets get back on topic.
After spending about 2 hours scanning my music collection mirage is finished, really good plugin just a shame it'll probably take about another 2 hours to scan all my music again next time I add an album

---

### Post by psyke83 on 2009-06-10
> **super.rad said:**
> yeah I understand why OO is installed, just that I don't need a full suite as I don't often use a word processor but nice to have one just incase which is why I just use abiword

Indeed. I always considered Abiword's advantage to be its lower system requirements (memory), which is especially helpful for older machines. Older machines should probably use a lighter derivative such as Xubuntu, though.

---

### Post by ghindo on 2009-06-10
> **psyke83 said:**
> Let's not even *joke* about Mono anymore, it's getting ridiculous. There are enough [anti-Mono trolls]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-June/008447.html") out there already ;).Oh dear.  How is this man allowed to post on the mailing list?

---

### Post by zekopeko on 2009-06-10
> **super.rad said:**
> yeah I understand why OO is installed, just that I don't need a full suite as I don't often use a word processor but nice to have one just incase which is why I just use abiword
but yeah lets get back on topic.
After spending about 2 hours scanning my music collection mirage is finished, really good plugin just a shame it'll probably take about another 2 hours to scan all my music again next time I add an album

why would it need to scan your music again? it will just scan the album you added.

---

### Post by super.rad on 2009-06-10
great, didn't know it did that. As banshee doesn't watch folders I have to rescan the libary everytime I add a new album so assumed I'd have to do the same with mirage

---

### Post by zekopeko on 2009-06-10
> **ghindo said:**
> Oh dear.  How is this man allowed to post on the mailing list?

i guess freedom of speech? suck sometimes. ah well... nature needs sheep.

oh and the worst is that "mark" aka troll_1 and a co-worker (i think) of one of the people involved reported him to his boss for posting (not on company time BTW). talk about evil and petty.

---

### Post by zekopeko on 2009-06-10
> **super.rad said:**
> great, didn't know it did that. As banshee doesn't watch folders I have to rescan the libary everytime I add a new album so assumed I'd have to do the same with mirage

there will be a plugin for 1.6 for folder watching. woot!

you can get it from gnome bugzilla i think (if you want to try it out).

---

### Post by Rainstride on 2009-06-10
> **zekopeko said:**
> there will be a plugin for 1.6 for folder watching. woot!

you can get it from gnome bugzilla i think (if you want to try it out).

cool,im going to have to find that.

---

### Post by ronacc on 2009-06-11
Is there a simple audio player left out there ? by simple I mean one that does NOT make playlists , does NOT hunt for album art , does NOT do visualizations, one that does not even remember what I played last . In other words one that only plays what I point it at and then does nothing else until I point it at the next thing I want played .

---

### Post by RAOF on 2009-06-11
> **ronacc said:**
> Is there a simple audio player left out there ? by simple I mean one that does NOT make playlists , does NOT hunt for album art , does NOT do visualizations, one that does not even remember what I played last . In other words one that only plays what I point it at and then does nothing else until I point it at the next thing I want played .

Totem.  Well, apart from the visualisations bit, but you don't *have* to have them enabled.  But is that really what you want from a music player?

---

### Post by yoasif on 2009-06-11
> **ronacc said:**
> Is there a simple audio player left out there ? by simple I mean one that does NOT make playlists , does NOT hunt for album art , does NOT do visualizations, one that does not even remember what I played last . In other words one that only plays what I point it at and then does nothing else until I point it at the next thing I want played .[moc]("http://moc.daper.net/") does what you want.

---

### Post by ronacc on 2009-06-11
@ RAOF  yes it is .

@ yoasif  thanks I'll give it a try .

---

### Post by ronacc on 2009-06-11
just for grins I  ran moc ,banshee and rythmbox on the same song , usages are taken from TOP 1/2 way through the playback so usages should have stabilized .
moc     CPU 2%    mem 0.1%    pulseaudio  cpu 1%  mem 0.2%        totals cpu 3%    mem 0.3%
banshee   CPU 8%   mem 1.8%   Pulseaudio  cpu 8%  mem 0.3%        totals cpu 16%   mem 2.1%  
rythmbox   CPU 5%  mem 1.3%   pulseaudio  CPU 8%  mem 0.3%        Totals cpu 13%   mem 1.6%

I wonder why rythmbox and banshee cause pulse to use so much more cpu ? I ran moc twice and the figures were the same the second time also .

---

### Post by gnomeuser on 2009-06-11
> **ronacc said:**
> just for grins I  ran moc ,banshee and rythmbox on the same song , usages are taken from TOP 1/2 way through the playback so usages should have stabilized .
moc     CPU 2%    mem 0.1%    pulseaudio  cpu 1%  mem 0.2%        totals cpu 3%    mem 0.3%
banshee   CPU 8%   mem 1.8%   Pulseaudio  cpu 8%  mem 0.3%        totals cpu 16%   mem 2.1%  
rythmbox   CPU 5%  mem 1.3%   pulseaudio  CPU 8%  mem 0.3%        Totals cpu 13%   mem 1.6%

I wonder why rythmbox and banshee cause pulse to use so much more cpu ? I ran moc twice and the figures were the same the second time also .

You forgot the crucial variables.. how much memory do you have and what is the size of your library.

Additional measurements done by directhex:
[http://www2.apebox.org/wordpress/wp-content/gallery/00-single/mediaplayers.png](http://www2.apebox.org/wordpress/wp-content/gallery/00-single/mediaplayers.png)

---

### Post by ronacc on 2009-06-11
for this comparison I did not beleive that total mem available was crucial since I merely wished to show the % difference , for what it is worth ram = 4GB  cpu = AMD64X2 4600  video = nvidia 7600gs with 185.18.08 driver ,system is gmome 64bit, banshee library = 0 files , rythmbox library = 2 files . visualizations were off for the test , rythmbox and banshee were started from nautilus "open with other application ", moc was started from gnome terminal .

---

### Post by tom56 on 2009-06-13
[QUOTE=Incognito-Here;7432268]The situation "One album, different artists" is very widespread./QUOTE]

But you're missing the point. I have albums with more than one artist and Banshee shows them as one no trouble, because they are correctly tagged. What you are saying is equivalent to insisting that Banshee should show your MP3s under Bob Dylan, even though you've tagged them as being the Spice Girls.

Having checked, Rhythmbox and Banshee seem to do it exactly the same (i.e. according to the Album Artist tag) so I guess you must be using an old version of Banshee.

---

