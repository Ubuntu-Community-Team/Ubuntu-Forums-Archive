---
title: "When will we see the current devel. X server?"
date: 2008-11-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klange on 2008-11-10
One of the biggest updates I'm looking forward to in Jaunty is the newest X server, which currently has DRI2 in a stable implementation on Intel hardware - which, as you may know, means significant improvements to 3d rendering and compositing.

As I've already jumped on the boat for Jaunty (I have a secondary, stable distro in case things break), and noticed no new X server yet, I have to ask: when will it get here?

---

### Post by Mazza558 on 2008-11-10
Alpha 1 perhaps (Nov 20th). Maybe that's too early...

---

### Post by klange on 2008-11-10
> **Mazza558 said:**
> Alpha 1 perhaps (Nov 20th). Maybe that's too early...
I'd say the earlier we get it in for testing, the better. My sources tell me it's quite stable and should do fine, plus it's better to risk breaking things now than when everyone has jumped on during the Alpha.

---

### Post by BwackNinja on 2008-11-10
You also have to wait for the 2.6.28 kernel to show up in ubuntu and hopefully that happens so so we can make the transition to 2.6.29 sometime later.

---

### Post by Slug71 on 2008-11-10
> **BwackNinja said:**
> You also have to wait for the 2.6.28 kernel to show up in ubuntu and hopefully that happens so so we can make the transition to 2.6.29 sometime later.

Im hoping 2.6.28 will be in Alpha 1.

---

### Post by Eclipse. on 2008-11-11
> **Slug71 said:**
> Im hoping 2.6.28 will be in Alpha 1.

If the kernel devs are going to plan on releasing Jaunty with .29 kernel the stock intrepid kernel will be used until its available.

---

### Post by tepsipakki on 2008-11-11
there are no releases that are interesting, so I doubt we'd get some random git snapshot of master, which happens to contain MPX etc (which won't get in 1.6). Once there's a 1.6 prerelease we will look into it.

---

### Post by autocrosser on 2008-11-11
Thank you for the information.

---

### Post by klange on 2008-11-12
> **tepsipakki said:**
> there are no releases that are interesting, so I doubt we'd get some random git snapshot of master, which happens to contain MPX etc (which won't get in 1.6). Once there's a 1.6 prerelease we will look into it.

XInput2 was pushed back again? Not that it was on my personal list... (I'm more interested in DRI2/GEM, which *will* be in 1.6)

---

### Post by ShirishAg75 on 2008-11-12
> **tepsipakki said:**
> there are no releases that are interesting, so I doubt we'd get some random git snapshot of master, which happens to contain MPX etc (which won't get in 1.6). Once there's a 1.6 prerelease we will look into it.

It would have been nice to have some dates defined but cool. As of right now, I have 1.5.2 

```


$ X -version

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Mugglewille-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present

```

---

