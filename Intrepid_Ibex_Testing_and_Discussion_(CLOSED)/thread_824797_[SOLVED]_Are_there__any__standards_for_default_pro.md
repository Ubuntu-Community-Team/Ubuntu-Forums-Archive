---
title: "[SOLVED] Are there _any_ standards for default programs in Ubuntu?"
date: 2008-06-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Vadi on 2008-06-10
I just found a project that has been included in Ubuntu 8.04 (after a very big debate, and a very silly decision in it's favour) that actively makes use of 'goto' in it's C code.

This leads to the question, are there *any* code standards for the default software in Ubuntu? Any at all?

---

### Post by twright on 2008-06-10
> **Vadi said:**
> I just found a project that has been included in Ubuntu 8.04 (after a very big debate, and a very silly decision in it's favour) that actively makes use of 'goto' in it's C code.

This leads to the question, are there *any* code standards for the default software in Ubuntu? Any at all?
which program?

---

### Post by Vadi on 2008-06-10
Transmission is the program that revealed this, however I'm just asking the general question.

---

### Post by 23meg on 2008-06-10
[https://wiki.ubuntu.com/UbuntuMainInclusionRequirements](https://wiki.ubuntu.com/UbuntuMainInclusionRequirements)

---

### Post by Vadi on 2008-06-10
Okay, thanks. What a wonderful piece of software do we have now.

---

### Post by 23meg on 2008-06-10
Yes, it's wonderful.

Use of goto does not have any proven side effect except for poor readibility and code structure (which is subjective, and upstream's concern to a much larger degree than being Ubuntu's), and its use for error handling is actually pretty common. A quick check of the Transmission code reveals that error and exception handling is all it's used for.

I don't know of a distribution that enforces programming styles for any subset of its packages.

---

### Post by talkingwires on 2008-06-10
I'd imagine the only one affected by it is the author(s). It will make debugging that much more difficult. But as long as the program runs fine, I don't think the Ubuntu developers are judging the coding prowess of the people that write the software included in the distribution.

---

### Post by Vadi on 2008-06-10
Combined with Transmissions awesome support for Linux (as said by their website - "you're on linux? here's the source code, go compile"), it was definitely a great choice to be picked. It definitely helps out new Ubuntu users who wish to update their transmission.

---

### Post by twright on 2008-06-10
> **Vadi said:**
> Combined with Transmissions awesome support for Linux (as said by their website - "you're on linux? here's the source code, go compile"), it was definitely a great choice to be picked. It definitely helps out new Ubuntu users who wish to update their transmission.
i love transmission, so simple yet so functional :)

---

### Post by 23meg on 2008-06-10
> **Vadi said:**
> Combined with Transmissions awesome support for Linux (as said by their website - "you're on linux? here's the source code, go compile"), it was definitely a great choice to be picked. It definitely helps out new Ubuntu users who wish to update their transmission.

Not this stuff [again]("http://ubuntuforums.org/showthread.php?t=667347"). 

Transmission upstream provides exactly the same level of "support" in that regard as provided by Ubuntu defaults such as F-Spot, Rhythmbox, OpenOffice.org, GEdit, Brasero, Totem, GIMP, Evolution.. you name it. You'd have a hard time arguing against any of them on that basis, and easy upgradability from third party (=unsupported by Ubuntu) packages is not a concern for default inclusion stated anywhere, nor should it be. If you want a new version, request or do a backport. Transmission has developers working closely with Ubuntu and tracking Ubuntu bugs, and their releases are almost guaranteed to be eligible for backports.

---

### Post by tighem on 2008-06-10
Transmission was included because it was part of Gnome 2.22. Notice how every other distro that uses gnome also recently picked up Transmission?

Anyway, it's a nice simple BitTorrent client. Something Ubuntu lacked, imo. Goto's for error exception handling is pretty common so I don't think you can say "this program contains 10 goto statements so it's out".

However, Vinagre does not seem to meet Ubuntu standards since it doesn't work with a lot of servers and based on that MainInclusionRequirements wiki, that would seem to be a deal breaker.

---

### Post by 23meg on 2008-06-10
[QUOTE=tighem]Transmission was included because it was part of Gnome 2.22.[/QUOTE]

No, it's not part of GNOME. It was included on its merits, simplicity being an important one.

---

### Post by twright on 2008-06-10
goto is fine in error handling e.g. (in java)

```
try {
[COLOR=DarkGreen] // operation which might generate an error[/COLOR]
} catch([COLOR=Green]errortype[/COLOR] [COLOR=DarkGreen]errorname[/COLOR]) {
goto [COLOR=DarkGreen]genericerrormessage[/COLOR];
}
```

---

### Post by Vadi on 2008-06-10
This topic isn't about the widely-critisied and controversial choice, but just about the application quality and the user experience it should provide as a whole.

Given the backlog of items in launchpad marked with "needs-packaging", relying on backports for a program that has a new release every two weeks (or something similarly absurd) isn't efficient, nor do I find backports to be too end-user friendly. What is is checking the website for the latest version to download, and even there, Transmission is purposely not including links to available .debs (which getdeb.net patiently makes for them, every single time). Instead, an easy install is offered for Macs, and for Linux - well, none.

Today's discovery was simply appaling. Using goto's across muptiple files to jump to some point in the program is, well, something that I understand was a nono 20 years ago. Making the choice of defaulting the program highly suspicious.

---

### Post by 23meg on 2008-06-10
> **Vadi]Given the backlog of items in launchpad marked with "needs-packaging", relying on backports for a program that has a new release every two weeks (or something similarly absurd) isn't efficient,[/QUOTE]

needs-packaging bugs have nothing to do with backport requests said:**
> nor do I find backports to be too end-user friendly. 

You seem to confuse "user-friendly" with "familiar", like 95% of the people who use that term. "Go to the application's website and download a package" is a more familiar model for Windows users, but Ubuntu != Windows. Activating the -backports repository (with the provided GUI) once and simply confirming updates when they become available is at least as "user friendly" as going to a website to *manually* check for updates, downloading a package and installing it. 

[QUOTE=Vadi]Transmission is purposely not including links to available .debs (which getdeb.net patiently makes for them, every single time)[/QUOTE]

Did you point them to that resource and ask why they don't? They may have a good reason, such as not trusting the packaging quality of getdeb.net, which if it is inferior, could do more harm than good. 

[QUOTE=Vadi]Today's discovery was simply appaling. Using goto's across muptiple files to jump to some point in the program is, well, something that I understand was a nono 20 years ago.[/QUOTE]

Times must have changed.

[QUOTE=Vadi]Making the choice of defaulting the program highly suspicious.[/QUOTE]

You can bring the issue up with the Technical Board by posting to the [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss"), or [contacting them directly]("https://wiki.ubuntu.com/TechnicalBoardAgenda").

---

### Post by plun on 2008-06-10
> **Vadi said:**
> T Transmission is purposely not including links to available .debs (which getdeb.net patiently makes for them, every single time). Instead, an easy install is offered for Macs, and for Linux - well, none.


Well... this is the way for mostly all open source projects

[http://www.transmissionbt.com/development.php](http://www.transmissionbt.com/development.php)

Debs are often built with help from someone within the community which runs a specific dist.

You have probably seen Google Gadgets and its exactly the
same situation. Their devs was surprised when a lof of Ubuntu
and Fedora users showed up and was using brand new versions which
broke their source code.

Fedora also uses Transmission...!!!


EDIT standard tarball on this page

[http://www.transmissionbt.com/download.php](http://www.transmissionbt.com/download.php)

---

### Post by twright on 2008-06-10
> **Vadi said:**
> This topic isn't about the widely-critisied and controversial choice, but just about the application quality and the user experience it should provide as a whole.

Given the backlog of items in launchpad marked with "needs-packaging", relying on backports for a program that has a new release every two weeks (or something similarly absurd) isn't efficient, nor do I find backports to be too end-user friendly. What is is checking the website for the latest version to download, and even there, Transmission is purposely not including links to available .debs (which getdeb.net patiently makes for them, every single time). Instead, an easy install is offered for Macs, and for Linux - well, none.

Today's discovery was simply appaling. Using goto's across muptiple files to jump to some point in the program is, well, something that I understand was a nono 20 years ago. Making the choice of defaulting the program highly suspicious.that is what ppa's are for, installing packages off websites is not they way apt is designed to be used

---

### Post by Vadi on 2008-06-10
Do they provide a PPA? No.

Edit: nvm, I don't care. Not like anything can change now, but I'm very dissapointed at the poor choice, with better alternatives available.

---

### Post by Seren on 2008-06-11
I don't have an example at hand, but as far as I know the Kernel uses plenty of "goto".

So if you want to remove transmission for that reason alone, you might also want to have the Kernel removed.

Edit :
From online Kernel sources :
 Freetext search: **goto**(7751 estimated hits)

---

### Post by insane_alien on 2008-06-11
the goto unction wouldn't exist if it wasn't to be used. sure there a plenty of scenarios where it is a really bad idea to use it but it dues have a useful function.

---

### Post by Vadi on 2008-06-11
I'm aware that goto is useful for low-level programming. As is assembly. Thanks.

---

### Post by twright on 2008-06-11
> **Vadi said:**
> Do they provide a PPA? No.

Edit: nvm, I don't care. Not like anything can change now, but I'm very dissapointed at the poor choice, with better alternatives available.
no but it is in one, with ubuntu and debian the rolling release cycle means you are not always meant to have the latest version of a program

i think that the only mainstream distros which don't have transmission in the repos are slackware based so the source is the right option for them (compiling stuff really isn't that hard)

i can't think of a better program for the job, can you?

---

### Post by 23meg on 2008-06-11
[QUOTE=Vadi]Do they provide a PPA? No.[/QUOTE]

Do you have any meaningful stats / predictions on the percentage / number of Ubuntu users that are explicitly aware (beyond the "I click a file and it starts downloading" sense, which for the most part is the intended use case) of some geek thing called a "BitTorrent client", of which the set of Ubuntu users who would be passionate about having the latest version of that thing would be a small subset? Probably no, and you're projecting your own priorities as if they were a very important concern for a considerable part of the user base.

I repeat: the major use case for Transmission, the default BitTorrent client, is the "tell Firefox to open something called a torrent link, or double click that mysterious .torrent file that you downloaded from somewhere which is supposed to initiate the download of *the thing that you actually want*". The target audience for Transmission *as the default app in Ubuntu* does not care for the latest version of Transmission; she cares for that file out there somewhere which she wants to get. Transmission is the means for getting it. The latest version? Who cares? 

I'll tell you who: the "power user", who happens to be aware of all the choices in the first place, their pros and cons, including Deluge, which is "easy to update because upstream provides packages on their website", and how to install them from Universe or elsewhere. If they don't like Transmission, or it doesn't work for them, it's not a big issue to uninstall it and install $FAVORITECLIENT instead.

---

### Post by Vadi on 2008-06-11
Quite a majority of people under 25 are aware of what a torrent is. The Pirate Bay lists as having 10 million users on it. 

People that you describe are likely not to use torrents at all; there are normal downloads provided in the case they're needed. And in case they do stumble upon one, I fail to see how one torrent client differs in the basic functionality. Considering a large, if not the biggest part of the Ubuntu userbase comes from Windows (like it or no - there *is* no proper user education on the apt-get system, backports, and blah blah blah. They just install Ubuntu and that's it), where upgrading from a website is quite common, this in my opinion is an issue. It's not like the issue is just in this case; however it *could have been* solved in this case, had not the worst possible solution been picked (or second worst. I don't remember if the old client had a link to the project page.).

---

### Post by castrojo on 2008-06-11
> **Vadi said:**
> Considering a large, if not the biggest part of the Ubuntu userbase comes from Windows (like it or no - there *is* no proper user education on the apt-get system, backports, and blah blah blah. They just install Ubuntu and that's it)

Exactly. So what's the problem?

---

### Post by Josh04 on 2008-06-11
10 PRINT "What's wrong with GOTO"
20 GOTO 10

I hated it when they made line numbers obsolete :(

---

### Post by twright on 2008-06-11
transmission is a brilliant bittorrent client which anyone can use simply but some more frequent users still need azurus or similar

i don't think however that the main use case considered for the inclusion of transmission was the illegal one. bittorrent is popular for sharing open media (such as peach or ubuntu CD's).

transmission is like gedit compared to the other bittorent clients, sure emacs is more powerful but it can't be the default as you need to know how to use it in order to use it :).

which bittorrent client do you suggest as the default?

---

### Post by The Warlock on 2008-06-11
transmission sure beats the hell out of the previous default, Gnome-Bittorrent.

---

### Post by 23meg on 2008-06-11
> **Vadi]People that you describe are likely not to use torrents at all said:**
> 

Indeed, when HTTP links are available, they'll choose those anyway. That's outside the use scenario, which begins when they *have to* use a torrent.

[QUOTE=Vadi]And in case they do stumble upon one, I fail to see how one torrent client differs in the basic functionality. 

Deluge, for example, pops up a "First Launch Configuration" wizard instead of working with sane defaults. Envision the experience of the user who doesn't know what "ports" to use, how many "half open connections" they should have, upon the first time they double click a torrent file. Would you find it sensible if Firefox asked the unsuspecting user how many "HTTP pipeline requests" they wanted at first run?

If you'd like to turn the thread into another Deluge vs. Transmission fight (which I doubt wasn't your intention in the first place :) ), I may dig up more examples. This one is fun.

