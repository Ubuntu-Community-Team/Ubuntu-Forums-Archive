---
title: "The saga about Firefox and fonts"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-09-18
Folks it's not complaining, it's me not getting it what's up.
It's already past alpha 6 and FF 3.5 has been released months ago yet the fonts issue which makes for a bad internet experience is still there and looks like it's not gonna be fixed anytime soon.
I don't have wine installed, and all other things I tried work only partially.
Screenshot attached with default Chrome's fonts and Firefox's default bold ugly fonts. FF is arguably the #1 app yet fixing it is not one of the top priorities? Come on.

---

### Post by Durden on 2009-09-19
The Ubuntu devs have never showed anything but contempt for Firefox. 3.5 has been out for a dogs age and it's still not in the 9.04 repos and they say never will be. You'll have to go to 9.10 to get it at all. They've been like this as long as I can remember. It's almost as if they were trying to get us to use something else, only there really isn't anything else.

---

### Post by FuturePilot on 2009-09-19
> **Durden said:**
> The Ubuntu devs have never showed anything but contempt for Firefox. 3.5 has been out for a dogs age and it's still not in the 9.04 repos and they say never will be. You'll have to go to 9.10 to get it at all. They've been like this as long as I can remember. It's almost as if they were trying to get us to use something else, only there really isn't anything else.

That's kind of the way Ubuntu works. The devs do not have some personal vendetta against Firefox. At release, the repositories are frozen and whatever version is out at the time is the version it stays at. And actually Firefox 3.5 is in the Jaunty repos. It doesn't replace Firefox 3.0 but you can run it side by side.

---

### Post by nhasian on 2009-09-19
while its true its not in the repos for 9.04 you can still add it yourself.  i like using ppa so it auto-updates when there is a bug release.  This is normal for ubuntu.  the repos will automatically be updated for bugfixes like firefox 3.0.x when a new major version comes out you will need to install it yourself or update ubuntu.

> **Durden said:**
> The Ubuntu devs have never showed anything but contempt for Firefox. 3.5 has been out for a dogs age and it's still not in the 9.04 repos and they say never will be. You'll have to go to 9.10 to get it at all. They've been like this as long as I can remember. It's almost as if they were trying to get us to use something else, only there really isn't anything else.

---

### Post by Merk42 on 2009-09-19
> **FuturePilot said:**
> That's kind of the way Ubuntu works. The devs do not have some personal vendetta against Firefox. At release, the repositories are frozen and whatever version is out at the time is the version it stays at. And actually Firefox 3.5 is in the Jaunty repos. It doesn't replace Firefox 3.0 but you can run it side by side.

Except it's called Shiretoko, which confuses people, and is still called Shiretoko in the [user-agent which breaks websites](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211).

A bug I feel the just won't fix and will tell people to upgrade to Karmic. Which is silly since it'll happen all over again in Karmic with 3.6

But that's all off-topic.

---

### Post by Aearenda on 2009-09-19
> **froggyswamp said:**
> Screenshot attached with default Chrome's fonts and Firefox's default bold ugly fonts
On my LCD screen, the bold text in your screenshot in Chrome looks worse than that in Firefox.

You can always go to a rolling release like Arch if you want the latest versions of everything, or use the ppa system as already explained by Futurepilot. There are good reasons for the version freeze system to be how it is: for example, I run a training lab where I'd really rather NOT have Firefox, or anything else for that matter, automatically updated to a new version (as opposed to applying fixes in the same version) without warning. To do so risks breaking Firefox add-ons, and means I would have to print a new set of manuals.

---

### Post by mikewhatever on 2009-09-19
The fonts in Firefox look OK, but rather crappy in Chrome. 

PS: I though complaining about FF3.5 has been over, after all, it's been in the repositories for a loooong time.

---

### Post by no1wantdthisname on 2009-09-19
Chromium might be a bit lighter.  But, it looks pretty much the same to me. Well that and the buttons.

---

### Post by bobince on 2009-09-22
I agree, I'd definitely take Firefox's fonts over Chromium's in these screenshots. The Chromium ones look over-hinted and quite misshapen.

Presumably the main reason is just different default fonts though. They are clearly different fonts above, not just different rendering options.

---

### Post by jlacroix on 2009-09-22
It is true that Firefox 3.5 was released after Jaunty's freeze, but so was KDE 4.3 and that was backported, so that's not an excuse. Some packages are backported and some aren't, and I think Firefox should be on that list. 

I don't really want the one called "Shiretoko" either, I want the real Firefox and I don't care about the branding drama, and most other people probably don't care either.

