---
title: "Alphas are going down instead of up"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-09-03
With Jaunty, the Alphas sucked, but got better with time. Karmic is the opposite. Alpha 4 wouldn't install/upgrade, etc. PERIOD. Alpha 5 is all fancy and fine but I can't activate my NVIDIA Drivers (tried both). I get booted to console and startx don't work, says no displays useable. I tried the drivers I downloaded from NVIDIA but can't compile. What's up?

---

### Post by joey-elijah on 2009-09-03
...and i've just hit pause on my .iso download. NVIDIA driver cuffufle = no show for me.

---

### Post by nanog on 2009-09-03
Two words: borked libc6.

---

### Post by lcohen999 on 2009-09-03
Just add the nvidia PPA and install it manually

took me 10 minutes and everything is working properly

---

### Post by zenarcher on 2009-09-03
I don't know.  I just did a fresh install of Kubuntu 9.10 Alpha 5 (64 bit) here.  I installed the Nvidia driver in the usual way using Hardware Drivers.  The Nvidia driver installed just fine and is working normally.

Cheers,
zenarcher

---

### Post by SigmaSanti on 2009-09-03
You guys get a GUI, I just get a console asking me to enter my ubuntu password when trying to run the 64bit livecd.

---

### Post by zenarcher on 2009-09-03
I forgot to mention that I used the Alternate Install CD, as I've had trouble with some of the Alpha LiveCD's.

Cheers,
zenarcher

---

### Post by TheForkOfJustice on 2009-09-03
I'm finding that the torrent is massively slow.  This is the TORRENT mind you.  Of a new Ubuntu Alpha release...

Hopefully the install will be worth it and I won't have many bugs like the fact I have no wired internet with Alpha 4.

---

### Post by Seventh Reign on 2009-09-03
No problems here with Nvidia Drivers.  Alphas 4 and 5 are flawless thus far.

---

### Post by SigmaSanti on 2009-09-03
> **Seventh Reign said:**
> No problems here with Nvidia Drivers.  Alphas 4 and 5 are flawless thus far.

Lucky
Did you do anything special?

---

### Post by exploder on 2009-09-03
Personally, I think the quality is going up. At this stage of development I think this release is very good and I hope it continues to improve.Considering all of the underlying improvements to the system, it is very stable.

---

### Post by Tibuda on 2009-09-03
> **Seventh Reign said:**
> No problems here with Nvidia Drivers.  Alphas 4 and 5 are flawless thus far.

Neither here. Everything is perfect without tweaking.

---

### Post by Xgen on 2009-09-03
I haven't had a problem with the karmic alphas/kernels with the 173 nv propriety drivers....as long as I purge the repo drivers which don't work.

---

### Post by jerrylamos on 2009-09-03
On this IBM ThinkCentre 2 gHz Celeron 1 gb memory with i845 video:

Alpha 2 booted and ran with intel video driver.

Alpha 3 wouldn't boot with intel video driver, had to use "vesa".

Alpha 4, same as 3, and now the Epson USB printer doesn't print.

Alpha 5 CD doesn't boot at all, pressing a key on the initial boot menu screen causes the CD to whirl then quit.  No action.  Time after time.  

On IBM Thinkpad T40 Pentium P4 with ati graphics the same CD does self check the CD no errors and does boot.  A couple of crashes occurred so launchpad bugs are being reported.

In past releases as time went on more and more changes went in to the Alpha's resulting in more and more significant bugs......many of which but not all were fixed by Release Code level.

The pc is multi-booted with intrepid & jaunty both running on same hardware O.K.

Jerry

---

### Post by Eclipse. on 2009-09-03
> **jerrylamos said:**
> On this IBM ThinkCentre 2 gHz Celeron 1 gb memory with i845 video:

Alpha 2 booted and ran with intel video driver.

Alpha 3 wouldn't boot with intel video driver, had to use "vesa".

Alpha 4, same as 3, and now the Epson USB printer doesn't print.

