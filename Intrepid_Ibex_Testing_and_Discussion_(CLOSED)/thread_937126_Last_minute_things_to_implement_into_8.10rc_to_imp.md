---
title: "Last minute things to implement into 8.10rc to improve usability."
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by yaknowwat on 2008-10-03
i was wondering if any of these if not all were to be implemented in the coming release candidate so that they are available in the final release.

A new theme.  There are tons of new theme ready for 8.10 styles that work wonderfully.

GIMP 2.6.x  the new 2.6 release came out and has many new improvements in it.

Compiz Fusion 0.7.8 instead of the 0.7.7git ( which is a complete development version )  Some of the improvements between 0.7.6 and 0.7.8 were new fewers a rearrangement of things memory leak fixes and optimizations  Of which i can't say how much of that made it to a git release thats over a month older than the 0.7.8 (stable development snapshot).

OpenOffice 3.0 (the release candidate if needed, i know the final keeps getting delays) every other linux distribution is including it so it'd make sense to keep up with them and include it to.


I'd imagine all that would be fairly simple (Since everything is there is as stable if not stabler than the previous version.) to implement into the release and more than likely should be done.  A range of people are kind of bummed these haven't been implemented in the beta release including myself.

---

### Post by olskar on 2008-10-03
> **yaknowwat said:**
> i was wondering if any of these if not all were to be implemented in the coming release candidate so that they are available in the final release.

A new theme.  There are tons of new theme ready for 8.10 styles that work wonderfully.

GIMP 2.6.x  the new 2.6 release came out and has many new improvements in it.

Compiz Fusion 0.7.8 instead of the 0.7.7git ( which is a complete development version )  Some of the improvements between 0.7.6 and 0.7.8 were new fewers a rearrangement of things memory leak fixes and optimizations  Of which i can't say how much of that made it to a git release thats over a month older than the 0.7.8 (stable development snapshot).

OpenOffice 3.0 (the release candidate if needed, i know the final keeps getting delays) every other linux distribution is including it so it'd make sense to keep up with them and include it to.


I'd imagine all that would be fairly simple (Since everything is there is as stable if not stabler than the previous version.) to implement into the release and more than likely should be done.  A range of people are kind of bummed these haven't been implemented in the beta release including myself.


I agree with everything you say but doubt anything of it will happen :(

---

### Post by yaknowwat on 2008-10-03
> **olskar said:**
> I agree with everything you say but doubt anything of it will happen :(
Which would be a shame if it wasn't.
I'd imagine it would be done if enough users came by and said they wanted this implemented. Though yes it would of course annoy the developers but it would in the end be appreciated by all end users even if they don't know it or not.

---

### Post by UbuWu on 2008-10-03
> **yaknowwat said:**
> 
Compiz Fusion 0.7.8 instead of the 0.7.7git

This one might happen:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/273923](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/273923)

---

### Post by UbuWu on 2008-10-03
Gimp 2.6 is also quite likely to get in, openoffice 3 not though.

---

### Post by yaknowwat on 2008-10-03
> **UbuWu said:**
> Gimp 2.6 is also quite likely to get in, openoffice 3 not though.


Ok thanks for the update.

If OpenOffice3 does make its final release on Oct 7 which is the current expected date would it make it ?

Reason having OpenOffice 3 in Ibex now is  that if its not included that will leave Ubuntu behind the curb for approximately 6 months and i don't think a normal user wants to download a 200 MiB or so OpenOffice + Languages Update.

I guess that just leaves the theme at a to be determine state, correct? :)

---

### Post by denzilla on 2008-10-03
As happens with EVERY Ubuntu release, all the really good stuff just misses the deadline by a matter of 2~3 weeks. Could we just please reset the official release date for the next version of Ubuntu by 1 month and be done with this?

---

