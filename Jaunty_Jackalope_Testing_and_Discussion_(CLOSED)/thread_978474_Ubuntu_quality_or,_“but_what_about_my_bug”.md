---
title: "Ubuntu quality: or, “but what about my bug?”"
date: 2008-11-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by plun on 2008-11-11
[mdz]("https://launchpad.net/~mdz") wrote an interresting aticle about bugs....

[http://mdzlog.wordpress.com/2008/10/29/ubuntu-quality/](http://mdzlog.wordpress.com/2008/10/29/ubuntu-quality/)

> Leading up to the Ubuntu 8.10 release, Ubuntu developers and quality assurance engineers have been very busy sorting bugs, deciding what can and should be fixed for the final release, and what cannot.  They make these decisions by estimating the importance of each bug, identifying whether it is a regression, assessing the risk of potential fixes, and by applying their best judgement.  Developers can then focus their efforts where they are most needed.

On the whole, I think that we do remarkably well at this.  In September, for example, the total number of open bugs in Ubuntu increased by only 70.  This doesn&#8217;t sound like much of an achievement, if not for the fact that in the same time period, 7872 new bug reports were filed.  The remaining 7802, or over 99%, were resolved (some duplicates, some invalid, some fixed, etc.).

The news isn&#8217;t all good, of course.  **There are currently over 46000 open Ubuntu bug reports in Launchpad**.  Even at this impressive rate of throughput, and even if we were to freeze all development and stop accepting new bug reports entirely, I estimate it would take over half a year just to sift through the backlog of reports we have already received.  There is a lot of noise in that data.

When 8.10 is released, as with each previous release, some users will be disappointed that it has a bug which affects them.  This is regrettable, and I feel badly for affected users each time that I read about this, but it is unlikely to ever change.  There will never be a release of Ubuntu which is entirely free of bugs, and every non-trivial bug is important to someone.

So, what do we do?  What should be our key goals where quality is concerned?  We don&#8217;t currently have a clear statement of this, but here&#8217;s a strawman:
[B]
Prioritize bug[/B] reports effectively.  It&#8217;s usually difficult to say whether a bug report is valid or serious until a human has reviewed it, so this means having enough people to review and acknowledge incoming bug reports, and helping them to work as efficiently as possible.  The Ubuntu bug squad is a focal point for this type of work, though a great deal of this is done by developers in their everyday work as well.  Projects like 5-a-day are a good way to get started.

**Measure **our performance objectively.  By tracking metrics for each part of the quality assurance process, we can understand where we need to improve.  The QA team has been developing tools, such as the package status pages, to collect hard data on bugs.

**Improve incrementally**.  By minimizing regressions from one release to the next, and making some progress on old bugs, we can hope to make each Ubuntu release better, in terms of overall quality, than the one before it (or at least no worse).  The regression tracker (which will hopefully move to the QA site soon) will help to coordinate this effort.

**Ensure **that the most serious bugs are identified and fixed early.  It&#8217;s important to the success of the project that we continue to produce regular releases, and showstopper bugs risk delaying our release dates and adversely affecting the next release cycle.  The release management weather report is one tool which helps monitor this process, though a great deal of coordination is required in order to provide it with useful data.

**Communicate about known bugs**.  It is inevitable that there will be known bugs remaining in each release, and we should do our best to advise our users about them, including any known workarounds.  The Ubuntu 8.10 beta release notes are a good example of this.


Many bug reports are just a "bless this mess" and includes +1 and "also for me" comments......

"Call for testings" must be used more and also with a more active developerw, I also find it meaningless to file a bug if no one answers and its just someone answers which doesn't no anything about it.....

A few developers such as wgrant, fta,  asac and RAOF for example are all closer the community and its just great. :)

They don't need to check it daily just a visit from times to time.

---

### Post by jerrylamos on 2008-11-11
We add our me too on the launchpad bug reports in hopes the developers will see how widespread a bug is.

Case in point, my bug #259385 where Intrepid would not run on my IBM Thinkpad R31.  There was a developers comment it would only affect a few old machines using certain Intel video graphics.  Compiz, on by default, uses a code path not used by any other software freezing the pc solid.

Reported on August 19 still on Intrepid Release Code two months later.  A subsequent update works around the bug by blacklisting compiz from running on some Intel video graphics.  Catch 22, you have to be able to run to get the update that enables you to run.

After Intrepid release searching the Ubuntu forums for on black (or tan, or orange, ...) screen after login you'll get what seems to me to be a significant number of hits, page after page after page.  That's one measure, what about those who try Ubuntu Intrepid CD Live on many IBM, Dell, HP, ... pc's, it doesn't boot and give up on Ubuntu without knowing about Ubuntu forums.  

