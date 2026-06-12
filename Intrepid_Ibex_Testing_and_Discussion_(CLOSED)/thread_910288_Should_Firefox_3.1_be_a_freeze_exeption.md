---
title: "Should Firefox 3.1 be a freeze exeption?"
date: 2008-09-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mc4100 on 2008-09-04
A few things I've noted when using Minefield 3.1b1pre that make me wonder if it should be included in the upcoming release:
> **'[S]Duke said:**
> Minefield is the codename for the "Trunk" of Firefox builds, Minefield is the constant latest version of Firefox. "Shiretoko" is the Codename for Firefox 3.1. As explained here: [http://www.mozilla.org/projects/fire.../releasenotes/](http://www.mozilla.org/projects/fire.../releasenotes/)
[list]
[*]Light memory footprint: 4 tabs (A flash video, Google, Digg, Ubuntuforums) = ~40 megs
[*]Updated JavaScript engine: Tracemonkey. Optimized for speed.
[*]Fixes stability issues with Flash, and video artifacts are gone.
[*]Strangely resistant to the random crashes ...
[*]Slightly better GTK+ integration. [citation needed]
[*]Ctrl+Tab cycles between browser tabs, with previewing -- like a window manager.
[*]Highlighting and Dragging text/images/etc is far more pleasant due to anti-aliasing. It works better, too.
[/list]

Has anyone found a site that will actually crash Minefield? I've tried most of the ones that previous versions had problems with, and they all work great (including [www.last.fm](www.last.fm) and [www.bbc.co.uk](www.bbc.co.uk), it's a bit choppy but it works fine)

EDIT: Here's the bug report from a later post in this thread, if anyone wants to comment (please do, positively or negatively):
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/264851](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/264851)

---

### Post by Slug71 on 2008-09-04
I voted yes but only if 3.0.2 doesnt fix the current issues with Flash. They just have to do something because this is just beyond annoying now! Ive fixed it a few time already and it only lasts a couple days and then starts crashing etc.

---

### Post by dudude on 2008-09-04
For Flash to have the windowless mode or whatever, would there have to be the newest version of Firefox (actually the newest version of xulrunner), and the final release of Flash, or just the newest Firefox with the windowless mode option enabled in the Flash 10 RC?

---

### Post by plun on 2008-09-04
> **dudude said:**
> For Flash to have the windowless mode or whatever, would there have to be the newest version of Firefox (actually the newest version of xulrunner), and the final release of Flash, or just the newest Firefox with the windowless mode option enabled in the Flash 10 RC?

The Windowsless mode bug is fixed in version 3.02

[https://bugzilla.mozilla.org/show_bug.cgi?id=435764](https://bugzilla.mozilla.org/show_bug.cgi?id=435764)

Flash10RC works just fine, 32 bit rock solid
[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)


I voted "No" mainly because of all trouble with 3.0 and it is easy to either backport or install from a ppa.

---

### Post by god0fgod on 2008-09-04
I choose the last one because Opera is better in my opinion. Not that it matters what browser is pre-installed.

---

### Post by mc4100 on 2008-09-04
> **god0fgod said:**
> I choose the last one because Opera is better in my opinion. Not that it matters what browser is pre-installed.
I added that option with Opera in mind (well, that and Midori), I know a lot of like opera's speed and built-in functionality -- I'm curious, have you tried the latest Firefox?
It would be interesting to hear another perspective on the updated JavaScript engine, from someone who uses a similarly fast browser, like I said in my other thread... I don't notice it too much, but it's certainly snappier.

---

### Post by OliW on 2008-09-04
Firefox (alongside a few other key apps) should be make permanent exceptions to Ubuntu's rigid upgrade policy. They should be constantly upgraded.

Of course there should be testing but these apps are major cross-platform performers. They have to go massive internal testing before they can be released.

---

### Post by pferraro on 2008-09-04
On what grounds do you consider an initial beta release "soon to be 3.1"?
There will likely be several more betas, and a few release candidates until then.

---

### Post by mc4100 on 2008-09-04
This post is redundant.

---

### Post by [S]Duke on 2008-09-04
Not to be overly nitpicky, but for clarification sake, Minefield is not the codename for Firefox 3.1

Minefield is the codename for the "Trunk" of firefox builds, Minefield is the constant latest test version of Firefox. It is most of the time extremely unstable.

"Shiretoko" is the Codename for Firefox 3.1. As explained here: [http://www.mozilla.org/projects/firefox/3.1a1/releasenotes/](http://www.mozilla.org/projects/firefox/3.1a1/releasenotes/)

With that said, I do think 3.1 should make it, it's looking like a great improvement over 3.

Whether it'll be done on time or not is doubtful though.

---

### Post by ccw on 2008-09-04
I was steadily in favor of including the 3.0 branch in Hardy, but I'm not in favor of this... why?

1) Hardy was an LTS that people will run for years. If they stayed at 2.0, HH would have been stuck with an EOL branch for years. intrepid is a normal release, that most people will upgrade past in april 2009 or soon after, which will still be well within 3.0 lifecycle. 
2) 3.0 was well into the development cycle at Hardy release (announced as the 5th and declared last beta) and final FF release dates were be pinned down. 3.1 is still alpha, beta release dates are being postponed and final release dates are unknown.

