---
title: "Firefox 3.5 transition nearing completion. Get ready."
date: 2009-08-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-08-08
Almost all requirements so far have been completed and the ubuntu-mozilla-daily ppa now reflects this.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
[https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5) (outdated?)

---

### Post by dentaku65 on 2009-08-08
> **Starks said:**
> Almost all requirements so far have been completed and the ubuntu-mozilla-daily ppa now reflects this.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
[https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5) (outdated?)

This means that "shiretoko" will be wiped away?

---

### Post by Starks on 2009-08-08
Firefox 3.0 will disappear. Shiretoko will become Firefox. Shiretoko will eventually be replaced by Firefox 3.6, Namaroka.

---

### Post by ghindo on 2009-08-08
Good things come to those who wait :popcorn:

---

### Post by mouchero08 on 2009-08-08
for a noob what does this mean please  .
Fx to be replaced in any further Jaunty upgrade ??

i have 2 pc with jaunty on 1   hardy on another and in both i'm only dipping myself into Ubuntu.

please don't shout @me   [:S]

---

### Post by dentaku65 on 2009-08-08
> **mouchero08 said:**
> for a noob what does this mean please  .
Fx to be replaced in any further Jaunty upgrade ??

i have 2 pc with jaunty on 1   hardy on another and in both i'm only dipping myself into Ubuntu.

please don't shout @me   [:S]

I think this is related to Karmic for FF 3.5 as main browser.
The codename in any Ubuntu versions of FF 3.5 is Shiretoko (at the moment); this will change soon, but for other versions the main browser will remain FF 3.0
Of course you can install FF 3.5 in other versions (or at least afaik in Jaunty) with:
```
sudo apt-get install firefox-3.5
```
All the stuff currently installed in your FF installation (plugins, extensions, bookmarks etc..) will be ported automatically in FF 3.5

I suggest to enable PPA of ubuntu-mozilla team
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
for update the most new version.

---

### Post by yoasif on 2009-08-08
Woo hoo -- same code, I assume, it'll just add some branding?

---

### Post by Simian Man on 2009-08-08
Wow, only took them 3 months.

---

### Post by 23meg on 2009-08-08
> **Simian Man said:**
> Wow, only took them 3 months.

Wow, that cheap jab took someone who didn't help with [the rather beefy task]("https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition") only 3 seconds to type.

---

### Post by zekopeko on 2009-08-08
> **Simian Man said:**
> Wow, only took them 3 months.

Look at the spec. There was significant amount of work to be done.

---

### Post by ghindo on 2009-08-09
> **Simian Man said:**
> Wow, only took them 3 months.Low blow dude :(

---

### Post by vishalrao on 2009-08-09
Fight! :lolflag: (no j/k)

---

### Post by DougieFresh4U on 2009-08-09
> **Starks said:**
> Firefox 3.0 will disappear. Shiretoko will become Firefox. Shiretoko will eventually be replaced by Firefox 3.6, Namaroka.

I use the '3.6a2pre' and it's being called 'Minefield'

---

### Post by taavikko on 2009-08-09
> **DougieFresh4U said:**
> I use the '3.6a2pre' and it's being called 'Minefield'

Take a guess why it's called a minefield ;)
Previous versions were called "minefield" too...

---

### Post by dentaku65 on 2009-08-09
> **DougieFresh4U said:**
> I use the '3.6a2pre' and it's being called 'Minefield'

Just for a while... **Shiretoko/3.5.3pre** at the moment (with the ubuntu-mozilla team repo)

---

### Post by oobuntoo on 2009-08-09
I don't understand why Ubuntu's version of Firefox has to go through so much before it gets released. All I need is for it to theme properly and not look ugly like the one I downloaded from mozilla.com.

---

### Post by 23meg on 2009-08-09
> **oobuntoo said:**
> I don't understand why Ubuntu's version of Firefox has to go through so much before it gets released. All I need is for it to theme properly and not look ugly like the one I downloaded from mozilla.com.

You have very modest requirements :) Some people also need it not to mess up the rest of their applications sharing libraries with it, and not to mess up their existing profiles and cause them to lose data, and be translated well, and actually work with the packaged extensions, and be able to report bugs through Apport, and...

---

### Post by qwertyu on 2009-08-09
Why when a new version of Firefox (or any program) is released for Windows or Mac OS X we can use it immediately and we cannot in Ubuntu (or Linux in general)?

I think this is one of the major drawbacks of Linux...

---

