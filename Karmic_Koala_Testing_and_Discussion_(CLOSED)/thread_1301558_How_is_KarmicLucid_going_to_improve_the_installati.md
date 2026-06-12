---
title: "How is Karmic/Lucid going to improve the installation of software? Is it enough?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hoppipolla on 2009-10-26
This is the biggest thing playing on my mind about the success of Ubuntu - software installation. I know I've said it before but I think we need, basically we need openSUSE 1-Click or similar. Are we getting something similar to this? :)

Hoppi-hop! :)

---

### Post by RichardLinx on 2009-10-26
add-apt-ppa is an improvement. I can't comment much on this right now because I haven't used the RC for 9.10, but I don't think, usability wise, it will be superior to openSUSE 1 click install. But it will be a good improvement.

---

### Post by samh785 on 2009-10-26
The software center is so simple that my parents (who barely have ever touched *any* computers) can use it with ease. So yeah, I think it's an improvement. :)

---

### Post by hoppipolla on 2009-10-26
> **samh785 said:**
> The software center is so simple that my parents (who barely have ever touched *any* computers) can use it with ease. So yeah, I think it's an improvement. :)

ah but it doesn't have EVERYTHING. And it never could. I love it too, but we need some kind of loose framework that makes adding software simple, an equivalent to 1-Click... don't we?

---

### Post by RichardLinx on 2009-10-26
> **samh785 said:**
> The software center is so simple that my parents (who barely have ever touched *any* computers) can use it with ease. So yeah, I think it's an improvement. :)

Software Centre is an improvement. But it will only include software that's included in the repositories and won't be updated for six months. (ie. Until next release) And I've noticed with this release how quickly outdated software in the repo's can become. 

Compared to Windows where you would download the latest software and install with a GUI. (Install Wizard is it?).

But yes, it's a huge improvement. If anything add-apt-ppa will make getting the latest software a smoother process.

---

### Post by matthew.ball on 2009-10-26
I only have to click once on .deb files? :S

---

### Post by hoppipolla on 2009-10-26
> **matthew.ball said:**
> I only have to click once on .deb files? :S

Yeah I guess so, but usually they don't auto-update or anything as they don't install the repos as well ._.

Do you see my point? I dunno, I just think it needs to be a bit simpler for everyday users, that will really help to pull people across :)

---

### Post by JillSwift on 2009-10-26
> **hoppipolla said:**
> Yeah I guess so, but usually they don't auto-update or anything as they don't install the repos as well ._.

Do you see my point? I dunno, I just think it needs to be a bit simpler for everyday users, that will really help to pull people across :)
What software outside of the repos do "everyday" users need?

add-apt-ppa looks like a step in that direction, however. Hence it's a matter of coming up with a unifying locater.

---

### Post by sisco311 on 2009-10-26
> **hoppipolla said:**
> Yeah I guess so, but usually they don't auto-update or anything as they don't install the repos as well ._.

Do you see my point? I dunno, I just think it needs to be a bit simpler for everyday users, that will really help to pull people across :)

Adding (untrusted) third-party repositories is a security risk.

Did you read the roadmap of Software Center? It seems quite promising.

[https://wiki.ubuntu.com/SoftwareCenter#Roadmap]("https://wiki.ubuntu.com/SoftwareCenter#Roadmap")

---

### Post by hoppipolla on 2009-10-26
> **JillSwift said:**
> What software outside of the repos do "everyday" users need?

add-apt-ppa looks like a step in that direction, however. Hence it's a matter of coming up with a unifying locater.

well, another big advantage is it would mean getting more regular updates of a certain program is easier. For example, let's say during the life of Karmic, Firefox 4 is released and I want it (which is probable). At present, I would have to:

a) Wait for backports to release it for Karmic (which may take time and doesn't happen for every program)

b) Lengthily install the PPAs (or maybe use add-apt-ppa which probably still means I would get development releases which I won't need and will probably still be a little hidden away on the Mozilla site won't it?)