---

### Post by Slug71 on 2008-09-04
I hope 3.0.2 is included with Alpha 5 so that we can at least test it and see if its working better than 3.0.1.

---

### Post by mc4100 on 2008-09-04
Here's the bug report, if anyone wants to comment (please do, positively or negatively):
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/264851](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/264851)

---

### Post by meborc on 2008-09-04
> **mc4100 said:**
> 
[*]Ctrl+Tab cycles between browser tabs, like a window manager.

are you saying that your firefox 3 does not support it already :d it does for me... has done it since ages...

---

### Post by Slug71 on 2008-09-04
Thanks mc4100, left a message.

---

### Post by mc4100 on 2008-09-04
> **meborc said:**
> are you saying that your firefox 3 does not support it already :d it does for me... has done it since ages...
Do you get a preview, like Alt+Tab with a window manager?
[https://wiki.mozilla.org/Firefox3.1/Features](https://wiki.mozilla.org/Firefox3.1/Features)
```
Target------------Item--------------------Bug---------Owner----Status
A1 	Basic tab switch preview 	bug 395980 	dao 	landed 
```

---

### Post by BwackNinja on 2008-09-04
I'd go with 3.1. Unless windowless mode would be fixed in 3.0.2 (which would require a workaround for stability otherwise), I don't think there's much reason not to upgrade. The beta seems stable enough, and if stability alone doesn't push this, I don't know what will. Regardless of the decision made, I'll be using 3.1.

---

### Post by Nullack on 2008-09-04
What is the schedule for release of 3.1?

---

### Post by mc4100 on 2008-09-04
> **Nullack said:**
> What is the schedule for release of 3.1?

There's no definitive one, it's mostly estimations:

[https://wiki.mozilla.org/Firefox3.1/Schedule](https://wiki.mozilla.org/Firefox3.1/Schedule)

[http://blogs.zdnet.com/open-source/?p=2777](http://blogs.zdnet.com/open-source/?p=2777)
> Beta 1 [and thus the freeze] is now tentatively scheduled for September 9th. 
So we'll have to wait until those are set, before trying to predict when they will release a final.

---

### Post by sharp65 on 2008-09-04
> **meborc said:**
> are you saying that your firefox 3 does not support it already :d it does for me... has done it since ages...

It's done graphically, sort of like alt-tab in windows.

---

### Post by Robertjm on 2008-09-04
ABSOLUTELY!! The problem with flash and crashes on main websites needs to be fixed. If updating to that version is a known fix, I'd be up for it as long as it didn't break other stuff in the process.

---

### Post by priegog on 2008-09-04
So here's what I think. 
For Hardy (a LTS, no less) they trusted in a beta because they tought the improvements it brought over FF v2 were worth the hassle. I think this situation might be repeating itself and I think there are several reasons it should be included.

1   Mozilla won't support the old version for long
2   We don't want an outdated distro within weeks of release (a browser is a VERY important part of a distro)
3   It's not a LTS... It's got intrepid in the name, for God's sake!
4   Firefox isn't that closely integrated into the system to justify saying stuff like "It'll require enormous amounts of man-hours to make it work, and thus isn't worth it past version-freeze"
5   If history is any indication, Mozillas' point releases are always rock solid and do nothing but solve problems, instead of creating them
6   It fixes the flash problems (altho I think 3.0.1 does that too, but still)
7   (and this is the most important one) TraceMonkey. We've all seen Google Chrome tear apart the web in just a couple of days, and at the moment only windows users can experience that sort of snappyness in webapps. TraceMonkey can (allegedly) bring that experience to Firefox (and Linux in general), so why prolong this situation for 6 more months? We don't windows users to be able to say their web experience is that much greater (and Chrome's V8 IS that much of a difference) than on Linux. And going a step further, we actually want that experience to be available to all ubuntu users ASAP.

Anyways, those are my 2 cents. In my mind I don't think there's justification NOT to include it seeing the enormous advantage point 7 brings to the table.

---

### Post by mc4100 on 2008-09-05
> **Robertjm said:**
> ABSOLUTELY!! The problem with flash and crashes on main websites needs to be fixed. If updating to that version is a known fix, I'd be up for it as long as it didn't break other stuff in the process.
Then why not try it out?
It's far better to find out early if there are any serious issues;
It might fail catastrophically, so first backup .mozilla, then add the repository below in software sources (or edit sources.list manually, if you wish)
```
deb http://ppa.launchpad.net/fta/ubuntu intrepid main
```
And then search for firefox in Synaptic ... you want firefox-3.1 , and also firefox-3.1-gnome-support packages.

If everything went smoothly, you now have a menu entry "Minefield 3.1 Web Browser", and if you want it to use the upgraded JavaScript engine:
Type "about:config" in the awesome-bar, press enter, type "jit" into the filter box and double click on the "javascript.options.jit.content" preference.

Done ... Browse Away!

Or, you can grab the source [here]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/shiretoko/alpha1/").

---

### Post by merlyn on 2008-09-05
> **Slug71 said:**
> I hope 3.0.2 is included with Alpha 5 so that we can at least test it and see if its working better than 3.0.1.

I've been running the Swiftfox 3.0.2 builds alongside the Firefox 3.0.1 builds from the repos.

To be honest I haven't noticed all that much difference in overall performance or improvements with Flash.

In fact there are still one or two sites that I visit, which cause 3.0.2 to crash, and 3.0.1 handles them happily.

The current 3.1 offering from ppa, doesn't miss a beat on the same two sites, and it's fast.

I cast my vote for 3.1 in Intrepid.

---

### Post by godot67 on 2008-09-05
According to [http://groups.google.com/group/mozilla.dev.planning/msg/8ea2037ce2cc145f](http://groups.google.com/group/mozilla.dev.planning/msg/8ea2037ce2cc145f) , "the code freeze for Beta 1 [is moving] to *Sept 30*"
And "Beta 2 will be after Beta 1, unsurprisingly, likely returning to the 4 week cadence and freezing on Oct 28th."

Intrepid release candidate is scheduled for October 23rd. Firefox 3.1 won't even be in beta2 stage at this date (not speaking of rc and final...)

So let's face it, Firefox 3.1 in Intrepid seems unrealistic.

But I agree that Firefox 3.0.x and Flash 10 causes serious problems to navigation, considering Flash is nowdays used on a great part of web sites.

---

### Post by psyke83 on 2008-09-05
This seems like a foolish poll, and I'm surprised at the current results. Firefox 3.0 got a FFe in Hardy because a) Hardy was an LTS release, b) Firefox 3.0 was very close to release and b) it would not be practical to continue supporting Firefox 2.x for an LTS release.

In this case, Intrepid is a regular release, and Firefox 3.1 is in a pre-beta stage. There is *no* sense in shipping an alpha (or early beta) release of Firefox 3.1.

As for the Flash issues that Firefox 3.1 will supposedly fix, that's bull****. Intrepid is currently using Flash 10 beta 2 which has (quite serious) performance regressions compared to Flash 9. The good news is that Flash 10 RC fixes those issues, and will be updated in Intrepid soon. There are some [prerequisites]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403/comments/14") that need to be fulfilled before it works properly (an update to ia32-libs and nspluginwrapper for 64bit users, and Firefox 3.0.2 will contain a necessary fix as well), which is why this particular update is taking longer than usual.

If you're a 32bit user and want to try Flash 10 RC, you can check my PPA [here]("https://launchpad.net/~psyke83/+archive") for a working package. Also see [bug #257403]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/257403") for more information.

N.B. Flash has been discussed [previously]("http://ubuntuforums.org/showthread.php?t=866965").

---

### Post by Slug71 on 2008-09-05
Well im not sure the poll is foolish. I think a lot of people just want this issue resolved which seems to be fixed even with a pre-beta while 3.0.2 is still having issues. Bottom line and regardless of version i think everyone just wants a working browser.
Hopefully we'll see 3.0.2 with Flash 10 RC soon.

---

### Post by plun on 2008-09-05
> **Slug71 said:**
> Well im not sure the poll is foolish. I think a lot of people just want this issue resolved which seems to be fixed even with a pre-beta while 3.0.2 is still having issues. Bottom line and regardless of version i think everyone just wants a working browser.
Hopefully we'll see 3.0.2 with Flash 10 RC soon.

Well, psyke 83 pointed to a URL and I did it earlier.:)

For 32 bit its rock solid !


FF3.1 is nevertheless fun to play with... with the JIT engine enabled
its FAST....:)

(also the challenge to enable non-compatible addons....8-)   )

---

### Post by Slug71 on 2008-09-05
> **plun said:**
> Well, psyke 83 pointed to a URL and I did it earlier.:)

For 32 bit its rock solid !


FF3.1 is nevertheless fun to play with... with the JIT engine enabled
its FAST....:)