The ones who are really screwed are those who use Ubuntu's recommended upgrade method now their pc doesn't run at all. Ubuntu doesn't have a "downgrade" path so they either have to give up on Ubuntu or re-install a previous release.  

Boot in rescue mode, apt-get remove compiz compiz-core then Intrepid runs very well on this Thinkpad.

On the other hand lots and lots of people including me get the bug where the CD drawer opens and shuts immediately so the user can't get the CD out.  My view, affects a lot a people, but just crude software.  Not nearly as significant as the cases where Ubuntu won't even run.

Being a glutton for punishment I do expect to get hit by early software - Jaunty hasn't wiped out my partitions (yet).

Jerry

---

### Post by Slug71 on 2008-11-11
Maybe 9.10 should just be updated with new Kernel, Gnome and apps like Pidgin, Mono etc with version updates and the rest of the dev cycle be for removing apps that dont get used, removing obsolete stuff and fixing bugs and paying attention to PA? 

Basically just keep 9.10 simple.:confused:

---

### Post by keep-on-smiling on 2008-11-11
Yep - I would agree with that - less of the new features - what we have with Intrepid is fine, but there is a need to reduce the bugs - as well as the long-promised new look.

---

### Post by unoodles on 2008-11-11
I think 9.04 should be a bugfix-only release.
On my system with opensource drivers, whenever I use a 3D application the entire system locks up. And guess what? This bug has been marked "High" priority since feisty. Thats more than 1 year old.
[https://bugs.launchpad.net/ubuntu/hardy/+source/mesa/+bug/120834](https://bugs.launchpad.net/ubuntu/hardy/+source/mesa/+bug/120834)

---

### Post by gnomeuser on 2008-11-11
> **unoodles said:**
> I think 9.04 should be a bugfix-only release.
On my system with opensource drivers, whenever I use a 3D application the entire system locks up. And guess what? This bug has been marked "High" priority since feisty. Thats more than 1 year old.
[https://bugs.launchpad.net/ubuntu/hardy/+source/mesa/+bug/120834](https://bugs.launchpad.net/ubuntu/hardy/+source/mesa/+bug/120834)

Sadly that idea fails on serveral levels in that to fix this bug, we will likely need the new X, we will need the new mesa, the new drivers and naturally the new kernel. Since to fix this we need DRI2, GEM and kernel modesetting. There is no way to fix that bug (and many others) without moving technology forward.

The same argument is often raised with regards to the kernel, shouldn't we take 3 months to just fix bugs, that is never going to happen. Often bugs need rewrites to go away, or developers will treat that 3 month cycle as extended time to work on new features for the next cycle, thus bring instability right back. 

The only way to make this stable is:

1) minimize causes of bugs you cannot do anything about. This means all the blackboxes. No adobe flash, no nvidia/ati proprietary drivers. 

2) make it easy to test and file bugs. Apport goes a long way and keeping every commit done to the development branch tested against regression suites also does wonders (just look at GStreamer, they do integrated testing with each commit to their code and it helps them catch bugs early to the effect that it is very stable while also being a complex codebase that is fast moving).

3) work with upstream always, any change you make to the code yourself is one you have to support. Any change made upstream is a support burden you can share with everyone else. 

The effects of 1 does mean functionality regression which is sad but investments into covering the now very few areas left that need these unfortunate proprietary components is reduced to maybe 3 big ones. Investments in money and development time should be able to cover them quickly, with maybe a year of a few fulltime developers nouveau could probably cover most basic functionality on nvidia e.g. In the meantime these are sources of many bug reports all over the platform and we really need to minimize that harm.

2 has pretty much no ill effects aside the time it takes to set up such integrated testing, but it will pay out over time. Every time a bug is found for which we can make an automated regression test it should be mandated to be added to the suite before the bug can be closed. The positive effects here will not show right away though.

The effects of 3 might lead to slower development, your feature code needs to be reviewed but in the end it will be nicer for the most part and as a bonus you do get a huge advantage in sharing the burden.

Ubuntu is in a unique position, it has many users who are passionate about the platform, there are many willing testers and an active forum for them to exchange experiences. This greatly eases the testing effort. Encouraging qualified users to do testing is hard, I have worked with Free Software QA for years, I know how hard it is to entice users to take actions that might just break their existing setups and there is no better way to get software tested than to actually get it run in loads of standard every day environments. That gets all the typical cases covered in loads of configurations.