[QUOTE=Vadi]Considering a large, if not the biggest part of the Ubuntu userbase comes from Windows (like it or no - there is no proper user education on the apt-get system, backports, and blah blah blah. They just install Ubuntu and that's it), where upgrading from a website is quite common, this in my opinion is an issue.[/QUOTE]

Thanks for *your opinion*. When I click System / Help and Support / Adding and Removing Programs, I see plenty of "proper user education", and if people don't care about that and "just install Ubuntu and that's it", that's fine; they have.. Transmission, a perfectly capable and simple BitTorrent client.

To put my point in slightly different terms:

If you're such a technical user as to care about the latest small batch of improvements in the two week old version of a BitTorrent client, it's safe to assume that you know or can easily learn how to install, update and remove applications in Ubuntu, and know about or can easily learn about the available selection of clients. You don't need to be catered for by the Ubuntu default. If the default client happens to be your favorite, how good for you, you just saved yourself a few minutes of Synaptic usage or at worst, in the case that you're just getting started with Ubuntu, half an hour of searching or asking around.  

If you're not, and if a BitTorrent client is either something you don't care much about and just occasionally use, or you don't even exactly know what it is and how it works, but it works anyway, the Ubuntu default should be fine for you. 

If you passionately care about having the latest version of pretty much *every* desktop app *all the time*, and won't bother to compile from source or do your own backports, you're using the wrong distribution anyway.

Note: I use Deluge and find it pretty good overall. It's more suited to my needs than Transmission.

---

### Post by bruce89 on 2008-06-11
If Ubuntu had code policies, then everything would have to be written in Python. Oh wait, it is.

Seriously, it's up to upstream if they want to use stupid code.

---

### Post by RAOF on 2008-06-12
There's nothing particularly stupid about goto.  It's a not-unreasonable way to implement try {} catch in C.

The same people who are absolutely against *goto* are also against use of *break* to terminate loops early.  While I can see the point, these are only guidelines (and poor ones, IMO) to achieve readable code.  It's obviously possible to use goto in a stupid way and produce horribly unreadable code, but it's not inherently evil.  Error cleanup code, particularly, can love goto.

---

### Post by plun on 2008-06-12
> **Vadi said:**
> Quite a majority of people under 25 are aware of what a torrent is. The Pirate Bay lists as having 10 million users on it. 



Well, just a "side note" that TPB is going to court in Sweden, I don't believe they survive. The same will probably happen with Mininova (Holland)

Support new sites such as Jonos   :)