### Post by 23meg on 2009-08-09
> **qwertyu said:**
> Why when a new version of Firefox (or any program) is released for Windows or Mac OS X we can use it immediately and we cannot in Ubuntu (or Linux in general)?

I think this is one of the major drawbacks of Linux...

With Firefox, you can. Go to getfirefox.net, choose the Linux build, download, extract, double click, run. You just won't get the distribution-specific added benefits, some of which I listed in my previous post, which you don't get in those other operating systems either.

---

### Post by dentaku65 on 2009-08-09
> **qwertyu said:**
> Why when a new version of Firefox (or any program) is released for Windows or Mac OS X we can use it immediately and we cannot in Ubuntu (or Linux in general)?

I think this is one of the major drawbacks of Linux...

As far I can say you can download the latest version directly from (in this case) firefox website, install and act as Win or Mac, nobody forbid you to manage your apps in this way.

The difference is when a distribution release the apps officially for the repositories; in this case it is better to have versions that point the status of the release(s); from my part this is a guarantee of security and compatibility; needs time to do this? Yes of course, resources (people and time) are not unlimited.

---

### Post by tekstr1der on 2009-08-09
> **23meg said:**
> With Firefox, you can. Go to getfirefox.net, choose the Linux build, download, extract, double click, run. You just won't get the distribution-specific added benefits, some of which I listed in my previous post, which you don't get in those other operating systems either.

@23meg: Thanks for keeping on keeping on and replying to all these folks that aren't seeing the big Ubuntu picture when it comes to Firefox integration. Boy, I would really expect the type of person who is dabbling with an alpha version of an OS to be fully aware of this concept and also the fact that the vanilla Firefox (with branding) can be downloaded and run on any Linux distro from day one when it's released alongside the Windows and Mac versions!

---

### Post by qwertyu on 2009-08-09
> **tekstr1der said:**
> @23meg: Thanks for keeping on keeping on and replying to all these folks that aren't seeing the big Ubuntu picture when it comes to Firefox integration. Boy, I would really expect the type of person who is dabbling with an alpha version of an OS to be fully aware of this concept and also the fact that the vanilla Firefox (with branding) can be downloaded and run on any Linux distro from day one when it's released alongside the Windows and Mac versions!

Yes, I know I can download every program from it's website and install it.

But why is it necessary to do all this integration work?
Windows and Mac OS programs in theory doesn't need to do all this process...

I know that Ubuntu team works for a better integration with the packages on the repository and to make sure that everything work but, does this means that everything that isn't on the repo maybe doesn't work properly? Is it the lack of a Linux standard (different distributions, KDE, Gnome, etc) what makes that every program after the offical release from the depelover, needs to be "ported" to each distribution?

---

### Post by Regenweald on 2009-08-09
> **qwertyu said:**
> Yes, I know I can download every program from it's website and install it.

But why is it necessary to do all this integration work?
Windows and Mac OS programs in theory doesn't need to do all this process...

I know that Ubuntu team works for a better integration with the packages on the repository and to make sure that everything work but, does this means that everything that isn't on the repo maybe doesn't work properly? Is it the lack of a Linux standard (different distributions, KDE, Gnome, etc) what makes that every program after the offical release from the depelover, needs to be "ported" to each distribution?

have a read, edify yourself: [https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5)

and feel free to read the FULL spec: [https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)

---

### Post by dentaku65 on 2009-08-09
> **qwertyu said:**
> Yes, I know I can download every program from it's website and install it.

But why is it necessary to do all this integration work?
Windows and Mac OS programs in theory doesn't need to do all this process...

I know that Ubuntu team works for a better integration with the packages on the repository and to make sure that everything work but, does this means that everything that isn't on the repo maybe doesn't work properly? Is it the lack of a Linux standard (different distributions, KDE, Gnome, etc) what makes that every program after the offical release from the depelover, needs to be "ported" to each distribution?

You make a little bit of confusion here. Linux (the kernel) IS a standard.
The applications belongs, in the case of your complain, to the distribution for security and compatibility reason; but you can install by your own directly at your own risk (like in Win and Mac); maybe for you Red Hat, Ubuntu or openSUSE are the same thing (same OS).

---

### Post by Simian Man on 2009-08-09
> **qwertyu said:**
> Why when a new version of Firefox (or any program) is released for Windows or Mac OS X we can use it immediately and we cannot in Ubuntu (or Linux in general)?

I think this is one of the major drawbacks of Linux...