Alpha 5 CD doesn't boot at all, pressing a key on the initial boot menu screen causes the CD to whirl then quit.  No action.  Time after time.  

On IBM Thinkpad T40 Pentium P4 with ati graphics the same CD does self check the CD no errors and does boot.

In past releases as time went on more and more changes went in to the Alpha's resulting in more and more significant bugs......many of which but not all were fixed by Release Code level.

The pc is multi-booted with intrepid & jaunty both running on same hardware O.K.

Jerry

Did you report bugs for all those issues? The developers can only fix them if you tell that about it.

---

### Post by trulan on 2009-09-03
The early Karmic Alphas were a little too good to be true.  This is more like it.  :P

I'm not a bit worried that things will be unstable once we hit the release date.  But if all the Alpha stuff is working flawlessly, don't you think the developers should be being a bit more adventurous and creative?

After all, the bugs are the reason we are alpha testers.

---

### Post by OliW on 2009-09-04
> **lcohen999 said:**
> Just add the nvidia PPA and install it manuallyThere's a nvidia driver PPA?

---

### Post by theozzlives on 2009-09-04
Well it's a test machine, I guess I can do without effects. It just urks me that I got the card cause Jaunty barfed on my Intel card.

---

### Post by ELD on 2009-09-04
Well heres to Alpha6...

---

### Post by andrek on 2009-09-04
Same goes for ATI drivers. They're simply f**ked up and there's no way they would work on karmic now ( ati 4570 in dell studio 1555 ).

---

### Post by raiwo on 2009-09-04
how is power management working in laptops in this version? Since 7.10 i have lost 1 hour of working time when using battery, 7.10 i had 2h15mins and now 9.04 i have 1h10mins battery time left and battery is just fine; charges full etc. using also powertop to kill all power consuming processes.

---

### Post by theozzlives on 2009-09-04
> **raiwo said:**
> how is power management working in laptops in this version? Since 7.10 i have lost 1 hour of working time when using battery, 7.10 i had 2h15mins and now 9.04 i have 1h10mins battery time left and battery is just fine; charges full etc. using also powertop to kill all power consuming processes.

How does this apply to video :confused:

---

### Post by NCLI on 2009-09-04
Well, the testing releases aren't supposed to grow much more stable during the alpha phase, that's what we do beta-testing for.

---

### Post by ranch hand on 2009-09-04
With the feature freeze last week and user interface freeze next week, I would say that we should expect some trouble as this stuff is thrown in.  There are a lot of very different things here from what we have been using.

I think that this is going to be slick and fast when released, if a little buggy.  10.04 (LTS) should really rock.

I am a lttle excited.

---

### Post by theozzlives on 2009-09-05
> **NCLI said:**
> Well, the testing releases aren't supposed to grow much more stable during the alpha phase, that's what we do beta-testing for.

Well Intrepid and Jaunty got good at about Alpha 6. 3 Seemed pretty stable with Karmic, however. Then it blew up in my face.

---

### Post by taavikko on 2009-09-05
Have to chime in,
It should make no difference what's the quality of alpha release, it's the final that counts.
That's why we test it, find the bugs, report etc.

Feature freeze was a week ago. So we have the latest of what upstream has to offer.
Now the work starts to putting pieces together for the final release.
As always, any man made software has bugs.

---

### Post by andrewabc on 2009-09-05
I'm expecting 9.10 to be rough since they are incorporating lots of new stuff and want to get everything possible in so 10.04 will be a more polished version of 9.10.

Usually by alpha 5 it is usable, but this alpha is kinda bad. I boot up, get two different loading progress bars, no icons in menus. I click to open firefox and it says it crashed (I click again and it opens fine). I try to remote desktop view my other 9.04 desktop and it crashes (Different remote desktop view not compatible?). I'm happy that intel graphics are still working great.

I hope all the major obvious problems are fixed for the beta, so people can focus on finding small bugs :)

---

