---
title: "Plymouth."
date: 2008-10-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klange on 2008-10-31
Plymouth is a very graphical boot splash (by RHEL, and which will be shipping in the next Fedora release) that operates at the appropriate display mode for your monitor and provides some pretty cool visuals.

You can read the article [on Phoronix](http://www.phoronix.com/scan.php?page=article&item=fedora_plymouth&num=1), which gives a fairly good review of the features and strong points, and it has videos.

Basically, the idea is that in the 30 seconds it takes for your machine to boot, you shouldn't be flickering through different display modes or staring at a horribly scaled frame-buffer splash. By setting the display mode appropriately, the transition between Plymouth and X is seamless, and with a matching Plymouth and GDM theme, you can do all sorts of visually appealing things.

---

### Post by bash on 2008-10-31
Would love to see a more feature rich (KMS) and easier to use boot splash. From what I understand usplash isn't the simplest to make new themes for. And splashy as a replacement was declined by the Devs. So this might be a good opportunity to make a switch to system that would also have more adoption than usplash. 

The only thing I don't want though is that this just gets implemented because it is in theory a neat thing, but practically not really ironed out, as happened with Pulse Audio. There was kind of a hype to have it in Ubuntu as well, because it sounded like salvation for a whole lot of audio problems, but it would probably have been to have waited another release or two until Pulse Audio was a bit smoother around the edges.

---

### Post by smartboyathome on 2008-10-31
Plymouth requires the modesetting patches to be applied to the kernel in order to use it. If they aren't, it just reverts to the text mode. So until the patches get accepted into the kernel, we won't get this.

---

### Post by hexion on 2008-10-31
> **smartboyathome said:**
> Plymouth requires the modesetting patches to be applied to the kernel in order to use it. If they aren't, it just reverts to the text mode. So until the patches get accepted into the kernel, we won't get this.

The KMS patches will be probably integrated in 2.6.29 [http://www.phoronix.com/scan.php?page=news_item&px=NjgyNA](http://www.phoronix.com/scan.php?page=news_item&px=NjgyNA) which will probably be kernel for the next Ubuntu iteration. So that won't be a problem.

The only problem would be from the drivers perspective. AFAIK, currently only the Intel drivers and the open source radeon support it. Others such as nvidia or ati propietary would fall back to console mode.

---

### Post by Martje_001 on 2008-11-01
This may be a stupid question, but, can't we use both? That if Plymouth fails Ubuntu will fall back on Usplash?

---

### Post by meastp on 2008-11-01
That video on Phoronix demonstrating Plymouth is really, *really* nice!

Especially the "sun" (has a "sun" in the lower right corner), which is very well integrated - the transition between boot, gdm and desktop is seamless. A couple of themes with that quality, and I would reboot all day! :)

---

### Post by gnomeuser on 2008-11-01
> **Martje_001 said:**
> This may be a stupid question, but, can't we use both? That if Plymouth fails Ubuntu will fall back on Usplash?

No by it's nature plymouth needs a certain level of integration. but the good news is that plymouth provides both a text only ascii fallback progressbar (also demoed n phoronix) while not pretty it will always work regardless of what level of support your system has. Additionally it has support for vesa framebuffer for cards that currently do not support Kernel Modesetting. vesafb is the same technology as usplash uses in essence so you have both, in a strict sense. 

You could setup the default to have vesafb 800x600 for all machines not white listed for kernel modesetting, then you would have the exact same experience as you do now. Only with the option to ramp up the resolution manually or switch over seemlessly when your setup becomes KMS enabled. 

Plymouth does offer both, e.g. I use it both on my KMS supported ATI card on the desktop and via the framebuffer on the nvidia card in my laptop. For machines such as certain servers which do not need this there are also plugins to provide text only output.

---

### Post by | MM | on 2008-11-03
While i agree Plymouth is nice, the [Intel engineers]("http://lwn.net/Articles/299483/") who got a Linux system to boot in 5 seconds make a good point.  They argue that the time invested in software such as Plymouth would be better invested in actually reducing the need for fancy boot splashes in the first place, i.e. reducing Linux boot time.

---

### Post by smartboyathome on 2008-11-03
> **| MM | said:**
> While i agree Plymouth is nice, the [Intel engineers]("http://lwn.net/Articles/299483/") who got a Linux system to boot in 5 seconds make a good point.  They argue that the time invested in software such as Plymouth would be better invested in actually reducing the need for fancy boot splashes in the first place, i.e. reducing Linux boot time.

While that is good, we do not want a whole bunch of text going across the screen either. I think that making the boot fast is just as needed as making the boot as graphically seamless as possible.

---

### Post by gnomeuser on 2008-11-03
> **| MM | said:**
> While i agree Plymouth is nice, the [Intel engineers]("http://lwn.net/Articles/299483/") who got a Linux system to boot in 5 seconds make a good point.  They argue that the time invested in software such as Plymouth would be better invested in actually reducing the need for fancy boot splashes in the first place, i.e. reducing Linux boot time.

Sure.. but you are not going to get any regular desktop to boot in 5 seconds. It doesn't have an SSD for the quick reads, it will need more support than Arjan' example. We can make it faster but there will likely be a need to still have some nice graphics to distract us all.

There is an entire thread dedicated to the 5 sec boot demo which amply highlights many of the problems that target has for your average desktop.

---

### Post by Gourgi on 2008-11-04
> **gnomeuser said:**
> Sure.. but you are not going to get any regular desktop to boot in 5 seconds. It doesn't have an SSD for the quick reads, it will need more support than Arjan' example. We can make it faster but there will likely be a need to still have some nice graphics to distract us all.

There is an entire thread dedicated to the 5 sec boot demo which amply highlights many of the problems that target has for your average desktop.

here are the threads for anyone interested 
[http://ubuntuforums.org/showthread.php?t=930579](http://ubuntuforums.org/showthread.php?t=930579)
[http://ubuntuforums.org/showthread.php?t=936797](http://ubuntuforums.org/showthread.php?t=936797)

sorry for being off-topic

---

### Post by plun on 2008-11-05
Fedora 10 pre-release is out, also Live CDs

[https://fedoraproject.org/get-prerelease](https://fedoraproject.org/get-prerelease)

I also ckecked Plymouth GIT and it builds without any issues..

initramfs/initrd...:confused:

---

### Post by smartboyathome on 2008-11-05
> **plun said:**
> Fedora 10 pre-release is out, also Live CDs

[https://fedoraproject.org/get-prerelease](https://fedoraproject.org/get-prerelease)

I also ckecked Plymouth GIT and it builds without any issues..

initramfs/initrd...:confused:

It won't work on Ubuntu though unless you recompile the kernel with the modesetting patches (which I have tried and can't get to patched to the kernel, though I am probably using old patches).

---

### Post by philinux on 2008-11-05
Interesting stuff
[http://uk.youtube.com/watch?v=ogzsX2b42fU](http://uk.youtube.com/watch?v=ogzsX2b42fU)

---

### Post by plun on 2008-11-06
Yup... Plymouth is beautiful.

Fedora also got kerneloops....

[[img]http://ubuntu-pics.de/thumb/5253/fail_98SIKR.jpg[/img]](http://ubuntu-pics.de/bild/5253/fail_98SIKR.jpg)

Error handle was nice...

---

### Post by Slug71 on 2008-11-23
Does anyone know how Plymouth has turned out for F-10?
I really hope the we get it.


Kerneloops by default would be nice too.

---

### Post by amano on 2008-11-23
> **Slug71 said:**
> 

Kerneloops by default would be nice too.

At least for the development builds...

---

### Post by stephantom on 2008-11-24
It would be nice to get Plymouth for JJ, but I seriously doubt it's going to happen.
Ubuntu is very conservative when it comes to the bootup process. We spent a lot of time hacking together usplash and it's been said on numerous occasions that it won't be let go all too quickly if there is no extremely well tested alternative available.
Note that one target for JJ is indeed the booting process. But they're aiming to *speed it up* not to make it pretty.

---

### Post by MacUntu on 2008-11-24
> **stephantom said:**
> hacking together usplash
At least that's how it looks like: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/276727](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/276727) :D

> But they're aiming to *speed it up* not to make it pretty.
Too bad they won't be able to speed it up enough to make the task "make it pretty" obsolete. So there's still work to do. :)

---

### Post by Slug71 on 2008-11-24
Found this on Brainstorm. It ain't mine but just figured i'd post it to help promote.


[[IMG]http://brainstorm.ubuntu.com/idea/11165/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/11165/)

---

### Post by ktp on 2008-11-24
plymouth would be nice additions at least for 30 seconds...

The other part of me says, why not just make boot really really fast so we don't need a nice boot screen.

---

### Post by Slug71 on 2008-11-24
> **ktp said:**
> 
The other part of me says, why not just make boot really really fast so we don't need a nice boot screen.

Thats just not realistic. Ubuntu's boot time is not really that bad IMO.

---

### Post by phenest on 2008-11-24
What about hibernation? I've always had to watch a blank screen, and wondered if usplash could be used. What about Plymouth? It's nice to know your computer is doing something instead of watching hard drive activity.

---

### Post by MaX on 2008-11-24
> **Slug71 said:**
> Thats just not realistic. Ubuntu's boot time is not really that bad IMO.

Eh, yes it is...

We could save alot of time NOT starting what isn't used.

Boot time is where we should put our money and time, not pretty startup screens that you shouldn't look at anyway.

If my computer takes 40-60 seconds to boot (from button pressed to usable desktop) I won't be there in front of my computer, I'll go away, take a dump or whatever.
If I'm in a hurry to get the latest bus times I need my computer to boot fast, nothing else.
And besides, I start my computer once or twice a day, that's 2 minutes a day that I want something pretty?

---

### Post by olskar on 2008-11-24
> **MaX said:**
> Eh, yes it is...

We could save alot of time NOT starting what isn't used.

Boot time is where we should put our money and time, not pretty startup screens that you shouldn't look at anyway.

If my computer takes 40-60 seconds to boot (from button pressed to usable desktop) I won't be there in front of my computer, I'll go away, take a dump or whatever.
If I'm in a hurry to get the latest bus times I need my computer to boot fast, nothing else.
And besides, I start my computer once or twice a day, that's 2 minutes a day that I want something pretty?

I don't think boot time is where we should put our money and time, I think the focus should be a on a very fast system once it is started. I think most people would accept ~30 seconds longer boot to have a really fast system.

---

### Post by Slug71 on 2008-11-24
Agreed, the system performance needs improvement like the loading of appz etc. 
Sure boot time could be tweaked a little but trying to achieve a boot time of 15sec and under is not gonna happen.

---

### Post by MacUntu on 2008-11-24
> **Slug71 said:**
> achieve a boot time of 15sec and under is not gonna happen.
Impossible is nothing: [http://img.xrmb2.net/images/894429.png](http://img.xrmb2.net/images/894429.png)
Add parallel init and 15 seconds are yours. :D 

Ok, bootchart in Ubuntu is not telling the whole truth. A starting GDM is far from a usable system.

I think 30 seconds from GRUB to a usable desktop should be possible on a 1-2 years old system.

---

### Post by decard_pain on 2008-11-24
there's no way to get 15 second bootup .
until solid state drives become more wide spread(and better engineered) 

it will probably happen by 2011-20012

i can't see it happening before that

but back to the topic this Plymouth thing looks interesting.
a unified boot to desktop theme would be nice 

but hopefully not another brown theme

---

### Post by MacUntu on 2008-11-24
There was no brown in the last four (same) usplash themes. :confused:

---

### Post by decard_pain on 2008-11-24
the splash should be almost identical to the the desktop so it looks smoother from boot to desktop

---

### Post by Geekkit on 2008-11-24
> **Slug71 said:**
> Thats just not realistic. Ubuntu's boot time is not really that bad IMO.

Seconded. I watch XP with all the services it employs (including anti-virus S/W), and worse, Vista which, yes, does show you a desktop faster than XP and sometimes Linux, but Vista takes another two minutes to allow you to *use* said desktop.

I would much rather see resources put into speeding up the runtime of the kernel. For example, by performing prefetch analysis (i.e., reference patterns) of applications (e.g., like how Windows stores that information in prefetch files) which is used for prefetch heuristics. This would help increase application loading (e.g., OO, GIMP).

EDIT: An interesting read:

[http://people.cs.vt.edu/~butta/docs/sigmetrics05_kernelPrefetch.pdf](http://people.cs.vt.edu/~butta/docs/sigmetrics05_kernelPrefetch.pdf)

---

### Post by Gourgi on 2008-11-25
> **decard_pain said:**
> the splash should be almost identical to the the desktop so it looks smoother from boot to desktop

+1

---

### Post by MaX on 2008-11-25
> **olskar said:**
> I don't think boot time is where we should put our money and time, I think the focus should be a on a very fast system once it is started. I think most people would accept ~30 seconds longer boot to have a really fast system.

So where does Plymoth make my system really fast?

I won't complain as long as boot time is under 60 seconds, but if it could be under 30 then that is even better.
That's saving 6 hours per year in boot time :) (if you start your computer two times a day every day of the year.)

---

### Post by Slug71 on 2008-11-25
It boots in about 30 secs for me.

---

### Post by klange on 2008-11-25
> **MaX said:**
> So where does Plymoth make my system really fast?

I won't complain as long as boot time is under 60 seconds, but if it could be under 30 then that is even better.
That's saving 6 hours per year in boot time :) (if you start your computer two times a day every day of the year.)

It's not supposed to make anything faster, but the CPU does stop momentarily when switching display modes, so I guess there could be some time saved there...

@decard_pain: In Fedora, it looks a bit different (it's the same thing, but from a different angle). It fades quite nicely into GDM, which then matches the desktop. The potential for transition effects is astonishing.

---

### Post by MaX on 2008-11-25
Yeah, but that's just graphical fluff...

What my convert friends complain about is Nautilus not sorting pictures after exif-date like in Windows, EOG not saving the rotation made to the actual image... No one complains about boot speed or that it doesn't look nice. They all complain about features that they miss from Windows.
We have bugs that are over 6 years old that no-one takes a look at because they are sorted under enhancement instead of bug.

We've got bigger fish to fry than looking good at boot.

---

### Post by klange on 2008-11-25
> **MaX said:**
> Yeah, but that's just graphical fluff...

What my convert friends complain about is Nautilus not sorting pictures after exif-date like in Windows, EOG not saving the rotation made to the actual image... No one complains about boot speed or that it doesn't look nice. They all complain about features that they miss from Windows.
We have bugs that are over 6 years old that no-one takes a look at because they are sorted under enhancement instead of bug.

We've got bigger fish to fry than looking good at boot.
And the people working on things like Plymouth have no interest in such things, and many are not qualified.

---

### Post by MadsRH on 2008-11-25
> **MaX said:**
> ...We've got bigger fish to fry than looking good at boot.

We do, but we also need to fry that fish. This is important - if not, why would a big company like Red Hat spend time and money on a project like Plymouth?


**//MadsRH**
[anotherubuntu.blogspot.com]("anotherubuntu.blogspot.com")

---

### Post by MacUntu on 2008-11-25
> **MaX said:**
> EOG not saving the rotation made to the actual image...
Yeah, why not adopt another flaw? EOG is a viewer and not there to manipulate images causing quality loss (yes, Windows ruins your pictures every time you rotate 'em).

---

### Post by Slug71 on 2008-11-25
Also, one of the main focuses of Jaunty is to fix bugs and catch up on the old ones as well as speed. 

If Plymouth does make it, it will most likely be one of a handfull of new features Jaunty will get.

---

### Post by MadsRH on 2008-11-26
> **MacUntu said:**
> Yeah, why not adopt another flaw? EOG is a viewer and not there to manipulate images causing quality loss (yes, Windows ruins your pictures every time you rotate 'em).

Well, there's a big dialogbox telling you that there will be quality loss ;-)

---

### Post by MaX on 2008-11-26
> **MacUntu said:**
> Yeah, why not adopt another flaw? EOG is a viewer and not there to manipulate images causing quality loss (yes, Windows ruins your pictures every time you rotate 'em).
Yes I do know about the quality loss, I tried rotating in GIMP but that also ruins the image.

You now there is a way to rotate without loosing quality don't you?

EXIF! Just tell the damn picture that left-is-bottom or right-is-bottom et voilá! Picture is rotated but no quality loss.

---

### Post by vishalrao on 2008-11-26
as "mpt" posted in the mailing lists: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-November/006386.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2008-November/006386.html)

---

### Post by phenest on 2008-11-26
> **MaX said:**
> ...EOG not saving the rotation made to the actual image...

Actually, it does. I use that feature a lot, ever since Edgy. But have you ever thought of filing a bug? I did once about another issue with EOG, and they fixed it pretty quickly.

Don't complain about missing, incomplete, or buggy features, when you could be helping to fix them.

Getting back on-topic, I'm quite happy with usplash, but again, would like to see both usplash and Plymouth utilised during hibernation. Will this ever happen? Should I file a feature request?

My laptop boots in about 20 secs, and I'm not particularly bothered about what the boot screen looks like, so long as I know it's doing something. Implementing fancy graphics for the sake of a one-off 30 second (on average) graphical boot screen, seems a bit pointless. Besides, I never see these boot screens very often as I use hibernation (have I mentioned that already:lolflag:).

---

### Post by autocrosser on 2008-11-26
A respond to my note to the developer-list:

Date: Wed, 26 Nov 2008 10:01:03 +0000
From: Matthew Paul Thomas [EMAIL="mpt@canonical.com"]<mpt@canonical.com>[/EMAIL]
Subject: Re: Thoughts about EXT4 optional in Jaunty Development &
	questions	about Plymouth
To: ubuntu-devel-discuss Dev [EMAIL="ubuntu-devel-discuss@lists.ubuntu.com"]<ubuntu-devel-discuss@lists.ubuntu.com>[/EMAIL]
Message-ID: [EMAIL="355b967ee3bbb41cb9997ac65cc2e063@canonical.com"]<355b967ee3bbb41cb9997ac65cc2e063@canonical.com>[/EMAIL]
Content-Type: text/plain; charset="us-ascii"

On Nov 24, 2008, at 12:07 AM, Dean Loros wrote:
[INDENT]> ...
> There has been talk in the testing group about Plymouth & possible
> replacement of Usplash...IMO Plymouth provides a better user experience
> due to a "more" seamless blending of Grub, Kernel boot & GDM. I realize
> that there could be "issues" with this, but it could also net a more
> positive user experience .
> ...
[/INDENT]
Plymouth is scheduled for discussion at the Ubuntu Developer Summit two 
weeks from now. 
[<https://blueprints.launchpad.net/ubuntu/+spec/plymouth>]("https://blueprints.launchpad.net/ubuntu/+spec/plymouth")

Cheers
-- 
Matthew Paul Thomas

---

### Post by Jay_Bee on 2008-11-26
I watched the video on Phoronix and I am a little disappointed that there is no smooth fading between Plymouth and GDM.
GDM just jumps out... I guess GDM should be updated as well.

---

### Post by olskar on 2008-11-26
> **Jay_Bee said:**
> I watched the video on Phoronix and I am a little disappointed that there is no smooth fading between Plymouth and GDM.
GDM just jumps out... I guess GDM should be updated as well.

I think it has been improved since the video on Phoronix

---

### Post by Jay_Bee on 2008-11-26
They have a new one from the final version:
[http://www.phoronix.com/scan.php?page=news_item&px=Njg3Nw](http://www.phoronix.com/scan.php?page=news_item&px=Njg3Nw)
That's the one I am talking about

---

### Post by MacUntu on 2008-11-26
Yup, there is room for improvement but still better than Usplash.

---

### Post by klange on 2008-11-26
> **Jay_Bee said:**
> I watched the video on Phoronix and I am a little disappointed that there is no smooth fading between Plymouth and GDM.
GDM just jumps out... I guess GDM should be updated as well.

Then you're watching an old video, they have one with a nice fade (the graphics buffer and context is maintained between Plymouth and X/GDM, so a number of effects, in theory, be used)

**e**: I just watched the video you linked to, and I have no idea what you're talking about. The transition is very smooth, with just a slight technical glitch with the actual login box (notice that everything else fades in perfectly).

---

### Post by amano on 2008-11-26
The only thing that would make Plymouth interesting for me would be the ability to manually switch to a text mode with the boot messages. That works with splashy. But does that work with Plymouth?

---

### Post by klange on 2008-11-26
> **amano said:**
> The only thing that would make Plymouth interesting for me would be the ability to manually switch to a text mode with the boot messages. That works with splashy. But does that work with Plymouth?
Short answer: Yes.

---

### Post by Jay_Bee on 2008-11-26
> **WindowsSucks said:**
> 
The transition is very smooth, with just a slight technical glitch with the actual login box (notice that everything else fades in perfectly).
Yes, I noticed that the background fades, I was indeed referring to the login box, that pop-out kind of ruins the whole thing for me, but it will hopefully get better over time.

---

### Post by Slug71 on 2008-11-27
> **Jay_Bee said:**
> Yes, I noticed that the background fades, I was indeed referring to the login box, that pop-out kind of ruins the whole thing for me, but it will hopefully get better over time.

I'm sure it will get better, in fact almost positive it will since it is still very much in development.

---

### Post by klange on 2008-11-27
> **Jay_Bee said:**
> Yes, I noticed that the background fades, I was indeed referring to the login box, that pop-out kind of ruins the whole thing for me, but it will hopefully get better over time.
I'm pretty sure that's a GDM bug anyway. And I don't think it would affect our default GDM themes simply because of how we do things. Can't say for sure, haven't tried it.

---

### Post by MadsRH on 2008-11-27
> **WindowsSucks said:**
> I'm pretty sure that's a GDM bug anyway. And I don't think it would affect our default GDM themes simply because of how we do things. Can't say for sure, haven't tried it.

Well, hopefully the GDM will be replaced with the [face-browser or Login Experience]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html") as it's called now.

Info about Login Experience here: [http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html")


;-)

---

### Post by Slug71 on 2008-11-27
> **MadsRH said:**
> Well, hopefully the GDM will be replaced with the [face-browser or Login Experience]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html") as it's called now.

Info about Login Experience here: [http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html")


;-)

Dude, that is just freaking cool!! :guitar:

I'd create user accounts for people i don't even know just so that i could play around with it. :lolflag:

---

### Post by gjoellee on 2008-11-27
Finally something modern comes to Linux for about a year or something!

---

### Post by plun on 2008-11-27
> **MadsRH said:**
> Well, hopefully the GDM will be replaced with the [face-browser or Login Experience]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html") as it's called now.

Info about Login Experience here: [http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html]("http://anotherubuntu.blogspot.com/2008/11/gdm-login-experience.html")


;-)

Yup... for me Plymouth is a non important function if our devs also can cut boot time.
GDM is more important.

But no boots such as with Intrepid where you can see nosplash events in the beginning...  Windows solved that 1994...

---

### Post by ktp on 2008-11-27
I would also say GDM is more important.

---

### Post by klange on 2008-11-27
Why does it seem like everyone has this mindset that if we're working on X, we're not working on Y, and in order to work on Y we need to stop working on X?
Most of the developers who work on one project wouldn't be working another project if they weren't working on the first one. Plymouth is a great example.

---

### Post by Starks on 2008-11-28
I eagerly await the release of the Y Window System. </sarcasm>

---

### Post by MadsRH on 2008-11-28
> **WindowsSucks said:**
> Why does it seem like everyone has this mindset that if we're working on X, we're not working on Y, and in order to work on Y we need to stop working on X?
Most of the developers who work on one project wouldn't be working another project if they weren't working on the first one. Plymouth is a great example.

+1

Well put ;-)

---

### Post by meastp on 2008-11-28
> **WindowsSucks said:**
> Why does it seem like everyone has this mindset that if we're working on X, we're not working on Y, and in order to work on Y we need to stop working on X?
Most of the developers who work on one project wouldn't be working another project if they weren't working on the first one. Plymouth is a great example.
QFT.

Sadly, some people can't grasp that the world doesn't resolve around their priorities.

---