Which brings me to the final order of business, gathering data. We really need to start employing Smolt ([www.smolts.org](www.smolts.org)). Gathering data on the hardware combinations gets us some important data to pindown what hardware is the most used and what hardware combinations caused the biggest issues. smolt in combination with kerneloops and apport give us a good platform for detecting which kernels boot for people, what hardware is causing issues thus narrowing down the number of possibilities dramatically. We can do most for that automatically as an opt-in development feature, a little deamon that submits data after each kernel upgrade (and other critical components like X) to show what failures where fixed and what were caused. You could even ask the user to verify once X comes up after a kernel upgrade that all the hardware works as expected, we already have a hardware testing app (which naturally would need to be expanded as test cases grow). We would also benefit greatly from building all the required infrastructure in collaboration with the other major distros, they have the same problems we do and history shows that the best possible solution is the one we work together on.

---

### Post by Slug71 on 2008-11-11
Yeh i dont think 9.04 would be a good choice for all the reasons Gnomeuser gave and Firefox 3.1, OOo 3, LSB 4.0 will most likely be there too and hopefully Mono 2.4 and Plymouth. 
The key is to bring it in ASAP and then maybe keep 9.10 simple and concentrate on bug fixing.

---

### Post by plun on 2008-11-11
> **Slug71 said:**
> Yeh i dont think 9.04 would be a good choice for all the reasons Gnomeuser gave and Firefox 3.1, OOo 3, LSB 4.0 will most likely be there too and hopefully Mono 2.4 and Plymouth. 
The key is to bring it in ASAP and then maybe keep 9.10 simple and concentrate on bug fixing.

Ubuntu is NOT Fedora.... simple as that.

---

### Post by eldragon on 2008-11-11
i dont mind new bugs, well, i do, but they are inevitable.

what i cannot believe is the ammount of regressions there are

stuff that just worked, dont. with no explanation: some of those are: suspend, hibernate, backlight dimming, cpu fan control. launchpad is full of those problems, i just wanna stay in intrepid. but when and if i get the time, there is no real progress. or even a move to get things sorted. i will be forced to switch distro. not really a threat, just a sad reflection of how things might end up for many users, if this goes on.

i dont really know how the development process is done, but it did smell like it was not going to be ready one month before the release, this metric is taken from the ammount of complains/bug reports in the II testing subforum. compared to hardys, gutsys or even feisty's releases.

one last thing i can complain about. my laptop is affected by a critical bug that makes it fail to boot any livecd, nor install the system, unless a patch which has already been released and tested is applied to the kernel, and it was done so before the II freeze time, yet there is no way we can convince the ubuntu devs to freakin INCLUDE the patch that fixes the bug that makes a batch of laptops sporting a special device for flash drives and ehternet work. its just frustrating to get them to even listen to your case. im just sad at how careless people can be. especially when all the work has already been done.

so, overall, im really disappointed on how things are being done in the ubuntu camp. and no, i dont feel like im owed anything.

nuff rant.

---

### Post by Kevbert on 2008-11-11
A bit of both. Some things that used to work, no longer work. Examples of this are bluetooth (it worked in 7.10 and early 8.04 but no longer works properly in 8.04.1, 8.10+), Floppy disk access (fine in 8.04, not in 8.10+), and accessing other drives (fine in 8.04, not in 8.10+). It's nice having new features/applications, but surely the basics should work first, before adding to them.

---

### Post by gnomeuser on 2008-11-11
> **Slug71 said:**
> Yeh i dont think 9.04 would be a good choice for all the reasons Gnomeuser gave and Firefox 3.1, OOo 3, LSB 4.0 will most likely be there too and hopefully Mono 2.4 and Plymouth. 
The key is to bring it in ASAP and then maybe keep 9.10 simple and concentrate on bug fixing.

My point was more that a bugfixing only cycle is not likely to work. Especially since when the floodgates open again you then have 12 months worth of new changes to come in a ruin your otherwise happy day meaning you are back to square one. Andrew Morton has written some good stuff on the subject of bugfix only cycles I suggest you go back and search for them.

If you want a "true bugfix only" thing you really need to branch off a release of Ubuntu and hammer on it for say 2 years, carefully backporting only selected fixes. But this is a lot of work and is in the end basically what Red Hat does with their Red Hat Enterprise Linux products. Canonical does not have manpower to do this. If you want this on your desktop for free, CentOS is a free rebuild of RHEL, so it's not like you can't have it.

