---
title: "Openoffice.org 3.0 when in Jaunty?"
date: 2008-11-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-11-16
Hi all, 
 Any idea when Openoffice 3.0 (or 3.1) be merged in Jaunty. 

On another note,  just got a mail which says that the jaunty alpha 1 would be next week.

---

### Post by andrewabc on 2008-11-16
Dunno, but I hope OOo3.1 is released on schedule and put into Jaunty.
[http://wiki.services.openoffice.org/wiki/OOoRelease31](http://wiki.services.openoffice.org/wiki/OOoRelease31)

[3.0.1](http://wiki.services.openoffice.org/wiki/OOoRelease301) should definitely be in it since it is supposed to be released before the new year.

---

### Post by calc on 2008-11-16
> **ShirishAg75 said:**
> Hi all, 
 Any idea when Openoffice 3.0 (or 3.1) be merged in Jaunty. 

On another note,  just got a mail which says that the jaunty alpha 1 would be next week.

Hopefully later this week, I will have to file a bunch of MIRs to get it built in main. I am planning on getting the split build into Jaunty as well but that may take some time to get working properly.

Also 3.1 will go into Jaunty if I can get a release exception for OpenOffice.org from the technical board and release team. I will be talking to them at UDS in a few weeks.

---

### Post by autocrosser on 2008-11-16
I'm still using Calc's PPA that was for Intrepid--everything still works & I would bet that when 3 really gets into Jaunty that there won't be a upgrade problem.....

The old thread: [http://ubuntuforums.org/showthread.php?t=889093&highlight=open+office](http://ubuntuforums.org/showthread.php?t=889093&highlight=open+office)

Hi Calc!!! I didn't see you post (I was posting :)  )....So, is your old PPA still relevant?

---

### Post by ShirishAg75 on 2008-11-16
I have actually stopped using Calc's PPA for I hope to see OOo 3.0.1 or 3.1 in the main repository and I would be interested in Calc's response to autocrosser's comments as well.

---

### Post by calc on 2008-11-16
> **autocrosser said:**
> I'm still using Calc's PPA that was for Intrepid--everything still works & I would bet that when 3 really gets into Jaunty that there won't be a upgrade problem.....

The old thread: [http://ubuntuforums.org/showthread.php?t=889093&highlight=open+office](http://ubuntuforums.org/showthread.php?t=889093&highlight=open+office)

Hi Calc!!! I didn't see you post (I was posting :)  )....So, is your old PPA still relevant?

It's still the newest debs available at the moment yes. I am planning on updating the packaging and uploading that to Jaunty. I was out of town week before last at OOoCon 2008 then on vacation this past week, so hopefully I can get the MIRs filed and get OOo built soon for Jaunty.

---

### Post by calc on 2008-11-16
> **ShirishAg75 said:**
> I have actually stopped using Calc's PPA for I hope to see OOo 3.0.1 or 3.1 in the main repository and I would be interested in Calc's response to autocrosser's comments as well.

A 3.1 beta won't go into Jaunty unless I get a release exception since it would undoubtedly need to be updated after Jaunty release due to bugs (eg 3.1.1). But 3.0.1 should be in Jaunty not too long after it is released. It is currently scheduled to be released a day before I fly to UDS so if it is actually released on time it might take an extra week before it is uploaded.

---

### Post by autocrosser on 2008-11-16
So, are you going to update the PPA first or just make 3 available thru the normal repositories?

And THANK YOU FOR THE INFORMATION!!!!!! It's very nice to have a dev post here somewhat regularly!!!!!


> **calc said:**
> It's still the newest debs available at the moment yes. I am planning on updating the packaging and uploading that to Jaunty. I was out of town week before last at OOoCon 2008 then on vacation this past week, so hopefully I can get the MIRs filed and get OOo built soon for Jaunty.

---

### Post by olskar on 2008-11-16
This is perhaps slightly offtopic but when can we with Intrepid enjoy OoO3 from backports?

---

### Post by autocrosser on 2008-11-16
You can goto the PPA I referenced a couple of posts above & get the current .debs -- as far as the backports--I defer to calc about that one.......

---

### Post by danf_1979 on 2008-11-16
The problem with calc's PPA is that opening files is so slow! For example, a 3MB ppt could easily take 3 minutes using calc's PPA, but if you install 3.0 available from openoffice.org, same file takes less than 10 seconds to load. Something very odd is happening here :S.

---

### Post by olskar on 2008-11-16
> **danf_1979 said:**
> The problem with calc's PPA is that opening files is so slow! For example, a 3MB ppt could easily take 3 minutes using calc's PPA, but if you install 3.0 available from openoffice.org, same file takes less than 10 seconds to load. Something very odd is happening here :S.

Yes, I made a thread about somewhere.. I wanted to file a bug but I did'nt know where to do it?

---

### Post by midnightflash on 2008-11-16
I'm a bit confused now. I thought not the original OOo is working in Ubuntu, but instead the one by [http://go-oo.org/]("http://go-oo.org/") is taken. And there is no Version 3.0 up by now.

So... what is taking me wrong? :confused:

btw: It's really a good thing to have a so called developer here around!

---

### Post by calc on 2008-11-16
> **danf_1979 said:**
> The problem with calc's PPA is that opening files is so slow! For example, a 3MB ppt could easily take 3 minutes using calc's PPA, but if you install 3.0 available from openoffice.org, same file takes less than 10 seconds to load. Something very odd is happening here :S.

Can you please file a bug, if you haven't already, and attach the file that loads quickly in official openoffice.org but takes a long time in the Ubuntu version?

---

### Post by Slug71 on 2008-12-04
Whats with the delay of OOo-3 for Jaunty?

---

### Post by ShirishAg75 on 2008-12-06
It would be in the repositories most probably come Monday, its been accepted for uploads [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001595.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001595.html) as well as [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001596.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001596.html) . Its right now missing a build dependancy libsaxonb-java, when they will build the build machine would try again.

---

### Post by ShirishAg75 on 2008-12-06
It would be in the repositories most probably come Monday, its been accepted for uploads [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001595.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001595.html) as well as [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001596.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001596.html) . Its right now missing a build dependancy libsaxonb-java, when they will build the build machine would try again.

---

### Post by calc on 2008-12-06
A lot more than just that one package is missing, thats just the first one it hit. I am in the process of getting the packages moved from universe to main so that OOo will build. Hopefully I will be able get the build started by later today so it will be built by tomorrow.

---

### Post by ShirishAg75 on 2008-12-06
Thanx calc, thanx a lot. I am sure lot of people would be mighty pleased with that :)

---

### Post by Gina on 2008-12-06
Yes indeed :)  Thank you very much :)

---

### Post by calc on 2008-12-06
It is now waiting on [bug 305790]("https://bugs.launchpad.net/bugs/305790") to be resolved before it will be able to build. Hopefully this will be taken care of soon.

---

### Post by plun on 2008-12-06
> **calc said:**
> It is now waiting on [bug 305790]("https://bugs.launchpad.net/bugs/305790") to be resolved before it will be able to build. Hopefully this will be taken care of soon.

Well.. that was a tragic bug and I hope the situation is better for Intrepid !

I also really hope that this will be discussed during UDS and hopefully will bring a better upgrades for important apps such as OpenOffice !  (despite of what Debian is doing)

---

### Post by calc on 2008-12-06
> **plun said:**
> Well.. that was a tragic bug and I hope the situation is better for Intrepid !

I also really hope that this will be discussed during UDS and hopefully will bring a better upgrades for important apps such as OpenOffice !  (despite of what Debian is doing)

Oh it won't take too long to be fixed. The person who is working on it though is in meetings with me at FOSSCamp/UDS.

---

### Post by vishalrao on 2008-12-06
OT: I know some of you developer folks blog about it, but I'm eagerly looking forward to some videos of UDS discussions on the Ubuntu Dev Channel on YouTube :D

---

### Post by ShirishAg75 on 2008-12-06
AFAIK, one of the conditions of moving packages from universe to main is the packages should be a strong copyleft license, isn't that true calc?

---

### Post by calc on 2008-12-07
> **ShirishAg75 said:**
> AFAIK, one of the conditions of moving packages from universe to main is the packages should be a strong copyleft license, isn't that true calc?

Yes, but I believe that is true of universe as well? I may need to look up the differences again but I think ones without proper licenses generally go into multiverse instead.

---

### Post by calc on 2008-12-07
> **vishalrao said:**
> OT: I know some of you developer folks blog about it, but I'm eagerly looking forward to some videos of UDS discussions on the Ubuntu Dev Channel on YouTube :D

I saw the guy working on the video a few days ago doing a test run to make sure the video equipment would be working, so I assume there will be video posted once UDS starts on Monday.

---

### Post by ShirishAg75 on 2008-12-07
> **plun said:**
> Well.. that was a tragic bug and I hope the situation is better for Intrepid !

I also really hope that this will be discussed during UDS and hopefully will bring a better upgrades for important apps such as OpenOffice !  (despite of what Debian is doing)

Could you elaborate on " despite of what Debian is doing" . I thought the only thing Debian is doing is its in freeze for lenny, other than that don't know anything that Debian is doing which is awful.

---

### Post by Slug71 on 2008-12-29
May as well skip 3.0 now and go right for 3.0.1 since it will be out in about 3 weeks.

---

### Post by jbernardo on 2009-01-05
For me the problem now with openoffice is that openoffice.org-kde is broken. I have to remove it to be able to use OOo 3.0 under kubuntu, or it will always crash claiming it is trying to recover some document.
I tried building it myself, but the build deps include almost 1Gb of mono packages, and I don't want that on my machine (don't have space for it, anyway).

