---
title: "Ubuntu 10.04 Beta 2 ISO Testing"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-04-06
Beta 2, which will be the second last milestone release of the Lucid Lynx development cycle, will be out this Thursday. Like every milestone release, this one will benefit from good community testing coverage.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the release candidate), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. Towards the end of this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

We are in [Beta 2 Freeze]("http://ubuntuforums.org/showthread.php?t=1444195"), and candidate images for Beta 2 are now available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-04-06
One rather nasty bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373)

I wonder if we'll get a rebuild today?

I must be crazy, because I just love iso testing :guitar:

Edit: This one appears to be fixed! Ubuntu's devs do an absolutely outstanding job.

---

### Post by Irihapeti on 2010-04-06
I've already got a "can't boot live CD" bug open. Do I need to post separately to the ISO testing tracker, or is the existing bug already taken into account?

---

### Post by kansasnoob on 2010-04-06
> **Irihapeti said:**
> I've already got a "can't boot live CD" bug open. Do I need to post separately to the ISO testing tracker, or is the existing bug already taken into account?

It would help a lot if you included more info, like a link to the bug report :)

And did that happen with the iso testing build or a previous build?

I don't know how to fix bugs but I know that providing the proper info is crucial to those who can.

---

### Post by Irihapeti on 2010-04-06
> **kansasnoob said:**
> It would help a lot if you included more info, like a link to the bug report :)

And did that happen with the iso testing build or a previous build?

I don't know how to fix bugs but I know that providing the proper info is crucial to those who can.

It's OK, I tested and reported the result. It was less hassle than I anticipated. :)

---

### Post by ranch hand on 2010-04-06
The last 2 ISOs we have tested will not easily allow you to transfer any data from OS to OS on your drive.  I am sure that it is possible to set up some sort of file sharing but I did not try that because it is not what someone that has no/little experience is going to do.

If you are re-installing your OS you need a way to recover the data easily.  This is not there  at all and I am bummed.

I filed a bug on this and when I tried to add them to the report they were deemed "invalid number entries".  Oh well I left comments anyway.

---

### Post by kansasnoob on 2010-04-07
> **ranch hand said:**
> The last 2 ISOs we have tested will not easily allow you to transfer any data from OS to OS on your drive.  I am sure that it is possible to set up some sort of file sharing but I did not try that because it is not what someone that has no/little experience is going to do.

If you are re-installing your OS you need a way to recover the data easily.  This is not there  at all and I am bummed.

I filed a bug on this and when I tried to add them to the report they were deemed "invalid number entries".  Oh well I left comments anyway.

I ran into a bit of that I think. I could normally restore a /home/username folder after installing and all would be well.

Now that's not the case. I must first be certain that the permissions are identical before moving all or part of an old /home/users files to a fresh install.

I also notice (for some time) that Live "persistence" now requires that you create a user w/root privileges. I'm not sure but I think these are security precautions.

---

### Post by ranch hand on 2010-04-07
I am not having any problem with the installed OS, just to make that clear.  Works fine.

The problem is the Live CD.  This is not just an installation and/or trial run tool.  This is the tool that you, as a single booting or dual booting with that Miserable Sucker OS, use as a rescue and repair tool.  Up through 9.10 it works fine for that.

I would hate to advise a noob to boot to the Live CD and attempt to edit and repair a funky grub, of any version, to functionality.  I can see how to scare folks right off with "well first we need to create a new user" and spend 3 pages getting that accomplished before the simple job of, say, updating grub1.98.

On the 9.10 Live CD it would be easier to explain and walk through fixing grub0.97 by installing it on the live session so that the commands for installing it on the MBR do not result in "command unknown" to someone with no experience in CLI (as a noob, even newber than now, I had at least used DOS).

This is rediculus.  All boxes now come with booting from a CD not enabled.  Any one with a little knowledge can get around this crap.  Heck use remastersys and make a Live DVD that will let you really work someones box over.

This is just cutting the legs out from under new users that like to play with their system and make a mistake.  I about wore out my Hardy LiveCD the first couple months using Ubuntu.  Anyone can check the stupid things I did by checking out my posts on these forum.  I do not know where I would be if it were not for the easy functionality of the Live CD.

I better quit this rant.  I believe most folks have gotten the hint that I may be upset about this.  I just remember my problems all too well.