RHEL follows a cycle of 7 year support for each release with updates released for security, stability and to add certain new features (on a predictable schedule) and you also get a new version of RHEL about every 2 years to update your platform. This is a very stable product, yet it also gives you the change to get a new tested major release every 2 years to bring the latest features. As CentOS is a recompile of RHEL you can get it at zero cost (though without the award winning Red Hat support). Fedora provides additional packages for CentOS releases and rpmfusion is supplying media codecs. All tested, lovingly like our mothers would have taught us.

---

### Post by eldragon on 2008-11-11
> **gnomeuser said:**
> My point was more that a bugfixing only cycle is not likely to work. Especially since when the floodgates open again you then have 12 months worth of new changes to come in a ruin your otherwise happy day meaning you are back to square one. Andrew Morton has written some good stuff on the subject of bugfix only cycles I suggest you go back and search for them.



you are right. i think the whole 'change lots of things and hope for the best every six monthes' will most likely never be as stable as we expect it to, because when something breaks, the cause of the bug could be anywhere. i guess the rollout distro model seems better. this is why im actually considering jumping to arch. if stuff gets rolled out as it comes out, when something breaks you know where to look at. same happens when there is a small ubuntu update that breaks something, its usually fixed within days. 

the whole intrepid release thing has been nothing but  pain..for many people. (me included) i dont really know what failed. im quite sure it was not the kernel, since i used 2.6.27 under hardy and it worked ok. but there seems to be something rotten under the hood.

---

### Post by Gina on 2008-11-11
My experience with intrepid (or 8.10 as it is now) has been pretty good and a definite improvement on 8.04.  Just a few niggles such as CD/DVD retracting immediately and needing the button pressed to get it out but I'm sufficiently satisfied to be using it full time now.

---

### Post by danf_1979 on 2008-11-12
As most software is developed upstream, then to improve Ubuntu's quality (i.e. less bugs), release cycles should be a bit longer, say 7-8 months. IMO there is no other way. Most of alfa's are only tested by developers and a handful of users, and beta's are also tested by only few people. So 5 months is very little time for so little amount of users and hardware combinations. There are two solutions, which are essentially one and the same: increase man-hour testing. This can be done increasing the release cycle time, or making more people test de alfa/beta software with no increase in the release cycle time. As the second will not happen, the first one should be done.

---

### Post by dawynn on 2008-11-12
I once looked at the bug list from a oldest-bugs first point of view.  The idea was to clear off some stuff that just wasn't valid anymore (like stuff for obsolete releases).  I ran into a whole lot of bug that weren't even bugs!  I kept hitting "wishlist" items.

Would it be possible to push these wishlist items off to a separate area and not count them as bugs?  How would that impact the "bug" count?

To me at least, "Gee, this would be a great feature" is a lot different than "My nVidia card does not work in Intrepid".  The wishlist items have their place, and do need consideration, but they should not be lumped in with the bug lists/counts.

---

### Post by gnomeuser on 2008-11-12
> **dawynn said:**
> I once looked at the bug list from a oldest-bugs first point of view.  The idea was to clear off some stuff that just wasn't valid anymore (like stuff for obsolete releases).  I ran into a whole lot of bug that weren't even bugs!  I kept hitting "wishlist" items.

Would it be possible to push these wishlist items off to a separate area and not count them as bugs?  How would that impact the "bug" count?

There is some merit to separating true bugs from feature requests, bugzilla can do this by adding keywords, I am sure Malone can do the same thing. 

We could also arrange bughunts, pick bugs from versions of Ubuntu that are no longer supported, see if they can be reproduced in the latest version, if not close them. That is an easy task for users to undertake. We can also encourage users to care for their most beloved applications. E.g. I use idle time running through bugs filed against Banshee in Fedora. Ask for relevant debug data, preparing the bug for the maintainer, pushing bugs to upstream when it's not Fedora specific, hunting down patches for known issues and preparing them for packaging. Little things and there are varying levels of difficulty, great starters for people who have a spare saturday to help Free Software and easy to learn.

---

### Post by ShirishAg75 on 2008-11-12
Hi all, 
 For e.g. what do you guys think about this one [lpbug]98955[/lpbug] . Now if one looks at this bug its been over 2 years, now either the bug should have been fixed or the package removed from the Live CD or something, what's the use of a package if it doesn't work . Its part of the base-package 

```

$ aptitude show upstart-logd
Package: upstart-logd
State: installed
Automatically installed: no
Version: 0.3.9-8
Priority: required
Section: base
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 102k
Depends: libc6 (>= 2.4), upstart (= 0.3.9-8)
Description: boot logging daemon
 This package contains the logd daemon used by /sbin/init to log output of jobs started with "console logged" in their
 definitions.

```

---