[http://www.severedfifth.com/](http://www.severedfifth.com/)

(maybe spam...:))

---

### Post by Vadi on 2008-06-12
> **whiprush said:**
> Exactly. So what's the problem?

The problem is that 23meg here is assuming that the userbase *is* educated about backports, how the 6month cycle works, and the relationship of ubuntu and upstream. When, in fact, they aren't, and the users simply follow the old habits - which because certain projects hold the "you're on linux, go compile" attitude, turns some experiences sour.

---

### Post by Vadi on 2008-06-12
> **23meg said:**
> I

Deluge, for example, pops up a "First Launch Configuration" wizard instead of working with sane defaults. Envision the experience of the user who doesn't know what "ports" to use, how many "half open connections" they should have, upon the first time they double click a torrent file. Would you find it sensible if Firefox asked the unsuspecting user how many "HTTP pipeline requests" they wanted at first run?

If you're such a technical user as to care about the latest small batch of improvements in the two week old version of a BitTorrent client, it's safe to assume that you know or can easily learn how to install, update and remove applications in Ubuntu, and know about or can easily learn about the available selection of clients. You don't need to be catered for by the Ubuntu default. If the default client happens to be your favorite, how good for you, you just saved yourself a few minutes of Synaptic usage or at worst, in the case that you're just getting started with Ubuntu, half an hour of searching or asking around.  