(also the challenge to enable non-compatible addons....8-)   )

Im using 64 bit plun:( Guess ill just have to wait for FF 3.0.2 and Flash 10 RC that psyke83 spoke about.

---

### Post by plun on 2008-09-05
> **Slug71 said:**
> Im using 64 bit plun:( Guess ill just have to wait for FF 3.0.2 and Flash 10 RC that psyke83 spoke about.

Well... "the 64 bits trap"...:)

I have never understand any reason for running 64 bits on clients.
(perhaps with heavy math calculations)

Yesterday, swfdec was upgraded maybe worth a try ?

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006377.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006377.html)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006396.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006396.html)

About:
[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

Ubuntu version including 64 bit
[http://packages.ubuntu.com/intrepid/swfdec-mozilla](http://packages.ubuntu.com/intrepid/swfdec-mozilla)


Testing...:)

```
sudo apt-get purge flashplugin-nonfree && sudo apt-get install swfdec-mozilla

```

EDIT

Well... swfdec kills my "fox"....it works a couple of seconds.  Back to Adobe...

---

### Post by psyke83 on 2008-09-05
> **plun said:**
> EDIT

Well... swfdec kills my "fox"....it works a couple of seconds.  Back to Adobe...

As far as I understand, the windowless mode bug also applies to swfdec. You may need xulrunner 3.0.2 (or find a way to disable windowless mode in swfdec, if possible).

---

### Post by aamukahvi on 2008-09-05
> **plun said:**
> Well... "the 64 bits trap"...:)