### Post by yaknowwat on 2008-10-03
> **denzilla said:**
> As happens with EVERY Ubuntu release, all the really good stuff just misses the deadline by a matter of 2~3 weeks. Could we just please reset the official release date for the next version of Ubuntu by 1 month and be done with this?

That would be well worth it for this release.

Though these things really don't need to set back this release as they are fairly simple to do.

---

### Post by Sef on 2008-10-04
> As happens with EVERY Ubuntu release, all the really good stuff just misses the deadline by a matter of 2~3 weeks. Could we just please reset the official release date for the next version of Ubuntu by 1 month and be done with this?Ubuntu is released one month after GNOME is released.

>  If OpenOffice3 does make its final release on Oct 7 which is the current expected date would it make it ?It can be downloaded, if you add this to your sources.list.   This may cause your system to crash, so use it at your own risk.  (Thanks to Nanog for that [post]("http://ubuntuforums.org/showthread.php?t=937258").)

```
#Calc's_open_office_ppa
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by yaknowwat on 2008-10-04
> **Sef said:**
> Ubuntu is released one month after GNOME is released.

It can be downloaded, if you add this to your sources.list.   This may cause your system to crash, so use it at your own risk.  (Thanks to Nanog for that [post]("http://ubuntuforums.org/showthread.php?t=937258").)

```
#Calc's_open_office_ppa
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

I already know its very possible to implement the changes afterwards but its so much better if they are done in main stream for the typical users.

---

### Post by wgrant on 2008-10-04
> **yaknowwat said:**
> I already know its very possible to implement the changes afterwards but its so much better if they are done in main stream for the typical users.

Except for the inevitable enormous heap of regressions and other bugs. We freeze for a reason.

---

### Post by Kow on 2008-10-04
If compiz 0.7.8 can get in I would surely expect gimp 2.6. compiz is nearing the top with regard to regression potential. Gimp... not so much. From my viewpoint, Openoffice 3.0 is out of the question as there are always a load of regressions after a release of this caliber. Also, Openoffice stability is an absolute must as it's probably one of the highest used packages Ubuntu offers.

---

### Post by Nullack on 2008-10-04
> **wgrant said:**
> Except for the inevitable enormous heap of regressions and other bugs. We freeze for a reason.

I agree with William. There needs to be a point in the lifecycle in which bits are frozen, and change management is applied to make sure the user experience is robust. We have it pretty good in Linux land with six month releases - try that with apple or Microsoft :)

---

### Post by olskar on 2008-10-04
> **Nullack said:**
> I agree with William. There needs to be a point in the lifecycle in which bits are frozen, and change management is applied to make sure the user experience is robust. We have it pretty good in Linux land with six month releases - try that with apple or Microsoft :)

That isn't really a fair comparison ;) Windows and Apple change a LOT of things in every release (at least apple :)), of course it is easier to release something every six month if the changes are not so radical

---

### Post by denzilla on 2008-10-04
> **Sef said:**
> Ubuntu is released one month after GNOME is released.

Ubuntu is in sync with Gnome, but out of sync with the rest of the important OSS projects included in Ubuntu. Why not sync with Gnome's .1 or .2 releases to give OOo, Gimp, Pidgin etc. some time to catch up and make it into the final release? I understand the need for feature freezes, schedules etc. but look back at every Ubuntu release and its easy to see a flaw in the current timing. No one is suggesting extending the 6 month cycle for all future Ubuntu releases, just make Jaunty a 7 month cycle and 6 months for every release there after.

---

### Post by yaknowwat on 2008-10-04
> **denzilla said:**
> Ubuntu is in sync with Gnome, but out of sync with the rest of the important OSS projects included in Ubuntu. Why not sync with Gnome's .1 or .2 releases to give OOo, Gimp, Pidgin etc. some time to catch up and make it into the final release? I understand the need for feature freezes, schedules etc. but look back at every Ubuntu release and its easy to see a flaw in the current timing. No one is suggesting extending the 6 month cycle for all future Ubuntu releases, just make Jaunty a 7 month cycle and 6 months for every release there after.

