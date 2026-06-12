---
title: "Google Chrome soon for GNU/Linux"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-12
[http://news.cnet.com/8301-17939_109-10138388-2.html?tag=rtcol;newsNow](http://news.cnet.com/8301-17939_109-10138388-2.html?tag=rtcol;newsNow)

Don't think it will make into jaunty but perhaps for jaunty+1. ?

Queries, questions all good. 

On second thought, they could give us the test shell so atleast we know little bit about the interface.

---

### Post by Martje_001 on 2009-01-12
Is it under GPL then?

---

### Post by binbash on 2009-01-12
I am waiting this for months : )

---

### Post by jfernyhough on 2009-01-12
Chromium is, which is Chrome's GPL base. It includes V8 (which is itself GPL) and is what I've been using on Windows since Chrome was released. The Chromium development snapshots give new features way before they are released as part of Chrome.

Maybe Canonical could create their own browser release based on Chromium? :O
(I'm copyrighting that idea, btw Canonical ;) )

---

### Post by bpl07 on 2009-01-12
There's a package for the testshell built in [fta's ppa]("https://launchpad.net/~fta/+archive").  He hasn't updated it in a while, but you can at least play with something for now.  Or you can try [compiling the code yourself]("http://code.google.com/p/chromium/wiki/LinuxBuildInstructions").

---

### Post by Slug71 on 2009-01-12
Well im looking forward to it. I think anything is better than Firefox at the moment.

---

### Post by ubulette on 2009-01-12
I've been busy so my package is kind of stalled.
It's not meant for testing at this point anyway. It was more to see if I got the initial bits correct, then i planed to improve it incrementally as time permits. And it's a test suite, not a browser [1].

But don't hold your breath just yet. It's far from ready, even upstream says so. The article also clearly says that there's only test_shell, and it's pretty raw. I'm sure something will come up at some point but unless there's a huge boost of external contributions, I doubt we'll see something this semester. There's just too much left to do.
If you want native 64bit, it's an either further goal.

[1] I like the idea of packaging a test suite so I'm doing the same thing for Mozilla, that's a lot of work too. The idea is to run those test suites at build time and also provide a package users could run themselves in their systems. I think it's good to improve QA, it's not really for end-users but in the end, they should get the benefits of this.

---

### Post by plun on 2009-01-12
> **ubulette said:**
>  And it's a test suite, not a browser [1].

 I think it's good to improve QA, it's not really for end-users but in the end, they should get the benefits of this.

Yup... I knows..:)

A rather unstable test shell, tested just for fun and was really surprised when something came up...

---

### Post by Martiini on 2009-03-08
chromium-browser 2.0.168.0~svn20090303r10836-0ubuntu1~fta1

from

[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

works ok .. at least for me

---

### Post by hockeyhead019 on 2009-03-08
it'll be interesting to see how this develops and grows but yea i just tested the shell for a little... it's very "raw" as they said haha but works

---

### Post by kindofabuzz on 2009-03-09
> **Slug71 said:**
> Well im looking forward to it. I think anything is better than Firefox at the moment.

there is NOTHING better than Firefox! FF rocks my socks!

---

### Post by Nullack on 2009-03-09
Chromes javascript is substantially faster than FF, hopefully for the fanbois of FF they will pick up Chromes technique.

---

### Post by kindofabuzz on 2009-03-09
> **Nullack said:**
> Chromes javascript is substantially faster than FF, hopefully for the fanbois of FF they will pick up Chromes technique.

reason why chrome runs faster is because there are no addons. FF runs just as fast without addons. Try a FF 3.1 nightly build sometime. JIT rocks.

---

### Post by Nullack on 2009-03-09
Untrue, look more deeply into the V8 javascript engine technology and benchmark results.

---

### Post by kindofabuzz on 2009-03-09
> **Nullack said:**
> Untrue, look more deeply into the V8 javascript engine technology and benchmark results.

well i haven't even sen chrome in action since no linux builds are out. I'm not installing windows just to try out a browser. I've been with FF since version .5, and I think I'll stay. I'd rather not support the monopoly which is Google. :D

---

### Post by cl333r on 2009-03-09
> **Slug71 said:**
> Well im looking forward to it. I think anything is better than Firefox at the moment.
+1
The 3 reasons I'm waiting for Chrome on Linux:
1) Firefox (especially on Linux) has the slowest startup among any other browser I know that exists on Earth to this day, even with no addon.
2) Mozilla might finally pay enough attention to the Linux code, cause, as I tested the latest daily build of FF 3.2, the Linux version is still like 30-40% slower than the windows one, this is not rants, this is truth, test it yourself if you have Linux & xp dual boot and compare a few benchmarks.
3) If Mozilla plans to stay relevant it should understand that RAM is already dirt cheap and will be even cheaper so saying they save RAM by not implementing a per-process tab browsing to save like 5MB/tab is a reason for a fewer people, and will become a _lame_ excuse in the very near future, so it must start working on it now before it's not too late. I and many other Linux/MS users had enough crashes because of one single tab crashed.