---

### Post by atlee on 2010-04-07
I'm ready for Beta 2 when you are :)

---

### Post by kansasnoob on 2010-04-07
> **ranch hand said:**
> I am not having any problem with the installed OS, just to make that clear.  Works fine.

The problem is the Live CD.  This is not just an installation and/or trial run tool.  This is the tool that you, as a single booting or dual booting with that Miserable Sucker OS, use as a rescue and repair tool.  Up through 9.10 it works fine for that.

I would hate to advise a noob to boot to the Live CD and attempt to edit and repair a funky grub, of any version, to functionality.  I can see how to scare folks right off with "well first we need to create a new user" and spend 3 pages getting that accomplished before the simple job of, say, updating grub1.98.

On the 9.10 Live CD it would be easier to explain and walk through fixing grub0.97 by installing it on the live session so that the commands for installing it on the MBR do not result in "command unknown" to someone with no experience in CLI (as a noob, even newber than now, I had at least used DOS).

This is rediculus.  All boxes now come with booting from a CD not enabled.  Any one with a little knowledge can get around this crap.  Heck use remastersys and make a Live DVD that will let you really work someones box over.

This is just cutting the legs out from under new users that like to play with their system and make a mistake.  I about wore out my Hardy LiveCD the first couple months using Ubuntu.  Anyone can check the stupid things I did by checking out my posts on these forum.  I do not know where I would be if it were not for the easy functionality of the Live CD.

I better quit this rant.  I believe most folks have gotten the hint that I may be upset about this.  I just remember my problems all too well.

I do understand what you're talking about. I first encountered that in early February and started this thread:

[http://ubuntuforums.org/showthread.php?t=1401995](http://ubuntuforums.org/showthread.php?t=1401995)

---

### Post by QLee on 2010-04-07
OK, I've a $.02 to add.

In the first place, this unreleased software should only be used by people who have the ability and experience to troubleshoot problems encountered - that is the bottom line recommendation for alpha; beta; RC.

None of the things that can be done with a live CD as a rescue disk can usually be done by inexperienced users by themselves, and this forum is littered with unsuccessful attempts and unsuccessful attempts to help. Countless cases of people who can't solve problems or even do updates correctly themselves, giving advice to novices. It's the nature of open technical help forums. So, to my mind, having to walk someone through adding a new user as a first step, isn't going to introduce a huge roadblock to assistance. But, I think we should be recommending that novices stick with released versions for the best user experience. In addition, when one does choose to help a novice (it's usually apparent from the dialogue) through a problem, one should take the time to explain their advice better, tell the poster "why", not just "do this , do that" and we should try to leave our "political feelings" out of the text, in my opinion this forum is not the best place to criticise developers' choices or to tout our own personal methods or point-of-view. Focus on the trouble report.

So many of the problems I have observed people posting seem to stem from frustration, frustration of inexperienced users, and also frustration of users who have experience but who are not good troubleshooters, don't follow a logical path but still try to help. Good intentions, but often just confusing people, who are already in over their heads, even more. 

Everyone should read and heed the stickies before they start to work with Lucid at this point in history. It's less than a month to wait for release.

---

### Post by ranch hand on 2010-04-07
> **kansasnoob said:**
> I do understand what you're talking about. I first encountered that in early February and started this thread:

[http://ubuntuforums.org/showthread.php?t=1401995](http://ubuntuforums.org/showthread.php?t=1401995)
Yes and at that time I tried it and had no trouble.  It could be that it was because my test platform is a usb drive.

It is only since B1 that this has been acting this way on those drives for me.

I take it that we are going with the ISO we tested yesterday.  Am I correct?

---

### Post by kansasnoob on 2010-04-07
> I take it that we are going with the ISO we tested yesterday. Am I correct?

I would guess the second one, yes:

[http://iso.qa.ubuntu.com/qatracker/info/3923](http://iso.qa.ubuntu.com/qatracker/info/3923)

The first one had a nasty bug for me:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/556373)

But it appears to be fixed.

---

### Post by ranch hand on 2010-04-07
Oh good.  I am kind of busy today and really did not want to do it again.

---

### Post by kansasnoob on 2010-04-07
> **QLee said:**
> OK, I've a $.02 to add.

In the first place, this unreleased software should only be used by people who have the ability and experience to troubleshoot problems encountered - that is the bottom line recommendation for alpha; beta; RC.

None of the things that can be done with a live CD as a rescue disk can usually be done by inexperienced users by themselves, and this forum is littered with unsuccessful attempts and unsuccessful attempts to help. Countless cases of people who can't solve problems or even do updates correctly themselves, giving advice to novices. It's the nature of open technical help forums. So, to my mind, having to walk someone through adding a new user as a first step, isn't going to introduce a huge roadblock to assistance. But, I think we should be recommending that novices stick with released versions for the best user experience. In addition, when one does choose to help a novice (it's usually apparent from the dialogue) through a problem, one should take the time to explain their advice better, tell the poster "why", not just "do this , do that" and we should try to leave our "political feelings" out of the text, in my opinion this forum is not the best place to criticise developers' choices or to tout our own personal methods or point-of-view. Focus on the trouble report.