c) Manually install the .debs or compile it (the former means no updates and the latter is beyond the abilities of most users).

Ideally we want to be able to go to the Mozilla page, click the Firefox logo and it installs the new version and repos for updates all at once.

Does add-apt-ppa fulfill this or are there plans for Karmic/Lucid?

---

### Post by tribaal on 2009-10-26
> What software outside of the repos do "everyday" users need?

In the same idea, what "everyday user" needs software that's more recent than 6 month?

- Trib'

---

### Post by bowens44 on 2009-10-26
Do you really find software installation in Ubuntu difficult? I really don't see how it can be any easier unless we can somehow get it to read our minds and install without any physical interaction.

---

### Post by JillSwift on 2009-10-26
> **bowens44 said:**
> Do you really find software installation in Ubuntu difficult? I really don't see how it can be any easier unless we can somehow get it to read our minds and install without any physical interaction.
I want that!

Wait, no I don't. I'd be installing ind de-installing all day. We fickle people need *something* to reign us in!

---

### Post by hoppipolla on 2009-10-26
> **bowens44 said:**
> Do you really find software installation in Ubuntu difficult? I really don't see how it can be any easier unless we can somehow get it to read our minds and install without any physical interaction.

No no ***I*** personally don't! I'm talking about newbie peoples who want something as easy as Winblows (or easier) :)

---

### Post by Tibuda on 2009-10-26
> **hoppipolla said:**
> No no ***I*** personally don't! I'm talking about newbie peoples who want something as easy as Winblows (or easier) :)

Like debian packages? Go to site, download, and click until app is installed.

---

### Post by hoppipolla on 2009-10-26
Case in point:

