---
title: "Pidgin 2.6.0 with voice and video support"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ascii79 on 2009-08-18
Will pidgin 2.6 will be included 

[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

---

### Post by xens on 2009-08-18
damn great news!!! have to check if the ppa is up to date

---

### Post by nyarnon on 2009-08-18
still on 1.2.5.8 here.

---

### Post by Merk42 on 2009-08-18
> **nyarnon said:**
> still on 1.2.5.8 here.

1.2.5.8 of Pidgin? is there such a thing?
Also I don't see this getting updated in Jaunty.

Funny how voice/video was one of the arguments for Empathy over Pidgin, now Pidgin has it and Empathy still doesn't.

---

### Post by philinux on 2009-08-18
2.5.5 in Jaunty. Getdeb's latest version is 2.5.8

2.5.8 in Karmic packages.

They've put a 1. in front of it.

[http://packages.ubuntu.com/karmic/pidgin](http://packages.ubuntu.com/karmic/pidgin)

---

### Post by jfernyhough on 2009-08-18
1: means an epoc change. It's there to force an upgrade, IIRC.

---

### Post by hanzomon4 on 2009-08-18
This is great but I don't think this will help in regards to the switch to empathy-telepathy

---

### Post by andrewabc on 2009-08-18
As for original poster, yes pidgin will be update in repositories. As far as I know it will continue to be updated until mid september or so. Probably as long as it is before last alpha or shortly before beta stuff can be updated if important enough (make sure they know about it by filing a bug report).

---

### Post by olskar on 2009-08-18
Wow, with this empathy is even furter back in the race

---

### Post by rajeev1204 on 2009-08-18
Great news indeed.Its due to work done on voice/video in google SOC in 2008.Glad to see its made its way in.

---

### Post by JohnJackson on 2009-08-18
500 - Internal Server Error

Looks like we might've overloaded the server with our excitement

---

### Post by andrewabc on 2009-08-18
> **olskar said:**
> Wow, with this empathy is even furter back in the race

B-b-but the potential it has!

Seriously though, I think I can convert a friend from vista to ubuntu. And they use msn messenger (live or whatever new name). From what I can tell pidgin is much more closer to features than empathy which I've tested (won't connect to http msn for me).

---

### Post by andrewabc on 2009-08-18
> **JohnJackson said:**
> 500 - Internal Server Error

Looks like we might've overloaded the server with our excitement

They didn't even have 2.6.0 for windows built yet when I checked sourceforge. Just the sources/linux versions.

---

### Post by bear24rw on 2009-08-18
which video protocols does it support? it only mentions googles

---

### Post by JohnJackson on 2009-08-18
> **bear24rw said:**
> which video protocols does it support? it only mentions googles

Yes it looks like it's just Gtalk and XMPP (which are almost the same thing). Empathy has MSN video support in testing doesn't it?

---

### Post by Merk42 on 2009-08-18
> **andrewabc said:**
> They didn't even have 2.6.0 for windows built yet when I checked sourceforge. Just the sources/linux versions.

I refreshed the homepage and the download button now says 2.5.8 again, it earlier said 2.6.0. Also the under the word Pidgin, and the Yahoo comment still say 2.6.0

---

### Post by gnomeuser on 2009-08-18
> **olskar said:**
> Wow, with this empathy is even furter back in the race

how so, this is support for XMPP and nothing else.. meaning exactly the same support Empathy already has.

Wow, I'm so unimpressed it has only taken them 5 years to get to this point.

---

### Post by gnomeuser on 2009-08-18
> **JohnJackson said:**
> Empathy has MSN video support in testing doesn't it?

The last I heard the pymsn people had the code ready to merge, but this still means that telepathy-butterfly needs to present it to Empathy as well. It should however be coming soon.

So in honesty I think it's only fair to say that we might not have that specific feature in Karmic (but in a PPA by launch day I think we have a good chance).

---

### Post by Merk42 on 2009-08-18
> **gnomeuser said:**
> how so, this is support for XMPP and nothing else.. meaning exactly the same support Empathy already has.

I think the point is that "Empathy has audio/video support" is no longer an advantage over Pidgin.

---

### Post by | MM | on 2009-08-18
The change log says they now have a voice/video 'framework'.  Only gtalk supports voice/video at this point in Pidgin. It looks like they are maintaining feature parity with empathy.

But the shift to empathy is likely due to the desire to get the telepathy framework into Gnome/Ubuntu as it enhances the whole Gnome platform in ways not yet realised.

---

### Post by plun on 2009-08-18
Tried to build it but it seems to be broken

```
plun@plun-laptop:~/src/pidgin-2.6.0$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_theme_loader_get_type

```

:---)

---

### Post by jpeddicord on 2009-08-18
> **| MM | said:**
> But the shift to empathy is likely due to the desire to get the telepathy framework into Gnome/Ubuntu as it enhances the whole Gnome platform in ways not yet realised.

This.