In regards to the first paragraph: you'd click next->next->next. Why? Because it's a very common thing to do on windows, and the defaults in the deluge client are sane, so you can just skip everything.

If you're a technical user, you'll be forced to compile, via transmissions website. Which doesn't make a great experience.

Edit: Whatever. Even non-technical users will want to get something if it's breaking news. Like the banshee 1.0 release - and yes, thankfully, they do care for their linux users.

---

### Post by twright on 2008-06-12
> **Vadi said:**
> In regards to the first paragraph: you'd click next->next->next. Why? Because it's a very common thing to do on windows, and the defaults in the deluge client are sane, so you can just skip everything.

If you're a technical user, you'll be forced to compile, via transmissions website. Which doesn't make a great experience.

Edit: Whatever. Even non-technical users will want to get something if it's breaking news. Like the banshee 1.0 release - and yes, thankfully, they do care for their linux users.
i think the answer for this would be someting like suse's onclick install or linux mint's mintinstall (maybe if apt-url could add repositories)

once something is included by default then people will use it, but generally users be have to use ppa's or (shock, horror) actually learn how to compile stuff

---

### Post by Vadi on 2008-06-12
The answer for this is to simple provide a .deb, or if you aren't in a position to make one, at least link to the ones people are making for you.

---

### Post by bruce89 on 2008-06-12
> **Vadi said:**
> In regards to the first paragraph: you'd click next->next->next. Why? Because it's a very common thing to do on windows, and the defaults in the deluge client are sane, so you can just skip everything.