[http://www.mozilla-europe.org/en/firefox/](http://www.mozilla-europe.org/en/firefox/) (no installer)

[http://wakoopa.com/account/download](http://wakoopa.com/account/download) (repos must be added separately)

[http://www.getsongbird.com/](http://www.getsongbird.com/) (no installer)

See? I mean it's easy as pie for me, but wouldn't you love to see a little "Install this on Ubuntu" button? :)

I might design one actually and send it to Mark Shuttleworth! hehe ^_^

---

### Post by lovinglinux on 2009-10-26
What is add-apt-ppa? I can't find it in the repos.

---

### Post by Tibuda on 2009-10-26
> **hoppipolla said:**
> Case in point:

[http://www.mozilla-europe.org/en/firefox/](http://www.mozilla-europe.org/en/firefox/) (no installer)

[http://wakoopa.com/account/download](http://wakoopa.com/account/download) (repos must be added separately)

[http://www.getsongbird.com/](http://www.getsongbird.com/) (no installer)

See? I mean it's easy as pie for me, but wouldn't you love to see a little "Install this on Ubuntu" button? :)

I might design one actually and send it to Mark Shuttleworth! hehe ^_^

Yeah, but this is up for them to do, not Canonical/Ubuntu. Canonical can only add apps to the official repos.

Songbird is available on GetDeb.

---

### Post by ajgreeny on 2009-10-26
It seems to me that the only way to get what the OP seems to want is a "rolling update" distro, which does not have a specific 6 month version update cycle, but as far as I'm aware most of those are more difficult to deal with than ubuntu in the first place, and therefore will not actually solve his problem.

As a long time user of Ubuntu (I have been using since 5.04) I have got so used to synaptic that it seems to me to be the best system I have so far found for updating and finding new applications.  I have a few ppa repos added and as far as I'm concerned that is as near to one click as it's ever likely to be, and so much easier than windows, in my opinion.  OK, I have to find and enable the ppa repos I want, but as a previous poster says, the only way things could be easier would be if the OS could read my mind, and know before I did, exactly what I want.  Not all new versions of applications are better than the previous ones, in spite of what many think.

Don't forget there are many many windows users who are still using Win XP or Win 2000, or even Win 98, and how old are those?  We should count ourselves lucky and be thankful for what we are beginning to take for granted; the best OS available!

---

### Post by Tibuda on 2009-10-26
> **lovinglinux said:**
> What is add-apt-ppa? I can't find it in the repos.

"add-apt-repository" it is a CLI tool to add repositories. It does the same as adding it from the GUI "Software sources". If you use "ppa:name" (in both CLI and GUI) instead of the full deb-line, it will download the PGP keys for you.

---

### Post by lovinglinux on 2009-10-26
> **danielrmt said:**
> "add-apt-repository" it is a CLI tool to add repositories. It does the same as adding it from the GUI "Software sources". If you use "ppa:name" (in both CLI and GUI) instead of the full deb-line, it will download the PGP keys for you.

Thanks.

---

### Post by RichardLinx on 2009-10-26
> Adding (untrusted) third-party repositories is a security risk.
There is no official list of what is trusted and what is not trusted, it's ultimately up to the user to decide whether an application is safe. All this talk about not worrying about security vulnerabilities in Linux and here we have the perfect post contradicting that argument. 

One day someone is going to leak a virus into a popular package and Ubuntu's invincibility will suddenly fall into question.

> What software outside of the repos do "everyday" users need?
I think people tend to simplify the stereotype of an average user. "Web browsing and word processing, maybe some music and movies. Oh, and some solitaire on the side".
I had a friend give Ubuntu a trial and he wanted the latest version of some miscellaneous media program I don't care to remember. 

It wasn't available in the repo's, only as a tar.gz file. He was stumped. And today I saw an old thread {started mid 2008} which was incidentally bumped, the problem? Getting WinFF which wasn't available in the repo's. Someone (Well, lots of people do it) has to compile and package all the programs. Don't forget that if you download a .deb file from a site like getdeb, there's also the chance of running into dependency hell. Though rare, it can happen. Yes, even with Debian.

---

### Post by hoppipolla on 2009-10-26
> **RichardLinx said:**
> There is no official list of what is trusted and what is not trusted, it's ultimately up to the user to decide whether an application is safe. All this talk about not worrying about security vulnerabilities in Linux and here we have the perfect post contradicting that argument. 

One day someone is going to leak a virus into a popular package and Ubuntu's invincibility will suddenly fall into question.


I think people tend to simplify the stereotype of an average user. "Web browsing and word processing, maybe some music and movies. Oh, and some solitaire on the side".
I had a friend give Ubuntu a trial and he wanted the latest version of some miscellaneous media program I don't care to remember. 

It wasn't available in the repo's, only as a tar.gz file. He was stumped. And today I saw an old thread {started mid 2008} which was incidentally bumped, the problem? Getting WinFF which wasn't available in the repo's. Someone (Well, lots of people do it) has to compile and package all the programs. Don't forget that if you download a .deb file from a site like getdeb, there's also the chance of running into dependency hell. Though rare, it can happen. Yes, even with Debian.

I agree completely :)

These issues need to be addressed and it needs to be as easy as possible for developers to make their software available on Ubuntu :)

I also think some kind of unique button on their sites would catch the attention of people who don't know what this "Ubuntu" thing is and it would get the name out there much more. In my mind it's better to think ambitiously and progressively about this than to just settle on what we've got :)

---

### Post by Pasdar on 2009-10-26
Ubuntu needs to come with an option to upgrade to the latest version of any software in the same way its software update works. New users don't know anything about ppa, and not all software is downloadable in deb packages. Seriously, wtf made Canonical decide that people should have the same software (for everything) for 6 months? I'm not talking about updating xserver here, i'm talking about little things like Skype and you name it... users want the latest version for all of these and they generally don't know how to install it.

It's nice that they have this forum to come to to ask, but one more step is needed... a point where they will not even have a question to ask because everything will be so easy you'd have to be a donkey not to know.

---

### Post by hoppipolla on 2009-10-26
I was actually thinking about this a fair bit, and I had some ideas and came to some small conclusions! :)

First of all, one problem with creating an official button like this:

[IMG]http://files.opensuse.org/opensuse/en/d/dd/Kde4-ymp.png[/IMG]

is that any old spyware or malicious site could get the png file and bug it on there, knowing that users would trust it.  This as far as I can tell is the biggest problem. Other than that an official button and installation procedure involving adding update repos would be really good, as it would get the Ubuntu branding out there.

I think the solution has to be at least Canonical making it easier for developers to package their programs' debian packages with repos and GPG keys and making the procedure more accepted and acknowledged.

I mean, it's impossible to have every program ever made in the official repos IMO, and it's impossible for the Ubuntu guys to keep everything up to date single-handedly. We need some kind of alternative, that's not QUITE as centralised but still uses the same basic underlying system. Hopefully it will move in this way gradually but I do think a bit more could be done :)

---

### Post by sisco311 on 2009-10-26
Click:

[URL="apt://kubuntu-desktop"][IMG]http://files.opensuse.org/opensuse/en/d/dd/Kde4-ymp.png[/IMG]
[/URL]

;)

