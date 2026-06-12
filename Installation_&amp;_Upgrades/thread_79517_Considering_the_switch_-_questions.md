---
title: "Considering the switch - questions"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by BlueNoteMKVI on 2005-10-20
Good morning all.

I'm considering switching some/all of my systems to Kubuntu in the near future.  I have a few questions that I hope the board can answer before I do.

First, some background.  I run a web development and hosting company.  I'm responsible for maintaining two web servers in a remote datacenter, both of which run CentOS.  In my office I have a server that runs nightly backups (running Gentoo),  a nice new AMD64 system (tried Gentoo AMD64, now running Xandros), my Centrino laptop (Gentoo) and my wife's older laptop (Xandros).  I also have a desktop box running Windows for my accounting software.  I've tried Fedora (Core 2 was the current version at the time), RedHat 9 and Mandrake.  Gentoo has been my primary workstation OS for the past year.  All that to say, I'm fairly knowledgeable about maintaining a Linux system.

I love Gentoo's package management, when it works.  I've got to say that my backup server has run smoothly for the last several months, but a Portage upgrade broke the internet connectivity and I had to pull it out to deal with that (normally it runs without a monitor or keyboard).  It was a simple issue of the module not loading properly at boot, removing the box from the closet and connecting peripherals took more time than actually fixing it, but it took a big chunk out of my day.  My laptop has broken several times.  When the hard drive failed it took about three days before I had a useful system again.  However, I have never needed a package that was not in Portage.  Everything is there and the dependency handling has never been an issue.

Gentoo64 was a nightmare.  Probably most of the problems I experienced were common to all Linux distros trying to run on AMD64, but several were Portage-specific.  After spending what should have been a profitable work day reading the Gentoo forums and trying to figure out the latest issue I dumped Gentoo.  After a bit of research into a user-friendly OS that would "just work" I settled on Xandros.  Xandros "just worked" on nearly everything, but it's only 32 bit and can't take advantage of the 64 bit processor (for whatever it's worth).  When my wife got a new laptop I installed Xandros on that and had a similar experience.

Since I got under the hood with Xandros, however, it's been frustrating.  My wife's laptop needs a special driver for the touchpad that requires a kernel recompile.  I know what I'm doing with a kernel (heck, I run Gentoo, I could do it in my sleep) but Xandros makes it difficult.  The kernel sources are not installed by default and the Xandros Networks updater tends to overwrite the things I change.  Basically, once you get out of the box that Xandros has put together, it all goes to pot.  I can install things from other sources (since Xandros is after all Debian based) but XN won't put them into my K menu (minor, but an annoyance nonetheless) and some context menus are not updated properly.  Xandros doesn't want people going outside the Xandros repositories and their user forums are not very helpful.

That was longer than I had planned.

Anyway, questions:

-Package management.  Are there any glaring holes in the Ubuntu repositories?  Is it difficult to add other repositories, can they coexist?  I know that Ubuntu is Debian based, are the repositories based on a particular version of Debian?  Do they roughly correspond to the Debian format of stable/testing/unstable?  How current are the packages?  Most importantly, does it break things?

-User forums.  I've read around a bit in these forums and most people seem knowledgeable and willing to help.  Any opinions on that, as compared to other places?

-64 bit version - what's been your experience?  Does it work well?  I tried the liveCD and everything  looked good, but you can't really tell anything about system admin from that.  Is there any noticeable performance boost?  Has the 64 bit platform matured a bit now so I don't have to manually tweak settings and recompile?

-Any other Gentoo (or ex-Gentoo) users out there who care to share their experiences?

-Going "outside the box" - are kernel sources installed, so I can tweak the configuration if I need to?  Are all needed modules installed in the KDE control panel?

My laptop has a Centrino chipset (IPW2200 b/g), will the wifi "Just Work"(tm) or is it easy to set up?  The reason I went to Gentoo in the first place was the wifi support, at the time the only howto I could find for running the Centrino under Linux was using Gentoo.  I tried Xandros on that laptop, the reason it's back to Gentoo is again the wifi.

Does Ubuntu use devfs or udev?  Anyone out there have a Treo 600, does everything work well with that and Ubuntu?

I will greatly appreciate the answers to any or all of these questions.  Thanks for reading this far down!

---

### Post by stuporglue on 2005-10-20
> 
-Package management.  Are there any glaring holes in the Ubuntu repositories?  Is it difficult to add other repositories, can they coexist?  I know that Ubuntu is Debian based, are the repositories based on a particular version of Debian?  Do they roughly correspond to the Debian format of stable/testing/unstable?  How current are the packages?  Most importantly, does it break things?

Ubuntu's default repos are good, solid, but slightly limited. Enable Universe if you need more software, and possibly Multiverse if you want even more stuff. Packages are very recent, getting frozen at each release, but with backports for security. Pick a release and stick with it for consistance on a server, or upgrade every six months for a desktop.

> -User forums.  I've read around a bit in these forums and most people seem knowledgeable and willing to help.  Any opinions on that, as compared to other places?

These and the Gentoo forums are the only usefull Linux forums I've ever found. Quality of answers depends on the day, who's answering and how obscure the question is. 

> -64 bit version - what's been your experience?  Does it work well?  I tried the liveCD and everything  looked good, but you can't really tell anything about system admin from that.  Is there any noticeable performance boost?  Has the 64 bit platform matured a bit now so I don't have to manually tweak settings and recompile?
Haven't used it, but the LiveCD and Install CD use the same hardware detection, and have the same default installed programs. In most cases you shouldn't have to recompile anything. (Cases being needing a module built into the kernel, proprietary video drivers perhaps, etc.)

> 
-Any other Gentoo (or ex-Gentoo) users out there who care to share their experiences?
I was on Gentoo for about 1.5 years. I just didn't have time to compile anymore, and Ubuntu's defaults were reasonabe, so I'm here. 

> -Going "outside the box" - are kernel sources installed, so I can tweak the configuration if I need to?  Are all needed modules installed in the KDE control panel?

Ubuntu has very strong ties to Debian. If you've never built a Debian kernel before, it's different than the process on Gentoo, but quite doable. I don't use KDE, so I don't know the second part.

---

Other notes... 

Kubuntu is very good and looks better, but I find Ubuntu to seem slightly more mature and have better default settings. You can install them both and test them by installing kubuntu-desktop and ubuntu-desktop. 

Emerge rocks, but Apt rocks too. One thing I like about Apt, is when I go to install a package, it lists "recomended" packages as well. For example going to install "digikam" recomends digikamimageplugins and  kipi-plugins. The recomendations have let me know about important codecs, helper programs or cool plugins that I wouldn't have known about with Emerge.

---