Doing this would be a double edged sword the first time this is done people would be in disappointment due to a change in release schedule for a while then eventual forget it ever happened if the releases are changed to *.05 and *.11 .
Doing this would also give the developers more time to work on the planned rapid bootup times for Jaunty Jackalope since the change would happen now.

---

### Post by plun on 2008-10-04
> **olskar said:**
> That isn't really a fair comparison ;) Windows and Apple change a LOT of things in every release (at least apple :)), of course it is easier to release something every six month if the changes are not so radical

Well ... MS and Apple also have someone which say Yes or No...:D
MS directors are maybe sometimes stupid but its nevertheless progress and
not endless discussions about "nada".

Also that MS and Apple knows what **mainstream wants** and just doing it.

It seems to be a bunch of open source devs which now works with Apples OS...

---

### Post by denzilla on 2008-10-04
> **yaknowwat said:**
> Doing this would be a double edged sword the first time this is done people would be in disappointment due to a change in release schedule for a while then eventual forget it ever happened if the releases are changed to *.05 and *.11 .
Doing this would also give the developers more time to work on the planned rapid bootup times for Jaunty Jackalope since the change would happen now.


I think most would be able to live with a 7 month dev cycle for Jaunty if it helped to ensure the newest versions of Gimp, OOo, Pidgin etc. got included in later releases going forward.

---

### Post by SnappyU on 2008-10-05
Let's leave the ubuntu team to decide what goes in and what waits for next release.

Delaying it by one month may allow some apps to come in, but there will definitely be something that is ready in Dec that can also come in if we further delay it by one more month.  Where do we then draw the line?

As it is, six months dev cycle-release cycle is pretty tight and I'm still warm from the hardy upgrade.

Seeing the issues with graphics and mouse support (btnx will *not* work!), my day machine may stay on running 8.04 while my home machine dual boots WinXP Pro and ubuntu 8.10, mainly running XP.  I'll test 8.10 until it is satisfactory before moving my day machine over to the latest release. :)

---

### Post by Sef on 2008-10-05
> Ubuntu is in sync with Gnome, but out of sync with the rest of the important OSS projects included in Ubuntu. Why not sync with Gnome's .1 or .2 releases to give OOo, Gimp, Pidgin etc. some time to catch up and make it into the final release? I understand the need for feature freezes, schedules etc. but look back at every Ubuntu release and its easy to see a flaw in the current timing. No one is suggesting extending the 6 month cycle for all future Ubuntu releases, just make Jaunty a 7 month cycle and 6 months for every release there after. 		                   		  		  		  		  		 		 			 				

GNOME is released on a 6 month cycle like Ubuntu, only it is released one month before.

---

### Post by Eversmann on 2008-10-05
Maybe backported after OO release. So we won't have to be dealing with personals PPA.

A solution for not having implemented (such an important thing) on release date but not a problem to add it later.

---

### Post by denzilla on 2008-10-05
> **SnappyU said:**
> Let's leave the ubuntu team to decide what goes in and what waits for next release.

Delaying it by one month may allow some apps to come in, but there will definitely be something that is ready in Dec that can also come in if we further delay it by one more month.  Where do we then draw the line?

As it is, six months dev cycle-release cycle is pretty tight and I'm still warm from the hardy upgrade.

Seeing the issues with graphics and mouse support (btnx will *not* work!), my day machine may stay on running 8.04 while my home machine dual boots WinXP Pro and ubuntu 8.10, mainly running XP.  I'll test 8.10 until it is satisfactory before moving my day machine over to the latest release. :)

I've heard that argument made before, but really what else is there that would be considered a "core" app besides, FF, OOo, Pidgin and Gimp? Most everything else is stuff that comes with Gnome other than Compiz, and NM. Anyway, not up too me just trying to offer some constructive input, thats all.

---