Sane defaults are the very cornerstones of GNOME. I installed Deluge once, talk about GUI disaster. Reminded me of Geany.

> **Vadi said:**
> Edit: Whatever. Even non-technical users will want to get something if it's breaking news. Like the banshee 1.0 release - and yes, thankfully, they do care for their linux users.

If you mean Banshee provide a messed up binary Debian package for i386, then yes, they do care. Under your definition GNOME, Linux and fd.o don't care.

> **Vadi said:**
> The answer for this is to simple provide a .deb, or if you aren't in a position to make one, at least link to the ones people are making for you.

I do have a PPA...

---

### Post by Vadi on 2008-06-12
Hi.

That's great that you got a PPA. Does the Tranmission website link to it, and does the PPA keep up to date with Transmission releases?

---

### Post by steeleyuk on 2008-06-13
Reading your posts Vadi it looks like you have some kind of vendetta against Transmission. They work just like a lot of other free software products in that they provide a compile-it-yourself tarball (which I might add is very easy to do if you really want/need by following the simple instructions that are out there - and I'm by no means an expert).

Transmission is a perfect client for the Ubuntu majority... simple, configurable (much more so than the old torrent client) and active. By the looks of it, you're just attempting to get it replaced with another client because you don't like it.

Sorry if I'm wrong, just my opinion and observations.

---

### Post by Vadi on 2008-06-13
> **steeleyuk said:**
> Reading your posts Vadi it looks like you have some kind of vendetta against Transmission. They work just like a lot of other free software products in that they provide a compile-it-yourself tarball (which I might add is very easy to do if you really want/need by following the simple instructions that are out there - and I'm by no means an expert).

Sorry if I'm wrong, just my opinion and observations.

You aren't wrong. I think all end-user projects should treat their Linux users as well as they do treat other users, or at least, ditch the "you're on linux, go compile" assumptions.

---

### Post by 23meg on 2008-06-13
> **Vadi said:**
> The problem is that 23meg here is assuming that the userbase *is* educated about backports, how the 6month cycle works, and the relationship of ubuntu and upstream. When, in fact, they aren't, and the users simply follow the old habits - which because certain projects hold the "you're on linux, go compile" attitude, turns some experiences sour.

No, I'm not assuming that. To assume that would take being cut off from the reality of how new Ubuntu users typically feel they way around as they get started. I've dealt with lots of new users here and elsewhere, mostly giving support, so I'm not. 

What I'm assuming is that we want to fix the "culture shock / paradigm shift" problem the way it should be fixed, in accordance with how our own paradigm works, which in turn may not be in accordance with the immediate expectations of some new users based on their experience with another OS. Expecting upstreams to cater for the packaging of every distribution (Why is Ubuntu special? Why not get mad at, say, Deluge for not providing Fedora packages, or CellWriter for not providing SUSE packages, or..) is just not realistic. Free software just doesn't work that way at this point. You do not expect upstreams to provide anything beyond a good source tarball. 

This is the status quo: upstreams release the raw code, distributions package it appropriately and deliver it. I'm not saying that it's perfect and covers all cases, but its shortcomings cannot be fixed with temporary workarounds such as expecting upstreams to do the packaging for all distributions. 

> **Vadi said:**
> You aren't wrong. I think all end-user projects should treat their Linux users as well as they do treat other users, or at least, ditch the "you're on linux, go compile" assumptions.

The assumption, rather, is "You're on Linux so you probably already have our stuff four clicks away, lucky you. If it's not the latest, look for third party packages, or go compile". It's not there because these projects set out to treat Linux users in an inferior way. It's because they're aware of how things work in the different spheres of different operating systems. 

There's no such thing as a "distribution" in the Mac and Windows worlds, and the toolchains and libraries that would be required for compiling and running their software if they were to provide just the source for Mac and Windows are often distributed poorly and in a non-standard fashion on those platforms, and as a matter of culture, their users are not capable of and/or interested in compiling from source anyway. 

Before you ask "Are Ubuntu users interested?", no, most are not either. That's why we have backports, PPAs, third party repositories, Autopackage, Klik, Zero Install, you name it. We have a different set of systems, so it's perfectly understandable that upstream projects act in a different way.

If you want to fix (or are interested in seeing a fix for) the problem of being unable to deliver the very latest versions of software packages to users of certain distributions, I suggest that you think in more general terms than the unwillingness of a certain upstream to package for a certain distribution.

---

### Post by twright on 2008-06-13
> **Vadi said:**
> You aren't wrong. I think all end-user projects should treat their Linux users as well as they do treat other users, or at least, ditch the "you're on linux, go compile" assumptions.
i think that as 60% of linux users will already have transmission installed and the rest will just use their package managers to install them

---

### Post by Vadi on 2008-06-13
So what do you say about projects that *do* provide .debs, .rpms, and whatnot for their users?

Like, Banshee 1.0 just got released. The news goes everywhere, and quite a lot of users want to get it. Who's going to wait until it appears in the backports? Not many, they'll all swarm the website and the "Downloads" section. Thankfully, there's something they can install right away. Is that wrong? Everybody was supposed to patiently wait until it's packaged or start figuring out how to compile it?

I understand that for projects that the end-user doesn't directly interact with, it's okay for the distro to provide program. But for things that the end-user does interact with, and with available websites, this only brings frustration - or a very heavy popularity of third-party packaging services. If the user can find them, because some projects ie transmission aren't even bothering to link.

---

### Post by twright on 2008-06-13
> **Vadi said:**
> So what do you say about projects that *do* provide .debs, .rpms, and whatnot for their users?

Like, Banshee 1.0 just got released. The news goes everywhere, and quite a lot of users want to get it. Who's going to wait until it appears in the backports? Not many, they'll all swarm the website and the "Downloads" section. Thankfully, there's something they can install right away. Is that wrong? Everybody was supposed to patiently wait until it's packaged or start figuring out how to compile it?

I understand that for projects that the end-user doesn't directly interact with, it's okay for the distro to provide program. But for things that the end-user does interact with, and with available websites, this only brings frustration - or a very heavy popularity of third-party packaging services. If the user can find them, because some projects ie transmission aren't even bothering to link.
1.21 is only a minor release whereas banshee 1.0 is revolutionary, i think that banshee should provide the ppa linux but then they would have to package for all distros.

source seems to have became the only way you can distribute a program to all linux users except via the package managers. though i would like an effort to be made for something like one click install for ubuntu we can't criticize projects for not using one until one is created

---

### Post by bruce89 on 2008-06-13
> **Vadi said:**
> That's great that you got a PPA. Does the Tranmission website link to it, and does the PPA keep up to date with Transmission releases?

Saying as I have no Transmission package, no. I wouldn't want the responsibility either.

> **twright said:**
> though i would like an effort to be made for something like one click install for ubuntu we can't criticize projects for not using one until one is created

There are other distros you know. [apt:transmission-gtk]("apt:transmission-gtk") is something like it.

---

### Post by 23meg on 2008-06-13
[QUOTE=Vadi]So what do you say about projects that do provide .debs, .rpms, and whatnot for their users?[/QUOTE]

Assuming that they do good packaging, and don't make it sound as if one *had to* get the software from them directly in binary form (I've never seen an example of this), more power to them. Bonus points for actively working with distributions to provide up to date packages as permitted by their release policies (which can flex when there is direct upstream involvement), or via external trusted means, such as official team PPAs with Universe-quality packaging assured. 

There are many examples of upstreams who work closely with distributions getting exceptions from distribution release and update policies. In Ubuntu we have [standing freeze exceptions]("https://wiki.ubuntu.com/StandingFeatureFreeze") for certain software we rely heavily on and work closely with. Stable release exceptions in Universe can also be granted when upstreams make a commitment to take maintainership of their software in Ubuntu when needed. An example of this was Tor, whose authors demanded that it be removed completely from Universe, citing that it was developed rapidly and keeping old versions in Ubuntu all along the support period of an Ubuntu release (from 1.5 to 5 years) would give users a false sense of anonymity. Since removing Tor would not be desirable from the standpoint of its users, a better solution was reached by issuing an exception to Tor which (if I recall correctly) allowed its developers / Debian maintainers to update the Ubuntu package in reasonable intervals when they deemed necessary.

I have nothing against upstreams who *want to* provide distribution packages. My point is that as things stand, this cannot be *demanded* of them, and their reluctance to do so would not be a good point of argument against their software.

---

### Post by Vadi on 2008-06-13
*shrug* and I think it does, if they're going through the troubles for providing executables for other platforms. It shows how much they care about their end-users, simple as that.

By the way, nothing is mentioned about backports in Ubuntu's "Installing Software" help file. I have no idea how are you expecting users to know that, be able to report requests for backports, and so on.

The system sounds great, if not for the fact that a) There is a huge list of [needs-packaging] bugs, b) For a lot of the major end-user software that comes out, a brainstorm idea pops up asking for an update to it, c) Users are pointed to source code by some projects website. And so on. 