---

### Post by Keyper7 on 2009-09-22
> **jlacroix said:**
> It is true that Firefox 3.5 was released after Jaunty's freeze, but so was KDE 4.3 and that was backported, so that's not an excuse. Some packages are backported and some aren't, and I think Firefox should be on that list.

What's so special about 3.5 that justifies a SRU or a backport?

I'm seriously asking. I use 3.0 in Jaunty and 3.5 in Vista and never noticed any outstanding difference.

---

### Post by oldsoundguy on 2009-09-22
Wake up and smell the coffee!!

If you want the latest and greatest of ANY Mozilla product, take a few SECONDS and install this:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Just follow the simple steps and you can have those updates in your build, frozen at release or not!

---

### Post by cyberkilla on 2009-09-22
Why is the text on the buttons larger on the Firefox screenshot?

---

### Post by Merk42 on 2009-09-22
> **Keyper7 said:**
> What's so special about 3.5 that justifies a SRU or a backport?

I'm seriously asking. I use 3.0 in Jaunty and 3.5 in Vista and never noticed any outstanding difference.

Better performance and more features
What else WOULD there be to justify the backport?

I see Karmic does not have 3.6 in its repositories.  This is sort of a good thing so people won't be downloading that package and get confused at the [broken](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211) result.
Of course there still will be a lot of threads asking how to install 3.6 in Karmic when it comes out, but aside from changing the rules to backport Firefox I don't see how else to fix that.

> **cyberkilla said:**
> Why is the text on the buttons larger on the Firefox screenshot?
That is actually the point of this thread, to ask why.

---

### Post by cyberkilla on 2009-09-22
> **Merk42 said:**
> Better performance and more features
What else WOULD there be to justify the backport?

I see Karmic does not have 3.6 in its repositories.  This is sort of a good thing so people won't be downloading that package and get confused at the [broken](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211) result.
Of course there still will be a lot of threads asking how to install 3.6 in Karmic when it comes out, but aside from changing the rules to backport Firefox I don't see how else to fix that.


That is actually the point of this thread, to ask why.

I only just noticed it myself - I assumed it was a result of me messing around with the gnome font sizes. Apparently not:)

---

### Post by Keyper7 on 2009-09-22
> **Merk42 said:**
> Better performance and more features
What else WOULD there be to justify the backport?

Fixes for showstopper bugs and security issues.

---

### Post by jlacroix on 2009-09-22
> **Keyper7 said:**
> What's so special about 3.5 that justifies a SRU or a backport?

I'm seriously asking. I use 3.0 in Jaunty and 3.5 in Vista and never noticed any outstanding difference.

I find it faster and more stable, but that's just me. The real reason why the latest version should be made available is because it's the right thing to do.

> **oldsoundguy said:**
> Wake up and smell the coffee!!

If you want the latest and greatest of ANY Mozilla product, take a few SECONDS and install this:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Just follow the simple steps and you can have those updates in your build, frozen at release or not!

That's not a viable alternative to all. I use Kubuntu, and if I use Ubuntuzilla, the KDE Qt-GTK hack will not apply to it and it will look like garbage.

---

### Post by jlacroix on 2009-09-22
Also I wanted to say too that if Ubuntu rebranded Firefox as something like "The Ubuntu Browser", dropped Firefox branding, made it their own, and kept it up to date between all supported versions, that would probably work even better.

---

### Post by Keyper7 on 2009-09-22
> **jlacroix said:**
> The real reason why the latest version should be made available is because it's the right thing to do.

But Ubuntu is not a rolling release...

---

### Post by jlacroix on 2009-09-22
> **Keyper7 said:**
> But Ubuntu is not a rolling release...

Whether or not it's a rolling release isn't the issue. Mac OSX and Windows XP are not "rolling releases" either and you can always get the latest Firefox for those... Why should we have to wait? It's just a browser, not a new kernel!!!

---

### Post by Keyper7 on 2009-09-22
> **jlacroix said:**
> Whether or not it's a rolling release isn't the issue.

Yes, it's the issue.

Firefox will not be updated in Jaunty *because Ubuntu is not a rolling release*.

It's *completely* the issue.

> **jlacroix said:**
> Mac OSX and Windows XP are not "rolling releases" either and you can always get the latest Firefox for those...

If you want to make comparisons, make *fair* comparisons. OSX and Windows don't have repositories. Getting the latest Firefox for those systems means going to the Firefox website and downloading it directly. You can do *exactly* the same for Ubuntu.

