---
title: "Is empathy ready to replace pidgin"
date: 2009-05-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-05-10
There's already idea on brainstorm concerning this issue
[http://brainstorm.ubuntu.com/idea/11705/](http://brainstorm.ubuntu.com/idea/11705/)
since missed the JJ, time for round two.

Would you like to see this implemented in KK.

Empathy is the default IM for gnome, so makes sense to replace pidgin.

This is also a re-occuring debate, but what the heck, let's throw it in anyway :)

---

### Post by gnomeuser on 2009-05-10
I haven't used Pidgin in 1½-2 years, empathy is very stable for me. It does many of the things I care about, like pidgin it still lacks webcam and voip support for msn. It lacks custom emoticons and crypto/OTR support which is present in pidgin, however it is just so damn slick in use.

I love empathy, I don't think it is the end all be all solution, in fact I think we need to move away from the whole IM as a separate application and move towards more integration with the DE. I think empathy is a good step in that direction.

I think Empathy is ready, however instead of having a a prolonged flamewar I think we should work towards a consistent set of bugs that empathy must and should fix to be the default.

amongst these I would definitely have:

MUST: migrate accounts, logs and contacts from pidgin
SHOULD: (n/a)
NICE: Webcam support (at least for jabber, bonus for MSN)
NICE: VoIP support (at least for jabber, bonus for MSN)
NICE: OTR and crypto support
NICE: Extension system

If we can reach all MUST requirements for Koala then we should switch now (or as soon as possible) and have extended exposiour early on. We can accept temporary regressions. 

I believe this to be the most honest approach and that it will give upstream a concrete set of improvements to target. We should avoid moving the goal post and instead set a hard set of must haves, everything beyond that is nice to have or should have items we can live without for a short period of time (say till a SRU or Koala +1). Additional features such as geolocation are bonuses we shouldn't disregard.

---

### Post by puccaso on 2009-05-10
i can never get empathy to connect to msn..

how can it be reaady!? psh..

---

### Post by rajeev1204 on 2009-05-10
Dont like empathy .The UI doenst make sense to me at all.Looks incomplete to me.

---

### Post by Gourgi on 2009-05-10
> **rajeev1204 said:**
> Dont like empathy .The UI doenst make sense to me at all.Looks incomplete to me.

+1 for that.

also i didn't like empathy as an irc client but pidgin is doing a great job there!
also i think that encryption should be a MUST! and not NICE! but nothing for this in roadmap [http://live.gnome.org/Empathy/Roadmap](http://live.gnome.org/Empathy/Roadmap) :(

---

### Post by super.rad on 2009-05-10
Yes I'd say it's ready to replace pidgin, been using it for a while now. Much prefer it over pidgin and haven't had any problems with it.
One feature I would like would be new mail notification like in pidgin.

---

### Post by tgpraveen on 2009-05-10
i also think we should replace pidgina nd get empathy in.
in 2.28 release they will have google video caht support. jabber and sip already have video caht.
geolocation features will be major feature in 2.28
they are also planning to implement end-to-end encryption features in jingle for security look at empathy faq for more info on  that.

migrate accounts from pidgin is already there from 2.26
logs migration will be there for 2.28 mostly as it is being worked on and there is a patch already.
contacts export from pidgin? what are u talking abt all the contacts are stored on the net so not much of a point there.

as for ui adium theme support will be thee in 2.28 . more ui enhancements can be slowly expected once they bring the core functions up to speed.

and mail notifications also has a very old patch available. if someone of us works on it it might land in 2.28 else it wont.

any other problems?

---

### Post by MadMan2k on 2009-05-10
I'd also like meta-contacts (collapsing accounts from several protocols into one).
I probably could code that myself, if only the UI was not written in C...

---

### Post by tgpraveen on 2009-05-10
there are two projects doing this soylent and people and i think last i heard both of them merged or something.
this is a target for gnome 3 btw.

ALSO for improving the ui in 2.28 version the presence status update thing is going to be revamped and made much better. there is a demo video somewhere. also the chat room selector menu is improved . so subtle changes are being made in every version.

---

### Post by gnomeuser on 2009-05-10
> **puccaso said:**
> i can never get empathy to connect to msn..

how can it be reaady!? psh..

Works for me, please file a bug.

---

### Post by gnomeuser on 2009-05-10
> **rajeev1204 said:**
> Dont like empathy .The UI doenst make sense to me at all.Looks incomplete to me.

Be productive, what is missing?

---

### Post by Gourgi on 2009-05-10
> **tgpraveen said:**
> i also think we should replace pidgina nd get empathy in.
in 2.28 release they will have google video caht support. jabber and sip already have video caht.
geolocation features will be major feature in 2.28
they are also planning to implement end-to-end encryption features in jingle for security look at empathy faq for more info on  that.

migrate accounts from pidgin is already there from 2.26
logs migration will be there for 2.28 mostly as it is being worked on and there is a patch already.
contacts export from pidgin? what are u talking abt all the contacts are stored on the net so not much of a point there.

as for ui adium theme support will be thee in 2.28 . more ui enhancements can be slowly expected once they bring the core functions up to speed.

and mail notifications also has a very old patch available. if someone of us works on it it might land in 2.28 else it wont.

any other problems?
ok , it sounds promising enough for me!
i'll keep an eye on it and i'm gonna test it soon:popcorn:

---

### Post by olskar on 2009-05-10
> **gnomeuser said:**
> 
MUST: migrate accounts, logs and contacts from pidgin



I recently installed empathy and was happily surprised when it offered to import my MSN account and IRC accounts from pidgin, including contacts. It did not import logs however but that shouldn't be that much of a problem to do.

---

### Post by olskar on 2009-05-10
Hm, If I open a chat with a MSN contact and then close it, I can not reopen the chat, I have to log out and back in, weird.

---

### Post by gnomeuser on 2009-05-10
> **olskar said:**
> I recently installed empathy and was happily surprised when it offered to import my MSN account and IRC accounts from pidgin, including contacts. It did not import logs however but that shouldn't be that much of a problem to do.

Excellent, I didn't know Empathy did that (having not used pidgin in a while). I would also like it to import from amsn, alot of users use amsm since it has webcam support so it might be nice to offer that as well. But if it does pidgin that is an important step since that is the current default and we should make sure the upgrade is as smooth as possible.

---

### Post by BwackNinja on 2009-05-10
My biggest problem with it is that it doesn't truncate tab titles when you have multiple tabs, and instead ends up showing just one or two conversations on the tab bar and you have to scroll through the rest of them or make the window bigger. Other than that, I have no problems with it.

---

### Post by taavikko on 2009-05-10
> **gnomeuser said:**
> 
[QUOTE=puccaso;7250213]i can never get empathy to connect to msn..

how can it be reaady!? psh..
Works for me, please file a bug.[/QUOTE]

works here also without any glitch...

> **rajeev1204 said:**
> Dont like empathy .The UI doenst make sense to me at all.Looks incomplete to me.

Yeah, if something looks incomplete, it's a sign of a poor app?
the default looks doesn't differ that much from pidgin.

The question I proposed was mearly an poll to see what you guys thought about this transition...

At the moment seems that all that favors "yae" and those against "ney"
goes fifty/fifty and those who haven't answered, favours another client.
Like, emesene/ amsn/ kopete/ etc/

after all, this is the gnome default client and should be treated as such.

---

### Post by Merk42 on 2009-05-10
What exactly are the advantages of Empathy over Pidgin?

---

### Post by rajeev1204 on 2009-05-10
> **gnomeuser said:**
> Be productive, what is missing?

Sorry iam not a developer so i cant explain in your language.

Dont want to argue with you but yes,I cant figure out that UI.I tried it once for google voice chat and was utterly disappointed.Its just looks incomplete ,doesnt seem to have much options for anything.

Why should an application which does its job so well be replaced by something half done?

You always seem to talk about what goes on behind the scenes about UI and code etc and separating it etc(yes i have read your posts), and most users arent bothered about that.

I think pidgin is one of the best and most complete applications bundled with ubuntu.period.

Maybe you should voice your support for video and voice for pidgin instead of empathy.

You are talking from a developers point of view but iam saying this from a user's point of view.
I will be very disappointed if empathy replaces pidgin.

I love pidgin.I have absolutely no issues with it.



Sorry but i know i might be sounding harsh here.


regards
rajeev

---

### Post by SKLP on 2009-05-10
I think it might be ready, yes. I did notice some crashes during the jaunty dev cycle, but it's pretty stable now i guess. 
Much nicer app than pidgin IMO: less cluttered GUI, as well as it's feature list is growing.
Also its the gnome default client so I believe it's what ubuntu should use.

---

### Post by gnomeuser on 2009-05-10
> **rajeev1204 said:**
> Sorry iam not a developer so i cant explain in your language.

Neither am I, but that is besides the point here. Just saying "it's bad" is not productive and does not further making "not bad(tm)". 

Giving specific examples of where Empathy is insufficient is infinitely more likely to lead to a debate on what solutions to your problems might be possible to enhance your empathy experience.

I didn't once ask you to produce code, merely to produce a use case scenerio we can examine.

It is about being constructive rather than destructive.

---

### Post by meborc on 2009-05-10
> **SKLP said:**
> I think it might be ready, yes. I did notice some crashes during the jaunty dev cycle, but it's pretty stable now i guess. 
Much nicer app than pidgin IMO: less cluttered GUI, as well as it's feature list is growing.
Also its the gnome default client so I believe it's what ubuntu should use.

sorry to raise hell :) but i don't agree... if you wanted to include gnome apps, we should all use epiphany and abiword instead of firefox and openoffice.org

pidgin just works and it is a GREAT experience for people new to linux... it has all you need from IM (no video of course)

empathy has still many bugs like the MSN chat not possible to open twice (as described before) which i can confirm...

why scratch if it does not itch?

---

### Post by rajeev1204 on 2009-05-10
> **gnomeuser said:**
> Neither am I, but that is besides the point here. Just saying "it's bad" is not productive and does not further making "not bad(tm)". 

Giving specific examples of where Empathy is insufficient is infinitely more likely to lead to a debate on what solutions to your problems might be possible to enhance your empathy experience.

I didn't once ask you to produce code, merely to produce a use case scenerio we can examine.

It is about being constructive rather than destructive.

If you are not a developer why do you speak like one?

Discussions about replacing a default application in ubuntu with something else is more appropriate in some ubuntu-devel mailing list dont you think?

And who is this 'we can examine' you keep talking about in your posts? 

This kind of discussion might be constructive to empathy,but harms pidgin .Also,you seem to be hostile towards it.You not using pidgin in 2 years doesnt mean anything here.
I have used it for 2 years without any problems.

Iam glad the ubuntu developers dont blindly use everything used in gnome as default or we would be stuck with that crappy epiphany as a browser.

This is ubuntu and users from the windows world will be happy with cross platform availability of pidgin,firefox etc.

---

### Post by amano on 2009-05-10
I'd like to have file transfer working for all common protocols before making it the default (eg. ICQ,...).

---

### Post by super.rad on 2009-05-10
> **meborc said:**
> sorry to raise hell :) but i don't agree... if you wanted to include gnome apps, we should all use epiphany and abiword instead of firefox and openoffice.org

I would love ubuntu to use epiphany and abiword as default, imo both are much better apps and not resource hogs like openoffice and firefox, but don't think that's going to happen

---

### Post by puccaso on 2009-05-10
ok, could you give me some info as to what you are using... jaunty/karmic... ?

verions of mission-control and empathy etc.. 

because i cant get empathy to work with msn.. infact, it hasnt worked for me since intrepid..

---

### Post by puccaso on 2009-05-10
ok, i just removed the butterfly telepathy plugin... it seems as the two dont work together.. 

but the haze plugin is the updated one, and that doesnt work.. 


bugs it is..

---

### Post by super.rad on 2009-05-10
I'm using karmic, everything is from karmic repo's (no ppa's or other repo's) telepathy-mission-control is version 4.67-2ubuntu1, empathy is 2.26.1-1ubuntu1, telepathy-butterfly is 0.3.3-2 and telepathy-haze is 0.3.0-1

---

### Post by super.rad on 2009-05-10
> **puccaso said:**
> ok, i just removed the butterfly telepathy plugin... it seems as the two dont work together.. 

but the haze plugin is the updated one, and that doesnt work.. 


bugs it is..

I have both installed and no problems with msn

---

### Post by Meson on 2009-05-10
My biggest criterion for picking which app to use is cross platform portability. Firefox, Thunderbird, Pidgin, Songbird, VLC, etc.

I don't think Empathy will ever be able to replace Pidgin because it doesn't meet this need.

Also, the Pidgin project sees the threat of Empathy's progress in audio/video and there is a big push to get these things working.  You also have to like Pidgin's philosphy a lot better too. It's about having a stand library libpurple, that handles all of the functionality and then any number of UIs that work with the library (GUI: pidgin, CLI: finch).

You can't beet the modularity and abstraction (and portability) that pidgin provides. And with AV coming.... YAY!

---

### Post by Merk42 on 2009-05-10
Meson mentions the advantages of Pidgin over Empathy.

As I asked two pages ago, what are the advantages of Empathy over Pidgin?

---

### Post by 23meg on 2009-05-10
Matthew Paul Thomas had produced [a usability comparison of Empathy and Pidgin]("https://wiki.ubuntu.com/EmpathyVsPidginUsability") during the Intrepid cycle, which may shed light on some of the questions brought up here.

---

### Post by rockin_goliath on 2009-05-10
> **Meson said:**
> My biggest criterion for picking which app to use is cross platform portability. Firefox, Thunderbird, Pidgin, Songbird, VLC, etc.

I don't think Empathy will ever be able to replace Pidgin because it doesn't meet this need.

Also, the Pidgin project sees the threat of Empathy's progress in audio/video and there is a big push to get these things working.  You also have to like Pidgin's philosphy a lot better too. It's about having a stand library libpurple, that handles all of the functionality and then any number of UIs that work with the library (GUI: pidgin, CLI: finch).

You can't beet the modularity and abstraction (and portability) that pidgin provides. And with AV coming.... YAY!

I have the feeling that the few features Empathy is missing will get implemented before AV gets implemented in Pidgin. We already have working AV in Empathy, and from what I understand, the code is pretty modular (although I am not a developer). Pidgin is even considering using the same Telepathy libraries.

I would consider Empathy to be ready when:
[LIST]
[*]File transfer is implemented for the popular protocols
[*]One is able to choose audio and video devices (such as webcams, microphones and speakers for playback/ringing) in a clean, user friendly GUI.
[*]AV works flawlessly with Gmail Voice/video.
[/LIST]

---

### Post by novafluxx on 2009-05-11
> **rajeev1204 said:**
> Dont like empathy .The UI doenst make sense to me at all.Looks incomplete to me.

Looks very bad to me too, like something I could design in an hour or less myself, very unprofessional and immature looking, IMHO.

---

### Post by SKLP on 2009-05-11
> **meborc said:**
> sorry to raise hell :) but i don't agree... if you wanted to include gnome apps, we should all use epiphany and abiword instead of firefox and openoffice.orgI mostly use Epiphany but I do understand it's important atleast for marketing reasons include such a famous app (firefox). I'm also on spatial nautilus, however my experience with abiword has been that it is less than adequate (sometimes one might want to open a rather complex word document, and I remember it formatting it all wrong last time I tried it)

---

### Post by rajeev1204 on 2009-05-11
Iam glad not all things from gnome are blindly taken into ubuntu .

I mean i just dont get this, why discuss replacing an application that works  so well and does its job?

I hope this thread is used for a good debate or discussion and doesnt harm the pidgin project.Its cross platform and very very nice.



regards
rajeev

---

### Post by syko21 on 2009-05-11
I'd like to see a bit more advanced network configuration in there. At school I'm behind a really annoying proxy server and with pidgin I was able to tweak here and there to get gtalk, aim, and msn to work properly (msn just works by itself on pidgin). On empathy I can't get google talk or msn to connect behind it and those are both dealbreakers since I'm an insane person who basically lives at school.

---

### Post by super.rad on 2009-05-12
Empathy is going to be the default IM client in Fedora 12 [https://fedoraproject.org/wiki/Features/Empathy](https://fedoraproject.org/wiki/Features/Empathy)

---

### Post by taavikko on 2009-05-12
> **super.rad said:**
> Empathy is going to be the default IM client in Fedora 12 [https://fedoraproject.org/wiki/Features/Empathy](https://fedoraproject.org/wiki/Features/Empathy)

Then in 10.04 we'll see empathy replacing pidgin as default IM :D

Both pidgin and empathy needs work on file transfer speeds, especially in msn protocol. Amsn is the only client atm that has a good support towards it. Mainly because it is a single protocol client...

Is webcam supoorted in either one? (pidgin/empathy) over msn.

---

### Post by Merk42 on 2009-05-12
> **super.rad said:**
> Empathy is going to be the default IM client in Fedora 12 [https://fedoraproject.org/wiki/Features/Empathy](https://fedoraproject.org/wiki/Features/Empathy)

But why? What is the advantage? Does anyone actually know the answer to this??

---

### Post by gnomeuser on 2009-05-12
> **super.rad said:**
> Empathy is going to be the default IM client in Fedora 12 [https://fedoraproject.org/wiki/Features/Empathy](https://fedoraproject.org/wiki/Features/Empathy)

Well it has been proposed, it is the second cycle in a row that has happened, each time there hasn't been much in line of productive debate or openness about the criteria Empathy is expected to meet.. much like here in fact.

---

### Post by jblackhall on 2009-05-12
> **Merk42 said:**
> But why? What is the advantage? Does anyone actually know the answer to this??

I think it's a number of reasons.  First, while Pidgin is cross-platform, the developers are sometimes difficult to deal with (from what I've heard).  They have their own ideas of how things should work and they don't take kindly to people disagreeing with them.

More importantly, Empathy is using the Telepathy framework, which allows it to be more closely incorporated into the Gnome core.  One of the main benefits is it will allow the Gnome desktop to become more task/person oriented as opposed to application oriented, like using a universal contacts scheme.  For example: a contact George.  You could send him an email (via Evolution), send him an IM (via Empathy), start a voice/video chat, place a phone call to him, transfer files to him, etc.  [See here]("http://blog.ibeentoubuntu.com/2008/08/gnome-has-empathy-for-you.html").  That kind of integration will likely never be possible with Pidgin, both due to their devs and the fact that it's cross-platform.  

The separation of Empathy and Telepathy also allows the extension of the traditional "IM client," allowing you to change the client interface (Empathy) while retaining the more thoroughly developed protocol framework (Telepathy), which ideally is more bug-free.  Adding a new protocol (e.g. Facebook chat or GoogleTalk video chat) simply requires adding support to Telepathy and then all its clients get to use a new protocol.

---

### Post by novafluxx on 2009-05-12
I use pidgin on my WinTel box also, and the only thing I am lacking there is a/v chat. I REALLY want this feature, and its the ONLY thing holding me to Windows.

I still have to have a 40GB partition for Windows on my laptop, becuase I need Skype, MSN, Yahoo! to work with a/v.

From what I've heard/read too, the pidgin devs aren't very keen on outside input, and have thier own idea of where Pidgin needs to go, moving forward.

---

### Post by Merk42 on 2009-05-12
> **novafluxx said:**
> I use pidgin on my WinTel box also, and the only thing I am lacking there is a/v chat. I REALLY want this feature, and its the ONLY thing holding me to Windows.

I still have to have a 40GB partition for Windows on my laptop, becuase I need Skype, MSN, Yahoo! to work with a/v.

From what I've heard/read too, the pidgin devs aren't very keen on outside input, and have thier own idea of where Pidgin needs to go, moving forward.

Skype in Linux works fine for a/v
MSN  a/v I think you can use aMSN
Yahoo a/v you can use GYachI

Granted those aren't in Pidgin/Empathy, but I would think loading up aMSN and GYachI is easier than dual booting.

---

### Post by novafluxx on 2009-05-12
For me, Skype doesn't work with my webcam, maybe its because its 32-bit, and my OS is 64-bit.

I'll look into those programs, cause I'd really like to have some a/v!

---

### Post by jblackhall on 2009-05-12
> **novafluxx said:**
> For me, Skype doesn't work with my webcam, maybe its because its 32-bit, and my OS is 64-bit.

I'll look into those programs, cause I'd really like to have some a/v!

Are you using skype from Medibuntu or from the Skype website?  You should use Medibuntu's version.

---

### Post by novafluxx on 2009-05-12
I've been using the one from Skype's sight. I haven't use the medibuntu repos

---

### Post by Merk42 on 2009-05-12
> **novafluxx said:**
> I've been using the one from Skype's sight. I haven't use the medibuntu repos

Use the medibuntu one, I'm running 64bit Jaunty and the webcam is fine.

Well I had to do a line of code, but I think that's because of my cam, not because of Skype.

---

### Post by Neon Lights on 2009-05-12
I'm still waiting on [this]("https://bugs.freedesktop.org/show_bug.cgi?id=17157") to be implemented in Telepathy, and subsequently Empathy. :/ The majority of my friends go mobile when offline, and it makes a difference at 1 in the morning as to whether they're on their phone or the computer. Granted, I'm sure not everyone has this problem, but yeah. :P

---

### Post by rajeev1204 on 2009-05-13
Gnomeuser .. i now remember what i didnt like or dislike.

I tried to add gtalk user to have a voice conversation with him,but there seem to be no clear indication of whether i can have a conversation with him,whether he has a mic,and neither does it tell you whether you yourself have configured things correctly.

OMG ,forgot to add this,the main window kept crashing at least 10 times and when i closed the window, it seemed to create multiple instances of the program.It was really realy bad.Iam not remembering correctly what happened that day, but i had major issues getting the program to quit.

Where are the audio/video configuration settings? I couldnt find them.




rajeev

---

### Post by CarpKing on 2009-05-14
> **rajeev1204 said:**
> You think users should use epiphany instead of firefox because its on gnome ? Oh please.

It isn't about what users should use, it's about what Ubuntu should ship.  If certain people have needs beyond the base platform, they can use the repositories.  Gnome is about providing a solid, functional base platform.  They feel that Empathy and Telepathy provide a lot of exiting potential for desktop integration, which Pidgin does not.  Ubuntu should create a list of criteria to determine when Empathy is ready for their purposes.

---

### Post by 23meg on 2009-05-14
> **rajeev1204 said:**
> 
So until gnome figures out what goes where, why should ubuntu blindly take all apps from gnome?

You think users should use epiphany instead of firefox because its on gnome ? Oh please.

[http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)

---

### Post by rajeev1204 on 2009-05-14
> **23meg said:**
> [http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)

nvm

---

### Post by rajeev1204 on 2009-05-14
> **CarpKing said:**
> It isn't about what users should use, it's about what Ubuntu should ship.  If certain people have needs beyond the base platform, they can use the repositories.  Gnome is about providing a solid, functional base platform.  They feel that Empathy and Telepathy provide a lot of exiting potential for desktop integration, which Pidgin does not.  Ubuntu should create a list of criteria to determine when Empathy is ready for their purposes.

Ok.Thanks.

But in jaunty/intrepid it did integrate with the gnome panel .Is this similar?

---

### Post by Nerd_bloke on 2009-05-14
I had another look back at MPT's usability [comparison,]("https://wiki.ubuntu.com/EmpathyVsPidginUsability") and the bugs that were reported against Pidgin and Empathy's trackers; Fedora is [using]("https://fedoraproject.org/wiki/Features/Empathy#Scope") these as potential blockers for Empathy-by-default in their version 12.

Of the bugs reported against Empathy eight are fixed already. 
However against Pidgin only [one]("http://developer.pidgin.im/ticket/6662") has been fixed, with two others marked as [won'tfix]("http://developer.pidgin.im/ticket/4564")/[invalid.]("http://developer.pidgin.im/ticket/6823") The further six are in limbo.

While not a perfect sample this seems to show (to me anyway) that the Empathy developers are much more receptive. The Jabber comment in the [won'tfix]("http://developer.pidgin.im/ticket/4564#comment:3") bug reminds me of a arrogance of the devoplers that lead to the [Carrier]("http://funpidgin.sourceforge.net/") split off. User choice over a feature or added clarity in the application, rejected because it wasn't the developer's idea.

As others have mentioned already Empathy will be part of a framework with other Gnome packages in what is primarily a Gnome based distribution.
Browsers such as Epiphany/Firefox do not use "contacts/people" that can be shared between desktop applications in the same way as instant messengers like Empathy/Pidgin do. 
Drawing a comparison is like comparing apples and oranges.

---

### Post by gnomeuser on 2009-05-14
> **rajeev1204 said:**
> Could you explain ? My english is not that good.

The straw man you put up was dismissing Empathy based on disliking Epiphany when using Epiphany is not the position.

Epiphany sucks compared to Firefox is not a valid counter argument to Empathy has great potential and is the GNOME default. That is your straw man argument. You aim at Epiphany to hit Empathy.

The examples in the wikipedia page should inform you more on the matter of this fallacy specifically. There should also be example pages in your language if that is easier for you to understand.

I would recommend taking a class on logical fallacies.

---

### Post by avb on 2009-05-14
> **gnomeuser said:**
> Works for me, please file a bug.

Not works for me since 1st releast. Bug on pymsn is already filled but seems dead for years.

---

### Post by GeoPirate on 2009-05-19
how do you turn of logging in empathy?  I can't figure this out, it's the main reason I stick to pidgin.

---

### Post by MacUntu on 2009-05-19
Why do ppl always want to replace working programms?

---

### Post by olskar on 2009-05-19
> **MacUntu said:**
> Why do ppl always want to replace working programms?

Probably for the same reason people sometimes reshuffle their furniture :)

But in this particular case I think people see what possibilities would come out of using Telepathy. Check here for example: [https://wiki.ubuntu.com/MOTU/Teams/IM/DesktopIntegrationSIPIM?action=show&redirect=MOTUIM%2FDesktopIntegrationSIPIM](https://wiki.ubuntu.com/MOTU/Teams/IM/DesktopIntegrationSIPIM?action=show&redirect=MOTUIM%2FDesktopIntegrationSIPIM)

---

### Post by hexsel on 2009-05-20
They're not replacing working programs, they're replacing a program that, although it doesn't crash (worse, it does on occasion), it doesn't work for something users want to do, namely Video.

I also despise their interface (at least until a year or 9 months ago), but having Video/Audio would be a great addition to THE IM program shipped with Ubuntu.

---

### Post by gnomeuser on 2009-05-20
> **hexsel said:**
> They're not replacing working programs, they're replacing a program that, although it doesn't crash (worse, it does on occasion), it doesn't work for something users want to do, namely Video.

I also despise their interface (at least until a year or 9 months ago), but having Video/Audio would be a great addition to THE IM program shipped with Ubuntu.

Upstream GNOME never had an IM client so they never replaced anything, downstreams like Ubuntu are merely following along and gaining what is a superior framework. Aside that empathy allows interesting concepts for communication one example of this can be seen in Moblin and how they already integrate people as a part of your computing experience.

---

### Post by Zlatan on 2009-05-21
> **super.rad said:**
> yes i'd say it's ready to replace pidgin, been using it for a while now. Much prefer it over pidgin and haven't had any problems with it.
One feature i would like would be new mail notification like in pidgin.

+1

---

### Post by yelo3 on 2009-05-21
I really like the idea behind empathy and telepathy, but it seems that well known protocols (msn for instance) are really poorly implemented.
Developers are working on absurd features (like telepathy tubes) while ignoring basic stuff. Here's what msn currently lacks:
- rich text
- custom emoticons
- nudges
- file transfers
- winks (not really useful)
- chat with multiple contacts
- compatibility with buddy icons from the new version of live messenger
- offline messages
- chat with invisible users
- user alias
- personal buddy icon and name retrieval
- mobile users are marked as 

On the other hand, empathy (in my opinion) should be redesigned. It's too similar to pidgin, but it's worse looking, because of:
- missing libnotify integration
- very ugly status icons (especially idle and available)

---

### Post by Incognito-Here on 2009-05-21
I think it's better looking than pidgin. I'm switched to Empathy from gajim, not pidgin though, I've never used this crap before.

---

### Post by Merk42 on 2009-05-21
> **Incognito-Here said:**
> I think it's better looking than pidgin. I'm switched to Empathy from gajim, not pidgin though, I've never used this crap before.

What 'crap' have you never used? If you've never used it, how do you know it's crap?

---

### Post by Incognito-Here on 2009-05-21
Once I've tried pidgin, and have never used it again :p

---

### Post by yelo3 on 2009-05-21
I forgot to say that empathy does not have even standard emoticons for protocols, only simple ones such as :) :( etc.

---

### Post by Incognito-Here on 2009-05-22
It's a feature. All chat windows should look the same.

---

### Post by yelo3 on 2009-05-22
If it's a feature that all chat windows should look the same, then add every emoticon from all protocols

---

### Post by Incognito-Here on 2009-05-22
Having sh1tload of emoticons in the IM? No, please ;)

---

### Post by yelo3 on 2009-05-22
(l) ({)

---

### Post by super.rad on 2009-05-22
yeah emoticons is something I can live without, really annoys me when people post loads

---

### Post by yelo3 on 2009-05-22
Remember there's an option to disable emoticons!

---

### Post by hexsel on 2009-05-22
I was talking about Ubuntu, not Gnome.  Funnily enough, I was in part agreeing with you.  Now I'm not.  If the promise of the future uses of the framework is the reason, you shouldn't replace something with better usability just because ONE DAY in the distant future IT MAY have more uses.  We're talking about the next release of Ubuntu.  We should ship the one that works best for "customers".  

I would really love to see Audio and Video.  


> **gnomeuser said:**
> Upstream GNOME never had an IM client so they never replaced anything, downstreams like Ubuntu are merely following along and gaining what is a superior framework. Aside that empathy allows interesting concepts for communication one example of this can be seen in Moblin and how they already integrate people as a part of your computing experience.

---

### Post by super.rad on 2009-05-22
Tried out empathy 2.27.1 on arch the other day and noticed a few nice changes, hopefully ubuntu gets the new version soon

> What's New?
===========
Bugs fixed:
 - Fixed #582641, crash in Empathy Instant Messenger: Making a call to a googl...
 - Fixed #501519, Empathy API need documentation
 - Fixed #504277, Empathy won't use 2nd and further protocols a connection manager provides
 - Fixed #530119, display remote caller in the call window
 - Fixed #539506, First message in conversation has no timestamp
 - Fixed #544678, Can't change account photo/avatar
 - Fixed #548704, "Add" button requires further action but lacks an ellipsis
 - Fixed #549366, Should use SimplePresence
 - Fixed #549641, Should use Contacts
 - Fixed #561033, Work on the documentation
 - Fixed #566905, avatar button is too tiny
 - Fixed #568403, Add header file in documentation
 - Fixed #568562, ghelp link broken in documentation
 - Fixed #570346, EmpathyTpChat should use the Group SelfHandle if present
 - Fixed #570545, Huge memory leak after opening some contacts discussion windows
 - Fixed #574626, No obvious way to display FT manager
 - Fixed #575090, Notifications of new messages stop working after closing the chat window
 - Fixed #575415, Should switch from libglade to GtkBuilder
 - Fixed #575442, "Call" string needs context for translation
 - Fixed #575817, empathy_tp_tube_new_stream_tube should allow NULL as parameters
 - Fixed #576384, "accept incoming call" dialog brings roster to current workspace
 - Fixed #576394, "Send Video" button and "Call -> Send video" menu entry are not synced
 - Fixed #577026, Sending slash-prefixed messages on IRC is a security risk.
 - Fixed #577427, Port to latest tp-glib API
 - Fixed #578356, Asserts when reconnecting to a chat room.
 - Fixed #578399, Change to supplying spelling suggestions in submenu
 - Fixed #579139, memleak in log_store_empathy_get_messages_for_file
 - Fixed #579148, Improves the Join New room UI by adding columns, changing the UI
 - Fixed #579553, Serveral memory leaks in empathy.
 - Fixed #579735, add empathy_tp_tube_call_when_ready ()
 - Fixed #579780, Several functions should be _dup_foo instead of _get_foo
 - Fixed #579800, adding or removing an IRC account causes a dialog to pop up
 - Fixed #579971, Try to access to a NULL GtkEntry when adding a new contact
 - Fixed #580097, Dispaly transfer speed, and make remaining time more dynamic
 - Fixed #580203, Theoretical race connecting to Received.
 - Fixed #580771, Video playback should have a fullscreen mode
 - Fixed #582751, No menu icon = no smiley
 - Fixed #563222, Wrong "time remaining" estimation when sending a file
 - Fixed #579484, New "join chatroom" dialog doesn't get list of rooms when room list is expanded
 - Fixed #579485, "Join Room" dialog should allow sorting the list of rooms
 - Fixed #571664, [1/3] Empathy should support Geolocation

---

### Post by Gourgi on 2009-06-15
[http://blogs.gnome.org/xclaesse/2009/06/15/empathy-adium-geolocalisation-desktop-sharing-and-file-transfer/](http://blogs.gnome.org/xclaesse/2009/06/15/empathy-adium-geolocalisation-desktop-sharing-and-file-transfer/)

just saw it on gnome planet
> **4 new** exciting feature of the upcoming Empathy 2.27.3

1) Adium - theming with webkit
2) Geolocalisation - publish your position to your contacts based on GPS or ip data
3) Desktop sharing - using vnc
4) File transfer - checksum support , soon resume support too 



---

### Post by castrojo on 2009-06-15
Empathy hug day coming up if you want to help out:

[https://wiki.ubuntu.com/UbuntuBugDay/20090618](https://wiki.ubuntu.com/UbuntuBugDay/20090618)

The Empathy guys hang out in #ubuntu-desktop and are very responsive to bugs, so file em if you got em.

---

### Post by yelo3 on 2009-06-15
Is the bug hug day only for empathy? or also telepathy?

---

### Post by castrojo on 2009-06-15
It's for Empathy but I am sure no one will mind people helping out with the entire stack, since it's kind of important to empathy.

---

### Post by zekopeko on 2009-06-15
> **Gourgi said:**
> [http://blogs.gnome.org/xclaesse/2009/06/15/empathy-adium-geolocalisation-desktop-sharing-and-file-transfer/](http://blogs.gnome.org/xclaesse/2009/06/15/empathy-adium-geolocalisation-desktop-sharing-and-file-transfer/)

just saw it on gnome planet

this is pure awesomeness!!!

---

### Post by nhasian on 2009-06-15
after reading this thread i decided to give empathy a try.  i installed it in karmic alpha 2 easy from the Synaptic Package Manager.  The first time I launched it, empathy auto detected and imported all of my contacts from pidgin, and i was up and running quickly and easily.

---

### Post by Bou on 2009-06-15
Am I the one missing contacts in Empathy? I mean, all my contacts set to "do not disturb" appear as disconnected here, and I'm at an IRC channel where no one appears in the list, even though there ARE people there.

---

### Post by DPic on 2009-06-15
Empathy is GREAT for most users, especially **new** ones, and it can replace poth pidgin AND ekiga. It lacks features only more hardcore users (yes, i just referred to some IM users as hardcore) like meta contacts, which is on the way as well. It is simple and integrates well, and we want to make Ubuntu friendly for NEW users. Old users who prefer the clutter and feature madness of pidgin will simply install it from Add/Remove. If Ubuntu switched to Empathy, it's development is going to get a huuuggggeee boost so the feature gap will close and eventaully reverse.

---

### Post by Swarms on 2009-06-15
> **DPic said:**
> Empathy is GREAT for most users, especially **new** ones, and it can replace poth pidgin AND ekiga. It lacks features only more hardcore users (yes, i just referred to some IM users as hardcore) like meta contacts, which is on the way as well. It is simple and integrates well, and we want to make Ubuntu friendly for NEW users. Old users who prefer the clutter and feature madness of pidgin will simply install it from Add/Remove. If Ubuntu switched to Empathy, it's development is going to get a huuuggggeee boost so the feature gap will close and eventaully reverse.

Very true!

---

### Post by super.rad on 2009-06-15
> **Bou said:**
> Am I the one missing contacts in Empathy? I mean, all my contacts set to "do not disturb" appear as disconnected here, and I'm at an IRC channel where no one appears in the list, even though there ARE people there.
Yeah I seem to be getting this bug, if I look on pidgin then I see a few people are online, I switch to empathy and it shows no online users.

---

### Post by yoasif on 2009-06-15
i've been playing with it for a while, and it has an extremely annoying behavior -- when a message is received from a person without an open conversation open, the alert comes up in the notification area, and does not spawn a new window -- this is unlike any other IM application I have ever used. 

I filed a bug report, and didn't get a friendly response, sadly. 

[http://bugzilla.gnome.org/show_bug.cgi?id=585914](http://bugzilla.gnome.org/show_bug.cgi?id=585914)

so for me, empathy is NOT ready to replace pidgin, as it presents a usability regression for me.

---

### Post by castrojo on 2009-06-15
When I get a new message I get a message-indicator thing, does that not happen for you?

---

### Post by yoasif on 2009-06-15
> **whiprush said:**
> When I get a new message I get a message-indicator thing, does that not happen for you?it does, it's just very annoying -- why do i need to click on the icon when in pidgin (or other IM apps), I can simply switch to the new conversation tab? Having to move my hand from the keyboard is extremely annoying in this case. 

also, most of the time, I don't even notice, since I don't look at the notification area often -- this means that friends can leave messages, and leave before I have the chance to respond, simply because I never noticed that i received an IM, even though I was actively using the application.

---

### Post by Bios Element on 2009-06-15
Once it has Meta-Contacts, I'm dumping Pidgin. Until then, I have to stick with Pidgin because having 6 "John Doe"'s is kinda annoying >.>

---

### Post by DPic on 2009-06-15
> **Bios Element said:**
> Once it has Meta-Contacts, I'm dumping Pidgin. Until then, I have to stick with Pidgin because having 6 "John Doe"'s is kinda annoying >.>

This is the thinking we should avoid. We are not choosing our own IM clients, we are choosing the client for new users. We may keep pidgin no matter what the default is. New users should be presented with empathy because is is simple and less intimidating. Most users aren't looking for meta-contacts (although it is on the way).

---

### Post by zekopeko on 2009-06-15
> **yoasif said:**
> it does, it's just very annoying -- why do i need to click on the icon when in pidgin (or other IM apps), I can simply switch to the new conversation tab? Having to move my hand from the keyboard is extremely annoying in this case. 

also, most of the time, I don't even notice, since I don't look at the notification area often -- this means that friends can leave messages, and leave before I have the chance to respond, simply because I never noticed that i received an IM, even though I was actively using the application.

agreed. this really should be fixed. it should behave like update manager but with flashing in the window list.

---

### Post by Bios Element on 2009-06-15
> **DPic said:**
> This is the thinking we should avoid. We are not choosing our own IM clients, we are choosing the client for new users. We may keep pidgin no matter what the default is. New users should be presented with empathy because is is simple and less intimidating. Most users aren't looking for meta-contacts (although it is on the way).

Um, Right...I already recommend it for new users. Why should I avoid the fact that it's only missing one feature for me to use it? That's a glowing endorsement. Ya know, Eating your own dog food and all that. >.> I never said the lack of meta-contacts would bother the general user, Just that it would bother me.

---

### Post by geojorg on 2009-06-15
I like Empathy and for 2.28 it would be more mature, love to see it in Ubuntu Karmic as default, but on the other side I find the notification icon not a desire option, the expected behavior is that messages show up in a new window.

---

### Post by zekopeko on 2009-06-15
and imagine all the cool stuff they can do later with empathy/telepathy!
can't wait.

---

### Post by meborc on 2009-06-16
> **zekopeko said:**
> and image all the cool stuff they can do later with empathy/telepathy!
can't wait.

i can imagine... BUT i would not change the app before those nice features emerge... WHEN they are there, THEN change the app... changing it now would be regression of usability

again - my own impression - does not necessarily be true or correct, but this is how -=I=- feel, so feel free to disagree :)

---

### Post by ricpelo on 2009-06-16
I'm against the idea of replacing Pidgin with Empathy:

- Pidgin has a much bigger user base.
- Pidgin has a great set of features which works very well.
- Pidgin has a great set of plugins (Guifications, for instance).
- Pidgin has a better MSN protocol support (essential for Spanish & other European users).
- Pidgin has a better UI (have you seen the Empathy's Accounts dialog? I'm unable to read the whole account name in the accounts list!).
- Pidgin has a better integration with the Ubuntu desktop (Indicator Applet, Fast User Switch Applet...).
- Pidgin is a much more mature and stable project.

So the answer is: no, Empathy is NOT ready to replace Pidgin at this moment.

---

### Post by taavikko on 2009-06-16
> **ricpelo said:**
> I'm against the idea of replacing Pidgin with Empathy:

- Pidgin has a much bigger user base.
<snip>
- Pidgin has a better integration with the Ubuntu desktop (Indicator Applet).
- Pidgin is a much more mature and stable project.




Pidgin/Empathy is nothing more than multiprotocol IM client, doesn't matter if 10 or 10k users.

Empathy is integrated to gnome, so would say it integrates far better than pidgin to any desktop distro that uses Gnome.

Empathy offers far more potential than pidgin all-around.
giving it enough time to fully evolve.

---

### Post by Joe_Bishop on 2009-06-16
> Pidgin has a much bigger user base.
 It's the only pure truth you said

> Pidgin has a great set of features which works very well.
 What about voice and video chat? Pidgin doesn't have them, Empathy does.

> Pidgin has a great set of plugins (Guifications, for instance).
 Don't know what are you talking about. I can't find "guification" in my plugins. So, this is half-true.

> Pidgin has a better MSN protocol support (essential for Spanish & other European users).
 Empathy use the same codebase (libpurple)

> Pidgin has a better UI (have you seen the Empathy's Accounts dialog? I'm unable to read the whole account name in the accounts list!).
 No, pidgin UI is overcomplicated and much worse in most case. Your fact is just one case. What about history? Empathy history is sooo much better ;)

> Pidgin has a better integration with the Ubuntu desktop (Indicator Applet, Fast User Switch Applet...).
 It's a lie. Empathy is better integrated. It's the default Gnome client, pidgin is not. Indicator applet is one big failure, it just sucks to reply through Indicator, than choose pidgin, than manually search for the contact ;)

> Pidgin is a much more mature and stable project.
 Hm, the second full truth.

> So the answer is: no, Empathy is NOT ready to replace Pidgin at this moment.
 After the plans to replace stable and "just works" RB with banshee, I would not be surprised if they get rid of pidgin.

// To moderators: please pass it, no offence here ;)

---

### Post by rhunwicks on 2009-06-16
In Jaunty, Empathy doesn't use the Gnome system Proxy Settings and has no facility to set a Network Proxy in its own preferences - see [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889).

I don't think Empathy is suitable to replace Pidgin until this bug has been fixed, as it looks like a major regression to anyone installing Ubuntu on new PCs behind a corporate firewall.

Once it is fixed, I think Empathy is the way to go.

Roger

---

### Post by meborc on 2009-06-16
> **taavikko said:**
> ...
Empathy offers far more potential than pidgin all-around.
giving it enough time to fully evolve.

again... you say it yourself: "...giving it enough time to fully evolve..."

this is the point... it is not ready NOW to replace pidgin.. maybe in the future, but not NOW

---

### Post by Swarms on 2009-06-16
> **rhunwicks said:**
> In Jaunty, Empathy doesn't use the Gnome system Proxy Settings and has no facility to set a Network Proxy in its own preferences - see [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/304889).

I don't think Empathy is suitable to replace Pidgin until this bug has been fixed, as it looks like a major regression to anyone installing Ubuntu on new PCs behind a corporate firewall.

Once it is fixed, I think Empathy is the way to go.

Roger

Details...

---

### Post by teddks on 2009-06-16
There's still no support for OTR encryption in Empathy, is there?

One of the reasons I recommend Ubuntu to new users is that it is secure by default. There aren't any open services, it has AppArmor and SSP by default, and it integrates _great_ with crypto. The default email and IM clients both have support for strong crypto, setting up an encrypted filesystem is easy, gpg is installed by default, etc..

The way I see it, if Empathy becomes the default client, we are moving from a program that allows users their privacy to one that does not. By extension, as a distribution, Ubuntu is moving away from its commitment to security.

I've gotten a _lot_ of people started on Ubuntu, and I've never had any complaints about Pidgin. Not only is it easy to use for "new users" (I don't know what could be easier), they can set up strong crypto with **one click**, making Pidgin-OTR the easiest security "papercut", if you will, to patch. Taking Pidgin out of the default install will (likely) mean taking the pidgin-otr package out of the default install, and since it isn't in Pidgin's depends, that will mean new users who want security will have to go into Synaptic or the command line to get it installed.

We are making a key security feature move from one click away to two installations away. Is that really acceptable?

---

### Post by DPic on 2009-06-16
[http://pinstack.blogspot.com/2009/06/empathy-in-ubuntu-karmic-910-or-karmic.html](http://pinstack.blogspot.com/2009/06/empathy-in-ubuntu-karmic-910-or-karmic.html)

We should include Empathy in Karmic or Karmic +1 and we should make andannounce the decision of which now.

If we donot include Empathy in Karmic, but plan on including it in Karmic +1 (and announce this)it will still give Empathy the attention it needs from developers to fix the bugs that would be considered regressions during the switch without actually replacing Pidgin before they're fixed.

On the other hand, it might still be preferable to include Empathy in Karmic to have more of a guarantee that bugs will be fixed in time for the 10.04 LTS release and many of the existing bugs could be fixed before the final release of Karmic. As someone [commented on my last post]("http://pinstack.blogspot.com/2009/06/replace-pidgin-with-empathy-in-karmic.html?showComment=1245133369575#c6152600795066756079"):
> Empathy has been the top active project in Gnome for the last few weeks, with about 100 commits a week on average. The pace of development is astounding. Once the move to Empathy is the default, Ubuntu can start depending on it for other applications' communication needs (using Tubes). Gnome Games are getting Tubes support. Vino just got Tubes support, meaning that you can share your desktop with your contacts in Empathy.
I understand why 8.04 didn't ship with Empathy, but the change needs to happen. Empathy is 95% there. The needed changes can be made before Karmic if Ubuntu (and Canonical) commits to it. If 9.10 ships with Empathy, all the major bugs will be worked out by 10.04. Who wants to add yet ANOTHER new technology to another LTS.
So whether we include it in Karmic, or we hold off until the LTS, let's make and announce the decision now.

---

### Post by yelo3 on 2009-06-16
In fact the problem is not empathy, it's telepathy, which is not so active in all protocols

---

### Post by sabre2th on 2009-06-16
> **DPic said:**
> On the other hand, it might still be preferable to include Empathy in Karmic to have more of a guarantee that bugs will be fixed in time for the 10.04 LTS release and many of the existing bugs could be fixed before the final release of Karmic. As someone [commented on my last post]("http://pinstack.blogspot.com/2009/06/replace-pidgin-with-empathy-in-karmic.html?showComment=1245133369575#c6152600795066756079"):

So whether we include it in Karmic, or we hold off until the LTS, let's make and announce the decision now.
I'd like to see some guarantee that Empathy does everything correctly before any decision is made.

> **taavikko said:**
> Pidgin/Empathy is nothing more than multiprotocol IM client, doesn't matter if 10 or 10k users.

Empathy is integrated to gnome, so would say it integrates far better than pidgin to any desktop distro that uses Gnome.
Most users don't care about that.  Typical users need a straightforward, easy solution and Pidgin provides that.  It's friendly and all the basic functionality works very well.  Reading through this thread, all I've really seen is this:

> **taavikko said:**
> Empathy offers far more potential than pidgin all-around.
giving it enough time to fully evolve.
Potential is great, but it's not the same as being good.  When all of these bug fixes and features are completed, it'll be worth a look.

Until someone can produce a clear list of reasons why Empathy has to replace Pidgin (ie. Broken/missing functionality in Pidgin or significant improvements in usability), this is all a waste of time.  A working program should not be replaced because another program is POTENTIALLY better.

---

### Post by castrojo on 2009-06-16
> **DPic said:**
> We should include Empathy in Karmic or Karmic +1 and we should make andannounce the decision of which now.

[https://wiki.ubuntu.com/DesktopTeam/Specs/Karmic/MessagingAndCommunicationSelection](https://wiki.ubuntu.com/DesktopTeam/Specs/Karmic/MessagingAndCommunicationSelection)

The decision was made at UDS, so unless there's something seriously broken it will probably be the default. Note that pidgin will remain in main for at least another cycle, and that people who upgrade will keep pidgin, but new installs will get empathy.

---

### Post by castrojo on 2009-06-16
> **sabre2th said:**
> I'd like to see some guarantee that Empathy does everything correctly before any decision is made.

If that were a rule then we'd never ship any software.

> Until someone can produce a clear list of reasons why Empathy has to replace Pidgin (ie. Broken/missing functionality in Pidgin or significant improvements in usability), this is all a waste of time.  A working program should not be replaced because another program is POTENTIALLY better.

Ubuntu needs working video conferencing in order to compete with other operating systems. Empathy has some rough edges sure, but they are being /quickly/ fixed, which is why we're asking people to participate in the hug day.

---

### Post by 23meg on 2009-06-16
> **whiprush said:**
>  Empathy has some rough edges sure, but they are being /quickly/ fixed, which is why we're asking people to participate in the hug day.

More on the Hug Day:

[http://ubuntuforums.org/showthread.php?t=1188976](http://ubuntuforums.org/showthread.php?t=1188976)

---

### Post by pferraro on 2009-06-16
> **teddks said:**
> There's still no support for OTR encryption in Empathy, is there?

Nope.  Here's the relevant feature request:

[http://bugs.freedesktop.org/show_bug.cgi?id=16891](http://bugs.freedesktop.org/show_bug.cgi?id=16891)

Unfortunately, it has a "low" priority.

---

### Post by tyfius on 2009-06-16
I am having a small problem with Empathy, it's not displaying any custom MSN status message set by my contacts nor does it seem to allow me to set one.

Use contact information is also not very complete. At the moment Emesene is doing a far better job for MSN and even Pidgin has more features.

---

### Post by ricpelo on 2009-06-16
> **taavikko]Pidgin/Empathy is nothing more than multiprotocol IM client, doesn't matter if 10 or 10k users.[/quote]

Most of the time, free software quality highly depends on the user base. MSN protocol (predominant in many countries) works worse in Empathy. And the plugins set is much bigger in Pidgin, probably due to it's bigger community.

[quote=taavikko]Empathy is integrated to gnome, so would say it integrates far better than pidgin to any desktop distro that uses Gnome.[/quote]

What "integrated to gnome" means? Pidgin works great with Gnome (for instance, it honors the Gnome proxy settings by default). And Pidgin in is better integrated with the Ubuntu-specific desktop elements like Indicator Applet and the Fast User Switch Applet. We're talking about Ubuntu, not any Gnome distro.

[quote=taavikko]
Empathy offers far more potential than pidgin all-around.
giving it enough time to fully evolve.[/quote]

The user doesn't need potential. The user needs the best IM tool NOW. When Empathy brings to the user a better IM experience than Pidgin, then will be the time to change.

[QUOTE=whiprush said:**
> Ubuntu needs working video conferencing in order to compete with other operating systems.

Ubuntu does already have that application. It's called Ekiga.

---

### Post by castrojo on 2009-06-16
> **ricpelo said:**
> Ubuntu does already have that application. It's called Ekiga.

Did you read the spec? This would replace Ekiga.

---

### Post by castrojo on 2009-06-16
> **ricpelo said:**
> And Pidgin in is better integrated with the Ubuntu-specific desktop elements like Indicator Applet and the Fast User Switch Applet. We're talking about Ubuntu, not any Gnome distro.

The indicator-applet patch is done and the FUSA patch is being worked on.

---

### Post by Joe_Bishop on 2009-06-16
> The indicator-applet patch is done and the FUSA patch is being worked on.
Only me hates this indicator applet? Please, don't make it in the same way as pidgin, it's a disaster!

---

### Post by ricpelo on 2009-06-16
> **whiprush said:**
> Did you read the spec? This would replace Ekiga.

Yes, I read the Spec, and I wonder if Empathy could bring a better a/v conferencing than Ekiga.

Anyway, the a/v conferencing has (for me) a lower priority than other features (good MSN support, good set of plugins like Guifications, OTR and so, more friendly UI, etc.).

Why don't simply fix Pidgin defects and work on it in order to have a still better IM app? Why don't (for instance) investigate the [pidgin-vv]("http://developer.pidgin.im/wiki/vv") project for a/v conferencing support?

---

### Post by sabre2th on 2009-06-16
In case it's not clear, I have no problem changing things around and using whatever I like most when I install (ie. I use Thunderbird instead of Evolution).  That's fine; that's what this is all about, but IN ITS CURRENT STATE, Empathy just doesn't look ready to take over the default slot.  I know there are people who agree with that.  That's all I'm saying.  Why have a thread about it if not to have differing viewpoints?

> **whiprush said:**
> Did you read the spec? This would replace Ekiga.
But why replace two easy-to-use programs that work well with a program that has so many rough edges?  If the edges are smoothed out, then it can be the default in Karmic or Karmic+1, but this thread reads like a fanboy push to make Empathy the default with promises that it will be fixed after.  Cart before the horse, as the saying goes.

---

### Post by castrojo on 2009-06-16
> **ricpelo said:**
> Why don't simply fix Pidgin defects and work on it in order to have a still better IM app? Why don't (for instance) investigate the [pidgin-vv]("http://developer.pidgin.im/wiki/vv") project for a/v conferencing support?

Ubuntu doesn't develop IM applications, it's an integrator of existing applications. You're going to be waiting for vv for a long time. :D

---

### Post by castrojo on 2009-06-16
> **sabre2th said:**
> In case it's not clear, I have no problem changing things around and using whatever I like most when I install (ie. I use Thunderbird instead of Evolution).  That's fine; that's what this is all about, but IN ITS CURRENT STATE, Empathy just doesn't look ready to take over the default slot.  I know there are people who agree with that.  That's all I'm saying.  Why have a thread about it if not to have differing viewpoints?

I'm not saying you shouldn't have a different opinion. The spec clearly states that we are switching early and if it's not what we want by feature freeze then pidgin stays. In fact I want to hear your concerns, that's why I am here.

> But why replace two easy-to-use programs that work well with a program that has so many rough edges?

To use Ekiga you need a sip account, it's a softphone, there's no easy way for me to call my mom on gtalk, for example. The guts for this stuff (Telepathy) have been shipping on maemo tablets for a long time, it's just getting the final polish in on the desktop stuff to make it better that needs to be done. They kind of polish you can get by say, switching to something early in a development release so people can bang on it and report bugs.

---

### Post by ricpelo on 2009-06-16
> **whiprush said:**
> Ubuntu doesn't develop IM applications, it's an integrator of existing applications. You're going to be waiting for vv for a long time. :D

Great! That's the reason why I say that Pidgin & Ekiga is a better set of applications for IM than Empathy is: Pidgin & Ekiga is NOW a better selection and Empathy seems to have a good future, but it's a worse selection in the present day.

(Offtopic: I'm both Pidgin & Empathy installed in my Jaunty. Empathy fails to login into my MSN account with a bare "Net error" message. Works perfectly with Pidgin. Oh, I forgot to say: I already tried importing the Pidgin account settings, without luck.)

---

### Post by castrojo on 2009-06-16
There was a telepathy-butterfly release today to fix some MSN issues, so you'll have to wait until that's packaged in the PPA to try it (I don't use MSN so I can't confirm)

You'll want to use karmic or follow the Telepathy PPA, the one in Jaunty is already too old: [https://edge.launchpad.net/~telepathy/+archive/ppa](https://edge.launchpad.net/~telepathy/+archive/ppa)

---

### Post by shafin on 2009-06-16
> **taavikko said:**
> 
Empathy offers far more **potential** than pidgin all-around.
giving it enough time to fully evolve.
There you said it. Empathy has more *Potential*. Now pushing a thing merely on potential is certainly not what ubuntu does. It it was so, packagekit would have made it. Empathy needs to turn these *potentials* into **features**. Only then it can be used as default.

---

### Post by ricpelo on 2009-06-16
> **whiprush said:**
> There was a telepathy-butterfly release today to fix some MSN issues, so you'll have to wait until that's packaged in the PPA to try it (I don't use MSN so I can't confirm)

You'll want to use karmic or follow the Telepathy PPA, the one in Jaunty is already too old: [https://edge.launchpad.net/~telepathy/+archive/ppa](https://edge.launchpad.net/~telepathy/+archive/ppa)

Thanks for the info. I'd just installed the PPA's version of Empathy (2.27.2), although I still unable to login. I'll wait for an update in the PPA's packages. Until then, I need to stay in Pidgin.

---

### Post by super.rad on 2009-06-16
This doesn't make much difference for advanced users, it's easy enough to remove one and install the other if you want.
Now if you're a beginner trying to setup a Google Talk account, which looks easier

[U]Pidgin

[/U] [[IMG]http://s274.photobucket.com/albums/jj243/super_rad/th_pidgin.png[/IMG]]("http://i274.photobucket.com/albums/jj243/super_rad/pidgin.png")

_Empathy_

[[IMG]http://s274.photobucket.com/albums/jj243/super_rad/th_empathy.png[/IMG]]("http://i274.photobucket.com/albums/jj243/super_rad/empathy.png")

I've been using pidgin for years and still get confused when trying to setup a new google talk account.
Jabber is another one, on empathy you select Jabber from the menu then type your address and password, on pidgin it is called XMPP and you also have to fill in "Domain" and "Resource" which one is easier/clearer for a new user?
Yes empathy has some rough edges (obviously as it's a lot newer than gaim/pidgin) but loads of work has been going into it recently and with the hug day coming up hopefully most the bugs will be sorted long before karmic is released

---

### Post by ricpelo on 2009-06-16
> **ricpelo said:**
> Thanks for the info. I'd just installed the PPA's version of Empathy (2.27.2), although I still unable to login. I'll wait for an update in the PPA's packages. Until then, I need to stay in Pidgin.

Well, I've just compiled the latest git source of telepathy-butterfly, and I still can't login into my MSN account.

---

### Post by super.rad on 2009-06-16
New version of empathy is released (2.27.3) so you could either try compiling that or wait till it's packaged for ubuntu

---

### Post by ikkefc3 on 2009-06-16
Why not use Kopete as standard IM?

---

### Post by super.rad on 2009-06-16
> **ikkefc3 said:**
> Why not use Kopete as standard IM?
Because it would mean including kde/qt libarys.
It's default for Kubuntu

---

### Post by sabre2th on 2009-06-16
> **whiprush said:**
> I'm not saying you shouldn't have a different opinion. The spec clearly states that we are switching early and if it's not what we want by feature freeze then pidgin stays. In fact I want to hear your concerns, that's why I am here.

To use Ekiga you need a sip account, it's a softphone, there's no easy way for me to call my mom on gtalk, for example. The guts for this stuff (Telepathy) have been shipping on maemo tablets for a long time, it's just getting the final polish in on the desktop stuff to make it better that needs to be done. They kind of polish you can get by say, switching to something early in a development release so people can bang on it and report bugs.
I haven't used Empathy enough to have many specific concerns at the moment.  It was the 'cart before the horse' thing that had me thinking earlier.  Now it sounds like we're on the same page, so I'll back off... at least until the betas  :)

> **ikkefc3 said:**
> [s]Why not use Kopete as standard IM?[/s]
[s]I assume because it's a KDE app.  It wouldn't be worth the hassle for a standard Ubuntu/Gnome install.[/s]

Edit: Oops, too slow  :p

---

### Post by ricpelo on 2009-06-16
> **super.rad said:**
> New version of empathy is released (2.27.3) so you could either try compiling that or wait till it's packaged for ubuntu

[quote=whiptail]There was a telepathy-butterfly release today to fix some MSN issues, so you'll have to wait until that's packaged in the PPA to try it[/quote]

I just realized that I can solve the problem uninstalling telepathy-butterfly and using telepathy-haze instead. What's the point?

---

### Post by zekopeko on 2009-06-16
Including empathy would bring multiple benefits to users and ubuntu:

1. Ekiga removed. By doing this you consolidate your online presence on the desktop. No more multiple applications to do things with your friends. You can IM each other, video/audio chat, play games together, exchange music library information (a banshee plugin) and later even listen to it, all from one simple interface. Not to mention that part of the telepathy framework are being used in different applications. 
In future you could do some awesome stuff with empathy/telepathy.

2. By including empathy on the liveCD you can see that empathy devs want it included and are eager to fix the most glaring issues. The same can be said about banshee's devs who are targeting bugs that ubuntu said where show stoppers. By including it now we will only help the project mature faster.

3. Ubuntu is closer to upstream Gnome. That means less work for ubuntu developers.

4. There is no 4.

---

### Post by meborc on 2009-06-16
i understand that a large user base as ubuntu's is something to desire by people behind empathy and telepathy... but please, don't push things too soon... if a default app is changed, then only by something with the same working features and some extra

i see feature in empathy, but the title says it all... is it ready??? the latest one packaged for jaunty (so we could test it) does not let me log into msn... :) i know i know there is a new version... but guys, more QA before changing default app

it seems like a closed circle - a lot of ubuntu users = more QA = bad response from new users = less ubuntu users :)

it is not that simple, but you get my point :)

---

### Post by ricpelo on 2009-06-16
> **meborc said:**
> the latest one packaged for jaunty (so we could test it) does not let me log into msn...

Probably the same problem as me, only solved by removing telepathy-butterfly and installing telepathy-haze. Not very evident nor user friendly, IMHO...

---

### Post by 23meg on 2009-06-16
[QUOTE=meborc]but guys, more QA before changing default app[/QUOTE]

Hence the point of testing it in the development branch, which is what we're supposed to be doing as testers, and what this forum is about, right? 

Chanting "more QA!" from the sidelines doesn't help anything; as a tester (I assume you are one by the fact that you post to this forum) why don't you step in and help with it? We're getting some upstream attention to Empathy bugs in Ubuntu, which is always nice to have, and we have a Hug Day coming up; opportunities abound.

---

### Post by zekopeko on 2009-06-16
> **meborc said:**
> i see feature in empathy, but the title says it all... is it ready??? the latest one packaged for jaunty (so we could test it) does not let me log into msn... :) i know i know there is a new version... but guys, more QA before changing default app

it seems like a closed circle - a lot of ubuntu users = more QA = bad response from new users = less ubuntu users :)

it is not that simple, but you get my point :)

i'm guessing that you installed it from the ppa. if so then you are a part of QA. this ppa isn't default in ubuntu. barking any uploading mistakes. the fairest thing would be to judge empathy once it's released as 2.28. anything in between is just a development release. it would be like comparing ubuntu karmic dev to ubuntu karmic final. the whole point of the ppa and a development cycle is to test things. not to mention that karmic as every other ubuntu release will be getting 2.28.1 since ubuntu ships a month after a stable Gnome release so that will yet again have many bug fixes.

EDIT: damn 23meg beat me to the punch :D

---

### Post by Bou on 2009-06-16
> **23meg said:**
> Hence the point of testing it in the development branch, which is what we're supposed to be doing as testers, and what this forum is about, right?

Right. The right question here is not "is empathy ready" but "WILL empathy be ready when the time comes?"

The devs have stated that they'll push it to Karmic so that bugs be filled, and that if it's not ready at the end of the cycle they'll swap for pidgin again. So test it, file bugs and let's see how things end. But 14 pages of discussion about the state of things today? That really doesn't make sense.

---

### Post by Staz on 2009-06-16
> **ricpelo said:**
> Well, I've just compiled the latest git source of telepathy-butterfly, and I still can't login into my MSN account.
And it would help if you opened a bug with the log attached [1] rather than only complaining on the forum. Developers can't help you if you don't notify them of the problem.

[1] see here for how to obtain log information [http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging)

---

### Post by andrewabc on 2009-06-16
About 4-5 months ago I tried empathy because pidgin never connected to http msn. empathy did not connect either. I think only aMSN and another program were able to connect, but they looked terrible and crashed often.

With jaunty, pidgin connects to http msn. So hopefully empathy fixed the same bug for me.

---

### Post by ricpelo on 2009-06-17
> **Staz said:**
> And it would help if you opened a bug with the log attached [1] rather than only complaining on the forum. Developers can't help you if you don't notify them of the problem.

[1] see here for how to obtain log information [http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging)

I posted a bugreport on Launchpad several hours before you commented here.

[https://bugs.launchpad.net/bugs/388154](https://bugs.launchpad.net/bugs/388154)

I did not complaining. I answered a comment by whiprush about the recently fixes on telepathy-butterfly. That's all, right?

---

### Post by golusweet on 2009-06-17
Can anyone tell me, Is latest Empathy version available for Jaunty?:D

---

### Post by Nerd_bloke on 2009-06-17
> **ricpelo said:**
> I posted a bugreport on Launchpad several hours before you commented here.

[https://bugs.launchpad.net/bugs/388154](https://bugs.launchpad.net/bugs/388154)



Possibly a duplicate of [this bug]("https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/383562")?

---

### Post by yoasif on 2009-06-17
As of today, I can't connect to gtalk servers: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388522](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/388522)

also, someone mentioned a ppa in the other thread -- is this the one? [https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa) I don't see any karmic lines if so.

---

### Post by Staz on 2009-06-17
@ricpelo, sorry I didn't mean to offend you, it's just that I've seen a lot of theses "can't connect" comments and not that much feedback in actual bugs reports with info

> **Nerd_bloke said:**
> Possibly a duplicate of [this bug]("https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/383562")?
More or less.

There where three issues affecting MSN in empathy which just got fixed in butterfly 0.3.4 :
  * All users where shown as offline (which some mistook as not being connected)
  * You couldn't open a chat with any contact
  * And once this was fixed, you could open a chat but not close it and reopen it.

Theses all got fixed in butterfly 0.3.4, the package just landed in Debian and the Jaunty PPA so it shouldn't be long before it enter in karmic. (@yoasif, there is no PPA for karmic still the packages in it still get updated)

Now the big issues left are :
  * It crash right after adding a contact
  * Some issue with proxies
  * Can't chat with offline users

And the nice features :
  * Audio and Video chat : this is being worked on in another branch and is nearly ready. (Will definitely been here for Gnome 2.28)
  * File Transfers
  * Custom smiley,  etc...

note that I'm talking about butterfly and not haze which is the alternative backend for MSN which is based on Pidgin libs.

---

### Post by meborc on 2009-06-17
> **23meg said:**
> Hence the point of testing it in the development branch, which is what we're supposed to be doing as testers, and what this forum is about, right? 

Chanting "more QA!" from the sidelines doesn't help anything; as a tester (I assume you are one by the fact that you post to this forum) why don't you step in and help with it? We're getting some upstream attention to Empathy bugs in Ubuntu, which is always nice to have, and we have a Hug Day coming up; opportunities abound.

i have no problem with testing stuff... i have many ppa's enabled which provide me with the latest and the greatest... but was not the point in the discussion about changing a default app when the app that is going to be changed performes better (or same) at the moment??? and the title says - is it ready... so i am guessing we are talking about NOW not future :)

and of course i will file bugs, as soon as i get empathy to connect (soory guys :D) to my account

i believe that empathy should stay in ppa until it is ready to be the default... and people who like to test and file bugs can do it then also... no need to make it default now

---

### Post by zekopeko on 2009-06-17
> **meborc said:**
> i believe that empathy should stay in ppa until it is ready to be the default... and people who like to test and file bugs can do it then also... no need to make it default now

you are kidding right? by including it by default you can get bug reports and polish the application before it ships in karmic or karmic+1 (which is probably going to be LTS).

---

### Post by chrisccoulson on 2009-06-17
I haven't read through this whole thread, but perhaps the title should be changed to "Will empathy be ready to replace pidgin by release date?"

Whether Empathy is ready to replace Pidgin now or not is totally irrelevant. What matters is that Empathy is introduced as default now to increase testing coverage to make sure that it is ready to replace Pidgin by release date. There is no point in not doing that right now, just because Empathy is not ready at this moment in time. 

This is exactly what testers here are for.

---

### Post by zekopeko on 2009-06-17
> **chrisccoulson said:**
> I haven't read through this whole thread, but perhaps the title should be changed to "Will empathy be ready to replace pidgin by release date?"

Whether Empathy is ready to replace Pidgin now or not is totally irrelevant. What matters is that Empathy is introduced as default now to increase testing coverage to make sure that it is ready to replace Pidgin by release date. There is no point in not doing that right now, just because Empathy is not ready at this moment in time. 

This is exactly what testers here are for.

i find it funny that testers complain about testing :P

---

### Post by snkiz on 2009-06-17
> **Meson said:**
> 
Also, the Pidgin project sees the threat of Empathy's progress in audio/video and there is a big push to get these things working.  You also have to like Pidgin's philosphy a lot better too. It's about having a stand library libpurple, that handles all of the functionality and then any number of UIs that work with the library (GUI: pidgin, CLI: finch).


the last time I was in the pidgin.. um track I think they call it.
I got the impression that the dev's there are egotistical, closed minded and over all pushing their agenda to the community at large weather they wanted it or not (see the great protocol icon debate, witch thank god they finally caved on.) Unless thats changed I love to see pidgin get the boot. That being said It does what it does well, just don't suggest they are wrong about anything, or suggest they actually support modern features. I say we port Miranada it has plugins for everything you can think of.

---

### Post by 23meg on 2009-06-17
> **meborc said:**
> but was not the point in the discussion about changing a default app when the app that is going to be changed performes better (or same) at the moment??? and the title says - is it ready... so i am guessing we are talking about NOW not future :)

You're of course entitled to your strictly literal interpretation of the title, which I don't find very useful to discuss.

[QUOTE=meborc]and of course i will file bugs, as soon as i get empathy to connect (soory guys :D) to my account[/QUOTE]

If it can't connect, that can be a bug. Why not start by investigating / filing it, or adding to an existing report? Take a look at [http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging) before reporting.

[quote=meborc]i believe that empathy should stay in ppa until it is ready to be the default... and people who like to test and file bugs can do it then also... no need to make it default now[/QUOTE]

Why? What will we gain with this that will justify the testing coverage lost?

---

### Post by ghindo on 2009-06-18
It's happened.

---

### Post by meborc on 2009-06-18
> **zekopeko said:**
> you are kidding right? by including it by default you can get bug reports and polish the application before it ships in karmic or karmic+1 (which is probably going to be LTS).

i give up... you clearly did not understand my point... :) sorry, but i guess i am a minority here... so you win - happy now? :) lets kill this thread... if empathy replaced pidgin, there is no point for this discussion

move on and file bugs

---

### Post by michaelzap on 2009-06-18
Personally I've really grown to like and rely on Pidgin. It does everything that I need, and it does it well and reliably. Recent integration with the Fast User Switcher Applet made it a seamless part of the Ubuntu desktop.

Empathy doesn't do everything I need (OTR, metacontacts, plugins), and it does other things that I don't need and likely add unnecessary bloat (video and audio chat).

I know that the Pidgin developers can be difficult, and it certainly sounds as if Empathy is heading in the right direction, but I don't understand why some people are in such a rush to replace a tried-and-true program with one that still has training wheels.

---

### Post by ricpelo on 2009-06-18
> **ghindo said:**
> It's happened.

I can't believe it :(

---

### Post by super.rad on 2009-06-18
Surely empathy (and all related packages) should be on the newest versions as it's Empathy hug day so without the latest versions we don't know whats been fixed recently

---

### Post by [h2o] on 2009-06-18
> **michaelzap said:**
> Personally I've really grown to like and rely on Pidgin. It does everything that I need, and it does it well and reliably. Recent integration with the Fast User Switcher Applet made it a seamless part of the Ubuntu desktop.

Empathy doesn't do everything I need (OTR, metacontacts, plugins), and it does other things that I don't need and likely add unnecessary bloat (video and audio chat).
Then you can happily keep Pidgin installed and use that instead. Problem Solved.

> I know that the Pidgin developers can be difficult, and it certainly sounds as if Empathy is heading in the right direction, but I don't understand why some people are in such a rush to replace a tried-and-true program with one that still has training wheels.
I don't think it is fair to say that Empathy "still has training wheels" since it is clearly a very usable application and has been so for at least a year.
And since Pidgin will still be available for everyone who likes it better I don't see what the fuss is all about.
For a new unexperienced user Empathy will function just as well as Pidgin. If they need OTR or any other Pidgin feature then they will most likely find Pidgin and install it.

---

### Post by Changturkey on 2009-06-18
Is Empathy in the daily builds? Alpha 2?

---

### Post by super.rad on 2009-06-18
Alpha 2 still has pidign as default but as of todays daily builds empathy should be default

---

### Post by castrojo on 2009-06-18
Please make sure you're using the PPA to test empathy/telepathy, whatever is in Jaunty is already old! If you've reported a bug with empathy and using the PPA fixes this, then please don't leave your bug open/flailing, thanks!

[http://ubuntuforums.org/showthread.php?p=7478157#post7478157](http://ubuntuforums.org/showthread.php?p=7478157#post7478157)

EDIT: Forgot to mention, the bug day is today, so now's the time to file/triage bugs!

---

### Post by super.rad on 2009-06-18
> **whiprush said:**
> Please make sure you're using the PPA to test empathy/telepathy, whatever is in Jaunty is already old! If you've reported a bug with empathy and using the PPA fixes this, then please don't leave your bug open/flailing, thanks!

[http://ubuntuforums.org/showthread.php?p=7478157#post7478157](http://ubuntuforums.org/showthread.php?p=7478157#post7478157)

EDIT: Forgot to mention, the bug day is today, so now's the time to file/triage bugs!

Howcome karmic isn't using 2.27.3 and telepathy-butterfly 0.3.4
Until I get the newer version of telepathy-butterfly I can't do much as all my contacts are shown as offline

---

### Post by castrojo on 2009-06-18
> **super.rad said:**
> Howcome karmic isn't using 2.27.3 and telepathy-butterfly 0.3.4

It's behind right now, but Ken Van Dine has a PPA for Karmic here in the meantime: [https://launchpad.net/~ken-vandine/+archive/ppa](https://launchpad.net/~ken-vandine/+archive/ppa)

Tried to get it all set for Karmic by the bug day but that didn't happen. :-/

---

### Post by super.rad on 2009-06-18
Thanks, at least with the newest version I can see my contacts so can now help out with the bug day

---

### Post by michaelzap on 2009-06-18
> **whiprush said:**
> Please make sure you're using the PPA to test empathy/telepathy, whatever is in Jaunty is already old! If you've reported a bug with empathy and using the PPA fixes this, then please don't leave your bug open/flailing, thanks!

[http://ubuntuforums.org/showthread.php?p=7478157#post7478157](http://ubuntuforums.org/showthread.php?p=7478157#post7478157)

EDIT: Forgot to mention, the bug day is today, so now's the time to file/triage bugs!
When I add that PPA and try to do an upgrade I'm told I can only do a partial upgrade. So I try that and get an authentication error and the upgrade manager quits. I've added the repository key - what else do I need to do to complete this upgrade?

(running Jaunty 64-bit)

---

### Post by castrojo on 2009-06-18
I need to know what it's holding back, please paste in what "apt-get upgrade" spits out.

---

### Post by michaelzap on 2009-06-18
> **whiprush said:**
> I need to know what it's holding back, please paste in what "apt-get upgrade" spits out.

```
zap@bicho:~$ sudo apt-get upgrade
[sudo] password for zap: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  empathy libempathy-common libempathy-gtk-common
  linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
zap@bicho:~$ 
```

---

### Post by taavikko on 2009-06-18
> **michaelzap said:**
> ```
zap@bicho:~$ sudo apt-get upgrade
[sudo] password for zap: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  empathy libempathy-common libempathy-gtk-common
  linux-generic linux-headers-generic
  linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
zap@bicho:~$ 
```

Use "apt-get dist-upgrade" if in doubt, paste the output of it here for confirmation.
As "apt-get upgrade" doesn't install new dependencies.

---

### Post by pferraro on 2009-06-18
> **whiprush said:**
> Please make sure you're using the PPA to test empathy/telepathy, whatever is in Jaunty is already old! If you've reported a bug with empathy and using the PPA fixes this, then please don't leave your bug open/flailing, thanks!

[http://ubuntuforums.org/showthread.php?p=7478157#post7478157](http://ubuntuforums.org/showthread.php?p=7478157#post7478157)

EDIT: Forgot to mention, the bug day is today, so now's the time to file/triage bugs!

Neither that PPA, nor the Karmic repo contains the latest version of empathy (2.27.3).  Surely "bug day" be more productive if we used the latest beta release, no?

---

### Post by super.rad on 2009-06-18
> **whiprush said:**
> It's behind right now, but Ken Van Dine has a PPA for Karmic here in the meantime: [https://launchpad.net/~ken-vandine/+archive/ppa]("https://launchpad.net/%7Eken-vandine/+archive/ppa")

Tried to get it all set for Karmic by the bug day but that didn't happen. :-/
Was posted on the last page

---

### Post by Bou on 2009-06-18
I've realised 2.27.3 lacks some advertised features, ie. geolocalisation and desktop sharing.

---

### Post by super.rad on 2009-06-18
yeah I was looking for those, shame as they sounded interesting

---

### Post by Bou on 2009-06-18
Would it be adequate to open a new thread commenting on the bug reports we make? I really want to like the app, but it does have a lot of holes right now.

---

### Post by castrojo on 2009-06-18
> **pferraro said:**
> Neither that PPA, nor the Karmic repo contains the latest version of empathy (2.27.3).  Surely "bug day" be more productive if we used the latest beta release, no?

The Telepathy PPA is run by the Empathy/Telepathy upstream guys, they update it to be useful for them, they'll probably update it when they want people to test the newer stuff.

---

### Post by michaelzap on 2009-06-18
> **taavikko said:**
> Use "apt-get dist-upgrade" if in doubt, paste the output of it here for confirmation.
As "apt-get upgrade" doesn't install new dependencies.

Thanks. That seems to be working (downloading now). Not sure why the GUI Update Manager couldn't do this, but command lines are fine, too.

---

### Post by Staz on 2009-06-18
> **Bou said:**
> I've realised 2.27.3 lacks some advertised features, ie. geolocalisation and desktop sharing.
Geolocalisation is a compilation option, it just mean the maintainer of the package did not enable it. 
Desktop sharing is implemented in patch for Vino and Vinagre and doesn't have any direct code in empathy (but of course you need it to run for this to works).


> **whiprush said:**
> The Telepathy PPA is run by the Empathy/Telepathy upstream guys, they update it to be useful for them, they'll probably update it when they want people to test the newer stuff.
Packages from the PPA are updated as soon as the new versions enter Karmic (or Debian Exp I don't remember) since the PPA packages are based on it. And as soon the PPA maintainers have the time to do it of course
There is really no complicated agenda behind this, we want new versions packaged as fast as we can since we use them as well ;) (most of the Telepathy dev I know run Ubuntu)

---

### Post by Paul21 on 2009-06-18
> **DPic said:**
> Empathy is GREAT for most users, especially **new** ones, and it can replace poth pidgin AND ekiga. It lacks features only more hardcore users (yes, i just referred to some IM users as hardcore) like meta contacts, which is on the way as well. It is simple and integrates well, and we want to make Ubuntu friendly for NEW users. Old users who prefer the clutter and feature madness of pidgin will simply install it from Add/Remove.

Would you call MSN users "hardcore users" as well? Because as far as I see, **empathy lacks of almost all MSNP basic features**. You can't see custom smileys (neither save them of course), you can't set a personal message/status. You can't even set your msn picture. It's 2009 and some features are a MUST nowadays. And these are features that almost every MSN user want and take for granted (and don't let me start with teenage users... )

So, you say that it is great for new users, but in the real world (unfortunately) many many people use Live Messenger. What about them?

The default UI has serious issues as well. For instance, to insert a smiley you have to go to *Conversation menu -> Insert smiley* instead of having a simple button widget on your conversation window to do this.

> **DPic said:**
> If Ubuntu switched to Empathy, it's development is going to get a huuuggggeee boost so the feature gap will close and eventaully reverse.

I agree, but I'm not sure if switching to it so soon is the best choice. I hope it is.

---

### Post by super.rad on 2009-06-18
> **Paul21 said:**
> You can't see custom smileys (neither save them of course)

 you can't set a personal message/status. 

You can't even set your msn picture. 


Support for custom smileys is being worked on, will be ready before karmic is released.
You can set a personal message and change your display name/picture.

Which version are you using?

---

### Post by castrojo on 2009-06-18
> **Staz said:**
> Packages from the PPA are updated as soon as the new versions enter Karmic (or Debian Exp I don't remember) since the PPA packages are based on it. And as soon the PPA maintainers have the time to do it of course There is really no complicated agenda behind this, we wanted new versions packaged as fast as we can since we use them as well ;) (most of the Telepathy dev I know run Ubuntu)

It looks like debian experimental. Thanks for clearing this up.

---

### Post by castrojo on 2009-06-18
> **Paul21 said:**
> I agree, but I'm not sure if switching to it so soon is the best choice. I hope it is.

Guys, there's a reason we have a development release and why we're doing this so early in the cycle. The reason Karmic exists right now is to experiment and break things, be bold, zig instead of zag, etc ...

---

### Post by Changturkey on 2009-06-18
So how is support for MSN in Empathy? Will it support Windows Live Groups? "Now Playing" messages?

---

### Post by Paul21 on 2009-06-18
> **super.rad said:**
> Support for custom smileys is being worked on, will be ready before karmic is released.
You can set a personal message and change your display name/picture.

Which version are you using?

Sorry I've been testing 2.26.1, now you can see why I was so worry about the whole thing.

My apologies.

---

### Post by super.rad on 2009-06-18
Personal messages and display pictures are all in 2.26

---

### Post by deathsshadow77 on 2009-06-18
my issue with empathy is the lack of file transfers. Pidgin has file transfers and changing to empathy would be quite a step back in this area(unless of course file transfers were added in the near future).

Audio/Video for AIM would be awesome

---

### Post by rudenko_ruslan on 2009-06-19
[https://launchpad.net/ubuntu/karmic/+source/ubuntu-meta/1.147](https://launchpad.net/ubuntu/karmic/+source/ubuntu-meta/1.147)

Huh, Pidgin is back, Empathy removed from desktop-recommends.

---

### Post by Nerd_bloke on 2009-06-19
Webcam support needs video codecs, getting these onto the Ubuntu install CD is the current [issue.]("https://bugs.launchpad.net/ubuntu/+source/telepathy-farsight/+bug/388898")

---

### Post by aamukahvi on 2009-06-19
> **rudenko_ruslan said:**
> [https://launchpad.net/ubuntu/karmic/+source/ubuntu-meta/1.147](https://launchpad.net/ubuntu/karmic/+source/ubuntu-meta/1.147)

Huh, Pidgin is back, Empathy removed from desktop-recommends.

If you read what the reason is you will find that it's just temporary, until all required bits are in *main*.

---

### Post by ricpelo on 2009-06-19
> **Staz said:**
> @ricpelo, sorry I didn't mean to offend you, it's just that I've seen a lot of theses "can't connect" comments and not that much feedback in actual bugs reports with info


No problem, don't worry ;)

---

### Post by ghindo on 2009-06-19
> **aamukahvi said:**
> If you read what the reason is you will find that it's just temporary, until all required bits are in *main*.Exactly.  See:  [https://bugs.launchpad.net/ubuntu/+source/telepathy-farsight/+bug/388898](https://bugs.launchpad.net/ubuntu/+source/telepathy-farsight/+bug/388898)

---

### Post by descendent87 on 2009-06-22
can we at least get empathy 2.27.3, if were supposed to be testing it then surely we should have the newest version (and all latest version of related packages, telepathy-butterfly etc)

---

### Post by AdrianTM on 2009-06-22
How about encryption, facebook chat? Does empathy have them? If it doesn't is useless to me.

---

### Post by chriswyatt on 2009-06-23
It's possible to get Facebook Chat running through Telepathy-Haze, there are some commands in this thread that make it very simple:

[http://ubuntuforums.org/showthread.php?t=973830](http://ubuntuforums.org/showthread.php?t=973830)

---

### Post by ildella on 2009-06-23
I have been able to use facebook haze in empathy, but is more complicated that adding the facebook chat to pidgin for the average user that can at least use synaptic.

with sofiasip I also added a SIP account but it just do not work, without providing feedback. I do not even know how to make a call to a custom number and I cannot add a new SIP contact. 

So, pidgin works very fine as multi-IM and ekiga works quite fine as a SIP client. 
Empathy is worst than both in respective fields but is the only one that can manage IM and SIP and the perspective to use people-project is exciting but is at least one year from now. 

My opinion is that empathy 2.26 is not comparable to pidgin+ekiga today The twos give works as a breeze but a latency problem in ekiga due to some pulseaudio issues, AFAIK.

---

### Post by zekopeko on 2009-06-23
> **ildella said:**
> My opinion is that empathy 2.26 is not comparable to pidgin+ekiga today The twos give works as a breeze but a latency problem in ekiga due to some pulseaudio issues, AFAIK.

there is only one problem with this statement. You should be testing Empathy 2.27.x (to be 2.28 ) not 2.26.

---

### Post by ildella on 2009-06-25
> **zekopeko said:**
> there is only one problem with this statement. You should be testing Empathy 2.27.x (to be 2.28 ) not 2.26.

I am now using 2.27.3 from ppa, update today. 

Well.. not good news. He put a lot of contacts out of facebook group, in a sort of "ungrouped" area. And I cannot move them anywhere. 

the sip plugin is not new, and I continue not to understand how to make or receive sip calls.

according to [http://live.gnome.org/Empathy/Roadmap](http://live.gnome.org/Empathy/Roadmap) I see:

# Port to GtkBuilder
its not a user feature

# Adium theme support.
not exactly a "killer" feature

# Geolocation.
wow but... what?

# New presence chooser widget. 
where, exaclty?

and they are actually cleaning up and writing doc and fixing bugs... so no new features at all. It seems that telepathy 2.28 will be almost the same as 2.26, and that the game is to push it to the users to have feedback for the next relases. Also, Empathy is "easier" and less confusing to the average user, I agree, but maybe same result could be obtained cleaning up pidgin. 

So, in the end, for me as user, it seems that pidgin+ekiga is still better.
For an average user, maybe it is not a bad choice, but I am not sure at all now seeing empathy being still an incomplete product.

---

### Post by Joe_Bishop on 2009-06-25
>  I agree, but maybe same result could be obtained cleaning up pidgin.
Pidgin is bloated and it's devs are hard to contact.
// Very exciting with adium theme support, absolutely love it.

---

### Post by yelo3 on 2009-06-25
Sorry, but what are you expecting from empathy? What features are you looking for?

---

### Post by ildella on 2009-06-25
> **yelo3 said:**
> Sorry, but what are you expecting from empathy? What features are you looking for?

Well, given that here we are discussing about the switch from pidgin+ekiga to empathy, I expect that empathy offers the same functionality of the twos, at least. 

On empathy, now, it seems that facebook chat is really hard to install for the average user, that I cannot even understand how to use the SIP plugin to make or receive calls. 

I think that voip and facebook are two key feature today and I can have them easily with the other two software. I think that if empathy cannot have this two features for 2.28, it will not be a serious replace. 

Maybe developer have more knowledge about the desires of the users and facebook/voip are not at the top, but I doubt.

---

### Post by chriswyatt on 2009-06-25
I personally don't think it's ready yet but I kind of support it being included in the new Ubuntu, it will really help development.  Many of the Pidgin devs appear to be pretty arrogant and don't really listen to their userbase so I'm in support of a replacement personally.

---

### Post by ildella on 2009-06-25
> **chriswyatt said:**
> I personally don't think it's ready yet but I kind of support it being included in the new Ubuntu, it will really help development.  Many of the Pidgin devs appear to be pretty arrogant and don't really listen to their userbase so I'm in support of a replacement personally.

Yep, I am sure that many consideration have to be done, not just the features. I was just restricting my observation to that field. 

I am sure that the feedback that could come with the inclusion as official IM in the karmic  is more valuable in the medium running than leaving some features back in the short. I do not know the underlying technology (telepaty) to say if this is a right technological choice, so I have to trust ubuntu developers :)

---

### Post by golusweet on 2009-06-25
Empathy's Interface looks terrible. It should be changed, so that users would interact with it easily.

I know, there's adium support now, it's buggy right now. I don't like smiley's in Empathy as well. User has to insert that.

It's still an early project, and will continue to improve.

I hope, they will make it better.

I would stick with pidgin for now.

---

### Post by philcamlin on 2009-06-25
i like pidgen :popcorn:

---

### Post by arindom on 2009-06-25
I have been using Empathy for sometime now. The feature that attracted me was the Voice and Video calls with my Gmail contacts. 

From my experience it seems there are some improvements needed for Empathy but at the same time I will say that great development effort is on many bugfixes are happening. That means we can assume that by the time Karmic releases Empathy will be more improved and should be ready to be used by a broad user base. 

The best part is as mentioned already by another user here, and that is the Video/Voice call. As per my understanding Pidgin is not going to have that feature in near future, so I will go for Empathy surely.

I only have a small wishlist which probably are already there for Empathy.
a) Some kind of Guification like notification system for Empathy. When one logs in / out, goes idle we should get some notification.

b) If someone pings me, the message window should pop up automatically. 

c) New mail arrival notification on Empathy.

---

### Post by chriswyatt on 2009-06-25
One thing that's been bugging me about Empathy is the size of the chat windows.  They're teeny and you have to resize them every time you start a conversation with someone new.  Also I'm finding the chat windows a little ugly at the moment but of course things will improve.

---

### Post by pferraro on 2009-06-25
> **yelo3 said:**
> sorry, but what are you expecting from empathy? What features are you looking for?
otr

---

### Post by descendent87 on 2009-06-25
I've never understood why people need otr so badly. Never used it myself but then I never have conversations that I'd need/want to be digitally signed, I don't need confirmation that the person I'm talking to is really them and if someone else managed to read my conversation then really all they'd learn from it is what I've been upto and what I have planned lol
Can someone explain why you would need otr?
Surely if your conversation is that private then just talk to them face to face

---

### Post by Joe_Bishop on 2009-06-25
> **chriswyatt said:**
> One thing that's been bugging me about Empathy is the size of the chat windows.  They're teeny and you have to resize them every time you start a conversation with someone new.
I've set its size only once.
>   Also I'm finding the chat windows a little ugly at the moment but of course things will improve.
In my opinion it's not ugly, it's very minimalistic. Pidgin chat window is really ugly, yeah.

---

### Post by dro0g on 2009-06-25
> **descendent87 said:**
> I've never understood why people need otr so badly. Never used it myself but then I never have conversations that I'd need/want to be digitally signed, I don't need confirmation that the person I'm talking to is really them and if someone else managed to read my conversation then really all they'd learn from it is what I've been upto and what I have planned lol
Can someone explain why you would need otr?
Surely if your conversation is that private then just talk to them face to face

You should spend some time sitting in a coffee shop reading people's e-mails, IMs, Facebook messages, etc. as they fly through the air - I think you'd be surprised at the amount of information most people disclose over those mediums. Also, a good time can be had injecting or modifying text in said messages :) (hypothetically speaking of course)

An awful lot of companies now log IM traffic as well. Sure you may feel you have nothing to hide, but personally I'd rather be safe than sorry.

---

### Post by chriswyatt on 2009-06-25
Yep, just because you don't send confidential information doesn't mean others don't as well.  That's quite a major oversight really.

---

### Post by philcamlin on 2009-06-25
what if they put both :D

---

### Post by michaelzap on 2009-06-25
> **descendent87 said:**
> Can someone explain why you would need otr?

To protect privacy and confidentiality, obviously. To be able to communicate password or credit card info. For all sorts of reasons, OTR is a must-have feature for me and I think that Ubuntu's default IM client should certainly be capable of encryption for those of us who use and require it.

---

### Post by descendent87 on 2009-06-25
Empathy will support OTR, not sure if it will be by 2.28 but it is planned.
If it's not ready by the time karmic is released then it's not hard for the people that need OTR to remove empathy and install pidgin.
I don't think this is any reason to stop it being default for karmic as I'd imagine most new users wouldn't require OTR

---

### Post by teddks on 2009-06-26
> **descendent87 said:**
> Empathy will support OTR, not sure if it will be by 2.28 but it is planned.
If it's not ready by the time karmic is released then it's not hard for the people that need OTR to remove empathy and install pidgin.
I don't think this is any reason to stop it being default for karmic as I'd imagine most new users wouldn't require OTR

Would you back removing a mail client that had GnuPG support and replacing it with one that didn't, because you "imagine most new users wouldn't require GnuPG"?

Really, if we start cutting features because people that don't know about them don't use them, we're just ensuring that these ignorant users (which is the real meaning of "new users" in the context of this thread) will stay ignorant.

---

### Post by Amaranth on 2009-06-26
If a new mail client came along that was really awesome but was missing one important feature (GnuPG support) and there was a plan to implement it I'd probably vote for it being the new default, assuming it was good enough at everything else to make it worth switching.

---

### Post by qamelian on 2009-06-26
> **Amaranth said:**
> If a new mail client came along that was really awesome but was missing one important feature (GnuPG support) and there was a plan to implement it I'd probably vote for it being the new default, assuming it was good enough at everything else to make it worth switching.
Unfortunately, for some of us, that is not an acceptable answer. If a feature is a requirement now, and that feature is not available, then the product being considered is no longer an option. If the default app for a given purpose doesn't meet my needs, that app is getting yanked. 

Personally, I actively hate Empathy and have no intention of using it unless it can do everything, without exception, that I am able to do with Pidgin. If it is missing features that I rely on, it is worthless to me and that is, in fact, where Empathy stands right now. I also find it hideously unstable and it doesn't seem to be able to maintain a stable connection to any of the IM protocols that I routinely use. By comparison, Pidgin is bullet-proof on all my systems and wins hands down in every category that matters to me.

---

### Post by snkiz on 2009-06-26
thats the beauty of Linux just because it came with a program to do a task doesn't mean you have to use it. Example: I don't think I've ever started evolution on my machine. I was using Thunderbird an now have switched to gmail both were easy to integrate into my desktop. I think Ubuntu is looking at the long view of this, sure empathy isn't quite ready, but its coming along. And as a project empathy is more receptive to the Ubuntu way.

---

### Post by blackxored on 2009-06-26
IMHO I'd stick to pidgin. Empathy seems to be lacking some features, I had problems connecting it to MSN and XMPP, and I see pidgin much more stable.

---

### Post by qamelian on 2009-06-26
> **snkiz said:**
> thats the beauty of Linux just because it came with a program to do a task doesn't mean you have to use it. Example: I don't think I've ever started evolution on my machine. I was using Thunderbird an now have switched to gmail both were easy to integrate into my desktop. I think Ubuntu is looking at the long view of this, sure empathy isn't quite ready, but its coming along. And as a project empathy is more receptive to the Ubuntu way.
That doesn't excuse swapping a default app for one with reduced funtionality. WHen Ubuntu was first introduced, one of the goals that was touted was to provide, out of the box, a suite of "best of breed" apps to accommodate the most common desktop tasks. In my opinion, Empathy does not meet that goal at this poiint. When it does acchieve that goal, I will have no objection. At the moment though, I consider the app to still be too far behind Pidgin to be considered useable for my needs. There are still too many things missing or not functioning correctly for me to consider it otherwise.

---

### Post by snkiz on 2009-06-26
pidgin isn't flawless, I haven't been able to login to yahoo for a month and a half. In my opinion the definition of best of breed is more than how the program works. but I'm about to rant so.. to each his own :)

---

### Post by Zlatan on 2009-06-27
> **qamelian said:**
> That doesn't excuse swapping a default app for one with reduced funtionality. WHen Ubuntu was first introduced, one of the goals that was touted was to provide, out of the box, a suite of "best of breed" apps to accommodate the most common desktop tasks. In my opinion, Empathy does not meet that goal at this poiint. When it does acchieve that goal, I will have no objection. At the moment though, I consider the app to still be too far behind Pidgin to be considered useable for my needs. There are still too many things missing or not functioning correctly for me to consider it otherwise.

there's no empathy in any official ubuntu release, as far as i know. when it will be there, you can complain on that. now you can help developers to give empathy all functionality you want it to have. all i want to say is that you complain too early.

---

### Post by gnomeuser on 2009-06-27
The following posting from one of the telepathy-butterfly developers [should clarify just what the plans are](http://lists.freedesktop.org/archives/telepathy/2009-June/003403.html) for that protocol and empathy.

I am pretty happy seeing that plan, it fills all the holes I have in MSN support with existing clients and adds a UI that is integrated and which I love.

---

### Post by change_mode on 2009-06-28
Generally I support changing to a messenger that is more suited to gnome, but the change should only be made when Empathy supports ALL the basic features. That includes offline messaging, file transfers and some basic preferences.

My main problem with the Empathy version in Jaunty is the lack of options.

- can't change away behaviour
- can't disable logging
- ICQ failed to connect and I had to restart the program, because of the missing reconnect option...

If you want simplicity for the average user, choose good default options and give them a button to reset to default in case they mess up.
Advanced users however should still be able to customize the program at least as much as Pidgin (without plugins) allows.

---

### Post by Joe_Bishop on 2009-06-28
> - can't disable logging
why? It's too specific, I haven't ever met people who needs in disabling
> - ICQ failed to connect and I had to restart the program, because of the missing reconnect option...
F4, then unset and set check for ICQ account.
> Advanced users however should still be able to customize the program at least as much as Pidgin (without plugins) allows.
"advanced" users use good xmpp client (gajim, psi, jabbim, etc) with transports, Pidgin is a crap.

---

### Post by yelo3 on 2009-06-28
> **gnomeuser said:**
> The following posting from one of the telepathy-butterfly developers [should clarify just what the plans are](http://lists.freedesktop.org/archives/telepathy/2009-June/003403.html) for that protocol and empathy.

I am pretty happy seeing that plan, it fills all the holes I have in MSN support with existing clients and adds a UI that is integrated and which I love.

He is not a telepathy-butterfly developer, so there is no plan. Anyway I reported lots of bugs upstream, and there are 2 critical ones too, but they don't seem to answer. Is butterfly still an alive project?

---

### Post by qamelian on 2009-06-28
> **Zlatan said:**
> there's no empathy in any official ubuntu release, as far as i know. when it will be there, you can complain on that. now you can help developers to give empathy all functionality you want it to have. all i want to say is that you complain too early.
Why should I do that when I already have an application that does everything I want and does it well? I have no vested interest in Empathy. It has nothing to offer me.

---

### Post by [h2o] on 2009-06-29
> **qamelian said:**
> Why should I do that when I already have an application that does everything I want and does it well? I have no vested interest in Empathy. It has nothing to offer me.
If you have an application that does everything you need, and no one is trying to force you to use anything else, then why are you complaining?
This decision will not have any effect on you what so ever, unless everyone suddenly switches to Empathy and Pidgin development stalls, which is unlikely considering the fair amount of whining that have cropped up in all the "OMG!11! They are removing Pidgin"-threads...

---

### Post by qamelian on 2009-06-29
> **'[h2o] said:**
> If you have an application that does everything you need, and no one is trying to force you to use anything else, then why are you complaining?
This decision will not have any effect on you what so ever, unless everyone suddenly switches to Empathy and Pidgin development stalls, which is unlikely considering the fair amount of whining that have cropped up in all the "OMG!11! They are removing Pidgin"-threads...
I'm complaining because the plan *is* to make Empathy the default, if you have been paying attention. I consider this to be an incredibly stupid move and as a member of this community, it is both my right and privilege to voice my opinion. If you don't like my opinion, ignore it or provide a rational refutation to convince me my opinion needs to be rethought. A long as Empathy is incapable of providing the features I use and cannot maintain a stable connection on any IM protocol, which has been my experience, I cannot consider it to be a valid replacement for the current default application. Why is that so difficult to understand?

---

### Post by [h2o] on 2009-06-29
> **qamelian said:**
> I'm complaining because the plan *is* to make Empathy the default, if you have been paying attention. I consider this to be an incredibly stupid move and as a member of this community, it is both my right and privilege to voice my opinion. If you don't like my opinion, ignore it or provide a rational refutation to convince me my opinion needs to be rethought.
I think others have done a great job explaining why it is a good idea, but ok, here are my reasons why I think it is a good idea:
[LIST]
[*]Empathy uses Telepathy which will be really interesting as more and more programs adopt it.
[*]Empathy integrates very well with Gnome, being part of the project and all. But sure, Pidgin does this as well.
[*]Making Empathy default in Ubuntu will givet it the attention it needs to get up to par with Pidgin where features are concerned.
[*]Feature-wise Empathy might be behind Pidgin, but it seems to me that the features missing in Empathy (OTR, emoticons or what ever) is easier to add than the features missing in Pidgin (Voice/video).
[/LIST]

>  A long as Empathy is incapable of providing the features I use and cannot maintain a stable connection on any IM protocol, which has been my experience, I cannot consider it to be a valid replacement for the current default application. Why is that so difficult to understand?
The Empathy version in Jaunty works very well for me. Yes, there are issues, but not much more than what I had in Pidgin.

---

### Post by qamelian on 2009-06-29
> **'[h2o] said:**
> I think others have done a great job explaining why it is a good idea, but ok, here are my reasons why I think it is a good idea:
[LIST]
[*]Empathy uses Telepathy which will be really interesting as more and more programs adopt it.
[*]Empathy integrates very well with Gnome, being part of the project and all. But sure, Pidgin does this as well.
[*]Making Empathy default in Ubuntu will givet it the attention it needs to get up to par with Pidgin where features are concerned.
[*]Feature-wise Empathy might be behind Pidgin, but it seems to me that the features missing in Empathy (OTR, emoticons or what ever) is easier to add than the features missing in Pidgin (Voice/video).
[/LIST]


The Empathy version in Jaunty works very well for me. Yes, there are issues, but not much more than what I had in Pidgin.
The Empathy version in Jaunty does not run well on any of the 6 systems I have tested it on. It fails to maintain a connection to MSN, Google Talk, and Yahoo. None of these connection persists for more than 10 to 15 minutes. On Pidgin. with the exception of the recent Yahoo issue, all three of these protocols persist and are pretty much bullet-proof. None of the items you mention above are of any use to me and are, therefore, not compelling reasons for me to consider Empathy acceptable. 

Empathy may be preferred by some users, and I respect that, but for my needs it is a step backwards that is unacceptable. If Empathy becomes the default, I'll simply remove it and install Pidgin. Pidgin meets *my* needs and Empathy doesn't. Is that really so difficult to accept and understand?

---

### Post by zekopeko on 2009-06-29
> **qamelian said:**
> The Empathy version in Jaunty does not run well on any of the 6 systems I have tested it on. It fails to maintain a connection to MSN, Google Talk, and Yahoo. None of these connection persists for more than 10 to 15 minutes. On Pidgin. with the exception of the recent Yahoo issue, all three of these protocols persist and are pretty much bullet-proof. None of the items you mention above are of any use to me and are, therefore, not compelling reasons for me to consider Empathy acceptable. 

Empathy may be preferred by some users, and I respect that, but for my needs it is a step backwards that is unacceptable. If Empathy becomes the default, I'll simply remove it and install Pidgin. Pidgin meets *my* needs and Empathy doesn't. Is that really so difficult to accept and understand?

any links to bugs you reported or contributed with info that are manifested on your setup? until you post/create them you are simply counter-productive to the ubuntu community.

---

### Post by steeleyuk on 2009-06-29
> **qamelian said:**
> The Empathy version in Jaunty does not run well on any of the 6 systems I have tested it on.

Which version? Its been mentioned about 10 times in this thread that the one in Jaunty is out of date. You need to test using the version from the Empathy PPA (i.e. Version **2.27.3**)

---

### Post by sabre2th on 2009-06-29
> **'[h2o] said:**
> I think others have done a great job explaining why it is a good idea, but ok, here are my reasons why I think it is a good idea:
[LIST]
[*]Empathy uses Telepathy which will be really interesting as more and more programs adopt it.
[*]Empathy integrates very well with Gnome, being part of the project and all. But sure, Pidgin does this as well.
[*]**Making Empathy default in Ubuntu will givet it the attention it needs to get up to par with Pidgin where features are concerned.**
[*]Feature-wise Empathy might be behind Pidgin, but it seems to me that the features missing in Empathy (OTR, emoticons or what ever) is easier to add than the features missing in Pidgin (Voice/video).
[/LIST]


The Empathy version in Jaunty works very well for me. Yes, there are issues, but not much more than what I had in Pidgin.
If and when Empathy has the basic features it needs to fill in for Pidgin, then it can become the default.  It should not be the default until it works consistently with all the major protocols.

Just like there's nothing stopping us from continuing to use Pidgin, there is nothing stopping people from installing Empathy on their own.  Voice and video are good features to have, but we should not sacrifice basic text just to get them.  Let Empathy mature, then switch.  I don't understand the sudden rush to change it.

---

### Post by [h2o] on 2009-06-29
> **qamelian said:**
> Empathy may be preferred by some users, and I respect that, but for my needs it is a step backwards that is unacceptable. If Empathy becomes the default, I'll simply remove it and install Pidgin. Pidgin meets *my* needs and Empathy doesn't. Is that really so difficult to accept and understand? No, and that is why we keep reiterating that people who don't want to use Empathy can happily keep using Pidgin for as long as you like. Just like I will keep using Empathy regardless of whether it is the Ubuntu default or not.

---

### Post by steeleyuk on 2009-06-29
> If and when Empathy has the basic features it needs to fill in for Pidgin, then it can become the default. It should not be the default until it works consistently with all the major protocols.

Which is the whole point of the development cycle and why no decision has been made yet...

---

### Post by qamelian on 2009-06-29
> **steeleyuk said:**
> Which version? Its been mentioned about 10 times in this thread that the one in Jaunty is out of date. You need to test using the version from the Empathy PPA (i.e. Version **2.27.3**)
I also have 2.27.3 on one test box and it still behaves the same way. Anyway, I can't be bothered with this thread anymore. Whatever happens happens. I simply won't use an application that is, in my opinion, not up to par. I also won't waste anymore of my time installing it on test boxes only to be frustrated by its failings. 

And for the poster who asked for links to bugs I filed: I didn't need to. Other users had already reported all of the same bugs I was experiencing. There was no reason for me to open new bugs. Use what you like. Empathy is not for me.

---

### Post by [h2o] on 2009-06-29
> **sabre2th said:**
> Let Empathy mature, then switch.  I don't understand the sudden rush to change it.
The reason mentioned have been that making it default in the current development version of Ubuntu will make lots of people test it, find bugs and make it a kickass application. It has (I believe) been said that unless it works ok it won't be the default once karmic is actually released.

So, everyone is basically whining over something that has not yet happened.

---

### Post by zekopeko on 2009-06-29
> **qamelian said:**
> And for the poster who asked for links to bugs I filed: I didn't need to. Other users had already reported all of the same bugs I was experiencing. There was no reason for me to open new bugs. Use what you like. Empathy is not for me.

do re-read what i posted. you could have contributed either by posting new info or simply up voting the bug.

---

### Post by zekopeko on 2009-06-29
> **'[h2o] said:**
> The reason mentioned have been that making it default in the current development version of Ubuntu will make lots of people test it, find bugs and make it a kickass application. It has (I believe) been said that unless it works ok it won't be the default once karmic is actually released.

So, everyone is basically whining over something that has not yet happened.

the same thing happend with the dark theme in hardy(?). it wasn't the default in the end but it did help Gnome devs find bugs in GTK+ rendering of dark themes.

---

### Post by sabre2th on 2009-06-29
> **'[h2o] said:**
> The reason mentioned have been that making it default in the current development version of Ubuntu will make lots of people test it, find bugs and make it a kickass application. It has (I believe) been said that unless it works ok it won't be the default once karmic is actually released.

So, everyone is basically whining over something that has not yet happened.
I understand that and that's why I haven't been overly vocal, but there's some unjustified 'rah rah Empathy' crap flying around this thread.  People need to be realistic about it and try to see both sides of the argument.

---

### Post by michaelzap on 2009-06-29
> **sabre2th said:**
> ...but there's some unjustified 'rah rah Empathy' crap flying around this thread.  People need to be realistic about it and try to see both sides of the argument.

+1000

Really, people. Take a step back and stop calling anyone who disagrees with you a "whiner" or "complainer". The title of this post is a question, and at a minimum no one should be flamed for answering that question as they choose.

---

### Post by qamelian on 2009-06-29
> **zekopeko said:**
> do re-read what i posted. you could have contributed either by posting new info or simply up voting the bug.
Which I did. I love how the assumption usually seems to be that a user griping about bugs has done nothing about it to help.

---

### Post by zekopeko on 2009-06-29
> **qamelian said:**
> Which I did. I love how the assumption usually seems to be that a user griping about bugs has done nothing about it to help.

that is the predominant behavior of users. i simply based it on a higher chance of you being one.

---

### Post by michaelzap on 2009-06-29
> **zekopeko said:**
> that is the predominant behavior of users. i simply based it on a higher chance of you being one.

I remember some timeless wisdom from a movie called The Bad News Bears regarding what happens when you assume...

---

### Post by zekopeko on 2009-06-29
> **michaelzap said:**
> I remember some timeless wisdom from a movie called The Bad News Bears regarding what happens when you assume...

considering that communication over internet is mostly sanitized of non verbal signs, assumptions should be acceptable to some degree.

---

### Post by qamelian on 2009-06-29
> **zekopeko said:**
> considering that communication over internet is mostly sanitized of non verbal signs, assumptions should be acceptable to some degree.
I have to diasagree. If anything, it makes assumptions even more dangerous.

---

### Post by descendent87 on 2009-06-29
Does anyone know if the geolocation feature in empathy will work with [Google Latitude](http://www.google.com/intl/en_us/latitude/intro.html) on google talk accounts?

---

### Post by zekopeko on 2009-06-29
> **qamelian said:**
> I have to diasagree. If anything, it makes assumptions even more dangerous.

as said: to some degree acceptable considering how many people bitch and then don't report a bug thinking that developers look for bug on forums.

i have nothing but your word on contributing to bugs (not asking for links since i'll trust your word on it). so leave me some minor, non-personal, experience-based, a priori assumptions :)

---

### Post by zekopeko on 2009-06-29
> **descendent87 said:**
> Does anyone know if the geolocation feature in empathy will work with [Google Latitude](http://www.google.com/intl/en_us/latitude/intro.html) on google talk accounts?

if somebody develops the plugin for geoclue (the library used for this) using google latitude this could be possible.

---

### Post by zerothis on 2009-06-29
It will not connect to Yahoo chat for me.

---

### Post by Joe_Bishop on 2009-06-30
> It will not connect to Yahoo chat for me.
Are you sure?

---

### Post by tgpraveen on 2009-06-30
you need the latest libpurple from the ppa for yahoo to work in both pidgin and empathy

or in both u can change the yahoo server to 

cn.scs.msg.yahoo.com

---

### Post by jonatanschroeder on 2009-07-07
I currently use Pidgin, and it's working fine. If Empathy really adds all the features already implemented in Pidgin, I'm eager to move to Empathy. I'm mostly interested in stuff like file transfer on MSN and custom emoticons, besides obviously bug fixing.

One question I have though, is: I have been using additional plugins to connect Pidgin to other protocols, like Facebook and Skype. I've seen solutions to work with Facebook, but is it possible to implement it with Skype? This would be an even better solution, as with Skype4pidgin I only have the chat and the call notification on Pidgin, but the call itself would be dealt on Skype. If Empathy has A/V, maybe a similar solution could be found to deal with the call... Currently Pidgin connects to a Skype running instance, and I'm ok if Empathy works like that, but an optimal scenario would be connecting to a library or directly to the Skype protocol (though I know it's closed source).

---

### Post by AFarris01 on 2009-07-10
I'll stick with pidgin.

If empathy had voice/video support maybe... I agree with others that the interface feels unfinished. It also refused to import 2 of my accounts... an AOL account, and an IRC account, though it recognized that they were there just fine.

adding the icons next to buddies so you know what protocol they're on would help too... I've got 4 accounts, and several people with the same names that I normally distinguish by the protocol. annoyingly difficult in empathy.

my 2 cents...

---

### Post by iandotcom on 2009-07-23
I got my hands on Karmic Alpha 3 just a bit ago.. first thing I did was take a look at Empathy because I just found out about the switch from Pidgin just recently.

Gotta admit, I read someone comment on the UI of Empathy looking incomplete, and I got to agree. Or maybe its because I'm over-biased from prolonged exposure to Pidgin.

See how it goes closer to release, maybe it'll be a lot different in implementation. If not, then I hope Ubuntu will still have good support for Pidgin. The notification applet and the user/status switcher were features I've grown to love from Jaunty.

---

### Post by ELD on 2009-07-23
The main thing that bugs me is the password/email being wrong way around on the default msn back-end. Which has now on the freedesktop bugzilla been told it is an actualy Empathy bug, and a rather annoying one!!

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/402194](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/402194)
Then to here:
[https://bugs.freedesktop.org/show_bug.cgi?id=22883](https://bugs.freedesktop.org/show_bug.cgi?id=22883)

Waiting for whoever to forward it on to where it should be.

---

### Post by Staz on 2009-07-23
> **ELD said:**
> The main thing that bugs me is the password/email being wrong way around on the default msn back-end. Which has now on the freedesktop bugzilla been told it is an actualy Empathy bug, and a rather annoying one!!

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/402194](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/402194)
Then to here:
[https://bugs.freedesktop.org/show_bug.cgi?id=22883](https://bugs.freedesktop.org/show_bug.cgi?id=22883)

Waiting for whoever to forward it on to where it should be.
The bug has been reported to the empathy BTS and there is already a patch for it :
[http://bugzilla.gnome.org/show_bug.cgi?id=587117](http://bugzilla.gnome.org/show_bug.cgi?id=587117)

I have updated the Launchpad bug.

---

### Post by ELD on 2009-07-23
> **Staz said:**
> The bug has been reported to the empathy BTS and there is already a patch for it :
[http://bugzilla.gnome.org/show_bug.cgi?id=587117](http://bugzilla.gnome.org/show_bug.cgi?id=587117)

I have updated the Launchpad bug.

Thanks a lot, any idea when ubuntu will get the fix in? I can't load the bug page up for some reason that is why i am asking :).

---

### Post by Staz on 2009-07-23
> **ELD said:**
> Thanks a lot, any idea when ubuntu will get the fix in? I can't load the bug page up for some reason that is why i am asking :).
Don't know when the patch will be reviewed and commited (I'm not an Empathy dev)
But next Empathy release is planned for the 27 Aug, following [gnome schedule]("http://live.gnome.org/Schedule") (plus a few days for the ppa to be updated) It will probably be in Karmic anyway.

---

### Post by ELD on 2009-07-23
That should be ample time to review and commit the patch then, hopefully it will be in Karmic then! If not we can always update from a newer PPA package right?

---

### Post by BCurtisWX on 2009-07-23
> **ELD said:**
> That should be ample time to review and commit the patch then, hopefully it will be in Karmic then! If not we can always update from a newer PPA package right?

yup.  sorry I have been busy these past few days and wasn't able to push the bug to the gnome bugzilla quick enough.

---

### Post by ELD on 2009-07-23
> **BCurtisWX said:**
> yup.  sorry I have been busy these past few days and wasn't able to push the bug to the gnome bugzilla quick enough.

No problem mate, but it will deffinately be commited for future versions though right? So if it does not make it into karmic then it will be in a PPA ready for +1? Just making sure :).

---

### Post by BCurtisWX on 2009-07-23
> **ELD said:**
> No problem mate, but it will deffinately be commited for future versions though right? So if it does not make it into karmic then it will be in a PPA ready for +1? Just making sure :).

Theres a few people that make daily PPA's of the Empathy program.  So if its (for some really strange reason) not in Karmic, it will def be Karmic+1.

---

### Post by ELD on 2009-07-23
Good news as it was bugging me a lot, looking forward to using Empathy :).

Is it the default now, as i tried a livecd for Karmic before and pidgin was still default.

---

### Post by 23meg on 2009-07-23
> **ELD said:**
> 
Is it the default now, as i tried a livecd for Karmic before and pidgin was still default.

It's the default now.

---

### Post by Merk42 on 2009-07-23
There is/will be support for importing Pidgin logs, am I correct?

Also, how is support from going from Empathy to Pidgin?
I ask because I dual boot Linux and Windows and like to keep the same log across both.

---

### Post by gnomeuser on 2009-07-23
> **23meg said:**
> It's the default now.

Let the good times roll

---

### Post by Arup on 2009-07-23
Installed empathy on Jaunty x64 from their ppa, dont' have voice or video otherwise works fine, also complains of a libgtk 23 issue when I try and install extra stuff like sendto universe etc.

---

### Post by mpt on 2009-07-24
> **iandotcom said:**
> Gotta admit, I read someone comment on the UI of Empathy looking incomplete, and I got to agree. Or maybe its because I'm over-biased from prolonged exposure to Pidgin.

I had a couple of meetings with the Empathy developers at the Gran Canaria Desktop Summit, and another meeting with them last week.

I have designed for them an initial setup assistant for Empathy, redesigned the accounts interface, and redesigned a couple of other awkward bits (View menu, subscription request dialog).

They’re now hard at work implementing the new accounts interface, and they hope to get this done in time for Gnome 2.28 (and therefore Ubuntu 9.10).

As soon as I get in front of a scanner I’ll scan the designs and upload them to live.gnome.org so y’all can see them.

---

### Post by tgpraveen on 2009-07-24
@mpt

eagerly waiting for 'em!!!!!!

---

### Post by deadspider187 on 2009-07-24
I'm not going to lie, I definitely did not read through 27 pages of this, but can someone tell me why they are replacing Pidgin, which is a fully functional and polished instant messaging application, with one they are writing from scratch to mimic what Pidgin already does?  

It will take months if not a couple of years to get Empathy up to where Pidgin is today.  I guess I just don't see the point. :confused:

---

### Post by BCurtisWX on 2009-07-24
> **deadspider187 said:**
> I'm not going to lie, I definitely did not read through 27 pages of this, but can someone tell me why they are replacing Pidgin, which is a fully functional and polished instant messaging application, with one they are writing from scratch to mimic what Pidgin already does?  

It will take months if not a couple of years to get Empathy up to where Pidgin is today.  I guess I just don't see the point. :confused:

Desktop Integration is _much_ better.  Hold many more possibilities for the future.

---

### Post by ELD on 2009-07-24
Not to mention it will properly support video calls i have read. Pidgin has been at a stand still for that. Although i've checked their tracker recently and it has now been split up to be protocol specific, looks like some work might be undergoing at last for it in pidgin!

---

### Post by BCurtisWX on 2009-07-24
> **ELD said:**
> Not to mention it will properly support video calls i have read. Pidgin has been at a stand still for that. Although i've checked their tracker recently and it has now been split up to be protocol specific, looks like some work might be undergoing at last for it in pidgin!

Its still pretty much dead though.

---

### Post by ELD on 2009-07-24
> **BCurtisWX said:**
> Its still pretty much dead though.

Yeah i know, sucks that it has been like it for so long when most other clients i have tried have at least viewing a persons webcam possible.

---

### Post by deadspider187 on 2009-07-24
> **BCurtisWX said:**
> Desktop Integration is _much_ better.  Hold many more possibilities for the future.

Is there no way Gnome could just work with the Pidgin developers to achieve the same thing?  Or make a plugin?  I don't even see any section of Empathy that integrates with anything else in Gnome?  Is there a way to sync contacts between other Empathy contacts and e-mail contacts?

My thought is that I would rather have a bunch of third-party apps that serve each of their function well even if they don't work well together, then to have a bunch of native apps that work well together, but don't serve each of their functions as well.

Don't get me wrong, I'm usually first to jump ship to new shiny applications, but I wonder if this is a step backwards.  

For example:

No plugins
No encryption
Lack of appearance options
Unpolished interface (although it does look nice for this early in)
No Windows/Mac version

Are any/all of these things planned to be implemented at some point?

---

### Post by BCurtisWX on 2009-07-24
> **deadspider187 said:**
> Is there no way Gnome could just work with the Pidgin developers to achieve the same thing?  Or make a plugin?  I don't even see any section of Empathy that integrates with anything else in Gnome?  Is there a way to sync contacts between other Empathy contacts and e-mail contacts?

My thought is that I would rather have a bunch of third-party apps that serve each of their function well even if they don't work well together, then to have a bunch of native apps that work well together, but don't serve each of their functions as well.

Don't get me wrong, I'm usually first to jump ship to new shiny applications, but I wonder if this is a step backwards.  

For example:

No plugins
No encryption
Lack of appearance options
Unpolished interface (although it does look nice for this early in)
No Windows/Mac version

Are any/all of these things planned to be implemented at some point?
From my understanding, the pidgin devs aren't extremely friendly people to get along with and make it really hard to work with.

In case you didn't know, you will still be able to install pidgin, it just won't be default.

---

### Post by ELD on 2009-07-24
> **BCurtisWX said:**
> From my understanding, the pidgin devs aren't extremely friendly people to get along with and make it really hard to work with.

In case you didn't know, you will still be able to install pidgin, it just won't be default.

You are right, no offense to them but they are highly annoying, they outright refuse to do certain things and it really bugs me, i will look forward to using something that is better integrated and has nicer devs ;)

---

### Post by deadspider187 on 2009-07-24
> **BCurtisWX said:**
> From my understanding, the pidgin devs aren't extremely friendly people to get along with and make it really hard to work with.

In case you didn't know, you will still be able to install pidgin, it just won't be default.

I do remember reading that about the Pidgin devs at some point, that's a shame.  I will probably have to have them installed parallel until Empathy builds a lot of the features I mentioned.  

Has this switch been a long time in the making?  It's the first time I've heard of it, and I'm usually quite the avid watcher of new/updated packages.

---

### Post by ELD on 2009-07-24
It was talked about for quite a while, there has been many, many topics on it.

---

### Post by Miata-MS on 2009-07-24
Was talking about Empathy with some friends recently and installed it thinking maybe I'd get used to it now. Started it up, poked around for a second, realized there was no encryption and ran "sudo apt-get purge empathy". No encryption, no point.

For the average user maybe encryption doesn't matter, but it's bad enough essentially every other form of communication is quite open to being snooped on....I'll take whatever security I can get.

Video is great. Voice is great. I really don't care if those are encrypted (though it sure would be nice), but not implementing an "OTR" compatible encryption method with Empathy is really inexcusable be it a plugin or an integral part of the program.

----------

Otherwise Empathy looks good. I like the interface better than Pidgin's overall, I prefer the simpler chat windows and such. For all of you who get your panties in a wad when someone disagrees with you... let me repeat...overall, Empathy is good stuff. But to be made the default IM client without supporting plugins and encryption? Someone made a really poor decision there. We're not making Google Chrome the default browser just because of it's advances over Firefox...it's quite usable, and very fast...but it just ISN'T READY.


/Everyone/ who uses instant messengers uses text chat...Video and Voice are the exceptions. And with all due respect to the Empathy devs, right now Pidgin is the better choice for that due to the encryption support. Make that happen and here's one more that'll gladly switch.

---

### Post by Arup on 2009-07-24
How do you get video and voice, in my case all are grayed out.

---

### Post by Merk42 on 2009-07-25
> **Miata-MS said:**
> 
/Everyone/ who uses instant messengers uses text chat...Video and Voice are the exceptions. 

And so is encryption as, like you said, not everyone uses it.

---

### Post by meborc on 2009-07-25
> **Merk42 said:**
> And so is encryption as, like you said, not everyone uses it.

not everyone uses "assistive technologies" from system - preferences... but some people need to... so in your mind we should discard it???

just because OTR is not used by 100% (or even 20%) of IM users does not mean that you just remove the possibility by default

i just hope that empathy gets ahead before 9.10 is released... :(

---

### Post by Swarms on 2009-07-25
> **Miata-MS said:**
> Was talking about Empathy with some friends recently and installed it thinking maybe I'd get used to it now. Started it up, poked around for a second, realized there was no encryption and ran "sudo apt-get purge empathy". No encryption, no point.

For the average user maybe encryption doesn't matter, but it's bad enough essentially every other form of communication is quite open to being snooped on....I'll take whatever security I can get.

Video is great. Voice is great. I really don't care if those are encrypted (though it sure would be nice), but not implementing an "OTR" compatible encryption method with Empathy is really inexcusable be it a plugin or an integral part of the program.

----------

Otherwise Empathy looks good. I like the interface better than Pidgin's overall, I prefer the simpler chat windows and such. For all of you who get your panties in a wad when someone disagrees with you... let me repeat...overall, Empathy is good stuff. But to be made the default IM client without supporting plugins and encryption? Someone made a really poor decision there. We're not making Google Chrome the default browser just because of it's advances over Firefox...it's quite usable, and very fast...but it just ISN'T READY.


/Everyone/ who uses instant messengers uses text chat...Video and Voice are the exceptions. And with all due respect to the Empathy devs, right now Pidgin is the better choice for that due to the encryption support. Make that happen and here's one more that'll gladly switch.

Unless you are a government agent or share your ebanking passwords across your IM you should be fine.

---

### Post by hgergo on 2009-07-25
I have ubuntu 9.10 instaled since alpha2 and it wil replace it automaticaly from update manager?

---

### Post by rudenko_ruslan on 2009-07-25
> **hgergo said:**
> I have ubuntu 9.10 instaled since alpha2 and it wil replace it automaticaly from update manager?
You will have Empathy & Pidgin installed.

---

### Post by Merk42 on 2009-07-25
> **meborc said:**
> not everyone uses "assistive technologies" from system - preferences... but some people need to... so in your mind we should discard it???

just because OTR is not used by 100% (or even 20%) of IM users does not mean that you just remove the possibility by default

i just hope that empathy gets ahead before 9.10 is released... :(

I didn't say I agreed with any of it.  I just guessing that's what the developers when the decided to make the switch.

I'd like to think "not yet included" more than "remove".

---

### Post by Miata-MS on 2009-07-25
> **Merk42 said:**
> And so is encryption as, like you said, not everyone uses it.

Merk42, agreed. As has been said earlier though, there's nothing preventing Pidgin from being installed and used in Karmic so that's the way I'll go. 

I guess I just see it as a matter of "feature regression" for lack of a better way to put it. It's always acceptable to add new features (or even replace them with better methods), but like meborc said, you don't take away features that even a small percentage of your user base employs.

@Swarms : I do use IM for work as I work from home quite a bit and end up asking co-workers for root passwords to servers and such. Having an IM session that goes "Me : Hey, what's the login for xyz.com? Coworker : 12345" in plain text is just asking for problems. Sure I could use the phone, email, or other methods, but my point is that currently, there is an encryption option for the default IM client that is arguably more secure than any of those methods ( aside from PGP encrypted emails ) that gives us enough security for what we need, and that's being taken away for "better DE integration" and Voice/Video. While those other things are great and I'm definitely happy to see linux making headway in that area, it should not come at a cost to other features.

On the Empathy homepage it describes the "Layered Encryption" as a poor approach due to it's incompatibility with native protocol clients. This doesn't really work though as they do not give an alternate solution. They say "XTLS + Jingle" is coming in the future, but that's only on a single protocol, and it's not here yet. OTR works right now, and on multiple protocols...no forced use of any particular protocol : XMPP, AIM, Yahoo, maybe MSN? (haven't tried on that protocol). What's more there's a library for it specifically for the ease of inclusion into other IM clients. Let alone the OTR aspect....just including the ability for OTHERS to add this functionality (and any other useful addition) via a plug-in should have been a basic requirement for the programs release as a default client.

---

### Post by Miata-MS on 2009-07-25
> **Merk42 said:**
> I'd like to think "not yet included" more than "remove".

Merk42, Sadly it is the latter in the minds of the devs...

From [http://live.gnome.org/Empathy/FAQ](http://live.gnome.org/Empathy/FAQ) quote :


"Will Empathy have OTR support?

We think that the correct approach to secure end-to-end communications is to support it natively in the protocol. There is ongoing work on standardising secure end-to-end messaging in Jingle (using XTLS and Jingle) and we plan to support this in the future.

We don't think that layering encrypted messaging on top of protocols that don't support it is very useful, since such extensions won't, by definition, work in native protocol clients, and any clients that do go out of their way to support encrypted messaging might as well do so using a native protocol. "

>  ...any clients that do go out of their way to support encrypted messaging might as well do so using a native protocol.

Agreed for the most part. Except no protocol currently encrypts natively. And the only one that has such functionality upcoming is XMPP via XTLS and Jingle. Not so useful in my opinion. More of my encrypted conversations happen over AIM than XMPP. Maybe someone uses Yahoo more? OTR allows this. Even if Emapathy supports XTLS (someday), it's still just one protocol.

I'm really fine with the base client package not supporting encryption. Pidgin doesn't. Adium doesn't. Both require plug-ins. Empathy doesn't even give you that option though... In fact, Plug-in capability is not even mentioned in their Roadmap.

---

### Post by rajeev1204 on 2009-07-25
nvm

---

### Post by deadspider187 on 2009-07-25
> **Arup said:**
> How do you get video and voice, in my case all are grayed out.


Same here.

---

### Post by bigiron45 on 2009-07-25
> **deadspider187 said:**
> Same here.

Mine as well, I wonder if this depends on the web cam used?

---

### Post by ELD on 2009-07-25
> **rajeev1204 said:**
> 
The devs are under no obligation to listen to anyone are they?

Anyways,too much hear say and bad mouthing the devs here.

Check the pidgin website,the version they mention for download is a deb for ubuntu .No other distro is even listed on the main page.Shows respect for every one's favourite distribution.

[http://www.pidgin.im/](http://www.pidgin.im/)

cheers

rajeev.


No but an open source project that a lot of dsitros use they should at least value user feedback.

I am not  just adding hearsay, i am one on the unlucky ones who tried working with them.

Also it doesnt show respect, they may use it so they would support it more.

---

### Post by slavik on 2009-07-25
> **Miata-MS said:**
> 
@Swarms : I do use IM for work as I work from home quite a bit and end up asking co-workers for root passwords to servers and such. Having an IM session that goes "Me : Hey, what's the login for xyz.com? Coworker : 12345" in plain text is just asking for problems. Sure I could use the phone, email, or other methods, but my point is that currently, there is an encryption option for the default IM client that is arguably more secure than any of those methods ( aside from PGP encrypted emails ) that gives us enough security for what we need, and that's being taken away for "better DE integration" and Voice/Video. While those other things are great and I'm definitely happy to see linux making headway in that area, it should not come at a cost to other features.


VPN + your own XMPP server = problem solved.

---

### Post by buzzmandt on 2009-07-25
> **slavik said:**
> VPN + your own XMPP server = problem solved.
I really don't use im that much and don't so much have a horse in this race but isn't using an im client that has encryption much easier then installing and setting up multiple vpn's + xmpp server?  

Occasionally I use im and have to say I really don't like empathy. but it's so easy to ```
sudo apt-get install pigdin
```.  

But I do see the argument on having empathy as default.  If it's being set as default because it's going to be better in the future, why not wait until it's better in the future to make it default?

---

### Post by zekopeko on 2009-07-25
> **buzzmandt said:**
> But I do see the argument on having empathy as default.  If it's being set as default because it's going to be better in the future, why not wait until it's better in the future to make it default?

Well it's a catch 22. It's going to improve faster if it's in the largest distro since you will have a greater pool of bug testers and the developer have an incentive to make it better. Not to mention that Empathy is getting Ubuntu developers helping out with bugfixes. But you have to first include it to start getting the benefits.

Empathy is also going to replace Ekiga, and that freed space is surely needed for the new applications Ubuntu is including. Empathy is now very close to getting the critical mass needed to propel it and the telepathy framework as the de facto cross-distro standard of communication.
You are also getting integrated SIP/Audio/Video, deeper desktop integration (Banshee can share libraries over telepathy tubes, screen-sharing is coming, all sorts of cool things, neatly integrated with the Gnome desktop) and Ubuntu is closer to upstream Gnome which is only going to make thing easier in the long term.

---

### Post by meborc on 2009-07-26
> **zekopeko said:**
> ...
Empathy is also going to replace Ekiga, and that freed space is surely needed for the new applications Ubuntu is including. Empathy is now very close to getting the critical mass needed to propel it and the telepathy framework as the de facto cross-distro standard of communication.
You are also getting integrated SIP/Audio/Video, deeper desktop integration (Banshee can share libraries over telepathy tubes, screen-sharing is coming, all sorts of cool things, neatly integrated with the Gnome desktop) and Ubuntu is closer to upstream Gnome which is only going to make thing easier in the long term.

this is what was needed to be said in the first place :) 

replacing 1 im with another does not make sense since the new im is not on bar with the features... but screen-sharing, that is another thing... 

if someone had said this sooner i would have not been so opposed to the empathy inclusion... that said i still prefer pidgin ;)

---

### Post by chriswyatt on 2009-07-26
I think the question is, which is more popular; VOIP or encryption?  If only a small percentage of users use encryption whereas there's more demand for VOIP then I say include Empathy.  The smaller userbase who need encryption can quite easily install Pidgin if they want to.

Of course this is over-simplified and doesn't take a lot of other things into account, but you see my point.

---

### Post by meborc on 2009-07-26
> **chriswyatt said:**
> I think the question is, which is more popular; VOIP or encryption?  If only a small percentage of users use encryption whereas there's more demand for VOIP then I say include Empathy.  The smaller userbase who need encryption can quite easily install Pidgin if they want to.

Of course this is over-simplified and doesn't take a lot of other things into account, but you see my point.

ok, is voice/video working out-of-the-box in empathy?

i have not tried the latest karmic builds

---

### Post by slavik on 2009-07-26
depending on your organisation, you might already have VPN and then you probably have some IM network anyway (just make sure it's xmpp).

---

### Post by puccaso on 2009-07-28
IS IT ME
or is there no way to BLOCK people on empathy?! what kinda nonsense is this!!!

---

### Post by Staz on 2009-07-29
> **puccaso said:**
> IS IT ME
or is there no way to BLOCK people on empathy?! what kinda nonsense is this!!!
Not you, it's not yet implemented.

---

### Post by Staz on 2009-07-29
One of the Telepathy developer, wjt has written a very interesting post about Empathy, it's relation with Telepathy and the status of Audio and Video chat on the Ferdora forums.

I'm quoting it here for thoses of you who may be interested in knowing more about theses projects.

> Hi,

It seems like there's some (understandable) confusion about the components involved in Telepathy. I'm a Telepathy (and occasional libpurple and Pidgin) developer, so thought I'd try to clear this up a bit.

Empathy itself doesn't make connections to IM servers (Google Talk, MSN, etc.); this is the job of Telepathy's connection managers, which are a collection of daemons implementing support for various protocols. So, the features that Empathy supports on a protocol depend entirely on how advanced the connection manager is:

    * For XMPP (as used by Jabber and Google Talk), the CM is called telepathy-gabble. Gabble's the most advanced CM we have; among its many other features, it's supported audio and video calls for years.
    * For SIP, the telepathy-sofiasip CM is used; it supports audio and video calls.
    * For MSN, the best CM is telepathy-butterfly, which will support audio and video calls from the next release.
    * For IRC and Link-Local XMPP (branded as Bonjour by Apple), the CMs are telepathy-idle and telepathy-salut; neither supports audio and video calls. (There are also a few other one-protocol CMs being worked on, but they're not stable yet.)


So far, nothing I've mentioned uses libpurple. However: for AIM, Yahoo!, ICQ, etc., the CM is telepathy-haze, which is built on libpurple. This lets us reuse the protocol code in libpurple, but so far only supports simple things like text IM. (You can also use haze for MSN, but with the next release of butterfly you'll be even better off using that, since you get calls!)


[QUOTE]you are aware that Pidgin 2.6.0 will have Voice/Video Support?
That's true, but only on XMPP for now.

Quote:
Empathy doesnt have its own Plugins like Pidgin has so Empathy needs to rely on pidgins plugins to be there/working
As I mentioned, Empathy doesn't make the connections to IM servers itself. It uses Haze for some protocols. It doesn't use any Pidgin or libpurple plugins itself.


> correct me if im wrong, people that neeed to use SSL connections in Empathy cant cause its not supported?

All of the Telepathy connection managers support SSL where appropriate. Consider yourself corrected. ;-)

Quote:
> however i do believe Empathy will use Pidgins Voice & Video within libpurple

Hmm.

Empathy uses a library named Farsight (built on GStreamer) to actually send audio and video over the internet, and display it on the screen (oversimplification, but it'll do). Pidgin 2.6.0 will also use Farsight to do this.

(It's feasible that, at some point in the future, libpurple will support audio/video calls on a protocol like AIM, for which we don't have a separate Telepathy connection manager which supports a/v. At that point, it would make sense for us to expose libpurple's a/v code to Telepathy via haze. But this is very hypothetical; there are no plans to do this at the moment, because there's no point.)


> [http://developer.pidgin.im/ticket/9754](http://developer.pidgin.im/ticket/9754) set for 2.6.0 uses SIP
That ticket's not "set for 2.6.0". No-one has worked on SIP calling support in libpurple.


> [http://developer.pidgin.im/query?gro...ilestone=2.6.0](http://developer.pidgin.im/query?gro...ilestone=2.6.0) most of those bug fix's had to be fixed for Empathy to even use its newer features like Voice an Video
No. Nothing on that list has anything *whatsoever* to do with Empathy's audio and video calling support.


> custom Emoticons, that isnt such a Great feature, Empathy devs need to work on real features not kindergarten features

I don't really understand this. Are you saying that custom emoticons are a “kindergarten feature”? If so, great! Empathy doesn't support those. ;-) What “real features” are you referring to here?

Empathy supports file transfers and group chats; I think that between this, calls and (of course) IMs, that covers most of what people actually use. On top of that, using Telepathy enables really interesting possibilities for desktop integration, such as sharing your desktop with your IM contacts (which is supported in Empathy master, if you have recent enough Vino and Vinagre: just right-click a contact, and pick "share my desktop"!). My colleague Guillaume Desmottes gave an excellent talk recently about these possibilities; if you're interested, take a look at his slides: [http://people.collabora.co.uk/~cassidy/talks/2009-07-07-lets-make-gnome-a-collaborative-desktop.pdf](http://people.collabora.co.uk/~cassidy/talks/2009-07-07-lets-make-gnome-a-collaborative-desktop.pdf)

I hope this helps clear up the confusion! [/QUOTE]
[URL="http://forums.fedoraforum.org/showpost.php?p=1247505&postcount=12"]
Original post[/URL] and [topic]("http://forums.fedoraforum.org/showthread.php?t=226976")

---

### Post by xens on 2009-07-29
very interesting :)

---

### Post by cowanh00 on 2009-07-29
> **Staz said:**
> One of the Telepathy developer, wjt has written a very interesting post about Empathy, it's relation with Telepathy and the status of Audio and Video chat on the Ferdora forums.

I'm quoting it here for thoses of you who may be interested in knowing more about theses projects.


[URL="http://forums.fedoraforum.org/showpost.php?p=1247505&postcount=12"]
Original post[/URL] and [topic]("http://forums.fedoraforum.org/showthread.php?t=226976")

Thanks for posting this here. Very interesting read! Anyone know when the next version of telepathy-butterfly is out as I'm looking forward to MSN voice and video calls. Will it be out before Karmic is final? 

Who'd have thought it, 2009 is the year of voice and video on Linux! :guitar:

---

### Post by Staz on 2009-07-30
> **cowanh00 said:**
> Thanks for posting this here. Very interesting read! Anyone know when the next version of telepathy-butterfly is out as I'm looking forward to MSN voice and video calls. Will it be out before Karmic is final? 

For the records, telepathy-butterfly 0.5.0 was released two days ago. It doesn't yet contain with voice and video call but it lead the path to it since it now use papyon instead of pymsn (which was unmaintained) as the backend library. A part from that it (and papyon) fix a lot of small bugs and crashes. Note that it only work since today because distutils stupidly forgot a file in the telepathy-python release on which butterfly depends so they had to do another one to today. 

Concerning Audio and Video call, I was told that the branches for it had fully working, they are awaiting review, should be merged soon and be part of the next releases. There is no schedule for butterfly releases but it should definitely in Karmic.

I also have an experimental branch where I started to implement offline messages support which I hope will be completed for Karmic. For now it support sending message to offline (and invisible) users but you can't receive offline message yet, so it's kinda useless. Unfortunately most of my time is spend writing my master thesis for uni so I can't work on it as much as I want to until September. :/

HTH

---

### Post by Aries K on 2009-08-02
Anyone know when file transfer will be supported? I see the option is there but it's greyed out. Though even without file transfers I still love what I'm seeing so far with it's rapid development.

---

### Post by mpt on 2009-08-03
> **mpt said:**
> I had a couple of meetings with the Empathy developers at the Gran Canaria Desktop Summit, and another meeting with them last week.

I have designed for them an initial setup assistant for Empathy, redesigned the accounts interface, and redesigned a couple of other awkward bits (View menu, subscription request dialog).

They’re now hard at work implementing the new accounts interface, and they hope to get this done in time for Gnome 2.28 (and therefore Ubuntu 9.10).

As soon as I get in front of a scanner I’ll scan the designs and upload them to live.gnome.org so y’all can see them.

Finally got time to upload [the mockups]("http://live.gnome.org/Empathy/AccountsAndSettings") yesterday.

I’m working on some tweaks and I’ll post them later this week.

---

### Post by Regenweald on 2009-08-03
> **mpt said:**
> Finally got time to upload [the mockups]("http://live.gnome.org/Empathy/AccountsAndSettings") yesterday.

I’m working on some tweaks and I’ll post them later this week.

I may just have to start back instant messaging and whatnot with this one-stop-shop you guys are creating. Very Impressive and thanks.

---

### Post by PGHammer on 2009-08-05
> **taavikko said:**
> There's already idea on brainstorm concerning this issue
[http://brainstorm.ubuntu.com/idea/11705/](http://brainstorm.ubuntu.com/idea/11705/)
since missed the JJ, time for round two.

Would you like to see this implemented in KK.

Empathy is the default IM for gnome, so makes sense to replace pidgin.

This is also a re-occuring debate, but what the heck, let's throw it in anyway :)

I use pidgin (instead of Kopete) for KDE because pidgin has better support for Yahoo (which has been a problem for empathy in the past as well, which is why I had originally chose pidgin for use in GNOME before swapping to KDE 4 as default desktop).  In the larger distributions (such as openSuSE and Fedora) while I still tend to prefer KDE as my desktop of choice, my applications themselves are a mix ("horses for courses", as someone else put it, and there are times when "Gnorm" has the best "horse" for my K Desktop Environment).  With Kubuntu, a mixed desktop is harder to configure (although not impossible).

---

### Post by shafin on 2009-08-05
I'm having quite an annoying problem with empathy.
Whenever I log in using invisible mode in empathy, my account is shown to others as busy. Only if then I re-set the status to invisible, I become truly invisible. How do I know? I have myself added as a contact just to check this. On another note, another bug in empathy is when I try to chat with "myself". whenever I write something, it keeps coming back infinitely. In pidgin, it also comes back, but only once.
I'm on alpha 3, anyone else having these problems?

---

### Post by Katalog on 2009-08-06
I'm way too invested in and used to Pidgin's behavior. Does everything I need it to do. And for the few people I actually give a rip about video chatting with, I use Ekiga. In short, I personally don't see any reason to switch to Empathy.

---

### Post by dext on 2009-08-06
Empathy IMO isnt ready to be made default. if people can use Skype for Video/Audio at the moment i dont see why Empathy should be made default till it becomes more on par with more usefull features.

---

### Post by keypox on 2009-08-07
i dont understand the big deal i ahve used it a bit now.  Its pretty good.  If i want pidgin i will install it

---

### Post by dext on 2009-08-07
pidgin does a better job than Empathy does an has more features than Empathy. i cant see people Ditching Skype to use Empathy for Audio/Video

---

### Post by Joe_Bishop on 2009-08-07
don't cry, I've never used pidgin, have always switched to another clients (gajim, using icq through xmpp-transport). Switched to empathy in 9.04, because it's just better.

---

### Post by victorche on 2009-08-07
I am reading a tons of posts about Empathy... One simple question:

As far as I can see it does NOT support blocking of users :O

It is a main and major feature and I really want to know will it be implemented in soon (I really hope before the release of Karmic)?

---

### Post by MacUntu on 2009-08-07
[IMG]http://img.xrmb2.net/images/975227.png[/IMG]

Is that really all information Empathy can show me for a contact? Not that I already know the alias and the status from the contact list... :-\"

There's a lot work to do before this should be considered default for 10.04.

---

### Post by dext on 2009-08-07
i'd be looking at making it default in 11.04 i think by then it should have much more features than it has now

---

### Post by victorche on 2009-08-07
> **dext said:**
> i'd be looking at making it default in 11.04 i think by then it should have much more features than it has now

Well it is maybe a really promising project... But as far as I can see... It is still very far from complete and finished IM client. Don't think this should be the default one.

---

### Post by zekopeko on 2009-08-07
Dudes and ladies! That's why you are testing it! Report bugs. Prod developers with pointy sticks. Threaten to kill a bunny!
Just commenting on this forum won't allow you to fix those pesky bugs that ruin your user experience.

EDIT: I'm just kidding on the "pointy sticks" part. Love thy developer. Bunnies on the other hand are free-for-all. Especially when in a stew...mmmmmmm....

---

### Post by MaX on 2009-08-07
> **MacUntu said:**
> [IMG]http://img.xrmb2.net/images/975227.png[/IMG]

Is that really all information Empathy can show me for a contact? Not that I already know the alias and the status from the contact list... :-\"

There's a lot work to do before this should be considered default for 10.04.

What more do you want to know?

I use empathy for google chat and some times msn.
All I want to know is:
[LIST]if someone is online or not,
if I can voip them or if I can video chat them
if I can transfer a file to them
what their status message is
what my statusmessage is (this needs work)
[/LIST]

---

### Post by MacUntu on 2009-08-07
How about nickname, first name, last name, gender, age, e-mail, date of birth, web page, interests, phone nr., IP, user client, online since, idle since, street, city, state, postal code, country, spoken languages, timezone, local time, about, notes, and work related info: company, department, position, street, city, state, postal code, country, and website.

---

### Post by rajeev1204 on 2009-08-07
> **zekopeko said:**
> Dudes and ladies! That's why you are testing it! Report bugs. Prod developers with pointy sticks. Threaten to kill a bunny!
Just commenting on this forum won't allow you to fix those pesky bugs that ruin your user experience.

EDIT: I'm just kidding on the "pointy sticks" part. Love thy developer. Bunnies on the other hand are free-for-all. Especially when in a stew...mmmmmmm....


You mean the develops are just making something without testing it themselves? That argument will not cut anything and is invalid.While the developers will of course use the bug reports which could be invisible to the normal eye,the majority of users on the forum are talking about very visible and obviously missing features which pidgin has.The developers are not blind to wait for user feedback for many features pidgin has and this doesnt.Of course, that goes the other way around too. ;)


This product is way too unfinished relatively ,and so what are you asking the users to do? Tell developers something they already know?


Us users, and that means all of us will report bugs as usual,but the point of this thread is something else,and just reporting some bug wont assure users that the next default client will have many of the features people are asking for.

So in a nutshell, do the developers even have time to finish empathy by 9.10? Highly unlikely iam afraid.Iam eagerly waiting for voice/video implementation.Is that working yet?


regards
raj.

---

### Post by zekopeko on 2009-08-07
@rajeev1204

you could voice your feature priorities...

---

### Post by mpt on 2009-08-07
> **mpt said:**
> Finally got time to upload [the mockups]("http://live.gnome.org/Empathy/AccountsAndSettings") yesterday.

I’m working on some tweaks and I’ll post them later this week.

On Wednesday I uploaded more detailed mockups of [the “Welcome to Empathy” window]("http://live.gnome.org/Empathy/WelcomeToEmpathy") and [the “Accounts and Settings” window]("http://live.gnome.org/Empathy/AccountsAndSettings").

Cosimo Cecchi at Collabora has been [working hard on implementing the “Welcome to Empathy” window]("http://people.collabora.co.uk/~cosimoc/assistant/").

---

### Post by Bou on 2009-08-07
Have you guys noticed that Empathy no longer supports IRC accounts? Am I crazy and it never did?

---

### Post by zekopeko on 2009-08-07
> **Bou said:**
> Have you guys noticed that Empathy no longer supports IRC accounts? Am I crazy and it never did?

telepathy-idle plugin IIRC. maybe it's not installed.

---

### Post by Bou on 2009-08-07
That solved it, thanks zekopeko.

---

### Post by wayne_cat on 2009-08-07
> **Bou said:**
> That solved it, thanks zekopeko.

+1 

thanks zekopeko

---

### Post by BCurtisWX on 2009-08-07
i always keep getting DC from IRC... anyone else?

---

### Post by dext on 2009-08-07
is your system up to date?

---

### Post by Mike_IronFist on 2009-08-08
**EDIT: I meant to say Empathy, not Epiphany. Epiphany is a web browser, not to be confused with Empathy, the subpar Instant Messneger**

I was reading Wikipedia's article on Ubuntu, and I know you can't ALWAYS trust data that's on Wikipedia, but I heard that Karmic Koala will be the first Ubuntu distro to include Empathy by default instead of Pidgin as an instant messenger.

THIS IS A HORRIBLE IDEA.

Replacing Pidgin with Empathy is like replacing a bicycle with a unicycle. It's like swapping out Windows XP for Windows 2000. It's the ultimate cheating, you-lose-scenario.

Now I know that you can just install Pidgin if you prefer it, but you have to understand why I am bothered by the prospect of this. Pidgin is a fantastic IM. It's got a ridiculous amount of features and it just works, really really well. 

People new to Ubuntu are getting cheated though, if Canonical really wants Ubuntu to start with Empathy instead of Pidgin. Empathy is lacking in so many areas - it's just a bland, featureless IM that feels like a chore to use compared to the achievement that is Pidgin.

Is Canonical really doing this, and if so, how do you feel about it? I for one am upset at the very prospect of an excellent piece of software like Pidgin getting thrust into relative obscurity so that a less impressive application can take its place.

I consider it a step back for the open source community if Ubuntu 9.10 is released with Pidgin hiding in the app repository instead of being pre-installed.

---

### Post by Lacrimstein on 2009-08-08
I don't think they would do this... Then again, they switched over to PulseAudio from a much more stable ALSA just for lulz

---

### Post by SunnyRabbiera on 2009-08-08
No its being rep[laced with Empathy not epiphany.
Epiphany is a web browser.
And I sort of agree, Empathy right now needs a lot of packages to make it work with all the major IM clients...
Ubuntu better make it have the  libpurple backend.

---

### Post by Methuselah on 2009-08-08
I don't understand.
Isn't epiphany a browser?
Let's not jump the gun....lol

EDIT: Thanks for clearing that up Sunny.

---

### Post by taavikko on 2009-08-08
> **Lacrimstein said:**
> I don't think they would do this... Then again, they switched over to PulseAudio from a much more stable ALSA just for lulz

You might wanna check what pulseaudio really is and in top of what it runs ;)

For original poster, yes empathy is immature, but why...
Could it be that it's been on active development far less than gaim/pidgin.
but is now been more actively worked on, compared to pidgin where the devs are hostile and lazy :D (hearsay)

---

### Post by Arup on 2009-08-08
The sad part is that Pidgin although a legitimately good client is not being developed to a good extent. IM's like aMSN, Kopete, Gyachi have had video and voice support for a long while but Pidgin is yet to implement it. Empathy is promising video and voice and thats where many are looking for in their IMs.

---

### Post by Mike_IronFist on 2009-08-08
> **taavikko said:**
> You might wanna check what pulseaudio really is and in top of what it runs ;)

For original poster, yes empathy is immature, but why...
Could it be that it's been on active development far less than gaim/pidgin.
but is now been more actively worked on, compared to pidgin where the devs are hostile and lazy :D (hearsay)

Pidgin is a program that I've yet to have a problem with, ever.

Empathy is, frankly, a piece of garbage compared to it. There's no meat to it. You can barely change your font.

I judge software based on its quality. Pidgin is at a point now where the only reason there is to release new builds is to squash the occasional bug. Empathy is not even good enough to be released.

If Ubuntu is going to go for the unpolished garbage instead of the quality stuff, it's going in the wrong direction.

---

### Post by Mike_IronFist on 2009-08-08
> **Arup said:**
> The sad part is that Pidgin although a legitimately good client is not being developed to a good extent. IM's like aMSN, Kopete, Gyachi have had video and voice support for a long while but Pidgin is yet to implement it. Empathy is promising video and voice and thats where many are looking for in their IMs.

I'd expect most people to look to Skype for that. But regardless, Canonical shouldn't choose Empathy at ALL in the current state it's in. (Which is, again, an unpolished, incomplete IM)

---

### Post by Bios Element on 2009-08-08
> **rajeev1204 said:**
> So in a nutshell, do the developers even have time to finish empathy by 9.10? Highly unlikely iam afraid.Iam eagerly waiting for voice/video implementation.Is that working yet?

And are the Pidgin devs ever going to even start working on it? ;) Nope. >.> That's probably the biggest cause of the switch. Pidgin is turning into a dead project.

---

### Post by kyleabaker on 2009-08-08
> **zekopeko said:**
> telepathy-idle plugin IIRC. maybe it's not installed.

Thanks, I was having the same problem. Wonder why this isn't "recommended" and installed by default?

---

### Post by Podex on 2009-08-08
You know, there is already a massive thread about this: [http://ubuntuforums.org/showthread.php?t=1154769](http://ubuntuforums.org/showthread.php?t=1154769) We didn't really need another one I think. Unless people say the poll adds something. Maybe you should have added an option "I don't care".

---

### Post by mdurham on 2009-08-08
> **Podex said:**
> Maybe you should have added an option "I don't care".
+1 for that comment.

---

### Post by juancarlospaco on 2009-08-08
Because the common people dont want to login on 69841484531216216514984 IM Protocols
or have 4987865432165489489464986512654165451521654 rarely used features, 
people want Webcam Support, with Audio.

:)

---

### Post by hanzomon4 on 2009-08-08
Well first you apparently don't know what pulse audio is or what it replaced. Second, relax the world is not over. Most people just chat with pidgin, empathy supports libpurple so nothing lost there.. I've used empathy so trust me all the protocols worked (last I checked). I know some people use things like otr which apparently is lacking in empathy. That's ok it will get there and on top of that telepathy is a great foundation for the future (that sounds a bit grandiose.. sorry). To make progress you got to try new things. Pidgin is not innovating, empathy atop telepathy is.. bottom line

---

### Post by gnomeuser on 2009-08-08
It's the default now, I love it. I am a big Telepathy fan and empathy really is a fine program I am happy to see it exposed. It still does lack a few features but we are making a bet for the future regression are unfortunate but will be ironed out.

---

### Post by Rackstar on 2009-08-08
I think the OP is exaggerating, pidgin is definitly a good IM, but really lacks the voice and video feature.

Also skinning in Empathy seems to be really nice: [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes) 

I believe they have good reasons, and maybe the devs can be trusted in knowing a little bit more than you. Calling them insane is just immature.

---

### Post by phenest on 2009-08-08
Alpha testing, and bug report springs to mind.

I'm not a big IM user, but I do require it never the less. I've just had a look at Empathy, and it looks good to me.

I think I'll vote... Empathy.

---

### Post by phenest on 2009-08-08
> **Rackstar said:**
> ... maybe the devs can be trusted in knowing a little bit more than you.

How can the devs know what I require or want. When it comes to changing default software, *we* must decide. *We* are the end users. There is a poll here. We'll that decide.

---

### Post by Rackstar on 2009-08-08
> **phenest said:**
> How can the devs know what I require or want. When it comes to changing default software, *we* must decide. *We* are the end users. There is a poll here. We'll that decide.

There are always other things you need to keep in mind, things that end-users fail to see. As I read somewhere else the activity in Pidgin is going downhill and the future of Empathy looks more bright.

Also, if you upgrade, it will not replace your pidgin with Empathy, it's only for fresh installs. It's not like they are forcing you to use it.

Ofcourse you are right that the end-user should have the last word. But nevertheless the reaction of the OP is rather childish.

---

### Post by phenest on 2009-08-08
> **Rackstar said:**
> There are always other things you need to keep in mind, things that end-users fail to see. As I read somewhere else the activity in Pidgin is going downhill and the future of Empathy looks more bright.

That should be more reason to support it. Didn't Gnome announce they weren't going to support Rhythmbox anymore? But now look at it.

---

### Post by gnomeuser on 2009-08-08
> **phenest said:**
> That should be more reason to support it. Didn't Gnome announce they weren't going to support Rhythmbox anymore? But now look at it.

GNOME doesn't have a default library media player, they just ship Totem. Thus they can't stop to support Rhythmbox.

You are clearly poorly informed. I would respectfully suggest that you invest a bit more time researching before posting.

---

### Post by phenest on 2009-08-08
> **gnomeuser said:**
> GNOME doesn't have a default library media player, they just ship Totem. Thus they can't stop to support Rhythmbox.

You are clearly poorly informed. I would respectfully suggest that you invest a bit more time researching before posting.

I was referring to the talk of replacing Rhythmbox with something else because development ceased.

I suggest you ask questions before jumping in with accusations like that.

---

### Post by gnomeuser on 2009-08-08
> **phenest said:**
> I was referring to the talk of replacing Rhythmbox with something else because development ceased.

I suggest you ask questions before jumping in with accusations like that.

You didn't read, GNOME has no default player outside of Totem.

The talks of replacing Rhythmbox are still ongoing within Ubuntu (Ubuntu != GNOME), Banshee will replace it for Koala+1 as things stand right now when the last blocker bugs will have been addressed. It should have been for Koala but especially concerns over the accessibility features have not yet been addressed due to problems with upstream ATK#.

My point stands, you do not have sufficient information to carry on this thread and would benefit from time researching before posting further.

---

### Post by gnomeuser on 2009-08-08
> **mpt said:**
> On Wednesday I uploaded more detailed mockups of [the “Welcome to Empathy” window]("http://live.gnome.org/Empathy/WelcomeToEmpathy") and [the “Accounts and Settings” window]("http://live.gnome.org/Empathy/AccountsAndSettings").

Cosimo Cecchi at Collabora has been [working hard on implementing the “Welcome to Empathy” window]("http://people.collabora.co.uk/~cosimoc/assistant/").

I somehow feel that the Welcome dialog shouldn't list choices it can probe for, e.g. Pidgin should be handled by detection 

"I noticed you previously used another instant messenger would you like me to migrate accounts from there" 

Debate happen surround such a default to migrate "import and delete original, unregister entries in keyrings and so on" or to plain import. Personally I favor migration, it seems like the option that will leave things the cleanest and safest but problematic if other clients don't support migration. Worst possible, migration happens to Empathy, user decides to switch back to Pidgin if Pidgin doesn't import from Empathy then we are screwed. This however is a more general problem if you are going to aim to replace a program make sure you either share important data formats or that you migrate cleanly, bugs should be filed.

---

### Post by Tibuda on 2009-08-08
Empathy got less features, but it got a more critical feature: video and voice. That's sane for me. Just replace it for Pidgin if you want. I'll do it, because I don't like vv.

---

### Post by loell on 2009-08-08
I just don't understand why some people are "Pidgin default" obsessed. :D

---

### Post by phenest on 2009-08-08
> **loell said:**
> I just don't understand why some people are "Pidgin default" obsessed. :D

Afraid of change? Or they don't understand, or know the reasons behind the decision? Probably the latter (I hope).

---

### Post by Tibuda on 2009-08-08
> **phenest said:**
> Afraid of change? Or they don't understand, or know the reasons behind the decision? Probably the latter (I hope).

Change? They don't have to change. They can keep using Pidgin.

---

### Post by MacUntu on 2009-08-08
Perfectly objective thread title! [-(

> **loell said:**
> I just don't understand why some people are "Pidgin default" obsessed. :D

Show me a feature-equivalent IM and Pidgin would be purged at once. Unless such an IM exists I don't understand why replacing Pidgin as default IM should be a good thing. And no, I don't care about video or audio support and Pidgin's lack of shouldn't justify the switch to an inferior solution.

---

### Post by Arup on 2009-08-08
> **Mike_IronFist said:**
> I'd expect most people to look to Skype for that. But regardless, Canonical shouldn't choose Empathy at ALL in the current state it's in. (Which is, again, an unpolished, incomplete IM)

Skype is but one protocol, how about those who don't use Skype or are on MSN or Yahoo, why leave them out. I do agree that Empathy needs to polish up before it becomes Ubuntu default.

---

### Post by phenest on 2009-08-08
> **danielrmt said:**
> Change? They don't have to change. They can keep using Pidgin.

Easy tiger! No one said they had to change. But if you read this entire thread, the reason for dropping Pidgin is a good one. I'm not telling what that is, because if you have indeed read this entire thread, you will already know that staying with Pidgin is not a very wise choice.

---

### Post by Tibuda on 2009-08-08
> **phenest said:**
> Easy tiger! No one said they had to change. But if you read this entire thread, the reason for dropping Pidgin is a good one. I'm not telling what that is, because if you have indeed read this entire thread, you will already know that staying with Pidgin is not a very wise choice.

You misunderstood me. I was not talking about Canonical, but the people complaining about the decision. If they want Pidgin they don't have to change. It's only the default.

---

### Post by xebian on 2009-08-08
Maybe Ubuntu should lead the way for pidgin Voice and Video.  At least we have some "Ubuntu made" instead of "RH made distributed by.."

Wait a minute.. I should say Voice and Video for Kopete..:)

---

### Post by MacUntu on 2009-08-08
> **danielrmt said:**
>  If they want Pidgin they don't have to change. It's only the default.

The same goes for Empathy. Everyone can install and test it till it's ready for being default. The whole point in using distributions is to get a good set of defaults - that's why defaults matter.

---

### Post by lswb on 2009-08-08
How about an poll choice of "I never use IM, *no* IM client should be installed by default."

---

### Post by loell on 2009-08-08
> **MacUntu said:**
> 
Show me a feature-equivalent IM and Pidgin would be purged at once. Unless such an IM exists I don't understand why replacing Pidgin as default IM should be a good thing. 

the switch isn't just about the vv feature.

> **MacUntu said:**
> 
And no,I  don't care about video or audio support and Pidgin's lack of shouldn't justify the switch to an inferior solution. 

the decision isn't just for a singular or several preferences of features, as has been pointed out over and over again.

---

### Post by MacUntu on 2009-08-08
> **loell said:**
> the switch isn't just about the vv feature.
the decision isn't just for a singular or several preferences of features, as has been pointed out over and over again.

The reasons for replacing Pidgin don't matter. The reasons why making Empathy default NOW matter and I've yet to see any good ones.

I wouldn't swap a rusty old car for a Ferrari with just two wheels if I need to drive.

---

### Post by rajeev1204 on 2009-08-08
> **zekopeko said:**
> @rajeev1204

you could voice your feature priorities...

My feature priorities was a hugely better user interface.

Well,i read its being addressed,so i rest now.


2 months to go for karmic,when do they implement this and when do they fix the bugs?

Plus, all the other things which other users have commented on this thread.

---

### Post by Scotty Bones on 2009-08-08
> **MacUntu said:**
> The reasons for replacing Pidgin don't matter. The reasons why making Empathy default NOW matter and I've yet to see any good ones.

I wouldn't swap a rusty old car for a Ferrari with just two wheels if I need to drive.

Agreed

Change for the sake of change, doesn't necessarily make for good change.
Empathy may one day be ready to replace Pidgin, but that day is not today. If they are able to make significant improvements, then maybe Karmic+1.

---

### Post by Mr. Picklesworth on 2009-08-08
I am surprised to see such an evenly matched poll; thought I was the only sane person here :P

Don't worry, you who voted No Will See what all the fuss over Empathy is about if you just give it a chance to shine, especially as things shape up further.

In decisions like this, being feature equivalent is not the only factor. Pidgin is not feature equivalent to Empathy, either.

It's about infrastructure. The number of buttons in the buddy list interface is irrelevant. The number of buttons in the dbus interface and the Telepathy API (which, by the way, is desktop-agnostic) is key. That's what this does well. With proper momentum, this will give us amazing things. In the free software world, that requires that a large enough distro, such as Ubuntu, SUSE or Fedora, make the decisive move to position the new technology as default so that surrounding applications begin to make use of it. If no distro makes the move, those applications will have no real incentive to implement the technology. It may see the odd implementation here and there, but nothing truly spectacular happens and then we risk losing that momentum.

Ubuntu taking that step is a great thing because this is a *hugely* popular distribution, so applications shipped here get loads of reason to do awesome stuff with the technology knowing that the work will reach a lot of users.

---

### Post by Neon Lights on 2009-08-08
As far as I know, it's not been said it will for SURE be default in the stable 9.10 release.
They put it in for testing purposes, to see how well it fared. 

As for me, I like it, but it's unusable because of [this bug]("https://bugs.freedesktop.org/show_bug.cgi?id=17157"). Stickin' to pidgin for now.

---

### Post by zekopeko on 2009-08-08
> **rajeev1204 said:**
> My feature priorities was a hugely better user interface.

Well,i read its being addressed,so i rest now.


2 months to go for karmic,when do they implement this and when do they fix the bugs?

Plus, all the other things which other users have commented on this thread.

It's unrealistic to expect that every feature request is going to make it in time. There are priorities. You can't please everyone. Take that into account. And those users that are usually asking where is OTR will still have Pidgin to install from the repos (and they are power users for the most part).
Not to mention that ff you upgrade from a previous install you are going to keep Pidgin. Empathy is going to be installed only for new users of fresh installs. 2 months is enough to fix major bugs.

---

### Post by zekopeko on 2009-08-08
> **Mr. Picklesworth said:**
> I am surprised to see such an evenly matched poll; thought I was the only sane person here :P

Don't worry, you who voted No Will See what all the fuss over Empathy is about if you just give it a chance to shine, especially as things shape up further.

In decisions like this, being feature equivalent is not the only factor. Pidgin is not feature equivalent to Empathy, either.

It's about infrastructure. The number of buttons in the buddy list interface is irrelevant. The number of buttons in the dbus interface and the Telepathy API (which, by the way, is desktop-agnostic) is key. That's what this does well. With proper momentum, this will give us amazing things. In the free software world, that requires that a large enough distro, such as Ubuntu, SUSE or Fedora, make the decisive move to position the new technology as default so that surrounding applications begin to make use of it. If no distro makes the move, those applications will have no real incentive to implement the technology. It may see the odd implementation here and there, but nothing truly spectacular happens and then we risk losing that momentum.

Ubuntu taking that step is a great thing because this is a *hugely* popular distribution, so applications shipped here get loads of reason to do awesome stuff with the technology knowing that the work will reach a lot of users.

+1. Very nicely said.

On a further note: Most users who clamor against Empathy do it for the "my precious" line of reasoning while ignoring (for the most part) the things it will bring to war effort. /end-LOTRlike-rant

 I completely understand that stance since nobody likes feature regression in any form, me included. But at least try to look in the future of Ubuntu and not a single release. Think like a developer while judging like a user.

---

### Post by rajeev1204 on 2009-08-08
> **zekopeko said:**
> It's unrealistic to expect that every feature request is going to make it in time. There are priorities. You can't please everyone. Take that into account. And those users that are usually asking where is OTR will still have Pidgin to install from the repos (and they are power users for the most part).
Not to mention that ff you upgrade from a previous install you are going to keep Pidgin. Empathy is going to be installed only for new users of fresh installs. 2 months is enough to fix major bugs.


Well,ya the OTR is probably not for everyone,even i dont use it really.Also,iam hoping we soon see the UI changes in the coming weeks.Iam using empathy now ,since thats default on karmic.So hope everything is fine in the end.Maybe its in some PPA,but i prefer the usual ubuntu upgrades to see new features :).Also,empathy i hope has almost all the plugins pidgin has or had.

Iam happy to see change in ubuntu always,and here's to voice and video.:guitar: ,and since a lot of positive things are happening on that front,its a good feeling.



regards
rajeev

---

### Post by rajeev1204 on 2009-08-08
> **Mr. Picklesworth said:**
> I am surprised to see such an evenly matched poll; thought I was the only sane person here :P

Don't worry, you who voted No Will See what all the fuss over Empathy is about if you just give it a chance to shine, especially as things shape up further.

In decisions like this, being feature equivalent is not the only factor. Pidgin is not feature equivalent to Empathy, either.

It's about infrastructure. The number of buttons in the buddy list interface is irrelevant. The number of buttons in the dbus interface and the Telepathy API (which, by the way, is desktop-agnostic) is key. That's what this does well. With proper momentum, this will give us amazing things. In the free software world, that requires that a large enough distro, such as Ubuntu, SUSE or Fedora, make the decisive move to position the new technology as default so that surrounding applications begin to make use of it. If no distro makes the move, those applications will have no real incentive to implement the technology. It may see the odd implementation here and there, but nothing truly spectacular happens and then we risk losing that momentum.

Ubuntu taking that step is a great thing because this is a *hugely* popular distribution, so applications shipped here get loads of reason to do awesome stuff with the technology knowing that the work will reach a lot of users.

This is a very positive reply.I agree.

I just hope it looks finished for the final release.

---

### Post by Asraniel on 2009-08-08
like that every desktop enviroment has it's problem. we kubuntu users get aurora as the konqueror replacement. konqueror might not be the best browser (but it's REALLY improving with every release), but aurora.. is really not ready yet.

---

### Post by andrewabc on 2009-08-08
> **loell said:**
> I just don't understand why some people are "Pidgin default" obsessed. :D

Because pidgin works better than empathy currently?

Did empathy get http msn connection yet? [Nope](https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/392195). Then it is useless so far for me. Although by October 31, I should not need http connection, but I'd feel bad for people who can't use the default program because it lacks a simple http connection that other IM have had for years.

I have empathy installed from PPA with latest version (on jaunty), and it has much less features than default pidgin. So replacing something with something worse just because it has potential does not benefit me.

http msn connection is only categorized as a wishlist. So doesn't seem very important to get done by 9.10 release. Nothing has been done to the bug for over a month.

---

### Post by Mike_IronFist on 2009-08-08
I care because I care about the state of Ubuntu. Pidgin makes Ubuntu look VERY GOOD. I show people Pidgin on Ubuntu live CD's and they get very excited about it.

Empathy...eh. Not nearly as much pizzazz yet. It's NOT READY.

That's the point. IT'S NOT READY.

You wouldn't try to impress someone with a team of baby basketball players when you have grown pros already available.

And I know some people don't care, but if you don't care, that's points in favor of Empathy.

---

### Post by Regenweald on 2009-08-08
> **Mike_IronFist said:**
> I care because I care about the state of Ubuntu. Pidgin makes Ubuntu look VERY GOOD. I show people Pidgin on Ubuntu live CD's and they get very excited about it.

Empathy...eh. Not nearly as much pizzazz yet. It's NOT READY.

That's the point. IT'S NOT READY.

You wouldn't try to impress someone with a team of baby basketball players when you have grown pros already available.

And I know some people don't care, but if you don't care, that's points in favor of Empathy.

You see, this is part of the problem. People like to scream the community should get to choose when it suits them, but the commune works both ways. Empathy is almost there, making it the default will expose it to a larger user/testing base which will provide valuable feedback for the developers in terms of problems and enhancements.

Pidgin is in the repos for those who prefer it. Empathy shows that Ubuntu is forward thinking and is not satisfied with settling for 'good enough'

Why can the 'community' not help with the enhancement of Empathy ?  some selfish users would probably much prefer that the developers slave away doing BOTH testing/coding so that a year from now they could say: 'ZOMG! the latest empathy is amazing!' 

Downloading a free operating system and demanding and complaining does not entitle you to anything. Logging into a forum does not entitle you to anything. Contribute. help out. lift a finger. Help make Empathy THE messaging client.

---

### Post by jfernyhough on 2009-08-08
> **Regenweald said:**
> Downloading a free operating system and demanding and complaining does not entitle you to anything. Logging into a forum does not entitle you to anything. Contribute. help out. lift a finger. Help make Empathy THE messaging client.Should I drop the other work I'm doing to help on Empathy? You know, the other bug testing and translation and support? Or should I keep going on what I can do and assume the rest of the system will work when I want it? Are you saying that because I don't work on Empathy code this means I shouldn't have an opinion about which application is better?

--

Ubuntu is not Sidux. Neither is it Debian. Keeping an application because it works isn't necessarily the right thing, but changing it before it's ready is not the right thing either. Pidgin works and has features that Empathy does not yet have (e.g. OTR). Empathy has features that Pidgin does not (e.g. video calling). Empathy should replace Pidgin, but only once I can transfer my five years-worth of data across. I use Thunderbird, so I have access to my email since I used Netscape Communicator. I use Pidgin, so I have access to my chat logs since 0.6ish.

Replacing Pidgin with Empathy at this point is like replacing Firefox with Chrome (Chromium). It certainly would get more testing done on Chromium, and WebKit is a newer technology, but it lacks features Firefox already has.

Not sure if any of this post makes sense...

---

### Post by 23meg on 2009-08-08
I've merged the two threads on the same subject.

---

### Post by Katalog on 2009-08-08
> **Bios Element said:**
> And are the Pidgin devs ever going to even start working on it? ;) Nope. >.> That's probably the biggest cause of the switch. **Pidgin is turning into a dead project**.

What makes you say that? I'm running version 2.5.8 on Jaunty right now, which was realeased less than 2 months ago (of which their is a working version for Karmic sitting in the Pidgin Dev PPA as well), and they are conducting development on 2.6.0 as we speak. Call me cynical, but dead projects typically don't release regular updates, do they (unless you know something I don't)? :confused:

---

### Post by 3rdalbum on 2009-08-08
Empathy doesn't seem much better than it was a year ago. Pidgin isn't any better than it was a year ago. But I agree that we need Telepathy deployed widely so applications can start using it for cool stuff.

---

### Post by Regenweald on 2009-08-08
> **jfernyhough said:**
> Should I drop the other work I'm doing to help on Empathy? You know, the other bug testing and translation and support? Or should I keep going on what I can do and assume the rest of the system will work when I want it? Are you saying that because I don't work on Empathy code this means I shouldn't have an opinion about which application is better?



I should not have to explain to you that you are CLEARLY not the type of user i was referring to. Empathy is in. pidgin is out. We are all free to do as we wish. I think i'll help test empathy.

---

### Post by 243kof on 2009-08-09
I think this debate is going in circles. Both sides have valid arguments. One user doesn't care about audio and video, an other doesn't care about Pidgin's features and plugins... not everyone can be pleased. As many have said before, experienced users will continue to use Pidgin if they want, so no big deal for them. As for new users, if they ask about a missing feature in Empathy I'm sure someone in here will point them to Pidgin. Besides, let's not judge an unfinished product, it is my understanding that Empathy is under heavy development at the moment, so we should wait for the final version (the one that's going into Karmic) before we compare features.. Peace :)

---

### Post by dext on 2009-08-09
im sure development on Empathy has Frozen so no new features can make its way into it untill Gnome3 gets under way

---

### Post by jfernyhough on 2009-08-09
> **Regenweald said:**
> I should not have to explain to you that you are CLEARLY not the type of user i was referring to. Empathy is in. pidgin is out. We are all free to do as we wish. I think i'll help test empathy.Yeah, sorry. It was late. :)

---

### Post by Stereotypical Rage on 2009-08-09
> **dext said:**
> im sure development on Empathy has Frozen so no new features can make its way into it untill Gnome3 gets under way

Empathy as it stands now should not enter into Karmic+1 (which would seem to be a LTS release). I just hope it's stability, aesthetics and features are up to snuff. One of the main things that makes Pidgin so great is its cross platform ability. Which helps ease the transition from Windows or another platform to Ubuntu (Linux). Who else is getting on the Empathy bandwagon? Novell? RedHat? Slack? Debian?

---

### Post by zekopeko on 2009-08-09
> **Stereotypical Rage said:**
> Empathy as it stands now should not enter into Karmic+1 (which would seem to be a LTS release). I just hope it's stability, aesthetics and features are up to snuff. One of the main things that makes Pidgin so great is its cross platform ability. Which helps ease the transition from Windows or another platform to Ubuntu (Linux). Who else is getting on the Empathy bandwagon? Novell? RedHat? Slack? Debian?

Fedora has Empathy as default IM. And I think that it's an official part of Gnome.

The whole point of trying to push Empathy into Karmic is to get it up to snuff by the time of Karmic+1. Even if it doesn't get it you guys/girls have produced enough bug reports to make this thing rock, and Empathy has certainly benefited from the exposure.

---

### Post by Stereotypical Rage on 2009-08-09
> **zekopeko said:**
> Fedora has Empathy as default IM. 

According to the below page, you would incorrect (although the page seems to be a contradiction).

[https://fedoraproject.org/wiki/Features/Empathy](https://fedoraproject.org/wiki/Features/Empathy)

> And I think that it's an official part of Gnome.  As of 2.24, yes I believe it is.

> The whole point of trying to push Empathy into Karmic is to get it up to snuff by the time of Karmic+1. Even if it doesn't get it you guys/girls have produced enough bug reports to make this thing rock, and Empathy has certainly benefited from the exposure.

You have to admit it's pretty lackluster right now. What's to say it's actually going to change pretty much over night?

I know I won't make the switch unless I can convert my 5 years worth of pidgin/gaim logs over. I would love to switch and help test, but there's several areas in which I can not give up.

---

### Post by zekopeko on 2009-08-09
> **Stereotypical Rage said:**
> According to the below page, you would incorrect (although the page seems to be a contradiction).

[https://fedoraproject.org/wiki/Features/Empathy](https://fedoraproject.org/wiki/Features/Empathy)

You asked about who is getting one the Empathy bandwagon. And I answered. Bad choice of a verb on my part.

> You have to admit it's pretty lackluster right now. What's to say it's actually going to change pretty much over night?

I know I won't make the switch unless I can convert my 5 years worth of pidgin/gaim logs over. I would love to switch and help test, but there's several areas in which I can not give up.

Well that just depends on what are you looking in a IM client. Empathy would be only installed by default for those people that are doing a clean install. Upgrades would still have Pidgin.

Migrating your logs certainly is a must have. Empathy can already import accounts from Pidgin. I don't know if that applies for logs but if it doesn't report a bug.

---

### Post by Stereotypical Rage on 2009-08-09
> **zekopeko said:**
> Well that just depends on what are you looking in a IM client.

Pretty much everything that Pidgin offers, but my main things...

* GTalk/Jabber, IRC, AIM, MSN/WLM, Yahoo, ICQ, Facebook, and MySpace protocols. (sadly I use them all)

* User to User Encryption (Like Pidgin's OTR)

* SSL support for all protocols.

* Libnotify support

* Migration from Pidgin support.

>  Empathy would be only installed by default for those people that are doing a clean install. Upgrades would still have Pidgin. I'm aware of that as a long time user. However, someone who is looking to make the switch from Windows to Linux may be disappointed to find that Pidgin isn't installed by default. Pidgin does help bridge the gap.

> Migrating your logs certainly is a must have. Empathy can already import accounts from Pidgin. I don't know if that applies for logs but if it doesn't report a bug.

I won't even think about switch to Empathy until my basic needs are met.:-P

---

### Post by Joe_Bishop on 2009-08-09
Pidgin is rarely used app in windows world, so it's not a problem.

---

### Post by xebian on 2009-08-09
I tried Empathy and it's pretty much lacking in features like privacy options.

 I could not add an account because I think it wants a password though it never said anything/complains about it.  I never store any password in my box so this is pretty bad.  I type password when I connect.  Kopete tries to do that but it never 'forces' you.

---

### Post by wayne_cat on 2009-08-09
> **gnomeuser said:**
> Works for me, please file a bug.

confirmed ... no problems with empathy and MSN

---

### Post by Katalog on 2009-08-09
Despite my earlier opposition to the possibility of changing the default IM client to Empathy, I decided for the sake of fairness to add the Empathy PPA to my sources and give it a fair trial. Three of my main concerns quickly dissipated  after having installed Empathy alongside Pidgin:

1. Development seems to be moving at an incredibly rapid pace on this application. There are updates which take place almost daily which seem to improve the app considerably. 

2. Upon first installing Empathy, it offered to import nearly all of my account settings from Pidgin. This was a nice surprise and one which I did not expect, and it even offer to import my Ekiga settings! (which I haven't had the nerve to try yet, but will soon).

3. My biggest fear, which was lacking compatibility with MSN, has now disappeared. The development and improvement of telepathy-butterfly have allowed my MSN account to now integrate and work almost flawlessly.

So my opinion on this issue is changing rapidly, and I dare say that we may not even have to wait for Karmic +1 to see this as the default IM client. I have to say that after all my grousing concerning this proposed change I am now certainly more in favor of it than I was previously. Now I just have to get Facebook working and things should then be right with the world.

---

### Post by zekopeko on 2009-08-09
> **Katalog said:**
> 2. Upon first installing Empathy, it offered to import nearly all of my account settings from Pidgin. This was a nice surprise and one which I did not expect, and it even offer to import my Ekiga settings! (which I haven't had the nerve to try yet, but will soon).

Does the importer import log/chat-history files from pidgin?

---

### Post by Katalog on 2009-08-09
> **zekopeko said:**
> Does the importer import log/chat-history files from pidgin?

I'm not sure, and I can't really remember if it offered to or not.

---

### Post by rajeev1204 on 2009-08-10
One thing i feel is really lame on the developers part is showing an audio and video call option when you right click when that thing doesnt work.

At least the pidgin devs make it clear they will implement it when they have time.

Total nonsense.I dont understand why the empathy fans here seem to have taken that lightly.

This is like ubuntu promising a new look and not delivering on them.Or internet explorer 6 having a tab button but greyed out . :|

---

### Post by gnomeuser on 2009-08-10
> **rajeev1204 said:**
> One thing i feel is really lame on the developers part is showing an audio and video call option when you right click when that thing doesnt work.


It's currently only implememted support for certain protocols

> 
At least the pidgin devs make it clear they will implement it when they have time.


And have done so for years. Besides current ideas in this direction rely on using telepathy farsight2, the same as Empathy so support will land at the same time, if not earlier in Empathy.

> 
Total nonsense.I dont understand why the empathy fans here seem to have taken that lightly.


Your raving and rantings are clearly the product of insufficient research, why should I take it seriously again?

> 
This is like ubuntu promising a new look and not delivering on them.Or internet explorer 6 having a tab button but greyed out . :|


First artwork drop for Karmic is late this month, you may want to make yourself familar with the schedule. A new look is not just a new theme, it means rethinking the underlying technology to allow for the things we can imagine. Little pieces of this vision are arriving such as notify-osd. Again education isn't a bad thing you know.

> 
No need to suck up too much to the empathy developers.

It's not about sucking up to anyone but about betting on the best technology (telepathy) and the implementation that gives us the best integration and possibilities for future development. Empathy is where we want to go, there will though always be regressions in functionality when such a switch is implemented. These will naturally be filled and heaps of new functionality will be added as well. The implication that we are "sucking up" to someone is deeply offensive, this is a decision based solely on technology.

---

### Post by rajeev1204 on 2009-08-10
k

---

### Post by rajeev1204 on 2009-08-10
ok

---

### Post by gnomeuser on 2009-08-10
> **rajeev1204 said:**
> Best technology is subjective,but ill give canonical the benefit of doubt.


Best technology is not subjective, it depends on your goals. Say if I have the choice between a gun and a can opener. Both fine technological marvels, but which is better. For murder probably the gun (though a can opener might have impressive results if used improperly), if I am opening a can of tuna for my sandwich most definitely a can opener.

When we debate communications technology we look at pidgin and telepathy/empathy, it is clear to assert that the latter presents a very well designed solution for the problems we face as well as letting us expand support and integrate into the desktop, and the other simply does not in any pleasant way.

> 
I will delete that line if its offensive.But its true anyway.Your bias is very evident.I suggest you dont reply to my threads or posts if you just want to run me down everytime.I dont want any arguments with you.


If you won't say it but still hold the opinion what has changed?  I consider technical debate very fruitful, I will correct anyone who makes a purely emotional argument or gets facts plainly wrong. I hope people will do the same with me.

> 
I dont know how to multi quote,thats sad.


It's fairly straight forward, just insert the quotation codes yourself [ quote ] and [ / quote ] (without spaces) around the parts you want to quote specifically. I agree it could be made easier but this way works.

> 
Also,why do you keep referring to yourself as 'we want to take this direction', as if you are an ubuntu rep.


I use we because I am part of the community, I am also active in a few projects, Ubuntu being one of them. It's a habit that came early in my involvement with Open Source, once you feel part of something, it's much easier to consider it as being part of the "family", there is an emotional connection and an investment in time and knowledge.

To me the community is a big part of why I like Linux, I have made many friends through my involvement with Linux and I have learned a lot from the people I have worked with. I am very grateful for those chances to connect. I hope other people feel the same way.

---

### Post by rajeev1204 on 2009-08-10
> **gnomeuser said:**
> It's currently only implememted support for certain protocols

So that means its ok if a user is adding a protocol for IM from add accounts window and empathy says 'sorry this protocol is not supported yet'? No it isnt.If some feature is incomplete then dont give an option which is greyed out.Leave it out completely.

And have done so for years. Besides current ideas in this direction rely on using telepathy farsight2, the same as Empathy so support will land at the same time, if not earlier in Empathy.

I agree on this.

Your raving and rantings are clearly the product of insufficient research, why should I take it seriously again?

Its not personal,so no need to use the 'I'.Iam talking in general.

First artwork drop for Karmic is late this month, you may want to make yourself familar with the schedule. A new look is not just a new theme, it means rethinking the underlying technology to allow for the things we can imagine. Little pieces of this vision are arriving such as notify-osd. Again education isn't a bad thing you know.

Iam very much aware of artwork first and second drop and UI freeze.Please keep your sarcasm to yourself.Thank you.

It's not about sucking up to anyone but about betting on the best technology (telepathy) and the implementation that gives us the best integration and possibilities for future development. Empathy is where we want to go, there will though always be regressions in functionality when such a switch is implemented. These will naturally be filled and heaps of new functionality will be added as well. The implication that we are "sucking up" to someone is deeply offensive, this is a decision based solely on technology.

I deleted that line,i should have used a milder statement.Sorry about that one.

I just want 'you' to know,iam not against empathy on the whole.Iam ok with it.I voted yes in the polls btw.Surprised?

I hope i learn to multi quote soon.Iam bad at that.Please check inside the quote for replies.

regards
rajeev

---

### Post by novafluxx on 2009-08-10
> **Stereotypical Rage said:**
> Empathy as it stands now should not enter into Karmic+1 (which would seem to be a LTS release). I just hope it's stability, aesthetics and features are up to snuff. One of the main things that makes Pidgin so great is its cross platform ability. Which helps ease the transition from Windows or another platform to Ubuntu (Linux). Who else is getting on the Empathy bandwagon? Novell? RedHat? Slack? Debian?

You just hit the nail on the head for me right there. I enjoy being able to the Firefox, Pidgin, OpenOffice, from Linux and Windows. I use them not only because I prefer them, but also because of their cross-platform compatability.

When Chrome stable (or beta even) is released for Linux, I will probably switch from Firefox to Chrome, as I'll be able to use it on both of my systems. My Windows gaming box (mainly), and my Linux everything else box :)

I've looked at Empathy for a total of about 5 minutes, and I thought it looked like something from the late 90s. The UI brought back memories of my Windows 98 days, and I instantly returned to Pidgin. Granted this was months ago, and apparently the Empathy development has been in high gear lately...

---

### Post by rajeev1204 on 2009-08-10
> **novafluxx said:**
> 
I've looked at Empathy for a total of about 5 minutes, and I thought it looked like something from the late 90s. The UI brought back memories of my Windows 98 days, and I instantly returned to Pidgin. Granted this was months ago, and apparently the Empathy development has been in high gear lately...


UI work is going on very fast.I think it will drop in during second UI drop.Probably gnomeuser knows better regarding this.Otherwise i agree with you on the UI  front.

Seems to be a hasty decision indeed on the developers part.But if they confidence they can pull it off, i want to support them every way.

So i have toned down my rants.:)


regards

rajeev

---

### Post by novafluxx on 2009-08-10
> **rajeev1204 said:**
> So i have toned down my rants.:)

Thats good :lolflag:

I'm eager to check out Karmic, I'll probably wait until Alpha 4, since thats about where I picked up Jaunty. I tried a daily-live from August 6th, and it didn't install the drivers for my Broadcom wireless card, and they weren't listed as available proprietary drivers wither, so I had no internet access...so I rebooted into Windows :P

I want to see how Empathy's coming along!

---

### Post by Merk42 on 2009-08-10
> **rajeev1204 said:**
> UI work is going on very fast.I think it will drop in during second UI drop.Probably gnomeuser knows better regarding this.Otherwise i agree with you on the UI  front.


Even if the UI ends up being **better** than Pidgin, it's not cross-platfrom

---

### Post by rajeev1204 on 2009-08-10
> **Merk42 said:**
> [QUOTE=rajeev1204;7763136]UI work is going on very fast.I think it will drop in during second UI drop.Probably gnomeuser knows better regarding this.Otherwise i agree with you on the UI  front.
/QUOTE]

Even if the UI ends up being **better** than Pidgin, it's not cross-platfrom

Dont blame me,its the devs who chose this path.

I always did prefer pidgin and continue to favour it.Atleast considering how efficiently it works.Well,at least on the surface.

---

### Post by zekopeko on 2009-08-10
> **Merk42 said:**
> Even if the UI ends up being **better** than Pidgin, it's not cross-platfrom

Yet...

And we aren't trying to improve Windows, are we?

---

### Post by zekopeko on 2009-08-10
@rajeev1203

You need to have everything you want to quote inside >  tags.
Here is an example:

[QUOTE]This is quote #1

My response to quote #1

----------------------------
And this is how it looks when you enter in the reply text field:

[HTML]> This is quote #1

My response to quote #1[/HTML]

So just find the sentence you want to respond to, select it, press the QUOTE button (the little text bubble), respond to it, then repeat for the rest of the text you want to quote and respond to. Hope this helps.

---

### Post by Merk42 on 2009-08-10
> **zekopeko said:**
> Yet...

And we aren't trying to improve Windows, are we?

Well no I was just relating to novafluxx about migrating to Linux from Windows and having familiar programs

Plus in my dual boot case I share the same logs file across Windows and Linux, obviously I'm a very small case for that though.


In other news, for some reason my quote got messed up (I since edited and fixed it) which is why when rajeev1203 quoted me it got all messed up

---

### Post by gnomeuser on 2009-08-10
> **Merk42 said:**
> Even if the UI ends up being **better** than Pidgin, it's not cross-platfrom

Nothing is preventing it from being cross platform so far as I can see, have at it. It just happens not to be a priority for Collabora (the company that sponsors a lot of the empathy/telepathy work currently). 

If you care deeply enough learn C and try porting it.

We care about making Ubuntu better, you want to also make Windows better I salute you and welcome your contributions.

---

### Post by andrewabc on 2009-08-10
> **novafluxx said:**
> Thats good :lolflag:

I'm eager to check out Karmic, I'll probably wait until Alpha 4, since thats about where I picked up Jaunty. I tried a daily-live from August 6th, and it didn't install the drivers for my Broadcom wireless card, and they weren't listed as available proprietary drivers wither, so I had no internet access...so I rebooted into Windows :P

I want to see how Empathy's coming along!

Yes, wait until alpha 4 this Thursday, since it's only 3 days away. And if you still have the no wireless drivers problem, look to see if bug has been reported, and if not make one so maybe it will get fixed :)

I usually test new ubuntu starting at alpha 2 or 3 to make sure everything works on my computers. If not I figure out why and try to get it fixed. No point in waiting until release day to reailize it doesn't work properly on your computer. ;)

---

### Post by miegiel on 2009-08-11
can't say empathy is ready till blocking contacts is implemented :(

---

### Post by novafluxx on 2009-08-11
Yes, the client-protocall specific privacy features/functions are essential to me

---

### Post by dext on 2009-08-11
even though i have voted i think privacy settings are essentiaal for Empathy to becoming default

---

### Post by Marat89 on 2009-08-12
I have a question to empathy.
I testet some old versions but have major issues with Files transfers (ICQ)

In Pidigin you have not the feature to receive or send more than one file per transfer. Is this with empathy possible???

---

### Post by Marat89 on 2009-08-13
Bump :-)

---

### Post by dext on 2009-08-13
> **Marat89 said:**
> I have a question to empathy.
I testet some old versions but have major issues with Files transfers (ICQ)

In Pidigin you have not the feature to receive or send more than one file per transfer. Is this with empathy possible???

i dont think what you want is possible im Empathy at the moment

---

### Post by Marat89 on 2009-08-13
then empathy has no major advantages for me

---

### Post by rajeev1204 on 2009-08-13
Empathy has long been promising voice and video like pidgin, but currently it only works for google talk, But if the user at the other end is using google's client, then voice calls is not possible :rolleyes: .So that makes 99% of the user base including me using gtalk on windows who cant do voice calls.

MSN support is being worked on like they say.Also, i dont get the point of using amsn either since it does not support voice.How someone can chat using video without voice is beyond me.

[http://live.gnome.org/Empathy/FAQ#head-42d5d34dc7fce244952e8b304a8e26aef77cd1a9](http://live.gnome.org/Empathy/FAQ#head-42d5d34dc7fce244952e8b304a8e26aef77cd1a9)

So as of now,it doesnt do anything better than pidgin.So i guess,it doesnt make much difference what they use in karmic,since neither can do anything more than chat.I hear empathy cant even do file transfers yet,but probably thats been fixed.

---

### Post by Joe_Bishop on 2009-08-13
> Empathy has long been promising voice and video like pidgin, but currently it only works for google talk, But if the user at the other end is using google's client, then voice calls is not possible  .So that makes 99% of the user base including me using gtalk on windows who cant do voice calls.
For me it worked properly only if one used google talk official client. Empathy-empathy didn't work properly. Empathy-Empathy didn't work well, today they can't connect to each other in my experience at all. And it theoretically supports jingle as well (doesn't work for me too), not only gtalk.

---

### Post by 243kof on 2009-08-13
> Empathy has long been promising voice and video like pidgin, but currently it only works for google talk,

Well, it's a start, isn't it? :)

> But if the user at the other end is using google's client, then voice calls is not possible 

Last time I heard, voice calls between empathy and the gtalk client worked. I know I have used this kind of interoperability since at least a year ago. Also, the link to the Empathy FAQ that you provided reads:

"You can have a video conversation with your Google Talk contact, but not if they are using the GTalk client. Audio call to either the Google Talk desktop client or their Web client should work but not video."

So it's the video call to the gtalk client that doesn't work, not audio! The gtalk client doesn't support video calls anyway. :)

---

### Post by rajeev1204 on 2009-08-13
> **243kof said:**
> Well, it's a start, isn't it? :)



Last time I heard, voice calls between empathy and the gtalk client worked. I know I have used this kind of interoperability since at least a year ago. Also, the link to the Empathy FAQ that you provided reads:

"You can have a video conversation with your Google Talk contact, but not if they are using the GTalk client. Audio call to either the Google Talk desktop client or their Web client should work but not video."

So it's the video call to the gtalk client that doesn't work, not audio! The gtalk client doesn't support video calls anyway. :)

I could never get empathy to dial to a  google talk user.Just couldnt see how to.Bad UI.

gtalk supports video and now , it even supports video chat inside gmail. You are late :D

My mistake- client doesnt support video (thats strange) .

---

### Post by hellion0 on 2009-08-13
Empathy's actually regressed in terms of Jabber support that I've noticed (my Jabber account which works in Pidgin 2.5.8 fails to work in Empathy 2.27.5, both on Karmic), so no, I can't agree with any proposal to make it default as of yet.

---

### Post by rajeev1204 on 2009-08-13
hooray.

I just saw the audio call button near a fried using gtalk.

Couldnt try calling but will probably try soon.

I hope audio gets implemented across all protocols.Is that possible for karmic?

---

### Post by zekopeko on 2009-08-13
> **rajeev1204 said:**
> hooray.

I just saw the audio call button near a fried using gtalk.

Couldnt try calling but will probably try soon.

I hope audio gets implemented across all protocols.Is that possible for karmic?

Not for Karmic. But then again jabber audio support beats no support.

---

### Post by fluffman86 on 2009-08-13
Let me preface this by saying that I'm a Tech Support Guy, providing Tech Support and computer lessons to individuals and businesses in the area.  One of my main lessons is "Don't be afraid to *USE* your computer.  Most things can be figured out easily if you just stop and *THINK* instead of trying to memorize where everything is."

Also, I've been using Ubuntu exclusively at home for 2 and a half years and have been using Gaim/Pidgin since 2005.

I say this because I want you to fully understand what I'm saying when I tell you that Empathy is confusing and hard to use.  

I upgraded to Karmic and tried empathy the other day.  First thing it does is import contacts/accounts from Pidgin.  Wow, that's actually cool.  Except half of them had the wrong username listed.  So I change everything and verify everything and I get 10 popups from Telepathy asking to connect to the default keyring.  I've successfully switched lots of people to Ubuntu, and I tell them it's safer because it asks you for you password for certain things.  If you didn't click anything then don't give your password.  If this was confusing *for me*--and I had actually read about what Telepathy was--then how much more confusing will it be for n00bs?

OK, so it looks like everything is working, or at least I'm not getting errors.  Wait...where's my MSN accounts?  I mean, my name is showing up 5 times in my buddy list (no meta-contacts as per pidgin), but my MSN account isn't there.  So I go back into the account dialog and see that MSN isn't checked.  So I try to click the check box.  Nothing.  It won't check.  So I deleted the account and added an "MSN Haze" account.   Now I get connection errors.  

Well, that's fine.  I'll just ignore MSN for now.  Let me try to regroup my accounts into one group.  Hmm...can't drag and drop.  Oh, I have to right-click, choose properties, and select a new group for each of my personas.  That sucks.  

Lets move on to IRC.  Where are my IRC accounts?  How do I join a channel?  I clicked EVERYWHERE, but nothing.  Let's check the account dialog and...all of my IRC names have been changed to my real name, instead of fluffman.  WTF?  So I change them all back and...nothing.  Nothing happens when I change the IRC information.  So I delete the accounts to re-add them, which is apparently impossible.

So here's my 0.02 dollars:  I don't think it's a good idea to include as default a program that a technologically savvy person can't figure out after an hour or two of fiddling with it, and that doesn't allow newcomers to Ubuntu to connect to IRC, one of Ubuntu's (and Empathy's! Ha!) own support methods.

---

### Post by kingborel on 2009-08-13
Welcome to **ALPHA 4** of (k)Ubuntu. Please file bugs for all those things you found problems with

---

### Post by msvolenski on 2009-08-13
Pidgin has the unwelcome problem that it doesn't support audio and video conversations yet, but they are already developping it. If I'm living this way, I could wait some more time. I read Empathy has this support just for GTalk and it's developping to others too...

Changing a promise for another,  I think I prefer Pidgin, it's interface is more beatiful and I'm already knows how to use it well. Also, it would be necessary to migrate my logs.

---

### Post by novafluxx on 2009-08-13
> **msvolenski said:**
> Pidgin has the unwelcome problem that it doesn't support audio and video conversations yet, but they are already developping it. If I'm living this way, I could wait some more time. I read Empathy has this support just for GTalk and it's developping to others too...

Changing a promise for another,  I think I prefer Pidgin, it's interface is more beatiful and I'm already knows how to use it well. Also, it would be necessary to migrate my logs.

I like how Pidgin can be used on multiple platforms as well, ie Windows.

I use Windows as my main OS on my desktop because, well, I play computer games!

I use Pidgin because the interface is the same on my laptop (running Ubuntu) and my desktop. I have a multitude of plugins available for me use if I want them.

I do, however, miss audio/video...Pidgin has REALLY been lacking on this front.

My experiences with Empathy have been sad to say the least, I tried it in Intrepid, Jaunty, and I will be trying it in Karmic. Its never looked modern, or very user friendly.

---

### Post by kingborel on 2009-08-13
If people don't like Empathy, just install Pidgin? I don't see the problems. You don't have to take the defaults for everything

---

### Post by dext on 2009-08-14
> **kingborel said:**
> If people don't like Empathy, just install Pidgin? I don't see the problems. You don't have to take the defaults for everything
but making Empathy the default now is pointless when it lacks features like **Privacy** an possibly doesnt do other things to well currently. when Pidgin has most features like Privacy an others, just lacks Voice/Video its best IMO to stay with Pidgin till Empathy shows or starts to show more features

---

### Post by mrgnash on 2009-08-14
The problem with both Pidgin and Empathy for me is that they are chasing maximum compatibility for too many, closed/proprietary, protocols. As you can see with the latest Pidgin changelogs, they've been furiously trying to get Yahoo working after changes to the authentication protocol. Trying to play "catch up" with these protocols, when the providers are not in the least bit interested in providing support for third-party developers is not only a losing battle in many ways, but one that consumes an inordinate amount of time and effort -- time and effort that could otherwise be spent implementing new features (such as voice/video talk). For that reason, I think the most promising messenger for open source platforms like Linux, would be something like Synapse, that concentrates on implementing all the features in an open-spec protocol like XMPP. 

I know that people will bring up their need to communicate with people using Yahoo/MSN/whatever, but frankly, I've encountered little difficulty in convincing the majority of my contacts to use something like Google Talk; once I explain the advantages, or how easy it is to access (many of them already have Gmail, so it's just a matter of them logging in and accessing the built-in messenger there). And for those sticks-in-the-mud who cling to rubbish clients like MSN and Yahoo, I'm quite happy to cease communicating with them... but then, I am a bit less socially oriented than most people, I suppose ;)

---

### Post by rajeev1204 on 2009-08-14
I agree with Mrgnash here,i personally have seen a very small shift to clients like gtalk,i hardly even use yahoo now,we need a single unified protocol like xmpp maybe ,and every single person i know of is now using skype for video and voice.Its not open source but doesnt really matter.Its works great.

So empathy or pidgin,both are in the race to tackle something which they probably will never achieve or maybe they just dont need to.

---

### Post by MacUntu on 2009-08-14
"No" leads, I win! :P

---

### Post by Staz on 2009-08-15
> **MacUntu said:**
> "No" leads, I win! :P

Thanks for summarizing exactly what's wrong in this thread ;)

The debate over the inclusion of pidgin or empathy as the default in Ubuntu is not about either side winning or losing. It's about what is best for the users, Ubuntu (and Free Software in general) in the future. So let's not just promote something because it's our pet project.

Sure as Telepathy contributor, I would love to have it included as the default. Not only because it would be a recognition of all the hard work put in it and it would offer a boost in it's development, but because I truly believe it's an unique opportunity to offer a truly integrated IM framework in the desktop, that other applications can take advantage and that it would offer a much better experience for the users.

But if Ubuntu finally decide to not include it as the default in Karmic, I will understand, I would rather have it wait than offer a bad experience that will ruin Telepathy image in the future. 

Yes it's a compromise to make, you lose some features and you gain others (you gain possibilities that open up too) but the debate should be whether this compromise is worth to make.

So let's discuss this rationally with arguments rather than with emotionally filled rants.

---

### Post by Katalog on 2009-08-15
Well, it almost appears as though the decision on whether or not to use Empathy as the default may have already been made. I just took a look at Alpha 4, and there it is in the Favorites menu. I can't recall for sure, but I think Pidgin was still there in Alpha 3. But anyway, this debate may already be moot, since if it's gonna be the default I guess it doesn't really matter whether we think it's ready or not.

---

### Post by andrewabc on 2009-08-15
The empathy in alpha 4 has msn http support, or at least a http connection checkbox (but it did not connect, my connection is very picky).

I'm using jaunty with PPA
[http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu)
and it doesn't have msn http support. I thought PPA had most up to date version?

---

### Post by coldReactive on 2009-08-15
I say no. I need to be able to have the new line plugin, and the ability to turn off/on incoming formatting, and set the height of the input box, among other things.

As soon as I get koala, I'm removing empathy and installing pidgin.

---

### Post by Neon Lights on 2009-08-15
> **Katalog said:**
> Well, it almost appears as though the decision on whether or not to use Empathy as the default may have already been made. I just took a look at Alpha 4, and there it is in the Favorites menu. I can't recall for sure, but I think Pidgin was still there in Alpha 3. But anyway, this debate may already be moot, since if it's gonna be the default I guess it doesn't really matter whether we think it's ready or not.
as far as I know, it's still only in for **testing purposes**.
If I'm wrong, someone please correct me. :)

---

### Post by Ranax on 2009-08-15
Kopete is much better than either of them.

---

### Post by coldReactive on 2009-08-15
> **Ranax said:**
> Kopete is much better than either of them.

And if you don't like KDE?

---

### Post by Ranax on 2009-08-15
> **coldReactive said:**
> And if you don't like KDE?

It works with GNOME, XFCE, Fluxbox so?

Or do you mean *anything* KDE based?

---

### Post by coldReactive on 2009-08-15
> **Ranax said:**
> It works with GNOME, XFCE, Fluxbox so?

Or do you mean *anything* KDE based?

I kind of boycotted anything KDE as soon as I tried to use the livecd of Kubuntu 7.10, when it couldn't detect my harddrives.

---

### Post by Zatara214 on 2009-08-16
No from me.  I'm using both Pidgin 2.6.0 and Empathy 2.27.5 in my new install of Fedora (Ubuntu... rest in peace, I may have messed with it a bit too much...).  After importing a single account into Empathy from Pidgin (an MSN Haze account with about 20 contacts), I decided to switch them all to the same group.  Amazed ay how fast Empathy was able to perform this task, I was not entirely surprised to find that it has actually erased every single one of my contacts in the process.

Great, so now I've lost 20 contacts thanks to some bug in Empathy.  Pidgin is perfectly stable, and until Empathy gets its act together with bugs, I'll continue to use Pidgin.  I'm not going to risk losing all of my contacts in favor or http support in MSN.  I'll stick with stability.

---

### Post by meborc on 2009-08-16
> **coldReactive said:**
> I kind of boycotted anything KDE as soon as I tried to use the livecd of Kubuntu 7.10, when it couldn't detect my harddrives.

off-topic... you do know that detecting harddrives is something totally not related to KDE, which is just a desktop environment and in case of kubuntu uses ubuntu as its base... so you should boycott all things that have ubuntu base instead ;)

---

### Post by coldReactive on 2009-08-16
> **meborc said:**
> off-topic... you do know that detecting harddrives is something totally not related to KDE, which is just a desktop environment and in case of kubuntu uses ubuntu as its base... so you should boycott all things that have ubuntu base instead ;)

Ubuntu and Xubuntu could detect my HDD though.

However, Fedora could only detect them, it couldn't auto-mount them. Kubuntu simply didn't detect them at all.

---

### Post by meborc on 2009-08-16
> **coldReactive said:**
> Ubuntu and Xubuntu could detect my HDD though.

However, Fedora could only detect them, it couldn't auto-mount them. Kubuntu simply didn't detect them at all.

that means there was some difference in kubuntu setup... but still nothing that KDE is responsible for

unfortunately kubuntu has never had the love from developers as gnome based ubuntu has enjoyed, KDE on the other hand is one of the fastest developing projects in the foss economy

---

### Post by mike310z on 2009-08-16
> **Zatara214 said:**
> No from me.  I'm using both Pidgin 2.6.0 and Empathy 2.27.5 in my new install of Fedora (Ubuntu... rest in peace, I may have messed with it a bit too much...).  After importing a single account into Empathy from Pidgin (an MSN Haze account with about 20 contacts), I decided to switch them all to the same group.  Amazed ay how fast Empathy was able to perform this task, I was not entirely surprised to find that it has actually erased every single one of my contacts in the process.

Great, so now I've lost 20 contacts thanks to some bug in Empathy.  Pidgin is perfectly stable, and until Empathy gets its act together with bugs, I'll continue to use Pidgin.  I'm not going to risk losing all of my contacts in favor or http support in MSN.  I'll stick with stability.

I have empathy 2.27.5 running on ubuntu 9.04 and it is a miserable experience compared to skype.  Google chat voice calls always hang empathy whether I am the recipient or caller. Much as I would love to consolidate all my communications I have to stick to skype as the only platform that for me has worked across MAC, Windows and Linux.

---

### Post by Taiebot65 on 2009-08-16
You can not lose any contacts but just the preferences...Because they are stored by your account. So it will import only your login and password.

---

### Post by aamukahvi on 2009-08-16
> **Taiebot65 said:**
> You can not lose any contacts but just the preferences...Because they are stored by your account. So it will import only your login and password.
A bug in the account/contact list handling may very well wipe out your contacts even if they are on the server side.

---

### Post by Staz on 2009-08-16
> **Zatara214 said:**
> No from me.  I'm using both Pidgin 2.6.0 and Empathy 2.27.5 in my new install of Fedora (Ubuntu... rest in peace, I may have messed with it a bit too much...).  After importing a single account into Empathy from Pidgin (an MSN Haze account with about 20 contacts), I decided to switch them all to the same group.  Amazed ay how fast Empathy was able to perform this task, I was not entirely surprised to find that it has actually erased every single one of my contacts in the process.

Great, so now I've lost 20 contacts thanks to some bug in Empathy.  Pidgin is perfectly stable, and until Empathy gets its act together with bugs, I'll continue to use Pidgin.  I'm not going to risk losing all of my contacts in favor or http support in MSN.  I'll stick with stability.

Wow this is a serious bug, can you please fill a bug a bug report?
Does the contacts have been removed in Pidgin too?

---

### Post by meeples on 2009-08-16
ive been using empathy for a few days now, i never liked pidgin.

i love how you can add Adium conversation themes ;D

ive got mine set up like ichat. i love it.

---

### Post by nhasian on 2009-08-16
anyone know when Empathy is going to get telepathy-butterfly back?  I'm looking forward to testing the video conferencing with messenger...

---

### Post by dext on 2009-08-16
> **nhasian said:**
> anyone know when Empathy is going to get telepathy-butterfly back?  I'm looking forward to testing the video conferencing with messenger...
there is no Video Support in Empathy on the MSN protocol i dont think, only Video support Empathy has an thats GTalk protocol

---

### Post by nhasian on 2009-08-16
i know that telepathy-butterfly was pulled from empathy because it wasnt ready yet and was temporarily replaced with telepathy-haze.  telepathy-butterfly is supposed to have audio/video conferencing for the msn protocol.  the Karmic release date is creeping up now and i was hoping to test telepathy-butterfly and iron out any bugs before the big release day.

> **dext said:**
> there is no Video Support in Empathy on the MSN protocol i dont think, only Video support Empathy has an thats GTalk protocol

---

### Post by dext on 2009-08-16
telepathy-butterfly-0.5.0.tar.gz is probably the one your after to get that, i dont think it made it into Empathy-2.28.0  i think you'll see it in Empathy3.0.0 [http://telepathy.freedesktop.org/releases/telepathy-butterfly/](http://telepathy.freedesktop.org/releases/telepathy-butterfly/)

---

### Post by Katalog on 2009-08-16
> **nhasian said:**
> i know that telepathy-butterfly was pulled from empathy because it wasnt ready yet and was temporarily replaced with telepathy-haze.  telepathy-butterfly is supposed to have audio/video conferencing for the msn protocol.  the Karmic release date is creeping up now and i was hoping to test telepathy-butterfly and iron out any bugs before the big release day.

telepathy-butterfly is in the telepathy ppa (I have it installed right now), so I have MSN support but no video. All telepathy-haze has done is help me get Facebook support working in Empathy. Running it in Empathy 2.27.5.

EDIT: My bad. I just looked at the telepathy ppa and there is no build of telepathy-butterfly available for Karmic. My mistake.

---

### Post by soapytheclown on 2009-08-16
> **Katalog said:**
> telepathy-butterfly is in the telepathy ppa (I have it installed right now), so I have MSN support but no video. All telepathy-haze has done is help me get Facebook support working in Empathy. Running it in Empathy 2.27.5.

can you tell me how you got facebook contacts working with it, ive managed to get empathy to let me add a facebook account but it never actually signs in. Thanks :)

---

### Post by Katalog on 2009-08-16
> **soapytheclown said:**
> can you tell me how you got facebook contacts working with it, ive managed to get empathy to let me add a facebook account but it never actually signs in. Thanks :)

There are instructions out there somewhere on getting telepathy-haze to play ball with the Pidgin Facebook plugin. I always get a network error for Facebook when I first start Empathy, but if I click "Try again" it always seems to connect.

I believe these are the instructions I used:

[http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/](http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/)

---

### Post by Staz on 2009-08-16
> **Katalog said:**
> telepathy-butterfly is in the telepathy ppa (I have it installed right now), so I have MSN support but no video. All telepathy-haze has done is help me get Facebook support working in Empathy. Running it in Empathy 2.27.5.

EDIT: My bad. I just looked at the telepathy ppa and there is no build of telepathy-butterfly available for Karmic. My mistake.

Telepathy-butterfly is in Karmic so no need to put in the PPA, it's just not installed by default.

---

### Post by Staz on 2009-08-16
> **dext said:**
> telepathy-butterfly-0.5.0.tar.gz is probably the one your after to get that, i dont think it made it into Empathy-2.28.0  i think you'll see it in Empathy3.0.0 [http://telepathy.freedesktop.org/releases/telepathy-butterfly/](http://telepathy.freedesktop.org/releases/telepathy-butterfly/)

Just a note on how the telepathy framework works : All protocols backends run as separates programs communicating via d-bus. So telepathy-butterfly is not a lib that get linked by empathy but run as a separate process. So it doesn't need to be included into empathy and can be updated separately it just need to get packaged

> **dext said:**
> there is no Video Support in Empathy on the MSN protocol i dont think, only Video support Empathy has an thats GTalk protocol

Audio/Video support is not yet included in any telepathy-butterfly release, but it's coded, the code is being reviewed and tested and it's planned to have it in karmic

---

### Post by nhasian on 2009-08-16
> **Staz said:**
> Audio/Video support is not yet included in any telepathy-butterfly release, but it's coded, the code is being reviewed and tested and it's planned to have it in karmic

see thats what i'm talking about.  how can i get in on some of that testing?  :)  I have 3 laptops with empathy on them. two karmic and one jaunty 9.04.  I wanna help get this app ready for primetime.

---

### Post by novafluxx on 2009-08-16
I always used Yahoo audio/video more then MSN. Any word on if/when that will be implemented?

---

### Post by soapytheclown on 2009-08-17
> **Katalog said:**
> There are instructions out there somewhere on getting telepathy-haze to play ball with the Pidgin Facebook plugin. I always get a network error for Facebook when I first start Empathy, but if I click "Try again" it always seems to connect.

I believe these are the instructions I used:

[http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/](http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/)

brilliant thanks :D

---

### Post by ildella on 2009-08-19
hey. I am now using empathy on 9.04, from ppa and I am very happy now. I was concerned about empathy not being ready but right now is equal or superior to pidgin for IM, while I have not tried voice comm...

Anyway, good job, now completely happy about the change, I am sure that in the future will become a great app and platform.

---

### Post by freakalad on 2009-08-19
Pidgin 2.6 now has native support for video & voice - XMPP only, so unfortunately no SIP yet

[http://webupd8.blogspot.com/2009/08/pidgin-260-adds-voice-and-video.html](http://webupd8.blogspot.com/2009/08/pidgin-260-adds-voice-and-video.html)

---

### Post by zoomy942 on 2009-08-26
So I have been using Empathy and it works okay, but I'm unsure how to block spambots.  in Pigdin it's easy with a plugin.  Does Empathy have that?

---

### Post by coldReactive on 2009-08-26
> **zoomy942 said:**
> So I have been using Empathy and it works okay, but I'm unsure how to block spambots.  in Pigdin it's easy with a plugin.  Does Empathy have that?

Even if there is a plugin, there is no manager for them, so you can't install the plugin, and then expect a manager GUI to turn them on/off/config them.

By the way, if it hasn't already been mentioned: Empathy doesn't allow you to manually increase the default height of the text input, and this time, the default text input height is 1 line.

---

### Post by joey-elijah on 2009-08-26
> **coldReactive said:**
> Even if there is a plugin, there is no manager for them, so you can't install the plugin, and then expect a manager GUI to turn them on/off/config them.

By the way, if it hasn't already been mentioned: Empathy doesn't allow you to manually increase the default height of the text input, and this time, **the default text input height is 1 line**.

:confused: OH.EM.GEE.

---

### Post by fela on 2009-08-26
No, because pidgin works just fine.

Why change what works, huh?

---

### Post by coldReactive on 2009-08-26
> **fela said:**
> No, because pidgin works just fine.

Why change what works, huh?

Possible: Ubuntu doesn't like it when your passwords aren't encrypted. Pidgin doesn't encrypt saved passwords as it would "break" or "throttle down" or whatever to pidgin.

---

### Post by fela on 2009-08-26
> **coldReactive said:**
> Possible: Ubuntu doesn't like it when your passwords aren't encrypted. Pidgin doesn't encrypt saved passwords as it would "break" or "throttle down" or whatever to pidgin.

Does empathy?

I shouldn't even be in this thread really. I'm skipping 9.10, I'll install the 10.04 LTS straight when 10.10 comes out. Only after rigorous testing of course. I don't want, don't need, can't have a buggy system :)

---

### Post by joey-elijah on 2009-08-26
> **fela said:**
> No, because pidgin works just fine.

Why change what works, huh?

IRC just works, too, doesn't mean we shouldn't use other protocols.

I don't use Pidgin or Empathy. The things that annoy me about Pidgin are all in Empathy and then some. 

Pidgin is much more CURRENTLY extensible, too, and i think the usages of the end user should be thought of. It's all very well saying "well all they wanna do is chat!! EMPATHY!!", but i wanna use my cam, i want to be able to have a now-playing plugin, i want to do whatever it is i can do in the relevant windows programmes more or less. Pidgin can do more than Empathy ergo Pidgin wins.

---

### Post by coldReactive on 2009-08-26
> **fela said:**
> Does empathy?

I shouldn't even be in this thread really. I'm skipping 9.10, I'll install the 10.04 LTS straight when 10.10 comes out. Only after rigorous testing of course. I don't want, don't need, can't have a buggy system :)

I'm upgrading my netbook to 9.10 because apparently, kernel 2.6.29 has wifi working on the NB205 out of the box (still need to enable it via Windblows). I can't install kernels manually as I am welcomed by a blank screen upon boot.

---

### Post by Dullstar on 2009-08-26
Who wants to close a flamewar?  

Pidgin should stay.  Very n00b friendly UI, which is good.  Why is it that every good app in Ubuntu is being considered for replacement?  Including the DE?

People...  let's not replace Firefox, Pidgin, or GNOME.  I'd be indiffernet about the mail client because I never use mail clients.  You guys are trying to make me have to do some more package work.

Maybe the apps, but why should I have to use Synaptic (or whatever's there then) to get my preferred DE?  And do you guys have a big problem with the default apps?  Is it so difficult to just get them yourself instead of have all of us use the package manager to suit YOUR wishes?  I think if people wanted it to be changed it would have already been changed.

---

### Post by novafluxx on 2009-08-26
I like Pidgin because its going places, as the latest 2.6.x shows us, and also because I can use it on Windows too.

I keep Windows installed to play computer games, which Linux doesn't do well at all, with most of the games I want to play.

I enjoy having a familiar interface and stuff in both OS's

Now that we have a good PPA for Pidgin...its even better.

I think I'll be using it whether or not its the default in Karmic...

Which leads me to my main point...why change the default? Those that drool for Empathy can install it, its in the Repo's, they can get it and use it and have all their fun times with it...no ones stopping them.

---

### Post by Merk42 on 2009-08-26
> **Dullstar said:**
> Why is it that every good app in Ubuntu is being considered for replacement?  Including the DE?

When was there ever discussion about changing the DE?:confused:

---

### Post by Mr. Picklesworth on 2009-08-27
Here is another of those beautiful examples of what is so great about Telepathy (ergo Empathy) which I like to nudge around:
[http://www.lamalex.net/2009/08/dont-tie-your-tubes-telepathy-can-use-them-for-mega-fun/](http://www.lamalex.net/2009/08/dont-tie-your-tubes-telepathy-can-use-them-for-mega-fun/)

[IMG]http://www.lamalex.net/wp-content/uploads/2009/08/screenshot_010.png[/IMG]

Beat that, Pidgin buddy list! :P

We need a stronger platform to encourage rapid development of rich applications. This app was built in a very short time and is really quite impressive. (It's multiplayer, with a working buddy list, and it "just works").

With a richer platform, we get a strong base of independent software developers and an environment where all those small apps (free and otherwise) integrate smoothly and "just work". That is one of the ways Mac OS really leads right now. Clutter is a part of this puzzle, as well as Webkit, Dbus, Gconf and Glib. (Maybe Vala, if all goes well). Telepathy is another piece that, as you can see, provides possibilities we did not have before.


Having said this, I wouldn't panic if Empathy was delayed until next release. There are some really good points here to that end. At this immediate moment, the awesome new stuff using Telepathy will (with some exceptions) not be in 9.04. Maybe with Laughing Loon we'll be shipping Telepathic Sudoku and others, which would justify the change in a far more immediate fashion.
It will really be worth it, though, if the release team commits to that move early on and encourages developers to take advantage of it for 10.04. This has not happened for 9.10, so I agree, moving to Empathy serves little purpose with the archive as is.

Basically, I've had an epiphany: users shouldn't have to be caught in the cross-fire of an attempt to establish consensus around a piece of platform, no matter how cool, if this piece hinges on external apps using it. Announcing, documenting and reaching out to poke the actual things we need to make it happen softly is a far better approach :)

---

### Post by kestal on 2009-08-27
Personally, an ugly but powerful program is still an ugly program, by default. However, in this case in the game, I do not believe Empathy should be even considered to be default YET. 

There are other programs that that seem far further in their development. Hell, even aMSN is further (though a bit clunky).

Galaxium has a great feel (and abides by xmpp) and if more people help with that, that could be great.
Emesene 1.5 looks pretty decent from my point of view, many features work out of the box and it has a great feel to it.

The main side (and many people here agree too, and many general users who switch to ubuntu when Karmic hits will too), the default UI/icons/theme looks horrid. Something from the 90's. Its my one pet peeve with anything linux. (though, I admit, Ubuntu has been taking considerable leaps forward in this regard).

I mean, yes, there are themes... but why should the default theme be the ugly theme? even the contact list layout/icons are annoying.

---

### Post by Ronald Pottol on 2009-08-27
I'm poking around empathy, and while I can believe it is over all a win, I am with the camp that says no OTR, no go.

I don't need dancing emoticons, and while I do look forward to ineroperable video chat, without OTR, I will only use it when I need a feature like video chat, but I will stick with pidgin for day to day.

---

### Post by puccaso on 2009-09-03
[SIZE="6"][LIST]
[*]erm, ok
[*]so can empathy block yet!?

[*]the last time i checked, it wasnt implimented?
[/LIST][/SIZE]

---

### Post by steeleyuk on 2009-09-03
You'd have gotten a reply in the other thread if you'd had been patient. No, it can't block contacts yet.

---

### Post by qamelian on 2009-09-03
> **puccaso said:**
> [SIZE=6]
[LIST]
[*]erm, ok
[*]so can empathy block yet!?
[*]the last time i checked, it wasnt implimented?
[/LIST]
[/SIZE]

Nope, it is still missing that basic and, for me ,show-stopping feature. As long as it can't do this, in my opinion it has no business being the default IM client.

---

### Post by Seventh Reign on 2009-09-03
Neither Pidgin nor Empathy are really all that good frankly.  Both lack features (granted none of them are things I use, but from reading everyone elses comments).

If I could choose, I would choose neither .. and hope someone creates a new IM client that just 'works'.  Because right now .. neither of those 2 options does that.

---

### Post by steeleyuk on 2009-09-03
...or maybe just help improve Empathy.

---

### Post by qamelian on 2009-09-03
> **steeleyuk said:**
> ...or maybe just help improve Empathy.
Frankly, I get tired of hearing that mantra when Pidgin already does everything I need in an instant messenger and Empathy doesn't.

---

### Post by steeleyuk on 2009-09-03
> **qamelian said:**
> Frankly, I get tired of hearing that mantra when Pidgin already does everything I need in an instant messenger and Empathy doesn't.

Well don't use it then and stop whinging. You know as well as I do that Pidgin will be in the repositories for a long time to come. Empathy will improve over time (as has been said for about the 100th time), giving two solid options for IM clients. Thats a good thing...

---

### Post by dext on 2009-09-03
so is Empathy still the default in Karmic Alpha5?

---

### Post by fluffman86 on 2009-09-03
just checked ubuntu.com/testing.  Looks like it's still default.  :(

empathy is just so annoying. "hey, can I access your keyring?"
"hey, can I access your keyring?"
"hey, can I access your keyring?"
"hey, can I access your keyring?"
"hey, can I access your keyring?"
.
.
.
.
.
.
"hey, can I access your keyring?"

:'(

---

### Post by Merk42 on 2009-09-03
> **qamelian said:**
> Frankly, I get tired of hearing that mantra when Pidgin already does everything I need in an instant messenger and Empathy doesn't.

I think steeleyuk said that in response of Seventh Reign's 'suggestion' of a third not-yet-existing IM application.

---

### Post by qamelian on 2009-09-03
> **steeleyuk said:**
> Well don't use it then and stop whinging. You know as well as I do that Pidgin will be in the repositories for a long time to come. Empathy will improve over time (as has been said for about the 100th time), giving two solid options for IM clients. Thats a good thing...
Frankly, I also get tired of Empathy supporters accusing other users of "whinging" when we point out flaws in their baby. When Ubuntu was first launched, we were promised that the default install would include "best of breed" applications. Empathy is not yet a "best of breed" application and therefore contradicts that promise. It doesn't matter how you want to slice it, Empathy does not yet belong in the default install.

---

### Post by qamelian on 2009-09-03
> **Merk42 said:**
> I think steeleyuk said that in response of Seventh Reign's 'suggestion' of a third not-yet-existing IM application.
Possibly, but it's still tiresome. If Empathy offered all the features I rely on in Pidgin, I wouldn't care as much. The simple fact is that it doesn't and it's inclusion in the default install is premature.

---

### Post by fluffman86 on 2009-09-03
> **qamelian said:**
> Frankly, I also get tired of Empathy supporters accusing other users of "whinging" when we point out flaws in their baby. When Ubuntu was first launched, we were promised that the default install would include "best of breed" applications. Empathy is not yet a "best of breed" application and therefore contradicts that promise. It doesn't matter how you want to slice it, Empathy does not yet belong in the default install.

agreed.  I'm not hating on Empathy.  Looks like it will eventually be great. Lots of Gnome integration.  Awesome.  

But as it stands, Pidgin is currently the most mature, developed, and best all-around IM application.  Not to mention it's the least buggy, as well as cross-platform.

edit: I should hardly say "least buggy." But "less buggy than empathy" would probably be a better fit.  Then again, since when was *.10 release *NOT* buggy?  :P

---

### Post by castrojo on 2009-09-03
> **fluffman86 said:**
> 
empathy is just so annoying. "hey, can I access your keyring?"
"hey, can I access your keyring?"
"hey, can I access your keyring?"


I don't think this is empathy specific, on my laptop every app is asking me the same question. (Not happening on my desktop though)

---

### Post by fluffman86 on 2009-09-03
> **whiprush said:**
> I don't think this is empathy specific, on my laptop every app is asking me the same question. (Not happening on my desktop though)
"Hey, can I access your keyring?"
Yes, every app that uses a password needs to access a keyring. "Hey, can I access your keyring?"  That's OK.  "Hey, can I access your keyring?"  Except Empathy asks for EVERY ACCOUNT.  "Hey, can I access your keyring?"  And I have ELEVEN. "Hey, can I access your keyring?"
"Hey, can I access your keyring?"
That's annoying.
"Hey, can I access your keyring?"

---

### Post by 23meg on 2009-09-03
> **fluffman86 said:**
> "Hey, can I access your keyring?"
Yes, every app that uses a password needs to access a keyring. "Hey, can I access your keyring?"  That's OK.  "Hey, can I access your keyring?"  Except Empathy asks for EVERY ACCOUNT.  "Hey, can I access your keyring?"  And I have ELEVEN. "Hey, can I access your keyring?"
"Hey, can I access your keyring?"
That's annoying.
"Hey, can I access your keyring?"

Smells like a good bug report.

---

### Post by fluffman86 on 2009-09-03
> **23meg said:**
> Smells like a good bug report.
Already reported here:
[https://wiki.ubuntu.com/EmpathyVsPidginUsability](https://wiki.ubuntu.com/EmpathyVsPidginUsability)

"It's a feature, not a bug."  :P

---

### Post by 23meg on 2009-09-03
> **fluffman86 said:**
> Already reported here:
[https://wiki.ubuntu.com/EmpathyVsPidginUsability](https://wiki.ubuntu.com/EmpathyVsPidginUsability)

"It's a feature, not a bug."  :P

Reported? I don't see bug numbers for the keyring issues, but empty parantheses, which means mpt probably didn't get round to reporting them yet; you can go ahead and report them if they haven't been already.

---

### Post by castrojo on 2009-09-03
> **fluffman86 said:**
> "Hey, can I access your keyring?"
Yes, every app that uses a password needs to access a keyring. "Hey, can I access your keyring?"  That's OK.  "Hey, can I access your keyring?"  Except Empathy asks for EVERY ACCOUNT.  "Hey, can I access your keyring?"  And I have ELEVEN. "Hey, can I access your keyring?"
"Hey, can I access your keyring?"
That's annoying.
"Hey, can I access your keyring?"

If you don't want to be annoyed then don't run the development release, being a smart *** doesn't help fix the problem.

---

### Post by denver on 2009-09-03
> **fluffman86 said:**
> agreed.  I'm not hating on Empathy.  Looks like it will eventually be great. Lots of Gnome integration.  Awesome.  

But as it stands, Pidgin is currently the most mature, developed, and best all-around IM application.  Not to mention it's the least buggy, as well as cross-platform.

edit: I should hardly say "least buggy." But "less buggy than empathy" would probably be a better fit.  Then again, since when was *.10 release *NOT* buggy?  :P

+1 to that!

I also don't appreciate having something shoved down my throat as a default, just so it can get more attention from the community. Tried out Empathy for a few days, didn't like it. Found the UI to be less then intuitive. Had to search all the menus just to change my buddy icon. Also, i got used to the "Blink on new message" that pidgin does with its tray icon.

In any case, Empathy supporters have repeatedly stated that if you don't like the default Empathy you can always install pidgin from the repos. Well, that's a revolving door. If you don't like pidgin, you can always install empathy from the repos.

I have also seen arguments like "stop whining and help improve it". If the other team already has that...why spend more time reinventing the wheel. You already have a pretty good IM client available, why not improve that?

I hate having to upgrade to the next release of ubuntu (clean install) and go to add/remove instead of just using my system right away.

Pidgin has been in development for years and years and years. Would it not make more sense to direct efforts to an already mature platform rather then starting from scratch?

Tubes? great! Love the idea!(although it sounds like a German adult movie). Desktop sharing? Well, if it works with people using windows, then it's really useful! Let's face it, how many linux users do you have in your contact list? Many of us have few! Empathy has GREAT potential, and i am willing to switch to it when it reaches that potential (at least part of it), but not before. For now I am inclined to stick with what works, and whats useful.

just my 2 cents.

---

### Post by fluffman86 on 2009-09-03
> **whiprush said:**
> If you don't want to be annoyed then don't run the development release, being a smart *** doesn't help fix the problem.

I run the dev release to see what's new, see if my clients can upgrade later.  As it currently stands, yes, Karmic will be just fine.  But having empathy installed by default just gives me one more thing to do.  Whatever, it's not a big deal.

---

### Post by fluffman86 on 2009-09-03
Huh...just finished upgrading my laptop and it removed empathy without me asking.  weird...

did this happen to anyone else?

---

### Post by puccaso on 2009-09-04
i rememebr some years ago, when gaim-vv was out,
one of the gaim guys went to work with google..

now at that time, gaim-vv worked on yahoo and msn! 

but after the dude left the google compound, gaim-vv was stopped.. 

canonical seems to have a slight anti-pidgin thing going on,
it could be a google-chrome-os backup kinda thing?

empathy is not ready to be a default,
its plain and simple..

there MUST be something deeper in this, this is not just about usability but something political it seems.

otherwise, the ubuntu devs have never introduced something half complete..  apart from this current karmic flavour.. gdm is new, grub2 was new, they werent complete but they were topped off with some ubuntu-dev-love.. but empathy cant even BLOCK clients... i mean wtf. 


if they wanted to get something working
why not just take the A/V stuff from amsn and put it into pidgin, the AMSN guys have the source open for the taking, the new AMSN even uses farsight -- so its not impossible.. but this empathy push is something way to romantic.. 

the interface sucks, its too clumbsy, and like my friend, justatshirt says, "does it make toast?"

---

### Post by puccaso on 2009-09-04
> **fluffman86 said:**
> Huh...just finished upgrading my laptop and it removed empathy without me asking.  weird...

did this happen to anyone else?

yes
happend to me too

---

### Post by Katalog on 2009-09-04
> **fluffman86 said:**
> Huh...just finished upgrading my laptop and it removed empathy without me asking.  weird...

did this happen to anyone else?

> **puccaso said:**
> yes
happend to me too

Seriously? That's freaking strange. What's even stranger is I was installing Karmic Alpha 5 just now and they had a slide show during the installation with Pidigin on it (I apologize if someone already mentioned this), yet when I first fire up the desktop, there is still - Empathy. It was almost as sad as the misspellings in the slide show itself. :P

---

### Post by zipperback on 2009-09-04
Pidgin works and has an easy to understand interface.
I don't think empathy is ready for full deployment as the default yet.

- zipperback

---

### Post by 23meg on 2009-09-04
> **Katalog said:**
> Seriously? That's freaking strange.

Not strange at all that things get removed if you don't check what your package manager wants to remove and why before proceeding and blindly upgrade.

---

### Post by fluffman86 on 2009-09-04
[sudo apt-get dist-upgrade]
The following packages will be removed:
empathy, libempathy, libempathy-suchandsuch
The following packages will be upgraded:
[1000 packages]

It doesn't list a reason why it was removed.  It just did it.

So yeah, not strange that it didn't list a reason, just strange that it's gone and wasn't re-installed as a new version.

---

### Post by 23meg on 2009-09-04
Again, not strange at all. When testing development releases, it's up to you to check to see why a package is being removed; we have changelogs, the build queue, this forum etc. to help with that. If you dist-upgrade, APT will not care about missing dependencies (which is why it wants to remove Empathy); don't use it unless you know exactly why you want to.

---

### Post by coldReactive on 2009-09-04
> **23meg said:**
> Again, not strange at all. When testing development releases, it's up to you to check to see why a package is being removed; we have changelogs, the build queue, this forum etc. to help with that. If you dist-upgrade, APT will not care about missing dependencies (which is why it wants to remove Empathy); don't use it unless you know exactly what you want to.

And where would you find these changelogs for every little thing?

---

### Post by taavikko on 2009-09-04
> **coldReactive said:**
> And where would you find these changelogs for every little thing?

Subscribe to mailing list
[https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes)

ps. use digest for less posts.

---

### Post by 23meg on 2009-09-04
> **coldReactive said:**
> And where would you find these changelogs for every little thing?

"Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or [packages.ubuntu.com]("http://packages.ubuntu.com"), or.. there are many ways to retrieve them.

---

### Post by coldReactive on 2009-09-04
> **23meg said:**
> "Package > Download Dhangelog" in Synaptic, or "aptitude changelog package_name", or [packages.ubuntu.com]("http://packages.ubuntu.com"), or.. there are many ways to retrieve them.

I didn't know about the first two. Believe me or not.

---

### Post by kestal on 2009-09-04
Its been said before, but I will say so again. Empathy looks half-finished. I am sure its backend can be powerful or whatever, but an ugly/unfinished but powerful program is still an ugly and unfinished program.

Pidgin (even with its flaws) is more complete than Empathy. Hell, Galaxium is more complete, and its not even worked on as much. There are others too, even ones that follow xmpp standards.

Im sure there are supporters of Empathy that think its the greatest thing ever. Well, its not, and they are biased as they already support it. To thrust a program that doesn't look remotely like it should belong in this century, with the menu options comparible to the same time frame, should not be set to default as Ubuntu's messenger flavor of choice.

First impressions count, and Empathy doesn't "scream" visually pleasant, or intuitive/user-friendly/accessible.

---

### Post by drdabbles on 2009-09-04
No contact blocking, no blocking of those not on contact list, AIM messages don't seem to come through and when you send one Empathy crashes...lots of missing things like that.

So now I get spammed on my IM accounts in Empathy.

---

### Post by teddks on 2009-09-04
Okay, so here's a recap, just so that everyone in this thread at this point can be on the same page. I believe all these things to be facts, and will edit this post if any of them are not. 

[list]
[*] Empathy is the default IM application for 9.10 "Karmic Koala".
[*] Empathy cannot block contacts.
[*] Empathy does not have Off-the-Record functionality via libotr, or via any sort of compatibility layer with LibPurple plugins. This is a low-priority feature and one the Empathy developers seem hostile to implementing (see [http://bugs.freedesktop.org/show_bug.cgi?id=16891](http://bugs.freedesktop.org/show_bug.cgi?id=16891) for a great example of "cooperative upstream" in the form of "stop bitching"/"I don't see your patches"/"I'm not going to read your drivel").
[*] Empathy has stable support of **some** protocols in LibPurple. Notably, IRC and MSN are unstable, as well as AIM (some users have reported).
[*] Empathy has voice and video chatting over XMPP and SIP.
[*] Pidgin has voice and video chatting over XMPP.
[*] Empathy has no compatibility with LibPurple plugins.
[*] Empathy makes use of the Telepathy framework, and thus is a good thing because that framework could be very cool.
[*] Very little (possibly no) GNOME apps in Ubuntu use Telepathy.
[*] It is expected that if Empathy is added to Ubuntu, Ubuntu developers will commit their time to patching Empathy to improve it where it is sub-par. (Question: Has this ever been done?)
[/list]

Please correct me if I'm wrong. I only intend to make a set of facts clear to all those reading this thread at this point.

---

### Post by Bios Element on 2009-09-04
> **drdabbles said:**
> No contact blocking, no blocking of those not on contact list, AIM messages don't seem to come through and when you send one Empathy crashes...lots of missing things like that.

So now I get spammed on my IM accounts in Empathy.

AIM actually works for me, though I admit I only have a handful of contacts who use it. Contact Blocking is important though...

---

### Post by fluffman86 on 2009-09-04
> **teddks said:**
> [list][*] Empathy has stable support of all protocols in LibPurple, including MSN.
[*] Empathy has voice and video chatting over all protocols that support it.
[*] Pidgin has voice and video chatting over XMPP.[/list]
1. I cannot connect to MSN or IRC in empathy, at least out of the box.  I haven't tried downloading patches and extra libtelepathy stuff, but is doing so really an option for an average user...especially when all protocols work out of the box with Pidgin/libpurple?

2. Empathy has voice and video for XMPP/Google Talk and SIP.  This means Empathy can theoretically replace the SIP functionality of Ekiga (although I haven't tested this).  AIM, MSN, Yahoo!, and other IM voice and video are currently under development.

3. Pidgin has voice and video for XMPP from linux to linux *ONLY*.  Expect a patch to make this work "soon."  Voice and Video for other IM clients are under development.

So again, I have yet to see a compelling reason to include empathy as default other than the fact that it could possibly be really awesome sometime in the future.

---

### Post by Katalog on 2009-09-04
> **Katalog said:**
> Seriously? That's freaking strange.

> **23meg said:**
> Not strange at all that things get removed if you don't check what your package manager wants to remove and why before proceeding and blindly upgrade.

That's a given (not carefully checking over what Update Manager is asking for is simply bad form), and certainly not what I meant by that statement. I know you're trying to make a point, but there are probably more diplomatic ways of going about it than the sniping manner which you chose to use, and especially when directed at me in particular. Especially considering the fact that I was merely commenting on two other people's posts on the topic, _*the two people who actually ran the update and allowed Emapthy to be deleted*_. I didn't even start the conversation, so your target was a little misplaced to begin with, in addition to the fact that I personally did not run that specific update myself. All I did was comment on it, and yet I'm the one who get's hit with your "lesson". You could have at least quoted the entire conversation rather than singling me out so that I end up looking like a buffoon.

Anyway, what I meant, for clarity's sake so I don't get spanked again, was that it's strange that whoever was pushing the updates at Canonical saw the need to pull Empathy in the first place (and I would assume, perhaps foolishly, that most people who read my statement already understood that). :?

---

### Post by Paqman on 2009-09-04
> **fluffman86 said:**
> 1. I cannot connect to MSN or IRC in empathy, at least out of the box.  I haven't tried downloading patches and extra libtelepathy stuff, but is doing so really an option for an average user...especially when all protocols work out of the box with Pidgin/libpurple?


Installing telepathy-butterfly will sort that right out. My understanding is that there's some discussion amongst devs about whether to use [telepathy-butterfly or telepathy-haze]("http://telepathy.freedesktop.org/wiki/Haze%20vs%20Butterfly"). Once they've decided I presume one of them will indeed make it's way into the default install.

---

### Post by 23meg on 2009-09-04
> **Katalog said:**
> That's a given (not carefully checking over what Update Manager is asking for is simply bad form), and certainly not what I meant by that statement. I know you're trying to make a point, but there are probably more diplomatic ways of going about it than the sniping manner which you chose to use, and especially when directed at me in particular. Especially considering the fact that I was merely commenting on two other people's posts on the topic, _*the two people who actually ran the update and allowed Emapthy to be deleted*_. I didn't even start the conversation, so your target was a little misplaced to begin with, in addition to the fact that I personally did not run that specific update myself. All I did was comment on it, and yet I'm the one who get's hit with your "lesson". You could have at least quoted the entire conversation rather than singling me out so that I end up looking like a buffoon.

Anyway, what I meant, for clarity's sake so I don't get spanked again,


Sorry, I didn't intend to single you out or "snipe" on you or "spank" you; you seem to have inferred a bit too much from my tone and those words are very much out of place. I only intended to comment on why it's not "strange" that package managers may offer to remove things in the development branch, hence my quoting *your* statement.

> **Katalog said:**
>  was that it's strange that whoever was pushing the updates at Canonical saw the need to pull Empathy in the first place (and I would assume, perhaps foolishly, that most people who read my statement already understood that). :?

Nobody is actively "pulling" Empathy, which was my point; what happens is that the archive often goes into an inconsistent state due to missing dependencies in the development branch, and some operating modes of some package managers, which assume a consistent archive, will do "strange" things if you don't keep them in check, and that's up to you to do.

---

### Post by fluffman86 on 2009-09-04
> **23meg said:**
> Nobody is actively "pulling" Empathy, which was my point; what happens is that the archive often goes into an inconsistent state due to missing dependencies in the development branch, and some operating modes of some package managers, which assume a consistent archive, will do "strange" things if you don't keep them in check, and that's up to you to do.

Thank you for answering.  I do indeed know how to keep an eye on my package manager, but when running standard updates I tend to let it do what it wants so that if something breaks I'll know how to help other people.  Plus, nobody I've installed Ubuntu for would know what any of those packages are anyway.  I just tell them "When Ubuntu says you have updates, click Install and type your password."

---

### Post by kestal on 2009-09-04
> **teddks said:**
> Okay, so here's a recap, just so that everyone in this thread at this point can be on the same page. I believe all these things to be facts, and will edit this post if any of them are not. 

[list]
[*] Empathy is the default IM application for 9.10 "Karmic Koala".
[*] Empathy cannot block contacts.
[*] Empathy does not have Off-the-Record functionality via libotr, or via any sort of compatibility layer with LibPurple plugins. This is a low-priority feature and one the Empathy developers seem hostile to implementing (see [http://bugs.freedesktop.org/show_bug.cgi?id=16891](http://bugs.freedesktop.org/show_bug.cgi?id=16891) for a great example of "cooperative upstream" in the form of "stop bitching"/"I don't see your patches"/"I'm not going to read your drivel").
[*] Empathy has stable support of all protocols in LibPurple, including MSN.
[*] Empathy has voice and video chatting over all protocols that support it.
[*] Pidgin has voice and video chatting over XMPP.
[*] Empathy has no compatibility with LibPurple plugins.
[*] Empathy makes use of the Telepathy framework, and thus is a good thing because that framework could be very cool.
[*] Very little (possibly no) GNOME apps in Ubuntu use Telepathy.
[*] It is expected that if Empathy is added to Ubuntu, Ubuntu developers will commit their time to patching Empathy to improve it where it is sub-par. (Question: Has this ever been done?)
[/list]

Please correct me if I'm wrong. I only intend to make a set of facts clear to all those reading this thread at this point.

-It looks horrid and incomplete.
-Its menu structure is unintuitive/badly placed.
-General/Important options are missing, by far.
-The icons look like they belong in the 90's.
-The general user experience/accessibility options are nearly non-existent.
-The pleasantry of the overall feel is lackluster, empty, and shameful.

I mean.. I like to have at least some pride when I show off Ubuntu. This clearly does not make good first impressions.

---

### Post by Bios Element on 2009-09-04
> **kestal said:**
> -It looks horrid and incomplete.
-Its menu structure is unintuitive/badly placed.
-General/Important options are missing, by far.
-The icons look like they belong in the 90's.
-The general user experience/accessibility options are nearly non-existent.
-The pleasantry of the overall feel is lackluster, empty, and shameful.

I mean.. I like to have at least some pride when I show off Ubuntu. This clearly does not make good first impressions.

Funny, I think the same thing about Pidgin. >.> So I really don't think "style" should be considered at this point as it's very easy to change that. It's not so easy to change actual features.

---

### Post by kestal on 2009-09-04
> **Bios Element said:**
> Funny, I think the same thing about Pidgin. >.> So I really don't think "style" should be considered at this point as it's very easy to change that. It's not so easy to change actual features.

Did you see me mention pidgin in my list, at all? Design and Style should be considered. It sets the frame of mind and standards of quality when working around such features. Again, a powerful but ugly program will end up being just an ugly program, to most people.

I dislike the way Pidgin is set up, as well. However, even with that, its more 'complete' than Empathy, anyway.

Also, your side-stepping the point. The point is, even in comparison of the two, Empathy is far from what should be considered as a default messenger on any OS, including Ubuntu. Do not even try to talk about the fact that its 'easy to change'. Thats a BS excuse that is plaguing pretty hefty amount of applications on Ubuntu. Give it a better look and feel from the start rather than an icon which looks to be made in 5 minutes. OooOOoo. Green Circle panel icon. Good job on the design aspect of that. That must have taken weeks. (Sarcasm)

I understand programming/backend is important (duh). However, so is marketing the product. "The image". The overall feel. I mean, isn't that what Karmic is about? Its premature to have included this as default, or even a working messenger with all the bugs and lack of options/features. Even if it is a passive push to get programmers to take notice of it.

---

### Post by Katalog on 2009-09-05
> **23meg said:**
> Sorry, I didn't intend to single you out or "snipe" on you or "spank" you; you seem to have inferred a bit too much from my tone and those words are very much out of place. I only intended to comment on why it's not "strange" that package managers may offer to remove things in the development branch, hence my quoting *your* statement.

Thank you for clarifying that. But as we all know, intentions  don't always translate well in written form, which is why I as a manager for almost 26 years still prefer face to face meetings if at all possible rather than email communication. What really got my dander up was not so much the wording of your reply (it was actually a good reminder to always be aware of your environment and the things that may impact it), but the fact that my particular quote appeared as though it was being put forth as the impetus for that statement when I had indeed not even committed the mistake you were referring to. I may not have responded at all had it not been for that. Had you quoted someone who had actually let the application be deleted from their system in context along with my reply, I probably would have viewed your post in an entirely different light. It really is just that simple, and at the core of it all that is what I was really trying to convey with my response.

---

### Post by redenex on 2009-09-06
Having used Empathy for more than a week now, I vote NO. PidGin is still the choice.

---

### Post by abhishek.s on 2009-09-06
Whats missing??is like whats missing in Opera(distribution licensing overlooked) in comparison with Firefox?
my major issue with it is it doesn't saves the log in txt format and its ui ain't all that intutive(even pidgin has a long way to go but its still better).besides all the plugins i love will need to be rewritten or find some other app for it.

---

### Post by abhishek.s on 2009-09-06
> **meborc said:**
> sorry to raise hell :) but i don't agree... if you wanted to include gnome apps, we should all use epiphany and abiword instead of firefox and openoffice.org

pidgin just works and it is a GREAT experience for people new to linux... it has all you need from IM (no video of course)

empathy has still many bugs like the MSN chat not possible to open twice (as described before) which i can confirm...

why scratch if it does not itch?


I agree with you cent percent.

---

### Post by misfitpierce on 2009-09-06
Empathy is very good, the integration with the icons and such is alot better. I think Empathy for sure should be integrated!

---

### Post by stoffe on 2009-09-06
Just installed the latest Alpha, updated, set up an account in Empathy and now it simply instantly crashes and apport can't even extract a reason.

On one hand, it is alpha software and bugs/crashes are somewhat expected, but judging from the instant experience - Not Ready.

---

### Post by novafluxx on 2009-09-06
> **fluffman86 said:**
> So again, I have yet to see a compelling reason to include empathy as default other than the fact that it could possibly be really awesome sometime in the future.

My thoughts exactly, however, as long as I can remove Empathy and install Pidgin from the repos, I don't care...

I'm going to use what I want to use regardless

The issue at hand is really the NEW USER experience. What is best for them, as they won't be so ready to uninstall a package and install something to replace it right off the bat.

The questions is: Does Empathy deliver a better experience on the live disc/clean install, then Pidgin does?

---

### Post by qamelian on 2009-09-06
> **novafluxx said:**
> The questions is: Does Empathy deliver a better experience on the live disc/clean install, then Pidgin does?

Not as long as it lacks the ability to block unwanted contacts.

---

### Post by dext on 2009-09-06
> **stoffe said:**
> Just installed the latest Alpha, updated, set up an account in Empathy and now it simply instantly crashes and apport can't even extract a reason.

On one hand, it is alpha software and bugs/crashes are somewhat expected, but judging from the instant experience - Not Ready.
that dont surprise me its crashing a lot on you, as i used it in F12 snap1 an it crashed as soon as i went to Add a IRC account, tried to open it again but could only get it to open in root where it wanted me to fill in new accounts again. it just aint ready to be made Default, needs heaps of work done to it

---

### Post by kestal on 2009-09-06
Looking at the roadmap, I am sure that Empathy has potential.. however, I am still confused as to what advantages it currently has over Pidgin? (enough to replace it, of course). Perhaps I have overlooked something.

---

### Post by dext on 2009-09-06
> **kestal said:**
> Looking at the roadmap, I am sure that Empathy has potential.. however, I am still confused as to what advantages it currently has over Pidgin? (enough to replace it, of course). Perhaps I have overlooked something.

i dont think it has any or much advantages over pidgin at this time, only benefit i can see with Empathy is you can view users Locations , where as you cant with Pidgin but thats no real Great feature that i'd be so concerned at, i think the best thing with Empathy is it has Themes in it an can use Voice/Video but isnt that only on SIP? and Google Protocols

---

### Post by Katalog on 2009-09-06
> **meborc said:**
> sorry to raise hell :) but i don't agree... if you wanted to include gnome apps, we should all use epiphany and abiword instead of firefox and openoffice.org


> **super.rad said:**
> I would love ubuntu to use epiphany and abiword as default, imo both are much better apps and not resource hogs like openoffice and firefox, but don't think that's going to happen

Sorry to go somewhat off topic, but I basically agree with both these sentiments and honestly wish it were that simple, to just use nothing but GNOME apps. I'm a pretty much a GNOME fan, devoted Epiphany user, love Abiword and would like nothing better than to see a complete goffice suite. But in reality Gnumeric is continually lagging behind Excel and Calc, and the core of the GNOME Office Suite (which is pretty much a misnomer seeing how incomplete and incohesive the applications that make up the "suite" Abiword, Gnumeric, Evolution and Evince, are) is pretty weak in comparison to OOo. OOo Writer probably has better integration with Evolution than Abiword does, which is kinda sad. And they've allowed the only thing they had which resembled a presentation app, Agnubis, (and Criawips didn't get very far either, and if I were a programmer, trust me I'd be working on that rather than typing this post) lie fallow for over 7 years. I would enjoy nothing more than to be able to use a complete, highly compatible, fully GNOME office suite, but it just doesn't exist. And saying that it's not worth duplicating the effort because OOo already exists doesn't really hold up, because that hasn't slowed the KOffice developers down one bit.
Unfortunately, the state that GNOME Office is in seems to be similar to the problem with Empathy - it's just not ready for prime time. And until it is, I'll continue to use an app that does currently work without the need to be continually hobbled and retooled. Right now I get the impression that Empathy is being rushed, and that can't possibly be good for developers with a deadline breathing down their necks, which manifests itself as frustration for testers and end users as well. After bouncing back and forth a few times, ultimately, IMO, I believe they should retain Pidgin for now, take their time with Empathy so they can get it right, and then perhaps include it as default in 10.04.

Sorry for the long winded post. :-\"

---

### Post by misfitpierce on 2009-09-07
It does lack blocking of contacts and unable to turn off logging which I dont like to do so i'm not happy about that... I like the feel of it and everything but still sticking with pidgin until you can turn on or off logging and block contacts and also theme it for bit more customization alot easier than it is right now.

---

### Post by Joe_Bishop on 2009-09-07
Most clients can't turn off logging. It's a pidgin's pain it doesn't have logging enabled by default, and its logging feature is very poor comparing to empathy or gajim. I've never met a people who wanted logging off before. So, you are uniq.

---

### Post by ubuntu27 on 2009-09-07
Sorry for hijacking the thread.

Can somone help this person with his Empathy problems?

[http://ubuntuforums.org/showthread.php?t=1240674](http://ubuntuforums.org/showthread.php?t=1240674)



**********

I don't mind if empathy becomes default in Ubuntu. It is already good enough for chatting.

---

### Post by caraboy on 2009-09-07
Don`t like it, can`t even connect to yahoo protocol using alpha 5. Can someone tell me where am I supposed to enter my login data? I select yahoo and I see no place to input my username and password...

---

### Post by qamelian on 2009-09-07
> **Joe_Bishop said:**
> Most clients can't turn off logging. It's a pidgin's pain it doesn't have logging enabled by default, and its logging feature is very poor comparing to empathy or gajim. I've never met a people who wanted logging off before. So, you are uniq.

Not really. Outside the forums, none of the people I deal with in "real life" use logging in the IM. I certainly don't.

---

### Post by frustphil on 2009-09-07
> **caraboy said:**
> Don`t like it, can`t even connect to yahoo protocol using alpha 5. Can someone tell me where am I supposed to enter my login data? I select yahoo and I see no place to input my username and password...

I've been wondering how to do this too. Empathy is so POOR usability wise...

---

### Post by ugm6hr on 2009-09-07
> **qamelian said:**
> Not really. Outside the forums, none of the people I deal with in "real life" use logging in the IM. I certainly don't.

Indeed.  Everyone I IM with views IM like a phone conversation, or perhaps SMS chat.

Social, so records not required.  Would be weird if we used logging; akin to taping my phone conversations...

---

### Post by steeleyuk on 2009-09-07
Looks like a bug in the latest version with Yahoo, should be fixed soon.

---

### Post by Marat89 on 2009-09-07
My problem with Empathy: No File transfers with ICQ Protocol

Also dont like the UI, especially with the Icon Menu.!

---

### Post by Staz on 2009-09-07
> **meborc said:**
> empathy has still many bugs like the MSN chat not possible to open twice (as described before) which i can confirm...

Fixed that like 3 months ago, if you are going to compare please use recent version. And if it still happen with the latest version please reopen a bug.

---

### Post by Joe_Bishop on 2009-09-07
> Indeed. Everyone I IM with views IM like a phone conversation, or perhaps SMS chat.

Social, so records not required. Would be weird if we used logging; akin to taping my phone conversations...
it's because you don't have this feature on. I've noticed I'm widely using it.

---

### Post by Joe_Bishop on 2009-09-07
> Indeed. Everyone I IM with views IM like a phone conversation, or perhaps SMS chat.

Social, so records not required. Would be weird if we used logging; akin to taping my phone conversations...
it's because you don't have this feature on. I've noticed I'm widely using it.

---

### Post by qamelian on 2009-09-07
> **Joe_Bishop said:**
> it's because you don't have this feature on. I've noticed I'm widely using it.
Your assertion makes no sense. The reason we don't have the feature on is that we don't need or desire it. I used to turn logging on, but never over a two year period ever used the logs for anything. Never. So I turned the feature off. For me it is completely, undeniably, absolutely, 100% not needed. If you like to use it, knock yourself out. I don't have a single reason to care about logging my chats.

---

### Post by donniezazen on 2009-09-07
Hi,

This discussion may be redundant. So, Please forgive me. I am using karmic and saw that Pidgin has been replaced for Empathy. I have been using Pidgin for a long time. It is very stable and works in almost all conditions. Empathy is crashing like hell in karmic. I am not able to transfer files using Empathy. [B]Why Empathy has replaced when Pidgin introduced voice and video support and has robust file transfer protocol?
[/B]
Regards,
SK.

---

### Post by hanzomon4 on 2009-09-07
> **soham_1207 said:**
> Hi,

This discussion may be redundant. So, Please forgive me. I am using karmic and saw that Pidgin has been replaced for Empathy. I have been using Pidgin for a long time. It is very stable and works in almost all conditions. Empathy is crashing like hell in karmic. I am not able to transfer files using Empathy. [B]Why Empathy has replaced when Pidgin introduced voice and video support and has robust file transfer protocol?
[/B]
Regards,
SK.

Telepathy

---

### Post by coldReactive on 2009-09-07
> **hanzomon4 said:**
> Telepathy

Doesn't matter, if pidgin gets telepathy support: [http://developer.pidgin.im/wiki/Telepathy](http://developer.pidgin.im/wiki/Telepathy) then we can get Ubuntu to go back.

---

### Post by orlox on 2009-09-07
I also believe that empathy is half-complete, is not the best looking multiprotocol IM out there, and with certain protocols it can be a bit** (not that I notice it though, just heard it, cause with jabber and msn I have no connection issues)...

However, I think it's the correct decision. Empathy is meant to bring a lot of great stuff, maybe not today, nor tomorrow, but with the LTS release being so close, I think it's important to suffer a while and test-drive empathy. Cause I don't think that these features can magically come out polished for 10.04.

And, I wouldn't bet on pidgin having it's telepathy support anytime soon.

Besides, I use empathy with adium themes, and it doesn't look that horrid (ignoring the contact list that can't be themed, but I like it the way it is...)

---

### Post by Katalog on 2009-09-07
> **orlox said:**
> However, I think it's the correct decision. Empathy is meant to bring a lot of great stuff, maybe not today, nor tomorrow, but with the LTS release being so close, I think it's important to suffer a while and test-drive empathy. Cause I don't think that these features can magically come out polished for 10.04.

I completely agree that telepathy is a groundbreaking piece of technology which has great potential and will be absolutely awesome once it's finally been polished and tuned, but I still disagree with it being included as default just yet. If people want to test and report bugs to improve it, let that be their choice and provide incentive for those that do. But in the meantime, you need to give something to people who may be using Ubuntu for the first time something that is stable and reliable. First impressions are everything with most people, and I'm just afraid that going with Empathy at this point in time may not make a good impression. I strongly support Ubuntu and have genuine concern for it's progress and future growth, and would hate to see potential users walk away with a bad taste in their mouth simply because one of the most commonly used apps in any OS doesn't perform like they expect it to.

EDIT: This is just an afterthought, but I wanted to clarify that I didn't intend to imply that other people posting in this thread don't have concern for Ubuntu's future when I made the above post, and I apologize to anyone who reads that part before getting to this edit if it appeared that way.

---

### Post by fct on 2009-09-10
Heads up: MSN audio/video support landed in latest papyon (MSN telepathy backend) release:

[http://git.collabora.co.uk/?p=papyon.git;a=commitdiff;h=231683d4acfb5d4ac8b3403feb979cf2c4fcad4f](http://git.collabora.co.uk/?p=papyon.git;a=commitdiff;h=231683d4acfb5d4ac8b3403feb979cf2c4fcad4f)

Promising.

---

### Post by NCLI on 2009-09-10
Plenty of time for it to make it in before the freeze; great! :-D

---

### Post by fct on 2009-09-10
> **NCLI said:**
> Plenty of time for it to make it in before the freeze; great! :-D

I'm not sure that will be the case, it'd probably require changes in telepathy and empathy and the features are frozen because of the Gnome release schedule ([http://live.gnome.org/TwoPointTwentyseven](http://live.gnome.org/TwoPointTwentyseven)).

Still, this is quite good news.

---

### Post by orlox on 2009-09-10
This is amazing! Perhaps this can't make it to karmic, but surely they will add it in karmic +1. Apparently also, it works fine with msn live clients.

But, who knows...considering they got to discuss to revert the "empathy over pidgin" decision, perhaps they will be open to adding this feature.

However, as fct mentioned, karmic is tied to gnome 2.28, wich is at rc stage. But I think they would also be open to include something like this off-schedule.

---

### Post by coldReactive on 2009-09-10
Is that MSN audio/video thing for pidgin or empathy?

---

### Post by fct on 2009-09-10
> **coldReactive said:**
> Is that MSN audio/video thing for pidgin or empathy?

Empathy.

---

### Post by geojorg on 2009-09-10
Audio and Video on msn is only for Empathy, it uses telepathy-butterfly which now relies on papyon but I don't think it would make it for Karmic, maybe in a PPA.

---

### Post by orlox on 2009-09-10
Just updated my system, and python-papyon appeared as a new installation.

version number, 0.4.1, according to the post above papyon gets audio/video support for msn in 0.4.2

Edit: papyon 0.4.2 seems to have been released just 2 days ago:
[http://telepathy.freedesktop.org/releases/papyon/](http://telepathy.freedesktop.org/releases/papyon/)

Edit of the Edit: version 0.4.0 seems to mention webcam session support:
> papyon-0.4.0 (2009-07-02)
=========================

Enhancements:
  * Forked pymsn to create papyon
  * Added webcam sessions support

Fixes:
  * Fixed reception of P2P data from WLM 2009 users
What does that mean exactly??

---

### Post by madmetal on 2009-09-10
I am only using pidgin or previously gaim but i voted for empathy .

---

### Post by fct on 2009-09-10
> **orlox said:**
> Just updated my system, and python-papyon appeared as a new installation.

version number, 0.4.1, according to the post above papyon gets audio/video support for msn in 0.4.2

Edit: papyon 0.4.2 seems to have been released just 2 days ago:
[http://telepathy.freedesktop.org/releases/papyon/](http://telepathy.freedesktop.org/releases/papyon/)

Edit of the Edit: version 0.4.0 seems to mention webcam session support:

What does that mean exactly??

Webcam session probably means basic infrastructure for session support (request messages and so on), not that the video/audio was already working.

In the identi.ca (free alternative to Twitter) Empathy group you can see that the first message talking about developers using it is from two days ago:

[http://identi.ca/group/empathy](http://identi.ca/group/empathy)
[http://identi.ca/notice/9657064](http://identi.ca/notice/9657064)

---

### Post by rajeev1204 on 2009-09-10
I would like to see yahoo voice and video .In my country not many use msn ,we started with yahoo wayyyyyyyy back,many(read that 99 %) of our first emails were yahoo mail.So was the case with messenger.It was yahoo.

Gmail as we know is relatively new , back then it was hotmail or yahoo.

---

### Post by Katalog on 2009-09-11
I'm almost beginning to think that I may have underestimated the Empathy development community's ability to deliver in a timely manner. Development now appears to be moving at a breakneck pace, as opposed to what appeared to almost be a bit of regression and setback only a week or so ago. In any case, this has certainly been a bit of a bumpy ride for those currently using/testing Empathy. While I am going to continuie to use Pidgin for the time being (I have too much customization and time invested in my current setup to ditch it) and still have my doubts as to whether or not this will be able to make it into a near term relase, I certainly have to give credit where credit is due. Hat's off to the Empathy folks, as this is certainly a big step forward.

---

### Post by gnomeuser on 2009-09-11
> **Katalog said:**
> I'm almost beginning to think that I may have underestimated the Empathy development community's ability to deliver in a timely manner. Development now appears to be moving at a breakneck pace, as opposed to what appeared to almost be a bit of regression and setback only a week or so ago. In any case, this has certainly been a bit of a bumpy ride for those currently using/testing Empathy. While I am going to continuie to use Pidgin for the time being (I have too much customization and time invested in my current setup to ditch it) and still have my doubts as to whether or not this will be able to make it into a near term relase, I certainly have to give credit where credit is due. Hat's off to the Empathy folks, as this is certainly a big step forward.

I think the problem, when not looking at commit logs and mailing lists is that average users mainly think of features such as "msn webcam support". While this is a feature a number of very important infrastructure things need to be in place that aren't sexy at all. Since this doesn't have appeal bordering on "scantly clad Megan Fox" levels they are hard to get users excited about, never the less they are more important than from a technical stance than the end result.

So it does seem to many people that development is slow for a while then suddenly you get major features released followed by more silence. 

The more accurate metric for the projects ability to provide would be looking at the upstream bug report count and looking at the commits to git. If the bug count is fairly stable or decreasing you are in a solid place with regards to stability and fulfilling feature requests. A solid stream of git commits show good ongoing open development. Empathy, Telepathy and it dependencies generally have good curves, lots of well tested and documented code goes in, bugs go out and features requests are fulfilled.

---

### Post by frustphil on 2009-09-11
> **rajeev1204 said:**
> I would like to see yahoo voice and video .In my country not many use msn ,we started with yahoo wayyyyyyyy back,many(read that 99 %) of our first emails were yahoo mail.So was the case with messenger.It was yahoo.

Gmail as we know is relatively new , back then it was hotmail or yahoo.

+1
Most of us here use yahoo...

---

### Post by Amaranth on 2009-09-11
MSN audio/video support should make it into karmic assuming there is a telepathy-butterfly release for it soon. I must warn you that this is really new stuff that only started working a couple days ago and has not been extensively tested.

---

### Post by Stereotypical Rage on 2009-09-11
> **Amaranth said:**
> MSN audio/video support should make it into karmic assuming there is a telepathy-butterfly release for it soon. I must warn you that this is really new stuff that only started working a couple days ago and has not been extensively tested.
And this is EXACTLY why Empathy SHOULD NOT be the default IM client at this time. It's still too young,feature incomplete and lacks proper extensive testing. It shouldn't make it in Karmic+1(Should be an LTS), but rather Karmic+2. Hopefully at that time things can be more extensively tested and more empathy aware apps will come to market. I have this feeling after Karmic, Empathy Dev is going to slow way down.

---

### Post by Amaranth on 2009-09-11
Um, this is for a feature pidgin doesn't even have. I fail to see how it would be worse than pidgin in this regard.

---

### Post by zekopeko on 2009-09-11
> **Stereotypical Rage said:**
> And this is EXACTLY why Empathy SHOULD NOT be the default IM client at this time. It's still too young,feature incomplete and lacks proper extensive testing. It shouldn't make it in Karmic+1(Should be an LTS), but rather Karmic+2. Hopefully at that time things can be more extensively tested and more empathy aware apps will come to market. I have this feeling after Karmic, **Empathy Dev is going to slow way down**.

Not if it's in Karmic.
And there are a few apps that use telepathy tubes.
Tic-Tac-Toe from a Gnome-do dev and the awesome extension for Banshee that allows sharing one's library over the internet with your IM contacts.

---

### Post by coldReactive on 2009-09-11
I stopped caring about this issue when people began to widely support empathy in this thread. :| I'm still going with pidgin. Especially since empathy doesn't allow you to change the minimum height of the input box, doesn't have typing notifications, and doesn't allow you to remove incoming formatting on messages.

---

### Post by qamelian on 2009-09-11
> **Amaranth said:**
> Um, this is for a feature pidgin doesn't even have. I fail to see how it would be worse than pidgin in this regard.
At least Pidgin allows me to block unwanted contacts. Empathy only lets me ignore them until my next login. As long as I still need to have Pidgin installed to block contacts, Empathy is a useless waste of my time.

---

### Post by qamelian on 2009-09-11
> **zekopeko said:**
> Not if it's in Karmic.
And there are a few apps that use telepathy tubes.
Tic-Tac-Toe from a Gnome-do dev and the awesome extension for Banshee that allows sharing one's library over the internet with your IM contacts.
Neither of these is a feature that is compelling in an instant messenger client. The ability to block unwanted contacts is.

---

### Post by Staz on 2009-09-11
> **fct said:**
> I'm not sure that will be the case, it'd probably require changes in telepathy and empathy and the features are frozen because of the Gnome release schedule ([http://live.gnome.org/TwoPointTwentyseven](http://live.gnome.org/TwoPointTwentyseven)).

Still, this is quite good news.
papyon (which is a python msn lib) and telepathy-butterfly (which is the telepathy backend for MSN which use papyon) aren't affected by the Gnome freeze since they are backends. Empathy doesn't need any modification since it already has all the required support.

Ubuntu is already in feature freeze but we plan to ask for an exception since we really want this to be included in Karmic (and we think Ubuntu want it too so we expect to have the exception granted)

---

### Post by coldReactive on 2009-09-11
> **Staz said:**
> papyon (which is a python msn lib) and telepathy-butterfly (which is the telepathy backend for MSN which use papyon) aren't affected by the Gnome freeze since they are backends. Empathy doesn't need any modification since it already has all the required support.

Ubuntu is already in feature freeze but we plan to ask for an exception since we really want this to be included in Karmic (and we think Ubuntu want it too so we expect to have the exception granted)

Who's WE?

Not me.

---

### Post by Staz on 2009-09-11
> **coldReactive said:**
> Who's WE?

Not me.

We = the telepathy-butterfly developers

---

### Post by Staz on 2009-09-11
> **Stereotypical Rage said:**
> And this is EXACTLY why Empathy SHOULD NOT be the default IM client at this time. It's still too young,feature incomplete and lacks proper extensive testing. It shouldn't make it in Karmic+1(Should be an LTS), but rather Karmic+2. Hopefully at that time things can be more extensively tested and more empathy aware apps will come to market. I have this feeling after Karmic, Empathy Dev is going to slow way down.

but Pidgin having just released XMPP A/V support is fine?

edit : and I don't see what give you the feeling that after Karmic we are going to stop coding and rest.

---

### Post by coldReactive on 2009-09-11
> **Staz said:**
> but Pidgin having just released XMPP A/V support is fine?

edit : and I don't see what give you the feeling that after Karmic we are going to stop coding and rest.

The ubuntu packager might rest and not update the Pidgin ppa for ubuntu. This is what I'm afraid of.

---

### Post by orlox on 2009-09-11
> **coldReactive said:**
> The ubuntu packager might rest and not update the Pidgin ppa for ubuntu. This is what I'm afraid of.

As long as pidgin development goes on, I wouldn't worry. The pidgin-developers team at launchpad is formed by pidgin developers who use launchpad (emmm, that sounds stupid now that I think so...). Anyways, the point is the ppa is maintained by pidgin developers, not the ubuntu team. If you want an up to date pidgin, this will always be a better alternative than the frozen version that stable ubuntu releases hold.

[https://launchpad.net/~pidgin-developers](https://launchpad.net/~pidgin-developers)

---

### Post by coldReactive on 2009-09-11
> **orlox said:**
> As long as pidgin development goes on, I wouldn't worry. The pidgin-developers team at launchpad is formed by pidgin developers who use launchpad (emmm, that sounds stupid now that I think so...). Anyways, the point is the ppa is maintained by pidgin developers, not the ubuntu team. If you want an up to date pidgin, this will always be a better alternative than the frozen version that stable ubuntu releases hold.

[https://launchpad.net/~pidgin-developers](https://launchpad.net/~pidgin-developers)

But it looks like the PPA contains a different package. So if I add that PPA, my current pidgin packages won't be updated from the looks of it.

---

### Post by orlox on 2009-09-11
> **coldReactive said:**
> But it looks like the PPA contains a different package. So if I add that PPA, my current pidgin packages won't be updated from the looks of it.

Where did you got your packages from??

2.6.2 seems to have been released 3 days ago (or something like that), and the download option on the pidgin website points to the ppa. Perhaps they haven't packaged it properly yet, and the version from the ppa (2.6.1) is not horrendously dated...

---

### Post by meborc on 2009-09-11
> **orlox said:**
> Where did you got your packages from??

2.6.2 seems to have been released 3 days ago (or something like that), and the download option on the pidgin website points to the ppa. Perhaps they haven't packaged it properly yet, and the version from the ppa (2.6.1) is not horrendously dated...

he is most probably using getdeb (or some other) packages then... when using default packages, the upgrade to PPA is seamless

---

### Post by Staz on 2009-09-11
> **coldReactive said:**
> The ubuntu packager might rest and not update the Pidgin ppa for ubuntu. This is what I'm afraid of.

now I'm really confused by your response :confused:

---

### Post by muximus on 2009-09-11
does empathy support file transfer n voice/video over gtalk?

---

### Post by steeleyuk on 2009-09-11
Yes, its supported over Jabber.

---

### Post by Aries K on 2009-09-11
Staz, keep up the good work. It is finally good to have a  nice collaborative/integrated IM app that is starting to make it to the level of I-chat. :popcorn:

---

### Post by coldReactive on 2009-09-11
> **orlox said:**
> Where did you got your packages from??

2.6.2 seems to have been released 3 days ago (or something like that), and the download option on the pidgin website points to the ppa. Perhaps they haven't packaged it properly yet, and the version from the ppa (2.6.1) is not horrendously dated...

I got it from here: [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

Takes about 3 days after a release (on average) for it to get into update manager.

---

### Post by orlox on 2009-09-11
> **coldReactive said:**
> I got it from here: [http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

Takes about 3 days after a release (on average) for it to get into update manager.

The instructions contained there do nothing more than add the ppa I linked before to your sources.list.d...So, are you sure the version in the ppa is not yours??

---

### Post by Ratscallion on 2009-09-11
Might just be me, but I don't want to change. I like my Linux IM the way it is, and really couldn't care less if it's not installed by default, I'll just go for a sudo apt-get install pidgin. Though, yes, it [pidgin] does lack the things that aMSN has... :(

---

### Post by coldReactive on 2009-09-11
> **orlox said:**
> The instructions contained there do nothing more than add the ppa I linked before to your sources.list.d...So, are you sure the version in the ppa is not yours??

Right now it's 2.6.1, still waiting for 2.6.2

---

### Post by orlox on 2009-09-11
> **coldReactive said:**
> Right now it's 2.6.1, still waiting for 2.6.2

yes, but you mentioned you downloaded pidgin using the "download" page from the pidgin website, which only adds that ppa to your packages. If this is so, then you should have the version included in that ppa, I don't see how the version of the ppa could be lower than yours...unless you installed 2.6.2 from another source, or something fishy happened in the ppa and it went back a version (not very likely though...)

---

### Post by coldReactive on 2009-09-11
I haven't downloaded it actually, I use the PPA because I don't want to download anything, I want the PPA to update it through the update manager.

---

### Post by Katalog on 2009-09-11
> **meborc said:**
>  when using default packages, the upgrade to PPA is seamless

Exact amundo (to quote "The Fonz"). If you just stick to the default Pidgin that was pacakged with your current version of Ubuntu, add the Pidgin Developers PPA to your sources, then it will update to the latest version through the Update Manager just like any other app. Works like a charm for me.

---

### Post by Joe_Bishop on 2009-09-13
They couldn't even make file transfer through d'n'd. Huge amount of old bugs haven't fixed yet. I wish this client will never be default, because these guys are much better in talking than in coding. Latest incomprehensible UI changes reduced usability, voice chat doesn't work for many (I think, for most) users. But its devs only promise new features without fixing old bugs. Does canonical actually want to replace ugly and unusable, but stable pidgin with such a bugware?

---

### Post by 23meg on 2009-09-13
Merged with the existing thread.

---

### Post by Joe_Bishop on 2009-09-13
Oops, usual crash. Can't connect to ICQ account after it.
Lol, it was much more stable in 2.26.

---

### Post by Joe_Bishop on 2009-09-13
Oops, usual crash. Can't connect to ICQ account after it.
It was much more stable in 2.26. It could voice chat (but had sound issue, so I couldn't make out what did the caller say). Today it can't connect at all. And these crashes in 5 minute. I was empathy user since 2.26, but I'm looking for better client now because pidgin is unusable for me.

---

### Post by joey-elijah on 2009-09-13
I'm sure it's hidden deep within the 61 pages before this one, but it made me laugh how Emapthy comes as default - yet in Karmic 5 it's not integrated with the "session" applet.. pidgin still is though. Little lol's... small minds...

Although i was never a fan of Pidgin or empathy, i have to say that empathy has become my default client against all odds! I have really grown to love it! Simple, small and the conversation themes are pretty rad, too.

</pointless contribution to thread>

---

### Post by Longinus00 on 2009-09-13
> **joey-elijah said:**
> I'm sure it's hidden deep within the 61 pages before this one, but it made me laugh how Emapthy comes as default - yet in Karmic 5 it's not integrated with the "session" applet.. pidgin still is though. Little lol's... small minds...

Although i was never a fan of Pidgin or empathy, i have to say that empathy has become my default client against all odds! I have really grown to love it! Simple, small and the conversation themes are pretty rad, too.

</pointless contribution to thread>

What's odd is that empathy integrates fine with the session applet in jaunty.

---

### Post by hanzomon4 on 2009-09-13
What happened with yahoo... I can't enter my login information anywhere

---

### Post by novafluxx on 2009-09-13
> **Katalog said:**
> Exact amundo (to quote "The Fonz"). If you just stick to the default Pidgin that was pacakged with your current version of Ubuntu, add the Pidgin Developers PPA to your sources, then it will update to the latest version through the Update Manager just like any other app. Works like a charm for me.

Worked for me as well, and 2.6.2 is the version I've been running for days now.

---

### Post by Mr. Picklesworth on 2009-09-13
> **Longinus00 said:**
> What's odd is that empathy integrates fine with the session applet in jaunty.

And with the (better designed and better named...) upstream fast user switcher applet.

---

### Post by extremizt on 2009-09-14
> **rajeev1204 said:**
> Dont like empathy .The UI doenst make sense to me at all.Looks incomplete to me.
+1 It is not that stable as well.

---

### Post by zeroseven0183 on 2009-09-14
I've been using Pidgin since last year. Never had major problems. It's cute and still easy to use. I would still prefer Pidgin over Empathy.

---

### Post by Ratscallion on 2009-09-14
> **zeroseven0183 said:**
> I've been using Pidgin since last year. Never had major problems. It's cute and still easy to use. I would still prefer Pidgin over Empathy.


+1 highly agree.

---

### Post by trebach on 2009-09-14
I don't know if this is systemic, but Pidgin has quite a few memory leaks that make it explode after a few hours. However I still like it better than Empathy.

---

### Post by Stereotypical Rage on 2009-09-14
> **trebach said:**
> I don't know if this is systemic, but Pidgin has quite a few memory leaks that make it explode after a few hours. However I still like it better than Empathy.

Really? I've never noticed and the RAM consumed rarely goes over 200M for me and I have it running for weeks and months. I've had it hit 1.1G before but that was due to faulty plugins (Facebook + MSN Pecan).

---

### Post by gnomeuser on 2009-09-14
> **Amaranth said:**
> Um, this is for a feature pidgin doesn't even have. I fail to see how it would be worse than pidgin in this regard.

And now papyon 0.4.2 has:

* Added support for audio and video conferences

[http://lists.freedesktop.org/archives/telepathy/2009-September/003821.html](http://lists.freedesktop.org/archives/telepathy/2009-September/003821.html)

With that telepathy-butterfly needs to be updated but I believe such a release is coming "real soon"(tm) and has already been tested successfully by relevant developers.

It looks like we might be able to sneak this in as a freeze exception given the importance of the feature, provided naturally it is stable enough in the incarnation we get.

---

### Post by Podex on 2009-09-14
> **gnomeuser said:**
> It looks like we might be able to sneak this in as a freeze exception given the importance of the feature, provided naturally it is stable enough in the incarnation we get.

The bug report for this is here: [https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/428779](https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/428779)

edit: Or actually, that's only for papyon, the wishlist bug for telepathy-butterfly is here [https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/333675](https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/333675), but there is no activity there. 

I'm sure hoping to see video chat support in Empathy for Karmic, should be cool. But if its not ready yet for the masses they shouldn't include it.

---

### Post by Reiger on 2009-09-14
&#8220;[Eww]("https://bugs.launchpad.net/ubuntu/+source/papyon/+bug/428779/comments/4")&#8221; indeed. That embedded encryption instead of using a system library is setting a bad precedent there, which is something I definitely do not want to see in *any* I/M client (including those of my contacts...) much less the one I use.

---

### Post by Ratscallion on 2009-09-14
Is that a yes (or at least a soon) for webcams in Pidgin then?

---

### Post by gnomeuser on 2009-09-14
> **Ratscallion said:**
> Is that a yes (or at least a soon) for webcams in Pidgin then?

The protocol code is there in telepathy-butterfly and papyon for them to adopt, but given their decision to not reuse telepathy for their jabber webcam support I think they might also elect to rewrite this support.. aka waiting time

---

### Post by Ratscallion on 2009-09-14
I think I just about get it... So we wait, we get.

---

### Post by Podex on 2009-09-14
> **gnomeuser said:**
> The protocol code is there in telepathy-butterfly and papyon for them to adopt, but given their decision to not reuse telepathy for their jabber webcam support I think they might also elect to rewrite this support.. aka waiting time

I thought we were talking about Empathy here, not Pidgin. At least I was anyway. Pidgin's implementation of video/audio chat with MSN is a separate story... right?

---

### Post by bash on 2009-09-14
Here a blog posts from the devs about the MSN audio/video call feature (even including screenshots):

[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

---

### Post by nhasian on 2009-09-14
fantastic.  thats very exciting news.  MSN video conferencing AND file transfers in empathy.  I look forward to trying it out when it hits the repos.

---

### Post by orlox on 2009-09-14
> **nhasian said:**
> fantastic.  thats very exciting news.  MSN video conferencing AND file transfers in empathy.  I look forward to trying it out when it hits the repos.

AND offline messages. Next empathy update could be quite a substantial one...

---

### Post by coldReactive on 2009-09-14
> **orlox said:**
> AND offline messages. Next empathy update could be quite a substantial one...

I hope it allows you to block contacts, have password encryption (if not already), plugin manager, able to block incoming formatting, able to change the minimum chat input size, etc.

Oh wait, Pidgin already does that. :|

---

### Post by 243kof on 2009-09-14
I wish people stopped debating about this...

---

### Post by Tibuda on 2009-09-14
> **coldReactive said:**
> I hope it allows you to block contacts, **have password encryption** (if not already), plugin manager, able to block incoming formatting, able to change the minimum chat input size, etc.

Oh wait, Pidgin already does that. :|

Pidgin does not encrypt your password. Open ~/.purple/accounts.xml and see.

---

### Post by coldReactive on 2009-09-14
> **danielrmt said:**
> Pidgin does not encrypt your password. Open ~/.purple/accounts.xml and see.

I know, I wish pidgin did.

---

### Post by k33bz on 2009-09-14
I for one do not believe empathy is ready to be a default. Having empathy as a default in its current condition is not going to attract any new users to Linux or much less Ubuntu.  I was curious about what I heard of empathy as far as having video and audio chat support (was like damn, bout time this happens) However, after installing I am no where near pleased with empathy. Especially when Empathy will not let me log into my Yahoo accounts. I will stick with Pidgin for now.  Hopefully it will be in the Repo's still. Cause that is the very first thing I will do when I upgrade to 9.10, and that is if I upgrade, I may wait for the next LTS.

Maybe Empathy will be ready in the near future, but that time is not now.

---

### Post by Katalog on 2009-09-15
> **trebach said:**
> I don't know if this is systemic, but Pidgin has quite a few memory leaks that make it explode after a few hours. However I still like it better than Empathy.

> **Stereotypical Rage said:**
> Really? I've never noticed and the RAM consumed rarely goes over 200M for me and I have it running for weeks and months. I've had it hit 1.1G before but that was due to faulty plugins (Facebook + MSN Pecan).

Same here. I never really thought about it, because I have Pidgin running in he background with a boatload of plugins about 80% of the time, and I can't recall ever suffering any kind of significant performance hit when doing things like working in OOo, running Evolution, and playing music on my netbook at the same time. Even so, I'm going to keep an eye on it for a couple of hours just to see if can catch the memory leak you're referring to. Googling around I've found a few recent bugs referring to this type of thing on both Trac and Launchpad, most of which appear to have been fixed in the application itself. Are there any specific add-ons or plugins that you're aware of that cause this behavior? If so, I'd like to know so I can avoid them. I noticed a little lag on occasion when I was using Facebook plugin 1.60 and earlier, but I installed 1.61. recently and it seems to work much smoother than the previous versions.

---

### Post by Katalog on 2009-09-15
> **243kof said:**
> I wish people stopped debating about this...

Oh, it'll stop soon - in less than two months in fact, when 9.10 is released. Then there won't be anything left to debate. :P 

But seriously, I wish people would quit killing each other, Microsoft would go bankrupt and Social Security was solvent enough to support us all when we retire. But like the Rolling Stones said, you can't always get what you want. Besides, debate is healthy. How else do you expect issues to get resolved if people don't discuss them? It's a necessary evil/side effect of a community driven operating system.

---

### Post by meborc on 2009-09-15
^^ this thread will die when the development forums are closed down... when 9.10 releases... so no worries

but we can always pick it up again in 10.04 development talk :D

---

### Post by Ratscallion on 2009-09-15
> **meborc said:**
> ^^ this thread will die when the development forums are closed down... when 9.10 releases... so no worries

but we can always pick it up again in 10.04 development talk :D
But then it would need to be "Should pidgin replace Empathy as default IM client..."

---

### Post by hanzomon4 on 2009-09-15
Well libpurple is installed... hmm

---

### Post by Swarms on 2009-09-15
> **Katalog said:**
> Oh, it'll stop soon - in less than two months in fact, when 9.10 is released. Then there won't be anything left to debate. :P 

But seriously, I wish people would quit killing each other, Microsoft would go bankrupt and Social Security was solvent enough to support us all when we retire. But like the Rolling Stones said, you can't always get what you want. Besides, debate is healthy. How else do you expect issues to get resolved if people don't discuss them? It's a necessary evil/side effect of a community driven operating system.

It is not a debate if the two factions use the same 5 arguments every time. They do not seem to convince anyone.

I am still pro Empathy. The development has been moving so fast. Pidgin has only been trying to include Telepathy support and MSN video and voice because it have been removed from it's "throne" and the devs are squirming to make it return. What happens if they returned, would the good ol' slow pace return? :popcorn:

---

### Post by the.dark.lord on 2009-09-15
What the heck exactly are the advantages of Empathy over Pidgin - apart from it being the default GNOME IM ?

---

### Post by Swarms on 2009-09-15
> **the.dark.lord said:**
> What the heck exactly are the advantages of Empathy over Pidgin - apart from it being the default GNOME IM ?

It has been said several times, but Telepathy and more development progress.

---

### Post by meborc on 2009-09-15
> **Swarms said:**
> It has been said several times, but Telepathy and more development progress.

and if pidgin uses telepathy... then why do we need empathy?

---

### Post by the.dark.lord on 2009-09-15
> **Swarms said:**
> It has been said several times, but Telepathy and more development progress.

Now, why replace something which has future potential("more development progress") in place of something which is -as of now- more mature and polished?

A better alternative would be to stall replacing Pidgin till Empathy gets better.

---

### Post by Swarms on 2009-09-15
> **meborc said:**
> and if pidgin uses telepathy... then why do we need empathy?

> **the.dark.lord said:**
> Now, why replace something which has future potential("more development progress") in place of something which is -as of now- more mature and polished?

A better alternative would be to stall replacing Pidgin till Empathy gets better.

My reply is to the both of you.

Because development pace of Pidgin has only increased recently (due to developers realising their project is removed from default Ubuntu install).

Empathy has been moving very fast and as you can read, can almost offer video and voice conferencing with MSN. Something the Pidgin devs have been promising and delaying for years.

Both projects can soon be compared in specs, and then why wouldn't you want to bet on the fastest horse?

Plus, by having more testing the program, more people will bugreport, suggest features and more developers will work the projects. This will end with us having a very solid IM program which is tightly integrated with the desktop through telepathy (which Pidgin do not have yet). And through the Karmic release cycle, it will be even more solid and full of features ready for being included in the LTS that will follow.

---

### Post by qamelian on 2009-09-15
> **Swarms said:**
> My reply is to the both of you.

Because development pace of Pidgin has only increased recently (due to developers realising their project is removed from default Ubuntu install).

Empathy has been moving very fast and as you can read, can almost offer video and voice conferencing with MSN. Something the Pidgin devs have been promising and delaying for years.

Both projects can soon be compared in specs, and then why wouldn't you want to bet on the fastest horse?

Plus, by having more testing the program, more people will bugreport, suggest features and more developers will work the projects. This will end with us having a very solid IM program which is tightly integrated with the desktop through telepathy (which Pidgin do not have yet). And through the Karmic release cycle, it will be even more solid and full of features ready for being included in the LTS that will follow.
And I don't care about any of this. As long as Empathy doesn't allow me to block unwanted contacts, it's a useless piece of crap. Any IM that doesn't have this basic functionality has no business in the default install. Since I need to install Pidgin to be able to do this, Empathy is utterly, 100% useless to me.

---

### Post by 243kof on 2009-09-15
And you have said that exactly how many times already? You were heard the first time. This is why I wish the debate was over.. it has become an infinite loop. Nevertheless, I believe you have a valid point.

---

### Post by the.dark.lord on 2009-09-15
> **Swarms said:**
> 
Empathy has been moving very fast and as you can read, can almost offer video and voice conferencing with MSN. Something the Pidgin devs have been promising and delaying for years.


A good point, but it must be noted Pidgin recently added video support for XMPP; and more protocols are said to be coming soon.

> **Swarms said:**
> 
Both projects can soon be compared in specs, and then why wouldn't you want to bet on the fastest horse?

Plus, by having more testing the program, more people will bugreport, suggest features and more developers will work the projects. This will end with us having a very solid IM program which is tightly integrated with the desktop through telepathy (which Pidgin do not have yet). And through the Karmic release cycle, it will be even more solid and full of features ready for being included in the LTS that will follow.

I beg to differ. I want the best software available at the moment by default (if Empathy was better NOW, I'd be all for it!); those who want to test Empathy are free to do so by installing it manually. 

As for helping the development by increasing the user base, the same can be said of Pidgin. Why not fix Pidgin itself? Invalid argument.

---

### Post by Stereotypical Rage on 2009-09-15
> **Swarms said:**
> It has been said several times, but Telepathy and more development progress.
and who is to say Empathy won't slow down either? Dev was slow before this. Empathy has been default in GNOME since 2.24 which is just over a year now and only over say the last 3-6 months has dev picked up on the suite. Pidgin's been fairly regular over that same time.

 It was pretty much even more useless to a power user than it is now. It can't block contact or use encryption properly but yet it should be default because of voice and video? That doesn't make any sense. Add the standard options that pretty much all clients have and go from there.

---

### Post by Swarms on 2009-09-15
Too many replies, off to work in 5 min so can not reply to all of them.

> **the.dark.lord said:**
> A good point, but it must be noted Pidgin recently added video support for XMPP; and more protocols are said to be coming soon.

The Pidgin devs got all active suddenly when it was stated that Ubuntu would include Empathy instead. Just like Rythmbox has picked up it's pace when it was considered replacing it with Banshee. The development pace should be moving on its own. And not when they get frightened of exclusion.

> **the.dark.lord said:**
> 
I beg to differ. I want the best software available at the moment by default (if Empathy was better NOW, I'd be all for it!); those who want to test Empathy are free to do so by installing it manually. 

As for helping the development by increasing the user base, the same can be said of Pidgin. Why not fix Pidgin itself? Invalid argument.
Sometimes, you have to make a tough choice that will beenefit the users in the long run.

If we said: "Let's include Empathy in a couple of releases, so it can mature before it get's included. The development speed would not reach the same height as it is now, when it is destined to be released alongside Ubuntu.

So if people can live without encryption and being unanble to block contacts for a little while, we will have a solid IM built on a much better platform than Pidgin ever could be fixed into.

Kind of comparable why they are making the Ubuntu Software Store instead of fixing Synaptic.

---

### Post by meborc on 2009-09-15
> **Swarms said:**
> The Pidgin devs got all active suddenly when it was stated that Ubuntu would include Empathy instead. Just like Rythmbox has picked up it's pace when it was considered replacing it with Banshee. The development pace should be moving on its own. And not when they get frightened of exclusion.

ok... you are not making any sense... one of the biggest arguments why to include empathy by default was that then there will be more testers and developers and the speed of the development goes up

that means that we could include ANY IM by default and the development would go up

still i think all this empathy/telepathy business is a big piece of politics... and i don't like that the users were not asked before the switch

---

### Post by qamelian on 2009-09-15
> **the.dark.lord said:**
>  I beg to differ. I want the best software available at the moment by default (if Empathy was better NOW, I'd be all for it!); those who want to test Empathy are free to do so by installing it manually. 
Bingo. I want the default apps in any distribution I use to be the best for the job, in general. That means those apps need to have all the features that should be considered essential for that app to serve its purpose. At the moment, Empathy does not fit that description. When it does, I have no objection to it being the default IM client, but for now it absolutely does not belong in the default installation. When I no longer need to install Pidgin to get the functionality that Empathy fails to provide, I'll consider it a suitable replacement.

---

### Post by qamelian on 2009-09-15
> **meborc said:**
> ok... you are not making any sense... one of the biggest arguments why to include empathy by default was that then there will be more testers and developers and the speed of the development goes up

that means that we could include ANY IM by default and the development would go up

still i think all this empathy/telepathy business is a big piece of politics... and i don't like that the users were not asked before the switch
I have to agree with you.

Thus far, I've read in this and other threads that Empathy needs to be included by default to speed development and, conversely, that Pidgin development has been spurred on by being dropped as default. So which is it? Does being the default app boost development efforts or is dropping an app more likely to do so? I don't think, in this case, that it makes sense to argue both ways.

---

### Post by coldReactive on 2009-09-15
> **the.dark.lord said:**
> I beg to differ. I want the best software available at the moment by default (if Empathy was better NOW, I'd be all for it!); those who want to test Empathy are free to do so by installing it manually. 

As for helping the development by increasing the user base, the same can be said of Pidgin. Why not fix Pidgin itself? Invalid argument.

Bingo as well.

---

### Post by zekopeko on 2009-09-15
> **meborc said:**
> ok... you are not making any sense... one of the biggest arguments why to include empathy by default was that then there will be more testers and developers and the speed of the development goes up

that means that we could include ANY IM by default and the development would go up

still i think all this empathy/telepathy business is a big piece of politics... and i don't like that the users were not asked before the switch

Those arguments apply to all software. The main argument that I heard for Empathy is the better foundations it's built on. Telepathy is a powerful piece of software. You have to look beyond the UI at times to really see what is being offered.

And the thing about Pidgin devs is correct. The work for AV in Pidgin was completed in GSoC 2008 and it got merged only a year later.

---

### Post by zekopeko on 2009-09-15
> **qamelian said:**
> Bingo. I want the default apps in any distribution I use to be the best for the job, in general. That means those apps need to have all the features that should be considered essential for that app to serve its purpose. At the moment, Empathy does not fit that description. When it does, I have no objection to it being the default IM client, but for now it absolutely does not belong in the default installation. When I no longer need to install Pidgin to get the functionality that Empathy fails to provide, I'll consider it a suitable replacement.

Those are called regressions. And when you plan for them they are nothing to get all fluttered about.
OTR isn't something that most regular users need. AV is.

---

### Post by zekopeko on 2009-09-15
> **qamelian said:**
> I have to agree with you.

Thus far, I've read in this and other threads that Empathy needs to be included by default to speed development and, conversely, that Pidgin development has been spurred on by being dropped as default. So which is it? Does being the default app boost development efforts or is dropping an app more likely to do so? I don't think, in this case, that it makes sense to argue both ways.

Survival of the fittest. Pidgin dev had AV code in august 2008. They sit on it for a year and when their place as THE IM messenger in Linux is threatened they release Pidgin with AV support.

---

### Post by BCurtisWX on 2009-09-15
> **zekopeko said:**
> Survival of the fittest. Pidgin dev had AV code in august 2008. They sit on it for a year and when their place as THE IM messenger in Linux is threatened they release Pidgin with AV support.

Exactly why I don't support pidgin.  The devs will only include things as they see the need to put them in.  Empathy threatens them, so they've been popping out releases fast.

---

### Post by coldReactive on 2009-09-15
> **BCurtisWX said:**
> Exactly why I don't support pidgin.  The devs will only include things as they see the need to put them in.  Empathy threatens them, so they've been popping out releases fast.

And I won't support empathy until I get what I want. I'm no coder either, so I can't help them get blocking features, etc.

---

### Post by meborc on 2009-09-15
> **zekopeko said:**
> Those arguments apply to all software. The main argument that I heard for Empathy is the better foundations it's built on. Telepathy is a powerful piece of software. You have to look beyond the UI at times to really see what is being offered.

did i understand correctly, that pidgin can also use telepathy? if so, why do we need empathy again???

---

### Post by coldReactive on 2009-09-15
> **meborc said:**
> did i understand correctly, that pidgin can also use telepathy? if so, why do we need empathy again???

[http://developer.pidgin.im/wiki/Telepathy](http://developer.pidgin.im/wiki/Telepathy)

They're still working on it.

---

### Post by the.dark.lord on 2009-09-15
> **Swarms said:**
> Too many replies, off to work in 5 min so can not reply to all of them.


The Pidgin devs got all active suddenly when it was stated that Ubuntu would include Empathy instead. Just like Rythmbox has picked up it's pace when it was considered replacing it with Banshee. The development pace should be moving on its own. And not when they get frightened of exclusion.


Sometimes, you have to make a tough choice that will beenefit the users in the long run.

If we said: "Let's include Empathy in a couple of releases, so it can mature before it get's included. The development speed would not reach the same height as it is now, when it is destined to be released alongside Ubuntu.

So if people can live without encryption and being unanble to block contacts for a little while, we will have a solid IM built on a much better platform than Pidgin ever could be fixed into.

Kind of comparable why they are making the Ubuntu Software Store instead of fixing Synaptic.

This begs the question - why do it at all? Why not focus on developing Pidgin - which is currently better?

---

### Post by BCurtisWX on 2009-09-15
> **coldReactive said:**
> And I won't support empathy until I get what I want. I'm no coder either, so I can't help them get blocking features, etc.

Yeah, i get both sides of the argument.  I just don't mind empathy, it's not bothering me the way it is right now.  I hope that in the course of the next 6 months they can get A/V working on all IM clients supported (AIM/MSN/YAHOO etc..) to which I know they already have working.

---

### Post by qamelian on 2009-09-15
> **zekopeko said:**
> Those are called regressions. And when you plan for them they are nothing to get all fluttered about.
OTR isn't something that most regular users need. AV is.
It doesn't change the fact that I still need to install Pidgin and use it if I want to block an unwanted contact. If I have to install Pidgin anyway, and it's already my preferred IM client for a number of reasons, and Empathy offers not one compelling reason for me to prefer it. Certainly none of the reason thus far given concerning Telepathy matter to me. 

I also dispute the importance of AV. Out of over 230 people using various protocols on my contact list, I find that only 3 actually consider AV to be desireable. For most users that I know, basic features like blocking unwanted contacts is a necessity; AV is a luxury. Personally, I could care less about OTR, but for others including some of my client's, lack of it in Empathy is a showstopper. 

I agree that more users of Empathy is a good thing for testing and development, but I will never agree this this method of trying to achieve that. It flies in the face of Canonical's origanal stated goals of providing "best of breed" applications in the default install.

---

### Post by coldReactive on 2009-09-15
> **qamelian said:**
> AV is a luxury.

Exactly. Remember MSNM 4 or 5 on the MACOS? Those red colors always perked me up. :3

---

### Post by the.dark.lord on 2009-09-15
> **meborc said:**
> ... and i don't like that the users were not asked before the switch

+1

I would like to know who gets the final say in this. As can be seen from the poll, the majority does not support the replacement of Pidgin with Empathy.

---

### Post by coldReactive on 2009-09-15
> **the.dark.lord said:**
> +1

I would like to know who gets the final say in this. As can be seen from the poll, the majority does not support the replacement of Pidgin with Empathy.

+1 again. Seriously, who makes a change in the community's OS when the community doesn't--oh wait, most people don't like using mailing lists (such as me), I forgot.

---

### Post by zekopeko on 2009-09-15
> **the.dark.lord said:**
> +1

I would like to know who gets the final say in this. As can be seen from the poll, the majority does not support the replacement of Pidgin with Empathy.

The majority of 500 people who voted. Not a representative sample by any measure.

---

### Post by the.dark.lord on 2009-09-15
> **zekopeko said:**
> The majority of 500 people who voted. Not a representative sample by any measure.

What representative sample was taken while replacing Pidgin with Empathy?

---

### Post by zekopeko on 2009-09-15
> **coldReactive said:**
> +1 again. Seriously, who makes a change in the community's OS when the community doesn't--oh wait, most people don't like using mailing lists (such as me), I forgot.

You probably missed the whole meritocracy thing that Linux and FLOSS in general are built on.
And UF is a support forum. Not a development forum. LP and ml are the place to propose ideas.

---

### Post by zekopeko on 2009-09-15
> **the.dark.lord said:**
> What representative sample was taken while replacing Pidgin with Empathy?

The Ubuntu DEVELOPER community at UDS. And I don't see Ubuntu dev that weren't present at the UDS complaining about Empathy being included.

---

### Post by Merk42 on 2009-09-15
> **zekopeko said:**
> The Ubuntu DEVELOPER community at UDS. And I don't see Ubuntu dev that weren't present at the UDS complaining about Empathy being included.

Can this line be a sticky or something?
It, if you want to take it cynically, shows that Ubuntu is "for developers, by developers", not "for human beings". (I have said for coders, by coders, but I figured I'd use the exact work)

---

### Post by zekopeko on 2009-09-15
> **Merk42 said:**
> Can this line be a sticky or something?
It, if you want to take it cynically, shows that Ubuntu is "for developers, by developers", not "for human beings". (I have said for coders, by coders, but I figured I'd use the exact work)

Developers are people too ;)

---

### Post by the.dark.lord on 2009-09-15
> **zekopeko said:**
> The Ubuntu DEVELOPER community at UDS. And I don't see Ubuntu dev that weren't present at the UDS complaining about Empathy being included.

That is extremely biased. The majority of the users are not developers. I fail to see how it represents a representative sample of the community.

---

### Post by coldReactive on 2009-09-15
> **the.dark.lord said:**
> That is extremely biased. The majority of the users are not developers. I fail to see how it represents a representative sample of the community.

I actually think it's a bit even on both sides.

---

### Post by zekopeko on 2009-09-15
> **the.dark.lord said:**
> That is extremely biased. The majority of the users are not developers. I fail to see how it represents a representative sample of the community.

Just because you post in this forums, doesn't make you a part of the community. When were are talking about the Ubuntu community, that doesn't mean all the people using Ubuntu are part of the community.
The Ubuntu community consists of many different levels. On top are the developers. Bug reporters and translators etc. are a level(s) below but still important in the process.
And just because something is labeled as a community doesn't mean it's an anarchy. There are mechanism in place for changing things. Just because somebody posted a pool in an obscure part of the forum doesn't mean that the pool result should be taken at face value as you do it.

---

### Post by the.dark.lord on 2009-09-15
> **coldReactive said:**
> I actually think it's a bit even on both sides.

Even if that is true, it does not obscure the fact it is prejudiced.

---

### Post by the.dark.lord on 2009-09-15
> **zekopeko said:**
> Just because you post in this forums, doesn't make you a part of the community. When were are talking about the Ubuntu community, that doesn't mean all the people using Ubuntu are part of the community.
The Ubuntu community consists of many different levels. On top are the developers. Bug reporters and translators etc. are a level(s) below but still important in the process.
And just because something is labeled as a community doesn't mean it's an anarchy. There are mechanism in place for changing things. Just because somebody posted a pool in an obscure part of the forum doesn't mean that the pool result should be taken at face value as you do it.

Pardon me for being cynical, but that just reeks of "for developers, by developers".

Perhaps it's time we took another look at the hierarchy, giving more importance to the non-developers.

---

### Post by zekopeko on 2009-09-15
> **the.dark.lord said:**
> Even if that is true, it does not obscure the fact it is prejudiced.

Users and developers have different priorities IMO. Users want short term gratification. Developer have long term goals that will bring users their gratification. Most of the times the users can't see that. They only want their Pidgin while forgetting that having Empathy in is a long term goal for the platform.

---

### Post by coldReactive on 2009-09-15
> **zekopeko said:**
> Users and developers have different priorities IMO. Users want short term gratification. Developer have long term goals that will bring users their gratification. Most of the times the users can't see that. They only want their Pidgin while forgetting that having Empathy in is a long term goal for the platform.

When you put it that way, it makes sense. However, it still doesn't make people wait for results. People will always want what they want now, rather than later. Some just have more patience than others.

---

### Post by zekopeko on 2009-09-15
> **the.dark.lord said:**
> Pardon me for being cynical, but that just reeks of "for developers, by developers".

Perhaps it's time we took another look at the hierarchy, giving more importance to the non-developers.

Well you are painting yourself as a non-developer so please enlighten us to how will people without required skill sets help Ubuntu.

And to hammer a point: FLOSS isn't a democracy, it's a meritocracy. Google the difference.

---

### Post by gnomeuser on 2009-09-15
> **the.dark.lord said:**
> What representative sample was taken while replacing Pidgin with Empathy?

A technical one, the developers selected the most promising technology for where we are now and where we want to go. They go by things like how feature requests are handled, how dependable upstream is for bug handling. Any corporate backing is also helpful since that ensures that developers will be present and not affected by issues that otherwise take volunteers away from projects. Another important thing to consider, are the developers unapproachable arrogant bottom dwellers or are they easy to work with (hint: The pidgin team definitely does not fall in to the latter).

Here is your problem, you assume this is a democracy, it is not. It is a meritocracy, if you contribute you get to have a voice in the debate. You also seem to assume that technical merit has no value unless it falls into your narrow definition.

---

### Post by the.dark.lord on 2009-09-15
> **zekopeko said:**
> Well you are painting yourself as a non-developer so please enlighten us to how will people without required skill sets help Ubuntu.

And to hammer a point: FLOSS isn't a democracy, it's a meritocracy. Google the difference.

I indeed know the difference between democracy, and meritocracy - I'm doing sociology :). 

What I suggest is not that the non-developer be raised to the status of dev, but be given more of a say in the development of the OS.

---

### Post by zekopeko on 2009-09-15
> **coldReactive said:**
> When you put it that way, it makes sense. However, it still doesn't make people wait for results. People will always want what they want now, rather than later. Some just have more patience than others.

Well that is the whole point. Ubuntu devs don't want to have feature regressions when switching to Empathy. But the fact is that they are there and they have to be evaluated to see if they are showstoppers.
Tere are already applications popping up that use Telepathy.
Take into consideration that the next Ubuntu is a LTS release. That's a big deal for Ubuntu. You don't want core parts of the architecture being changed just before you release something that you have to support for 3/5 years.

---

### Post by gnomeuser on 2009-09-15
> **the.dark.lord said:**
> I indeed know the difference between democracy, and meritocracy - I'm doing sociology :). 


You may need to hit the books, I believe you are fundamentally confused as to how Open Source works.

> 
What I suggest is not that the non-developer be raised to the status of dev, but be given more of a say in the development of the OS.

"I want to decide but I don't want to lift a finger to make it happen".. that sounds an awful lot like arrogance. 

Remember contribution can be as simple as filing bugs and feature requests to highlight the areas where we currently regress. These will be valuable in determining if and when to switch defaults..

---

### Post by zekopeko on 2009-09-15
> **the.dark.lord said:**
> I indeed know the difference between democracy, and meritocracy - I'm doing sociology :). 

What I suggest is not that the non-developer be raised to the status of dev, but be given more of a say in the development of the OS.

I'm betting that if Empathy is included (final decision still hasn't been made) by the time of 10.04 people will hail Empathy as the best thing that has ever happened to Ubuntu. It's always like that once the long term goals of developers are converted into tangible user satisfaction.

---

### Post by the.dark.lord on 2009-09-15
> **gnomeuser said:**
> You may need to hit the books, I believe you are fundamentally confused as to how Open Source works.




Am I wrong in understanding that in OS hierarchy, a developer a MUCH higher status than the non-developer because he/she develops? Well, I do agree that the developers do know a lot more about the OS than the non-dev does, but this does not warrant entirely ignoring the opinion of the non-devs as was done in this case.


> **gnomeuser said:**
> 
"I want to decide but I don't want to lift a finger to make it happen".. that sounds an awful lot like arrogance. 

Remember contribution can be as simple as filing bugs and feature requests to highlight the areas where we currently regress. These will be valuable in determining if and when to switch defaults..

Arrogance? That sounds a lot like "if you want something done, go do it; or just shut up and let the developers decide." 

And, for your information, I do indeed file bugs when I encounter them - but that's beside the point.

---

### Post by the.dark.lord on 2009-09-15
> **zekopeko said:**
> I'm betting that if Empathy is included (final decision still hasn't been made) by the time of 10.04 people will hail Empathy as the best thing that has ever happened to Ubuntu. It's always like that once the long term goals of developers are converted into tangible user satisfaction.

That's what you think. According to the poll, a lot of people -non developers, at least- think otherwise.

---

### Post by LowSky on 2009-09-15
Anyone find it ironic that people are arguing on how the developers have more say than the end users. In the business world, where people pay for applications the end user is king. In the open source arena it the people who develop the application.

Anyway...

Why doesn't Ubuntu go to a pick your own poison at install type of measure.
Many users now complain of installing software they dont want or need, including pidgin, empathy, openoffice, transmission, and so on. For instance What developer thought it was a good idea to take away dial up support in 9.04, a good deal of end users complained on these forums. When it becomes a world where only the developer matter we end up with quirky menu they might only understand and use. It's why linux has a 1% OS share. Listen to the people who use your product and you get higher satisfaction in how it works.

---

### Post by fluffman86 on 2009-09-15
> **LowSky said:**
> Anyone find it ironic that people are arguing on how the developers have more say than the end users. In the business world, where people pay for applications the end user is king. In the open source arena it the people who develop the application.

No.  It's not ironic.  It's correct.  When you pay for something, whether that be with your time or your money, you decide how it works.  So if you pay some dude to develop an app for you, you can tell him how you want the software to work.  You are *NOT* paying for Ubuntu, the people who dedicate their time to working with and on applications are.

Which just gave me a great idea: create a voting system where interested users who don't/can't code or develop pay like $10 for each ubuntu release and get to vote and discuss what goes into the next one.  The final release is still free for all to use.  :)

And I'm getting tired of this pidgin vs. empathy debate.  How about we start discussing getting rid of rhythmbox and replacing it with Banshee? :P  No really though.  I think Ubuntu should support the best applications available.  Right now, that's Pidgin, Firefox, VLC or Mplayer, and Banshee, amirite?  I don't want just another Gnome distro with Epiphany, Totem, and Rhythmbox just because they're there.

---

### Post by Ratscallion on 2009-09-15
Going off topic, I'm fine with Rhythmbox... Does Banshee have Crossfading tools and last.fm support? If not, then it's Rhythmbox all the way... Just change the name to something we can all spell... :P

---

### Post by the.dark.lord on 2009-09-15
> **fluffman86 said:**
> No.  It's not ironic.  It's correct.  When you pay for something, whether that be with your time or your money, you decide how it works.  So if you pay some dude to develop an app for you, you can tell him how you want the software to work.  You are *NOT* paying for Ubuntu, the people who dedicate their time to working with and on applications are.

Which just gave me a great idea: create a voting system where interested users who don't/can't code or develop pay like $10 for each ubuntu release and get to vote and discuss what goes into the next one.  The final release is still free for all to use.  :)

And I'm getting tired of this pidgin vs. empathy debate.  How about we start discussing getting rid of rhythmbox and replacing it with Banshee? :P  No really though.  I think Ubuntu should support the best applications available.  Right now, that's Pidgin, Firefox, VLC or Mplayer, and Banshee, amirite?  I don't want just another Gnome distro with Epiphany, Totem, and Rhythmbox just because they're there.

In short: "for developers, by developers". End users just need to accept what the devs shove down their throat(by default, at least!).

And I used to wonder why Linux still had 1% market share.

P.S.: I love and admire you devs for your work, but the end-user NEEDS to be represented too.

---

### Post by fluffman86 on 2009-09-15
> **Ratscallion said:**
> Does Banshee have Crossfading tools and last.fm support? 

yes to last.fm.  I don't think it has crossfading yet, though. :(

@the.dark.lord: Why not pay someone to use remastersys and create iso's for you then?  It's actually pretty easy to have your own Ubuntu-based distro.

---

### Post by the.dark.lord on 2009-09-15
> **fluffman86 said:**
> 
@the.dark.lord: Why not pay someone to use remastersys and create iso's for you then?  It's actually pretty easy to have your own Ubuntu-based distro.

That is beside the point. And it is exactly this kind of mentality hampering most open source projects.

---

### Post by fct on 2009-09-15
> **the.dark.lord said:**
> That is beside the point. And it is exactly this kind of mentality hampering most open source projects.

If you hate that mentality, I don't understand why you want to use pidgin. Their developers have been putting themselves before users' needs for as long as I've been following the project.

---

### Post by the.dark.lord on 2009-09-15
> **fct said:**
> If you hate that mentality, I don't understand why you want to use pidgin. Their developers have been putting themselves before users' needs for as long as I've been following the project.

They have, indeed? I have no personal experience with the Pidgin devs.

As for why I want to use Pidgin: it is currently more mature and polished than Empathy.

---

### Post by fct on 2009-09-15
> **the.dark.lord said:**
> They have, indeed? I have no personal experience with the Pidgin devs.

As for why I want to use Pidgin: it is currently more mature and polished than Empathy.

Yeah, the project has been alive since it was called gaim so it's natural that it's mature and polished.

Just to give you an idea of the age of the project, the first patch to add a/v capabilities to gaim is from 2005:

[http://gaim-vv.sourceforge.net/](http://gaim-vv.sourceforge.net/)

---

### Post by fluffman86 on 2009-09-15
> **fct said:**
> If you hate that mentality, I don't understand why you want to use pidgin. Their developers have been putting themselves before users' needs for as long as I've been following the project.

Yeah, so true.  I've been using pidgin for 4 years now, since pre-1.0.  I would read the forums a good bit, and normal users would help out where possible, and inevitably a dev would get on there and say, "Well, this is the way I like it.  If you can write it better and if I decide that it's ok to go into the build, then maybe I'll include a patch from you."

---

### Post by gnomeuser on 2009-09-15
> **LowSky said:**
> 
Why doesn't Ubuntu go to a pick your own poison at install type of measure.


How would the user decide.. Applications don't universally import each others data correctly (Banshee does it correctly e.g. but Rhythmbox does not). So if the user decides to try every app to determine the best one he can't migrate his data.. this makes users sad. Aside that we pick defaults for a reason. 

A default application is something we feel comfortable supporting, something we can support. Adding say 6 choices for every application adds a considerable burden for support and developers. It simply not tenable for a distribution to fully support every application in the repo to it's fullest extend. 

Finally leaving it as a choice is a cop-out, the whole point of a distribution is to present a best of breed set of applications  for a given use case. 

It also serves to provide a remarkably poorer experience to continually present the user with choices and options. We should aim for good defaults that seek to fulfill the greatest common benefactor. 

[an interesting read on the subject of choice](http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html)

Mandatory choice is the road to retardation.

---

### Post by CoolHand on 2009-09-15
I vote no.  Keep Pidgin until the other is demonstrably better.  I installed it and tried it for a while just to see and I see no improvement over Pidgin and many lacking UI features.  If the features are there then they are not intuitive.  For instance in Empathy how do I set my fonts or colors?  How do I get Empathy to remember its window position when I minimize it to the system tray?  How do I turn on or off logging of my message history?  Here is one I saw right away...when connecting multiple accounts if one account doesn't connect how can I tell which one?  All I saw was a spinning icon and I had to disable the accounts one at a time to figure out which one was hung.

I'm staying with Pidgin until Empathy is better at the little things.  They may succeed in getting it made default but that won't make me use it.

---

### Post by fluffman86 on 2009-09-15
Good point, gnomeuser.  It's important to remember that Ubuntu exists as a for-profit product by canonical, who sells support to corporate clients.  They can't possibly support thousands of possible app combos on a daily basis.

---

### Post by the.dark.lord on 2009-09-15
> **fct said:**
> Yeah, the project has been alive since it was called gaim so it's natural that it's mature and polished.

Just to give you an idea of the age of the project, the first patch to add a/v capabilities to gaim is from 2005:

[http://gaim-vv.sourceforge.net/](http://gaim-vv.sourceforge.net/)

I've used it when it was called gaim. Anyway, more reason to keep Pidgin; or at least stall Empathy inclusion by default.

---

### Post by the.dark.lord on 2009-09-15
> **gnomeuser said:**
> How would the user decide.. Applications don't universally import each others data correctly (Banshee does it correctly e.g. but Rhythmbox does not). So if the user decides to try every app to determine the best one he can't migrate his data.. this makes users sad. Aside that we pick defaults for a reason. 

A default application is something we feel comfortable supporting, something we can support. Adding say 6 choices for every application adds a considerable burden for support and developers. It simply not tenable for a distribution to fully support every application in the repo to it's fullest extend. 

Finally leaving it as a choice is a cop-out, the whole point of a distribution is to present a best of breed set of applications  for a given use case. 

It also serves to provide a remarkably poorer experience to continually present the user with choices and options. We should aim for good defaults that seek to fulfill the greatest common benefactor. 

[an interesting read on the subject of choice](http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html)

Mandatory choice is the road to retardation.

You are missing the point. What I proposed was not we included all the random apps we can think up, so that the end-user will have a choice. 

What I said was while editing/changing default apps, the community (at least, those in these forum) be given a chance to have their say.

---

### Post by the.dark.lord on 2009-09-15
> **fluffman86 said:**
> Yeah, so true.  I've been using pidgin for 4 years now, since pre-1.0.  I would read the forums a good bit, and normal users would help out where possible, and inevitably a dev would get on there and say, "Well, this is the way I like it.  If you can write it better and if I decide that it's ok to go into the build, then maybe I'll include a patch from you."

Well, how does it differ from what I'm going through right now?

---

### Post by fluffman86 on 2009-09-15
> **the.dark.lord said:**
> Well, how does it differ from what I'm going through right now?

It doesn't.  I'm just saying it doesn't really make it *wrong*.  Although I understand it's annoying.

---

### Post by fct on 2009-09-15
> **the.dark.lord said:**
> Well, how does it differ from what I'm going through right now?

Empathy developers haven't said that they won't implement blocking cause they aren't interested in MSN, neither ignored correct patches that add that feature. In fact, you can expect those features to go in without bickering, forking threats and so on while current versions get tested to hell.

In the meanwhile, you can install pidgin and override the default, leaving it exactly as it was before. That's the immediate difference. ;)

---

### Post by coldReactive on 2009-09-15
> **fct said:**
> In the meanwhile, you can install pidgin and override the default, leaving it exactly as it was before. That's the immediate difference. ;)

I'm glad karmic is publishing Pidgin 2.6.x though, meaning users can get 2.6.x when they have Ubuntu 9.10.

---

### Post by Ratscallion on 2009-09-15
2.6 is out???!!

---

### Post by motang on 2009-09-15
Going to be using Pidgin, even after Karmic's release.

---

### Post by tehk on 2009-09-15
if gmail ever gets the feature to popout new IM's by default... goodbye Instant Messaging apps!

---

### Post by coldReactive on 2009-09-15
> **Ratscallion said:**
> 2.6 is out???!!

I've been using it for a while now. Oh wait, 2.6 is only applicable to Jaunty and above, as Audio/Video support is not supported in previous versions.

---

### Post by gnomeuser on 2009-09-15
> **tehk said:**
> if gmail ever gets the feature to popout new IM's by default... goodbye Instant Messaging apps!

I think you can expect this along with Googles ChromeOS efforts.

---

### Post by Ratscallion on 2009-09-15
> **gnomeuser said:**
> I think you can expect this along with Googles ChromeOS efforts.
Chrome OS will probably make a standalone app for Google talk/GMail IMs

---

### Post by coldReactive on 2009-09-15
> **Ratscallion said:**
> Chrome OS will probably make a standalone app for Google talk/GMail IMs

No, because Chrome OS is built on web-based apps.

---

### Post by Ratscallion on 2009-09-15
(Going off topic I know...)
I know, but web based != several instances of Chrome for each app.. 

For example, if we were to have a desktop icon of GTalk, GMail and, say, GDocs.
Open each of them, and we get a window of Chrome with the GTalk page, then another one a GMail page, a GDocs and so on.

---

### Post by coldReactive on 2009-09-15
> **Ratscallion said:**
> (Going off topic I know...)
I know, but web based != several instances of Chrome for each app.. 

For example, if we were to have a desktop icon of GTalk, GMail and, say, GDocs.
Open each of them, and we get a window of Chrome with the GTalk page, then another one a GMail page, a GDocs and so on.

That's why there's Prism, which is already available for Linux.

---

### Post by zoomy942 on 2009-09-15
for me, empathy is okay, but no facebook connect (for my brothers and sisters) and i have constant problems adding people to MSN through it.  it's a pain when i simply need an IM client that works.  sure, pidgin doesnt have video and voice, but i dont use those, so those arent relevant to me.

however, whether it should be defualt or not - I vote for simply an IM client i dont have to worry about.

---

### Post by Stereotypical Rage on 2009-09-15
> **zoomy942 said:**
> for me, empathy is okay, but no facebook connect (for my brothers and sisters) and i have constant problems adding people to MSN through it.  it's a pain when i simply need an IM client that works.  sure, pidgin doesnt have video and voice, but i dont use those, so those arent relevant to me.

however, whether it should be defualt or not - I vote for simply an IM client i dont have to worry about.

Let's not forget one thing... Pidgin is cross-platform. Firefox/Thunderbird are cross-platform. OpenOffice is cross-platform. Empathy is not cross-platform friendly at this time. If we really expect a major following, wouldn't it be wiser to make the transition as easy as possible? Instead of re-inventing the wheel, why not fix/improve what we have?

:popcorn:

---

### Post by Merk42 on 2009-09-15
> **Stereotypical Rage said:**
> wouldn't it be wiser to make the transition as easy as possible? Instead of re-inventing the wheel, why not fix/improve what we have?

:popcorn:

...because arguably we **couldn't** fix what we had.  The Pidgin devs are/were notorious for not listening to input. The webcam feature alone has been a request for YEARS and it does seem a bit coincidental it only gets applied after it is possibly dropped from Ubuntu's default.

---

### Post by Stereotypical Rage on 2009-09-15
> **Merk42 said:**
> ...because arguably we **couldn't** fix what we had.  The Pidgin devs are/were notorious for not listening to input. The webcam feature alone has been a request for YEARS and it does seem a bit coincidental it only gets applied after it is possibly dropped from Ubuntu's default.

Is it really that much of a priority? Just because "a few" want the change, doesn't mean it is good for all.

I don't know how so few of my thousands of contacts DON'T use silly webcam support. It's a Luxury. I'd rather have CVEs fixed over Voice and Video support.

Empathy is pretty pathetic in it's current state(not to mention it relies on Pidgin in some areas!). It's like driving a Pinto vs driving the Delorian.

---

### Post by 23meg on 2009-09-15
> **Merk42 said:**
> Can this line be a sticky or something?
It, if you want to take it cynically, shows that Ubuntu is "for developers, by developers", not "for human beings". (I have said for coders, by coders, but I figured I'd use the exact work)

And you *always* want to take it cynically, don't you? 

If it was "for developers, by developers", you would have a terminal IRC client in place of a graphical instant messaging application, and this thread would have been titled "Is [irssi]("http://irssi.org/") ready to replace [finch]("http://developer.pidgin.im/wiki/Using%20Finch")?". End of story.

---

### Post by hanzomon4 on 2009-09-15
Come on let's not be so sore.. free hugs

:popcorn:

---

### Post by zekopeko on 2009-09-15
> **Stereotypical Rage said:**
> Let's not forget one thing... Pidgin is cross-platform. Firefox/Thunderbird are cross-platform. OpenOffice is cross-platform. Empathy is not cross-platform friendly at this time. If we really expect a major following, wouldn't it be wiser to make the transition as easy as possible? Instead of re-inventing the wheel, why not fix/improve what we have?

:popcorn:

Let's see: Empathy devs are actually listening to input from Ubuntu devs.
Nothing is stopping you from using Pidgin in Windows. Or MSN Live Messenger or Yahoo! Messenger etc. What is stopping people from using Ubuntu is the lack of AV support.
Empathy pretty much fixes that. You will note that Ekiga is planned to be replaced with Empathy. So you have all of your contacts in one place, accessible to the rest of desktop applications.

---

### Post by 23meg on 2009-09-15
> **the.dark.lord said:**
> In short: "for developers, by developers". End users just need to accept what the devs shove down their throat(by default, at least!).

And I used to wonder why Linux still had 1% market share.

And Microsoft Windows, which is proprietary, closed-source, ships with hard-wired default applications that the end user cannot replace *at all* (such as IE), doesn't have development and governance structures that give the end user any way to be involved in its development *at all*, has a 95% market share.

> **the.dark.lord said:**
> P.S.: I love and admire you devs for your work, but the end-user NEEDS to be represented too.

[The Messaging/Video Conferencing/VOIP selection blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-messaging-and-communication-selection") includes among its list of work items:

> look at feedback from users at feature freeze and decide what to use for karmic: DONE

Which means, feedback (mainly from bug reports) was incorporated into the decision-making process. That means the end user who contributed to the process through filing bug reports *was* represented.

---

### Post by zekopeko on 2009-09-15
> **Stereotypical Rage said:**
> Is it really that much of a priority? Just because "a few" want the change, doesn't mean it is good for all.

I don't know how so few of my thousands of contacts DON'T use silly webcam support. It's a Luxury. I'd rather have CVEs fixed over Voice and Video support.

Empathy is pretty pathetic in it's current state(not to mention it relies on Pidgin in some areas!). It's like driving a Pinto vs driving the Delorian.

So let me get this straight: You are saying that one FLOSS project using code from another FLOSS project is a bad thing?

---

### Post by coldReactive on 2009-09-15
> **zekopeko said:**
> So let me get this straight: You are saying that one FLOSS project using code from another FLOSS project is a bad thing?

I don't think so, as ReactOS uses code from WINE, and vice versa at times.

---

### Post by Merk42 on 2009-09-15
Stereotypical Rage I was only using webcam support as an example.

> **23meg said:**
> And you *always* want to take it cynically, don't you? 
Of course! But don't take it personally or even something as specific as Ubuntu.  I'm just generally a cynical person

> **23meg said:**
> And Microsoft Windows, which is proprietary, closed-source, ships with hard-wired default applications that the end user cannot replace *at all* (such as IE), doesn't have development and governance structures that give the end user any way to be involved in its development *at all*, has a 95% market share.
Actually you can get rid of, or rather never install, IE in Windows 7...
Although, specifically to Ubuntu Karmic, if I wanted to could I install Pidgin and completely remove empathy?

There's MSDN. Another place where there are forums which were quite active during development of Windows 7.

And despite (or because?) of that, it has 95% market share.

---

### Post by 23meg on 2009-09-15
> **Merk42 said:**
> 
Of course! But don't take it personally or even something as specific as Ubuntu.  I'm just generally a cynical person

It shows, and it's not exactly helping make the community you participate in a better place.

[QUOTE=Merk42]Actually you can get rid of, or rather never install, IE in Windows 7...[/QUOTE]

But Windows didn't gain its 95% market share with Windows 7, but with versions where IE was hard-wired, so that point is moot.

[QUOTE=Merk42]Although, specifically to Ubuntu Karmic, if I wanted to could I install Pidgin and completely remove empathy?[/QUOTE]

Of course.

[QUOTE=Merk42]There's MSDN. Another place where there are forums which were quite active during development of Windows 7.[/QUOTE]

Which are not even remotely comparable to freely distributable and modifiable source code, open bug tracking and development discourse, open standards and development tools and so on, all provided on a non-discriminatory basis, which we've come to take for granted in free software.

---

### Post by qamelian on 2009-09-15
> **zekopeko said:**
> Let's see: Empathy devs are actually listening to input from Ubuntu devs.
Then why do I still need to install Pidgin to be able to block unwanted contacts. This issues has been commented on numerous times by myself and others.

> What is stopping people from using Ubuntu is the lack of AV support.
This is simply not true. Less than 2% of my contact list of over 230 people actually want / use voice/video in their IM client regardless of which OS they run. Exactly 3 contacts out of 230+. I'm pretty sure that my particular assortment of contacts can't be *that* much of an aberration from the norm. What I do believe is that the folks who *do* want voice & video are simply more vocal that those who don't want it or don't care. 

The last time I tried to use empathy, I started getting requests to add contacts I didn't recognize to my contact list. Although I was offered an option to ignore those contacts, they were back every time I logged in. To get rid of them permanently, once again I had to install Pidgin. Sorry, but for me that is a show-stopper and demonstrates the Empathy has no business as default. 

The default IM client should be one that at least gets the basics right. Pidgin isn't perfect but it's a darn sight closer than Empathy.

---

### Post by Stereotypical Rage on 2009-09-15
> **zekopeko said:**
> ... What is stopping people from using Ubuntu is the lack of AV support...

That's NOT what's truly stopping people from using Ubuntu and other distros including the various BSD flavors and you know it. Gaming and interoperability are more significant than silly AV support in a multi-purpose chat client. I'm sure we could write a ton on what's holding people back from using anything other than Windblows.

---

### Post by Stereotypical Rage on 2009-09-15
> **zekopeko said:**
> So let me get this straight: You are saying that one FLOSS project using code from another FLOSS project is a bad thing?

In this instance yes it is, especially when there's this silly zealots of Empathy that just say "use empathy!!!!!!11111 elevnty one!!!! Its bet-r!".

---

### Post by Katalog on 2009-09-15
> **Swarms said:**
> It is not a debate if the two factions use the same 5 arguments every time. They do not seem to convince anyone.

Actually, I'd have to disagree with you on that one for two reasons, aside from the fact that there only being the same 5 arguments is just a bit of and exaggeration, and that is 1) that I've actually read few stories reporting that devs were briefly reconsidering this very issue based *partially* on the enormous amount of debate going on in the community and 2) because their have been some points stated during some of these debates, discussions or whatever you choose to call them that have had some kind of influence to one degree or another (depending on how informed/intelligent the information was) on my own position concerning the whole matter.

Be that as it may, I'm at a point where what's currently being discussed is all pretty moot to me at the moment (only reason I replied is because I'm subscribed to this thread and happened to see your reply in email - something I'll remedy by unsubscribing as soon as I post this) because I feel like I've garnered enough info to convince me to stick with PIdgin for the time being. That's not to say I'm not willing to give the final release of Emapthy a fair shake when Karmic hits the streets, I just feel more comfortable where I'm at at this particular point in time.

Out. :guitar:

---

### Post by zoomy942 on 2009-09-15
I still content that Empathy is a step in the right direction but it's not offering the fluid user experience people have grown accustomed to.  Empathy cant even block spam messages - yet.  it cant connect to facebook - yet.  it cant even use the plethora of plugins that pidgin does - yet....

thats the thing, so many 'yets' when its supposed to be default?  it's as if we are okay with giving up features just for the future.  give it more time in the oven - then let us use it.  i have both pidgin and empathy installed, and i havent learned to trust empathy - yet.  :)

---

### Post by Ratscallion on 2009-09-16
> **qamelian said:**
> Then why do I still need to install Pidgin to be able to block unwanted contacts. 

I think you can...

---

### Post by the.dark.lord on 2009-09-16
> **fct said:**
> Empathy developers haven't said that they won't implement blocking cause they aren't interested in MSN, neither ignored correct patches that add that feature. In fact, you can expect those features to go in without bickering, forking threats and so on while current versions get tested to hell.

In the meanwhile, you can install pidgin and override the default, leaving it exactly as it was before. That's the immediate difference. ;)

What I was referring to was not Empathy devs, but this current argument about replacing Pidgin with Empathy- in which the the developers have virtually overruled the opinion of most (at least, in this forum) end-users.

---

### Post by the.dark.lord on 2009-09-16
> **23meg said:**
> And you *always* want to take it cynically, don't you? 

If it was "for developers, by developers", you would have a terminal IRC client in place of a graphical instant messaging application, and this thread would have been titled "Is [irssi]("http://irssi.org/") ready to replace [finch]("http://developer.pidgin.im/wiki/Using%20Finch")?". End of story.

Perhaps the statement needs to be rephrased: "For people, by developers who think they know what the people want".

---

### Post by Ratscallion on 2009-09-16
Check the screenshot... Blocking is there?

---

### Post by the.dark.lord on 2009-09-16
> **23meg said:**
> 


Which means, feedback (mainly from bug reports) was incorporated into the decision-making process. That means the end user who contributed to the process through filing bug reports *was* represented.

I file bug reports, and I wasn't made aware of any means of how I could represent my stand. 

And most end-users are normal people who usually do not file bug reports. As has been commented on various times on this thread- several people have remarked that the community(non-devs at least) are not taken into account while making these decisions.

---

### Post by the.dark.lord on 2009-09-16
> **Ratscallion said:**
> Check the screenshot... Blocking is there?

That is on Pidgin, he was talking about the non-availability of that feature on Empathy.

---

### Post by the.dark.lord on 2009-09-16
> **qamelian said:**
> 

The default IM client should be one that at least gets the basics right. Pidgin isn't perfect but it's a darn sight closer than Empathy.

How many times has this been said? 

The only valid argument against Pidgin is that the developers do not listen, and implement features at their own sweet time. But, at this moment, the Pidgin developers have a better IM than those at Empathy do. 

It's great that Empathy devs do listen- and are implementing features at a faster rate - which means that Empathy will logically overtake Pidgin soon. Let's have it as default then. Those who want to test Empathy now are free to do so by manually installing it.

---

### Post by 23meg on 2009-09-16
> **the.dark.lord said:**
> Perhaps the statement needs to be rephrased: "For people, by developers who think they know what the people want".

Or rephrased even more finely: "For people, by developers who *have to* make a non-binding choice on behalf of those people, and can't possibly please all of those people no matter what they choose".

---

### Post by 23meg on 2009-09-16
> **the.dark.lord said:**
> I file bug reports, and I wasn't made aware of any means of how I could represent my stand. 

There wasn't supposed to be any special means; you just had to file bug reports as usual.

> **the.dark.lord said:**
> And most end-users are normal people who usually do not file bug reports.

I was under the impression that you were talking about pre-release testers, as in people who voted in this very thread, who are *not* supposed to be "normal people" in that sense. 

> **the.dark.lord said:**
> As has been commented on various times on this thread- several people have remarked that the community(non-devs at least) are not taken into account while making these decisions.

So can you come up with a magical scheme for incorporating the feedback of non-participants (an oxymoron?) in decision-making, short of mind reading? This is a genuine question.

---

### Post by zekopeko on 2009-09-16
> **qamelian said:**
> Then why do I still need to install Pidgin to be able to block unwanted contacts. This issues has been commented on numerous times by myself and others.

What is interesting is that a simple search against bug reports on Empathy using "block", "blocking", "unwanted" didn't give me 1 bug report about missing block functionality. It's in the gnome bugzilla but people aren't commenting on that or pushing for it.

---

### Post by zekopeko on 2009-09-16
> **Stereotypical Rage said:**
> That's NOT what's truly stopping people from using Ubuntu and other distros including the various BSD flavors and you know it. Gaming and interoperability are more significant than silly AV support in a multi-purpose chat client. I'm sure we could write a ton on what's holding people back from using anything other than Windblows.

Interoperability is there for most tasks.
Gaming is a luxury on the other hand. Most people don't game or at least don't care about gaming.

---

### Post by fct on 2009-09-16
> **zekopeko said:**
> What is interesting is that a simple search against bug reports on Empathy using "block", "blocking", "unwanted" didn't give me 1 bug report about missing block functionality. It's in the gnome bugzilla but people aren't commenting on that or pushing for it.

Yeah. Now is when people are requesting the enhancement and linking to that bug here:

[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

---

### Post by meborc on 2009-09-16
i think it is time to close this thread

because:

1) it reminds me of the old emacs vs vi / kde vs gnome / firefox vs opera threads... there will be no resolution...

2) whatever we say on this thread will never change anything, the ubuntu developers have made up their mind... so we just have to accept it and move on

3) the thread has nothing new in it... the subject has been fully analyzed and no results found

---

### Post by the.dark.lord on 2009-09-16
> **23meg said:**
> 
So can you come up with a magical scheme for incorporating the feedback of non-participants (an oxymoron?) in decision-making, short of mind reading? This is a genuine question.

How about creating a voting system where interested end-users can register? Developers votes can carry more points, than a normal end-user's does. Like one developers vote can be equal to say 3(?) end-users. Wouldn't that be fair?

---

### Post by 23meg on 2009-09-16
> **the.dark.lord said:**
> How about creating a voting system where interested end-users can register? Developers votes can carry more points, than a normal end-user's does. Like one developers vote can be equal to say 3(?) end-users. Wouldn't that be fair?

No, and [trusting numbers blindly]("http://www.useit.com/alertbox/20040301.html") in that fashion would be very misleading.

---

### Post by fct on 2009-09-16
> **the.dark.lord said:**
> How about creating a voting system where interested end-users can register? Developers votes can carry more points, than a normal end-user's does. Like one developers vote can be equal to say 3(?) end-users. Wouldn't that be fair?

Closest thing I could think of:

[http://fridge.ubuntu.com/node/1357](http://fridge.ubuntu.com/node/1357)

---

### Post by gnomeuser on 2009-09-16
> **the.dark.lord said:**
> How about creating a voting system where interested end-users can register? Developers votes can carry more points, than a normal end-user's does. Like one developers vote can be equal to say 3(?) end-users. Wouldn't that be fair?

No, users rarely if ever have the technical insight to determine what the best solution is from a design and roadmap point of view. Regardless are you saying it only takes 3 users to make up for a developer. Then by inference the 35,611 users currently online would be equaliant to roughly 12.000 developers.. there simply aren't that many developers available to us. If we drown the insight and expertise of developers in pointless uninformed user babble we are going to piss them off and development will take a significant hit, worst of all though, Ubuntu will suck and be without any hope of ever improving.

Your opinion gets heard based on it's merit and nothing else.. period. If you, the user, want influence, get your hands out your pockets and start contributing. You don't have to do coding but you do have to know what you are talking about and provide some support for your opinion and why it matters. 

There is no professional field that works in the way you describe.. imagine if 3 patients was equal to the opinion of a surgeon. If 3 out of those 4 people this pool would make up say we should operate on your brain, do you care which side the person with years of medical training and a lengthy education is on? I thought so too.

---

### Post by Podex on 2009-09-16
So, I don't know if this has been mentioned before, but a final decision has been made: [https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-15](https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-15)

> # ACTION: rickspencer3 to disuss piddin/empathy with seb128 and pitti and make call for Karmic

    * RESULT: we are sticking with the POR:
          o Empathy will be installed in new installs, pidgin won't be
          o Empathy will be installed on upgrade installs, pidgin won't be removed
          o Empathy will offer to import pidgin settings on first run 

> [17:32] <rickspencer3> pitti, seb128 - yes, I'm just publically announcing the deciscion, and marking the end of discussion on the matter
[17:32] <rickspencer3> (until the next UDS ;) )

---

### Post by zekopeko on 2009-09-16
> **Podex said:**
> So, I don't know if this has been mentioned before, but a final descision has been made: [https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-15](https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-15)

And the forces of long term planning WIN!!!!

not-so FLAWLESS VICTORY!!!

---

### Post by gnomeuser on 2009-09-16
> **Podex said:**
> So, I don't know if this has been mentioned before, but a final descision has been made: [https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-15](https://wiki.ubuntu.com/DesktopTeam/Meeting/2009-09-15)

I read that on the mailing list but i don't think it was mentioned here. Regardless if we can manage to rescue the thread from it's current devolution I think we might get some sensible data out of it.

A list of lacking features to take to upstream as proper and polite feature requests e.g., hopefully nicely prioritized. In return we could probably get some input from the telepathy and empathy guys into how much infrastructure needs to be in place to make those happen and which ones they are immediately interested in working on. 

On the list so far from looking at the last few pages:
1) More extensive contact configuration (primarily blocking)
2) Off the Record
3) Yahoo! webcam/voip (and other protocols)

My personal guess on these:
1. seems like a likely target for fixing soon.
2. is going to take some infrastructure work on telepathy and is also likely to require developers with a certain expertise. 
3. is likely not to happen soon without some corporate sponsorship, reverse engineering protocols is hard and time consuming, it's a big job for such little gain and as such is probably going to be best suited for passionate volunteers currently.

---

### Post by fluffman86 on 2009-09-16
First, I'd like to see Empathy easier to use.  I honestly couldn't figure it out.  I couldn't get IRC to work at all...is it supported?  Finally, facebook support would be awesome.

Regardless of how easy to use or nice empathy is for basic IM use, without Facebook and IRC support it's pretty much useless for me, because the only other protocol I use regularly is google talk.  No need to run an IRC client, Facebook in the browser, and Empathy for google talk when I could just use gmail.

---

### Post by zekopeko on 2009-09-16
> **fluffman86 said:**
> First, I'd like to see Empathy easier to use.  I honestly couldn't figure it out.  I couldn't get IRC to work at all...is it supported?  Finally, facebook support would be awesome.

Regardless of how easy to use or nice empathy is for basic IM use, without Facebook and IRC support it's pretty much useless for me, because the only other protocol I use regularly is google talk.  No need to run an IRC client, Facebook in the browser, and Empathy for google talk when I could just use gmail.

telepathy-idle?

---

### Post by 243kof on 2009-09-16
> **gnomeuser said:**
> 
A list of lacking features to take to upstream as proper and polite feature requests e.g., hopefully nicely prioritized. In return we could probably get some input from the telepathy and empathy guys into how much infrastructure needs to be in place to make those happen and which ones they are immediately interested in working on. 

On the list so far from looking at the last few pages:
1) More extensive contact configuration (primarily blocking)
2) Off the Record
3) Yahoo! webcam/voip (and other protocols)



Add file transfer to the list! (at least for gtalk :) )

---

### Post by Merk42 on 2009-09-16
> **23meg said:**
> But Windows didn't gain its 95% market share with Windows 7, but with versions where IE was hard-wired, so that point is moot.
Okay, but then again I'm not even sure what you original point was as you listed 3 "bad" things about Microsoft then ended with how they have 95% market share

> **zekopeko said:**
> And the forces of long term planning WIN!!!!

not-so FLAWLESS VICTORY!!!
Um, a lot of people who are/were against empathy were simply against it **now**, a lot had no problem with Empathy "in the long run".

> **gnomeuser said:**
> I read that on the mailing list but i don't think it was mentioned here. Regardless if we can manage to rescue the thread from it's current devolution I think we might get some sensible data out of it.
Well with the announcement, what is the point of this thread? People can still say it's not ready until they're blue in the face but a decision has been made.

Feature requests? It seems unless you're a coder, or at the very least know the ease/difficulty of programming, a suggestion has no 'merit' and therefore won't be considered.

> **gnomeuser said:**
> There is no professional field that works in the way you describe.. imagine if 3 patients was equal to the opinion of a surgeon. If 3 out of those 4 people this pool would make up say we should operate on your brain, do you care which side the person with years of medical training and a lengthy education is on? I thought so too.
Well in the "professional field", the user (or patient in your case), can simply say "well I'm going to spend my money elsewhere, you lose business from me because I'm not being considered".  FLOSS users don't have that leverage.

---

### Post by Joe_Bishop on 2009-09-16
> **243kof said:**
> Add file transfer to the list! (at least for gtalk :) )
it's already here

---

### Post by qamelian on 2009-09-16
> **Ratscallion said:**
> I think you can...
Not permanently, at least not as of last week when I tried Empathy again. It alerts me that someone wants to be added to my contact list. The only negative option I am given is to ignore, which I select. The next time I log into my laptop, I ampresent with a request from the same unwanted contact. This persists every single time until I finally launch Pidgin and block the pest. Then I never see them again. The way it appears to work in Empathy is not acceptable and will prevent me from giving it serious consideration.

---

### Post by 23meg on 2009-09-16
> **Merk42 said:**
> Okay, but then again I'm not even sure what you original point was as you listed 3 "bad" things about Microsoft then ended with how they have 95% market share

*sigh*

The poster I quoted implied a causative correlation between their perceived notion of the "end user" having no say in development and "Linux" having a 1% market share. I debunked that by providing the Windows example: Windows end users can't get involved in Windows development discussions at any reasonable extent (that is "Microsoft doesn't listen to its users" in forum speak), can't modify the source code of the software they pay for, can't replace part of their default software if they disagree with Microsoft's decisions for defaults, can't roll out a modified Windows with, say, VLC preinstalled instead of Windows Media Player, yet still, Windows has a 95% market share.

---

### Post by qamelian on 2009-09-16
> **Ratscallion said:**
> Check the screenshot... Blocking is there?
That's for existing contacts. You don't get the option when a spammer requests to be added to you contact list. I have better things to do with my time than click "ignore" on the same batch of spammers every time I login.

---

### Post by qamelian on 2009-09-16
> **the.dark.lord said:**
> How many times has this been said? 

The only valid argument against Pidgin is that the developers do not listen, and implement features at their own sweet time. But, at this moment, the Pidgin developers have a better IM than those at Empathy do. 

It's great that Empathy devs do listen- and are implementing features at a faster rate - which means that Empathy will logically overtake Pidgin soon. Let's have it as default then. Those who want to test Empathy now are free to do so by manually installing it.
That is exactly my point. I have no problem with Empathy being the default if and when it can provide the features I require that already exist in Pidgin. As far as Empathy / Telepthy laying the foundation for future functionality, I don't give a rat's backside about that if it means I need to install a second app to retain the features that I need.

---

### Post by zoomy942 on 2009-09-16
> **qamelian said:**
> That's for existing contacts. You don't get the option when a spammer requests to be added to you contact list. I have better things to do with my time than click "ignore" on the same batch of spammers every time I login.

thats why i love bot-sentry so much with pidgin

---

### Post by qamelian on 2009-09-16
> **zekopeko said:**
> What is interesting is that a simple search against bug reports on Empathy using "block", "blocking", "unwanted" didn't give me 1 bug report about missing block functionality. It's in the gnome bugzilla but people aren't commenting on that or pushing for it.
Sorry but blocking should be a "no-brainer". I have no faith in any development effort that could ignore or omit such a basic element of an instant messenger in favour of laying the ground-work for features that are by no means essential in an instant messaging client. Pretty much every "feature" I have heard mentioned in conjunction with where Empathy is heading amount to a luxury item. The ability to block IM spammers is not. Failing to add this feature early on indicates to me deficiencies in the planning of the developers.

---

### Post by qamelian on 2009-09-16
> **zekopeko said:**
> And the forces of long term planning WIN!!!!
Hardly. Like I said. I don't care what features this will offer me in the long-term if it adds complications to my life now. It doesn't matter how you colour, this is a poor decision. If people are interested in testing Empathy, they will. I am no longer interested in doing so. Including it in the default install makes us all testers by default, requiring to opt-out if we prefer to use the more feature complete choice. That should never be the case. Testing should follow an opt-in model, not the other way around.

---

### Post by qamelian on 2009-09-16
> **zoomy942 said:**
> thats why i love bot-sentry so much with pidgin
Definitely.

---

### Post by novafluxx on 2009-09-16
> **qamelian said:**
> That's for existing contacts. You don't get the option when a spammer requests to be added to you contact list. I have better things to do with my time than click "ignore" on the same batch of spammers every time I login.

> **qamelian said:**
> That is exactly my point. I have no problem with Empathy being the default if and when it can provide the features I require that already exist in Pidgin. As far as Empathy / Telepthy laying the foundation for future functionality, I don't give a rat's backside about that if it means I need to install a second app to retain the features that I need.

> **qamelian said:**
> Sorry but blocking should be a "no-brainer". I have no faith in any development effort that could ignore or omit such a basic element of an instant messenger in favour of laying the ground-work for features that are by no means essential in an instant messaging client. Pretty much every "feature" I have heard mentioned in conjunction with where Empathy is heading amount to a luxury item. The ability to block IM spammers is not. Failing to add this feature early on indicates to me deficiencies in the planning of the developers.

> **qamelian said:**
> Hardly. Like I said. I don't care what features this will offer me in the long-term if it adds complications to my life now. It doesn't matter how you colour, this is a poor decision. If people are interested in testing Empathy, they will. I am no longer interested in doing so. Including it in the default install makes us all testers by default, requiring to opt-out if we prefer to use the more feature complete choice. That should never be the case. Testing should follow an opt-in model, not the other way around.

> **qamelian said:**
> Definitely.

You can use the multi-quote feature ya know. Just FYI man. I agree with you though, so I'm not attacking, just letting ya know in case you didn't know about the multi-quote feature!:guitar:

---

### Post by coldReactive on 2009-09-16
> **novafluxx said:**
> You can use the multi-quote feature ya know. Just FYI man. I agree with you though, so I'm not attacking, just letting ya know in case you didn't know about the multi-quote feature!:guitar:

That's also why there's a report button feature ( [img]http://ubuntuforums.org/images/buttons/report.gif[/img] ). Just a friendly FYI.

---

### Post by gnomeuser on 2009-09-16
> **243kof said:**
> Add file transfer to the list! (at least for gtalk :) )

Filetransfer works for me in google talk via empathy. Addtionally I read in the msn webcam announcement that they also got filetransfer working there.

---

### Post by novafluxx on 2009-09-16
> **coldReactive said:**
> That's also why there's a report button feature ( [img]http://ubuntuforums.org/images/buttons/report.gif[/img] ). Just a friendly FYI.
:confused::confused::confused::confused::confused:
I'd rather inform somone of a feature they may not know about, then jump into repoting them. I'm not evil.

---

### Post by coldReactive on 2009-09-16
> **novafluxx said:**
> :confused::confused::confused::confused::confused:
I'd rather inform somone of a feature they may not know about, then jump into repoting them. I'm not evil.

Informing someone of a feature is best left for PMs, not posts where you could sound like you're acting like a moderator for doing such. I know I'm sounding like one right now, aren't I.

---

### Post by the.dark.lord on 2009-09-16
-Delete this, mods- Double posted accidentally.

---

### Post by novafluxx on 2009-09-16
> **coldReactive said:**
> Informing someone of a feature is best left for PMs, not posts where you could sound like you're acting like a moderator for doing such. I know I'm sounding like one right now, aren't I.

You're probably right on that, I should have PM'd him instead.

---

### Post by the.dark.lord on 2009-09-16
> **23meg said:**
> No, and [trusting numbers blindly]("http://www.useit.com/alertbox/20040301.html") in that fashion would be very misleading.

I agree that this method is not without its flaws, but that does not obscure the fact that it is most widely used method. Why? Because it's efficient.

> **gnomeuser said:**
> No, users rarely if ever have the technical insight to determine what the best solution is from a design and roadmap point of view. Regardless are you saying it only takes 3 users to make up for a developer. Then by inference the 35,611 users currently online would be equaliant to roughly 12.000 developers.. there simply aren't that many developers available to us. If we drown the insight and expertise of developers in pointless uninformed user babble we are going to piss them off and development will take a significant hit, worst of all though, Ubuntu will suck and be without any hope of ever improving.


Your opinion gets heard based on it's merit and nothing else.. period. If you, the user, want influence, get your hands out your pockets and start contributing. You don't have to do coding but you do have to know what you are talking about and provide some support for your opinion and why it matters.


Three was not meant to be taken literally, it's just a number I suggested. Make that 50? 100? I'm sure a number can be agreed upon. Notice the '?' at the end of it. I have serious doubts that 36,000 people will sign up for such a thing. For example, take the people who voted in this poll. As this is the development section of the forum, we can assume fair knowledge of the subject by the users. Valid arguments were provided. How about you get a brush up on the Ubuntu philosophy of inclusion?

Far from making Ubuntu, sucky; taking the learned end-user into consideration will enhance the development, and the user experience can be said to considerably improve. Note again that I'm saying that the developer NEEDS to be given a *very* high importance so that their expertise will be given due consideration. Inclusion (fair consideration, at least) of the end-users views will be beneficial to all.

> **gnomeuser said:**
> There is no professional field that works in the way you describe.. imagine if 3 patients was equal to the opinion of a surgeon. If 3 out of those 4 people this pool would make up say we should operate on your brain, do you care which side the person with years of medical training and a lengthy education is on? I thought so too.


Allow me to quote 23meg:

[http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)

> **zekopeko said:**
> And the forces of long term planning WIN!!!!

not-so FLAWLESS VICTORY!!!

Going back to the original topic, Empathy only has **potential** advantage over Pidgin.

qamelian got this right:

"It doesn't matter how you colour, this is a poor decision. If people are interested in testing Empathy, they will. I am no longer interested in doing so. Including it in the default install makes us all testers by default, requiring to opt-out if we prefer to use the more feature complete choice. That should never be the case. Testing should follow an opt-in model, not the other way around."

---

### Post by 23meg on 2009-09-16
[QUOTE=the.dark.lord]I agree that this method is not without its flaws, but that does not obscure the fact that it is most widely used method. Why? Because it's efficient.[/QUOTE]

Then you can perhaps show me a software project that uses such a binding polling system for technical decision making and feature planning where positive results have been obtained due to the use of that system.

---

### Post by jpeddicord on 2009-09-16
> **novafluxx said:**
> :confused::confused::confused::confused::confused:
I'd rather inform somone of a feature they may not know about, then jump into repoting them. I'm not evil.

> **coldReactive said:**
> Informing someone of a feature is best left for PMs, not posts where you could sound like you're acting like a moderator for doing such. I know I'm sounding like one right now, aren't I.

novafluxx has a point. Report Post won't PM the poster. It will just report the post to us. What are we supposed to do with that? :P

---

### Post by qamelian on 2009-09-16
> **novafluxx said:**
> You can use the multi-quote feature ya know. Just FYI man. I agree with you though, so I'm not attacking, just letting ya know in case you didn't know about the multi-quote feature!:guitar:
Thanks, but I was just responding to each post as I hit them on my break this morning. No attack detected, so all good.  :)

---

### Post by qamelian on 2009-09-16
> **jacobmp92 said:**
> novafluxx has a point. Report Post won't PM the poster. It will just report the post to us. What are we supposed to do with that? :P
Pat me on the head and give me a cookie? :)

---

### Post by coldReactive on 2009-09-16
> **jacobmp92 said:**
> novafluxx has a point. Report Post won't PM the poster. It will just report the post to us. What are we supposed to do with that? :P

Mods are usually expected to merge such posts, plus, can't mods edit posts accordingly?

---

### Post by zekopeko on 2009-09-16
> **qamelian said:**
> Sorry but blocking should be a "no-brainer". I have no faith in any development effort that could ignore or omit such a basic element of an instant messenger in favour of laying the ground-work for features that are by no means essential in an instant messaging client. Pretty much every "feature" I have heard mentioned in conjunction with where Empathy is heading amount to a luxury item. The ability to block IM spammers is not. Failing to add this feature early on indicates to me deficiencies in the planning of the developers.

I was pointing out the possible way to influence the devs "their" way.

---

### Post by Keyper7 on 2009-09-16
> **qamelian said:**
> Sorry but blocking should be a "no-brainer". I have no faith in any development effort that could ignore or omit such a basic element of an instant messenger in favour of laying the ground-work for features that are by no means essential in an instant messaging client. Pretty much every "feature" I have heard mentioned in conjunction with where Empathy is heading amount to a luxury item. The ability to block IM spammers is not. Failing to add this feature early on indicates to me deficiencies in the planning of the developers.

Sorry, but I don't have problems with spammers and I don't consider blocking a "no-brainer basic element".

My point? Just because you consider something to be essential, doesn't mean everyone agrees. So, aside for conceding amazing psychic powers to the developers, the only way of getting your point across is going to the mailing lists and bug reports. As zekopeko pointed out, it doesn't seem like this is being done enough.

I agree that not being able to read people's minds is a "deficiency", Magneto, but please be a little bit more merciful to us non-mutants. :)

That reminded me of a friend of mine, who is a teacher at an university. She once gave a course using slides instead of the blackboard and was later completely slandered by the students' evaluation of the course, because they claimed that slides were "obviously" a less efficient method of teaching. They are entitled to their opinion, but what really pissed off my friend was that they had *four months* of classes to point this out and *no one said a thing*. A simple hand raised would've made her happily go back to the blackboard.

---

### Post by Keyper7 on 2009-09-16
Who the hell tagged this thread as "pigeons have no empathy"? :)

---

### Post by Aries K on 2009-09-16
If Pidgin got as much love as it's OSX cousin Adium I would gladly switch over. Adium has had all around better features than Pidgin for the longest. They had plenty of time to incorporate these features into Pidgin or just better yet make an Adium port for Linux. I am glad they made the bold decision and chose Empathy over Pidgin. Pidgin is just too conservative for my tastes and the Finch team treats it as a second rate program compared to where they made it with Adium. As far as "cross platform" or "recognition" goes very few people in the Windows world even know about Pidgin(compared to those who use proprietory clients), they prefer to use the popular Yahoo or MSN messenger and wouldn't touch Pidgin. Pidgin is NOT the "Firefox" of the IM world. If I wanted something that was overly basic and simplistic I would use some type of command line IM. Even back before Empathy existed Kopete surpassed Pidgin in features. I am sure blocking will be incorporated soon, in all of the years I have used any IM program I have rarely had to block anyone unless it was a personal issue with someone etc. If you are having problems with spam your screename(s) are getting leaked somewhere via Google etc and bots are picking them up. EDIT: Nevermind not even Adium has had voice/video support yet, still a better app than Pidgin though.

---

### Post by qamelian on 2009-09-16
> **Keyper7 said:**
> Sorry, but I don't have problems with spammers and I don't consider blocking a "no-brainer basic element".

My point? Just because you consider something to be essential, doesn't mean everyone agrees. So, aside for conceding amazing psychic powers to the developers, the only way of getting your point across is going to the mailing lists and bug reports. As zekopeko pointed out, it doesn't seem like this is being done enough.

I agree that not being able to read people's minds is a "deficiency", Magneto, but please be a little bit more merciful to us non-mutants. :)

That reminded me of a friend of mine, who is a teacher at an university. She once gave a course using slides instead of the blackboard and was later completely slandered by the students' evaluation of the course, because they claimed that slides were "obviously" a less efficient method of teaching. They are entitled to their opinion, but what really pissed off my friend was that they had *four months* of classes to point this out and *no one said a thing*. A simple hand raised would've made her happily go back to the blackboard.

If you don't have a problem with spammers, consider yourself lucky I and many other users I know do. And it *is* a no-brainer. This is a basic feature that is common to every decent IM I have ever encountered. It is as logically a necessity in an IM as the ability to chat in the first place. It is so basic as to be part of the security requirements for a number of my clients who use instant messaging. No mind-reading should be required. 

I also find it difficult to lend any credence to your opinion since you found it necessary to resort to name-calling. It dramatically reduces any consideration I might have otherwise given your argument. Insulting behaviour certainly won't change my opinion.

---

### Post by Amaranth on 2009-09-16
Have you filed a bug?

---

### Post by scaine on 2009-09-16
> **qamelian said:**
> If you don't have a problem with spammers, consider yourself lucky I and many other users I know do. And it *is* a no-brainer. This is a basic feature that is common to every decent IM I have ever encountered. It is as logically a necessity in an IM as the ability to chat in the first place. It is so basic as to be part of the security requirements for a number of my clients who use instant messaging. No mind-reading should be required.

I've been using IM since ICQ was founded in the late 90's and I've been using the same screen name since about 2003/4.  Never, once, have I had a spam-bot, nor ever needed to block a person.  Each to their own, I suppose, but this backs the original assertion, that just because you think it's essential, it's not everyone's opinion.

I'm lucky enough to be able to use invite-only buddies of course, so I suppose this is why I'm never affected.

> **qamelian said:**
> I also find it difficult to lend any credence to your opinion since you found it necessary to resort to name-calling. It dramatically reduces any consideration I might have otherwise given your argument. Insulting behaviour certainly won't change my opinion.

I think you're taking the mick here, but I'm not sure.  Just in case, Keyper7 was making fun of psychic ability with the use of an X-Men quote.  He wasn't being insulting.  I think.  I'm not psychic though.

---

### Post by orlox on 2009-09-16
> **qamelian said:**
> If you don't have a problem with spammers, consider yourself lucky I and many other users I know do. And it *is* a no-brainer. This is a basic feature that is common to every decent IM I have ever encountered. It is as logically a necessity in an IM as the ability to chat in the first place. It is so basic as to be part of the security requirements for a number of my clients who use instant messaging. No mind-reading should be required. 

I also find it difficult to lend any credence to your opinion since you found it necessary to resort to name-calling. It dramatically reduces any consideration I might have otherwise given your argument. Insulting behaviour certainly won't change my opinion.

I for myself, have only blocked a contact once in my life...Perhaps for you it's an absolute necessity, but at least for me, it's by no way a showstopper.

I've disliked pidgin for ages, cause it forced me to resort to amsn every time I needed webcam support (which happens often), just as you need to resort to pidgin to block your empathy contacts. For me, empathy with msn a/v support is by far more important than blocking contacts...heck, I didn't even knew empathy was unable to do it until I read this thread...

Just as you, I could say pidgin is useless, cause I need to resort to another software to fulfil some functionality. I could call a no-brainer the fact that they have ignored working on a/v support, and say I'm impressed on how people trust such a wrongly directed project. But I don't do that, cause the truth is, I see that mine is a particular point of view, and not an absolute truth. Many disagree with me and consider a/v support a luxury, while I consider "contact blocking" a wishlist item...And neither of us is wrong, we just have different use cases...

@Keyper7: Charles Xavier reads minds, not Magento...

---

### Post by Keyper7 on 2009-09-16
> **qamelian said:**
> If you don't have a problem with spammers, consider yourself lucky **I** and many other users I know do. And it is a no-brainer. This is a basic feature that is common to every decent IM **I** have ever encountered. It is as logically a necessity in an IM as the ability to chat in the first place. It is so basic as to be part of the security requirements for a number of **my** clients who use instant messaging. No mind-reading should be required.

You didn't get the point. The empathy developers are doing what they should, which is to prioritize efforts according to user feedback. Right now, bug reports about blocking are absent or silent according to zekopeko. Even if I agreed with you that blocking is an essential feature, think about what the developers are seeing now: *no reports asking for this*.

> **qamelian said:**
> I also find it difficult to lend any credence to your opinion since you found it necessary to resort to name-calling. It dramatically reduces any consideration I might have otherwise given your argument. Insulting behaviour certainly won't change my opinion.

Wait, what? Could you please quote the name-calling? I'm serious. I'm re-reading my previous post over and over again and I'm not seeing what prompted you to say this.

---

### Post by Keyper7 on 2009-09-16
> **orlox said:**
> @Keyper7: Charles Xavier reads minds, not Magento...

Do not dare to question my geekiness with such an obvious statement, oh heretic one. :)

I mentioned Magneto because he is the one who considers lack of special powers (which in this case is mind reading but could be something else) as a "deficiency".

---

### Post by qamelian on 2009-09-16
> **scaine said:**
> I've been using IM since ICQ was founded in the late 90's and I've been using the same screen name since about 2003/4.  Never, once, have I had a spam-bot, nor ever needed to block a person.  Each to their own, I suppose, but this backs the original assertion, that just because you think it's essential, it's not everyone's opinion.

I'm lucky enough to be able to use invite-only buddies of course, so I suppose this is why I'm never affected.

Congratulations. I know many people who aren't as lucky. The only virus that ever successfully infected my old Windows box was installed by a 'bot through ICQ. While it may not be a priority to some end-users, the ability to block unwanted contacts should be high on the list of priorities of any conscientious developer. Neglecting to include this basic feature would be enough to get a developer fired in some organizations I've contracted to over the years. 



> I think you're taking the mick here, but I'm not sure.  Just in case, Keyper7 was making fun of psychic ability with the use of an X-Men quote.  He wasn't being insulting.  I think.  I'm not psychic though.
No, I was not "taking the mick". I found the way he expressed himself to be genuinely insulting. As someone who suffers from a genetic deformity about which I am very sensitive, I don't appreciate name-calling even in alleged jest. 

Anyway, the discussion is pointless. I stand by my previous statement that including Empathy by default to encourage wider testing is not acceptable because it requires those of us who don't want to be involved in testing this app to opt-out. Testing should always be an opt-in process. 

For me and many of my clients, Ubuntu loses significant credibility due to this decision. Ubuntu originally promised to shipped with the "best of breed" in each category of app installed by default, and Empathy does not meet this standard yet.

---

### Post by por100pre1 on 2009-09-16
I don't care if Empathy has better integration with GNOME. It doesn't even support buddy icons. I'm an Average Joe and I want my IM to just work...
[B]
Pidgin +1[/B]

---

### Post by orlox on 2009-09-16
> **Keyper7 said:**
> Do not dare to question my geekiness with such an obvious statement, oh heretic one. :)

I mentioned Magneto because he is the one who considers lack of special powers (which in this case is mind reading but could be something else) as a "deficiency".
You're absolutely right about that. Just for one second I thought you were the one making a completely heretic analogy. Guess I missed the deeper meaning in your statement ;)

---

### Post by qamelian on 2009-09-16
> **Keyper7 said:**
> You didn't get the point. The empathy developers are doing what they should, which is to prioritize efforts according to user feedback. Right now, bug reports about blocking are absent or silent according to zekopeko. Even if I agreed with you that blocking is an essential feature, think about what the developers are seeing now: *no reports asking for this*.

There shouldn't need to be a bug report as it should have been part of the initial design spec. I've seen developers fired for smaller oversights. I'm responsible everyday for making sure such oversights don't occur.

> Wait, what? Could you please quote the name-calling? I'm serious. I'm re-reading my previous post over and over again and I'm not seeing what prompted you to say this.

You referred to me as "Magneto" and indirectly referred to me as a mutant by referring others as non-mutants. English syntax isn't so complicated  as to make that hard to understand. I'm offended for the reasons stated in my response to another poster. 

Anyway, I've completely had it with this discussion. User feedback needs to be balanced with common sense development principles, and I don't see that happening with Empathy. The decision is already made and, considering the current state of the app, there is nothing you can say that will convince me that it is right. It might have been appropriate in 6 months or a year after Empathy has mature more fully, but it is certainly not appropriate now.

---

### Post by Keyper7 on 2009-09-16
> **qamelian said:**
> There shouldn't need to be a bug report as it should have been part of the initial design spec. I've seen developers fired for smaller oversights. I'm responsible everyday for making sure such oversights don't occur.

Yeah, but there's already three people in this thread already who don't consider this an oversight. You're not giving logical arguments, you're giving anedoctal data, which can be countered with different anedoctal data. The only *structured and verifiable* way through which the developers can collect data are bug reports.

> **qamelian said:**
> You referred to me as "Magneto" and indirectly referred to me as a mutant by referring others as non-mutants. English syntax isn't so complicated  as to make that hard to understand. I'm offended for the reasons stated in my response to another poster.

*English syntax* is easy, but *comic book semantics* are not.

So I'll have to explain why you have no reason to be offended.

Magneto is a Marvel comic book villain who is a mutant. A "mutant", in the Marvel universe, is a generic term used to define people who were born with super-human powers. Magneto believes that common humans, who do not have such powers, are inferior to mutants and refers to their lack of powers as a "deficiency".

From your posts, my opinion was that you wanted the Empathy developers to read the minds of the users, which is a super-human power. You used the word "deficiency" to refer to their lack of knowledge of something which, in my opinion, requires mind-reading. This reminded me very much of Magneto's speeches, so that's why I made the joke.

In short, the message in the joke was: "it seems you consider lack of super-powers as a deficiency".

So, sorry if you felt offended. Sometimes I forget that not everybody is a comic book geek like me. :)

---

### Post by tretle on 2009-09-16
> **qamelian said:**
> There shouldn't need to be a bug report as it should have been part of the initial design spec. I've seen developers fired for smaller oversights. I'm responsible everyday for making sure such oversights don't occur. 

Thank you so much, you are the most important contributor to the OSS community, I see that now. Screw the people who take the time to design and implement the specs. 
If you can bash everyones effort because you don't think the +1 should not mean progression then we all have to realize that you know what you are talking about.
And of course we need to think about users but if we only thought about users then the development process would be horrendous and the applications would not progress. 
Telepathy not only brings new core IM features that pidgin does not have but it also brings new features for developers with an excellent spec which not only eases development but offers new opportunities.
New opportunities mean better apps which means happier users.
Its not just the OSS developers that agree with that either, both nokia and intel back it and I would trust intel/nokia/oss developers opinion more than some guy who trolls forums arguing about change.
I mean have you even read the spec you just bashed? Do you know the difference between telepathy/empathy and pidgin?
The main problem with empathy right now is not the application itself but the packaging, allot of features are currently missing which where in earlier alpha's before the switch and that is creating allot of confusion about it.
These forums are really starting to put me off of open source software these days, I will most likely just need to switch to a different distro as arrogant opinions from people who do not have any idea about the development process seems to be outweighing the ideas of the people who have actual degrees in the subject. 
Everyone wants there own mark on it regardless of whether its right or not.
These forums are on par with fox news in terms of actual factual debate and its not hard to see why the majority of developers who release code upstream do not run ubuntu, why would you when you have people bitching at you about your work and what you contribute.
So back to your responsibility, If you actually cared you would file a bug and be productive not moan in this forum. 
99.9% of developers don't come here because of threads like this. Do you blame them?

---

### Post by Aries K on 2009-09-16
> **por100pre1 said:**
> I don't care if Empathy has better integration with GNOME. It doesn't even support buddy icons. I'm an Average Joe and I want my IM to just work...
[B]
Pidgin +1[/B]

Empathy DOES infact support buddy icons and much more. You are running the outdated version from the Jaunty repos. Empathy has changed A LOT since then. 

[IMG]http://staz.be/tup/2009-06/Capture-Conversations.png[/IMG]

---

### Post by coldReactive on 2009-09-16
> **Aries K said:**
> Empathy DOES infact support buddy icons and much more. You are running the outdated version from the Jaunty repos. Empathy has changed A LOT since then. 

[IMG]http://staz.be/tup/2009-06/Capture-Conversations.png[/IMG]

Looks like they're going the way of WLM, and merging IMs that people do in succession, I didn't like that, made the IM window too crowded.

---

### Post by Aries K on 2009-09-16
> **coldReactive said:**
> Looks like they're going the way of WLM, and merging IMs that people do in succession, I didn't like that, made the IM window too crowded.

It does not come like that out the gate, that is a custom Adium chat style that user chose to use. They were just giving an example of the theme system in action.

---

### Post by andrewabc on 2009-09-16
> **Aries K said:**
> Empathy DOES infact support buddy icons and much more. You are running the outdated version from the Jaunty repos. Empathy has changed A LOT since then. 

[IMG]http://staz.be/tup/2009-06/Capture-Conversations.png[/IMG]

No wonder msn http isn't in my jaunty install, but it is in karmic alphas.

Can I install karmic [ppa](https://launchpad.net/~telepathy/+archive/ppa) on jaunty? Does that work better? Or does it break stuff on jaunty. I only want to test empathy to see what works etc. I don't actually use IM much.

I'm using jaunty and will until final released (I test karmic releases though).

---

### Post by coldReactive on 2009-09-16
> **Aries K said:**
> It does not come like that out the gate, that is a custom **Adium** chat style that user chose to use. They were just giving an example of the theme system in action.

Adium, pff...

---

### Post by Aries K on 2009-09-16
> **andrewabc said:**
> No wonder msn http isn't in my jaunty install, but it is in karmic alphas.

Can I install karmic [ppa](https://launchpad.net/~telepathy/+archive/ppa) on jaunty? Does that work better? Or does it break stuff on jaunty. I only want to test empathy to see what works etc. I don't actually use IM much.

I'm using jaunty and will until final released (I test karmic releases though).

Information can be found here on how to install the latest Empathy in Jaunty. [http://ubuntuforums.org/showthread.php?p=7497168](http://ubuntuforums.org/showthread.php?p=7497168)

Information to install themes can be found here: [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

---

### Post by andrewabc on 2009-09-16
> **Aries K said:**
> Information can be found here on how to install the latest Empathy in Jaunty. [http://ubuntuforums.org/showthread.php?p=7497168](http://ubuntuforums.org/showthread.php?p=7497168)

Information to install themes can be found here: [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

I already have jaunty PPA for empathy installed. But it is not the same as found on livecd alphas.

On live cd alphas there is an option for http connect for msn. On my jaunty empathy install (using ppa which does get updates), there is no msn http conection option. I need http connect option to connect.

---

### Post by Aries K on 2009-09-16
> **andrewabc said:**
> I already have jaunty PPA for empathy installed. But it is not the same as found on livecd alphas.

On live cd alphas there is an option for http connect for msn. On my jaunty empathy install (using ppa which does get updates), there is no msn http conection option. I need http connect option to connect.

Ah ok I get what you mean now. :) What version of Empathy are you running on Jaunty? The latest one should be 2.28.0.

---

### Post by andrewabc on 2009-09-16
> **Aries K said:**
> Ah ok I get what you mean now. :) What version of Empathy are you running on Jaunty? The latest one should be 2.28.0.

empathy 2.27.92 via synaptic (and help->about)
libempathy30
libempathy-gtk28

[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)
Doesn't list anything higher.

---

### Post by Aries K on 2009-09-16
> **andrewabc said:**
> empathy 2.27.92 via synaptic (and help->about)
libempathy30
libempathy-gtk28

[https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)
Doesn't list anything higher.

Ah ok I got it now, we are running different PPAs. That is the "PPA for Telepathy". I am running the "empathy-daily PPA" which updates more often. Here is the link for it, there are options for Jaunty and Karmic.

[https://launchpad.net/~amoog/+archive/empathy-daily](https://launchpad.net/~amoog/+archive/empathy-daily)

---

### Post by andrewabc on 2009-09-16
> **Aries K said:**
> Ah ok I got it now, we are running different PPAs. That is the "PPA for Telepathy". I am running the "empathy-daily PPA" which updates more often. Here is the link for it, there are options for Jaunty and Karmic.

[https://launchpad.net/~amoog/+archive/empathy-daily](https://launchpad.net/~amoog/+archive/empathy-daily)

Jaunty version on that page is older than on one I linked.
2009-09-11 vs 2009-08-23

Although maybe there are differences between packages.

I think I'll just test off alpha cds instead of messing around.

---

### Post by coldReactive on 2009-09-16
> **andrewabc said:**
> Jaunty version on that page is older than on one I linked.
2009-09-11 vs 2009-08-23

Although maybe there are differences between packages.

I think I'll just test off alpha cds instead of messing around.

The build for empathy in jaunty also failed.

---

### Post by qamelian on 2009-09-16
> **Keyper7 said:**
> Yeah, but there's already three people in this thread already who don't consider this an oversight. You're not giving logical arguments, you're giving anedoctal data, which can be countered with different anedoctal data. The only *structured and verifiable* way through which the developers can collect data are bug reports.



*English syntax* is easy, but *comic book semantics* are not.

So I'll have to explain why you have no reason to be offended.

Magneto is a Marvel comic book villain who is a mutant. A "mutant", in the Marvel universe, is a generic term used to define people who were born with super-human powers. Magneto believes that common humans, who do not have such powers, are inferior to mutants and refers to their lack of powers as a "deficiency".

From your posts, my opinion was that you wanted the Empathy developers to read the minds of the users, which is a super-human power. You used the word "deficiency" to refer to their lack of knowledge of something which, in my opinion, requires mind-reading. This reminded me very much of Magneto's speeches, so that's why I made the joke.

In short, the message in the joke was: "it seems you consider lack of super-powers as a deficiency".

So, sorry if you felt offended. Sometimes I forget that not everybody is a comic book geek like me. :)

I don't need you to explain Magneto either I've been reading comics since Magnus still kicking around his old sidekick, Toad. My collection goes back to when Marvel was still Timely Comics. In the real world, calling someone a mutant, even indirectly, is offensive. I've taken a lot of verbal abuse and even physical assault over my deformity when I was younger. It makes me a little thin-skinned about it.

I don't expect mind-reading. I do expect good design principles in the software I use. I don't see that in Empathy. And I still haven't heard one single argument in favour of Empathy that is compelling. Not one. In the environments in which I work, messaging software without a blocking feature would be considered incomplete and unacceptable for general use.

---

### Post by qamelian on 2009-09-16
> **tretle said:**
> Thank you so much, you are the most important contributor to the OSS community, I see that now. Screw the people who take the time to design and implement the specs. 
If I see a spec as flawed, then I will comment on it. If you feel like blowing that all out of proportion, that's your problem, not mine. It doesn't matter how avidly you defend it, a bad decision is a bad decision. Empathy is still to immature to be included in the default install and nothing you or anyone else can say will change my opinion on that. 

You're free to voice your opinion and I'm free to voice mine.

EDIT: And in answer to your question, yes I have read and understood the spec. I would not choose to comment on it otherwise.

---

### Post by Jesus_Valdez on 2009-09-16
I install it and I can see the options to send and receive webcam and sound, but I can't click on it, I supose I'm missing some package, but wich one?

---

### Post by Aries K on 2009-09-16
> **andrewabc said:**
> Jaunty version on that page is older than on one I linked.
2009-09-11 vs 2009-08-23

Although maybe there are differences between packages.

I think I'll just test off alpha cds instead of messing around.

Yeah that might be a better idea, don't wanna bork your Jaunty install by trying Karmic PPAs. But yeah the differences might be in the packages, while the numbers may look different the packages with the really long numbers probably equate to "2.28.0" or something (I could be wrong). I know for sure on my about screen it says "2.28.0" Good luck on whatever method you use to test it though. :)

---

### Post by hanzomon4 on 2009-09-16
> **Jesus_Valdez said:**
> I install it and I can see the options to send and receive webcam and sound, but I can't click on it, I supose I'm missing some package, but wich one?

Same..

---

### Post by gnomeuser on 2009-09-17
> **Jesus_Valdez said:**
> I install it and I can see the options to send and receive webcam and sound, but I can't click on it, I supose I'm missing some package, but wich one?

Telepathy-farsight 0.0.13 is needed which is currently unreleased.

---

### Post by coldReactive on 2009-09-17
> **gnomeuser said:**
> Telepathy-farsight 0.0.13 is needed which is currently unreleased.

Uh, then why the heck is empathy being released in karmic without that support?

---

### Post by dext on 2009-09-17
> **coldReactive said:**
> Uh, then why the heck is empathy being released in karmic without that support?its in Fedora12 i just dont think its installed as default in Empathy.

---

### Post by Jesus_Valdez on 2009-09-17
> **gnomeuser said:**
> Telepathy-farsight 0.0.13 is needed which is currently unreleased.
Thanks.

Well, I'll just sit and wait.

---

### Post by fct on 2009-09-17
> **coldReactive said:**
> Uh, then why the heck is empathy being released in karmic without that support?

Isn't karmic still in alpha?

---

### Post by gnomeuser on 2009-09-17
> **coldReactive said:**
> Uh, then why the heck is empathy being released in karmic without that support?

Because the feature depends on multiple libraries, you already have teleapthy-butterfly and papyon in there for the new msn support. telepathy-farsight has the webcam protocol.

It is in git but they just haven't made a tarball release yet, if needed one could grab a snapshot and release that but lets give upstream a few days to release they probably want to cross those t's and dot those i's.

---

### Post by Staz on 2009-09-17
> **Merk42 said:**
> 

Feature requests? It seems unless you're a coder, or at the very least know the ease/difficulty of programming, a suggestion has no 'merit' and therefore won't be considered.

That's not entirely true, we are always interested in constructive user feedback, this is why we have open bugs tracking systems. 
But repeated rants and bashing by people who won't take the time to fill bugs are unproductive and a lost of time for us, which is probably why I'm the only telepathy dev on this forum, your feedback get lost and you complain nobody listen to you.

Personally I never considered blocking a important feature as I never had to use it (and think it's the same for the other telepathy dev) and I don't think it has ever been really asked (in bug reports or by paying clients). Which doesn't mean it will never been implemented either, just that it had lower priority than other tasks.

---

### Post by girto on 2009-09-17
> **Staz said:**
> Personally I never considered blocking a important feature as I never had to use it (and think it's the same for the other telepathy dev) and I don't think it has ever been really asked (in bug reports or by paying clients). Which doesn't mean it will never been implemented either, just that it had lower priority than other tasks.
Several bugs regarding contacts blocking have been reported in gnome bugzilla:
[https://bugzilla.gnome.org/show_bug.cgi?id=551911](https://bugzilla.gnome.org/show_bug.cgi?id=551911)
[https://bugzilla.gnome.org/show_bug.cgi?id=558773](https://bugzilla.gnome.org/show_bug.cgi?id=558773)
[https://bugzilla.gnome.org/show_bug.cgi?id=588293](https://bugzilla.gnome.org/show_bug.cgi?id=588293)
[https://bugzilla.gnome.org/show_bug.cgi?id=593351](https://bugzilla.gnome.org/show_bug.cgi?id=593351)

---

### Post by coldReactive on 2009-09-17
> I confirm that you should be able to block messages from people not in the
buddy list. However your message is clearly a spam and does not comes from
Empathy.

That's clearly a sign that this issue will be put on the shelf and never touched again. :|

---

### Post by fct on 2009-09-17
> **coldReactive said:**
> That's clearly a sign that this issue will be put on the shelf and never touched again. :|

The bug is open and it's not marked as "won't fix", which would be a clear sign.

I also don't get that vibe from the comments here:

[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

---

### Post by coldReactive on 2009-09-17
> **fct said:**
> The bug is open and it's not marked as "won't fix", which would be a clear sign.

I also don't get that vibe from the comments here:

[http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

Not tagging it with won't fix doesn't mean they'll fix it. The developer clearly stated it should work, meaning s/he basically said worksforme.

---

### Post by Staz on 2009-09-17
> **coldReactive said:**
> Not tagging it with won't fix doesn't mean they'll fix it. The developer clearly stated it should work, meaning s/he basically said worksforme.

No he meant he confirm it's a bug and that Empathy should provide this feature but doesn't yet. If he thought it was working for him (and having developed the application he would know he didn't implement it yet) or that the request wasn't valid believe me he wouldn't have hesitated one second to close the bug.

---

### Post by zekopeko on 2009-09-17
> **qamelian said:**
> Congratulations. I know many people who aren't as lucky. The only virus that ever successfully infected my old Windows box was installed by a 'bot through ICQ. While it may not be a priority to some end-users, the ability to block unwanted contacts should be high on the list of priorities of any conscientious developer. Neglecting to include this basic feature would be enough to get a developer fired in some organizations I've contracted to over the years.

Staz(?) commented on this. Telepathy is commercially supported by Collabora. Their clients didn't see the need for this. So for paid developers the spec is inline with the expectations of their clients. And you can't demand from volunteers to fix a bug on their free time since it's by definition theirs to spend.

> No, I was not "taking the mick". I found the way he expressed himself to be genuinely insulting. As someone who suffers from a genetic deformity about which I am very sensitive, I don't appreciate name-calling even in alleged jest.

You referred to me as "Magneto" and indirectly referred to me as a mutant by referring others as non-mutants. English syntax isn't so complicated  as to make that hard to understand. I'm offended for the reasons stated in my response to another poster.

You can't hold it against the poster for not knowing about your "genetic deformity". And even then it wasn't directed as a stab at your "genetic deformity". You can't have an informal discussion and expect strangers not to offend you by a remark that they think is just an interesting analogy. That is, unless you want all people to stop communicating. 

> Anyway, the discussion is pointless. I stand by my previous statement that including Empathy by default to encourage wider testing is not acceptable because it requires those of us who don't want to be involved in testing this app to opt-out. Testing should always be an opt-in process.

Assuming you are running Karmic you are by default a willing tester. The product was found to have acceptable regression and is being shipped.

> For me and many of my clients, Ubuntu loses significant credibility due to this decision. Ubuntu originally promised to shipped with the "best of breed" in each category of app installed by default, and Empathy does not meet this standard yet.

What is stopping you from hiring a developer and fixing the bug? It's obvious that you are making money on Ubuntu. If you aren't paying for official support from Canonical/Collabora you are in the same position as the rest of us when demanding features (not that you should have any right to demand something from volunteers and certainly not from people on company hours, a company of which you aren't a paying customer).

> **qamelian said:**
> There shouldn't need to be a bug report as it should have been part of the initial design spec. I've seen developers fired for smaller oversights. I'm responsible everyday for making sure such oversights don't occur.

I'm wondering how many oversights you made. Perhaps so many that you can now spot one?

> Anyway, I've completely had it with this discussion. User feedback needs to be balanced with common sense development principles, and I don't see that happening with Empathy. The decision is already made and, considering the current state of the app, there is nothing you can say that will convince me that it is right. It might have been appropriate in 6 months or a year after Empathy has mature more fully, but it is certainly not appropriate now.

Sorry what are "common sense development principles"?

---

### Post by qamelian on 2009-09-17
> **zekopeko said:**
> Staz(?) commented on this. Telepathy is commercially supported by Collabora. Their clients didn't see the need for this. So for paid developers the spec is inline with the expectations of their clients. And you can't demand from volunteers to fix a bug on their free time since it's by definition theirs to spend.

So a quantity of money indicates the level of common sense? This is nonsense.

> You can't hold it against the poster for not knowing about your "genetic deformity". And even then it wasn't directed as a stab at your "genetic deformity". You can't have an informal discussion and expect strangers not to offend you by a remark that they think is just an interesting analogy. That is, unless you want all people to stop communicating. 

I can, however, expect to have an informal discussion without being mocked. No foreknowledge of my condition should be necessary. Commoon courtesy dictates that.

> Assuming you are running Karmic you are by default a willing tester. The product was found to have acceptable regression and is being shipped.

I was referring to remarks made by others that they want it in the Karmic release to ensure wider testing. That means that even after Karmic is out of testing as a genuine release, Empathy will still be there to ensure wider testing. So, my remark stands: this make being a tester on the final release an opt-out proposition. This is wrong and should never be the case.

> What is stopping you from hiring a developer and fixing the bug? It's obvious that you are making money on Ubuntu. If you aren't paying for official support from Canonical/Collabora you are in the same position as the rest of us when demanding features (not that you should have any right to demand something from volunteers and certainly not from people on company hours, a company of which you aren't a paying customer).

You love twisting peoples words, don't you? I make money by providing support to my clients (among other things), some of whom use Ubuntu, some Windows, some Mac OS. I have no need to fix the "bug" because we will not be using Empathy at all unless the state of the software changes. That is not the issue. I don't care how many people actually *want* to use Empathy. That does not change the fact that it does not belong as the default IM in Karmic's final release. No little word games you play will change that.

> I'm wondering how many oversights you made. Perhaps so many that you can now spot one?

I've made my fair share of mistakes over the years and never claimed otherwise. That doesn't have any bearing on this discussion, other than to try to obfuscate the real issue.

> Sorry what are "common sense development principles"?

Why do I even bother? Check any university level computer science text book. They're not that hard to discover.

---

### Post by gnomeuser on 2009-09-17
> **coldReactive said:**
> That's clearly a sign that this issue will be put on the shelf and never touched again. :|

If one was so inclined one could become a paying customer of Collabora and then magically it would be on the table. Not through repeated bashing and attacks but through payments.. just saying, there is always a way.

Another way naturally would be to write up the code.. the door never closes in Open Source except through malice.

---

### Post by por100pre1 on 2009-09-17
> **Aries K said:**
> Information can be found here on how to install the latest Empathy in Jaunty. [http://ubuntuforums.org/showthread.php?p=7497168](http://ubuntuforums.org/showthread.php?p=7497168)

Information to install themes can be found here: [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

I'm gonna try latest Empathy, thanks for the link.

---

### Post by tretle on 2009-09-17
> **qamelian said:**
> So a quantity of money indicates the level of common sense? This is nonsense.
Your an idiot.


> **qamelian said:**
> I can, however, expect to have an informal discussion without being mocked. No foreknowledge of my condition should be necessary. Commoon courtesy dictates that.
Your a moron.



> **qamelian said:**
> I was referring to remarks made by others that they want it in the Karmic release to ensure wider testing. That means that even after Karmic is out of testing as a genuine release, Empathy will still be there to ensure wider testing. So, my remark stands: this make being a tester on the final release an opt-out proposition. This is wrong and should never be the case.
You realize you have been "testing" pidgin before this debacle regardless of whether it was a final release or not.



> **qamelian said:**
> You love twisting peoples words, don't you? I make money by providing support to my clients (among other things), some of whom use Ubuntu, some Windows, some Mac OS. I have no need to fix the "bug" because we will not be using Empathy at all unless the state of the software changes. That is not the issue. **I don't care how many people actually *want* to use Empathy. That does not change the fact that it does not belong as the default IM in Karmic's final release. No little word games you play will change that.**
Ok, 
1. He quoted you, thats not twisting words. Its trying to get you to see what a moron you are.
2. Common courtesy towards you in my view is the wrong approach to take at this point.
3.Unfortunately you do not rule the world and if people want empathy(both users and developers) then empathy wins. Your job is support so do it instead of moaning about progression because your a lazy ***. 
 



> **qamelian said:**
> I've made my fair share of mistakes over the years and never claimed otherwise. That doesn't have any bearing on this discussion, other than to try to obfuscate the real issue.
The real issue is everything you say is subjective because you don't bother actually learning anything in life.



> **qamelian said:**
> Why do I even bother? Check any university level computer science text book. They're not that hard to discover.
You haven't bothered, not one bit.Your broad statements insinuate to me that you probably never went to university or at the very best dropped out. 
How about you prove you actually know what you are talking about instead of talking ****? You would rather bitch and moan on a forum and pretend you are better than everyone else when in reality you are tech support agent who wants the world to stop progressing so that you wont have to work. 
Stop being such a lazy *** and do your job. 
If I were your employer I would fire you.

---

### Post by steeleyuk on 2009-09-17
This is just getting stupid now... Empathy looks like its going to be default (barring some major reversal). Either live with it, install your preferred IM client or simply change distribution.

Most of this topic has been a pretty good read, regardless of whether you agree with each other. Probably best trying to keep it that way and leave out personal stuff that isn't relevant.

---

### Post by fluffman86 on 2009-09-17
> **tretle said:**
> Your an idiot.
Your a moron.

Your != You're

Just FYI.

Edit: I figure this thread NEEDS a grammar nazi.  :{P

---

### Post by tretle on 2009-09-17
Grammer nazi's are about as productive as this forum these days.

---

### Post by por100pre1 on 2009-09-17
Ok, I tried latest Empathy. It supports buddy icons, that's good. The only issue with it is that I can't setup hidden status correcty on MSN.

No problem now with Empathy as default, but I will continue using Pidgin.

---

### Post by zekopeko on 2009-09-17
> **qamelian said:**
> So a quantity of money indicates the level of common sense? This is nonsense.

The quantity of money indicates a level of developer interest in the feature since the developer is paid by the company which is in turn paid by clients for specific needs.


> I can, however, expect to have an informal discussion without being mocked. No foreknowledge of my condition should be necessary. Commoon courtesy dictates that.

Sorry, somebody calling somebody Magneto in jest isn't mocking. At the very least it's super awesome being compared to the biggest and most awesome bad guy in the X-Men universe.

> I was referring to remarks made by others that they want it in the Karmic release to ensure wider testing. That means that even after Karmic is out of testing as a genuine release, Empathy will still be there to ensure wider testing. So, my remark stands: this make being a tester on the final release an opt-out proposition. This is wrong and should never be the case.

You are missing the part where Empathy is only the GUI for the deeper things that power it, mainly Telepathy. Any software that has bugs (e.g. ALL of it) is always in testing when used. Empathy has a list of bugs that are going to be fixed by the time of the official release. Just because you miss one feature doesn't mean that it isn't feature complete for average users. Not to mention that upgrading is the officially supported method of moving from one release to another by Canonical and that in the upgrade you will not lose your beloved Pidgin. 

> You love twisting peoples words, don't you? I make money by providing support to my clients (among other things), some of whom use Ubuntu, some Windows, some Mac OS. I have no need to fix the "bug" because we will not be using Empathy at all unless the state of the software changes. That is not the issue. I don't care how many people actually *want* to use Empathy. That does not change the fact that it does not belong as the default IM in Karmic's final release. No little word games you play will change that.

So what is your problem if you are not going to be using the program? Because you have to provide support for installing pidgin by using the official method which doesn't remove pidgin?!

The only thing I hear from you is me,me,me,my clients. What about my poor mother that wants to use MSN/Jabber/GTalk AV? We haz no moneys for pricey Windows 7.

> I've made my fair share of mistakes over the years and never claimed otherwise. That doesn't have any bearing on this discussion, other than to try to obfuscate the real issue.

One would think that a person who made it's share of mistakes would have more understanding when other people make them (not that there was any to begin with).

> Why do I even bother? Check any university level computer science text book. They're not that hard to discover.

Do tell if some of those text books have a chapter on limited developer resources,client "wants" and acceptable regressions.

---

### Post by 23meg on 2009-09-17
I'm closing this thread. It's now devoid of its purpose, and has degenerated into various kinds of irresponsible and unproductive behavior. 

To recap:

[list][*] At the beginning of the Karmic cycle, during the Ubuntu Developer Summit, plans to replace Pidgin and Empathy were discussed and [a blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-messaging-and-communication-selection") was drafted and approved, according to which the final call regarding the suitability of Empathy would be made around Feature Freeze, according to feedback from testers.


[*] Empathy, after being tested via a PPA maintained with the participation of upstream developers, became the default IM application in Alpha 3. 


[*] As with pretty much every major change of defaults, many people found it unsuitable, mainly citing missing features. Discussions ensued on various forums and mailing lists.


[*] During the Karmic cycle, Empathy saw various improvements, part of which came from Ubuntu developers and designers.


[*] In [the Desktop Team meeting of September 15th]("https://lists.ubuntu.com/archives/ubuntu-desktop/2009-September/002263.html"), the call was made to go forward with the plan. Empathy will be the default IM client on new installs, and will also be offered in upgrades (as opposed to the initial plan), but Pidgin will not be removed during the upgrade. Empathy will offer to migrate Pidgin contacts on first run.


[*] Despite the improvements, some users remain unsatisfied with the decision, mainly due to missing features compared to Pidgin at present. [/list]


The constructive thing to do is set aside the default discussion, and see what we can do to help ship Empathy in the best form, with as few feature regressions and bugs as possible in Karmic. Let's do this in a new thread: [Missing Features in Empathy]("http://ubuntuforums.org/showthread.php?p=7965681").

---

### Post by zekopeko on 2009-09-17
> **por100pre1 said:**
> Ok, I tried latest Empathy. It supports buddy icons, that's good. The only issue with it is that I can't setup hidden status correcty on MSN.

No problem now with Empathy as default, but I will continue using Pidgin.

Search for bug and/or report a new one against telepathy-butterfly (better check if this is the correct library for MSN support).
If you do find an open bug report for your problem don't forget to provide info (Empathy version number and other libs that it uses) and click the "It affects me too" link to bump the bug in the list.

---

### Post by 23meg on 2009-09-17
I'm closing this thread. It's now devoid of its purpose, and has degenerated into various kinds of irresponsible and unproductive behavior. 

To recap:

[list][*] At the beginning of the Karmic cycle, during the Ubuntu Developer Summit, plans to replace Pidgin and Empathy were discussed and [a blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-messaging-and-communication-selection") was drafted and approved, according to which the final call regarding the suitability of Empathy would be made around Feature Freeze, according to feedback from testers.


[*] Empathy, after being tested via a PPA maintained with the participation of upstream developers, became the default IM application in Alpha 3. 


[*] As with pretty much every major change of defaults, many people found it unsuitable, mainly citing missing features. Discussions ensued on various forums and mailing lists.


[*] During the Karmic cycle, Empathy saw various improvements, part of which came from Ubuntu developers and designers.


[*] In [the Desktop Team meeting of September 15th]("https://lists.ubuntu.com/archives/ubuntu-desktop/2009-September/002263.html"), the call was made to go forward with the plan. Empathy will be the default IM client on new installs, and will also be offered in upgrades (as opposed to the initial plan), but Pidgin will not be removed during the upgrade. Empathy will offer to migrate Pidgin contacts on first run.


[*] Despite the improvements, some users remain unsatisfied with the decision, mainly due to missing features compared to Pidgin at present. [/list]


The constructive thing to do is set aside the default discussion, and see what we can do to help ship Empathy in the best form, with as few feature regressions and bugs as possible in Karmic. Let's do this in a new thread: [Missing Features in Empathy]("http://ubuntuforums.org/showthread.php?p=7965681").

---

