---
title: "How Can I install GCC, G++, and Cpp compile enviroment?"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by muffinhead on 2006-05-16
I couldn't figure out an appropriate Place to post this, so feel free to move it if needed.

Anyway, I downloaded, gcc, g++, cpp , and the neccessary libraries for the compile enviroment via the Synaptic Package manager. I don't believe the Synaptic package manager installs it automatically, So I decided to post and ask, how can I install these, and what do I have to enter in the terminal to install? Thanks if you can help me;)

---

### Post by Lord Illidan on 2006-05-16
Did you mark the checkboxes, and press Apply? That's all that there is needed. Synaptic will download the .debs from the repositories, and install them for you too. Convenience unlimited!

You can also use the terminal to install stuff.

Try doing this:

```
sudo apt-get install build-essential
``` to make sure that you have all the necessary libs for development.

and

```
sudo apt-get install anjuta
``` to get a nice IDE.

EDITED : Forgot the apt-get INSTALL (silly me)

---

### Post by ryanakca on 2006-05-16
I believe that theres one package that has everything you need for a compile environment...
try this: 
> sudo apt-get install build-essential
It should have everything you need :)
Please correct me if I'm wrong ;) 

Cheers,
ryanakca

---

### Post by muffinhead on 2006-05-16
Thanks, I must of did something wrong, I'll try what you mentioned. I'm Just not used to Linux yet, It's new to me, so it'll take some time before I can navagate through it like windows:mrgreen: Ubuntu to me is about as good as windows, if not better;), it doesn't make dual booting and transitioning os's a major hassle, but there's still some new things to learn in the process.

I haven't noticed anything slowing down unlike windows due to spyware, adware, malware. If wine for Ubuntu could play all of my favorite PC Games flawlessly, I'd be able to transition with no problem, I love the screensavers in Ubuntu, most are 3d screensavers, and very cool. Ubuntu came packed with more, and better screensavers than my copy of windows xp did:) 

Thank you for your help, Keep up the good work;)

---

### Post by Lord Illidan on 2006-05-16
About your games... Depends on your games.

What kinda games do you have?

---

### Post by muffinhead on 2006-05-16
[quote=Lord Illidan]About your games... Depends on your games.

What kinda games do you have?[/quote]