> **jlacroix said:**
> Why should we have to wait? It's just a browser, not a new kernel!!!

Why is the latest version of "just a browser" so important for you?

---

### Post by NCLI on 2009-09-22
> **jlacroix said:**
> It is true that Firefox 3.5 was released after Jaunty's freeze, but so was KDE 4.3 and that was backported, so that's not an excuse. Some packages are backported and some aren't, and I think Firefox should be on that list. 

I don't really want the one called "Shiretoko" either, I want the real Firefox and I don't care about the branding drama, and most other people probably don't care either.
KDE 4.3 fixed A LOT of bugs, making the desktop environment a lot more stable. The bugs fixed in FF 3.5 have also been fixed in 3.0.X, so backporting it is not necessary.

---

### Post by LKjell on 2009-09-22
There isn't a lot of differences between those two versions. But I do miss the porno mode, erm I mean the private mode in 3.0.

---

### Post by Merk42 on 2009-09-22
> **LKjell said:**
> There isn't a lot of differences between those two versions. But I do miss the porno mode, erm I mean the private mode in 3.0.

Cannot safely browse porn on shared computer.
Hmm sounds like a critical bug to me, yep better backport 3.5!

---

### Post by dumblebee100 on 2009-09-22
> **froggyswamp said:**
> Folks it's not complaining, it's me not getting it what's up.
It's already past alpha 6 and FF 3.5 has been released months ago yet the fonts issue which makes for a bad internet experience is still there and looks like it's not gonna be fixed anytime soon.
I don't have wine installed, and all other things I tried work only partially.
Screenshot attached with default Chrome's fonts and Firefox's default bold ugly fonts. FF is arguably the #1 app yet fixing it is not one of the top priorities? Come on.

I think you are suffering from the antialiased fonts in firefox which are no more effected by default gnome font settings instead they follow some other font config file which I will show you ..do this and then post the screenshot 

```
edit the file

/etc/fonts/conf.avail

10-antialias.conf

change anti alias from TRUE to false

now enjoy firefox with crisp fonts


```

---

### Post by jlacroix on 2009-09-22
> **Keyper7 said:**
> Yes, it's the issue.

Firefox will not be updated in Jaunty *because Ubuntu is not a rolling release*.

It's *completely* the issue.

Yes, I know Ubuntu is not a rolling release. The latest version of a browser is not going to hurt anyone to make available. There are mainline kernels, KDE point releases, KDE betas, applications like KOffice, Amarok and others that are given releases in the current release. There is no excuse why the same can't be done for something like Firefox.

> **Keyper7 said:**
> If you want to make comparisons, make *fair* comparisons. OSX and Windows don't have repositories. Getting the latest Firefox for those systems means going to the Firefox website and downloading it directly. You can do *exactly* the same for Ubuntu.

You're missing my point on purpose. If it's not an issue to run the latest browser on other operating systems, it shouldn't be for Ubuntu either. Making Firefox available to everyone is not going to hurt anybody. I'm not asking Canonical to support it.

> **Keyper7 said:**
> Why is the latest version of "just a browser" so important for you?

See above.

---

### Post by LKjell on 2009-09-22
> **jlacroix said:**
> 
...
You're missing my point on purpose. If it's not an issue to run the latest browser on other operating systems, it shouldn't be for Ubuntu either. Making Firefox available to everyone is not going to hurt anybody. I'm not asking Canonical to support it.
....

I am a bit confuse here. You can install FF3.5 in jaunty. It is in the repo.
Or do you want to install FF3.5 and make sure it replace the old one? Well you can do it too. You just have to make sure you remove v3.0.

What I do not like is it is named shieko or whatever and has an ugly blue icon. And some Ubuntu plugins are broken.

---

### Post by Keyper7 on 2009-09-22
> **jlacroix said:**
> Yes, I know Ubuntu is not a rolling release. The latest version of a browser is not going to hurt anyone to make available.

The philosophy of release cycles is not "release if *releasing is not going to hurt*", it is "release if *not releasing is going to hurt*". It's not the case here. No computer is freezing or being invaded because of 3.0.

> **jlacroix said:**
> There are mainline kernels, KDE point releases, KDE betas, applications like KOffice, Amarok and others that are given releases in the current release.

And for every one of those SRUs and backports detailed discussions were made and they eventually were deemed worthy. So far, the only argument you gave in favor of 3.5 was "it feels faster and more stable". That's hardly enough to even *start* a discussion.

> **jlacroix said:**
> There is no excuse why the same can't be done for something like Firefox.