---

### Post by hoppipolla on 2009-10-26
> **sisco311 said:**
> Click:

[URL="apt://kubuntu-desktop"][IMG]http://files.opensuse.org/opensuse/en/d/dd/Kde4-ymp.png[/IMG]
[/URL]

;)

lol not quite the same when it's already in my enabled repos though is it? xD

We need it to ADD new repos not just do something I could do in Synaptic!

---

### Post by sisco311 on 2009-10-26
> **hoppipolla said:**
> 
We need it to ADD new repos not just do something I could do in Synaptic!

The feature was implemented in apturl, but was disabled for security reasons. 

First we need some kind of rating system for the ppa repos.

[noparse]Something like: Stable/Unstable , Trusted/Untrusted, Maintainer:Dev/Community/Trusted user ...[/noparse]

---

### Post by hoppipolla on 2009-10-26
> **sisco311 said:**
> The feature was implemented in apturl, but was disabled for security reasons. 

First we need some kind of rating system for the ppa repos.

[noparse]Something like: Stable/Unstable , Trusted/Untrusted, Maintainer:Dev/Community/Trusted user ...[/noparse]

That would be cool :)

---

### Post by ajgreeny on 2009-10-26
@Pasdar
> I'm not talking about updating xserver here, i'm talking about little things like Skype and you name it... users want the latest version for all of these and they generally don't know how to install it.
You picked a bad example here as skype is not made available by canonical at all, it comes either direct from skype or via medibuntu.  So a ubuntu user could go to the skype website, download the .deb version from there and install it, just like in windows.  Except, of course those who are used to windows will probably not download the deb, but an exe and then wonder why it won't install.  There is no way round that problem, unfortunately, except for education; "Ubuntu is not windows, so why did you download a windows install file?"

However, to say everybody always wants the latest version of everything is a gross oversimplification of the situation; everybody does not want that.  I agree some people do, and there are ways to get them, although it may not be as simple as you would wish it to be.  Don't forget that somebody has to produce the packages, make sure that there are no unmet dependencies, and that those dependencies do not in turn break any packages already installed by adding new libs etc which may not be usable for something else.  Who is going to do all that when there are more important things to sort out, like the next version of Ubuntu, it's only six months, for goodness sake.

As I already said in a previous post, if you want to always have the most up-to-date package for everything, Ubuntu is probably the wrong distro for you.  Try one of the rolling update distros.

OK, I'll get of my soapbox now that I've had a rant, but I believe many expect too much from ubuntu, and lets face it, they don't pay for it in the first place.

---

### Post by hoppipolla on 2009-10-26
> **ajgreeny said:**
> @Pasdar

