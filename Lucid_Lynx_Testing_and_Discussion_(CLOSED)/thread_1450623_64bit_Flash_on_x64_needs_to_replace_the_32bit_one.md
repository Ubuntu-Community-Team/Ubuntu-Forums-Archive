---
title: "64bit Flash on x64 needs to replace the 32bit one"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-04-09
Hi,
De facto this is what is happening on Lucid x64:
Canonical (through flashplugin-nonfree) installs a 32 bit version which is troublesome, first because there's still the "click" problem with flash (clicking on flash controls on some/many websites has no effects thus rendering flash useless and trust me it's very annoying) and it also installs the extra 32bit compatibility layer which is tens of MB.

On the other hand the latest "alpha" 64 bit release doesn't feature the annoying "click" bug and doesn't require installing the extra 30MB of x32 compatibility stuff and everything works fine.

Afaik the official response from Canonical is that they stick to the (sh#tty) 32bit on x64 cause it's deemed "stable" but de facto it's the other way around.

Given this, don't you think folks that we need to rely on what the de facto usability is, rather then on how the stuff is labeled?

ps: I got x64 beta2 with latest upgrades.

---

### Post by ubunterooster on 2010-04-09
Ubuntu-tweak installed 64-bit for me but that [ubuntu-tweak] is not a default program.

Oh, and I dig the signature; I saw FOSS as good before hearing about Linux because I actually read those EULAs. :&#9837;

---

### Post by philinux on 2010-04-09
64 bit should be the default now. Firefox got a beta in a release not long back. The restricted extras pulls in to much 32 support stuff.

---

### Post by lovinglinux on 2010-04-09
I'm using the 64bit version without problems since I switched to 64bit system (Karmic). I also have been recommending the 64bit versions to lots of users who didn't complain after installing it.

---

### Post by zenarcher on 2010-04-09
I completely agree!  All my systems are 64 bit and the 64 bit flashplayer has worked perfectly, without all the extra 32 bit packages.  No matter whether it's called "beta" or not, it works better and should be included!

Cheers,
zenarcher

---

### Post by seamuso on 2010-04-09
try running hulu with the 64bit flash plugin

"For the benefit of people who aren't using the 64-bit plugin anymore, the full message is "We're sorry but we're unable to stream videos to your system. This may be due to an Adobe software limitation on 64-bit Linux systems." (Actually, they should have said a limitation with the 64-bit plugin - the 32-bit wrapped plugin still works on 64-bit systems.)"

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

And a link to the [[color=blue]Hulu error[/color]](http://info.bluefrogcs.com/images/hulu.png)

( I personally just dl whatever the current 64bit version is at and drop the .so into my ~/.mozilla/plugins folder and am done with it)

on a side note, I've pretty much stopped using hulu because of the above issue (hulu is blaming adobe for changing something, but a previous known working version of the 64bit flash plugin also no longer works for me).

---

### Post by Slug71 on 2010-04-09
Yeh its long about time we get the 64bit version in the repos.

---

### Post by lovinglinux on 2010-04-09
> **seamuso said:**
> try running hulu with the 64bit flash plugin

"For the benefit of people who aren't using the 64-bit plugin anymore, the full message is "We're sorry but we're unable to stream videos to your system. This may be due to an Adobe software limitation on 64-bit Linux systems." (Actually, they should have said a limitation with the 64-bit plugin - the 32-bit wrapped plugin still works on 64-bit systems.)"

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

( I personally just dl whatever the current 64bit version is at and drop the .so into my ~/.mozilla/plugins folder and am done with it)

on a side note, I've pretty much stopped using hulu because of the above issue (hulu is blaming adobe for changing something, but a previous known working version of the 64bit flash plugin also no longer works for me).

Well, that only affects US citizens, because the rest of the world is locked out from Hulu. I see that as a geo-DRM, so it shouldn't be a motive to prevent distributing Ubuntu with a better plugin. Just my opinion.

---

### Post by xir_ on 2010-04-09
64 bit ppa is often the first thing i add to my systems. I think we should standardize around it as it may help speed up its stabilization.

---

### Post by Linuxforall on 2010-04-09
I held off installing flash till x64 alpha came along and from day one, I never had any issues, I have been quite happy with its performance, now Adobe needs to enable mic and webcam support in it and it will be all set.

---

### Post by seamuso on 2010-04-09
> **lovinglinux said:**
> Well, that only affects US citizens, because the rest of the world is locked out from Hulu. I see that as a geo-DRM, so it shouldn't be a motive to prevent distributing Ubuntu with a better plugin. Just my opinion.

That was just just for examples sake. like I mentioned, the first thing I do when I install/re-install and need flash is to head over to adobe labs and dl the most current 64bit plugin available.

But, that version is still an alpha pre-release version until adobe releases it as beta or full release. So the question becomes why would you want anyone to incorporate an alpha release of anything into what's meant to be a stable verion of an os .. especially an lts

As a timeline reference, I've been using the 64bit plugin since it was originally made available by adobe. It cured some browser crashes that were freezing me out of my desktop (had to ssh in and fix it often). lol

---

### Post by xlinuks on 2010-04-09
+1 for 64 bit flash, it's not perfect but overall it's certainly (a lot) better than the 32 bit version imho, that's why I install the 64 bit version all the time (by hand).

---

### Post by descendent87 on 2010-04-09
I use the script on the forums to install 64bit flash, never had any problems with it so yes I think it should be default

---

### Post by rajeev1204 on 2010-04-09
They aint going to listen, too rigid with their alpha status rules.

This poll result is overwhelmingly leaning towards the 64 bit plugin and was the same during the last release but the devs still wont budge.

I guess adobe putting a fake 'RC' status on the plugin will change their minds.

---

### Post by xebian on 2010-04-09
> **rajeev1204 said:**
> They aint going to listen, too rigid with their alpha status rules.

This poll result is overwhelmingly leaning towards the 64 bit plugin and was the same during the last release but the devs still wont budge.

I guess adobe putting a fake 'RC' status on the plugin will change their minds.

Actually IMHO they will.  Remember the OO, Yahoo search, rhythmbox,??

---

### Post by zika on 2010-04-09
Yes.
In the meantime: [https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv)

---

### Post by rajeev1204 on 2010-04-09
> **xebian said:**
> Actually IMHO they will.  Remember the OO, Yahoo search, rhythmbox,??

What about these? 

But if i understand your post correctly, some of these came in (like grub2 beta) since the devs believe they are open source so will probably be fixed or get better.

Not with flash though.

---

### Post by rajeev1204 on 2010-04-09
> **zika said:**
> Yes.
In the meantime: [https://launchpad.net/~voronov84/+archive/andreyv]("https://launchpad.net/%7Evoronov84/+archive/andreyv")

Not sure why anyone would use this ppa for flash instead of the simple way of downloading and copying the plugin to .mozilla/plugins.

---

### Post by Funnnny on 2010-04-09
Automatic update is a hand-up ;)

---

### Post by zika on 2010-04-09
> **rajeev1204 said:**
> Not sure why anyone would use this ppa for flash instead of the simple way of downloading and copying the plugin to .mozilla/plugins.I'm the one that was doing that wor quite some time, ever since 64-bit plugin emerged. I've, simpy put, got tired of checking if a new version were available and I'm happy that someone will do that for me... If You search this and my local Forum, You'll find my numerous messages abou how to to do that "by simply copying the file in ~/.mozilla/plugins", but, as time goes by and as I'm getting (even more, yes, that is possible) older... The same stands for Java in this ppa... Just being lazy...

---

### Post by tad1073 on 2010-04-09
> **seamuso said:**
> try running hulu with the 64bit flash plugin

"For the benefit of people who aren't using the 64-bit plugin anymore, the full message is "We're sorry but we're unable to stream videos to your system. This may be due to an Adobe software limitation on 64-bit Linux systems." (Actually, they should have said a limitation with the 64-bit plugin - the 32-bit wrapped plugin still works on 64-bit systems.)"

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

And a link to the [[COLOR=blue]Hulu error[/COLOR]]("http://info.bluefrogcs.com/images/hulu.png")

( I personally just dl whatever the current 64bit version is at and drop the .so into my ~/.mozilla/plugins folder and am done with it)

on a side note, I've pretty much stopped using hulu because of the above issue (hulu is blaming adobe for changing something, but a previous known working version of the 64bit flash plugin also no longer works for me).

and here 
[http://www.hulu.com/discussions/19/124339/592999#](http://www.hulu.com/discussions/19/124339/592999#)

---

### Post by tad1073 on 2010-04-09
> **zika said:**
> I'm the one that was doing that wor quite some time, ever since 64-bit plugin emerged. I've, simpy put, got tired of checking if a new version were available and I'm happy that someone will do that for me... If You search this and my local Forum, You'll find my numerous messages abou how to to do that "by simply copying the file in ~/.mozilla/plugins", but, as time goes by and as I'm getting (even more, yes, that is possible) older... The same stands for Java in this ppa... Just being lazy...

I do not have the ~/.mozilla/plugins/ folder, all my stuff is in /usr/share/...

---

### Post by sonicb00m on 2010-04-09
> **kahumba said:**
> 
Afaik the official response from Canonical is that they stick to the (sh#tty) 32bit on x64 cause it's deemed "stable" but de facto it's the other way around.


Good god, is that true? The 32 bit wrapped in x64 systems just DOES NOT WORK properly. It's useless.

I always put the alpha on and it works flawlessly.

---

### Post by ViperScull on 2010-04-09
but why does flashplugin-nonfree from repos make me install ia32-libs, a lot of lib32*, lib...386, and nspluginwrapper if it's the 64 bit version????

It seems to me they are stuck to 32 bit version.

---

### Post by powder on 2010-04-09
I'm also using the alpha and it seems to work well enough for my use.  However, we really don't have any idea what major bugs or regressions it has because it's not open source.  I think Canonical made the right decision for now.

---

### Post by zika on 2010-04-09
> **tad1073 said:**
> I do not have the ~/.mozilla/plugins/ folder, all my stuff is in /usr/share/...Because You have it installed in a proper way. Putting it in ~/.mozilla/plugins works but it is, essentially, a tweak... Yes, that folder does not exist in a clean install. I've made it every time after a clean install. Ergo, I've came back to proper way of using Flash... :)
As long as we have choice of using 32-bit or 64-bit I'm OK with that. I'd like more to have it 64-bit out-of-the-box, but I do not mind doing it for myself... Two great tools: [http://ubuntuforums.org/showpost.php?p=8872675&postcount=1](http://ubuntuforums.org/showpost.php?p=8872675&postcount=1) and [https://launchpad.net/~voronov84/+archive/andreyv](https://launchpad.net/~voronov84/+archive/andreyv) make that, now, even easier...
Update: Several posts after this one, ppa:sevenmachines/flash is mentioned. That is, also, a very good ppa, I, simply, forgot off... Thank You, LuquidMeson...

---

### Post by xebian on 2010-04-09
> **powder said:**
> I'm also using the alpha and it seems to work well enough for my use.  However, we really don't have any idea what major bugs or regressions it has because it's not open source.  I think Canonical made the right decision for now.

LOL.  The 32-bit is as closed source as the 64-bit.

---

### Post by xebian on 2010-04-09
> **tad1073 said:**
> I do not have the ~/.mozilla/plugins/ folder, all my stuff is in /usr/share/...

Everyone has their ways but I usually put in /usr/lib/mozilla/plugins where other browsers will look.

---

### Post by dyltman on 2010-04-09
Oh dear god yes, I keep googling for about 20 minutes or so untill I can find a half-decent guide on how to install the x64 flash. Not being able to click buttons kills alot of websites.

---

### Post by ubunterooster on 2010-04-09
> **dyltman said:**
> Oh dear god yes, I keep googling for about 20 minutes or so untill I can find a half-decent guide on how to install the x64 flash. Not being able to click buttons kills alot of websites.
I used to go to the forum and look at active member's sigs. Ne'er took more than 10 min b/f I found it. Last time I used Ubuntu-tweak, though

---

### Post by amano on 2010-04-09
Couldn't Medibuntu pull in an own 64bit plugin via the non-free-codecs meta-packages?

Most people would install this meta-package anyway and canonical could officially obey their possible contractional obligations with adobe or follow their possible internal policy to include just final blobs.

For the users it would be easier to have all additional stuff within the Medibuntu repos instead of relying to several possibly dubious additional repos (most would "trust" Medibuntu anyway and install their other stuff).

---

### Post by tad1073 on 2010-04-09
> **zika said:**
> Because You have it installed in a proper way. Putting it in ~/.mozilla/plugins works but it is, essentially a tweak... Yes, that folder does not exist in a clean install. I've made it every time after a clean install. Ergo, I've came back to proper way of using Flash... :)
As long as we have choice of using 32-bit or 64-bit I'm OK with that. I'd like more to have it 64-bit out-of-the-box, but I do not mind doing it for myself... Two great tools: [http://ubuntuforums.org/showpost.php?p=8872675&postcount=1](http://ubuntuforums.org/showpost.php?p=8872675&postcount=1) and [https://launchpad.net/~voronov84/+archive/andreyv]("https://launchpad.net/%7Evoronov84/+archive/andreyv") make that, now, even easier...

[http://ubuntuforums.org/showpost.php?p=8522076&postcount=1](http://ubuntuforums.org/showpost.php?p=8522076&postcount=1)

is what I use...

but would really like getting [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/) working

---

### Post by djchandler on 2010-04-09
Anybody that wants to install a proprietary alpha, go right ahead. Just don't force an alpha on everybody else that's not fully functional.

I don't want alpha software on my computer. There are enough issues with beta software without introducing a variable such as alpha stage software package over which Canonical has zero control.

---

### Post by powder on 2010-04-09
> **xebian said:**
> LOL.  The 32-bit is as closed source as the 64-bit.

I never said that it wasn't.  My point is that 32 bit flash is much more mature than 64 bit flash because it's been around for far longer.  Is that so funny to you?

---

### Post by FrancoNero on 2010-04-10
someone stop the 32bit nonsense :)

---

### Post by LiquidMeson on 2010-04-10
In the mean time,
sudo add-apt-repository ppa:sevenmachines/flash/ubuntu && sudo apt-get update && sudo apt-get install flashplugin64-installer
In your terminal.

---

### Post by dcstar on 2010-04-10
Until Adobe release the 64-bit player as an official release it would be irresponsible of Ubuntu to use it.

There are specific terms and conditions set by Adobe in regards to this software that may well prevent Ubuntu from offering it as an install:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

We will all have to wait for Adobe to put the resources into supporting the Linux community and make a release worthy 64-bit version available to us.

---

### Post by novafluxx on 2010-04-10
> **powder said:**
> I never said that it wasn't.  My point is that 32 bit flash is much more mature than 64 bit flash because it's been around for far longer.  Is that so funny to you?

I don't think it really matters, its not like its a major code re-write...or am I wrong?

They just change some variables, recompile as 64-bit... :-D SO EASY A CAVEMAN CAN DO IT

---

### Post by djchandler on 2010-04-10
> **novafluxx said:**
> I don't think it really matters, its not like its a major code re-write...or am I wrong?

They just change some variables, recompile as 64-bit... :-D SO EASY A CAVEMAN CAN DO IT

Maybe not. If you read the FAQs, you'll discover that there is no Mac or Windows version. Do you wonder why? I do. And the question that comes to mind is, "why can't there be a universal plug-in?" On the other hand I know Flash is getting integrated into Google's Chrome browser, no plug-in necessary to run Flash content in the near future for Chrome. Then add in the fact that Apple snubbed Flash on the iPad. This picture is bigger and more complex than is being discussed here. So far most of the sentiment is,"But I want it NOW!" You are assuming that what you are seeing wiil develop into an end-product.

If you read further down in the FAQs, Adobe states there is probably no discernible performance gain. So that leaves me wondering why anybody here really wants it when some features are yet to even be implemented.

Anyway, the upshot is Linux is probably going to see the 64-bit plug-in first, or a browser is going to be released by Google that has no need of a plug-in. We may be looking at something so transitory that it isn't worth the trouble to find a way to package it.

By all means, all of you who want to, test it. Just don't get the idea that you can pull the rest of the Ubuntu Community into Alpha and Beta testing along with you. Despite the results of the poll, it's probably not going to happen.

Read Adobe's material from the links below to make an informed choice about 64-bit Flash.

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)
[http://labs.adobe.com/technologies/flashplayer10/faq.html](http://labs.adobe.com/technologies/flashplayer10/faq.html)
[http://forums.adobe.com/community/labs/flashplayer10_64bit/](http://forums.adobe.com/community/labs/flashplayer10_64bit/)

I don't want to see, ""Sorry, we are unable to stream this video"  when I try to stream video from Hulu (or anybody else for that matter).

BTW, [ESPN 3]("http://espn.go.com/espn3/player?size=condensed") (formerly ESPN 360) just started allowing native Linux browsers access to their Flash video streams with no Move Networks executable necessary, so something is *UP*! See if your 64-bit plug-in works [on their site]("http://espn.go.com/espn3/player?size=condensed").
:guitar:

---

### Post by FrancoNero on 2010-04-10
the whole notion of needing a "plugin" to play some sort of content on the web seems so antiquated

---

### Post by powder on 2010-04-10
> **novafluxx said:**
> I don't think it really matters, its not like its a major code re-write...or am I wrong?

They just change some variables, recompile as 64-bit... :-D SO EASY A CAVEMAN CAN DO IT

Unfortunately it's not that simple.  64 bit Wine is a good example of this.

[http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64)

---

### Post by rajeev1204 on 2010-04-11
> **djchandler said:**
> Anybody that wants to install a proprietary alpha, go right ahead. Just don't force an alpha on everybody else that's not fully functional.

I don't want alpha software on my computer. There are enough issues with beta software without introducing a variable such as alpha stage software package over which Canonical has zero control.

A company releasing its product as final doesnt guarantee it being stable .Recently released games come to mind.

Isnt the result of the poll obvious to you yet ? Are you even using the 64 bit version yet ?

If adobe suddenly said its final version you will believe its stable ? Great.Its closed source software, so the users speak on it being more usable solely on experience.You really think flash 32 bit deserves to be called stable release?

---

### Post by cl333r on 2010-04-11
@rajeev1204 +1

Nothing is perfect, fact is however, the 64bit version overall is way better (in fact I have had _no_ problem using it for a year or so) than the "stable" 32bit one, so I always install it manually.

---

### Post by robinl on 2010-04-11
> **djchandler said:**
> 
...

If you read further down in the FAQs, Adobe states there is probably no discernible performance gain. So that leaves me wondering why anybody here really wants it when some features are yet to even be implemented.

...

I don't want to see, ""Sorry, we are unable to stream this video"  when I try to stream video from Hulu (or anybody else for that matter).


How about 64-bit users simply wanting to have a working Flash plugin? Have you even tried using Flash in 64-bit or read the title post? With the click bug on 32 bit plugin Flash is basically unusable on ALL websites. You would rather see users not being able to click on buttons on Flash videos (and hence you know, stream stuff) than give them something that works, except for one single US-only site? You want to use a stop-gap hack to glue different components from different architectures together rather than a proper native (albeit testing) version? It's not a matter of release vs. alpha software, it's a matter of broken vs. working software.

---

### Post by lovinglinux on 2010-04-11
> **rajeev1204 said:**
> A company releasing its product as final doesnt guarantee it being stable .Recently released games come to mind.

Isnt the result of the poll obvious to you yet ? Are you even using the 64 bit version yet ?

If adobe suddenly said its final version you will believe its stable ? Great.Its closed source software, so the users speak on it being more usable solely on experience.You really think flash 32 bit deserves to be called stable release?

I agree. I don't think I ever saw a poll here so homogeneous.

---

### Post by t.alex on 2010-04-11
> **robinl said:**
> How about 64-bit users simply wanting to have a working Flash plugin? Have you even tried using Flash in 64-bit or read the title post? With the click bug on 32 bit plugin Flash is basically unusable on ALL websites. You would rather see users not being able to click on buttons on Flash videos (and hence you know, stream stuff) than give them something that works, except for one single US-only site? You want to use a stop-gap hack to glue different components from different architectures together rather than a proper native (albeit testing) version? It's not a matter of release vs. alpha software, **it's a matter of broken vs. working software.**

couldn't have said it better myself :) The 32 bit plugin is just awful. Many new users will struggle with it, not even knowing that there's a 64 bit version, which to some degree (well, it's flash, you can't expect too much from it) even works.

---

### Post by zenarcher on 2010-04-11
> **seamuso said:**
> try running hulu with the 64bit flash plugin

"For the benefit of people who aren't using the 64-bit plugin anymore, the full message is "We're sorry but we're unable to stream videos to your system. This may be due to an Adobe software limitation on 64-bit Linux systems." (Actually, they should have said a limitation with the 64-bit plugin - the 32-bit wrapped plugin still works on 64-bit systems.)"

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

And a link to the [[color=blue]Hulu error[/color]](http://info.bluefrogcs.com/images/hulu.png)

( I personally just dl whatever the current 64bit version is at and drop the .so into my ~/.mozilla/plugins folder and am done with it)

on a side note, I've pretty much stopped using hulu because of the above issue (hulu is blaming adobe for changing something, but a previous known working version of the 64bit flash plugin also no longer works for me).

Well, I have 64 bit Kubuntu 10.04 Beta 2 installed here on four machines (I don't have any 32 bit systems around) and have installed the 64 bit flash player using the PPA.  And, I run Hulu on all four of the systems just fine...no error message.  Nor have I encountered any other problems with the 64 bit flash player on any other website.

Cheers,
zenarcher

---

### Post by solitaire on 2010-04-11
well if they can fix the "npviewer" crashing at the drop of a hat, then i'd be for only using 64bit version.

---

### Post by volanin on 2010-04-11
Is there a bug report for this?
We could put a link to this discution there.

---

### Post by dudude on 2010-04-11
The bug report for the 32 bit version not registering clicks on 64 bit systems is [here]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407").

I don't know if things have changed since the last time I have used it, but the 64 bit version of Flash does not work for me. The problem with not using the NSPluginwrapper (or however that is spelled) is that whenever Flash crashes, Firefox crashes, meaning that Firefox would crash frequently and I would lose whatever I was looking at frequently.

I guess I am unusual in that I open many tabs when I am looking at things in the browser, so the effects of a crash are more extreme for me.

With the wrapper around Flash, whenever Flash crashes, Firefox continues to run and Flash can be restarted later.

Also, I don't know if it will come in a future update for Lucid, but Firefox 3.6 is supposed to get its "[Lorentz]("http://news.slashdot.org/story/10/04/10/0121202/Firefox-Lorentz-Keeps-Plugin-Crashes-Under-Control")" plugin architecture that should hopefully make this point moot.

---

### Post by lovinglinux on 2010-04-11
> **dudude said:**
> Also, I don't know if it will come in a future update for Lucid, but Firefox 3.6 is supposed to get its "[Lorentz]("http://news.slashdot.org/story/10/04/10/0121202/Firefox-Lorentz-Keeps-Plugin-Crashes-Under-Control")" plugin architecture that should hopefully make this point moot.

Yes, it does make this point moot. I'm testing Lorenz with 64bit Flash and it doesn't crash or lock. All I get is...;)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=152925&d=1270996391[/IMG]

Why wouldn't Lorentz come to Lucid? It is an update to Firefox 3.6 not a major new release.

---

### Post by zika on 2010-04-17
> **rajeev1204 said:**
> Not sure why anyone would use this ppa for flash instead of the simple way of downloading and copying the plugin to .mozilla/plugins.I've answered You a bit of time ago. I, sort of, liked the fact that I could delegate upgrade work to aforementioned ppa. But, You were right! I should have stayed with my preferred method of simple extract-and-copy for both, Flash and Java plugins. It works much better that way. I want to apologize and to say that I'm back to the way real Ubuntu people do it. Cheers! I was wrong and You're right...

---

### Post by Won1der on 2010-04-28
> **seamuso said:**
> try running hulu with the 64bit flash plugin

"For the benefit of people who aren't using the 64-bit plugin anymore, the full message is "We're sorry but we're unable to stream videos to your system. This may be due to an Adobe software limitation on 64-bit Linux systems." (Actually, they should have said a limitation with the 64-bit plugin - the 32-bit wrapped plugin still works on 64-bit systems.)"

[http://www.hulu.com/discussions/9/110036/495965](http://www.hulu.com/discussions/9/110036/495965)

And a link to the [[color=blue]Hulu error[/color]](http://info.bluefrogcs.com/images/hulu.png)

( I personally just dl whatever the current 64bit version is at and drop the .so into my ~/.mozilla/plugins folder and am done with it)

on a side note, I've pretty much stopped using hulu because of the above issue (hulu is blaming adobe for changing something, but a previous known working version of the 64bit flash plugin also no longer works for me).

A stupid workaround to that stupid Hulu problem but here is what I did.
Install wine
Install PlayOnLinux
use PlayOnLinux to install Firefox 3.6 in wine
Select flash add-ons for Firefox during installation
use Firefox 3.6 in wine to watch Hulu

Whatever you do, don't try to run Hulu in full screen it seems to cause issues with the gnome desktop. I got around that by enabling zoom in compiz and just zooming the video to my preferred size.

As I said, stupid but it works.

---