### Post by executorvs on 2008-10-05
I would hope at the very least for backports before Jaunty for gimp and Ooffice. I run into two complaints while moving people over to ubuntu constantly 
1.) lack of MSOffice07 file format support
and 
2.) lack of cmyk support in gimp

that being said I see those as two very significant improvements in the current releases. also while many argue that stability is needed for Ooffice because of it's broad use, I would point out that we used FF3beta5 in the last release and more people use it than Ooffice.

don't take this as my complaining. I try and convert anyone I can BECAUSE I think OSS is a better way. Ubuntu has been very good at a simple and polished approach which makes the transition easy and gained my respect through it.

---

### Post by dabl on 2008-10-05
I don't blame the Ubuntu team for choosing NOT to put their release schedule at the mercy of the various third parties' version releases.  How do you win at that game?  There's always one more new version or major bug fix coming down the pike, so a line on the calendar has to be drawn sooner or later no matter what -- might as well draw it at 6 months and be consistent about it.  At least your users will know the game plan.

Two cents' worth.  :)

---

### Post by denzilla on 2008-10-05
I think people here are making more out of what I'm suggesting than what it actually is. Let me clarify a few things:

* I am not suggesting Ubuntu alter its release schedule according to the whims of every peice of software included in the distro.

* I am not saying the Ubuntu dev cycle needs to be longer than 6 months.

* I am not complaining in **any** way shape or form! 

Virtually every previous Ubuntu release has been marred by a core program undergoing a slight delay that places it just outside of feature freeze. IMO, it would better for Ubuntu and the community to give jaunty a 7 month dev cycle in order to re-align the release dates for future Ubuntu releases to better cope with possible delays of core apps like Gimp, OOo, FF, Pidgin, etc. This isn't something that would need to be done with every release, but there is nothing wrong with taking a step back and see how other projects are coming along once in awhile and possibly making an adjustment if it benefits the project as a whole. Yes, there will always be something better just down the road and you can't just keep delaying a release for something else to be included, but for the sake of quality, sometimes a course correction is worthwhile. 

At the risk of angering quite a few people, I will say that none of this would be an issue if the Linux community would deal with a fundamental flaw in its design: dependencies. Some will say dependencies and tightly knitting apps together with the core of the OS is a strength in terms of security but If Ubuntu or any other Linux distro wishes to really go after the mainstream market, repositories and package managers need to go, period. Mainstream users want to be able to download an installer, and use the program, not be locked in to whatever software or driver is available in the repositories. Synaptic does a great job for what its designed to do but its really just placing a clean sheet over a dirty bed. One could even argue that the current situation deters commercial software/hardware vendors from releasing Linux compatible products due to the influx of support issues that would soon follow. You will never get the average user accustomed to the idea of compiling from source, or accepting just the software offered through a repository. 

As shocking as this may be, its often easier for the average user to experience quality OSS on a proprietary OS than it is on its native platform.

---

### Post by executorvs on 2008-10-05
denzilla, 
I agree with the first half and understood those points. I however think you are gravely mistaken about the package manager being a weakness. yes it's flawed at times and doesn't support management of executable tar files and .sh scripts well but that means it's a program needing improvement not that it's a bad idea or even a bad program.

also, synaptic does support many executables without use of a repository, so it's more a point of educating new linux users about linux executables and how they work without repositories. saying let's get rid of package lists and repositories is flawed as all it would do is take away an additional way of doing things.

a package manager offers the side benefit of avoiding duplicate dependencies something windows does not do well. do you really need to have the same DirectX .Dll located 6 places in your OS or does once serve just as well?

---

### Post by denzilla on 2008-10-05
> **executorvs said:**
> denzilla, 
I agree with the first half and understood those points. I however think you are gravely mistaken about the package manager being a weakness. yes it's flawed at times and doesn't support management of executable tar files and .sh scripts well but that means it's a program needing improvement not that it's a bad idea or even a bad program.