So many of the problems I have observed people posting seem to stem from frustration, frustration of inexperienced users, and also frustration of users who have experience but who are not good troubleshooters, don't follow a logical path but still try to help. Good intentions, but often just confusing people, who are already in over their heads, even more. 

Everyone should read and heed the stickies before they start to work with Lucid at this point in history. It's less than a month to wait for release.

I don't think anyone would disagree with what you're saying here. For me it's simply a matter of recognizing a "change" in how the Lucid Live CD's handle "saving" or "transferring" data to an installed OS's /home folder.

I actually seldom use that method anyway, I prefer using a persistent Live USB and I haven't tried that with Lucid yet because I don't like to "overwrite" my thumb drives frequently. I'll probably wait for the RC before I change one of my USB sticks to Lucid.

So far I've been testing Live CD persistence just by creating a small "casper-rw" partition on my testing hard drive because "spinning disc" drives are much more durable than thumb drives.

---

### Post by QLee on 2010-04-07
[QUOTE=kansasnoob]I don't think anyone would disagree with what you're saying here.[/QUOTE]
 

Well, if wait long enough someone might. Certainly, many don't exhibit behaviour that supports your contention. <chuckle>

[QUOTE=kansasnoob]For me it's simply a matter of recognizing a "change" in how the Lucid Live CD's handle "saving" or "transferring" data to an installed OS's /home folder.[/QUOTE]

Err, yeah, perhaps you're meaning that automagic stuff that I care little about, I'm showing my bias, eh?

[QUOTE=kansasnoob]...because "spinning disc" drives are much more durable than thumb drives.[/QUOTE]

True, dat! However, flash drives of sufficient size for installing a version of  Ubuntu to test are becoming pretty cheap these days and they wear level better than first generation. Your method is rational, but now someone is likely to ask you, "how do you do that" and it probably will be someone who isn't yet ready to understand your answer and they might even do it in this thread about something else.

---

### Post by ToxicBurn on 2010-04-08
do we have a guood iso yet or are we still testing because its the 8th here well 1am on the 8th haha but still would like to know whats going on if anything this late at night.
 
thanks anything i can do to help im here .

---

### Post by ranch hand on 2010-04-08
It will be announced in a sticky in 15 hours or so (maybe longer).

Try not to get you knickers in a knot.  It will be coming.

---