I have never understand any reason for running 64 bits on clients.
(perhaps with heavy math calculations)
I have been running 64-bit ever since I got 4 gigs ram. Pissed me off to no end having 4GB but only being able to use 3. So there you go.

As to why anyone would need more than 3GB of memory... go figure. I for one run VMs.

---

### Post by psyke83 on 2008-09-05
> **aamukahvi said:**
> I have been running 64-bit ever since I got 4 gigs ram. Pissed me off to no end having 4GB but only being able to use 3. So there you go.

As to why anyone would need more than 3GB of memory... go figure. I for one run VMs.

Hmm. Doesn't the 32bit -server kernel support PAE to allocate the full 4GB? You should be using that kernel if you run VMs anyway.

---

### Post by plun on 2008-09-05
> **psyke83 said:**
> As far as I understand, the windowless mode bug also applies to swfdec. You may need xulrunner 3.0.2 (or find a way to disable windowless mode in swfdec, if possible).

I am testing with both 3.02pre and 3.1 and both crashes.

```
Loading stream: http://s.ytimg.com/yt/swf/watch-vfl53733.swf
unhandled event 19
Loading stream: http://www.youtube.com/crossdomain.xml
Loading stream: http://v20.cache.googlevideo.com/get_video?video_id=EQ-JyAGUsys&origin=dal-v127.dal.youtube.com&signature=AEEC02C9CE5A3AE48EADFAC740CC95F3F9CB9298.64E84F226C6566872D7B86222659C7C9BF525B1C&ip=85.226.33.207&ipbits=8&expire=1220654788&key=yt1&sver=2
**firefox: pcm_pulse.c:278: pulse_write: Assertion `pcm->last_size >= (size * pcm->frame_size)' failed.**
Aborted (core dumped)