I'd say "3.0 works and has security patches", "more important SRUs exist", "more important backports exist", "Karmic development is happening", "developers are finite", "resources are finite" and "several maintainers are unpaid volunteers" are pretty good excuses.

> **jlacroix said:**
> You're missing my point on purpose. If it's not an issue to run the latest browser on other operating systems, it shouldn't be for Ubuntu either. Making Firefox available to everyone is not going to hurt anybody. I'm not asking Canonical to support it.

Why exactly it's an issue in Ubuntu?

Download from the Firefox site, unpack and run.

By doing that you even get automatic updates.

---

### Post by magneze on 2009-09-22
I kinda agree with the Ubuntu stand on Firefox in the repositories, and all apps. Upgrading stuff just for the sake of it is something that many techie users like, but for the mass market of users it's totally unnecessary - I guess that's the main reason it's done.

If someone wants the latest and greatest then just download directly ... just like all the other operating systems.

... so what was this font issue anyway ... :D

e2a: The continuous upgrade treadmill is not something that the software community should be particularly proud of either. Once something just works then we should try and leave it as "just working" for as long as possible. If a user is happy with their system, why change it unless it is actually broken? Ubuntu's system takes steps towards this, rather than the rather haphazard nature of application updates in Windows & OSX.

---

### Post by Longinus00 on 2009-09-22
What's wrong with doing this in jaunty?

```
$ sudo apt-get install firefox-3.5
```

If you're savvy enough to know the what firefox 3.5 is then you should be able to type that into a terminal.

---

### Post by LKjell on 2009-09-22
> **Longinus00 said:**
> What's wrong with doing this in jaunty?

```
$ sudo apt-get install firefox-3.5
```

If you're savvy enough to know the what firefox 3.5 is then you should be able to type that into a terminal.

Exactly. The problem I think is that it does not replace the old one and is not that integrated with gnome.

---

### Post by Merk42 on 2009-09-22
> **Longinus00 said:**
> What's wrong with doing this in jaunty?

```
$ sudo apt-get install firefox-3.5
```

If you're savvy enough to know the what firefox 3.5 is then you should be able to type that into a terminal.

Because as mentioned before it creates an entry called "Shiretoko", not the expected behavior of "Firefox" or even "Firefox 3.5" and, as said earlier, it's [broken](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/397211), and it seems they have no intention of fixing it.

But so is this thread, hardly anyone is talking about the font issue

Everyone is talking about updating Firefox to the latest version. That will happen when Ubuntu gets a new theme, the same day there is an advertisement on TV for Ubuntu and when people stop saying "M$"; as in **never**.

---

### Post by LKjell on 2009-09-22
Back to the font issue then. It looks ugly and the antialias thing does not really work. It just mess up the system font.

---

### Post by Sophont on 2009-09-22
Sigh.

1. Neither of the fonts in the screenshots is "ugly". You're overhyping your case.

2. People tried to explain to you that Ubuntu is not a rolling release. And that's exactly why usually neither FF nor any other app gets feature upgrades after release. There are some exceptions - but mostly its only security patches and minor fixes that go out after release.
Ifthe 6-month rhythm is too slow for your taste you have options:
a) get it from a PPA
b) switch to another distro with a different release policy

3. The name Shiretoko has nothing to do with branding issues. It's Mozilla policy to give pre-release version a code name so that regular users don't accidentally install an unfinished version.

4. Next month you'll get FF 3.5 with 9.10 - so what's your problem exactly?

Some of us like their software fresh alll the time and there distros that offer that.
But many people don't want their software changed all the time and they don't care about every feature upgrade. And on the extreme end enterprise can't have apps - that have to be evaluated first - changing all the time either. Ubuntus 6-month release cycle and the slower LTS cycle provides a compromise between every day bleeding edge and only upgrading twice a decade.

Again - if the 6-month cycle doesn't suit you then Ubuntu is simply not the right distro for you. There's plenty of alternatives. For most people 6-months is plenty fast enough.

---

### Post by gabba on 2009-09-23
> **Keyper7 said:**
> 
Why is the latest version of "just a browser" so important for you?

If you ask that question, I guess you're not using any Firefox extensions, then? A typical scenario is that there's an extension you've been using, but you discover it suffers from a showstopper bug. The author acknowledges the issue, but develops the next, bugfixed version for the new version of firefox... let's just say, it sucks to have to wait months for a proper upgrade.

