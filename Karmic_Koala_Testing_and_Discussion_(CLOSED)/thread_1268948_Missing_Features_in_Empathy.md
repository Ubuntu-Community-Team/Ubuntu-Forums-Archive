---
title: "Missing Features in Empathy"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-17
In the long discussion regarding whether Empathy is ready to replace Pidgin as the default IM client, many people have cited that they don't find Empathy suitable due to its current lack of certain features that Pidgin has.

Please post the features you're missing in Empathy compared to Pidgin, along with links to wishlist bugs already filed if possible, and let's see altogether what we can do towards having the feasible ones implemented in time for Karmic. The list is brief now, since I'm not very familiar with the advanced features of each application, but I will update it as new ones get posted.

Please be concise in your posts, and refrain from discussing the topic of the previous thread, and any other discussion not related to the goal of this thread.

[SIZE="4"]**Missing Features**[/SIZE]
[list]
[*] OTR
[*] Contact blocking [SIZE="1"][[Upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=551911")][/SIZE]
[*] ICQ: no file transfer (bi-directional)
[*] Invisible list: (maybe protocol-dependent) allow on a per-contact basis to force or override your invisible status
[*] Plugin manager
[*] Custom emoticons
[*] All standard emoticons
[*] File transfer support for MSN
[*] Cross-protocol contact merging
[*] Ability to select specific contacts to show on the contact list even when offline (when the "show offline contacts" option is disabled)
[*] Support for Microsoft OCS/LCS 
[*] Ability to define the time to automatically change from online to away
[*] Theming support (including contact list)
[*] Remember status (away/available/busy)
[/list]

---

### Post by tretle on 2009-09-17
Any chance you could update your post to show features which empathy has that pidgin does not. 
Geolocation, Voice/video over jabber/msn and google talk come to mind along with webkit chat themes.
Also integration with other applications like rhythmbox,banshee, jokosher etc would be a good thing to point out to the community.

---

### Post by 23meg on 2009-09-17
> **tretle said:**
> Any chance you could update your post to show features which empathy has that pidgin does not. 
Geolocation, Voice/video over jabber/msn and google talk come to mind along with webkit chat themes.
Also integration with other applications like rhythmbox,banshee, jokosher etc would be a good thing to point out to the community.

While that's a good idea, let's refrain from doing that in this particular thread, since it will trigger unrelated discussions of "feature parity". You're welcome to start a separate thread for that purpose.

---

### Post by coldReactive on 2009-09-17
Please don't use abbreviations, some of us (like me) don't know what they mean. Anyway, I can give a few:

1. Can't set the minimum height for text input
2. Cannot nullify incoming formatting
3. No "User is typing..." notification
4. No plugin manager.

This is from Jaunty Empathy. I am not willing to upgrade because of these missing features in Jaunty.

---

### Post by 23meg on 2009-09-17
> **coldReactive said:**
> 
This is from Jaunty Empathy. 

Then it's irrelevant. Please base your entries on the current version of Empathy in Karmic.

---

### Post by thecityofgold2006 on 2009-09-17
If you can't block contacts then it's unusable.

---

### Post by 23meg on 2009-09-17
> **thecityofgold2006 said:**
> If you can't block contacts then it's unusable.

Please refrain from posting unless you're adding something new to the list. As you can see, contact blocking is on the list. This is not a discussion of whether Empathy is a good default.

---

### Post by coldReactive on 2009-09-17
> **23meg said:**
> Then it's irrelevant. Please base your entries on the current version of Empathy in Karmic.

I'm using 2.27.92 Empathy and the features I listed do not exist in it. On that note: When importing pidgin accounts, they aren't added properly (except MSN), but I'm not going to break my back and submit a bug report.

IE: When I import my list, I go to accounts, it shows a list of my pidgin accounts, hitting OK brings up a new window where I can add and edit accounts. The old list dialog NEVER appears again.

Also, you cannot REMOVE accounts from this new dialog.

---

### Post by 243kof on 2009-09-17
> **coldReactive said:**
> Please don't use abbreviations, some of us (like me) don't know what they mean. Anyway, I can give a few:

1. Can't set the minimum height for text input
2. Cannot nullify incoming formatting
3. No "User is typing..." notification
4. No plugin manager.

This is from Jaunty Empathy. I am not willing to upgrade because of these missing features in Jaunty.

It was my understanding that typing notification is already implemented? At least it worked for me in MSN a while back. It doesn't work over gtalk though. I have filed a bug report:
[https://bugs.launchpad.net/empathy/+bug/399039]("https://bugs.launchpad.net/empathy/+bug/399039")

---

### Post by 23meg on 2009-09-17
> **coldReactive said:**
> On that note: When importing pidgin accounts, they aren't added properly (except MSN), but I'm not going to break my back and submit a bug report.

IE: When I import my list, I go to accounts, it shows a list of my pidgin accounts, hitting OK brings up a new window where I can add and edit accounts. The old list dialog NEVER appears again.

Also, you cannot REMOVE accounts from this new dialog.

Missing features only, please; not bugs. Especially if you're not going to file a bug report, there's no point in talking about bugs here.

---

### Post by coldReactive on 2009-09-17
> **243kof said:**
> It was my understanding that typing notification is already implemented? At least it worked for me in MSN a while back. It doesn't work over gtalk though. I have filed a bug report:
[https://bugs.launchpad.net/empathy/+bug/399039]("https://bugs.launchpad.net/empathy/+bug/399039")

I was having the problem with YIM.

---

### Post by Technoviking on 2009-09-17
Facebook chat was missing the last time I used it.

T-V

---

### Post by Sashin on 2009-09-17
Not really a feature but pidgin looks alot slicker, maybe empathy should be updated with the new icons in the top right bar. It would be even better and more consistant if the available icon was a speech bubble with the rest of them.

---

### Post by anders_c_ on 2009-09-17
When importing from pidgin i dont get to keep my logs...

---

### Post by gnomeuser on 2009-09-17
a character counting plugin, which I am told is useful for those microblogging services.

---

### Post by twisted_steel on 2009-09-17
I use [pidgin-encryption]("http://pidgin-encrypt.sourceforge.net/") with some contacts of mine, though I don't see a problem moving over to OTR if it were supported in the future.

---

### Post by cowanh00 on 2009-09-17
It would be nice to have custom smilies. 

Also I have some Polish friends and use Gadu-Gadu sometimes. For some reason on this protocol you always have to download your buddies list manually when you have a fresh install. I cannot find a way to do this on Empathy so Gadu-Gadu is almost unusable as you cannot see your buddies online.

Pidgin has both of these features. Also plugin support would be nice!

---

### Post by MacUntu on 2009-09-17
* ICQ: no file transfer (bi-directional)
* ICQ: maybe I did something wrong but I haven't seen my contact's avatars
* ICQ and maybe others: the contact detail window doesn't show enough information
* Invisible list: (maybe protocol-dependent) allow on a per-contact basis to force or override your invisible status

---

### Post by Neon Lights on 2009-09-17
Last I checked, mobile status still isn't recognized [[bug]("http://bugs.freedesktop.org/show_bug.cgi?id=17157")].

---

### Post by fct on 2009-09-18
> **Technoviking said:**
> Facebook chat was missing the last time I used it.

T-V

According to this it's at the least being worked on, or even working in recent versions:
[http://identi.ca/notice/9822573](http://identi.ca/notice/9822573)

---

### Post by kestal on 2009-09-18
Though I have not tried the most recent version (I have been toying with my new laptop lately), I had a bit of trouble importing adium themes properly. I couldnt use the theme drop down afterwards (though that could have been my own mistake). 

I am not sure if this would be a consideration or if this applies, but is there any way to import themes from adium, like adium on mac osx? contact list and message styles, or anything else that may be missing.

If not directly importing from adium, then from something else (or new?)

Also, unless if it was changed.. Under the main contact list and message screen, there is no extra space or border around each window, and often can be hard to change the size of the windows.

---

### Post by misfitpierce on 2009-09-18
Exactly... two most important atm are turning off logging and no block list. Other than that though... Empathy is pretty nice. Wish it was easier to theme up with the adium theme things I saw.

---

### Post by denver on 2009-09-18
I don't know if this is a feature or not, but i'd have to say:

- an intuitive User Interface

The one Empathy has now looks like it was made in a hurry on a monday morning.

---

### Post by Staz on 2009-09-19
> **coldReactive said:**
> Please don't use abbreviations, some of us (like me) don't know what they mean. Anyway, I can give a few:

1. Can't set the minimum height for text input

It autoresize so the empathy dev don't consider this a bug, so it won't probably not get fixed.
> 
2. Cannot nullify incoming formatting

ATM empathy doesn't support message formating at all so the problem is not in nullifying it but in having it in the first place ;)

> 
3. No "User is typing..." notification

Empathy support this, if it doesn't works for some protocols please open bugs specifying which ones.
> 
4. No plugin manager.

No plugin support at all. Would also like to have this.

---

### Post by coldReactive on 2009-09-19
> **Staz said:**
> No plugin support at all. Would also like to have this.

Actually it does have plugin support, just no manager.

Also, about the notification for typing, it was with YIM. Never tested on MSN or AIM.

---

### Post by orlox on 2009-09-19
> **coldReactive said:**
> Actually it does have plugin support, just no manager.

Also, about the notification for typing, it was with YIM. Never tested on MSN or AIM.

There really is a plugin API for empathy?? I've looked for info on this but haven't found any...Were did you got this info??

---

### Post by Staz on 2009-09-19
> **coldReactive said:**
> Actually it does have plugin support, just no manager.

> There really is a plugin API for empathy?? I've looked for info on this but haven't found any...Were did you got this info?

Yes and no. Empathy via the Telepathy framework does have pluggable backends for protocols and components but Empathy itself doesn't have any plugin system to modify it's UI.

---

### Post by zoomy942 on 2009-09-19
> **23meg said:**
> Missing features only, please; not bugs. Especially if you're not going to file a bug report, there's no point in talking about bugs here.

What about facebook chat?

---

### Post by novafluxx on 2009-09-19
**If any of these are currently slated to be included with the Empathy version that will be in 9.10 correct me**

1. Contact Blocking
2. Protocol Specific Privacy settings
3. Plugin Support
4. Theme Support
5. HTML and Plain text logging options
6. A/V for MSN and Yahoo as well as XMPP
7. Ability to alter the default input field size


If it gets all these, the only thing left for me would be cross-platform binaries! I'd like to run it in Windows too! :guitar:

---

### Post by andrewabc on 2009-09-19
I don't know if these are possible or implemented (msn won't connect, and I don't have alpha 6 on cd yet to test). I'm just going to list as much as I can think of.

- Transparency. Possible to make everything transparent except text/icons/avatars on contact list?
- Change fonts on contact list (and in chat).
- icons per network. Say have msn icon next to msn contacts, icq next to icq etc.
- metacontacts
- how advanced are the tooltips over contacts? Are they customizable, so you can include: avatar, nickname, uid(email/icq#), last message received, status, last seen
- msn style info at top of program for your: avatar, status, nickname, status message, and other info that you can click on to change?
- smiley packages, sound packages. Sound per contact
- spellchecker
- plugin to analyse exactly what client users are using.

If anyone wants to figure out all possible customizations, get miranda instant messenger (for windows), as it is probably most customizable instant messenger available.
[Here's](http://forums.miranda-im.org/showthread.php?t=7758) a list of most of the popular plugins for it. Maybe give someone an idea to implement.

---

### Post by dext on 2009-09-19
> **misfitpierce said:**
> Exactly... two most important atm are turning off logging and no block list. Other than that though... Empathy is pretty nice. Wish it was easier to theme up with the adium theme things I saw.
what they should do  for Empathy3 is put the themes that are working in Empathy by Default that way they can be chosen when the user wanted to switch themes instead of installing them. Logging not everyone likes to have that turned on by Default without a Disable logging feature, i dont always use Logging unless its an important chat that i had

- spellchecke - that should be easy to implement.

---

### Post by coldReactive on 2009-09-19
> **dext said:**
> - spellchecke - that should be easy to implement.

Or integrate aspell like Pidgin.

---

### Post by novafluxx on 2009-09-19
> **coldReactive said:**
> Or integrate aspell like Pidgin.

I second this.

---

### Post by Staz on 2009-09-19
> **dext said:**
> what they should do  for Empathy3 is put the themes that are working in Empathy by Default that way they can be chosen when the user wanted to switch themes instead of installing them.

I think the idea is that the distributions would package themes and install some nice one by default ;)
> 
Logging not everyone likes to have that turned on by Default without a Disable logging feature, i dont always use Logging unless its an important chat that i had

Frankly, I don't get this idea. Why should I be the one to told my computer when to log when it can log everything for me without any significant use of resource ?

I've been more bothered by application not having logs when I needed them that the opposite.

> 
- spellchecke - that should be easy to implement.
Empathy already has spell check. I believe it use the same framework as Gnome for this.

---

### Post by Staz on 2009-09-19
> **novafluxx said:**
> **If any of these are currently slated to be included with the Empathy version that will be in 9.10 correct me**

1. Contact Blocking
2. Protocol Specific Privacy settings
3. Plugin Support
4. Theme Support

It's there, see [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)
> 
5. HTML and Plain text logging options
6. A/V for MSN and Yahoo as well as XMPP

Yahoo A/V is not supported
XMPP has been working since several versions (though the support should be improved in Karmic)
MSN just recently arrived last week [http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)
> 
7. Ability to alter the default input field size


If it gets all these, the only thing left for me would be cross-platform binaries! I'd like to run it in Windows too! :guitar:

---

### Post by dext on 2009-09-19
> **Staz said:**
> I think the idea is that the distributions would package themes and install some nice one by default ;)

Frankly, I don't get this idea. Why should I be the one to told my computer when to log when it can log everything for me without any significant use of resource ?

I've been more bothered by application not having logs when I needed them that the opposite.


Empathy already has spell check. I believe it use the same framework as Gnome for this.

the idea of all Distributions putting in there own themes? correct me if im wrong but all the other developers of other Distributions are tied up doing other projects, so they cannot do " this idea " 

what your doing with this Logging by turning it on by Default without a Disable button is **Forcing** the user to use this Feature when they dont want it turned on. i dont understand why people have to force things on people.

---

### Post by novafluxx on 2009-09-19
> **Staz said:**
> It's there, see [http://live.gnome.org/Empathy/Themes](http://live.gnome.org/Empathy/Themes)

Yahoo A/V is not supported
XMPP has been working since several versions (though the support should be improved in Karmic)
MSN just recently arrived last week [http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy](http://cass.no-ip.com/~cassidy/blog/index.php/post/2009/09/14/MSN-audio/video-chat-in-Telepathy)

Thank you for the reply, its much appreciated.

Are there any plans at all for Yahoo! A/V? Will MSN A/V be in Karmic, is it available to test right now?

I've tried Empathy in the past, but not since this development sprint has taken off! I'm eager to witness the improvements to be honest.

---

### Post by coldReactive on 2009-09-19
> **novafluxx said:**
> I've tried Empathy in the past, but not since this development sprint has taken off! I'm eager to witness the improvements to be honest.

Main reason why this all went down: Ubuntu is helping.

---

### Post by novafluxx on 2009-09-19
> **coldReactive said:**
> Main reason why this all went down: Ubuntu is helping.

Thats what its all about though, its open-source. I'm about to try out Empathy right...about...now.

UPDATE:
I tried it, and I can't log in to my Yahoo account (no fields for account info), and my friend is telling me I'm appearing "offline" to her. Is there anything special I need to do to make it show me as "online" to my friends contact lists? How can I test A/V! :-)


Please, please, PLEASE add an option to close conversation windows with the ESC key. I'm so used to doing this instead of moving the mouse to the "x" that without it I get frustrated...just an option, doesn't have to be default

---

### Post by tretle on 2009-09-19
> **zoomy942 said:**
> What about facebook chat?

Pidgin implemented this before facebook announced that they were switching protocols to xmpp. Facebook have yet to finish the migration.

---

### Post by bigbrovar on 2009-09-19
My biggest grips with empathy is the lack of network proxy support. while some protocol (last time i tried only yahoo) use the gnome-network-proxy settings, others will not connect if you are behind a network proxy. for me this is a serious show stopper

---

### Post by coldReactive on 2009-09-19
> **novafluxx said:**
> I tried it, and I can't log in to my Yahoo account (no fields for account info), and my friend is telling me I'm appearing "offline" to her. Is there anything special I need to do to make it show me as "online" to my friends contact lists? How can I test A/V! :-)

A/V isn't supported for Yahoo. Only MSN/XMPP and whatnot. Also, when I import my account info from pidgin, only MSN makes it through correctly.

> **tretle said:**
> Pidgin implemented this before facebook announced that they were switching protocols to xmpp. Facebook have yet to finish the migration.

lol... that's how it goes sometimes with big places like that.

---

### Post by tretle on 2009-09-19
> **coldReactive said:**
> Main reason why this all went down: Ubuntu is helping.

Ubuntu deciding to switch this release has no relevance to the sfeatures beginning to drop in empathy right now. This stuff has been in development a long time.
Its only after a long period post final distribution release that the new users will see some impact from their bug reports and whatnot.

---

### Post by novafluxx on 2009-09-19
> **coldReactive said:**
> A/V isn't supported for Yahoo. Only MSN/XMPP and whatnot. Also, when I import my account info from pidgin, only MSN makes it through correctly.

I can't even log on to Yahoo, it doesn't give me any fields to enter my account info into...

---

### Post by coldReactive on 2009-09-19
> **tretle said:**
> Ubuntu deciding to switch this release has no relevance to the sfeatures beginning to drop in empathy right now. This stuff has been in development a long time.
Its only after a long period post final distribution release that the new users will see some impact from their bug reports and whatnot.

Is it also a wonder that Pidgin started chucking out features when they heard they were being dropped? Ubuntu people then said: "crap" when they saw audio/video support for XMPP, basically.

---

### Post by tretle on 2009-09-19
> **coldReactive said:**
> A/V isn't supported for Yahoo. Only MSN/XMPP and whatnot. Also, when I import my account info from pidgin, only MSN makes it through correctly.



lol... that's how it goes sometimes with big places like that.

Yeah but its been a year, you might understand how this makes telepathy devs jobs harder as they don't want to support the current facebook protocol if they can reuse the xmpp one any day now. 
Facebook need to clarify the situation, there is nothing worse than spending lots of time reverse engineering a protocol to have your work redundant once they switch to another protocol you already supported.
The switch to xmpp will be better for users too as people with facebook im accounts will be able to send text/voice/video chats to people on google talk and other xmpp based IM's through the one account.
Yahoo experimented with it some time ago and if they switch then microsoft should feel pressure. Would be great to be able to have cross communication between different IM providers without needing multiple accounts.

---

### Post by coldReactive on 2009-09-19
> **tretle said:**
> Yeah but its been a year, you might understand how this makes telepathy devs jobs harder as they don't want to support the current facebook protocol if they can reuse the xmpp one any day now. 

Does it really? If they don't want to support something, they just drop the code and let other people make an extension or patch. Isn't that the point of open source? Granted, it would be nice to have it by default.

> **tretle said:**
> Facebook need to clarify the situation, there is nothing worse than spending lots of time reverse engineering a protocol to have your work redundant once they switch to another protocol you already supported. The switch to xmpp will be better for users too as people with facebook im accounts will be able to send text/voice/video chats to people on google talk and other xmpp based IM's through the one account. Yahoo experimented with it some time ago and if they switch then microsoft should feel pressure. Would be great to be able to have cross communication between different IM providers without needing multiple accounts.

Yes, indeed. Multiple accounts is not a great thing. But the lack of support for YIM to MSN and MSN to YIM in Pidgin is also a caveat. (AIM <> ICQ works almost flawless.)

---

### Post by tretle on 2009-09-19
> **coldReactive said:**
> Is it also a wonder that Pidgin started chucking out features when they heard they were being dropped? Ubuntu people then said: "crap" when they saw audio/video support for XMPP, basically.

Yeah but empathy supports audio/vido over xmpp(google talk, jabber etc) + MSN whereas pidgin just supports xmpp(google talk + jabber) not MSN. Also empathy has loads of other features that pidgin does not and will also help make other applications super cool with telepathy as evident from work done on sharing your music library with your contacts on banshee and collaboration with contacts on abiword and jokosher.
The ubuntu devs still dont think it was a bad choice as there was more too it than voice and video.

---

### Post by coldReactive on 2009-09-19
> **tretle said:**
> The ubuntu devs still dont think it was a bad choice as there was more too it than voice and video.

Do both Pidgin and empathy encrypt passwords though? I don't think so. Shouldn't Ubuntu recognise that, and not put either in until they do it?

---

### Post by novafluxx on 2009-09-19
So...is there a way to log into Yahoo using Empathy...? Just curious...if this is going to be the default I'd like to know what to do lol

---

### Post by coldReactive on 2009-09-19
> **novafluxx said:**
> So...is there a way to log into Yahoo using Empathy...? Just curious...if this is going to be the default I'd like to know what to do lol

Most likely it's better for you to submit a bug report.

[Click Here](https://bugs.launchpad.net/ubuntu/+source/empathy/+filebug)

---

### Post by tretle on 2009-09-20
> **coldReactive said:**
> Does it really? If they don't want to support something, they just drop the code and let other people make an extension or patch. Isn't that the point of open source? Granted, it would be nice to have it by default.



Yes, indeed. Multiple accounts is not a great thing. But the lack of support for YIM to MSN and MSN to YIM in Pidgin is also a caveat. (AIM <> ICQ works almost flawless.)

I take it you have never had to reverse engineer anything before. Yes it takes time. And when a public announcement was made that stated that what you were going to reverse engineer would be dropped in favor of something already supported it makes you less likely to waste your time.

Pidgin implemented it before the announcement was made, the guy that implemented it probably kicked himself in the teeth right after it was announced.

Its worth noting that aim and icq are supposed to be switching to xmpp at some point.

---

### Post by novafluxx on 2009-09-20
> **coldReactive said:**
> Most likely it's better for you to submit a bug report.

[Click Here](https://bugs.launchpad.net/ubuntu/+source/empathy/+filebug)

I've seen this reported here on the forums before, can't recall the thread now, but I'm sure its been reported already. Just was wondering if there was a workaround.

---

### Post by coldReactive on 2009-09-20
> **tretle said:**
> I take it you have never had to reverse engineer anything before. Yes it takes time. And when a public announcement was made that stated that what you were going to reverse engineer would be dropped in favor of something already supported it makes you less likely to waste your time.

Yes, I have never, and I agree.

> **tretle said:**
> Pidgin implemented it before the announcement was made, the guy that implemented it probably kicked himself in the teeth right after it was announced.

I probably would be doing the same.

> **tretle said:**
> Its worth noting that aim and icq are supposed to be switching to xmpp at some point.

Really? First for me to hear this.

---

### Post by gnomeuser on 2009-09-20
> **coldReactive said:**
> 
Really? First for me to hear this.


[2008 welcomes you](http://slashdot.org/article.pl?sid=08/01/18/1748218)

---

### Post by Merk42 on 2009-09-20
> **gnomeuser said:**
> [2008 welcomes you](http://slashdot.org/article.pl?sid=08/01/18/1748218)

All that links shows is that it's been 1.75 years and they STILL haven't switched.

---

### Post by gnomeuser on 2009-09-20
> **Merk42 said:**
> All that links shows is that it's been 1.75 years and they STILL haven't switched.

They haven't come out and commited to the change but on the other hand they haven't said that they are not still working on it. 

I imagine it takes quite a while to ensure that every feature of their old client is supported and working. Let alone the whole process of rolling out the new protocol and having it still work with clients that have not upgraded and on the scale we are talking about none the less - how many million users might we be looking, 5-10? Not breaking for any of them is going to take serious testing and development.

It sure sounds like a big job that would take a couple of years to roll out to me. It might also be one of the projects they have been put on the backburner, it provides little value to Yahoo upfront and in times of crisis perhaps the engineers were put to better use for a bit.

---

### Post by zoomy942 on 2009-09-20
> **tretle said:**
> Pidgin implemented this before facebook announced that they were switching protocols to xmpp. Facebook have yet to finish the migration.

So what's that mean for empathy?

---

### Post by gnomeuser on 2009-09-20
> **zoomy942 said:**
> So what's that mean for empathy?

If they switch to xmpp then telepathy-gabble should do the gruntwork, all you would need would be a profile which is easy.

I don't know if applications that integrate with the chat system need to register so API but even if we need that there are plenty of examples out there on how to do this.

---

### Post by Staz on 2009-09-20
> **coldReactive said:**
> Do both Pidgin and empathy encrypt passwords though? I don't think so. Shouldn't Ubuntu recognise that, and not put either in until they do it?
Empathy support password encryption via gnome-keyring, Pidgin doesn't as they don't want to include it by default as it not cross platform but I've heard some platform such as fedora patch it

Facebook chat is supported via telepathy-haze
For Yahoo we reuse the Pidgin library. they don't have video so we also don't have it

---

### Post by coldReactive on 2009-09-20
> **Staz said:**
> Empathy support password encryption via gnome-keyring, Pidgin doesn't as they don't want to include it by default as it not cross platform but I've heard some platform such as fedora patch it

What about md5? Or...

---

### Post by Staz on 2009-09-20
> **dext said:**
> the idea of all Distributions putting in there own themes? correct me if im wrong but all the other developers of other Distributions are tied up doing other projects, so they cannot do " this idea " 
I didn't mean to imply that each distribution create their own themes but rather that they packages existing themes. Packaging themes separately from the application is cleaner and that is the way it's also done for others applications/libs such as GDM, gtk, etc...

Also Empathy choose the location for it's adium themes as application-neutral so it could be reused by other program which also support adium themes such as Kopete.

> 
what your doing with this Logging by turning it on by Default without a Disable button is **Forcing** the user to use this Feature when they dont want it turned on. i dont understand why people have to force things on people.
Providing Enable/disable button for every feature of a program seems a bit silly to me and confusing for the user.

@coldReactive MD5 only works if you want to keep a hash of the password, so you can check it again when you receive it, not if you want to keep the password in full so that you can send it to servers.

---

### Post by coldReactive on 2009-09-20
> **Staz said:**
> @coldReactive MD5 only works if you want to keep a hash of the password, so you can check it again when you receive it, not if you want to keep the password in full so that you can send it to servers.

Most forum softwares encrypt your passwords using the md5 command in PHP. PHP can also do it reverse.

---

### Post by Keyper7 on 2009-09-20
> **Staz said:**
> Providing Enable/disable button for every feature of a program seems a bit silly to me and confusing for the user.

What about a gconf key at least? For advanced users?

---

### Post by coldReactive on 2009-09-20
> **Keyper7 said:**
> What about a gconf key at least? For advanced users?

gconf is not universal, just like the encryption issue for Pidgin, hence why Pidgin uses these buttons. Understand your program, before understanding others'

---

### Post by Keyper7 on 2009-09-20
> **coldReactive said:**
> gconf is not universal, just like the encryption issue for Pidgin, hence why Pidgin uses these buttons. Understand your program, before understanding others'

I thought Empathy wasn't caring (yet) for portability. Staz just said they use gnome-keyring.

EDIT: In fact, Empathy is *already* using gconf for a lot of things.

---

### Post by coldReactive on 2009-09-20
> **Keyper7 said:**
> I thought Empathy wasn't caring (yet) for portability. Staz just said they use gnome-keyring.

That's because Empathy is GNOME only.

---

### Post by Keyper7 on 2009-09-20
> **coldReactive said:**
> That's because Empathy is GNOME only.

YES, I KNOW!!! AND EMPATHY IS WHAT I WAS TALKING ABOUT FROM THE BEGGINING!!!

Sorry for shouting, but you seem to be having some trouble understanding me. :)

---

### Post by Staz on 2009-09-20
> **coldReactive said:**
> Most forum softwares encrypt your passwords using the md5 command in PHP. PHP can also do it reverse.

The md5 function in PHP return a hash, you cannot simply reverse it.
See [http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function) for more info on hashing function

---

### Post by coldReactive on 2009-09-20
> **Keyper7 said:**
> YES, I KNOW!!! AND EMPATHY IS WHAT I WAS TALKING ABOUT FROM THE BEGGINING!!!

Sorry for shouting, but you seem to be having some trouble understanding me. :)

The problem is, the quote you quoted at first was quoting features that pidgin had. Understand the past before understanding the present.

> **Staz said:**
> The md5 function in PHP return a hash, you cannot simply reverse it.
See [http://en.wikipedia.org/wiki/Cryptographic_hash_function](http://en.wikipedia.org/wiki/Cryptographic_hash_function) for more info on hashing function

Oh yeah, I forgot that what PHP does when you login, is take your logging in password that you typed in the field and convert it to md5, then compare the two md5s, thanks, I forgot.

---

### Post by Keyper7 on 2009-09-20
> **coldReactive said:**
> The problem is, the quote you quoted at first was quoting features that pidgin had. Understand the past before understanding the present.

In the quote, Staz was explaining why the feature is missing in Empathy.

---

### Post by orlox on 2009-09-20
> **coldReactive said:**
> Most forum softwares encrypt your passwords using the md5 command in PHP. PHP can also do it reverse.

Inverting md5 is not something that can be done with a invert_md5() function. PHP doesn't need to unencrypt the encrypted hash to check for a password, you simply apply the same encryption to the string you receive and you check it against the other password.

If MD5 could be so easily turned the other way around, it would certainly be a very crappy encryption for the uses it's given. Besides, how would you handle the collisions of MD5???

---

### Post by coldReactive on 2009-09-20
> **Keyper7 said:**
> In the quote, Staz was explaining why the feature is missing in Empathy.

Thank you for finally clarifying.

> **Keyper7 said:**
> I thought Empathy wasn't caring (yet) for portability. Staz just said they use gnome-keyring.

EDIT: In fact, Empathy is *already* using gconf for a lot of things.

Sorry, my last post also didn't point out that GNOME can run on windows anyway, ever heard of cygwin? If you can compile, run and configure GNOME on Windows, you can run GNOME apps.

> **orlox said:**
> Inverting md5 is not something that can be done with a invert_md5() function. PHP doesn't need to unencrypt the encrypted hash to check for a password, you simply apply the same encryption to the string you receive and you check it against the other password.

If MD5 could be so easily turned the other way around, it would certainly be a very crappy encryption for the uses it's given. Besides, how would you handle the collisions of MD5???

Read my earlier post:

> **coldReactive said:**
> Oh yeah, I forgot that what PHP does when you login, is take your logging in password that you typed in the field and convert it to md5, then compare the two md5s, thanks, I forgot.

---

### Post by aamukahvi on 2009-09-20
> **coldReactive said:**
> Most forum softwares encrypt your passwords using the md5 command in PHP. PHP can also do it reverse.

Incorrect. 

1. Hashes are used exactly for the reason that they are irreversible.
2. Given a hash, you can only find out the password by bruteforcing, which, depending on the complexity and length of the password may take a while.

The way it usually works is this:
1. A hash is stored when the user creates/changes the password
2. when a user tries to log in, a new hash is calculated using the password given in login request
3. this hash is then compared to the stored one. If they match, login = success.

---

### Post by Keyper7 on 2009-09-20
> **coldReactive said:**
> Thank you for finally clarifying.

You are welcome.

> **coldReactive said:**
> Sorry, my last post also didn't point out that GNOME can run on windows anyway, ever heard of cygwin? If you can compile, run and configure GNOME on Windows, you can run GNOME apps.

Yeah, but that's an awful lot of work that goes waaay beyond what one would consider "portability". It's easier to simply set up a Virtualbox Linux host with Gnome.

---

### Post by zoomy942 on 2009-09-20
> **Staz said:**
> Empathy support password encryption via gnome-keyring, Pidgin doesn't as they don't want to include it by default as it not cross platform but I've heard some platform such as fedora patch it

Facebook chat is supported via telepathy-haze
For Yahoo we reuse the Pidgin library. they don't have video so we also don't have it

How can I setup telepathy haze to work?   I didn't know that

---

### Post by Staz on 2009-09-20
> **zoomy942 said:**
> How can I setup telepathy haze to work?   I didn't know that
[http://aslakjohansen.wordpress.com/2009/06/21/facebook-chat-with-empathy-and-ubuntu/](http://aslakjohansen.wordpress.com/2009/06/21/facebook-chat-with-empathy-and-ubuntu/)
or there also posts about this on the forum.

If you have the latests version this should'nt even be needed.

---

### Post by ben2talk on 2009-09-20
My personal biggest shock was not being able to see a marker for MSN or Yahoo in the contact list or the Chat Window.

I had trouble working out who one contact was, and didn't realise that it was an MSN contact, not a Yahoo contact.

The contact told me they had a display picture, I could not see this either.

---

### Post by zoomy942 on 2009-09-20
> **Staz said:**
> [http://aslakjohansen.wordpress.com/2009/06/21/facebook-chat-with-empathy-and-ubuntu/](http://aslakjohansen.wordpress.com/2009/06/21/facebook-chat-with-empathy-and-ubuntu/)
or there also posts about this on the forum.

If you have the latests version this should'nt even be needed.

i thought i had the latest version of empathy; there was a post a little while ago about adding some ppa's for the latest version.  

as for it working now, this is what i have.

---

### Post by stoffe on 2009-09-20
Quick list from playing around with it a little again, likely not complete, and maybe one or two things are actually fixed, please let me know if that's the case.

There seems a thorough lack of stability, usability and polish, possibly unless you only use XMPP, in which case there would be no use forking/switching from gossip in the first place. Got tired quickly from all the usability problems that plague it, so the list is kind of short.

Updated empathy as of today.

* Name/rename accounts to real names - no "new jabber account"
* Stable support for friendly names, icons and status messages in MSN - only a few seems update quickly, the rest takes a LOOOONG time (XMPP seems to be better)
* Music tracker support not only for Rhythmbox but also for Spotify under Wine
* File transfer support for MSN
* All standard basic emoticons for the protocols
* Custom emoticons
* Set image and info for all accounts
* Failing that, at least SAVE the info for the account! It does not today, under personal information.
* View big version of buddies image
* As much/as good information about "buddies" in the list as Pidgin has
* Is it still as unstable as a week ago? - then more stability. Didn't crash this time, may be fixed.

---

### Post by andrewabc on 2009-09-20
Testing alpha 6.

Empathy does not have MSN HTTP connection.
I remember at one point testing empathy, it did have an msn http option, but I don't see it now.
I'm pretty sure most IM have this option.

Luckily for me, I probably won't be needing this option in a month, but I'd feel bad for those that do.

---

### Post by gnomeuser on 2009-09-20
> **andrewabc said:**
> Testing alpha 6.

Empathy does not have MSN HTTP connection.
I remember at one point testing empathy, it did have an msn http option, but I don't see it now.
I'm pretty sure most IM have this option.

Luckily for me, I probably won't be needing this option in a month, but I'd feel bad for those that do.

You probably used the telepathy-haze "bridge" to libpurple whereas now the msn support is granted via telepathy-butterfly.

---

### Post by Innu on 2009-09-20
I have many accounts: MSN, GChat, Jabber. There are some contacts that are included many times. So in the pidgin, I can expand a contact and then merge these contacts.

Pidgin has so many plugins and options.

Also, I would really like to see OTR plugin in the Empathy.

In my opinion, Empathy isn't ready to replace Pidgin.

---

### Post by GepettoBR on 2009-09-20
Show-stopper: lack of file transfer support in MSN.

Convenient but not vital: ability to select specific contacts to show on the contact list even when offline (when the "show offline contacts" option is disabled).

I've had other problems, but they've already been brought up in this thread. the file-transfer problem was also mentioned, but I think it's a severe issue that bears repeating.

---

### Post by zekopeko on 2009-09-20
> **GepettoBR said:**
> Show-stopper: lack of file transfer support in MSN.

I think there is MSN file transfer support in Empathy's git repo. Hopefully we'll get it in Karmic.

---

### Post by olskar on 2009-09-20
The bugreport linked to in the first post refers to a bug about not being able to block everyone not on your contactlist (to prevent spam) but when reading in the first post, it looks like Empathy does not support blocking people at all (and maybe it doesn't, I don't know). But the link and the text in the first post does not talk about the same issue as far as I can see.

---

### Post by master5o1 on 2009-09-20
I'd like to see a nicer looking GUI...

I suppose it would good if the contact list could be themed using Adium styles.

I have noticed that there is no (obvious?) way of saving a SIP user as a contact, or similar.

I would like to see (more?) IRC commands, or rather, more protocol commands for that matter -- Pidgin handles msn nudges nicely with '/nudge'.

I suppose being able to use the adiumxtra:// uri would be helpful.

and some other things that I cannot think of right now...

---

### Post by GepettoBR on 2009-09-21
> **zekopeko said:**
> I think there is MSN file transfer support in Empathy's git repo. Hopefully we'll get it in Karmic.

Hopefully. That's one feature I can't live without, so if we don't get it I'll have to stick with Pidgin.

---

### Post by gnomeuser on 2009-09-21
> **GepettoBR said:**
> Hopefully. That's one feature I can't live without, so if we don't get it I'll have to stick with Pidgin.

The ft feature was announced at the same time as the webcam/voip one, the code is there but the branch hasn't been merged yet. This is likely to come in another release, hopefully shortly. If it doesn't make it into Karmic on a freeze break then the Telepathy PPA will definitely carry the goods.

Generally I would recommend using the PPA, that way you are always granted the latest telepathy/empathy goodness.

---

### Post by coldReactive on 2009-09-21
> **gnomeuser said:**
> The ft feature was announced at the same time as the webcam/voip one, the code is there but the branch hasn't been merged yet. This is likely to come in another release, hopefully shortly. If it doesn't make it into Karmic on a freeze break then the Telepathy PPA will definitely carry the goods.

Generally I would recommend using the PPA, that way you are always granted the latest telepathy/empathy goodness.

Then why do we have empathy in by default if all we're going to be doing is adding PPAs? We didn't have to do that with pidgin (since we have MSN File transfer there) unless we really wanted to.

---

### Post by gnomeuser on 2009-09-21
> **coldReactive said:**
> Then why do we have empathy in by default if all we're going to be doing is adding PPAs? We didn't have to do that with pidgin (since we have MSN File transfer there) unless we really wanted to.

superior technology, think of the PPA as a fast track around debian to test if bugs are fixed. The road to ubuntu goes through debian but for testing a PPA is a good option.

Post release a PPA might not be a bad idea either, the rules for upgrading a package are strict (for a reason) but some users might enjoy additional updates to get new features not deemed acceptable as SRU.

But yes, the option we present in Karmic should be the finest we can manage within the confines of the development cycle. One way of ensuring that is to get early testing, hence the recommendation of the PPA to shortcircuit the cycle between updates by not waiting for the package to go through debian everytime.

---

### Post by mojorising on 2009-09-21
There appears to be no support for Microsoft OCS/LCS in Empathy. This is a must for many corporate environments (I hate MS too but I need to be able to use this IM protocol for my job. Without it's support in Linux, I'd have to run Windows or something). If anyone out there sees support for OCS in Empathy, please let me know. 

Pidgin does have the ability to use the OCS protocol with the SIPE plug-in ([http://sipe.sourceforge.net/](http://sipe.sourceforge.net/)). 

Pidgin has support for many other plug-ins too. Not being able to support approximately the same number of plug-ins or somehow match the features and functions provided by them seems like an issue to me. 

Also, OTR support is important and is something I use daily. Looking at the Empathy project site, it looks like the developers are opposed to having support for it added in Empathy. 


Mike

---

### Post by Punish3r on 2009-09-21
All in msn account
I don't know if they were all mentioned or not but here goes...

1 - ability to see avatars in conversation window.
2 - some way to manage the groups. I can see a way to remove the groups but cant see how to create one.
3 - ability to define the time to automatically change from online to away.
4 - see the " <someone> is typing a message" (or something like that)
5 - proxy connection
6 - nudge.


I also reported the following bug [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/433294](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/433294)

for now its all I can remember.

---

### Post by cassidy on 2009-09-21
Please, report bugs; listing missing features on a forum is completely useless.

Here are few things you can do to give us useful bug reports:

- Is the problem an Empathy or Telepathy one? In general, if the problem is pure UI that's an Empathy bug. If the problem only appears with one protocol (like "My contacts' avatars don't appear on ICQ") that's probably a Telepathy bug.

- If the bug is a Telepathy one, you should open a bug on the right connection manager:
* Jabber/XMPP: telepathy-gabble
* MSN: telepathy-butterfly
* SIP: telepathy-sofiasip
* IRC: telepathy-idle
* Link local XMPP: telepathy-salut
* ICQ, Yahoo, AIM...: telepathy-haze

- Check if there is already an upstream bug opened. Empathy bugs are tracked on [https://bugzilla.gnome.org/](https://bugzilla.gnome.org/) and Telepathy ones on [https://bugs.freedesktop.org/](https://bugs.freedesktop.org/)

- Attach logs to your bug report. See [http://live.gnome.org/Empathy/Debugging](http://live.gnome.org/Empathy/Debugging)

- Help us to triage bugs! We receive A LOT of bugs (upstream and on launchpad), help to triage them would be really appreciated.

- Contribute and help us to fix bugs

I'm aware that some people miss important features with Empathy. Helping us is the best way to get them implemented.

---

### Post by 23meg on 2009-09-21
[QUOTE=cassidy]Please, report bugs; listing missing features on a forum is completely useless.[/QUOTE]

Thanks for participating. My point with starting the thread was to get people to list missing features *in one place* (as opposed to the scattered piecemeal complaining and back-and-forth debate that goes on otherwise), go through the list a few days later to check if bugs haven't been filed for any, and file the ones that haven't.

---

### Post by novafluxx on 2009-09-21
> **23meg said:**
> Thanks for participating. My point with starting the thread was to get people to list missing features *in one place* (as opposed to the scattered piecemeal complaining and back-and-forth debate that goes on otherwise), go through the list a few days later to check if bugs haven't been filed for any, and file the ones that haven't.

Actually sounds like a practical and logical plan to me.

Thank you 23meg for closing that old thread and creating this one. I'm hoping Empathy gets some more major love before final freeze!

---

### Post by Regenweald on 2009-09-21
Google talk Status features.
Invisible and such. Empathy currently does not support it.

---

### Post by kestal on 2009-09-21
> **23meg said:**
> Thanks for participating. My point with starting the thread was to get people to list missing features *in one place* (as opposed to the scattered piecemeal complaining and back-and-forth debate that goes on otherwise), go through the list a few days later to check if bugs haven't been filed for any, and file the ones that haven't.

Question 23meg. What features do YOU think are missing that would be helpful to bring together the general public in accepting Empathy (to a certain degree of success - as full acceptance is not possible with anything as certain features are subjective).

---

### Post by david1274 on 2009-09-22
connection over microsoft lcs...there is no way to use with empathy...there is a plpugin for pidgin but not for empathy...I desperatly need it because in may office istant messaging is over msn (microsoft lcs)

---

### Post by [h2o] on 2009-09-22
> **david1274 said:**
> connection over microsoft lcs...there is no way to use with empathy...there is a plpugin for pidgin but not for empathy...I desperatly need it because in may office istant messaging is over msn (microsoft lcs)
Have you tried using telepathy-haze, the Telepathy Pidgin backend? I was under the impression it supported everything Pidgin supports.

---

### Post by Tibuda on 2009-09-22
> **Regenweald said:**
> Google talk Status features.
Invisible and such. Empathy currently does not support it.

Neither does Pidgin.

---

### Post by olskar on 2009-09-22
Time to update the first post perhaps? Lots of valid posts about lacking features has been made (and some unvalid e.g bugreports)

---

### Post by 23meg on 2009-09-22
> **olskar said:**
> Time to update the first post perhaps? Lots of valid posts about lacking features has been made (and some unvalid e.g bugreports)

Coming up in a few hours.

---

### Post by david1274 on 2009-09-22
> **'[h2o] said:**
> Have you tried using telepathy-haze, the Telepathy Pidgin backend? I was under the impression it supported everything Pidgin supports.

Yes tried...but ia a third part pidgin plugin and is not usable for empathy unlucky  :O(((

---

### Post by Ric_NYC on 2009-09-22
I don't understand why "half-baked" applications can become the default.

---

### Post by GepettoBR on 2009-09-22
> **'[h2o] said:**
> Have you tried using telepathy-haze, the Telepathy Pidgin backend? I was under the impression it supported everything Pidgin supports.

Only what's supported by libpurple. Protocols that pidgin can only support via plugins are not covered by telepathy-haze.

---

### Post by quazi on 2009-09-22
So things which at a glance seem to be missing for me:

-Facebook chat
-Idle time reporting with AIM.  I like to know if I'm messaging someone who's actually there.

---

### Post by taavikko on 2009-09-22
after the latest round of updates to empathy, I'm missing
Ability to minimize to tray by pressing the green circle (tray icon)

not much to whine about though :)

---

### Post by dmatrix on 2009-09-22
Another vote for facebook chat support with empathy.

Blocking contacts is another big feature missing.

And my notification area for empathy is also missing after the last updates.

---

### Post by taavikko on 2009-09-22
> **dmatrix said:**
> 

And my notification area for empathy is also missing after the last updates.

empathy is now shipped using the indicator-applet by default. (not running one?)
this can be disabled via empathy's preferences.

---

### Post by Ratscallion on 2009-09-22
Pidgin does Facebook chat??!! I never realised... something I must get around to using! 

If it's any good, add my vote to the whole "Add Facebook chat to Empathy" thing!

---

### Post by antono on 2009-09-22
> **Ratscallion said:**
> Pidgin does Facebook chat??!! I never realised... something I must get around to using! 

If it's any good, add my vote to the whole "Add Facebook chat to Empathy" thing!

It can be easily done via telepathy-haze if pidgin's facebook plugin will be merged to libpurple.

---

### Post by quazi on 2009-09-22
It's possible it already works.  This site seems to indicate that it does: [http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/](http://philliptweedie.wordpress.com/2009/05/18/facebook-chat-with-empathy-in-ubuntu/)

Really the whole failure to report idle time is the biggest thing for me.

EDIT: This no longer works.

---

### Post by psychok7 on 2009-09-25
hey there.. for some reason my msn in empathy makes my contact appear offline, and i cant seem to change it.. im using the ppa repositories so i guess its updated. Empathy seems to be a good alternative, but im afraid they should speed up the development in order to make it to KARMIC, otherwise they should leave pidgin witch is also getting a more active development

---

### Post by GepettoBR on 2009-09-25
> **psychok7 said:**
> hey there.. for some reason my msn in empathy makes my contact appear offline, and i cant seem to change it.. im using the ppa repositories so i guess its updated. Empathy seems to be a good alternative, but im afraid they should speed up the development in order to make it to KARMIC, otherwise they should leave pidgin witch is also getting a more active development

I agree. Unfortunately, the decision has been made already. It seems the devs are willing to give Karmic a crippled default package if it means there'll be more development to secure a more feature-rich version for Lucid, which will be an LTS release. and of course, being put in a spotlight of sorts as the default for Ubuntu will certainly boost the development of Empathy - it already has.

The good news is that it's easy as pie to install Pidgin, Kopete, aMSN or any other IM client if we aren't happy with Empathy. I agree with their decision, even though I don't think Empathy is close enough to the expected functionality.

---

### Post by stoffe on 2009-09-25
> **GepettoBR said:**
> being put in a spotlight of sorts as the default for Ubuntu will certainly boost the development of Empathy - it already has.


Too bad it mostly seems to boost the hacking-on-the-fun-stuff parts that was already going on. Tubes and whatnot are impressive and definitely something no others have, but it would be nice to have the absolute basics first.

---

### Post by GepettoBR on 2009-09-25
> **stoffe said:**
> Too bad it mostly seems to boost the hacking-on-the-fun-stuff parts that was already going on. Tubes and whatnot are impressive and definitely something no others have, but it would be nice to have the absolute basics first.

inb4 "don't complain, it's free" or "it's open-source, you can fix it yourself".

I have high expectancies for Empathy in Lucid Lynx, but I'll probably be better off with Pidgin until then.

---

### Post by GepettoBR on 2009-09-25
I just heard that Pidgin is back as the default.
[http://www.ubuntero.com.br/?p=787](http://www.ubuntero.com.br/?p=787)
Can anyone confirm this?

---

### Post by Podex on 2009-09-25
I can confirm that it is not back as default: [http://ubuntuforums.org/showpost.php?p=8007460&postcount=14](http://ubuntuforums.org/showpost.php?p=8007460&postcount=14)

---

### Post by kestal on 2009-09-25
It is a packaging bug. Personally, talking about Pidgin should not be the focus of this thread. There already has been a flame thread about choosing between pidgin/empathy and thats where it should stay.

Fact is, Empathy is now default and has made a lot of changes over the last few months. Granted, it is missing certain features, and that's what this thread is about.

Going back On-Topic, I'd be much obliged if we could somehow create our own themes via empathy's own standards and framework, rather than hijacking a select few themes from Adium which do not give full control to do what most people would enjoy to do, while theming. (most of which from the site, do not work)

Adium is a good example of this, actually, by letting you choose exactly what you want to change with easy to follow links which download automatically and let you change via a simple interface.

This is, of course, a nice dream as I am sure there are tons of other things that would be needed first, but I would gladly contribute time to design themes if an easy way to integrate/install them becomes available. (I have a bit of experience in the field)

---

### Post by Regenweald on 2009-09-25
> **danielrmt said:**
> Neither does Pidgin.

But I don't use pidgin, I use Empathy :) So of what bearing does this have in a thread suggesting improvements to Empathy ?

---

### Post by MacUntu on 2009-09-26
> **regenweald said:**
> so of what bearing does this have in a thread suggesting improvements to empathy ?

> **23meg said:**
> in the long discussion regarding whether empathy is ready to replace pidgin as the default im client, many people have cited that they don't find empathy suitable due to its current lack of certain **features that pidgin has**. :p

---

### Post by Frank-NL on 2009-09-26
Pidgin was just pushed here with today's upgrade. I know have Empathy and Pidgin available, doesn't seem like a packaging bug to me?

---

### Post by LosD on 2009-09-26
Status control:
- Remember status (away/available/busy) missing
- No ability to turn off that annoying "feature" that change back to available automatically.

Smileys:
- No custom smileys
- Only a few smileys, not all the ones that MSN supports (don't know about other protocols).

---

### Post by 23meg on 2009-09-26
> **kestal said:**
> Question 23meg. What features do YOU think are missing that would be helpful to bring together the general public in accepting Empathy (to a certain degree of success - as full acceptance is not possible with anything as certain features are subjective).

What I think is not really relevant, as I haven't used instant messaging extensively in the last decade or so, and haven't closely observed others using it, so I don't feel qualified to comment on that.

---

### Post by 23meg on 2009-09-26
I have compiled a tentative list in the first post that it seems, if completely implemented, would cover beyond 95% of the complaints. 

However, I'm not really familiar with the intricacies of IM applications, thus the list may include things that are already implemented, or not implemented in Pidgin either.

This thread will be open for one more day, so if you have some last minute modifications and clarifications to the list, please add them. After that, we'll have a separate thread where we do the bit of work that actually matters: making sure bugs have been filed for all missing features, and seeing how we can help with the progress of the existing bugs.

---

### Post by Tibuda on 2009-09-26
> **Regenweald said:**
> But I don't use pidgin, I use Empathy :) So of what bearing does this have in a thread suggesting improvements to Empathy ?

Sorry, I misunderstood you.

---

### Post by Gourgi on 2009-09-26
my IRC specific requests for empathy :

[LIST]
[*] Option to suppress IRC Nickserv Identification Messages - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=555051")**
[*] provide IRC nick fallbacks - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=586940")** 
[*] Show /whois info when selecting information on a irc user - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=592795")** 
[*] irc channels should show status of users - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=589623")** 
[*] Empathy and telepathy-idle don't pass on server commands to server - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=573407")**  <- Absolute blocker to me, pidgin's irc support is just perfect here for me :) 
[*] Tab completion doesn't work when completing a shared prefix - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=575670")**
[*]Empathy should use ContactInfo - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=588922")**
[*] Send files using drag and drop - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=595226")**
[/LIST]

general things missing :
[LIST]
[*] Empathy should support OTR encryption - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=545347")**
[*] Evolution/Empathy connectivity for contacts, etc - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=590898")** 
[*] Empathy should support formatted text - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=513176")**
[*] URL in contact's status are not clickable - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=525576")**
[*] empathy is not able to save chatlogs in simple text format - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=590033")**
[*] In Empathy, "F2" key should rename contacts - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=586257")**
[*] missing CTRL-Z support in chat window - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=585876")**
[*] Empathy does not display idle times - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=567531")**
[*]  Support metacontacts - **[Upstream Bug]("https://bugzilla.gnome.org/show_bug.cgi?id=460647")**
[/LIST]

**_ALL_ (!)** the above are available in pidgin either by default or by plugins.

Obviously there is plenty of room for improvement in empathy, especially regarding irc support.
I hope my list helps 23meg :popcorn:

---

### Post by alvevind on 2009-09-26
+1 OTR

The lack of OTR is the only show stopper for me to accept Empathy as default IM client. But it's a major one. I would never recommend anyone switch to an IM client without OTR support. It is the only viable cross platform solution to secure IM in the foreseeable future.

[https://bugzilla.gnome.org/show_bug.cgi?id=545347](https://bugzilla.gnome.org/show_bug.cgi?id=545347)

[http://lists.cypherpunks.ca/pipermail/otr-users/2009-September/001710.html](http://lists.cypherpunks.ca/pipermail/otr-users/2009-September/001710.html)

---

### Post by Regenweald on 2009-09-26
> **MacUntu said:**
> :p

Very true :P but from my point of view, I'm not a user citing lacking features based on a comparison from Pidgin. I'm a brand new Empathy user citing features/enhancements to my software of choice. So the suggestion based could be said to have two or more sets of user sources.... but again, valid point ;)

---

### Post by Regenweald on 2009-09-26
> **danielrmt said:**
> Sorry, I misunderstood you.

I was corrected by MacUntu, and see your point. I can see how my remark could have been interpreted as 'Well Pidgin has it!' 

Thanks for pointing out the feature parity though :)

---

### Post by dext on 2009-09-26
Empathy does not display idle times - [upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=567531") that one i don't think is a major Bug that needs to be put in any releases cause i don't care for idle times

---

### Post by michaelzap on 2009-09-26
> **alvevind said:**
> +1 OTR

The lack of OTR is the only show stopper for me to accept Empathy as default IM client. But it's a major one. I would never recommend anyone switch to an IM client without OTR support. It is the only viable cross platform solution to secure IM in the foreseeable future.

[https://bugzilla.gnome.org/show_bug.cgi?id=545347](https://bugzilla.gnome.org/show_bug.cgi?id=545347)

[http://lists.cypherpunks.ca/pipermail/otr-users/2009-September/001710.html](http://lists.cypherpunks.ca/pipermail/otr-users/2009-September/001710.html)

+1000

Things like text formatting and smilies are trivialities; lack of encryption is a fundamental flaw.

---

### Post by denver on 2009-09-26
> **michaelzap said:**
> +1000

Things like text formatting and smilies are trivialities; lack of encryption is a fundamental flaw.

Encryption is useful for few. Personally i don't care if someone is eavesdropping on my conversation. Its not like I'm planning world domination. If anyone has enough time to listen to me talk to family and friends about such topics as "what movie would you recommend" or "is the salad any good at XYZ?" then maybe they just missed a few hugs when they were kids.

Esthetics matter to most, and empathy is still a diamond in the rough. When it comes to IM clients I care more about voice,video and the way it looks rather then feeling "secure".

Don't get me wrong, OTR is a must if you wish to send sensitive information like user account information for your paypal account to your wife or family, but very few people choose to do this, and even less people have ever heard of OTR to start with.

---

### Post by alvevind on 2009-09-27
> **denver said:**
> Encryption is useful for few. Personally i don't care if someone is eavesdropping on my conversation.

Good argument there. Personally I don't care if there's a surveillance camera in my bathroom either. As long as I know it's only government employees, Microsoft and their business partners that are watching me. I think no one should have a problem with a camera in their bathroom, and if they do they must surely have some criminal activity to hide, right? 
/sarcasm

Not all people are the same, not all governments are the same, not all companies are the same, not all laws are the same, and things may change over time.

I believe that having a cross platform open source technology available that enables normal non-technical people to have a private conversation over the Internet, without having the risk of third parties logging it or censoring it, is a good thing.

OTR is not something you "sell" the software with, just as the seatbelt is not what you "sell" a car with. It's a safety feature that from a point of principle should just be there. People can themselves choose whether and when to use it.

---

### Post by denver on 2009-09-27
> **alvevind said:**
> Good argument there. Personally I don't care if there's a surveillance camera in my bathroom either. As long as I know it's only government employees, Microsoft and their business partners that are watching me. I think no one should have a problem with a camera in their bathroom, and if they do they must surely have some criminal activity to hide, right? 
/sarcasm


By your logic people should be afraid to meet and share a conversation in public, or never do it at all because someone might be listening to whatever nonsense i may have to share over a cup of tee. Being scared to leave the house or have a private conversation in a public or semi public place because something "might" happen is no way to go through life.

> **alvevind said:**
> 
Not all people are the same, not all governments are the same, not all companies are the same, not all laws are the same, and things may change over time.


Like i said in my previous post, OTR is a must in some situations, but at the present stage in development, Empathy is lacking basic features and usability improvements (scroll back through the posts...list is too long). Things do change, and so will Empathy if given enough time. I am certain that this will eventually make its way in, but at the moment Empathy stands to replace Pidgin and it must first serve the prime scope of its use, and that's to be a friendly, usable and intuitive IM client. 

> **alvevind said:**
> 
I believe that having a cross platform open source technology available that enables normal non-technical people to have a private conversation over the Internet, without having the risk of third parties logging it or censoring it, is a good thing.


I respect your beliefs and to some extent i agree with you, but there is a time and place for everything and in this particular moment in time, Empathy should concentrate on just delivering a stable, usable product that suits the majority of people.

Non technical people have been using Yahoo! messenger for years and years on windows without any encryption, and are still using it regardless. Yes some parts of the world are rough, and OTR might give some people some comfort in knowing "the government" or little green men are not listening in. However, if you do live in such a part of the world, protecting your IMs will be the least of your worries.

> **alvevind said:**
> 
OTR is not something you "sell" the software with, just as the seatbelt is not what you "sell" a car with. It's a safety feature that from a point of principle should just be there. People can themselves choose whether and when to use it.

I agree with you here, its just too bad that i have to convince the other 250 contacts in my list to use an IM client that actually implements OTR. I have yet to see a commercial IM client support this (correct me if i'm wrong). At the present moment i can only use OTR with about 8-10 of my entire list. I assure you that i am not the only one in this situation.

While this matter should not even be discussed, and every message we send should be encrypted, the reality is that 98% of people don't even know what OTR stands for, let alone what it does or why they need it. All they see is the lack of contacts blocking or customizable smiley's, and that will make the real difference in adopting an IN client or not.

The rest of those other 2% will either use pidgin or wait until Empathy implements it. I am hoping to see it soon, it is a deal-breaker for me as well, but i do acknowledge that I am a minority in this matter.

Just my 2 cents,
Best wishes to you!

---

### Post by michaelzap on 2009-09-27
> **denver said:**
> I have yet to see a commercial IM client support this (correct me if i'm wrong).!

Not sure what you mean by "a commercial IM client". I used to use OTR in Trillian on Windows, and that's commercial software. Most of the popular IM clients are freeware (Adium, Pidgin, Psi, Miranda, Digsby, and yes Messenger, etc.). Why does OTR need to be supported in a commercial client for it to be important...?

To me this is like removing Firefox from the core Ubuntu applications and replacing it with a new Gnome-only browser that doesn't support SSL.

This thread isn't really for debating the merits of IM encryption, so I guess I'll leave it there.

---

### Post by denver on 2009-09-27
> **michaelzap said:**
> Not sure what you mean by "a commercial IM client". I used to use OTR in Trillian on Windows, and that's commercial software. Most of the popular IM clients are freeware (Adium, Pidgin, Psi, Miranda, Digsby, and yes Messenger, etc.). Why does OTR need to be supported in a commercial client for it to be important...?

To me this is like removing Firefox from the core Ubuntu applications and replacing it with a new Gnome-only browser that doesn't support SSL.

This thread isn't really for debating the merits of IM encryption, so I guess I'll leave it there.

Sorry, "commercial" was a poor choice of words. I was thinking of "official" IM clients like Yahoo Messenger, MSN messenger, Google Talk, ICQ messenger and so on. But again, correct me if i am wrong, it has been a long time since i have used any of them.

---

### Post by popejeremy on 2009-09-27
I'm curious. Why is there a push to replace Pidgin with anything? What's wrong with Pidgin?

---

### Post by Neon Lights on 2009-09-27
> **popejeremy said:**
> I'm curious. Why is there a push to replace Pidgin with anything? What's wrong with Pidgin?
It's not so much about replacing Pidgin as it is about introducing the Telepathy framework, as well as the supposedly speedy development rate of Empathy.

*feels neglected cuz his missing feature wasn't put on the front post*
> **Neon Lights said:**
> Last I checked, mobile status still isn't recognized [[bug]("http://bugs.freedesktop.org/show_bug.cgi?id=17157")].

---

### Post by alvevind on 2009-09-28
> **denver said:**
> By your logic people should be afraid to meet and share a conversation in public, or never do it at all because someone might be listening to whatever nonsense i may have to share over a cup of tee. Being scared to leave the house or have a private conversation in a public or semi public place because something "might" happen is no way to go through life.

That is actually a very good example of a logical fallacy called the "straw man" argument. Read about straw man and other fallacies here (it's actually quite interesting and thought provoking reading):
[http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man)
[http://en.wikipedia.org/wiki/Logical_fallacy](http://en.wikipedia.org/wiki/Logical_fallacy)

Sorry for the digression.

:popcorn:

---

### Post by GepettoBR on 2009-09-28
> **denver said:**
> By your logic people should be afraid to meet and share a conversation in public, or never do it at all because someone might be listening to whatever nonsense i may have to share over a cup of tee. Being scared to leave the house or have a private conversation in a public or semi public place because something "might" happen is no way to go through life.

While I agree with the rest of your post, I have to raise a flag for *reductio ad absurdum* here. Of course, you're replying to another logical phallacy of the same kind, but you're taking it to extremes.

But like michaelzap said, this thread isn't really for debating the merits of IM encryption. It's an important feature, but not a priority. To keep with teh car metaphor, I'd rather have all-terrain tires (good support for msot features of every supported protocol) first, and a seatbelt second.

---

### Post by psyke83 on 2009-09-28
> **GepettoBR said:**
> While I agree with the rest of your post, I have to raise a flag for *reductio ad absurdum* here. Of course, you're replying to another logical phallacy of the same kind, but you're taking it to extremes.

But like michaelzap said, this thread isn't really for debating the merits of IM encryption. It's an important feature, but not a priority. To keep with teh car metaphor, I'd rather have all-terrain tires (good support for msot features of every supported protocol) first, and a seatbelt second.

Yes, I agree.

There are legitimate uses for IM encryption, especially considering that any corporations (including those that host IM servers) which retain chat logs can be privy to privacy or security violations. Using encryption is taking control of your own information and reducing the risk of third parties getting access to your private details.

As to the necessity of encryption, I wouldn't say it's a strict necessity, but it's certainly useful. You can censor the type of communication you transmit based on the presence or lack of encryption - such as giving telephone numbers or temporary passwords for remote assistance, etc.

A little off-topic for a moment (to lighten the mood) - how did you say [phallacy]("http://en.wikipedia.org/wiki/Phallus") with a straight face? ;)

---

### Post by GepettoBR on 2009-09-28
Well, you have to remember that there's not really a difference between the f and the ph... you're the one thinking dirty thoughts. :lolflag:

---

### Post by Ratscallion on 2009-09-28
> **popejeremy said:**
> i'm curious. Why is there a push to replace pidgin with anything? What's wrong with pidgin?
 +1

---

### Post by Keyper7 on 2009-09-28
> **alvevind said:**
> That is actually a very good example of a logical fallacy called the "straw man" argument.

An even better example is this one:

> **alvevind said:**
> [QUOTE=denver;8013235]Encryption is useful for few. Personally i don't care if someone is eavesdropping on my conversation.

Good argument there. Personally I don't care if there's a surveillance camera in my bathroom either. As long as I know it's only government employees, Microsoft and their business partners that are watching me. I think no one should have a problem with a camera in their bathroom, and if they do they must surely have some criminal activity to hide, right?
/sarcasm[/QUOTE]

The analogy is completely out of place. A more accurate analogy would be: denver doesn't want to install a camera signal scrambler in his house because someday, someone might install a camera in his living room to see how many times a day he picks his nose.

It also should be noticed that you *conveniently* edited the original paragraph, leaving out the part where denver made very clear that he didn't care about eavesdropping because his conversations were irrelevant and harmless:

> **denver said:**
> Encryption is useful for few. Personally i don't care if someone is eavesdropping on my conversation. **Its not like I'm planning world domination. If anyone has enough time to listen to me talk to family and friends about such topics as "what movie would you recommend" or "is the salad any good at XYZ?" then maybe they just missed a few hugs when they were kids.**

I doubt his opinion is the same for *private* conversations, so your analogy doesn't work.

---

### Post by cyberkilla on 2009-09-28
> **Ratscallion said:**
> +1

Empathy is a GNOME project, isn't it? I suppose they are consolidating:P I can understand the benefits of GNOME having it's own project for every piece of common desktop software.

I do not, however, understand why Ubuntu cares so much. It's not like they are fast-tracking Epiphany to replace Firefox too.

---

### Post by Merk42 on 2009-09-28
[SIZE="2"]**It is not that Ubuntu wants to replace Pidgin with Empathy.  It is that they want to implement Telepathy, which Pidgin did not want to use.**[/SIZE]

---

### Post by Keyper7 on 2009-09-28
Plus, despite the Gnome philosophy of hiding customization options and trying to *guess* what's best for the user (not always succeeding), they *do* have user satisfaction in mind. Since the Pidgin developers made very clear in the past that it's "developer satisfaction first, user satisfaction second", I'd guess that at *some point* they would clash with Canonical's future directions.

(sorry for the off-topic posts)

---

### Post by alvevind on 2009-09-28
> **Keyper7 said:**
> The analogy is completely out of place. A more accurate analogy would be: denver doesn't want to install a camera signal scrambler in his house because someday, someone might install a camera in his living room to see how many times a day he picks his nose.


At least I wrote "/sarcasm" to make it clear that I used a sarcasm. Sarcasm is one thing. A logical fallacy is another. ;-)

I can accept your modified analogy but with one correction:
The camera *is* already installed. We assume that the video is not being monitored or recorded at this time. But we have no real way of knowing.

I think the discussion itself is interesting but it is out of place in this thread. I apologize for having continued it here. 

If anyone want to discuss OTR and the security implications of person-to-person communication networks I have created a separate thread for that here:

[http://ubuntuforums.org/showthread.php?p=8020781](http://ubuntuforums.org/showthread.php?p=8020781)

Please join in!

And now:
Let the **"Missing Features in Empathy"** discussion commence!

---

### Post by 23meg on 2009-09-28
> **Gourgi said:**
> ...

I hope my list helps 23meg :popcorn:

Thanks, Gourgi, for taking the time to hunt for upstream bugs; that definitely looks helpful.

---

### Post by 23meg on 2009-09-28
> **alvevind said:**
> 
And now:
Let the **"Missing Features in Empathy"** discussion commence!

Or rather, [end, slightly later than it should have]("http://ubuntuforums.org/showpost.php?p=8009989&postcount=126"). Thanks all for participating. I'll very soon start a separate thread where we'll see what we can do to help with the progress of these desired features.

---