### Post by tepsipakki on 2008-11-12
> **WindowsSucks said:**
> XInput2 was pushed back again? Not that it was on my personal list... (I'm more interested in DRI2/GEM, which *will* be in 1.6)

1.6 will focus on GEM/KMS/XI1.5 and then 1.7 should include MPX/XI2 etc (for X11 R7.5). Keith Packard from Intel will be the release manager for 1.6, and he said that within a week or two 1.6 should be branched and final release hopefully in December (with a couple of prereleases before that).

---

### Post by Mr. Picklesworth on 2008-11-12
Thanks for the information, tepsipakki. Great!

I, on the other hand, dream of XInput 2. Hopefully that will roll out at the same time as a new input device config tool and with an MPX-supporting Mango Lassi following days later. In a sense, the anticipation is worth it.

DRI2 could shape up quite well. If it gets Intel and others who have decent Linux graphics drivers another step above NVidia -- this time in a way people see in benchmarks -- those lazy cowards may grow some common sense and stop doing such a hack job. (Maybe pull out the resources that are making completely unstable driver releases on a weekly basis for Windows, and put them into building stable drivers that work as graphics drivers are meant to -- that being rendering graphics properly for the platform at hand, not enhancing specific applications at the expense of others).

---

### Post by dudude on 2008-11-12
Will the DRI2 stuff only benefit people with Intel graphics adapters, or will it have any benefit for ATI/Nvidia users as well?

It would be nice to not have my wine applications spaz out every time I try to use the desktop cube.

---

### Post by PmDematagoda on 2008-11-12
> **dudude said:**
> Will the DRI2 stuff only benefit people with Intel graphics adapters, or will it have any benefit for ATI/Nvidia users as well?

It would be nice to not have my wine applications spaz out every time I try to use the desktop cube.

DRI2 support is [coming]("http://jglisse.livejournal.com/1486.html") for the ati driver, so yes, it can benefit ATi users as well. Not sure about Nvidia, unless nouveau implements it.

---

### Post by RAOF on 2008-11-12
> **dudude said:**
> Will the DRI2 stuff only benefit people with Intel graphics adapters, or will it have any benefit for ATI/Nvidia users as well?

It would be nice to not have my wine applications spaz out every time I try to use the desktop cube.

Definitely not for nVidia - they don't use the DRI infrastructure anyway, and their stack already supports the sort of things DRI2 allows.

For ATI it'll depend on how the drivers are going; DRI2 requires extensive driver support both in-kernel and in userspace.  I'm unsure how far the ATI-GEM-TTM work is along; I don't really follow the ATI drivers.  There's certainly been substantial work on it, though.

Nouveau is (slowly) growing a memory-manager, which is the prerequisite for all this shiny.  Nouveau's development is much much slower than ATI's, what with the lack of paid developers and all.

---

### Post by gnomeuser on 2008-11-13
> **RAOF said:**
> 
For ATI it'll depend on how the drivers are going; DRI2 requires extensive driver support both in-kernel and in userspace.  I'm unsure how far the ATI-GEM-TTM work is along; I don't really follow the ATI drivers.  There's certainly been substantial work on it, though.

Fedora 10 ships with all this and kms/gem is supported on ATI from r100 till r500 (with r600 coming soon I am lead to believe). ATI is better supported than Intel for this currently.

---

### Post by RAOF on 2008-11-13
> **gnomeuser said:**
> Fedora 10 ships with all this and kms/gem is supported on ATI from r100 till r500 (with r600 coming soon I am lead to believe). ATI is better supported than Intel for this currently.

Cool!  I find that quite surprising; the GEM interface was developed by hackers on the Intel drivers and, unless I'm misunderstanding, is implemented using bits of TTM for ATI and nouveau.  Turn out that cards with actual physical RAM have different needs to no-ram Intel chips.  Who knew? :)

---

### Post by klange on 2008-11-13
Fedora 10 does not have GEM (and even if it did, the X server isn't patched for it). The only extra patches to the 2.6.27 kernel are for KMS on ATI (Intel was bumped back to 11)

---

### Post by gnomeuser on 2008-11-14
> **RAOF said:**
> Cool!  I find that quite surprising; the GEM interface was developed by hackers on the Intel drivers and, unless I'm misunderstanding, is implemented using bits of TTM for ATI and nouveau.  Turn out that cards with actual physical RAM have different needs to no-ram Intel chips.  Who knew? :)

I believe the radeon driver was already being ported to TTM so Dave Airlie appears to have TTM underneath bastardized to have the GEM API. I am fuzzy on the details, but he claims to have support for r100-r500 for it in F10 (I have an r600 card so I am still a bit away from being a cool kid.. happy mistake when I bought the thing I picked the wrong model from the shelf).

---

### Post by gnomeuser on 2008-11-14
> **WindowsSucks said:**
> Fedora 10 does not have GEM (and even if it did, the X server isn't patched for it). The only extra patches to the 2.6.27 kernel are for KMS on ATI (Intel was bumped back to 11)

*cough* [You are wrong](http://koji.fedoraproject.org/koji/buildinfo?buildID=69715)

Please search for GEM.

---

### Post by klange on 2008-11-14
> **gnomeuser said:**
> *cough* [You are wrong](http://koji.fedoraproject.org/koji/buildinfo?buildID=69715)

Please search for GEM.
Then why can't I use it?
(Bare DRI from X 1.5.2 doesn't use GEM)

---

### Post by bash on 2008-11-14
Updates on the schedule for XServer 1.6:

> Back in September when the X developers raided the Edinburgh Zoo for the 2008 X Developers' Summit, Intel's Keith Packard made the rather dramatic announcement that he intended to ship X Server 1.6 and he would step up as the release manager.

This announcement was significant in that it had taken a year to go from X Server 1.4 / X.Org 7.3 to X Server 1.5 / X.Org 7.4 (and there was six months just for a point release), but Keith would throw X Server 1.6 together in just about three months.

Keith's intentions for X Server 1.6 is strictly a time-based release cycle as there are some features not yet in a released version of the X Server that he would like to have available to Intel's customers. X Server 1.6 is scheduled to introduce Predictable Pointer Acceleration, a revised version of DRI2 that hadn't made it in time for X Server 1.5, RandR 1.3 (the Resize and Rotate extension), and X Input 2 or X Input 1.5 with device properties. If X Input 2 is primed for X Server 1.6, this server release will also arrive with Multi-Pointer X support.

Since XDS we haven't heard any more on the schedule of X Server 1.6, but this afternoon Keith Packard had provided an update on the X.Org mailing list. Keith is hoping to branch X Server 1.6 from git master on November 24 and then create an X Server 1.6 Release Candidate 1. Following that, X Server 1.6 Release Candidate 2 is scheduled to ship on December 8 and a third release candidate on the 23rd of December. Around the time period of X Server 1.6 RC3, efforts will turn from new code development to bug fixing. With the current schedule, X Server 1.6.0 would then be released on the 5th of January.

This is just days after the end of 2008, but shouldn't be bad as long as the release schedule is met and the bug blocker list at least semi-cleared. If the original X.Org 7.5 release schedule remains in tact, the release of that with X Server 1.6 or X Server 1.7 will be occur on the first of April.

When it comes to RandR 1.3 support, just minutes after announcing this release schedule, Keith Packard proposed a series of patches (32 in total) that add projective transform support. Discussed recently have also been new properties for RandR 1.3.

Source: [X Server 1.6 Gets A Release Schedule](http://www.phoronix.com/scan.php?page=news_item&px=Njg1Mw) (Phoronix)

---

### Post by autocrosser on 2008-11-17
Just a note: From xorg-request-list--- 

On Fri, Nov 14, 2008 at 01:13:16PM -0800, Keith Packard wrote:
> I volunteered to manage an X server 1.6 release, tentatively scheduled
> for the end of the year (yes, this year, 200:cool:. This release will
> include DRI2 and RandR 1.3 support. I'd like to know how much of the 
> new Xinput stuff will be ready in time.

---

### Post by klange on 2008-11-17
> **autocrosser said:**
> Just a note: From xorg-request-list--- 

On Fri, Nov 14, 2008 at 01:13:16PM -0800, Keith Packard wrote:
> I volunteered to manage an X server 1.6 release, tentatively scheduled
> for the end of the year (yes, this year, 2008 ). This release will
> include DRI2 and RandR 1.3 support. I'd like to know how much of the 
> new Xinput stuff will be ready in time.

The response to which was pretty much "not enough for XI2/MPX".
It would have been a great addition to Jaunty, but I guess we won't be getting it until "Kinky".

At least Intel users get the great advantages of DRI2.

---

### Post by autocrosser on 2008-11-17
At least xorg is picking up the pace--I only hope that the bug count won't follow the same pace :)

We'll see about Kooky Kangaroo :)

---

### Post by BwackNinja on 2008-11-17
> **WindowsSucks said:**
> The response to which was pretty much "not enough for XI2/MPX".
It would have been a great addition to Jaunty, but I guess we won't be getting it until "Kinky".

At least Intel users get the great advantages of DRI2.

Well, judging by the way things are going, ATi opensource driver users are going to be getting DRI2 fairly soon too. I'm so excited :)

---

### Post by klange on 2008-11-17
> **BwackNinja said:**
> Well, judging by the way things are going, ATi opensource driver users are going to be getting DRI2 fairly soon too. I'm so excited :)

While I hope it makes it, I fear it won't be stable enough. It wasn't but a few weeks ago that they had even the simplest of OpenGL apps just starting to shape up (glxgears). But, yes, hopefully ATi gets it, then all three of my machines (Intel, nVidia, ATi) will be able to render OpenGL properly when compositing.

---

### Post by gnomeuser on 2008-11-18
> **BwackNinja said:**
> Well, judging by the way things are going, ATi opensource driver users are going to be getting DRI2 fairly soon too. I'm so excited :)

To quote The Smiths ["How soon is Now"](http://jglisse.livejournal.com/1623.html)

---

### Post by BwackNinja on 2008-11-18
Yup! That's what I was going off of, and why I'm so excited. Its almost here and I'm thinking about testing. Its not yet in a state ready to be included in Jaunty yet though.

---

### Post by gnomeuser on 2008-11-18
> **BwackNinja said:**
> Yup! That's what I was going off of, and why I'm so excited. Its almost here and I'm thinking about testing. Its not yet in a state ready to be included in Jaunty yet though.

We could also go for a Smashing Pumpkins song ["Today"](http://www.botchco.com/agd5f/?p=32)

---

### Post by BwackNinja on 2008-11-18
> **gnomeuser said:**
> We could also go for a Smashing Pumpkins song ["Today"](http://www.botchco.com/agd5f/?p=32)

...wow, a lot has been happening with the opensource radeon drivers recently. Next we're gonna see "oh, don't mind us, we just have r700 3D graphics working using Gallium3D with DRI2 and hardware accelerated video decoding and kernel modesetting works perfectly with all hardware."

(And if even just part of this occurs soon, I'll probably be getting myself an r700 sometime.)

Jeez, I like where this is going and how fast its all coming together, but its like they planned for everything to be nearing completion right about now. Practically EVERYTHING graphics-related and awesome is happening right now.

---

### Post by Progressive on 2008-11-18
As an ATI user, I know exactly what you mean. It isn't just graphics though. EVERYTHING is coming together on linux.

Even Creative just came around and GPL'ed their X-Fi driver. And Adobe decided to give Linux first dibs on 64 bit Flash... yea thats right, even before Windows.

Of course the older goodies like open source java are still paying dividends, and I think linux is going to skyrocket, especially with these new netbooks in our hurting economy which is quickly becoming frugal.

---

### Post by gnomeuser on 2008-11-18
> **BwackNinja said:**
> ...wow, a lot has been happening with the opensource radeon drivers recently. Next we're gonna see "oh, don't mind us, we just have r700 3D graphics working using Gallium3D with DRI2 and hardware accelerated video decoding and kernel modesetting works perfectly with all hardware."

(And if even just part of this occurs soon, I'll probably be getting myself an r700 sometime.)

Jeez, I like where this is going and how fast its all coming together, but its like they planned for everything to be nearing completion right about now. Practically EVERYTHING graphics-related and awesome is happening right now.

Sadly getting all that working on nvidia is likely going to take a while. It's not like nvidia are helping the Nouveau project, and they have declined to support the new X features themselves (as they have their own stuff in their proprietary driver). I would though be very interested in seeing how far we can go down that road in the next 6 months (or roughly for the next generation of distros). The X community has a tendency to surprise me, 6 months ago I would not have believed how far we are along now so I hope that trend continues.

---

### Post by Changturkey on 2008-11-18
> **gnomeuser said:**
> Sadly getting all that working on nvidia is likely going to take a while. It's not like nvidia are helping the Nouveau project, and they have declined to support the new X features themselves (as they have their own stuff in their proprietary driver). I would though be very interested in seeing how far we can go down that road in the next 6 months (or roughly for the next generation of distros). The X community has a tendency to surprise me, 6 months ago I would not have believed how far we are along now so I hope that trend continues.

I think I am a new ATI convert.

---

### Post by RAOF on 2008-11-18
> **gnomeuser said:**
> Sadly getting all that working on nvidia is likely going to take a while. It's not like nvidia are helping the Nouveau project, and they have declined to support the new X features themselves (as they have their own stuff in their proprietary driver). I would though be very interested in seeing how far we can go down that road in the next 6 months (or roughly for the next generation of distros). The X community has a tendency to surprise me, 6 months ago I would not have believed how far we are along now so I hope that trend continues.

Right.  Nvidia's GL stack has been doing what DRI2 allows for quite some time, and TwinView was better than old xrandr.  However the X stack is rapidly maturing to rival (and, in the case of XRandR 1.2, exceed for common uses) nvidia's proprietary solutions.

It'd be nice to think that watching ATI piggy-back on and contribute to this infrastructure work would push nVidia towards opening up.

> **Changturkey said:**
> I think I am a new ATI convert.

This has been quite some time coming.  It's not particularly surprising what a couple of full-time paid developers (and a bunch of volunteers) with access to the relevant documentation can do :).

---

### Post by Progressive on 2008-12-03
Any updates on this?

---

### Post by rbmorse on 2008-12-03
John Bridgeman, the ATI engineer heading up the Open-source support effort, was up on [http://www.phoronix.com]("http://www.phoronix.org") and said the dev teams working under NDA out of (other distributions we shall not name) have prototype accelerated 3D/XV drivers for ATI R600/R700 chipsets at the "mostly working" stage.  Development continues but under NDA at the moment. 

Release of this driver code under an open-source license is contingent upon obtaining clearance from various parties involved (one assumes that some are external to ATI given the way these things get licensed).  

He also hopes to make available certain programming documentation pertaining to the R6XX and R7XX families available, but that may come later as in some cases they are finding that the documentation that would be most helpful to developers does not currently exist and they (the open-source guys) are having to write it as they go along. 

The IP review of the driver code is currently in it's third or fourth iteration and that process continues as this is written. Bridgeman points out it is impossible to know how long the review will take, or whether changes will be required to the prototype driver code before it can be released.  If changes are required he can't forecast how long those will require to implement and whether or not they will require yet another full review (likely) or simple statement of compliance (probably only on crossing "t" and dotting "i" type changes. 

All that being said, he hopes to have something for the Christmas stockings of loyal ATI R6XX and R7XX owners waiting for a full-function (sort of) open driver for the Linux operating system.  No promises.

---