also, synaptic does support many executables without use of a repository, so it's more a point of educating new linux users about linux executables and how they work without repositories. saying let's get rid of package lists and repositories is flawed as all it would do is take away an additional way of doing things.

a package manager offers the side benefit of avoiding duplicate dependencies something windows does not do well. do you really need to have the same DirectX .Dll located 6 places in your OS or does once serve just as well?

Don't get me wrong, Windows has plenty of flaws when it comes to the way it handles installation/removal and system file placement so its not that I'm trying to take sides. However, the way programs are installed and removed in Windows is easy for the average joe to comprehend. You DL an installer, run it, it places icons on your desktop and start menu and if you don't want the app, simply go to add/remove and uninstall it. Yes, its not always that simple if the program was poorly designed and leaves garbage files/settings behind, but when its done right it just works for the most part. With Linux, you have .debs, rpms, .tarballs etc. Some are executable some have to be made executable. Some place icons in your menus, others you have to type a command to start. Some apps work in KDE and not in Gnome and vice versa. Choice is great, but whats wrong with common standard of doing things? Again, its not that people couldn't learn the current Linux way of doing things, but honestly I have a hard time convincing people to bother. Linux doesn't have to be Windows to succeed, but there are some principles used in Windows that people are familiar with that could be carried over, built upon and done better in Linux.

Relying on Repos and Synaptic wouldn't be so bad if it was possible to have the latest stable version of an application available without having to use backports and risk potential system instability in using them. When I turn someone onto using OOo 3.0 in Windows then later convince them to try Ibex and its still using 2.4.1 what am I supposed to tell them? Sorry, you'll have to wait another 6 months to enjoy the new features they're using right now in Windows. Same possible scenario with Gimp, Pidgin, Firefox. This is my reasoning for why the current system is flawed.

---

### Post by wgrant on 2008-10-05
> **denzilla said:**
> Relying on Repos and Synaptic wouldn't be so bad if it was possible to have the latest stable version of an application available without having to use backports and risk potential system instability in using them. When I turn someone onto using OOo 3.0 in Windows then later convince them to try Ibex and its still using 2.4.1 what am I supposed to tell them? Sorry, you'll have to wait another 6 months to enjoy the new features they're using right now in Windows. Same possible scenario with Gimp, Pidgin, Firefox. This is my reasoning for why the current system is flawed.

The Ubuntu Backports project is exactly what you are talking about. The reason backports are separate is because of the inherent instability of updating applications like that - it's nothing particularly special about our backports project.

---

### Post by denzilla on 2008-10-05
> **wgrant said:**
> The Ubuntu Backports project is exactly what you are talking about. The reason backports are separate is because of the inherent instability of updating applications like that - it's nothing particularly special about our backports project.

Yes, but I also said the drawback to using backports was the instability factor, which goes toward the point I'm trying to make.

---

### Post by wgrant on 2008-10-05
> **denzilla said:**
> Yes, but I also said the drawback to using backports was the instability factor, which goes toward the point I'm trying to make.

So you are complaining that one cannot, in Ubuntu, stably update applications using backports, so we should do it more officially... even though it would inherit the same instability? You inherently reduce stability by updating applications. I don't see that there's any way to resolve your complaint in any operating system.

---

### Post by danbuter on 2008-10-05
> **Nullack said:**
> I agree with William. There needs to be a point in the lifecycle in which bits are frozen, and change management is applied to make sure the user experience is robust. We have it pretty good in Linux land with six month releases - try that with apple or Microsoft :)

In Windows or Apple, I would just download the new file the day it is available. No dependency on repos required. Repos are good and bad.

---