The games I have (I'll only list a few) are Silent Hill 3, Silent Hill 4: The Room, Doom 3, Rainbow Six 3: Raven Shield, Max Payne 1 & 2, Unreal Tournement 2004, Grand Theft Auto III, and GTA: Vice city, and Others that would take to long to list, so I only listed a a little more than a few.

Btw, how do games and Programs work under wine, and Linux, that require Direct X, When Direct X is M$ invention, and copyrighted? I'm Just curious that's all, on how Direct X games can work under Linux with wine.

Thanks if you can get back to me, I'd really apreciate it, if you could let me know, if my games are compatable with wine, or can Link me to a compatability thread on another forum, Thank You:)

---

### Post by Lord Illidan on 2006-05-16
[quote=muffinhead]The games I have (I'll only list a few) are Silent Hill 3, Silent Hill 4: The Room, Doom 3, Rainbow Six 3: Raven Shield, Max Payne 1 & 2, Unreal Tournement 2004, Grand Theft Auto III, and GTA: Vice city, and Others that would take to long to list, so I only listed a a little more than a few.

Btw, how do games and Programs work under wine, and Linux, that require Direct X, When Direct X is M$ invention, and copyrighted? I'm Just curious that's all, on how Direct X games can work under Linux with wine.

Thanks if you can get back to me, I'd really apreciate it, if you could let me know, if my games are compatable with wine, or can Link me to a compatability thread on another forum, Thank You:)[/quote]

Doom 3 and UT 2004 are supported natively under Linux.

About wine, the best is to check [www.winehq.com](www.winehq.com)

---

### Post by ryanakca on 2006-05-16
[QUOTE=muffinhead]
Btw, how do games and Programs work under wine, and Linux, that require Direct X, When Direct X is M$ invention, and copyrighted? I'm Just curious that's all, on how Direct X games can work under Linux with wine.
[/QUOTE]
For some reason Direct X doesn't work in wine... sadly... but there IS a windows emulator, for linux, that was created specifically for gaming. It's called cedega... and it looks like they're doing pretty good... much better than they were a year ago, anywais.
[http://www.transgaming.com/](http://www.transgaming.com/)
[http://en.wikipedia.org/wiki/Cedega](http://en.wikipedia.org/wiki/Cedega)

Hope this helps,
ryanakca

---

### Post by YokoZar on 2006-05-17
[QUOTE=ryanakca]For some reason Direct X doesn't work in wine... sadly... but there IS a windows emulator, for linux, that was created specifically for gaming. It's called cedega... and it looks like they're doing pretty good... much better than they were a year ago, anywais.
[http://www.transgaming.com/](http://www.transgaming.com/)
[http://en.wikipedia.org/wiki/Cedega](http://en.wikipedia.org/wiki/Cedega)

Hope this helps,
ryanakca[/QUOTE]
DirectX has been working in Wine for 4+ years now, many times better than Cedega.

---

### Post by YokoZar on 2006-05-17
[QUOTE=muffinhead]Btw, how do games and Programs work under wine, and Linux, that require Direct X, When Direct X is M$ invention, and copyrighted? I'm Just curious that's all, on how Direct X games can work under Linux with wine.[/quote]Wine can run Direct X programs the same way Wine can run programs that require every other Windows library - by rewriting them from scratch.

This is why not all applications work in Wine yet - not every function in every Windows library has been rewritten in the exact way it behaves on Windows.  This is why more complex and idiosyncratic applications tend to not work as well - they use more esoteric libraries, and so have a greater chance of calling some function that isn't working right just yet.
> Thanks if you can get back to me, I'd really apreciate it, if you could let me know, if my games are compatable with wine, or can Link me to a compatability thread on another forum, Thank You:)
Check out the applications database at [http://appdb.winehq.org](http://appdb.winehq.org)

Be warned, however, that it is often out of date (Wine releases come out every 2 weeks now) and consequently the best thing to do may be to just try installing the game and see if it works or not.

---

### Post by muffinhead on 2006-05-17
Thanks for replying, I just tried to download the latest version of wine for ubuntu, via thier website, but was unable to, because for some reason thier Ubuntu Breezy badger Repository, is not in service, It comes up with an error when I enter the wine Repository url for wine in synaptic package manager, and then ubdate it, saying connection has timed out, or repository cannot be found a such and such.

I am entering in the right repository off thier website, so thats not the problem.

I ended up having to download an out of date version with the synaptic package manager.

Also the version I downloaded with synaptic, when ever I try to install doom 3 with wine, It comes up with an error, saying the cdkey.dll file couldn't be found. It says this game is compatable, yet I cannot install it:confused:

I read on thier website, and it says, that almost all my games are compatable, but when I put them in the  CD drive, It the files are not recognized in Ubuntu, and won't show up on the /media/cdrom in Ubuntu.

Does wine have a support forum? If they do, I can gladly state my question, and problems over there.

Thanks if you can help me and let me know;)

---

### Post by Lord Illidan on 2006-05-17
No need to use Wine for Doom 3.

[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

It is supported natively, i.e., you don't need to load a windows enviroment like Wine to run it.

---

### Post by muffinhead on 2006-05-17
Thank You, I'm downloading the Linux Installer for doom 3 right now. About my other Programs/Games, How am I supposed to install them with wine? I put the Cd in for the games, but the files on the cd don't show up in the browser.](*,)

I checked and the majority of my Games and Programs are compatable with wine, But I have no Idea how to use it, everytime I try to install any windows Program or game, it doesn't want to install, or I'm presented with an error.

Like I've asked before, does wine have a support forum, so I can gladly Post my Problem over there. Thanks once again if you can help me, or point me in the right direction, Thank You;)

---

### Post by ryanakca on 2006-05-17
Goodies!
*ditches cedega*.... yet for some reason I couldn't install DirectX... odd... anywais, sorry for misinforming you there...
Here comes wine! Sorry I can't aswer your latest questions.. I'm not the greatest on wine, as you can see :).  There is a wine channel where you can whine... lol... #winehq, on freenode... they're great for wine questions.

Cheers,
ryanakca

---

### Post by muffinhead on 2006-05-17
Thanks anyways, but I hope there may be someone here that knows how to use wine for Linux, and can tell me what I need to do to get my Games/Programs working with it, and can tell me why I'm getting errors, saying it couldn't install it error code somthing, when I checked and it is compatable with wine (I Checked on winhq for compatability)

I'll use thier support chat, as a last resort if noone can help me on this forum, anyways Thank You;) for your help, I guess I Just have to wait to see if anyone comes along and posts, that knows how  to use wine:)

---