---

### Post by directhex on 2009-01-05
> **jbernardo said:**
> For me the problem now with openoffice is that openoffice.org-kde is broken. I have to remove it to be able to use OOo 3.0 under kubuntu, or it will always crash claiming it is trying to recover some document.
I tried building it myself, but the build deps include almost 1Gb of mono packages, and I don't want that on my machine (don't have space for it, anyway).

1 GiB of Mono packages? Really? How odd, because every single Mono package in the archive comes to a fraction of that.

And I'd say the bigger issue was the 10 GiB of space needed for the actual compile

---

### Post by jbernardo on 2009-01-05
> **directhex said:**
> 1 GiB of Mono packages? Really? How odd, because every single Mono package in the archive comes to a fraction of that.

And I'd say the bigger issue was the 10 GiB of space needed for the actual compile


Well, the calculated total by apt of space occupied after install by the build dependencies for openoffice.org-kde was somewhere around 950Mb-1GB, and most of these were mono packages. Possibly they weren't the biggest packages in the dependencies, or possibly it is because I don't have mono or gnome installed on the netbook. But you're right, 10GB for the compile is even a bigger issue. I had hoped building openoffice.org-kde wouldn't mean building the full openoffice.org package.

---

### Post by directhex on 2009-01-05
> **jbernardo said:**
> Well, the calculated total by apt of space occupied after install by the build dependencies for openoffice.org-kde was somewhere around 950Mb-1GB, and most of these were mono packages. Possibly they weren't the biggest packages in the dependencies, or possibly it is because I don't have mono or gnome installed on the netbook.