### Post by danbuter on 2008-10-05
> **denzilla said:**
> 
Virtually every previous Ubuntu release has been marred by a core program undergoing a slight delay that places it just outside of feature freeze. IMO, it would better for Ubuntu and the community to give jaunty a 7 month dev cycle in order to re-align the release dates for future Ubuntu releases to better cope with possible delays of core apps like Gimp, OOo, FF, Pidgin, etc. This isn't something that would need to be done with every release, but there is nothing wrong with taking a step back and see how other projects are coming along once in awhile and possibly making an adjustment if it benefits the project as a whole. Yes, there will always be something better just down the road and you can't just keep delaying a release for something else to be included, but for the sake of quality, sometimes a course correction is worthwhile. 



I REALLY wish they had done this with Hardy, then we would be on schedule now, and Hardy would have been a better long-term release.

---

### Post by denzilla on 2008-10-06
> **wgrant said:**
> So you are complaining that one cannot, in Ubuntu, stably update applications using backports, so we should do it more officially... even though it would inherit the same instability? You inherently reduce stability by updating applications. I don't see that there's any way to resolve your complaint in any operating system.


No thats not what I'm saying and please try not to take my posts as complaints as they're not. This issue with installing\removing and updating apps is a general problem with Linux not specifically Ubuntu. You saying that system stability is compromised by simply updating an application is proof enough (for me at least) that the current system is flawed. Again, not a complaint or trying to stoke flames, but I've never experienced stability issues installing, updating or uninstalling OOo, FF, Pidgin, Gimp, etc. on Windows. Thats what Linux needs to strive for: Not too be like Windows, but as simple as Windows when it comes to app installation and removal. Same goes for drivers.

Anyway, I can already tell some are starting to take this personal, so lets end it here. Nothing I posted was intended to offend the Ubuntu Devs or to criticize their work.

---

### Post by RAOF on 2008-10-06
> **denzilla said:**
> ...
You saying that system stability is compromised by simply updating an application is proof enough (for me at least) that the current system is flawed.
He's not acutally saying that system stability is compromised, he's saying that the stability of the app is potentially compromised.  You can't upgrade a program without the risk of introducing new bugs *in that program*, and things which depend on it.

It's very easy to only install the app that you're after from Backports, and this is the recommended way of using the backports repository.  In that case, you only get possible regressions in the apps that you deliberately upgrade.

> **denzilla said:**
>  Again, not a complaint or trying to stoke flames, but I've never experienced stability issues installing, updating or uninstalling OOo, FF, Pidgin, Gimp, etc. on Windows. Thats what Linux needs to strive for: Not too be like Windows, but as simple as Windows when it comes to app installation and removal. Same goes for drivers.

There are a number of things working against what you want, the most fundamental of which is that Windows apps are (essentially) statically linked to all the libs which aren't absolutely core to Windows.  This has disadvantages, such as disc space, in-memory size, and security updates, and an advantage: ease of installation.  It's generally considered, at least in the linux community, that the advantages of static linking are outweighed by the disadvantages, but it's not practical to dynamically link Windows executables.

As for drivers, this seems a relatively common theme.  One that I just don't get.  We have a superior driver experience to Windows, generally - all the drivers that are available are installed out of the box!  The problem is when you have hardware that doesn't have a driver, and then there's basically nothing you can do, short of writing one yourself.  Our driver experience is pretty all-or-nothing: either it just works, or it won't work no matter how much you fiddle with it.

---

### Post by melalcoolique on 2008-10-06
> **yaknowwat said:**
> 
GIMP 2.6.x  the new 2.6 release came out and has many new improvements in it.

Gimp 2.6.0 has just been accepted:

[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008013.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/008013.html)

---

### Post by UbuWu on 2008-10-06
> **melalcoolique said:**
> Gimp 2.6.0 has just been accepted:


Yes but it won't build before gegl and babl are promoted to main.

---

### Post by nanog on 2008-10-06
The reason to include open office 3 is that for many users 2.4 just does not work. Open office 3 is now approaching enterprise readiness.

---

### Post by olskar on 2008-10-09
And now gimp 2.6.1 is released

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/280898](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/280898)

---