### Post by ELD on 2009-09-05
How many times do people need to get told no icons thing is a feature of gnome now, they are taken icons out of lots of things :\

As far alphas getting worse i agree, i can boot alpha 3 but not 5 :(.

It is a bit annoying when they make such huge changes from one release to another, ubuntu seems to have no consistency anymore.

---

### Post by andrewabc on 2009-09-05
> **ELD said:**
> How many times do people need to get told no icons thing is a feature of gnome now, they are taken icons out of lots of things :\


There is a space where icons used to be. If they are getting rid of icons (why?), then I don't see the need for a large space before the text.

Who came up with the idea at gnome to get rid of icons? I'm not sure how it is beneficial. Is it going to be a text only distro? Trying to make all the programs get rid of icons in menus?

Does this mean the ubuntu icon for applications at top left corner will go away?

---

### Post by MacUntu on 2009-09-05
> **ELD said:**
> It is a bit annoying when they make such huge changes from one release to another, ubuntu seems to have no consistency anymore.

"Please no big changes." - "Nothing's moving. Too few changes." - "Please not too much breakage during the alpha phase." - "Please no boring development releases without breakage." No wonder developers give this forum a wide berth.

If you are afraid of big changes, don't upgrade your system twice a year?

---

### Post by ELD on 2009-09-05
No idea who came up with it, and obviously there will still be icons in places, but certain places will no longer have them. Nothing to do with ubuntu its Gnome being stupid.

> **MacUntu said:**
> "Please no big changes." - "Nothing's moving. Too few changes." - "Please not too much breakage during the alpha phase." - "Please no boring development releases without breakage." No wonder developers give this forum a wide berth.

If you are afraid of big changes, don't upgrade your system twice a year?

Now your just being rather silly. Who said they are "afraid" of big changes? I am talking about minor annoyances like moving the shutdown button from one place to another, when the place it had before was fine and other weird ideas.

I wouldn't upgrade if i didn't want half the changes though obviously.

Changes are great and the distro at times really feels like it is moving forward, but a lot of the time it's change for the sake of change.

---

### Post by 23meg on 2009-09-05
[QUOTE=taavikko]It should make no difference what's the quality of alpha release, it's the final that counts.
That's why we test it, find the bugs, report etc.
[/QUOTE]

This.

I have a hard time understanding people spending a lot of time comparing the quality of milestone releases *after the fact*. It makes sense to care about release quality before a milestone, since we want milestones to be reasonably free of bugs, at least more so than daily images, [and perform additional testing on a best effort basis so that they can be tested by a wider audience]("https://wiki.ubuntu.com/Testing#ISO%20testing"), but in the end, they're slightly stabilized snapshots of the archive at some predetermined dates, and once they're out, they're out and that's the end of it.

There *will* be unforeseen issues, regressions, bloopers, despite the efforts, and the assumption that since each milestone builds on the previous one, they will necessarily "go up" for all given configurations is a false one.

Milestones are not ends in themselves; they're a means to an end, the final release. Still, if you care about making them better, so that more people will be able to *test* them, and more efficiently, you're more than welcome to contribute to [milestone ISO testing]("https://wiki.ubuntu.com/Testing#ISO%20testing").

---

### Post by 23meg on 2009-09-05
> **ELD said:**
> How many times do people need to get told no icons thing is a feature of gnome now, they are taken icons out of lots of things :\

How many times do people need to get told that, no, they're not taking icons out of things; they're just shipping a single gconf key disabled by default, as a first step to menu icon visibility being decided upon on a per-application basis, which is a saner way of dealing with it...

> **ELD said:**
> It is a bit annoying when they make such huge changes from one release to another, ubuntu seems to have no consistency anymore. 
[URL="http://en.wikipedia.org/wiki/Wikipedia:Avoid_weasel_words"]
What huge changes? You haven't cited any[/URL].

---

### Post by ELD on 2009-09-05
> **23meg said:**
> How many times do people need to get told that, no, they're not taking icons out of things; they're just shipping a single gconf key disabled by default, as a first step to menu icon visibility being decided upon on a per-application basis, which is a saner way of dealing with it...

[URL="http://en.wikipedia.org/wiki/Wikipedia:Avoid_weasel_words"]
What huge changes? You haven't cited any[/URL].

That is what i meant, off be default, i just poorly chose my wording of the situation.

And as for huge changes i don't want to get into a big debate about it, but ubuntu does change some big things from time to time, and like i said ubuntu is going forward, but for me there have been issues no one can seem to solve which is why i am eagerly awaiting Karmic.

---

### Post by 23meg on 2009-09-05
Yes, Ubuntu is making some bold changes, whose significance is easy to miss with short-term thinking. It's impossible to make bold changes *and* please everyone; some people will certainly be turned off by them, and that's good.

---

### Post by ELD on 2009-09-05
> **23meg said:**
> Yes, Ubuntu is making some bold changes, whose significance is easy to miss with short-term thinking. It's impossible to make bold changes *and* please everyone; some people will certainly be turned off by them, and that's good.

Yeah i know i wasn't massively complaining i was just stating near on exactly what you said there, again my wording was just off.

Either way i've got a new daily cd to see if it boots for me yet :D

---

### Post by MacUntu on 2009-09-05
Sorry for being snide. It's just that this forum is more about complaining than finding, confirming and help fixing bugs.

---

### Post by ELD on 2009-09-05
> **MacUntu said:**
> Sorry for being snide. It's just that this forum is more about complaining than finding, confirming and help fixing bugs.

Yeah i know, some times people end up venting rather than helping, but hey it happens to everyone.

Got my fingers crossed this cd boots up heh.

---

### Post by WishMaster on 2009-09-05
Burning cd's doesn't work since Jaunty, so I always use the "live usb" creator.

KK alpha 4: KVM doens't play well with Intel i855. "nomodeset" didn't work either.
KK alpha 5: KVM still doesn't work. Booting with "single modeset" gives me a DOS-like screen: "resume normal boot", "fixk broken packages", "terminal without internet", etc.
When I choose "resume normal boot", I see the new 'loading ubuntu bar'. When I expect to see the desktop, all I see is a black screen and my mouse pointer is the symbol of 'loading/opening'. And it stays like that forever...

so the alpha's are getting a LITTLE better for me, but I seriously doubt the full release will work properly...

---

### Post by ELD on 2009-09-05
> **WishMaster said:**
> 
so the alpha's are getting a LITTLE better for me, but I seriously doubt the full release will work properly...

This is exactly what we have just been on about, this is still ALPHA how the heck can you compare it to the full release?

I just tried a daily cd from today, doesn't boot up, but doesn't mean it won't on the next alpha.

---

### Post by ranch hand on 2009-09-05
> **WishMaster said:**
> Burning cd's doesn't work since Jaunty, so I always use the "live usb" creator.

KK alpha 4: KVM doens't play well with Intel i855. "nomodeset" didn't work either.
KK alpha 5: KVM still doesn't work. Booting with "single modeset" gives me a DOS-like screen: "resume normal boot", "fixk broken packages", "terminal without internet", etc.
When I choose "resume normal boot", I see the new 'loading ubuntu bar'. When I expect to see the desktop, all I see is a black screen and my mouse pointer is the symbol of 'loading/opening'. And it stays like that forever...

so the alpha's are getting a LITTLE better for me, but I seriously doubt the full release will work properly...
I have yet to see a fresh release of any OS by anyone that works perfectly at first.

9.10 will work well enough for an interim release.

10.04 is LTS and it will work well on release (with some small problems I am sure).  This is the whole point of 9.10 - get ready for 10.04.  If you stick with the LTS you will not have too much trouble.

I am not on it now but I still have 8.04 on here as my Main OS.  I don't use it as much as I do this 9.04 variant (Stoner Edition) but it is the one that I do all business from and trust to work every time I need it.

If you don't want breakage stick with the LTS and avoid, at all cost, alpha releases.

---

### Post by bear24rw on 2009-09-05
to get the icons back

gconf-editor

/desktop/gnome/interface/menus_have_icons

---

### Post by theozzlives on 2009-09-05
It just seems that Ubuntu is working on cosmetics to compete with other distros, and laxing off on functionality. The lack of default flashiness and a good solid OS is what sold me. They used to leave it to the user what "eye-candy" they want (or not). Of course I will always call myself a DOS man. I know times change but since DOS 5.0, I thought I finally found an OS/Distro that "just worked" and I think were going away from that, Although I like ext4 and Jaunty.

---

### Post by ranch hand on 2009-09-05
> **theozzlives said:**
> It just seems that Ubuntu is working on cosmetics to compete with other distros, and laxing off on functionality. The lack of default flashiness and a good solid OS is what sold me. They used to leave it to the user what "eye-candy" they want (or not). Of course I will always call myself a DOS man. I know times change but since DOS 5.0, I thought I finally found an OS/Distro that "just worked" and I think were going away from that, Although I like ext4 and Jaunty.
I quite agree with your sentiment.

I also think that you need to wait and see the final release.  I am actually getting more excited as time goes on.

Yes I have a number of 9.10 variations on my box that do not work right now (all 4 32bit ones work - 2 of 6 64bit ones do).  We are between feature freeze and user interface freeze.  I think breakage is to be expected.

Over all I think that 9.10 will be more functional.  Right now there are some basic changes that all seem to have to do with eye candy.  The only one that I think really is about looks is the slide show on the CD.

It could never appear and I would be happy.

Other than that I think most of the problems are just basic getting things to go with the kernal.

A lot of folks here on the forums think way too little effort is spent on cosmetics.  I am not one of them.  I think that functionality is still what most are looking for and what is being developed.

---

### Post by WishMaster on 2009-09-06
> **ELD said:**
> This is exactly what we have just been on about, this is still ALPHA how the heck can you compare it to the full release?
I can't compare it obviously.
That's also why I try the alpha's as a "live usb", just to see what works (or not). I certainly don't use it as a primarily system.

I am just saying that KVM seems to be the new item for Karmic, and that it isn't working properly (for my system) with only 2 months from the 6 to go...

---

### Post by theozzlives on 2009-09-06
> **WishMaster said:**
> I can't compare it obviously.
That's also why I try the alpha's as a "live usb", just to see what works (or not). I certainly don't use it as a primarily system.

I am just saying that KVM seems to be the new item for Karmic, and that it isn't working properly (for my system) with only 2 months from the 6 to go...

Yeah, I got tired of wasting CDs so I went RW.

---

### Post by theozzlives on 2009-09-09
Well with the introduction of 2.6.31.10, I am now able to install my NVIDIA drivers on Alpha 5. Still no sound.... once had it, now I don't.

EDIT: Sound's working now. I thought Alpha 5 was stable enough to use on my laptop, but it threw-up all over my Broadcom 4312 card when it worked fine in Alpha 3. I don't know why they are changing things that work. Alpha 3 was way unfinished, but usable.

I also want to change my GDM background to /usr/share/gdm/themes/human/background.png, and my login logo to be as attached. any ideas?

---

### Post by WishMaster on 2009-09-21
> **WishMaster said:**
> I can't compare it obviously.
That's also why I try the alpha's as a "live usb", just to see what works (or not). I certainly don't use it as a primarily system.

I am just saying that KVM seems to be the new item for Karmic, and that it isn't working properly (for my system) with only 2 months from the 6 to go...

Okay, I must say I am pretty amazed --> alpha 6 is booting !

---

### Post by theozzlives on 2009-09-22
> **WishMaster said:**
> Okay, I must say I am pretty amazed --> alpha 6 is booting !

Alpha 5 worked fine after 2.6.31.10, I tryed it on my laptop and it couldn't get my wireless. I know, not for production systems....

---