As for Pidgin, 2.6.0 will probably be available in the archives (it's not yet feature freeze) but Empathy will remain the new default.

---

### Post by plun on 2009-08-18
Pidgin wiki about this


[http://developer.pidgin.im/wiki/vv](http://developer.pidgin.im/wiki/vv)


Howto build
[http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo](http://developer.pidgin.im/wiki/GSoC2008/VoiceAndVideo)

---

### Post by philinux on 2009-08-18
I'm not an expert in voice video stuff can someone explain in plain English what this all means?

My main contacts use msn and I would like to use my webcam properly. Kopete failed as no voice support.

---

### Post by JohnJackson on 2009-08-18
> **plun said:**
> Tried to build it but it seems to be broken

```
plun@plun-laptop:~/src/pidgin-2.6.0$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_theme_loader_get_type

```

:---)

It builds for me and I can run it from the pidgin directory (without running make install) but it doesn't recognise my accounts, neither can I add any accounts as there are no protocols. I guess I need to do something in the configure script?

Edit: Guess I needed to install it :p

> **philinux said:**
> I'm not an expert in voice video stuff can someone explain in plain English what this all means?

My main contacts use msn and I would like to use my webcam properly. Kopete failed as no voice support.

There is no video support for MSN. Audio clips and handwriting is now supported though.

---

### Post by Tibuda on 2009-08-18
I wonder if this release has something to do with Ubuntu choosing Empathy for karmic...

---

### Post by JohnJackson on 2009-08-18
I have it installed - no idea how to initiate a Gtalk video or voice session though. As for MSN, there don't seem to be any GUI controls for sending handwritten messages or sending audio clips. Looking at the wording of the changelog you can only receive them.

---

### Post by nhasian on 2009-08-18
*Right Now* if you want to video chat with people using MSN messenger, you can use amsn in the repos.  thats the only way i know right now, but by the time Karmic is released empathy will have msn video conferencing as well.

now if we can get skype working with 64bit karmic we will be in good shape.

---

### Post by Merk42 on 2009-08-18
> **nhasian said:**
> *Right Now* if you want to video chat with people using MSN messenger, you can use amsn in the repos.  thats the only way i know right now, but by the time Karmic is released empathy will have msn video conferencing as well.

now if we can get skype working with 64bit karmic we will be in good shape.

Skype works fine for me in Jaunty, was there a regression?

---

### Post by zanglang on 2009-08-19
> **danielrmt said:**
> I wonder if this release has something to do with Ubuntu choosing Empathy for karmic...

Sounds logical. VV has been brought up/promised/implemented/dumped way more times than we can count now.

Isn't VV still disabled in Karmic Empathy, though?

---

### Post by Swarms on 2009-08-19
Haha it is so visible why the Pidgin developers 5 years later all of sudden include support. They are scared of being removed from Ubuntu.
Competition has been great for the IM scene of Ubuntu.

And of course we should stick to Empathy.

---

### Post by Tibuda on 2009-08-19
[John Bailey blogged about it]("http://theflamingbanker.blogspot.com/2009/08/pidgin-260-its-about-time.html") in [Pidgin planet]("http://planet.pidgin.im/"). They have also [released 2.6.1]("http://developer.pidgin.im/wiki/ChangeLog").

> 
Voice and Video support - Thanks to Mike Ruprecht and his Summer of Code project from 2008, libpurple now has a voice and video framework that can be used to add these features to our protocol plugins. Currently we support these features only on XMPP, but Mike is working on other protocols as I write this and hopes to have more protocols at least partially supported soon. The dependencies are a bit of a mess for the uninitiated, but unfortunately that's unavoidable. I'm hoping most distributions will be able to catch up with this soon and make it completely effortless for users, but this is a headache even for some distributions. The biggest setback thus far is we're currently not able to support these features on Windows--but we're working on it! Please be patient!

---

### Post by ELD on 2009-08-19
It does seem a little strange that code from a year ago suddenly gets dropped in, pidgin is not that big a program so anything they say about it taking time is a load of balls. It is blatently because of Ubuntu dropping it.

Although i am glad they finally put the framework in and with the voice clips and handwriting for msn both are very welcome additions. Either way the IM scene has just pushed forwards a good deal, i am happy this has happend :D

---

### Post by rajeev1204 on 2009-08-19
> **gnomeuser said:**
> how so, this is support for XMPP and nothing else.. meaning exactly the same support Empathy already has.

Wow, I'm so unimpressed it has only taken them 5 years to get to this point.


Your bias is so obvious.Pidgin never promised any video /voice timeline as is very obvious from their wiki.Main devs never felt this feature a priority.I dont know where you got the 5 years info from.

This has been possible from the GSOC project.So finally they got it into pidgin.Some competition is always good of course.

You seem to have a personal problem with the pidgin devs surely.If you support empathy thats nice, no need of sarcasm for other open source projects.

The gsoc project can be used for any other IM also using libpurple i believe.

So whether you like it or not, apart from firefox and open office,pidgin is one of the best open source cross-platform applications that exist.

---

### Post by Tibuda on 2009-08-19
> **rajeev1204 said:**
> The gsoc project can be used for any other IM also using libpurple i believe.

Yes, ["libpurple now has a voice and video framework that can be used to add these features to our protocol plugins"]("http://theflamingbanker.blogspot.com/2009/08/pidgin-260-its-about-time.html"). It looks like they only have to work now with the protocol-specific coding.

I am also excited about the new theming features. I hope it uses (X)HTML/CSS. I can't wait to start working with it.

---

### Post by Bou on 2009-08-19
> **nhasian said:**
> by the time Karmic is released empathy will have msn video conferencing as well.

Is that so? :confused:

---

### Post by rajeev1204 on 2009-08-19
> **ELD said:**
> It does seem a little strange that code from a year ago suddenly gets dropped in, pidgin is not that big a program so anything they say about it taking time is a load of balls. It is blatently because of Ubuntu dropping it.

Although i am glad they finally put the framework in and with the voice clips and handwriting for msn both are very welcome additions. Either way the IM scene has just pushed forwards a good deal, i am happy this has happend :D


Nothing strange about it,the code was available since a year before,testers had trouble getting pidgin to compile and/or run with voice/video support.You can check the pidgin wiki pages for this.Also, voice/video as we know is very difficult to implement as such,and just because libpurple had the code doesnt mean it can be dragged and dropped into pidgin just like that.

1 year seems good enough to get this feature then doesnt it?

Next step, msn video and voice + yahoo :D


rajeev

---

### Post by ELD on 2009-08-19
I can see where you are coming from to a point, but even much more basic IM programs had at least receiving webcams working really, really well like amsm and mecury for examples.

Either way lets not bitch and moan, it is here that is the main thing :D

---

### Post by rajeev1204 on 2009-08-19
> **ELD said:**
> I can see where you are coming from to a point, but even much more basic IM programs had at least receiving webcams working really, really well like amsm and mecury for examples.

Either way lets not bitch and moan, it is here that is the main thing :D


Amsn was a project aimed specifically to get msn on linux with all features, so it was one of their goals,not so with pidgin or probably empathy even.Pidgin's goal was IM with all protocols with video/voice support added when they have time or resources or motivation.

Iam a little sad that all clients like pidgin and empathy are supporting msn video/voice and not yahoo,since in india,we use yahoo for this.MSN is not common at all.But frankly,i use skype for this.

So i guess,everyone can stop moaning and rejoice :).Good news indeed for pidgin users.I hope all protocols get implemented soon in pidgin/empathy etc.

Also,amsn would be good with voice support.Looking at someone using amsn and hearing his voice on phone is really funny :D

---

### Post by joey-elijah on 2009-08-19
Just to chip in that Emesne 1.5 (NOT the one in the repos) has had MSN Webcam support for a little while now, too. It's pretty good. 

I'm pleased Pidgin has started actually implementing the somewhat "basic" features of an IM client. WHat with the news about themeing, too, i may actually be able to use Pidgin for once!

---

### Post by Matyy on 2009-08-19
It's on getdeb - but without video support. Is it possible to compile it?

---

### Post by JarekMk on 2009-08-19
Ehh why? ;/

---

### Post by kestal on 2009-08-19
> **joey-elijah said:**
> Just to chip in that Emesne 1.5 (NOT the one in the repos) has had MSN Webcam support for a little while now, too. It's pretty good.

I do like Emesene, however, I had some contact list syncing problems the last time I tried it. Has this been fixed?

Also, Galaxium is doing pretty well, aside for, at this very moment, the lack of development. Its a bit of a shame, too, as I could see Galaxium helping people with the transition, especially 0.8.

---

### Post by mrgnash on 2009-08-19
The Pidgin team also have their own PPA, which I assume features Pidgin built with audio/video support. 

I find it funny that people are complaining that Empathy and Pidgin "only" support XMPP/Google Talk as far as audio/video are concerned. XMPP is precisely the protocol that needs to be embraced by the FOSS community, since it is the only one that adheres to its standards. Anyway, /rant this is great news.

---

### Post by fr34k_0/\/_4_1345l-l on 2009-08-19
wait, wait, wait, pidgin actually,really has voice and video support at last??

---

### Post by ghindo on 2009-08-19
> **fr34k_0/\/_4_1345l-l said:**
> wait, wait, wait, pidgin actually,really has voice and video support at last??Read the thread.  Only for XMPP.

---

### Post by fr34k_0/\/_4_1345l-l on 2009-08-19
> **ghindo said:**
> Read the thread.  Only for XMPP.

rofl. oh man x]