So it looks like the expected standard is for the projects not to care about their end-users, and instead rely on the distributions to attempt to keep up (which, like ubuntu, even fail to educate about the backports). Okay!

---

### Post by psyke83 on 2008-06-13
Vadi,

Let me get this straight... First, you complain about the allegedly low quality of Transmission for it's use of "goto" statements in their code. Then, you accuse the upstream developers of hostility towards users for not providing precompiled distribution packages on their homepage. Don't you see the irony?

Did one of the developers run over your dog or something?

---

### Post by bruce89 on 2008-06-13
Surely the most important thing is a program's working, not the precise code used to do it? *goto* can be useful to get out of big nested loops anyway.

Of course, curly brackets on the same line as other content is inexcusable, but I'd have a tough time finding any program that doesn't do it that way.

---

### Post by 23meg on 2008-06-14
> **Vadi said:**
> *shrug* and I think it does, if they're going through the troubles for providing executables for other platforms. It shows how much they care about their end-users, simple as that.

Other platforms work in other ways, which necessitate providing binaries to them, as I've described and you seem to ignore.

[QUOTE=Vadi]By the way, nothing is mentioned about backports in Ubuntu's "Installing Software" help file. I have no idea how are you expecting users to know that, be able to report requests for backports, and so on.[/QUOTE]