There are also advantages, which I won't go into, to having the same version of Firefox on all your desktop computers. But currently Ubuntu's version always lags behind Windows, where upgrading is easy as pie. If you want to stay in sync, you have to choose either a badly integrated or a broken version.
(Remember that for Windows, Mozilla can do the integration themselves since they have only XP, Vista and Seven to target. Therefore Windows users can install Firefox themselves and have a good experience out-of-the box; however with Linux distros the burden of integration lies with the distro maintainer.)

In summary, since the whole "ecosystem" of software around Firefox and similar major open-source programs moves forward as a whole, it doesn't make much sense to lag behind. Unless of course you run a server, but Ubuntu is primarily a desktop distro, right? And who forces you to install a backport?

"Ubuntu is not a rolling release"... what if applying that to the letter slows down Ubuntu's progress on the desktop?

---

### Post by umberstark on 2009-09-23
Fonts are a pain. 

Get hem looking good on the desktop (which usually for me just means dropping the font size from 10 to 9 in the Gnome font config screen and leaving the hinting etc options at default) and they look terrible in Firefox. 

Then there's Openoffice... 

It's beyond stupid that probably the two biggest OSS browser and office suite projects don't respect Gnome desktop font settings.

Installing MS Core Fonts (which I find is a must) just adds to the complications. No one setting (of hinting etc) seems to work for all the fonts, unlike in Windows where if I have Dejavu, Liberation installed they look great alongside MS fonts.

---

### Post by Keyper7 on 2009-09-23
> **gabba said:**
> If you ask that question, I guess you're not using any Firefox extensions, then?

Six. All of them work perfectly in 3.0.

> **gabba said:**
> A typical scenario is that there's an extension you've been using, but you discover it suffers from a showstopper bug. The author acknowledges the issue, but develops the next, bugfixed version for the new version of firefox... let's just say, it sucks to have to wait months for a proper upgrade.

Another typical scenario is that an extension is not compatible with a new version of Firefox and the author takes ages to make it compatible or never does. Happened to me. We can trade anecdotes all day and that wouldn't prove anything.

> **gabba said:**
> There are also advantages, which I won't go into, to having the same version of Firefox on all your desktop computers. But currently Ubuntu's version always lags behind Windows, where upgrading is easy as pie. If you want to stay in sync, you have to choose either a badly integrated or a broken version.

Back when FF3 was released and I used Gutsy, I downloaded it from Mozilla's site, unpacked it and set the preferred browser to it. All done with mouse clicks. No hassle, no command line involved, and perfect integration. And I had automatic updates.

> **gabba said:**
> (Remember that for Windows, Mozilla can do the integration themselves since they have only XP, Vista and Seven to target. Therefore Windows users can install Firefox themselves and have a good experience out-of-the box; however with Linux distros the burden of integration lies with the distro maintainer.)

Making a distro-independent installer is not difficult.

> **gabba said:**
> In summary, since the whole "ecosystem" of software around Firefox and similar major open-source programs moves forward as a whole, it doesn't make much sense to lag behind. Unless of course you run a server, but Ubuntu is primarily a desktop distro, right? And who forces you to install a backport?

Ubuntu is target at the average user who simply wants to browse the web. 3.0 does that, and does it well. For the non-average user, installing and integrating 3.5 is not exactly rocket science.

> **gabba said:**
> "Ubuntu is not a rolling release"... what if applying that to the letter slows down Ubuntu's progress on the desktop?

It does. In exchange for predictability, stability and consistency. It's no perfect system, but no perfect system exists.

---

### Post by gabba on 2009-09-23
> **Keyper7 said:**
> 
Another typical scenario is that an extension is not compatible with a new version of Firefox and the author takes ages to make it compatible or never does. Happened to me. We can trade anecdotes all day and that wouldn't prove anything.


People were asking for a scenario where you're forced to upgrade or else give up functionality or be stuck with a bug, and I provided one. That the scenario you describe exists as well doesn't invalidate my point.

> 
Back when FF3 was released and I used Gutsy, I downloaded it from Mozilla's site, unpacked it and set the preferred browser to it. All done with mouse clicks. No hassle, no command line involved, and perfect integration. And I had automatic updates.


Perfect integration? I doubt it. Unless the distro maintainers get their hands dirty there's always *something* wrong, be it copying rich text or images to other programs not working, weird file picking dialog boxes that don't show mounted drives or FUSE drives, file type associations not working, and so on.
Even if the Mozilla devs had time to spend for Gnome integration in the release your talking about, doesn't mean anything for future ones. And if by some miracle they get it right every time, we can't expect the same of every major desktop app.