---

### Post by andrewabc on 2009-08-19
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
Pidgin ppa only has 2.5.8 so far. Probably take a couple days to update

[This PPA is maintained by one developer, so please be patient. It often lags behind the source releases a couple of days.](http://www.pidgin.im/download/ubuntu/)

---

### Post by khc on 2009-08-20
> **danielrmt said:**
> I wonder if this release has something to do with Ubuntu choosing Empathy for karmic...

Consider that this was code from GSoC 2008 and the project was picked in April 2008...

---

### Post by hanzomon4 on 2009-08-20
> **khc said:**
> Consider that this was code from GSoC 2008 and the project was picked in April 2008... 

When was empathy made gnome default? Was pidgin ever in the default gnome

---

### Post by kingborel on 2009-08-20
> **hanzomon4 said:**
> When was empathy made gnome default? Was pidgin ever in the default gnome

Pidgin was default up until about 8 weeks ago ;)

---

### Post by 23meg on 2009-08-20
> **kingborel said:**
> Pidgin was default up until about 8 weeks ago ;)

No, Pidgin has never been part of GNOME. 

Empathy has been in GNOME since GNOME 2.24 (September 2008).

---

### Post by covenguardian on 2009-08-20
> **plun said:**
> Tried to build it but it seems to be broken

```
plun@plun-laptop:~/src/pidgin-2.6.0$ pidgin
pidgin: symbol lookup error: pidgin: undefined symbol: purple_theme_loader_get_type

```:---)

just type "sudo ldconfig" in terminal

---

### Post by teolemon on 2009-08-20
[http://stemp.wordpress.com/2009/08/20/pidgin-2-6-1-audiovideo/](http://stemp.wordpress.com/2009/08/20/pidgin-2-6-1-audiovideo/)
Here are the DEBs with video activated

---

### Post by shakaran on 2009-08-20
Guys, we need more cowbell!

Gimp 2.7, Pidgin 2.6.1, Firefox 3.6, more and more cowbell!

---

### Post by dumblebee100 on 2009-08-20
anyways I dont need any of these ...bcz when I tried to add google talk account pidgin segfaults ...

---

### Post by evuraan on 2009-08-20
> **ghindo said:**
> Read the thread.  Only for XMPP.

Wait, whats this hype for then? With this pidgin 2.6 thingy, you still can't do audio/vido on gtalk. Which leaves me wondering:

What's this good for? Absolutely nothing, yet? :guitar: heheh

:P

---

### Post by khc on 2009-08-20
> **evuraan said:**
> Wait, whats this hype for then? With this pidgin 2.6 thingy, you still can't do audio/vido on gtalk. Which leaves me wondering:

What's this good for? Absolutely nothing, yet? :guitar: heheh

:P

gtalk uses xmpp

---

### Post by evuraan on 2009-08-21
> **khc said:**
> gtalk uses xmpp

right. except  i dont see how to use voice on gtalk despite running Pidgin 2.6.1 - :confused:

[IMG]http://24.16.26.121/screenshots/images/1250828308.jpg[/IMG]

The closest I could find is [this comment]("http://webupd8.blogspot.com/2009/08/pidgin-260-adds-voice-and-video.html#comment-15058733") hinting the goodies for voice are not yet in place.

---

### Post by martijntje on 2009-08-21
You cannot use it yet. They have built support for it now in libpurple, but they still have to make the interface for it.

---

### Post by hellmet on 2009-08-21
Oh .. crap. What was all the hoolah about then?

---

### Post by ELD on 2009-08-21
> **martijntje said:**
> You cannot use it yet. They have built support for it now in libpurple, but they still have to make the interface for it.

You gotta be kidding me? So they made so big hooha about it being included a year after having the code, yet they don't put in a way for us to use it? Lame.

---

### Post by martijntje on 2009-08-21
They haven't created an interface for it *yet*. They have done the first step, however, by having libpurple support. Because without that, they can build all the interfaces they want, it's not going to work ;) .