Mono is split into an enormous number of tiny packages with long names, to ensure that only as much Mono as is required for a task need be installed, to prevent bloat. By "not the biggest", you mean "only a few K big each". A complete install of EVERY Mono library (note: OOo doesn't need or install all of them) is less than half the size of, say, the OpenJDK build-dep of OOo (which weighs in at over 100 meg on its own).

> But you're right, 10GB for the compile is even a bigger issue. I had hoped building openoffice.org-kde wouldn't mean building the full openoffice.org package.

You can't "build openoffice.org-kde" - the source package for openoffice.org-kde is the same source package as mozilla-openoffice.org, openoffice.org-impress, ttf-opensymbol, libuno-cli-basetypes1.0-cil, etc - the one "openoffice.org" source package creates loads of binary packages, for assorted different use cases. A bit like Mono, in fact. You only install as much as you want.

---

### Post by xebian on 2009-01-05
You can get the debs from OO directly.  No mono required.

Also, I read evolution is now dependent on mono.  Am guessing it's the integration with evo that's requiring this mono?

---

### Post by directhex on 2009-01-05
> **xebian said:**
> You can get the debs from OO directly.  No mono required.

Installing OOo in Ubuntu also doesn't require Mono. Only building it does, in order to build some of the optional add-ons.

I would STRONGLY caution you against using deb packages from openoffice.org directly - there are significant usability gaps compared to an integrated package provided with your distro, and you may have problems upgrading dist in the future

> Also, I read evolution is now dependent on mono.  Am guessing it's the integration with evo that's requiring this mono?

You read wrong, possibly because you read blogs by lying idiots who shall remain nameless. Evolution has absolutely no Mono dependencies at run or compile time. There exists a Mono binding for it, in a different source package.

The need for Mono in order compile OOo comes from the provision in some optional packages to create macros & plugins using Mono languages - the libuno-cli-*-cil packages and cli-uno-bridge. Whether anybody actually does so, I have no idea, but that's actual cause of the build-dep.

OOo and Evo have no dependencies on Mono. And build-deps are not deps.

---

### Post by ShirishAg75 on 2009-01-06
Hi all, 
 As of right now, openoffice.org 3.0.0-6ubuntu1 builds are trying to get their foot in the door. Have a look at [https://launchpad.net/ubuntu/+builds?build_text=&build_state=building](https://launchpad.net/ubuntu/+builds?build_text=&build_state=building)

---

### Post by int on 2009-01-06
OpenOffice.org 3.0.1 RC1

---

### Post by directhex on 2009-01-06
> **ShirishAg75 said:**
> Hi all, 
 As of right now, openoffice.org 3.0.0-6ubuntu1 builds are trying to get their foot in the door. Have a look at [https://launchpad.net/ubuntu/+builds?build_text=&build_state=building](https://launchpad.net/ubuntu/+builds?build_text=&build_state=building)

Status:  	 Dependency wait 


E: Package libstlport4.6-dev has no installation candidate

---

### Post by Slug71 on 2009-01-09
It almost seems like we might not have OOo3/3.0.1 by Alpha 3. Still some days left though.

---

### Post by directhex on 2009-01-09
> **Slug71 said:**
> It almost seems like we might not have OOo3/3.0.1 by Alpha 3. Still some days left though.

[15:06] <calc> pitti: i'll get the new OOo build uploaded in a few hours, i have to test then it takes around 1.5-2 hr to upload due to my 512kbps upload rate

---

### Post by ShirishAg75 on 2009-01-09
[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002840.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002840.html)

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002841.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002841.html)

for your convenience.

---

### Post by Slug71 on 2009-01-09
Looks like we can expect 3.0.1 soon then. :)

---

### Post by andrewabc on 2009-01-09
Lets assume that 3.1 miraculously gets released on March 26. Beta release of Jaunty is around the same time. Would it make it in?

I know if it is much later than jaunty beta then don't expect it, but just wondering about it :D

I'm guessing they will update release date for 3.1 once 3.0.1 is released.

Sad to see bugs in openoffice open since 2005 not fixed.
[Cell notes do not move when cells are sorted in Calc](http://www.openoffice.org/issues/show_bug.cgi?id=59745) is one that affects me and makes notes almost useless with my spreadsheets with OOo. Supposed to be fixed for 3.1, so hopefully 3.1 makes it into jaunty :D

---

### Post by ShirishAg75 on 2009-01-09
In case if it does happen, then somebody may have to file feature-freeze exception. 

The other way/option would be to have backports open and give a request when it gets released in jaunty+1.

---

### Post by Slug71 on 2009-01-09
> **ShirishAg75 said:**
> In case if it does happen, then somebody may have to file feature-freeze exception. 

The other way/option would be to have backports open and give a request when it gets released in jaunty+1.

Yep, thats the only way we will see it.

I would only expect it in KK 9.10 though.

---

### Post by ShirishAg75 on 2009-01-10
Trivia. :- Btw I'm sure you know that coincidentally or not, the person who has a PPA of Oo.o his nicname is Calc :)

---

### Post by gnomeuser on 2009-01-10
> **ShirishAg75 said:**
> Trivia. :- Btw I'm sure you know that coincidentally or not, the person who has a PPA of Oo.o his nicname is Calc :)

sssh it's a vast and terrible conspiracy.. like when you fold the dollar bill and see the twin towers burning..

What you say, to much coffee? NEVER!

---

### Post by ShirishAg75 on 2009-01-10
The conspiracy is actually that** you** have > Extra Foam Sugar Free Ubuntu while I have just > 100% Pure Ubuntu evem though I have made more posts than you . (pouts a bit) :(

Btw has anybody got openoffice.org3 yet? Its still negative here :(

---

### Post by taavikko on 2009-01-10
> **ShirishAg75 said:**
> The conspiracy is actually that** you** have  while I have just  evem though I have made more posts than you . (pouts a bit) :(


What's the deal with coffee cups/beans and the funny titles?
[http://ubuntuforums.org/announcement.php?f=48](http://ubuntuforums.org/announcement.php?f=48)

---

### Post by ShirishAg75 on 2009-01-10
taaviko, 
 I know that FAQ. The problem is I like the coffee cup, it looks so rich with the circle and everything, way way better than my coffee cup. 

I know its foolish and all but its human nature I guess (sniffles a bit)

---

### Post by namdung on 2009-01-10
Will OO3 also be available for Hardy Heron? Any possibility of this happening with Hardy 8.04.2 releasing on 22nd Jan? I'm not very keen on using the debs from OO3 website and would rather have the one from go-oo.org with enhancements.

---

### Post by ShirishAg75 on 2009-01-10
I don't think so, you may do a backport request but it would take lot of efforts. 

Just for getting it into jaunty they had to move lot of things into Main. They would have to move those things to main too and all those things would also need an upgrade. 

The most important would be Java and it may or may not break compatibility with other tools which use Java. 

So the way I see it, there are lots of ifs and buts. 

If you want to try it try backporting some of the packages required by openoffice.org using Prevu 

Here's a list of the packages that would need to be moved to Main and I guess all of them would need to be backported. 

[https://bugs.launchpad.net/bugs/305790](https://bugs.launchpad.net/bugs/305790)

---

### Post by jfernyhough on 2009-01-11
> i386 build of openoffice.org 1:3.0.1~rc1-2ubuntu1 in ubuntu jaunty RELEASE
Build started on 2009-01-09 on vernadsky (i386) and finished on 2009-01-09 taking 5 hours 40 minutes — see the log 
And the changes from [https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002840.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002840.html)

Is there a time delay on getting the packages into the repos? (What is the normal time delay?) I can't see the new packages... :( Although the Intrepid builds from Calc's repo work fine in Jaunty (at the moment at least).

---

### Post by ubulette on 2009-01-11
> **jfernyhough said:**
> And the changes from [https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002840.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002840.html)

Is there a time delay on getting the packages into the repos? (What is the normal time delay?) I can't see the new packages... :( Although the Intrepid builds from Calc's repo work fine in Jaunty (at the moment at least).

It is waiting in the [NEW queue]("https://launchpad.net/ubuntu/jaunty/+queue") because the package contains some new debs: openoffice.org-presenter-console, openoffice.org-kab and openoffice.org-pdfimport and some libs.
So, an archive admin has to manually look at those NEW and approve them. Definitely not during a w-e.

---

### Post by jfernyhough on 2009-01-11
Ah, right. Thanks.

---

### Post by andrewabc on 2009-01-11
Using calc's PPA, and using intrepid I just got the update to 3.0.1RC

22 packages
82.3mb download

---

### Post by ShirishAg75 on 2009-01-11
wait for a day or two you get the official packages.

---

### Post by ShirishAg75 on 2009-01-12
Downloading the 3.0.1 from archive as we speak

---

### Post by calc on 2009-01-12
I pushed a new release out for jaunty a couple hours ago 1:3.0.1~rc1-2ubuntu2 with uploads to the ppa for hardy and intrepid as well. It won't build on jaunty until after the mysql 5.0/5.1 mess is resolved but hopefully that will happen by tomorrow.

---

### Post by Foaming Draught on 2009-01-14
Thank you calc.  I should have thanked you earlier.   It can't be easy to upgrade a major, multi-module suite part-way through an alpha phase.  

But it was getting a bit embarrassing that ubuntu was the only leading distro which didn't include OO3.0  ;)

---

### Post by calc on 2009-01-14
> **Foaming Draught said:**
> Thank you calc.  I should have thanked you earlier.   It can't be easy to upgrade a major, multi-module suite part-way through an alpha phase.  

But it was getting a bit embarrassing that ubuntu was the only leading distro which didn't include OO3.0  ;)

Well Ubuntu won't have 3.1 for Jaunty either so it will be back to that again. The OpenOffice.org release timetable just does not work well with ours.

---

### Post by andrewabc on 2009-01-14
> **calc said:**
> Well Ubuntu won't have 3.1 for Jaunty either so it will be back to that again. The OpenOffice.org release timetable just does not work well with ours.

Yes, the wiki says release March 26. But that was put in there back in November. 3.0.1 release was delayed a month or more, so I wouldn't expect 3.1 final until after ubuntu 9.04 release.

As long as you keep the PPA up for when 3.1 is released I'll be happy. Using it for 3.0 was a must for me.

---

### Post by victorche on 2009-01-26
3.0.1 is OUT now... :)
[ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/stable/3.0.1/OOo_3.0.1_LinuxIntel_install_en-US.tar.gz](ftp://sunsite.informatik.rwth-aachen.de/pub/mirror/OpenOffice/stable/3.0.1/OOo_3.0.1_LinuxIntel_install_en-US.tar.gz)

---

### Post by andrewabc on 2009-01-26
I don't see any official announcements.
Not supposed to be released until tomorrow, and they havn't shown this weeks meeting notes yet.
[http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes#Agenda_for_next_meeting](http://wiki.services.openoffice.org/wiki/ReleaseStatus_Minutes#Agenda_for_next_meeting)

EDIT:
I do see some 3.0.1 final releases at various file sites. So it probably will be released officially soon.

---

### Post by Foaming Draught on 2009-01-27
Hitting Help/About tells me that I'm running 3.0.1

---

### Post by merlyn on 2009-01-27
It's definitely there, I upgraded my slightly neglected Jaunty install this afternoon.

Edit:  G'day Foaming Draught, which brings to mind a refreshing Coopers Sparkling Ale would be very nice right about now.

---

### Post by calc on 2009-01-31
OpenOffice.org 3.0.1-1ubuntu1 is now available in Jaunty and for Hardy/Intrepid it is in the openoffice-pkgs ppa. It is fine to report problems about the ppa version in the Launchpad bugtracker as well, just please remember to report them using "Help->Report a Problem". This gathers lots of information which is vital to helping debug issues. Also any documents you have specific problems with please attach to the bug report or if you can narrow down the issue a simple example document is even better.

I will be working on OOo 3.1.0 debs probably starting in late March or early April, and they will be using the split build that Novell has been working on.

Off to catch my flight to Berlin for the Jaunty Sprint.

ttyl

---

### Post by andrewabc on 2009-02-01
I noticed with the version released before the one you just uploaded, when I try to open .wb3 file (corel spreadsheet) it crashes openoffice and starts the autorecovery. Autorecovery freezes and I have to kill OOo.

Although oddly on OOo3.0 on windows it does not crash, but is not able to open the spreadsheet (is there a corel importer tool/filter? I tried some from the list but none worked).

Even more oddly is the MS office 2003 is unable to open the file (opens it blank). Happens with other .wb3 files as well.

I may upload the file later to see if anyone else can open it.

---

### Post by calc on 2009-02-02
> **andrewabc said:**
> I noticed with the version released before the one you just uploaded, when I try to open .wb3 file (corel spreadsheet) it crashes openoffice and starts the autorecovery. Autorecovery freezes and I have to kill OOo.

Although oddly on OOo3.0 on windows it does not crash, but is not able to open the spreadsheet (is there a corel importer tool/filter? I tried some from the list but none worked).

Even more oddly is the MS office 2003 is unable to open the file (opens it blank). Happens with other .wb3 files as well.

I may upload the file later to see if anyone else can open it.

Yes, there is a bug in launchpad about this issue, bug 314147. Feel free to attach your document there as well if you would like. I will be submitting the bug report upstream as soon as I get time.

---

### Post by andrewabc on 2009-02-02
> **calc said:**
> Yes, there is a bug in launchpad about this issue, bug 314147. Feel free to attach your document there as well if you would like. I will be submitting the bug report upstream as soon as I get time.

Thanks I submitted a file there.

EDIT: for those looking the bug is [url=https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/314147]here]

---