You picked a bad example here as skype is not made available by canonical at all, it comes either direct from skype or via medibuntu.  So a ubuntu user could go to the skype website, download the .deb version from there and install it, just like in windows.  Except, of course those who are used to windows will probably not download the deb, but an exe and then wonder why it won't install.  There is no way round that problem, unfortunately, except for education; "Ubuntu is not windows, so why did you download a windows install file?"

However, to say everybody always wants the latest version of everything is a gross oversimplification of the situation; everybody does not want that.  I agree some people do, and there are ways to get them, although it may not be as simple as you would wish it to be.  Don't forget that somebody has to produce the packages, make sure that there are no unmet dependencies, and that those dependencies do not in turn break any packages already installed by adding new libs etc which may not be usable for something else.  Who is going to do all that when there are more important things to sort out, like the next version of Ubuntu, it's only six months, for goodness sake.

As I already said in a previous post, if you want to always have the most up-to-date package for everything, Ubuntu is probably the wrong distro for you.  Try one of the rolling update distros.

OK, I'll get of my soapbox now that I've had a rant, but I believe many expect too much from ubuntu, and lets face it, they don't pay for it in the first place.

Wouldn't it be nice to match or exceed Windows in every way though? If we actually CAN'T do this for some reason, then I think something is wrong. If there are issues causing our system to be inferior or incapable of something Windows/OSX can do then we must fix or revise them.

Personally I think the current system can probably be made to work, but I think we need to think progressively and constructively about how we can make it the best OS possible! :)

---

### Post by johnzollo on 2009-10-26
> **hoppipolla said:**
> 
Personally I think the current system can probably be made to work, but I think we need to think progressively and constructively about how we can make it the best OS possible! :)

agreed

-john

---

### Post by sisco311 on 2009-10-26
> **hoppipolla said:**
> That would be cool :)

from: [https://wiki.ubuntu.com/SoftwareCenter#Roadmap]("https://wiki.ubuntu.com/SoftwareCenter#Roadmap")

October 2010
[list=1]
[*]Integrate the ratings and review mechanism from Launchpad into Ubuntu Software Center. This will likely involve: 

[list]
[*]An interface within the Center for rating and reviewing software that is installed now (or that has been installed recently). 

[*]A mechanism for reporting, and staff for moderating, inappropriate reviews (e.g. those that use offensive language). 
[/list]
[*]Establish a mechanism for establishing and conveying a trust level for software in PPAs, and for easily adding PPAs within the Center.[/list]

---

### Post by hoppipolla on 2009-10-26
> **sisco311 said:**
> from: [https://wiki.ubuntu.com/SoftwareCenter#Roadmap]("https://wiki.ubuntu.com/SoftwareCenter#Roadmap")

October 2010
[list=1]
[*]Integrate the ratings and review mechanism from Launchpad into Ubuntu Software Center. This will likely involve: 

[list]
[*]An interface within the Center for rating and reviewing software that is installed now (or that has been installed recently). 

[*]A mechanism for reporting, and staff for moderating, inappropriate reviews (e.g. those that use offensive language). 
[/list]
[*]Establish a mechanism for establishing and conveying a trust level for software in PPAs, and for easily adding PPAs within the Center.[/list]

That's great :)

You know what, I think chances are my concerns here are unfounded - I think they know what they're doing and probably have some great things in the works!

I should learn to have faith! hehe :)

---

### Post by seeker5528 on 2009-10-28
> **hoppipolla said:**
> 
See? I mean it's easy as pie for me, but wouldn't you love to see a little "Install this on Ubuntu" button? :)

Would be nice, but in the bigger picture, while it certainly doesn't make sense for everything......

When possible Firefox, Songbird, and other higher level stuff should be made available as LSB compliant packages, 

LSB 4 was supposed to update the packaging specification to make it more attractive to ISVs, but if we don't start to see upstream projects make LSB compliant packages available independent of the distribution you are using, whether that is through their own effort or through the effort of volunteers who just do the packaging, what chance is there of winning over the ISVs?

Later, Seeker

---