```

"D--ned" pulse again....  filing a bug...

---

### Post by Slug71 on 2008-09-05
Im only using 64 bit because 32 bit Alpha 3&4 wouldnt install for me. It would just hang at the installation screen after choosing your language. Will try Alpha 5 32 bit once it is released as that is probably going on my Parents PC too because XP is too slow on their PC and they dont keep their Anti-Virus and such up to date all the time.

---

### Post by psyke83 on 2008-09-05
> **plun said:**
> I am testing with both 3.02pre and 3.1 and both crashes.

```
Loading stream: http://s.ytimg.com/yt/swf/watch-vfl53733.swf
unhandled event 19
Loading stream: http://www.youtube.com/crossdomain.xml
Loading stream: http://v20.cache.googlevideo.com/get_video?video_id=EQ-JyAGUsys&origin=dal-v127.dal.youtube.com&signature=AEEC02C9CE5A3AE48EADFAC740CC95F3F9CB9298.64E84F226C6566872D7B86222659C7C9BF525B1C&ip=85.226.33.207&ipbits=8&expire=1220654788&key=yt1&sver=2
**firefox: pcm_pulse.c:278: pulse_write: Assertion `pcm->last_size >= (size * pcm->frame_size)' failed.**
Aborted (core dumped)

```

"D--ned" pulse again....  filing a bug...

Don't file a new bug! [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326)

---

### Post by psyke83 on 2008-09-05
> **Slug71 said:**
> Im only using 64 bit because 32 bit Alpha 3&4 wouldnt install for me. It would just hang at the installation screen after choosing your language. Will try Alpha 5 32 bit once it is released as that is probably going on my Parents PC too because XP is too slow on their PC and they dont keep their Anti-Virus and such up to date all the time.

Uhm, are you crazy? ;). Put a stable release on your parents' PC, test Intrepid and file bugs on your own. Unless your parents intend to file bugs...?

---

### Post by Slug71 on 2008-09-05
> **psyke83 said:**
> Uhm, are you crazy? ;). Put a stable release on your parents' PC, test Intrepid and file bugs on your own. Unless your parents intend to file bugs...?


Haha, well Intrepid seems to be pretty stable for me except for Firefox at the moment. They have an older laptop(few years old i think) so i think it should be fine on there. They only really use internet, email and skype. But i have Hardy on cd which i wont be needing anymore so i'll probs just send them that.

---

### Post by ubulette on 2008-09-05
> **mc4100 said:**
> 
It might fail catastrophically, so first backup .mozilla, then add the repository below in software sources (or edit sources.list manually, if you wish)
```
deb http://ppa.launchpad.net/fta/ubuntu intrepid main
```
And then search for firefox in Synaptic ... you want firefox-3.1 , and also firefox-3.1-gnome-support packages.

If everything went smoothly, you now have a menu entry "Minefield 3.1 Web Browser", and if you want it to use the upgraded JavaScript engine:
Type "about:config" in the awesome-bar, press enter, type "jit" into the filter box and double click on the "javascript.options.jit.content" preference.


Thanks for pointing to my PPA. A few comments though:
1/ my package will create a copy of the default firefox profile at the 1st run, then it will use it. It will never touch the original (this means 3.0 and 3.1 can run at the same time)
2/ I don't recommend jit for now, it's not stable yet. You may have a bad user experience with it. Wait for it to become default.
3/ my package calls Minefield all intermediate snapshots, and Shiretoko all releases. I will call it Firefox only when upstream starts calling it that way.