---

### Post by lean on 2009-08-21
So... How can you set up your own xmmp server with jingle support?
I already have a jabber server and it is great, but if my contacts could route voice through it, it would be even greater :D

---

### Post by 23meg on 2009-08-21
[QUOTE=ELD]they made so big hooha about it being included[/QUOTE]

[COLOR="Navy"][citation needed][/COLOR]

---

### Post by 243kof on 2009-08-21
> **martijntje said:**
> They haven't created an interface for it *yet*. They have done the first step, however, by having libpurple support. Because without that, they can build all the interfaces they want, it's not going to work ;) .

Look here: [http://news.softpedia.com/news/Pidgin-2-6-0-Has-Voice-and-Video-Support-119557.shtml]("http://news.softpedia.com/news/Pidgin-2-6-0-Has-Voice-and-Video-Support-119557.shtml")

The screenshot in there indicates that they HAVE an interface. I'm guessing it's a matter of having the right libraries installed. Apparently, very few people currently have :confused:

---

### Post by rajeev1204 on 2009-08-21
> **hellmet said:**
> Oh .. crap. What was all the hoolah about then?

voice/video in XMPP support is implemented ,that means it works with gtalk for voice,and with the gmail web interface for voice /video.

And for those who dont have a clue yet, google uses the XMPP protocol.

There is no hoolah being made by the pidgin devs, its the thread title which has been interpreted by you as such,

[www.pidgin.im](www.pidgin.im)

---

### Post by Matyy on 2009-08-21
[http://stemp.wordpress.com/2009/08/20/pidgin-2-6-1-audiovideo/](http://stemp.wordpress.com/2009/08/20/pidgin-2-6-1-audiovideo/)

that's how you can install it (For Englih scroll a bit down). But I have noone to test it. Audio/video call are always greyed out - but I guess that's because most of my xmmp using friends are using 2.5 or 2.6.1 withouth audio/video.

---

### Post by rajeev1204 on 2009-08-21
It should soon be into karmic i suppose.Along with the required libs.

I have a question though, with empathy being default, have they moved pidgin to universe now?

---

### Post by puccaso on 2009-08-21
mmm i posted a post, but i cant see it now? 
so i'll repeat, 

i am getting a libzephyr3 error...

---

### Post by 23meg on 2009-08-21
> **rajeev1204 said:**
> I have a question though, with empathy being default, have they moved pidgin to universe now?

[No, it's in main]("http://packages.ubuntu.com/karmic/pidgin"). The plan laid out at UDS included keeping Pidgin in upgrades to Karmic (I can't find a source to confirm if that's still the plan now; will ask), which means Empathy will only be default in new installations. That alone requires keeping Pidgin in main.

---

### Post by rajeev1204 on 2009-08-21
> **23meg said:**
> [No, it's in main]("http://packages.ubuntu.com/karmic/pidgin"). The plan laid out at UDS included keeping Pidgin in upgrades to Karmic (I can't find a source to confirm if that's still the plan now; will ask), which means Empathy will only be default in new installations. That alone requires keeping Pidgin in main.

Ok thank you.Maybe new users should be notified about a new default application available for install when they upgrade. hmm not sure how that will be implemented though.

Ya , during upgrade a question maybe to the user to select either IM sounds good?

---

### Post by 23meg on 2009-08-21
[QUOTE=rajeev1204]Maybe new users should be notified about a new default application available for install when they upgrade.[/QUOTE]

Someone who's upgrading is almost certainly not a new user.

[QUOTE=rajeev1204]Ya , during upgrade a question maybe to the user to select either IM sounds good?[/QUOTE]

Doesn't sound good to me. It's not a question most users will be qualified to answer at upgrade time. Most users won't be able to tell without having to do research why they might want "Empathy" over "Pidgin". It also conflicts with [https://wiki.ubuntu.com/UbuntuArchitecture](https://wiki.ubuntu.com/UbuntuArchitecture).

---

### Post by fab.head on 2009-08-21
> **Matyy said:**
> [http://stemp.wordpress.com/2009/08/20/pidgin-2-6-1-audiovideo/](http://stemp.wordpress.com/2009/08/20/pidgin-2-6-1-audiovideo/)

that's how you can install it (For Englih scroll a bit down). But I have noone to test it. Audio/video call are always greyed out - but I guess that's because most of my xmmp using friends are using 2.5 or 2.6.1 withouth audio/video.

I've just tested this version in Jaunty, but it doesn't seem work (missing libraries?)
I've simply installed GoogleTalk on another PC with WindowsXP and logged in GTalk with a different user.

1. If I call from GTalk, then Pidgin crashes.

2. If I call from Pidgin, I get the following error message:

> 
[B][COLOR="Red"](14:31:10) Error creating session: Could not create the rtp muxer element

(14:31:10) Error adding stream.[/COLOR]
(14:31:10) The call has been terminated.[/B]



I'll test it in Karmic later today

---

### Post by rajeev1204 on 2009-08-21
> **23meg said:**
> Someone who's upgrading is almost certainly not a new user.



Doesn't sound good to me. It's not a question most users will be qualified to answer at upgrade time. Most users won't be able to tell without having to do research why they might want "Empathy" over "Pidgin". It also conflicts with [https://wiki.ubuntu.com/UbuntuArchitecture](https://wiki.ubuntu.com/UbuntuArchitecture).

Those are slightly contradictory statements.But my point is,let it be an option for users who are aware of the change,but dont want the installer to go ahead and install pidgin or empathy or vice-versa, and provide an option to select which im they prefer.

But thanks for that ubuntu architecture link,its clear in point number one from design principle 

> There should be exactly one recommended way to accomplish a task in the default installation, to promote consistent documentation and support

I stand corrected.And your point is noted and taken.


P.S.Can someone for god's sake explain me how to multiquote.#-o

---

### Post by 23meg on 2009-08-21
[QUOTE=rajeev1204]Those are slightly contradictory statements.[/QUOTE]

Why?

[QUOTE=rajeev1204]But my point is,let it be an option for users who are aware of the change,but dont want the installer to go ahead and install pidgin or empathy or vice-versa, and provide an option to select which im they prefer.[/QUOTE]

It *is* already an option for them: people who know clearly that they want Pidgin over Empathy, or vice versa, and why, can be assumed to know, or in the worst case, easily discover how to uninstall the one they don't want and install the one they want. The option doesn't have to be advertised during an upgrade, at the cost of inconsistency with design principles and more disruptive and mostly irrelevant questions, leading to a worse experience for the uninitiated user.

[QUOTE=rajeev1204]But thanks for that ubuntu architecture link,[/QUOTE]

You're welcome, and please share it when the context arises.

---

### Post by rajeev1204 on 2009-08-21
> **23meg said:**
> Why?



Aah nvm now :).

---

### Post by outphase on 2009-08-21
> **fab.head said:**
> I've just tested this version in Jaunty, but it doesn't seem work (missing libraries?)
I've simply installed GoogleTalk on another PC with WindowsXP and logged in GTalk with a different user.

1. If I call from GTalk, then Pidgin crashes.

2. If I call from Pidgin, I get the following error message:




I'll test it in Karmic later today
I installed all of the necessary packages via that site as well. #2 happens the same for me. #1 I managed to get it to know it's receiving a call, but it never connects. Eventually someone using the Gmail client quits out.

---

### Post by hellmet on 2009-08-21
> **rajeev1204 said:**
> voice/video in XMPP support is implemented ,that means it works with gtalk for voice,and with the gmail web interface for voice /video.

And for those who dont have a clue yet, google uses the XMPP protocol.

There is no hoolah being made by the pidgin devs, its the thread title which has been interpreted by you as such,

[www.pidgin.im](www.pidgin.im)
Well, I was referring to all these threads on these and other forums about this and to the devs. Full respect to the devs!

---

### Post by elitenoobboy on 2009-08-21
It's nice to see pidgin is finally getting with the times and starting to implement some of this stuff. Not having video or voice chat was one of the primary reasons for switching to empathy, wasn't it? Also, does empathy even have a way to import chat logs from pidgin yet (and not just accounts)? I can't imagine anyone wanting to switch without that.

---

### Post by Swarms on 2009-08-21
> **elitenoobboy said:**
> It's nice to see pidgin is finally getting with the times and starting to implement some of this stuff. Not having video or voice chat was one of the primary reasons for switching to empathy, wasn't it? Also, does empathy even have a way to import chat logs from pidgin yet (and not just accounts)? I can't imagine anyone wanting to switch without that.

Not really. Empathy uses the Telepathy framework which makes some cool stuff with integration between apps possible.

For example, share your music directly with a contact, or browse and experience his library.

---

### Post by Bios Element on 2009-08-22
> **elitenoobboy said:**
> It's nice to see pidgin is finally getting with the times and starting to implement some of this stuff. Not having video or voice chat was one of the primary reasons for switching to empathy, wasn't it? Also, does empathy even have a way to import chat logs from pidgin yet (and not just accounts)? I can't imagine anyone wanting to switch without that.

There were many reasons, that being just one. And there has been chat long import for as long as I've tested empathy which is over 6-some months. And you won't switch without chat log importing? Ever hear of copy/paste? >.>

---

### Post by Nyoro on 2009-08-22
> **Merk42 said:**
> 1.2.5.8 of Pidgin? is there such a thing?
Also I don't see this getting updated in Jaunty.

Funny how voice/video was one of the arguments for Empathy over Pidgin, now Pidgin has it and Empathy still doesn't.


Even more funny that this code has been lying around for about 1 year, then now when empathy threathens Pidgins place in Gnome, the devs finally turns around and implement it.

---

### Post by nhasian on 2009-08-22
oh my god, is that a quote from the Saturday Night Live with christopher walken?  :lolflag:

> **shakaran said:**
> Guys, we need more cowbell!

Nyoro, the application amsn has had video conferencing for msn messenger protocol for a long time.  how come neither pidgin nor empathy have incorporated it up till now?

> **Nyoro said:**
> Even more funny that this code has been lying around for about 1 year, then now when empathy threathens Pidgins place in Gnome, the devs finally turns around and implement it.

---

### Post by Nyoro on 2009-08-22
> **nhasian said:**
> 
Nyoro, the application amsn has had video conferencing for msn messenger protocol for a long time.  how come neither pidgin nor empathy have incorporated it up till now?

It sounds a bit like you're implying something with that question, please spell it out if so.

In the meantime I will try to answer your question. Pidgin and aMSN have been in development far longer time than empathy. To be fair, afaik aMSN has been focussed on 1 protocol, and on mimicking MSN messenger as close as possible. Such a single target project is probably quicker to carry out.

Besides, the Pidgin devs' attitude towards people asking for video/voice support has ranged from arrogant refusal, to non-forthcoming answers like "I don't use a web cam, I don't know anyone who does, hence I don't think it's important, go ahead and make a patch and *maybe* we wont turn it down flatly.". Based on this attitude, it *is* funny to see the project turning around.

The attitude I describe (towards users and towards possible contributors) is exactly what makes me not wanna help spread Pidgin to the world.

---

### Post by Stemp on 2009-08-22
> **fab.head said:**
> (14:31:10) Error creating session: Could not create the rtp muxer element

(14:31:10) Error adding stream.
(14:31:10) The call has been terminated.


rtpmux is in the gstreamer0.10-plugins-bad package, i will add it to the dependencies ;)

---

### Post by fab.head on 2009-08-22
> **Stemp said:**
> rtpmux is in the gstreamer0.10-plugins-bad package, i will add it to the dependencies ;)

I have the **gstreamer0.10-plugins-bad** package installed, therefore I shouldn't be getting that error message...

---

### Post by Stemp on 2009-08-22
> **fab.head said:**
> I have the **gstreamer0.10-plugins-bad** package installed, therefore I shouldn't be getting that error message...

Could you test with farsight2 0.0.14 ? 
[libgstfarsight0.10 0.0.14 amd64]("https://edge.launchpad.net/~stemp/+archive/ppa/+files/libgstfarsight0.10-0_0.0.14-0~jjamsn1_amd64.deb")
[libgstfarsight0.10 0.0.14 i386]("https://edge.launchpad.net/~stemp/+archive/ppa/+files/libgstfarsight0.10-0_0.0.14-0~jjamsn1_i386.deb")

If it doesn't work maybe Pidgin need Farsight1 librairies (there is a rtpmuxer there).
[gstreamer0.10-plugins-farsight 0.12.11 amd64]("https://edge.launchpad.net/~amsn-daily/+archive/ppa/+files/gstreamer0.10-plugins-farsight_0.12.11-1~jjamsn1_amd64.deb")
[gstreamer0.10-plugins-farsight 0.12.11 i386]("https://edge.launchpad.net/~amsn-daily/+archive/ppa/+files/gstreamer0.10-plugins-farsight_0.12.11-1~jjamsn1_i386.deb")

---

### Post by shakaran on 2009-08-22
> **nhasian said:**
> oh my god, is that a quote from the Saturday Night Live with christopher walken?  :lolflag:


Yep, good catch!

---

### Post by fab.head on 2009-08-22
> **Stemp said:**
> Could you test with farsight2 0.0.14 ? 
[libgstfarsight0.10 0.0.14 amd64]("https://edge.launchpad.net/~stemp/+archive/ppa/+files/libgstfarsight0.10-0_0.0.14-0~jjamsn1_amd64.deb")
[libgstfarsight0.10 0.0.14 i386]("https://edge.launchpad.net/~stemp/+archive/ppa/+files/libgstfarsight0.10-0_0.0.14-0~jjamsn1_i386.deb")

No luck...


> **Stemp said:**
> 
If it doesn't work maybe Pidgin need Farsight1 librairies (there is a rtpmuxer there).
[gstreamer0.10-plugins-farsight 0.12.11 amd64]("https://edge.launchpad.net/~amsn-daily/+archive/ppa/+files/gstreamer0.10-plugins-farsight_0.12.11-1~jjamsn1_amd64.deb")
[gstreamer0.10-plugins-farsight 0.12.11 i386]("https://edge.launchpad.net/~amsn-daily/+archive/ppa/+files/gstreamer0.10-plugins-farsight_0.12.11-1~jjamsn1_i386.deb")

If I install the Farsight1 libraries, it uninstalls **ubuntu-desktop** and **gstreamer0.10-plugins-bad**. 
I did it, but still no luck... (then I just reverted the changes)

Anyway, I've just noticed that the Pidgin devs are updating the ppa right now, therefore I hope that soon all the necessary dependencies will be available.

We just need a bit of patience :)

---

### Post by 243kof on 2009-08-23
I updated pidgin through the ppa, installed all the dependencies (I'm on Jaunty). Although options for audio/video call now appear, they don't work. When a gmail contact tries to call me, Pidgin crashes. When I try to call him, it outputs an error:

> (01:07:34 PM) Error creating session: Could not create the valve element

(01:07:34 PM) Error adding stream.
(01:07:34 PM) The call has been terminated.

Could this somehow be related to Google updating its voice and video software on Thursday? [http://juberti.blogspot.com/]("http://juberti.blogspot.com/")

Edit: Sorry, I just noticed this thread is in Karmic Discussion forum.

---

### Post by abhiroopb on 2009-08-23
Just to let you guys know. I installed Pidgin 2.6.1 (through the pidgin dev PPA) and all the required libraries were updated/installed. 

The Audio/Video chat worked great with a friend using a Mac. Not as clear as skype but definitely a good alternative for me.

---

### Post by fab.head on 2009-08-23
> **fab.head said:**
> I've just tested this version in Jaunty, but it doesn't seem work (missing libraries?)
I've simply installed GoogleTalk on another PC with WindowsXP and logged in GTalk with a different user.

1. If I call from GTalk, then Pidgin crashes.

2. If I call from Pidgin, I get the following error message:

> 
[B][COLOR="Red"](14:31:10) Error creating session: Could not create the rtp muxer element

(14:31:10) Error adding stream.[/COLOR]
(14:31:10) The call has been terminated.[/B]


I'll test it in Karmic later today

I googled for "Could not create the rtp muxer element" and I found the solution here:
[http://www.amsn-project.net/forums/viewtopic.php?t=6622]("http://www.amsn-project.net/forums/viewtopic.php?t=6622")

You just need to remove the .gstreamer-0.10 directory in home and everything starts working. :)

---

### Post by fab.head on 2009-08-23
New issue:

1. Pidgin calls GTalk (on WinXP) **[COLOR="Blue"]>[/COLOR]** GTalk displays "Incoming call" **[COLOR="Blue"]>[/COLOR]** GTalks answers the call **[COLOR="Blue"]=[/COLOR]** the audio conversation starts, all fine

2. GTalk calls Pidgin **[COLOR="Blue"]>[/COLOR]** Pidgin displays "xyz wishes to start an audio session with you" **[COLOR="Blue"]>[/COLOR]** Pidgins answers the call (Accept) **[COLOR="Blue"]=[/COLOR]** the audio conversation does not start (GTalk thinks that Pidgin is not answering while Pidgin shows the "call in progress" window)

I've tested the above under Jaunty and Karmic.

Any tip?

---

### Post by crjackson on 2009-08-23
> **ascii79 said:**
> Will pidgin 2.6 will be included 

[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog)

I can't actually read that link (it's blocked on my network), but I''m using 2.6.1 right now, and I don't see any settings for voice / video support.

Am I missing something here?

---

### Post by kevdog on 2009-08-23
crjackson

You installed from source or from ppa?

---

### Post by crjackson on 2009-08-23
> **kevdog said:**
> crjackson

You installed from source or from ppa?

[http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin")

---

### Post by fab.head on 2009-08-24
> **crjackson said:**
> [http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin")

The version on [www.getdeb.net](www.getdeb.net) has voice/video support disabled.
> 
 ***No voice/video support***
 By **korn**, 2009-08-19 13:48:17

This voice/video support in this version is disabled because jaunty does not provide the required library versions. 


Please add the following PPA to your software sources to download ver.2.6.1 with voice/video enabled: **[http://pidgin.im/download/ubuntu/]("http://pidgin.im/download/ubuntu/")**

---

### Post by kevdog on 2009-08-24
Is it easy  to make a PPA?  Ive compiled 2.6.2 on Intrepid with voice and video support.  The current PPA is for jaunty.  I'm really not sure why the ppa couldn't be installed on previous versions b/c all it contains is gstreamer libs and packages, libnice, farsight2, and pidgin -- no kernel stuff that I am aware of.  Anyway I wanted to prove that voice and video could run in something other than Jaunty and Karmic.  People are making a lot of claims stating this to be true!!

---

### Post by shakaran on 2009-08-24
> **kevdog said:**
> Is it easy  to make a PPA?  Ive compiled 2.6.2 on Intrepid with voice and video support.  The current PPA is for jaunty.  I'm really not sure why the ppa couldn't be installed on previous versions b/c all it contains is gstreamer libs and packages, libnice, farsight2, and pidgin -- no kernel stuff that I am aware of.  Anyway I wanted to prove that voice and video could run in something other than Jaunty and Karmic.  People are making a lot of claims stating this to be true!!

Yeah, make a PPA is easy! You only need read a little!
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by fab.head on 2009-08-24
> **kevdog said:**
> Is it easy  to make a PPA?  Ive compiled 2.6.2 on Intrepid with voice and video support.  The current PPA is for jaunty.  I'm really not sure why the ppa couldn't be installed on previous versions b/c all it contains is gstreamer libs and packages, libnice, farsight2, and pidgin -- no kernel stuff that I am aware of.  Anyway I wanted to prove that voice and video could run in something other than Jaunty and Karmic.  People are making a lot of claims stating this to be true!!

2.6.2 ?

Is there a new update?
The Pidgin site only mentions 2.6.1

---

### Post by JohnJackson on 2009-08-24
Is it just me, or do other people get disconnected from MSN multi-user chats quite often?

After about 2 minutes of inactivity it seems I can't send messages. Do not remember it happening in 2.5.

Anyone else?

---

### Post by kevdog on 2009-08-24
2.6.2 is the monotone version.  As I'm taking a look at the future while the rest of you mere measlings are using 2.6.1 -- I can proclaim -- I don't really notice anything different.  Are you satisfied??

On a serious note -- why are my voice and video options always greyed out?

And yes I was able to compile for intrepid.  Can I offer a PPA?

---

### Post by Stemp on 2009-08-25
> **kevdog said:**
> On a serious note -- why are my voice and video options always greyed out?

And yes I was able to compile for intrepid.  Can I offer a PPA?

Do you mean voice and video options are greyed out on Intrepid ?

Because as far as I know, there is no Farsight2 packages for Intrepid (libgstfarsight), so audio and video cannot work.

---

### Post by kevdog on 2009-08-25
I just compiled the farsight2 libraries on intrepid. (along with all the gstreamer packages, nice, and theora -- The collection of dependencies was a royal pain!  I don't think I'm going to be writing up the method since it took a long time.  Pidgin wa compiled from the monotone developer tree -- currently 2.6.2 -- this is equal to the svn/cvs build if people don't know what monotome describes.

Last night I hooked up with another user running pidgin 2.6.0 from ppa repository and I was running 2.6.2 from source compilation.  The options were no longer "greyed" out.  We tried initiating an audio only call, but on both ends, we only got audio for at most 1 second -- call it a static rush and then nothing.

In my 2.6.2 build I have an option under tools->Plugins->voice and video where it allows to select the input and output devices for both audio (in one tab) and video (in a second tab).  The choices for audio were ALSA, OSS, TEST, Default.  There was no such dialog box on the 2.6.0 build.

Is this normal?

---

### Post by Mr.Carramba on 2009-08-26
> **fab.head said:**
> The version on [www.getdeb.net]("http://www.getdeb.net") has voice/video support disabled.


Please add the following PPA to your software sources to download ver.2.6.1 with voice/video enabled: **[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)**


I reinstalled pidgin using this link but I have no video or audio suport.
why it is so? using 9.04

---

### Post by fab.head on 2009-08-26
> **Mr.Carramba said:**
> I reinstalled pidgin using this link but I have no video or audio suport.
why it is so? using 9.04

Double-click a contact to open a conversation window.

Then **Conversation** > **Media** > **Audio call** or **Video Call** or **Audio/Video Cal**l

---

### Post by Mr.Carramba on 2009-08-26
> **fab.head said:**
> Double-click a contact to open a conversation window.

Then **Conversation** > **Media** > **Audio call** or **Video Call** or **Audio/Video Cal**l

Audio call or Video call are gray and not clickable.

---

### Post by fab.head on 2009-08-26
> **Mr.Carramba said:**
> Audio call or Video call are gray and not clickable.

They become available only if you and the contact you want to call both use XMPP accounts (for example GoogleTalk)

---

### Post by Mr.Carramba on 2009-08-26
> **fab.head said:**
> They become available only if you and the contact you want to call both use XMPP accounts (for example GoogleTalk)

oh, so it will not work to have video for msn?

---

### Post by BCurtisWX on 2009-08-26
Empathy is actually doing better than pidgin... we should take note of this

---

### Post by Tibuda on 2009-08-26
> **Mr.Carramba said:**
> oh, so it will not work to have video for msn?

Not right now. Only XMPP/Jabber/Google is implemented, but the [new Emesene 1.5]("http://www.emesene.org/") has support for video.

---

### Post by elitenoobboy on 2009-08-26
> **Bios Element said:**
> There were many reasons, that being just one. And there has been chat long import for as long as I've tested empathy which is over 6-some months. And you won't switch without chat log importing? Ever hear of copy/paste? >.>

Care to tell me how to access this chat log import feature? I have empathy installed too, and I do not see one.
And do you really expect me to go through a couple hundred days worth of logs, copying and pasting them individually?

---

### Post by TheBuzzSaw on 2009-08-26
Whenever I start a voice call with a friend (I use Pidgin; he uses GTalk), I can hear his voice for about 2 seconds, then it cuts out. I still see his audio meter fluctuating (he continues talking), and he can hear me just fine. During those 2 seconds (sometimes less), his voice is all scratchy/noisy/loud.

Help? I tried lowering the volume, suspecting that the excess volume might be overloading it and shutting off my sound. However, it only dies for incoming Pidgin sound. My other sounds (video, music, etc.) work fine.

---

### Post by kal on 2009-08-27
For me, audio is working fine but my contacts can't see me! I can see them, but they can't see me : the image is freezed :(

---

### Post by jc4gavejc on 2009-08-27
pretty new to the forums, been using ubuntu only since jaunty..

I'm running Jaunty right now on an HP tx2513cl tablet and am having a problem with Pidgin 2.6 

I installed Pidgin from the developer repo yesterday, and everything seems to be working fine except video chat through XMPP. Calling other xmpp users also using pidgin 2.6.1 seems to work fine but if I call someone who is using Google's jingle plugin for Windows, the video chat window opens up for a split second and then vanishes. Receiving calls simply results in a timeout on both ends, though it does prompt me if I want to receive the call on ubuntu, and pops up a video window where I can see myself. 

Anybody else having this strange problem? I was thinking it might be because my front mic is a bit crackly when making voice calls, as well as the webcam image being stretched vertically a tiny bit. (When I configured it using gstreamer-properties the distortion was not evident, only when using programs such as pidgin and cheese)

 Maybe I should try Skype or something, haven't done that yet...

I really want to get pidgin working in ubuntu; when I heard about XMPP video support I got really excited because that was the one thing keeping me from completely removing windows from the pc. (to my knowledge)

---

### Post by jc4gavejc on 2009-08-27
Skype doesn't terminate or anything but the audio can barely be considered distinguishable; works much better using cheese recordings, though even a bit crackly and full of static at that. 

I really don't want to mess with Skype though, its a pretty useless service for me seeing as nobody I know really pays much attention to Skype and if they do there are better ways to contact them anyway which both of us have easier and more familiar access to. 

Tried Fedora 11 and Pidgin 2.6.1 with no luck; the problem remains exactly the same and the newest Pidgin is already included in the Fedora 11 repo?! That should entail stability and functionality even more so than the developer release, and Fedora has been pretty on top of things in that respect, I just like ubuntu better. 

I'm thinking this might be a hardware issue like I said before so I might try to resurrect one of the old topics about tx2500 series hardware setup with specific reference to the microphone issues (The previous focus has been on the wacom features and etc...) because I have studied the hardware setup tutorials that have been posted pretty thouroughly to no avail. 

Also, one of the things required to get my sound card working was adding a line to /etc/modprobe.d/alsa-base.conf that seemed to make my laptop out to be a Toshiba. Anyway I probably shouldn't go any farther; I'm going to make myself look pretty dumb..

---

### Post by abhiroopb on 2009-08-28
> **jc4gavejc said:**
> Skype doesn't terminate or anything but the audio can barely be considered distinguishable; works much better using cheese recordings, though even a bit crackly and full of static at that. 

I really don't want to mess with Skype though, its a pretty useless service for me seeing as nobody I know really pays much attention to Skype and if they do there are better ways to contact them anyway which both of us have easier and more familiar access to. 

Tried Fedora 11 and Pidgin 2.6.1 with no luck; the problem remains exactly the same and the newest Pidgin is already included in the Fedora 11 repo?! That should entail stability and functionality even more so than the developer release, and Fedora has been pretty on top of things in that respect, I just like ubuntu better. 

I'm thinking this might be a hardware issue like I said before so I might try to resurrect one of the old topics about tx2500 series hardware setup with specific reference to the microphone issues (The previous focus has been on the wacom features and etc...) because I have studied the hardware setup tutorials that have been posted pretty thouroughly to no avail. 

Also, one of the things required to get my sound card working was adding a line to /etc/modprobe.d/alsa-base.conf that seemed to make my laptop out to be a Toshiba. Anyway I probably shouldn't go any farther; I'm going to make myself look pretty dumb..

For me its the opposite. Everyone is on skype (and hardly anyone is on Gtalk). So, skype is really important for me.

---