---

### Post by gnomeuser on 2009-03-09
When I visited my fiancée last december I got to spend a month using Chrome (since she is a Vista user and I didn't bring my laptop). It is an amazing browser, I cannot wait for it to come to Linux. The one thing I love the most is probably the single process per tab feature, any standard browser that crashes takes down the whole thing however Chrome does not. Aside this it's user interface has very good design, it's blazingly fast and it's defaults are well picked.

I cannot wait to have some Chrome on my Linux.

---

### Post by plun on 2009-03-09
> **Nullack said:**
> Untrue, look more deeply into the V8 javascript engine technology and benchmark results.

It should be compared with **_FF3.2_** and Ubuntus mozilla-team got builds.

Fabien also build those....:D

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

asac's presentation
[http://www.asoftsite.org/s9y/archives/158-Ubuntu-Mozilla-Daily-Archive-with-firefox-3.1-and-3.2-for-hardy,-intrepid-and-jaunty.html](http://www.asoftsite.org/s9y/archives/158-Ubuntu-Mozilla-Daily-Archive-with-firefox-3.1-and-3.2-for-hardy,-intrepid-and-jaunty.html)

Without measuring with real benchmarking chromium seems to be a little faster and that the Mozilla project must decide how their tactic should be in future.  **FF3.1** is delayed because of the script-engine as I understands it.

---

### Post by olskar on 2009-03-09
> **gnomeuser said:**
> When I visited my fiancée last december I got to spend a month using Chrome (since she is a Vista user and I didn't bring my laptop). It is an amazing browser, I cannot wait for it to come to Linux. The one thing I love the most is probably the single process per tab feature, any standard browser that crashes takes down the whole thing however Chrome does not. Aside this it's user interface has very good design, it's blazingly fast and it's defaults are well picked.

I cannot wait to have some Chrome on my Linux.

Is the single process per tab working? Last time I checked all were under the same process (PID 7696). Google Chrome includes it's very own processmanager, you can access it with about:memory.

---

### Post by zika on 2009-03-09
> **kindofabuzz said:**
> reason why chrome runs faster is because there are no addons. FF runs just as fast without addons. Try a FF 3.1 nightly build sometime. JIT rocks.
+1 try 3.2 nightly!

---

### Post by kindofabuzz on 2009-03-09
> **cl333r said:**
> +1
The 3 reasons I'm waiting for Chrome on Linux:
1) Firefox (especially on Linux) has the slowest startup among any other browser I know that exists on Earth to this day, even with no addon.
2) Mozilla might finally pay enough attention to the Linux code, cause, as I tested the latest daily build of FF 3.2, the Linux version is still like 30-40% slower than the windows one, this is not rants, this is truth, test it yourself if you have Linux & xp dual boot and compare a few benchmarks.
3) If Mozilla plans to stay relevant it should understand that RAM is already dirt cheap and will be even cheaper so saying they save RAM by not implementing a per-process tab browsing to save like 5MB/tab is a reason for a fewer people, and will become a _lame_ excuse in the very near future, so it must start working on it now before it's not too late. I and many other Linux/MS users had enough crashes because of one single tab crashed.

1. Mine only takes 7 seconds to load, if you seriously can't wait 7 seconds then something is wrong with you.
2. No dual boot and never will. =)
3. With computers today, why are you even worried about RAM? My FF never ever goes above 120M.

---

### Post by Simian Man on 2009-03-09
I won't use a browser without the equivalent of Adblock Plus.  I doubt Google, the king of online ads, will add this to their browser.

---

### Post by Darkshade on 2009-03-09
> **Simian Man said:**
> I won't use a browser without the equivalent of Adblock Plus.  I doubt Google, the king of online ads, will add this to their browser.

Agree :)

---

### Post by babyhuey on 2009-03-09
> **Darkshade said:**
> Agree :)

An extension system has been in development for a while now. I'm sure someone will make the equivalent to adblock plus.

---

