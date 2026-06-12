---
title: "F11 gets Presto - can we has delta-debs too plz"
date: 2008-11-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DFreeze on 2008-11-21
I just saw an article on [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=Njg2OQ") about some of the new features of Fedora 11. [Presto]("https://fedoraproject.org/wiki/Features/Presto") being one of them, a delta-RPM plugin.

I know this topic has been covered in many a thread or blueprint, but I just wanted to collect the thoughts, (im)possibilities and (im)probabilities here. How far away would such an infrastructure for .deb be, and what would have to be done to get it?

I for one have a hard time justifying that linux is more stable and secure than Windows to the people I installed Linux for, when every update amounts to several MegaBytes of updates. Windows in their memory only sporadically needed updating. How can something be good if it needs so much fixing, they reason. I know that is nowhere near a benchmark, but it is an impression people get. Not to mention what people would think about all that when their only internet connection is dialup or a slow broadband setup.

So, please educate me on this ;-)

---

### Post by Gina on 2008-11-21
XP has been updated for 6 or 7 years - I don't know what Vista is like but suspect it has plenty and I've heard a lot of grumbles about it.  M$ have been in the business for many years and have a big team working on their products and a huge monetary input.  Ubuntu is different - it's relatively young.  

However, having said that, I find Ubuntu more reliable than XP and certainly easier to install and get going.  Having jusst reinstalled both XP and Ubuntu on my P4 machine after I was over enthusiastic with my housekeeping, I have a direct comparison.  Many drivers need installing manually on XP whereas after installing Ubuntu 8.10 from Live CD everything worked straight off.  So... 20 mins installing Ubuntu and it works - over an hour installing XP followed by setting up networking then finding it needed the NIC driver installed manually before I could even connect to the net.  Also, it's essential to install anti-virus software with Windows.  Of course, if you buy a PC with Windows installed on it then the suppliers/manufacturers have spent the time installing the system and all required drivers - plus extra software such as anti-virus and other applications.  