### Post by tokyobadger on 2010-04-08
@ToxicBurn: that's a fair question, I'm also on April 8th, 14:45 JST but looking at [the official release schedule](https://wiki.ubuntu.com/LucidReleaseSchedule) it states
[quote="Lucid Release Schedule"]Freezes normally happen at the start of the given date, UTC time.[/quote]
Admittedly that's for the freeze not the release, but the schedule does seem to be working on UTC; that said, by my reckoning, it's 05:45 UTC so is it late? Not clear to me. 
[There's a google calendar for the release too, but again, no time specified](https://www.google.com/calendar/hosted/canonical.com/embed?src=canonical.com_38a0dkgrg9rjm36c9sis0mfgog@group.calendar.google.com&ctz=GMT)

@ranch hand: why do you think 15 hours or so for the sticky?

---

### Post by atlee on 2010-04-08
I will test beta 2 when it gets released as a public ISO, maybe i might get this tonight.

---

### Post by ranch hand on 2010-04-08
> **tokyobadger said:**
> @ToxicBurn: that's a fair question, I'm also on April 8th, 14:45 JST but looking at [the official release schedule]("https://wiki.ubuntu.com/LucidReleaseSchedule") it states

Admittedly that's for the freeze not the release, but the schedule does seem to be working on UTC; that said, by my reckoning, it's 05:45 UTC so is it late? Not clear to me. 
[There's a google calendar for the release too, but again, no time specified]("https://www.google.com/calendar/hosted/canonical.com/embed?src=canonical.com_38a0dkgrg9rjm36c9sis0mfgog@group.calendar.google.com&ctz=GMT")

@ranch hand: why do you think 15 hours or so for the sticky?
It is 12:37AM here.  The release is usually late afternoon or evening here.

---

### Post by tokyobadger on 2010-04-08
@ranch hand: fair enough, though the launchpad page for beta 2 states
[quote="launchpad"][url=https://launchpad.net/ubuntu/+milestone/ubuntu-10.04-beta-2]Expected:
6 hours ago[/url][/quote]
/shrugs - I'm new to Ubuntu (not linux), so still getting a feel for how development and the community interact

I'm personally hoping that I don't need the ISO and can just upgrade all the way through, though I'd may test the liveCD aspect and/or repair functionality

---

### Post by kaffemonster on 2010-04-08
Sorry for being daft, but if I grab one of the testing ISO's now - would it be the same ISO as the "official" Beta 2 that will be released later today? Work is unusually slow today so I think a re-install would be in order :D

---

### Post by ikt on 2010-04-08
> **tokyobadger said:**
> I'm personally hoping that I don't need the ISO and can just upgrade all the way through

Yes you can do that.

> **kaffemonster said:**
> Sorry for being daft, but if I grab one of the testing ISO's now - would it be the same ISO as the "official" Beta 2 that will be released later today? Work is unusually slow today so I think a re-install would be in order :D

It may or may not be the same as the beta 2 release, that's the chance you take, however I don't believe there will be a big difference between the two.

---

### Post by ranch hand on 2010-04-08
The main thing about the B2 release is that there will be a Live DVD image released.  If you are using 10.04 now and update you will have B2 on your box.

Do not try downloading until they say it is ready as it will slow down getting the image out to the other mirrors.

If you need an ISO grab the daily and run updates.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Yes I know it is 2 days old.  Not many updates in that time due to the B2 freeze.

---

### Post by ToxicBurn on 2010-04-08
W00t im excited and stuff Bring on Beta 2 :)

---

### Post by kaffemonster on 2010-04-08
> **ToxicBurn said:**
> W00t im excited and stuff Bring on Beta 2 :)

+1

My Intel X25-M arrives tomorrow, can't wait to install!

---

### Post by Rockyc on 2010-04-08
April 8th, GMT is quickly coming to a close. . . any news on Beta 2?

---

### Post by ramasan on 2010-04-08
looks like the directory is up... 
[http://cdimage.ubuntu.com/releases/10.04/beta-2/](http://cdimage.ubuntu.com/releases/10.04/beta-2/)

firing up utorrent in 3...2...

---

### Post by ranch hand on 2010-04-08
Wait for the release notification.

---

### Post by kaffemonster on 2010-04-08
I'm seeding the torrent right now - on a 50/50mbit line here, should I share the ISO over FTP?

---

### Post by howefield on 2010-04-08
> **ranch hand said:**
> Wait for the release notification.

It is linked from the front page of ubuntu.com. I guess that's notification enough. :)

---

### Post by ToxicBurn on 2010-04-08
> **howefield said:**
> It is linked from the front page of ubuntu.com. I guess that's notification enough. :)
 
 
agree i do :)

---

### Post by andrewabc on 2010-04-08
[http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)

> Mozilla Firefox

Default search engine has been changed to Yahoo! The default Home Page will use either Google or Yahoo! depending on user setting.
But I thought they switched back to google, making this text not needed. ?

---

### Post by Rockyc on 2010-04-08
Beta 2 is up!

---

### Post by atlee on 2010-04-08
I'm getting Desktop dvd flavour for 64bit for my dream machine :P and netbook flavour for my older laptop :)

---

### Post by 23meg on 2010-04-08
Beta 2 has been [released]("http://ubuntuforums.org/showthread.php?t=1450110") - thanks to all who participated in ISO testing!

---