It's really the Debian style of packaging where everything has to be done in a specific way and they make non-trivial modifications of programs.  This way Debian, and Ubuntu, do packaging is kind of unmaintainable.  If one wants Firefox to have all these features, shouldn't they just, you know, join the Firefox team?

Most distributions will take the upstream applications, package them up and test that they don't break anything when installed and ran, and that's usually about it.  Fedora 11 has had 3.5 since well before it was even released and most other distros have had it for a while as well - at least for the *development version*.

This also causes the weird thing Debian users have with "stability".  They often do not consider something stable until well after it has been released.  The Firefox team wouldn't have released 3.5 if it wasn't stable and, honestly, any instability in Debian packages is likely caused by a combination of their own unrealistic requirements combined with the ineptitude of many of their packagers.

Well, I won't sully this thread with this argument any longer, but suffice it to say that if you want to be using the normal, upstream applications in a reasonable amount of time, Debian and Ubuntu are not good distros.

---

### Post by tekstr1der on 2009-08-09
> **Simian Man said:**
> ...if you want to be using the normal, upstream applications in a reasonable amount of time, Debian and Ubuntu are not good distros.

I've got to admit, though I'm an avid Ubuntu user, this is where Arch really rules with a rolling release model. Six months is still a fairly quick cycle and we all presumably live with it. Really only a hassle when stable stuff is released late in or just after a Ubuntu development cycle and doesn't make it into the release (e.g. OpenOffice 3.0 for Intrepid or Firefox 3.5 for Jaunty).

---

### Post by OliW on 2009-08-09
Does anybody know what's happening regarding profile migration?

I have separate Firefox and Shiretoko profiles. I'm happy with that. But when things move up, I want my current Firefox profile to be my new Firefox profile (instead of my current Shiretoko one).

Any idea if that is the default behaviour?

---

### Post by tekstr1der on 2009-08-09
Not sure what the official plan is, but personally I'd just scrap my profiles all together and start a freshee. If you're really into hanging onto your profile, simply start Firefox with the profile manager

```
firefox-3.5 -profilemanager 
```

Select the profile you want, make it default, kill off the other one and restart Firefox normally. Maybe you know all this and are just wondering what Ubuntu plans to do? If so, sorry I wasted our time!

---

### Post by Starks on 2009-08-09
You could always copy the profile folders to where you want them.

---

### Post by dentaku65 on 2009-08-09
> **OliW said:**
> Does anybody know what's happening regarding profile migration?

I have separate Firefox and Shiretoko profiles. I'm happy with that. But when things move up, I want my current Firefox profile to be my new Firefox profile (instead of my current Shiretoko one).

Any idea if that is the default behaviour?

I think there is a "copy-carbon" of the two profiles; I'm not sure (because I'm usung only Shiretoko) but you should have the same stuff on both versions except the unsupported extensions on FF 3.5 side. You can try to save a bookmark on FF 3.0 then check if is saved on Shiretoko.

---

### Post by Merk42 on 2009-08-09
*waits for the same comments/questions to be brought up in Karmic+1's Firefox 3.6 transition*

---

### Post by zekopeko on 2009-08-09
I just install 3.5 in jaunty and it ask if you want to import settings from 3.0 or keep the ones from 3.5 alpha/beta that you were using.

---

### Post by ghindo on 2009-08-10
> **Merk42 said:**
> *waits for the same comments/questions to be brought up in Karmic+1's Firefox 3.6 transition*We'll cross that bridge when we get to it.

---

### Post by novafluxx on 2009-08-10
This is what makes me want to use Arch…the fact that when the devs of the program/library/plugin say its stable, Arch puts it in the release…no waiting around.

> **tekstr1der said:**
> I've got to admit, though I'm an avid Ubuntu user, this is where Arch really rules with a rolling release model. Six months is still a fairly quick cycle and we all presumably live with it. Really only a hassle when stable stuff is released late in or just after a Ubuntu development cycle and doesn't make it into the release (e.g. OpenOffice 3.0 for Intrepid or Firefox 3.5 for Jaunty).

---

### Post by gnomeuser on 2009-08-10
> **Merk42 said:**
> *waits for the same comments/questions to be brought up in Karmic+1's Firefox 3.6 transition*

I wonder though, looking at the other interesting datapoint in the migration report. When will this be unimportant, more and more projects are moving to Webkit (a rough estimate seems to be that instead of migrating to xulrunner 1.9.1 half the projects elected to switch to webkit this time).