The online help mentions it, but the offline one probably should too. Please file a bug report in ubuntu-docs.

[QUOTE=Vadi]The system sounds great, if not for the fact that a) There is a huge list of [needs-packaging] bugs,[/QUOTE]

Which as I said before and you apparently haven't read, are completely irrelevant,

[QUOTE=Vadi]b) For a lot of the major end-user software that comes out, a brainstorm idea pops up asking for an update to it,[/QUOTE] 

which is yet another proof that people are using Brainstorm for all the wrong things,

[QUOTE=Vadi]c) Users are pointed to source code by some projects website. And so on. [/QUOTE]

which is wrong: project websites of "end-user software" almost always say "Check your distribution first, where our software should already be packaged for you".

[QUOTE=Vadi]So it looks like the expected standard is for the projects not to care about their end-users, and instead rely on the distributions to attempt to keep up (which, like ubuntu, even fail to educate about the backports). Okay![/QUOTE]

"Caring about users" is a red herring; it's about the way the whole system works. Good luck to you getting all upstreams who provide the Ubuntu defaults to ship up to date Ubuntu packages before complaining about Transmission.

---

### Post by Vadi on 2008-06-14
I simply started this to find the standard for programs used in Ubuntu. This thread answered it. Thanks!

(oh, yeah, and you still got the problem of brainstorm being "used for the wrong things". Users are like an explosion - it'll find the shortest way out. And this simply points out that brainstorm is more accessible to users than anything else, ie, the system is failing on education)

---

### Post by 23meg on 2008-06-14
I never said the system was perfect and we had no problems educating new users about procedures (I'm actually on record saying the opposite quite often). Feel free to help improve things.

---