---

### Post by oldsoundguy on 2008-09-05
It really makes no difference if they freeze FireFox and related for a build or not.  They froze it at FF2 for Gutsy yet I am running FF3.X (not beta) on Gutsy machines.

Simply because I did not select from the repository but went to Source Forge and the Ubuntuzilla project.  Works great and it tells me when there is an update available .. although (if you read the instructions) it IS a bit more complicated to update, but not impossible.

---

### Post by gjoellee on 2008-09-05
Firefox 3.1 will be so much as up to 7times faster, + MANY bug fixes etc......etc.....etc.....

---

### Post by plun on 2008-09-05
> **psyke83 said:**
> Don't file a new bug! [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/262326)

Thanks  ! ....  add this info to your bug.

EDIT also confirmed PA

---

### Post by Slug71 on 2008-09-05
> **mc4100 said:**
> Then why not try it out?
It's far better to find out early if there are any serious issues;
It might fail catastrophically, so first backup .mozilla, then add the repository below in software sources (or edit sources.list manually, if you wish)
```
deb http://ppa.launchpad.net/fta/ubuntu intrepid main
```
And then search for firefox in Synaptic ... you want firefox-3.1 , and also firefox-3.1-gnome-support packages.

If everything went smoothly, you now have a menu entry "Minefield 3.1 Web Browser", and if you want it to use the upgraded JavaScript engine:
Type "about:config" in the awesome-bar, press enter, type "jit" into the filter box and double click on the "javascript.options.jit.content" preference.

Done ... Browse Away!


Or, you can grab the source [here]("http://releases.mozilla.org/pub/mozilla.org/firefox/releases/shiretoko/alpha1/").


So i did this to give 3.1 a try and ended up getting 3.0.2??
Anyway will give this a try for a while and see how that goes.

---

### Post by Slug71 on 2008-09-05
I think 3.0.2 is just as bad as 3.0.1.

---

### Post by mc4100 on 2008-09-05
> **Slug71 said:**
> So i did this to give 3.1 a try and ended up getting 3.0.2??
Anyway will give this a try for a while and see how that goes.

 Ok ... I have to ask: 
after adding the ppa, did you go in and explicitly install 3.1. Or something else like update?

---

### Post by Slug71 on 2008-09-05
> **mc4100 said:**
> Ok ... I have to ask: 
after adding the ppa, did you go in and explicitly install 3.1. Or something else like update?


Did update. Came straight in after i closed Software Sources.

Removed 3.0.2 already though as it was worse than 3.0.1.

---

### Post by mc4100 on 2008-09-05
> **Slug71 said:**
> Did update. Came straight in after i closed Software Sources.

Removed 3.0.2 already though as it was worse than 3.0.1.
OK, that makes sense;
The PPA has an updated firefox-3.0 package (that includes 3.0.2, not 3.1), so that's why when you updated, you only got 3.0.2 .

If you still want to try 3.1, this should do the trick:
```
sudo apt-get install firefox-3.1 firefox-3.1-gnome-support
```

---

### Post by Slug71 on 2008-09-05
Awesome, thanks!

---

### Post by plun on 2008-09-05
@Slug71

A little more so you are within "the match" ...:)

Every ppa is like a repo.

Please take a look at below URL,   scroll down so you sees all packages

[https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)


Have Fun !

---

### Post by Slug71 on 2008-09-05
> **plun said:**
> @Slug71

A little more so you are within "the match" ...:)

Every ppa is like a repo.

Please take a look at below URL,   scroll down so you sees all packages

[https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)


Have Fun !


Thanks plun, really starting to dig this Ubuntu/Linux thing thanks to this forum and the people on it.
If only Linux was supported by TomTom Home i could trully say good bye to Windows.
Very much doubt Windows will be on the Desktop i build next year.

---

### Post by Nullack on 2008-09-05
Please keep in mind that if your using external repos and PPAs that your no longer on the Intrepid build configuration and any bug reports or unexpected behaviour needs to address your build not being Intrepids.

---

### Post by Slug71 on 2008-09-05
Cool, thanks.

---