I would wager that Firefox might not have long to win back the platform, they shunned application developers for a long time and have not managed to clean up their API to make it nice to work with. Their failure to do so might end up making Firefox the only Xulrunner user or one of very few at least, this means we will be carrying all that code for basically one application only.

Once we get to the point of having such a shrinking userbase for xulrunner, it might be attractive to simply replace Firefox with another browser to save space and reduce the amount of code we have to maintain (firefox being especially tricky due to the vast amounts of security problems this has had historically and continues to have). Other problem would include Mozillas lack of commitment to Linux, their poor integration with the underlying platform and poor performance on Linux. They are making it very hard to love them.

At the current rate I would wager a year from now we might be forced to face this issue, how it is resolved especially over time as alternatives such as chromium grow strong will be mighty interesting.

For now, bring on Firefox 3.5.

---

### Post by djchandler on 2009-08-10
Your suggestion about using another browser raises an interesting point. What browsers would be considered?

If you install Epiphany now from the repositories, it uses Gecko to render web pages. It's nearly as dependent on Mozilla as Firefox or its derivatives are. It is my understanding that Epiphany 2.27.x will exclusively use Webkit to render pages. Is there any push in that direction? Does Midori (browser, not MS codename) have a future?

You can install Midori and Epiphany (2.26.x) now from the repositories. If you want to give Firefox 3.5 a try in Jaunty, try the Abrowser version. It seems to have fewer complications than Shiretoko did.  Abrowser was better at integrating my existing Firefox 3.0.x extensions and plugins.

---

### Post by Regenweald on 2009-08-10
Once Chromium completes its native 64bit i believe that it and Epiphany Webkit would be strong contenders. I favour chromium. Neither my Xp install nor Ubuntu contain firefox anymore. Firefox's hard drive bug a few weeks ago convinced me to switch.

---

### Post by Merk42 on 2009-08-10
> **Regenweald said:**
> Once Chromium completes its native 64bit i believe that it and Epiphany Webkit would be strong contenders. I favour chromium. Neither my Xp install nor Ubuntu contain firefox anymore. Firefox's hard drive bug a few weeks ago convinced me to switch.

I would hope once Chromium supported extensions it would be considered default.
I'd much rather have a 32bit browser with extensions in a 64bit OS  than a 64bit extension-less browser.

What Hard Drive bug?

---

### Post by zekopeko on 2009-08-10
> **Merk42 said:**
> What Hard Drive bug?

I think that Regenwald is talking about the one on Windows in 3.5 .
Anyway they (in their brilliance) would read the temp folder of Windows AND IE. Every file, every byte in the file to generate some sort of crypto key for the FF session, needed for https or some such thing. It could take minutes to start FF depending on the size of the temp folders.

On Linux the problem was excessive use of fsync which would make FF unresponsive due to massive disk writing. You might have crossed paths with this one. I know I did.

I'm using Chromium now on my Win desktop and Linux netbook since it starts fast and IS fast. Install privoxy, set the Chrome proxy server to 127.0.0.1:8118 and there go the ads. Works nice with minor inconveniences. I'm hoping for adblock once Chrome 3.0 is out with extension support.

---