### Post by Chemical Imbalance on 2009-03-09
If they do make an extension system and Adblock Plus is ported...*and* if Chromium is as fast and stable as Chrome...it might just be my next browser...*might* :)

Oh yeah, *and* if Noscript.....
and if, and if  :)

---

### Post by lukjad on 2009-03-09
Not interested. Google knows too much about me already.

---

### Post by dBuster on 2009-03-09
I do not use adblock since it is more of a nuisance to me, instead I use NOSCRIPT along with a very good userchrome.css file and I filter 98% of all ads.  

There are some that I choose to see on some websites but for the most part I do not see any....

I'd be willing to share that userchrome if anyone cares to give it a whirl and see how much it blocks.

---

### Post by zika on 2009-03-09
> **lukjad007 said:**
> Not interested. Google knows too much about me already.
and what if they do? I do not have anything to hide. I really do not get this fear of someone knowing about ... whatever. what harm can it do ... ? this is not retorical question. I really want to know. what am I missing?

just to add, I do not like Chrome very much since FF3.2 is OK for me ... but ...

---

### Post by cb951303 on 2009-03-09
> **lukjad007 said:**
> Not interested. Google knows too much about me already.

it's a 100% open source project for gods sake. I don't trust google too but fearing chrome is paranoia.


I'm a FF follower from the start but I had enough of it. I'll even ditch my addons when chromium is stable. 
Also I hope some skillfull hackers take the source, make it look like a real GTK application, and remove all the google logos :P

---

### Post by Sand &amp; Mercury on 2009-03-09
> **cb951303 said:**
> it's a 100% open source project for gods sake. I don't trust google too but fearing chrome is paranoia.
Yeah... if there was anything at all in there to say that Google was using Chrome to track their users, it would fork immediately.

---

### Post by scaine on 2009-03-11
1.  One-process-per-tab.  It's a cool idea, but I honestly can't remember the last time FF crashed on me and I use Alpha Jaunty on almost every box I use.  Is this *really* that big a deal?  Cos it's not for me.

2.  Since I use Alpha software regularly, I need a rollback for my web browsing.  Does Epiphany/Konquerer/Chrome have anything like FEBE for FF (honest question)?  I can't imagine losing my browser history/cookies/passwords/bookmarks just because I'm re-installing my O/S with a fresh /home partition.

3.  Chromium might be open source, but I doubt "Google Chrome" will be.  So get your tin-foil hats at the ready.

I actually love Google and use many of their products, but I found it a bit scary that if you log in to their website (even just iGoogle), then log-out again, the cookie they store *still updates your browsing habits against your Google account*.  That's a big wrong, even though they're very honest about it in their privacy policy.

I feel that when you log out of a site, it should respect your privacy.  It certainly shouldn't check to see if you've ever logged in there before and try to track you with the logged-in cookie.

But it doesn't stop me using their reader, their webcal, their search engine, their product searches... the list goes on.

---

### Post by Giant Speck on 2009-03-11
I've never posted in this particular part of the forum, but I saw the thread title on the homepage and just had to read it.

I. CAN'T. WAIT.

---

### Post by jblackhall on 2009-03-11
> **scaine said:**
> 1.  One-process-per-tab.  It's a cool idea, but I honestly can't remember the last time FF crashed on me and I use Alpha Jaunty on almost every box I use.  Is this *really* that big a deal?  Cos it's not for me.

Used it with Flash lately?  Cuz it's better than it used to be, but still crashes on me quite frequently.  It would be nice to just be able to kill a tab and not the entire browser.  Stupid Flash.  

That said, I do prefer FF over Chrome.  I've used Chrome on my girlfriend's Windows box and I don't feel like the browser itself is all interesting to use and the lack of plugins sucks.  But I will say that it's VERY responsive and quick to start up.  I REALLY hate how slow FF is on Linux.  But for those blaming FF devs, they're mostly blaming Linux, according to Asa Dotzler: [http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626289](http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626289) [http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626395](http://weblogs.mozillazine.org/asa/archives/2009/02/how_many_linux.html#comment-2626395) (I posted these elsewhere earlier in the week)

There definitely is much room for Firefox to improve in the responsiveness category though.  And it's definitely not all to do with the javascript engine...

---

### Post by scaine on 2009-03-11
Yeah - I'm not a big flash-site user, maybe that's all there is to it.

What would it take to get Firefox to pre-load itself into memory, do you think?  I remember experimented with all-tray from the repos to do that, but it was a little clunky in that if you ignored the tray-version running in your panel and tried to open firefox normally, it complained that it was still running...