> 
Making a distro-independent installer is not difficult.


If it's suppose to install the app correctly on any distro with any version of the core libraries, and integrate correctly with Gnome/KDE/Xfce/Fluxbox/Moblin etc, I'd say the task is impossible.

> 
Ubuntu is target at the average user who simply wants to browse the web. 3.0 does that, and does it well. For the non-average user, installing and integrating 3.5 is not exactly rocket science.


Ubuntu could be as far back as what, 5 months behind the latest version?
The "average" user is bound to run into a website, extension, java plugin (the new "kernel" jvm with finally acceptable speed was only for the latest version, at the time), flash plugin, moonlight plugin, god-knows-what plugin that requires the latest version of Firefox. This category of users often use the latest media technologies much more that the typical programmer or sysadmin.

> 
It does. In exchange for predictability, stability and consistency. It's no perfect system, but no perfect system exists.


I don't see how systematically backporting the latest versions of Firefox, OpenOffice, GIMP and other major apps would affect those. If you're looking for "predictability, stability and consistency", you leave the backports repos disabled anyways.

---

### Post by Keyper7 on 2009-09-23
> **gabba said:**
> People were asking for a scenario where you're forced to upgrade or else give up functionality or be stuck with a bug, and I provided one. That the scenario you describe exists as well doesn't invalidate my point.

"People"? I thought it was a direct response to me.

Anyway, the point is: those scenarios are not convincing enough to justify an upgrade. They do not change the fact that there are no outstanding issues or security holes in 3.0.

> **gabba said:**
> Perfect integration? I doubt it. Unless the distro maintainers get their hands dirty there's always *something* wrong, be it copying rich text or images to other programs not working, weird file picking dialog boxes that don't show mounted drives or FUSE drives, file type associations not working, and so on.

Used it for months, don't remember an issue.

> **gabba said:**
> Even if the Mozilla devs had time to spend for Gnome integration in the release your talking about, doesn't mean anything for future ones. And if by some miracle they get it right every time, we can't expect the same of every major desktop app.

What I'm discussing here is what makes Firefox 3.5 special. If you want to expand the discussion to every major desktop app, then what's being put into question is the six-month model itself. But I'm not discussion that.

> **gabba said:**
> If it's suppose to install the app correctly on any distro with any version of the core libraries, and integrate correctly with Gnome/KDE/Xfce/Fluxbox/Moblin etc, I'd say the task is impossible.

You are correct in this one. I expressed myself badly, sorry. What I meant is: I believe a simple combination of static compilation and correct usage of freedesktop standards and unix filesystem structure is enough to cover 90% of the cases, the remaining 10% being non-average users.

> **gabba said:**
> Ubuntu could be as far back as what, 5 months behind the latest version?
The "average" user is bound to run into a website, extension, java plugin (the new "kernel" jvm with finally acceptable speed was only for the latest version, at the time), flash plugin, moonlight plugin, god-knows-what plugin that requires the latest version of Firefox. This category of users often use the latest media technologies much more that the typical programmer or sysadmin.

If he's using a plugin that requires 3.5, such plugin is not in the repositories either. So providing 3.5 would be an incomplete solution anyway.

> **gabba said:**
> I don't see how systematically backporting the latest versions of Firefox, OpenOffice, GIMP and other major apps would affect those. If you're looking for "predictability, stability and consistency", you leave the backports repos disabled anyways.

Actually, those points were referring to an SRU. If you're only talking about backports they do not apply.

---

### Post by Sophont on 2009-09-25
> **Keyper7 said:**
> 

[QUOTE=gabba;7992887]
"Ubuntu is not a rolling release"... what if applying that to the letter slows down Ubuntu's progress on the desktop?

It does. In exchange for predictability, stability and consistency. It's no perfect system, but no perfect system exists.[/QUOTE]

I don't see how a 6-month cycle slows down desktop progress.

None of the issues discussed here are much relevant to most regular users. Bleeding edgers use Arch, Gentoo or Debian Testing (or even experimental), etc... Or they install PPAs on Ubuntu. This is a tiny percentage of people - so no slowdown of desktop adoption here.

And the 6-month cycle doesn't mean you're loosing any speed over time - you just skip interim versions. At next release Ubuntu rebases on Debian Testing and upstream again.

Most of the changes that excite us here on the dev forums are of 0 interest to the rest of humanity and most would consider updates faster than 6-months a hassle. Heck - Canonical introduced 2-year LTS because 6-month is too fast for enterprise use.

---