### Post by rudenko_ruslan on 2009-08-10
[https://launchpad.net/ubuntu/karmic/+source/firefox-3.0/3.0.13+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/firefox-3.0/3.0.13+nobinonly-0ubuntu2)
[https://launchpad.net/ubuntu/karmic/+source/firefox-3.5/3.5.2+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/firefox-3.5/3.5.2+nobinonly-0ubuntu2)

Hooray!

---

### Post by Regenweald on 2009-08-10
> **Merk42 said:**
> I would hope once Chromium supported extensions it would be considered default.
I'd much rather have a 32bit browser with extensions in a 64bit OS  than a 64bit extension-less browser.

What Hard Drive bug?

not so much a hard drive bug as Firefox 3.5 in windows would intermittently go crazy and eat cpu cycles and send my hd thrashing. Most research in the internet results in blog entries. Since i don't use add ons or extensions(basically firefox bare) and taskmanager showed 100% cpu and 90-100% IO. It was firefox. I'm sorry i can't provide any better resources on the matter, needless to say it seemed quite random as some did not experience anything of the sort.

This is one of the many blogs ( not reliable news but should give an idea) [http://weblogs.asp.net/fbouma/archive/2009/07/09/the-firefox-3-5-fiasco.aspx](http://weblogs.asp.net/fbouma/archive/2009/07/09/the-firefox-3-5-fiasco.aspx)

Edit: thanks zekopeko :) as i could not find proper documentation on it i was fearful of posting a blog entry. I know the rules :)

---

### Post by wayne_cat on 2009-08-10
> **rudenko_ruslan said:**
> [https://launchpad.net/ubuntu/karmic/+source/firefox-3.0/3.0.13+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/firefox-3.0/3.0.13+nobinonly-0ubuntu2)
[https://launchpad.net/ubuntu/karmic/+source/firefox-3.5/3.5.2+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/karmic/+source/firefox-3.5/3.5.2+nobinonly-0ubuntu2)

Hooray!

hmmm ... since 10 minutes in the queue

[https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=](https://edge.launchpad.net/ubuntu/karmic/+queue?queue_state=3&queue_text=)

This version also has the "wonderful Multisearch" add-on?

---

### Post by aamukahvi on 2009-08-10
> **djchandler said:**
> If you install Epiphany now from the repositories, it uses Gecko to render web pages. It's nearly as dependent on Mozilla as Firefox or its derivatives are. It is my understanding that Epiphany 2.27.x will exclusively use Webkit to render pages. Is there any push in that direction?
```
sudo aptitude install epiphany-webkit
```
This is 2.27.3 from karmic/universe.

---

### Post by andrewabc on 2009-08-10
> **Regenweald said:**
> not so much a hard drive bug as Firefox 3.5 in windows would intermittently go crazy and eat cpu cycles and send my hd thrashing. Most research in the internet results in blog entries. Since i don't use add ons or extensions(basically firefox bare) and taskmanager showed 100% cpu and 90-100% IO. It was firefox. I'm sorry i can't provide any better resources on the matter, needless to say it seemed quite random as some did not experience anything of the sort.

This is one of the many blogs ( not reliable news but should give an idea) [http://weblogs.asp.net/fbouma/archive/2009/07/09/the-firefox-3-5-fiasco.aspx](http://weblogs.asp.net/fbouma/archive/2009/07/09/the-firefox-3-5-fiasco.aspx)

Edit: thanks zekopeko :) as i could not find proper documentation on it i was fearful of posting a blog entry. I know the rules :)

It's not just you, I think happens to many people.
With firefox on windows xp and ubuntu when typing in addressbar and it searches for my links hard drive thrashes, and when browsing bookmarks or adding bookmarks hard drive thrashes. 

There is 20mb sqlite database in your profile that is constantly getting data written in and out of, which slows firefox down.

If you can follow and properly implement [Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475) it will make firefox much faster and no more hard drive thrashing. I tried it but it was very unstable for me (see last couple pages for my posts).

Glad to see 3.5 as default. Now when people download alpha 4 in a couple days they can test it and no one has to listen or waste time explaining why 3.5 isn't default.

---

### Post by alphacrucis2 on 2009-08-10
It's landed on my test machine. 

Multisearch is still there.

---

### Post by zekopeko on 2009-08-10
> **alphacrucis2 said:**
> It's landed on my test machine. 

Multisearch is still there.

Multisearch should be gone by alpha4. It's only a user interaction test.

---

### Post by wayne_cat on 2009-08-10
> **zekopeko said:**
> Multisearch should be gone by alpha4. It's only a user interaction test.

I saw this was mentioned in one of the  bug reports ... so it is a final decision to remove it in A4?

---

### Post by zekopeko on 2009-08-10
> **wayne_cat said:**
> I saw this was mentioned in one of the  bug reports ... so it is a final decision to remove it in A4?

They said that it is only meant to be used between alpha3 and alpha4. Further then that I don't know.

---

### Post by wayne_cat on 2009-08-10
> **zekopeko said:**
> They said that it is only meant to be used between alpha3 and alpha4. Further then that I don't know.

thanks for the clarification

---

### Post by Darkshade on 2009-08-10
Ok, Shiretoko is now called Firefox. What was the big deal anyway? :popcorn:

---

### Post by Regenweald on 2009-08-10
> **andrewabc said:**
> It's not just you, I think happens to many people.
With firefox on windows xp and ubuntu when typing in addressbar and it searches for my links hard drive thrashes, and when browsing bookmarks or adding bookmarks hard drive thrashes. 

There is 20mb sqlite database in your profile that is constantly getting data written in and out of, which slows firefox down.

If you can follow and properly implement [Howto; Firefox profile in RAM for increased speed and stability](http://ubuntuforums.org/showthread.php?t=1120475) it will make firefox much faster and no more hard drive thrashing. I tried it but it was very unstable for me (see last couple pages for my posts).

Glad to see 3.5 as default. Now when people download alpha 4 in a couple days they can test it and no one has to listen or waste time explaining why 3.5 isn't default.

The thrashing kind of saddened me for a final release. Anyway, i did come across that howto but it seemed like quite a bit of work at the time and firefox was performing well. Now my solution is to simply install a faster browser with better performance.

Would be a very nice feature if in future a browser implemented 'load into RAM' as a editable preference, but that would be a hell of a lot of work for the devs.

---

### Post by zekopeko on 2009-08-10
> **Darkshade said:**
> Ok, Shiretoko is now called Firefox. What was the big deal anyway? :popcorn:

Impatient people.

---

### Post by jithin1987 on 2009-08-11
In karmic firefox 3.5 in Languages under addons windows says 

Firefox(en-GB) and Xulrunner(en-GB) not compatible with Firefox 3.5.2

Is this normal or how do I fix this?

---

### Post by jocko on 2009-08-11
> **jithin1987 said:**
> Is this normal or how do I fix this?
Yes, it's normal and to fix it, just wait. You are running an alpha version. Those packages will get updated eventually.

---

### Post by taavikko on 2009-08-11
> **jithin1987 said:**
> In karmic firefox 3.5 in Languages under addons windows says 

Xulrunner(en-GB) not compatible with Firefox 3.5.2


That's the version that FF3.0 uses, so no worries, 
Can't say about the languages....

---

### Post by dentaku65 on 2009-08-11
> **zekopeko said:**
> Impatient people.

Well it is not only that. It happens to me that on some site the user-agent with Shiretoko cause the message "this site is available for FF 3.0 or above, please upgrade your browser" :-)

---

### Post by rudenko_ruslan on 2009-08-11
[https://lists.ubuntu.com/archives/karmic-changes/2009-August/006000.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006000.html)

So, goodbye "Multisearch"?

---

### Post by taavikko on 2009-08-11
> **rudenko_ruslan said:**
> [https://lists.ubuntu.com/archives/karmic-changes/2009-August/006000.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/006000.html)

So, goodbye "Multisearch"?

That only affect's the FF-3.0 let's wait for the announcement for
FF-3.5 before saying "au revoir" to it.

---

### Post by tekstr1der on 2009-08-11
> **jithin1987 said:**
> In karmic firefox 3.5 in Languages under addons windows says 

Firefox(en-GB) and Xulrunner(en-GB) not compatible with Firefox 3.5.2

Is this normal or how do I fix this?

Looks like some cruft left behind. First I purged firefox-3.0 then I determined what was leftover and deleted it.

First the en-gb language pack:
```
sudo rm -r /usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com
```

An old empty unused plugin path:
```
sudo rm -r /usr/lib/firefox-addons/plugins
```

Finally the old xulrunner addon:
```
sudo rm -r /usr/lib/xulrunner-addons/extensions/langpack-en-GB@xulrunner-1.9.ubuntu.com
```

I do wish they would do a better job of cleanup. This is all Ubuntu installed cruft. It should be uninstalled by Ubuntu. Firefox cleans up after itself, but is not aware of these extras installed with Ubuntu.

---

### Post by zekopeko on 2009-08-11
@tekstr1der

report a bug. The transition should be clean.

---

### Post by pressureman on 2009-08-11
> **dentaku65 said:**
> Well it is not only that. It happens to me that on some site the user-agent with Shiretoko cause the message "this site is available for FF 3.0 or above, please upgrade your browser" :-)

Type about:config in the address bar, then filter the settings by 'general.useragent'. You can override the useragent that Firefox sends.

---

### Post by jithin1987 on 2009-08-11
> **tekstr1der said:**
> Looks like some cruft left behind. First I purged firefox-3.0 then I determined what was leftover and deleted it.

First the en-gb language pack:
```
sudo rm -r /usr/lib/firefox-addons/extensions/langpack-en-GB@firefox-3.0.ubuntu.com
```

An old empty unused plugin path:
```
sudo rm -r /usr/lib/firefox-addons/plugins
```

Finally the old xulrunner addon:
```
sudo rm -r /usr/lib/xulrunner-addons/extensions/langpack-en-GB@xulrunner-1.9.ubuntu.com
```

I do wish they would do a better job of cleanup. This is all Ubuntu installed cruft. It should be uninstalled by Ubuntu. Firefox cleans up after itself, but is not aware of these extras installed with Ubuntu.

I did that now the entire languages section is gone. Is that ok?

---

### Post by tekstr1der on 2009-08-11
Well, provided those two broken "add-ons" were the only things listed under the languages tab, then yes, that is what you had desired based on your original post.

---

### Post by rudenko_ruslan on 2009-08-11
> **taavikko said:**
> That only affect's the FF-3.0 let's wait for the announcement for
FF-3.5 before saying "au revoir" to it.
I'm now running Firefox 3.5.2 and there is no "Multisearch" thing in Extensions list.

---

### Post by wayne_cat on 2009-08-11
> **jithin1987 said:**
> I did that now the entire languages section is gone. Is that ok?

The language settings appear again if you install a language pack. Firefox uses en_US if there 
is no other (active) language pack .. the answer to your question ... yes, it is ok. ;)

---

### Post by jithin1987 on 2009-08-11
> **wayne_cat said:**
> The language settings appear again if you install a language pack. Firefox uses en_US if there 
is no other (active) language pack .. the answer to your question ... yes, it is ok. ;)

Can you tell me which packages to install to get en-GB?

Also I don't understand xulrunner listed under the language pack.

---

### Post by wayne_cat on 2009-08-11
> **jithin1987 said:**
> Can you tell me which packages to install to get en-GB?

Also I don't understand xulrunner listed under the language pack.

_**The language pack**_:

[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-i686/xpi/en-GB.xpi](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/latest/linux-i686/xpi/en-GB.xpi)

_**The British dictionary:**_

[https://addons.mozilla.org/en-US/firefox/tag/British](https://addons.mozilla.org/en-US/firefox/tag/British)




I have already removed xulrunner (from the command line) ... it was listed under languages?

---

### Post by jithin1987 on 2009-08-14
The en-Gb language parts came back automatically again. The only action I did recently with firefox was completely removing firefox-3.1 from my system.

[IMG]http://farm3.static.flickr.com/2487/3821634113_8a35153f36_o.png[/IMG]

---

### Post by Wiebelhaus on 2009-08-14
> **Starks said:**
> Almost all requirements so far have been completed and the ubuntu-mozilla-daily ppa now reflects this.

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
[https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition](https://wiki.ubuntu.com/MozillaTeam/Specs/Karmic/Firefox35Transition)
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5](https://blueprints.launchpad.net/ubuntu/+spec/desktop-karmic-firefox-3.5) (outdated?)

Awesome! Thanks a billion.

---

### Post by wayne_cat on 2009-08-15
> **jithin1987 said:**
> The en-Gb language parts came back automatically again. The only action I did recently with firefox was completely removing firefox-3.1 from my system.



the same problem here ... They came after restarting firefox.

---

### Post by Merk42 on 2009-08-15
When the transition is done, is it also going to apply to Jaunty since "Firefox-3.5" is in those repos?

If not, why was it in the Jaunty repos in the first place?

---

### Post by andrewabc on 2009-08-15
> **Merk42 said:**
> When the transition is done, is it also going to apply to Jaunty since "Firefox-3.5" is in those repos?

If not, why was it in the Jaunty repos in the first place?

I do not think it will be in jaunty by default as update. They rarely update older software to their newest versions.

It was included for people who wanted 3.5
When Jaunty was released 3.5 was not final, so that is why 3.5 was not default but at least they have official ubuntu install in repos.

---

### Post by kklimonda on 2009-08-15
No, Jaunty is going to have a Firefox 3.0 as a default browser. Also, official branding won't be applied to Firefox 3.5 in Jaunty.

---

### Post by Merk42 on 2009-08-16
> **kklimonda said:**
> No, Jaunty is going to have a Firefox 3.0 as a default browser. Also, official branding won't be applied to Firefox 3.5 in Jaunty.

Okay, which again begs the question, why was firefox-3.5 in Jaunty's repos **at all**?

Is Karmic getting 3.6 in its repos even though it will never be default and always called Namaroka so the user is better off just using Ubuntuzilla anyway?

---

### Post by meborc on 2009-08-16
> **Merk42 said:**
> Okay, which again begs the question, why was firefox-3.5 in Jaunty's repos **at all**?

Is Karmic getting 3.6 in its repos even though it will never be default and always called Namaroka so the user is better off just using Ubuntuzilla anyway?

i never quite understood what firefox version i'm supposed to use :) so i usually use the latest minefield from [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

at the moment, i'm running firefox 3.7a1pre

it does not matter to me what is the default browser of ubuntu because the toughness of security updates and regulation, the default is always a step behind the actual development

---

### Post by 23meg on 2009-08-16
> **tekstr1der said:**
> @23meg: Thanks for keeping on keeping on and replying to all these folks that aren't seeing the big Ubuntu picture when it comes to Firefox integration. Boy, I would really expect the type of person who is dabbling with an alpha version of an OS to be fully aware of this concept 

You're welcome. Most people who visit this forum don't actually follow the blueprints and mailing list discourse, hence the shortage of genuine information, and the inflation of hearsay. All we can do is make people aware of where the information is, and counter hearsay with fact.

> **tekstr1der said:**
> and also the fact that the vanilla Firefox (with branding) can be downloaded and run on any Linux distro from day one when it's released alongside the Windows and Mac versions!

I think most people are aware of that, but apparently some are stuck with the impression that "in Linux you can't just download a vendor-provided binary and expect it to run without messing with runtime dependencies".

> **Merk42 said:**
> Okay, which again begs the question, why was firefox-3.5 in Jaunty's repos **at all**?

[http://ubuntuforums.org/showpost.php?p=7566029&postcount=35](http://ubuntuforums.org/showpost.php?p=7566029&postcount=35)

[quote=Merk42]Is Karmic getting 3.6 in its repos even though it will never be default and always called Namaroka so the user is better off just using Ubuntuzilla anyway?[/QUOTE]

It isn't expected that 3.6 will be final before Karmic is released. That was the case with Firefox 3.5 and Jaunty, so a transition to 3.5 was required in the Jaunty development cycle.

---

### Post by xebian on 2009-08-16
Didn't check but sometimes it's in the backports.  Check if you have it enabled.

---

### Post by andrewabc on 2009-08-16
> **Merk42 said:**
> Okay, which again begs the question, why was firefox-3.5 in Jaunty's repos **at all**?

Why not?

With 3.5 in jaunty it meant people could use 3.5 from repos, and test/use it. I'm not sure what the problem is. 9.04 was released in April, ff3.5 was released in July(?). No reason for 3.5 to become default. Ubuntu doesn't go upgrading all the software everytime a new upstream version is released. That's what the 6 month upgrade cycle is for or backports.

So far no ff3.6 in karmic
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Maybe they'll add it in the repo later.

---

### Post by xebian on 2009-08-16
> **andrewabc said:**
> Why not?

..I'm not sure what the problem is. 9.04 was released in April, ff3.5 was released in July(?). ..Ubuntu doesn't go upgrading all the software everytime a new upstream version is released. That's what the 6 month upgrade cycle is for or backports.

..

FF upgrade is not just any version upgrade.  They are security updates, and you can't just leave jaunty users vulnerable would you?  Ubuntu must apply these security updates not just for LTS but for any versions still valid out there.  It's the moral responsiblity.

---

### Post by Merk42 on 2009-08-16
> **xebian said:**
> FF upgrade is not just any version upgrade.  They are security updates, and you can't just leave jaunty users vulnerable would you?  Ubuntu must apply these security updates not just for LTS but for any versions still valid out there.  It's the moral responsiblity.

I'm not positive, but I don't think that's the case.
3.0.13 came out August 3rd, months after 3.5
3.5.2 came out on August 3rd as well.  So I'm guessing for a while any security updates found in 3.5.X, if applicable, will be applied to 3.0.X

---

### Post by andrewabc on 2009-08-16
> **xebian said:**
> FF upgrade is not just any version upgrade.  They are security updates, and you can't just leave jaunty users vulnerable would you?  Ubuntu must apply these security updates not just for LTS but for any versions still valid out there.  It's the moral responsiblity.

Mozilla is still supporting 3.0 as of now (security), so I'm not sure what you're going on about. Jaunty/intrepid/hardy users are still receiving 3.0 updates. I'm not sure when 3.0 support ends.

I'm not sure what your argument for updating to 3.5 has to do with security updates when 3.0 still has security updates.

---

### Post by ghindo on 2009-08-17
Has anybody else experienced regeressions with 3.5?  Some websites aren't rendering correctly with 3.5, but render fine with 3.0, Midori, etc.

---

### Post by wfp on 2009-08-19
Yes on karmic64-bit pages are rendering really slow. Also some images do not show up at all. I had the same problem on fedora64-bit,
and on saybayon64-bit. Not sure if this is just a 64-bit problem or not. firefox 3.0.13 runs great.

---