That said, Firefox opens in about 3 seconds on my aging, but decently specc'd PC, and once it's open, it tends to stay open until I close my session.

---

### Post by darco on 2009-03-18
Pre-Alpha Chrome available for Linux....

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

darco

---

### Post by cb951303 on 2009-03-19
> **darco said:**
> Pre-Alpha Chrome available for Linux....

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

darco

AFAIK that's just a testing shell. The actual browser may not be this one.

---

### Post by nyarnon on 2009-03-19
Especially not considering the announcement of the new beta that has no word about Linux 
[http://ubuntuforums.org/group.php?do=discuss&discussionid=423](http://ubuntuforums.org/group.php?do=discuss&discussionid=423)

---

### Post by jocheem67 on 2009-03-19
There might be privacy-issues with Google....

And I don't like that.

[http://coderrr.wordpress.com/2008/09/03/google-chrome-privacy-worse-than-you-think/](http://coderrr.wordpress.com/2008/09/03/google-chrome-privacy-worse-than-you-think/)

Don't get me wrong, I'm not paranoid. However a company like Google is as amoral as any other big kapi-company.....and it seems that their perception to the public might just be a bit too positive on these matters.

Just my two cents..

---

### Post by khelben1979 on 2009-03-19
Sounds interesting! Will be looking forward on testing it, although I highly doubt it will replace Opera or Firefox, at least not for me.

Chrome will be used with things where it's faster compared to the other web browsers (whatever that is? Java rendering? I don't remember, I read about this a long time ago).

---

### Post by conorn on 2009-03-19
Any sign of an ad-blocker for Chrome?  Ha ha, as if.

---

### Post by cecilpierce on 2009-03-19
I just installed it from ppa and a terminal window comes up and says "STOP, this browser is not ready yet". Is there any way to try it ???

---

### Post by Zorael on 2009-03-19
As for Mozilla developers blaming Linux for the performance difference (compared to Windows), I saw [some test](http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox) showing that a Firefox running under WINE was faster than a native linux Firefox. So, um, mmkay.
> These numbers are particularly interesting because of what they suggest *isn't* the problem.

If ff+wine is almost as quick as ff+win, doesn't that mean that the linux kernel and X are off the hook here? Doesn't it also hold that gcc is quite capable of compiling linux, x and wine to be quick enough to run ff+wine at near-native speeds, and therefore gcc itself is not broken (as I saw suggested on slashdot), even if perhaps it is not being used optimally to compile ff+linux?

And most importantly, doesn't that also mean that the wine people have done a f**king amazing job if we can expect near native performance with a huge app like firefox in a clean-room reverse-engineered reimplementation of something as stupendously huge as the win32 api?

I have always felt that ff+linux was a bit too sluggish. It's kinda usable, but the full-page zooming feature is ridiculously slow and scrolling is a joke. It's imperative that the source of the problems here be identified and rectified, but it seems like the ff+wine vs ff+linux numbers do vindicate some components of our os of choice, and demand vociferous praise for others.
> Yeah it means the Linux kernel and X have nothing to do with it.

Why people are trolling X because of this article, I will not know. There are a lot of ------- clueless people who just sit and talk **** about MIT X architecture, and never even looked at a line of code in their lives. Just a bunch of ------- morons who hate Linux because they are too stupid to appreciate it.
Defenders in those comments pushed blame on linux builds not taking advantage of PGO. And GTK.

[SIZE="1"](Qt <3)[/SIZE]

---

### Post by simtaalo on 2009-03-19
> **conorn said:**
> Any sign of an ad-blocker for Chrome?  Ha ha, as if.

on another site i read that you can use privoxy as an ad-blocker for chrome. i haven't looked into it though so don't know how good/true it is.

---

### Post by ubulette on 2009-03-19
> **cecilpierce said:**
> I just installed it from ppa and a terminal window comes up and says "STOP, this browser is not ready yet". Is there any way to try it ???

It's just the default Home page, to prevent you from complaining ;)

you can enter URLs and navigate.. somehow.
I'm not done with that package yet. It's crashing a lot more on amd64, I'm working on fixing that. This is a packaging issue.

btw, it's now more than just test_shell, there's a real binary and i've added an entry in the menu, with a nice icon.
I decided to open a terminal at the same time as the main chromium so you can see the "not-implemented" messages, instead of doing something and seeing nothing happening (or crashing).

Chromium is improving day after day, but the road is still long.
The idea is my daily PPA was just to expose that progress to you guys, but please, don't jump everywhere when it fails, it's expected at this point.

no need to report bugs in launchpad, or even upstream. Ping me eventually on IRC if you feel like it.

---

### Post by BackwardsDown on 2009-03-19
> I decided to open a terminal at the same time as the main chromium so you can see the "not-implemented" messages, instead of doing something and seeing nothing happening (or crashing).

Is it possible to keep the terminal open when chromium chrashes? Now it just exits too.

---

### Post by sdowney717 on 2009-03-19
arora is very fast
have you tried it yet?

[http://ubuntuforums.org/showthread.php?t=1096140](http://ubuntuforums.org/showthread.php?t=1096140)

---

### Post by jfernyhough on 2009-03-19
> **BackwardsDown said:**
> Is it possible to keep the terminal open when chromium chrashes? Now it just exits too.Yes. Run it /from/ a terminal, i.e. $ chromium-browser

Annoyingly I get HungRendererWarnings on each of my machines...(EeePC Jaunty, Acer Jaunty (9600GT + Compiz), Acer Intrepid (GMA + Compiz). I wonder if it's down to a user profile setting (and no, running with only metacity makes no difference. ;) )

> **sdowney717 said:**
> arora is very fast
have you tried it yet?

[http://ubuntuforums.org/showthread.php?t=1096140](http://ubuntuforums.org/showthread.php?t=1096140)
Tried the version in the repos. It's not bad but it could do with a nightly build against webkit-trunk. The wekbit used so far doesn't pass Acid3, but newer webkit builds do.

---

### Post by sdowney717 on 2009-03-19
yes. I downloaded the 0.5 version and compiled it with qtcreator webkit qt4.5

this way the plugins like flash will work.

---

### Post by jfernyhough on 2009-03-19
> **sdowney717 said:**
> yes. I downloaded the 0.5 version and compiled it with qtcreator webkit qt4.5

this way the plugins like flash will work.Flash works for me anyway. :D

But I'm going to have to try compiling it myself so I can compile against webkit-trunk. /goes to see if qtcreator is in the repos. :)

---

### Post by sdowney717 on 2009-03-19
I am running intrepid which has only qt4.4
jaunty has qt4.5 which will allow arora to use flash plugin.
So I had to compile it with qtcreator and tell qtcreator to use qt4.5 when it compiles.
The qtcreator downloaded from that site comes as a .bin and does a very nice install with menus.

---

### Post by marijus on 2009-03-22
any particular reason why i have to have msttcorefonts installed to use chromium?

can it be changed somewhere to use linux fonts instead?

atm if i dont have ms fonts installed the browser will just show an empty page doesnt matter which site...

regards, marijus

---

### Post by jfernyhough on 2009-03-22
Grr... so that's why it hasn't been working for me. And to think I'd got away from having those fonts installed...

Yup, installed and I have a page being displayed.

---

### Post by rburkartjo on 2009-03-22
i have messed around with the beta version (works with wine) i liked. however when i uninstalled it left some files behind that killed my ability to review any videos in ff. took me awhile to find and delete so ff worked correctly. will try again but not until the linux version is out.

---

### Post by zeroandone on 2009-03-27
> **zika said:**
> +1 try 3.2 nightly!
Can you provide a link to 3.2 nightly build for FireFox?

---

### Post by zika on 2009-03-27
> **zeroandone said:**
> Can you provide a link to 3.2 nightly build for FireFox?
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)

(forgot to say, this is 3.6 now)

---

### Post by zeroandone on 2009-03-27
> **zika said:**
> [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central/)

Thanks, I am going to give it a try.

---

### Post by ubulette on 2009-03-27
> **zeroandone said:**
> Can you provide a link to 3.2 nightly build for FireFox?

[https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
Probably not the best day to advertise this link as there's some red but well, dailies...

---

### Post by binbash on 2009-03-27
up to firefox 3.6 [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/)

---

### Post by ubulette on 2009-03-27
> **marijus said:**
> any particular reason why i have to have msttcorefonts installed to use chromium?

can it be changed somewhere to use linux fonts instead?

atm if i dont have ms fonts installed the browser will just show an empty page doesnt matter which site...

I raised that upstream several times already.
Details are in the [meta bug]("http://code.google.com/p/chromium/issues/detail?id=9100")

So in the meantime, i updated the [chromium-browser]("https://edge.launchpad.net/~chromium-daily/+archive") package to depend on msttcorefonts #-o

---

### Post by sandy8925 on 2009-03-28
> **Slug71 said:**
> Well im looking forward to it. I think anything is better than Firefox at the moment.

What about Opera then ?

---