I think you have to compare like with like - take an empty hard drive and an installation CD and get it all working.  Ubuntu may need to go online and download and install the odd driver (though my hardware didn't need it) - raw Windows XP didn't even have a NIC driver.  

Most people running Ubuntu (or other Linux distro) for the first time will most likely have a ready-built Windows system to start with.  If this is fairly new, it will have hundreds of Windows updates already installed.

Personally, I think Ubuntu has already passed Windows in the usability stakes.  But for the most part, I'm preaching to the converted here :lolflag:

---

### Post by Nerd_bloke on 2008-11-21
Here is the brainstorm idea page, links to Launchpad and a lot of comments

[Delta (patch based) updates ]("http://brainstorm.ubuntu.com/idea/13/")

They make a big difference to updating on openSuSE, would be nice to see as standard in Ubuntu.

---

### Post by gnomeuser on 2008-11-21
We could also be looking at this wrong, maybe adding all this to apt is polishing of <waste product featuring similar coloring to the our default theme>. 

There are clean implementations like Conary out there which does all this and more. We could consider a long term plan of switching instead of extending apt for all eternity. As a bonus it already has a lot of the features we want such as the planned move to integrate bazaar with the packaging system, Conary already does something like this, the packaging format is greatly simplified over current offerings (basically each package is represented with a small python script). 

It won't be the last time functionality will be desired to be strapped onto apt, it's certainly not the first. Maybe, just maybe, the short term pain of a switch to a new solution will be worth it in the long term.

---

### Post by Changturkey on 2008-11-21
> **gnomeuser said:**
> We could also be looking at this wrong, maybe adding all this to apt is polishing of <waste product featuring similar coloring to the our default theme>. 

There are clean implementations like Conary out there which does all this and more. We could consider a long term plan of switching instead of extending apt for all eternity. As a bonus it already has a lot of the features we want such as the planned move to integrate bazaar with the packaging system, Conary already does something like this, the packaging format is greatly simplified over current offerings (basically each package is represented with a small python script). 

It won't be the last time functionality will be desired to be strapped onto apt, it's certainly not the first. Maybe, just maybe, the short term pain of a switch to a new solution will be worth it in the long term.

How hard would this switch be?

---

### Post by gnomeuser on 2008-11-21
> **Changturkey said:**
> How hard would this switch be?

you would need to redo all the packages and retrain your packagers to the new syntax. Plus your buildsystem would likely need to be changed. Then comes testing the upgrade for users, definitely not something you would do over just one cycle. I would wager a full 3 cycles from the next LTS would be a good start of implementation, time till then can be prep work such as writing documentation, teaching people about the new format, starting the conversion of packages for a parallel repo.

The mitigating factors would include the fact that we can already pull in a lot of packages from rPath and helping them build their repo of "vanilla" packages makes it easy for us to branch for ubuntu specific change meaning we don't have to start our own seperate branch just use rPath'. They also have good documentation and already supply a packagekit backend for Conary.

The show stopper would be if we insisted on depending on Debian, either Debian would have to change as well or we would have to rebase to rPath. I think the latter is more plausable. 

The interesting idea would be to start this as a cross distro effort, get Fedora and openSUSE to consider it as well. Building a common repo of packages would greatly help us all and still retain the change to brand and patch packages easily (plus pulling patches across distros is dead easy).

---

### Post by Nerd_bloke on 2008-11-21
Trouble is that Red Hat and SuSE both already use RPM which is under the [LSB]("http://www.linuxfoundation.org/en/LSB")
Nothing to stop them saying, "sure come and use RPM like we already do..." 
I don't see their need right now (unlike Ubuntu) to adopt a new package manager.

Debian is a supertanker, its momentum takes a long time to slow down or turn, I don't see them any making any large changes either.

The move to delta updates would be big benefit and could be achieved for now by bolting on top of the current framework. 
A grand integration could still be a long term goal on the horizon; but trying to leapfrog to one now would delay any paydirt for a long, long time.

---

### Post by Slug71 on 2008-11-23
> **Nerd_bloke said:**
> Trouble is that Red Hat and SuSE both already use RPM which is under the [LSB]("http://www.linuxfoundation.org/en/LSB")
Nothing to stop them saying, "sure come and use RPM like we already do..." 
I don't see their need right now (unlike Ubuntu) to adopt a new package manager.

Debian is a supertanker, its momentum takes a long time to slow down or turn, I don't see them any making any large changes either.

The move to delta updates would be big benefit and could be achieved for now by bolting on top of the current framework. 
A grand integration could still be a long term goal on the horizon; but trying to leapfrog to one now would delay any paydirt for a long, long time.



Autopackage is another option. 

I think a collaboration of Autopackage and Conary would be kickass.

---

### Post by Sand Lee on 2008-11-25
This idea has been around for some time...

[Mailing list discussion (2006): Debian delta packages]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-October/021751.html")

[WikiPage: Smaller Updates]("https://wiki.ubuntu.com/SmallerUpdates")

[WikiPage: APT Package Deltas]("https://wiki.ubuntu.com/APTPackageDeltas")

[Debian bug report: xdelta]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=147187")

Blueprints: [apt-sync]("https://blueprints.launchpad.net/ubuntu/+spec/apt-sync"), [smaller-updates]("https://launchpad.net/ubuntu/+spec/smaller-updates"), [succinct]("https://blueprints.launchpad.net/ubuntu/+spec/succinct")

---

### Post by meastp on 2008-11-25
Just a quick note:
When you compare the size of Windows updates, compared to what we have in Ubuntu, remember that Ubuntu updates the *entire* system (software etc.) while Windows only update the OS, mostly.

That said, apt downloading changes only would save some bandwith and time- which is good.

---

### Post by Starks on 2008-12-14
So... Is delta for Debian dead in the water until 2010 at the earliest?

---

### Post by ShirishAg75 on 2008-12-15
wish we could get some sort of input on this one.

---

### Post by ShirishAg75 on 2008-12-18
Hi all, 
 Just an update. Put up a collection of things I could find on the topic at [http://flossexperiences.wordpress.com/2008/12/19/better-package-managementbetter-package-management/](http://flossexperiences.wordpress.com/2008/12/19/better-package-managementbetter-package-management/) . Feel free to comment on the same as well.

---

### Post by vishalrao on 2008-12-27
Looks like Fedora community too have been discussing/wishlisting Presto for many releases (FC6, F7...) and it will be a killer feature IMO especially since some of us have poor broadband speeds and pay-per-MB DSL. Old link: [http://fedoraproject.org/wiki/FWN/Issue97#Presto-digitation](http://fedoraproject.org/wiki/FWN/Issue97#Presto-digitation) I believe openSUSE has this in their update system already?

If we start filing wishlist bugs/brainstorms now, maybe we can see it in Ubuntu in a couple of years :D

I just wish developers see this thread and we get some sort of official word (blog/mailing list post etc) from the devs whether there is even a slim chance of seeing this in Jaunty, or ever... I guess most of the devs live in places where net speeds are fast and cheap :)

---

### Post by gnomeuser on 2008-12-27
> **vishalrao said:**
> Looks like Fedora community too have been discussing/wishlisting Presto for many releases (FC6, F7...) and it will be a killer feature IMO especially since some of us have poor broadband speeds and pay-per-MB DSL. Old link: [http://fedoraproject.org/wiki/FWN/Issue97#Presto-digitation](http://fedoraproject.org/wiki/FWN/Issue97#Presto-digitation) I believe openSUSE has this in their update system already?


Yes, Presto is some what a feature that has been haunting us. We really want it but it was one of those situations where the end user bits were working but we needed the build system to push out deltas. There were some objections to this by mirror handlers (some tended to dislike having to mirror what might amount to hundreds of thousands small files for technical reasons). Now we are pretty confident all the bits are in the correct order and it should land in F11. But this is Free Software and a feature that is done AFAIK entirely without any involvement of full time paid developers, and in an area that involves quite a bit of information on both the rpm format and how the specific build and mirroring system works.. it's ready when it's ready, hopefully this means F11.

openSUSE (and thus SLEx) have hard this for a while, I have played with it some and it works very well. Still not as nice as Conary' way of handling things but it is definitely a step in the right direction and makes a good impact on download size.

---

### Post by plun on 2008-12-27
> **Starks said:**
> So... Is delta for Debian dead in the water until 2010 at the earliest?

Yes.....   also never ending flame wars within mailing lists instead of code work, tons of users with opinions but without knowledge of coding, just "**shitstorms**" :-x

This blog is really interesting from a real user with knowledge...:)

[http://www.kdedevelopers.org/blog/57](http://www.kdedevelopers.org/blog/57)


Another blog about PackageKit talks about the Black & White problems....

[http://www.glatzor.de/blog/blog-details/article/i-dont-want-to-be-prada/?tx_ttnews](http://www.glatzor.de/blog/blog-details/article/i-dont-want-to-be-prada/?tx_ttnews)[backPid]=4&cHash=5281e9e9d1

Burning time on non-issues.....:(

---

### Post by Starks on 2009-03-20
So. No go for delta in Karmic or LL?

---

### Post by NCLI on 2009-03-20
Sounds like it. I don't think we should expect to see any major part of Ubuntu(besides the theme, if you count that) changing this LTS cycle.

---

### Post by inportb on 2009-03-20
Actually, delta-debs are often much slower than normal debs. While they do save bandwidth, they require way more connections. Debian testing versions have traditionally used delta debs because of the frequency of updates, but many people switch to normal debs because they're faster.

---

### Post by deathsshadow77 on 2009-03-20
> **DFreeze said:**
> I for one have a hard time justifying that linux is more stable and secure than Windows to the people I installed Linux for, when every update amounts to several MegaBytes of updates. Windows in their memory only sporadically needed updating. How can something be good if it needs so much fixing, they reason.

I totally disagree. The way I see it, the more the updates the better. In my opinion it means the security issues are being addressed immediately.

In the case of Windows, sporadic updates have definitely worked out great, right? ;)

Also a feature like this sounds great

---

### Post by gnomeuser on 2009-03-20
> **plun said:**
> Yes.....   also never ending flame wars within mailing lists instead of code work, tons of users with opinions but without knowledge of coding, just "**shitstorms**" :-x

This blog is really interesting from a real user with knowledge...:)

[http://www.kdedevelopers.org/blog/57](http://www.kdedevelopers.org/blog/57)


Another blog about PackageKit talks about the Black & White problems....

[http://www.glatzor.de/blog/blog-details/article/i-dont-want-to-be-prada/?tx_ttnews](http://www.glatzor.de/blog/blog-details/article/i-dont-want-to-be-prada/?tx_ttnews)[backPid]=4&cHash=5281e9e9d1

Burning time on non-issues.....:(

Because asking users questions during install is so sane?

Really I thought the world had progressed to selecting good defaults by now but apparently not Debian. 

So Ubuntu officially moved away from PackageKit, and reinvented the wheel to support their desire to avoid picking defaults and worrying users.

---

### Post by andrewsomething on 2009-03-20
> **gnomeuser said:**
> Because asking users questions during install is so sane?

Really I thought the world had progressed to selecting good defaults by now but apparently not Debian. 

So Ubuntu officially moved away from PackageKit, and reinvented the wheel to support their desire to avoid picking defaults and worrying users.

I'm not really sure how this is relevant to the discussion. Maybe I missed something. Anyways...

I my experience, the only time I need to deal with debconf asking me questions is when a config file is going to be over written. Sometimes files that would be very bad for my local configuration if they were over written to the packager's (no matter how sane for most systems) default. How does PackageKit handle such situations?

---

### Post by gnomeuser on 2009-03-21
> **andrewsomething said:**
> I'm not really sure how this is relevant to the discussion. Maybe I missed something. Anyways...

I my experience, the only time I need to deal with debconf asking me questions is when a config file is going to be over written. Sometimes files that would be very bad for my local configuration if they were over written to the packager's (no matter how sane for most systems) default. How does PackageKit handle such situations?

When I installed Jaunty Alpha 4 and upgraded one of the upgrades was to glibc. This invokes debconf, in the middle of the install. The purpose was apparently to ask if I wanted to upgrade libc and to restart services. My point is that doing this is counterproductive, if anyone who doesn't know what the implications are is asked this we have the following two outcomes:

1) update is not applied out of fear which has bad security implications
2) update is applied by meaningless yes clicking behaviour.

1 is truly terrible and will likely prevent future updates as well meaning the user will either be asked this repeatedly till he joins the 2 crowd or any future updates that depends on this will be ignored.

2 can lead to all sorts of bad behaviour long term, just clicking yes every time the computer asks something. Kinda like that security system in Vista really. This also is bad for security, we should ask as few questions as possible. Aside this if the expectation is for 99% of all people to click yes, why not just pick good defaults it will accomplice the same without the delay, confusion and likely long term bad outcomes.

Now if one insists on continuing this insane foot shooting exercise to cater to a few highly technical users who will need this, PackageKit does allow for such questions to be asked before the transaction is begun. Thus one could add metadata to ask many such things before I imagine, or a patch could be produced to add the functionality in the debian copy of packagekit to do it during the transaction even if that would never go upstream.

I just fail to see any reason why this would be a good idea, we have the tools to protect config files and we can do a post install merge if we need to but this is still going down a path where most mortals would fear to tread.

Regardless the point was more to point out the obvious strangeness of pluns posting

---

