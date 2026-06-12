---
title: "whats going on with karmic development?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by manfer on 2009-10-03
I know it is a beta and problems can happen but... so many, almost on every update a new issue, ...

Last one. Last update was going to update all openoffice and it broke it. It was solved with a forced update from terminal to solve dependencies but the upgrade broke it before, why? It is normal I receive a broken upgrade.

A similar thing happened on a dist-upgrade which was supposed to upgrade mysql from 5.0 to 5.1. 5.0 mysql core and server were dropped but mysql 5.1 ones where no installed on that dist-upgrade. To be even more strange 5.0 client was not dropped. So I finished with a system with no server and only client and not upgraded to 5.1. To solve it I had to drop 5.0 client and install 5.1 client, core, server myself.

Update manager crash just almost from a month now, I have to do updates from CLI.

When first suhosin-php was introduced a lot of apache requests were not served.

Some months ago a problem appeared, on boot the system always reported that some files on system partition had a time in future (I did nothing so that could happened just appeared). That finally was solved with a check on that file system but I don't know if that was correct because the files should not be wrong, what was wrong should be some package not working as it should.

Aptdaemon is buggy and crash just on X ini.

....

And a lot more issues that I cant remember.

And the system itself is not going very smooth. Instead of going better as always happened for me it is going worst and worst. I use ubuntu on this computer because it was really a lot faster than windows but now it is starting to work more as a windows platform than a linux one. Many times the system gets frozen for some seconds because it can't do all its tasks (and those tasks are only the Operating System itself and a web browser, ????)

Flash player gets 100% CPU (well I suppose this is not an ubuntu problem just adobe). But I think it was going much better before (maybe before 10.0 version appeared I don't know exactly).

I repeat I know I'm testing a beta but there are thinks I can't understand. I'm testing ubuntu betas since 5.04 as I can remember and never never had so many issues that on this Ubuntu OS release.

Is it just me that maybe has something broken or someone else is experimenting the same?

---

### Post by cariboo on 2009-10-03
If you have problems, this is the wrong place. Moved to [Karmic Testing]("http://ubuntuforums.org/forumdisplay.php?f=359")

---

### Post by manfer on 2009-10-03
Sorry but I was not looking for a solution I was only looking for opinions it is just why I posted it on Cafe.

---

### Post by raqball on 2009-10-03
No major breakage here... Everything going nice and smooth on my end... It's so rock solid, I have actually been using it as the only OS on my laptop since Alpha...

Not sure what you have going on, but it may be something busted on your end causing all the issues...

> **manfer said:**
> I know it is a beta and problems can happen but... so many, almost on every update a new issue, ...

Last one. Last update was going to update all openoffice and it broke it. It was solved with a forced update from terminal to solve dependencies but the upgrade broke it before, why? It is normal I receive a broken upgrade.

A similar thing happened on a dist-upgrade which was supposed to upgrade mysql from 5.0 to 5.1. 5.0 mysql core and server were dropped but mysql 5.1 ones where no installed on that dist-upgrade. To be even more strange 5.0 client was not dropped. So I finished with a system with no server and only client and not upgraded to 5.1. To solve it I had to drop 5.0 client and install 5.1 client, core, server myself.

Update manager crash just almost from a month now, I have to do updates from CLI.

When first suhosin-php was introduced a lot of apache requests were not served.

Some months ago a problem appeared, on boot the system always reported that some files on system partition had a time in future (I did nothing so that could happened just appeared). That finally was solved with a check on that file system but I don't know if that was correct because the files should not be wrong, what was wrong should be some package not working as it should.

Aptdaemon is buggy and crash just on X ini.

....

And a lot more issues that I cant remember.

And the system itself is not going very smooth. Instead of going better as always happened for me it is going worst and worst. I use ubuntu on this computer because it was really a lot faster than windows but know it is starting to work more as a windows platform than a linux one. Many times the system gets frozen for some seconds because it can't do all its tasks (and those tasks are only the Operating System itself and a web browser, ????)

Flash player gets 100% CPU (well I suppose this is not an ubuntu problem just adobe). But I think it was going much better before (maybe before 10.0 version appeared I don't know exactly).

I repeat I know I'm testing a beta but there are thinks I can't understand. I'm testing ubuntu betas since 5.04 as I can remember and never never had so many issues that on this Ubuntu OS release.

Is it just me that maybe has something broken or someone else is experimenting the same?

---

### Post by NoFearDJB on 2009-10-03
I've had no issues except the occasional app crashing. Nothing catastrophic though.

---

### Post by exploder on 2009-10-03
I see a very minor issue with the raw desktop color bleeding through under the mouse pointer when applications like Synapic are refreshing. The Solar Winds screen saver crashed a couple of times, (only the one screen saver does this). Those are the only problems I am seeing at the moment and they are very minor. Updates have been coming quickly and remaining issues are getting fixed.

---

### Post by FrancoNero on 2009-10-03
I'd say give it another shot come Release Candidate... I agree that there's a flurry of breakages over the last few weeks. been running karmic since alpha 4 or so, and I can't say it was a smooth experience so far, but that's why it's called alpha/beta.
I do hope they work out the remaining flaws until release candidate, because I can't wait to fully switch to Karmic

---

### Post by MC707 on 2009-10-03
> **FrancoNero said:**
> I'd say give it another shot come Release Candidate... I agree that there's a flurry of breakages over the last few weeks. been running karmic since alpha 4 or so, and I can't say it was a smooth experience so far, but that's why it's called alpha/beta.
I do hope they work out the remaining flaws until release candidate, because I can't wait to fully switch to Karmic

I agree. I have a little testing machine with karmic... still too soon not to be f***ed up with updates and stuff. I am still eagerly waiting for it, so many great things will come with it, I sense it (aka I hope).

---

### Post by manfer on 2009-10-03
Well, maybe it is only me who has problems with those strange updates. I really don't understand those updates that breaks packages and dependencies.

I understand it is a beta and all other problems will appear but those ones??

I hope next updates would repair the issues on my system.

Could be something broken on my system? I don't know how exactly apt works but it seems very strange those updates breaking dependencies or dropping packages that needs update without installing corresponding updates like what happened with mysql.

---

### Post by slakkie on 2009-10-03
Doing a dist-upgrade is not smart. Upgrade (apt-get) or safe-upgrade (aptitude) are the safe choices. If you dist-upgrade (apt-get/aptitude) or full-upgrade (aptitude) you could get yourself into trouble. Read both the man-pages of apt-get and aptitude to understand why.

I did not have any problems with mysql-server packages during the whole karmic alpha/beta stage.

---

### Post by manfer on 2009-10-03
But sometimes update manager does dist-upgrades if I'm not mistaken and when that happened with mysql was doing it through update manager not on CLI. I saw it was going to drop mysql server and core and did it anyway cause I supposed there was a good reason (and of course I supposed it was going to install the 5.1 versions, but I didnt look for them in the huge list of packages that were going to be updated). But after the upgrade finished I saw the update 5.1 versions where not installed and I did it myself.

Maybe I did something wrong anyway so I would look those man pages.

Thanks.

---

### Post by Seventh Reign on 2009-10-03
So far I've only encountered 2 problems with the Recent Beta.  

The god-aweful yellow orange default wallpaper.

You all know I'm a strong believer and advocate for the "You cant please everyone" group, and if you dont like it you can change it.  But seriously ... that wallpaper is by far the worst I've ever seen.  

And the Software Center .. when you click to show only installed Apps nothing changes.  It just shows everything.

---

### Post by chrisccoulson on 2009-10-03
The problems you're experiencing with "broken" packages are generally only because you're trying to upgrade packages before their dependencies have been built and/or published, so the packages aren't broken, as such. This is completely normal throughout the whole development cycle (pretty much right up to final freeze), and the problems will sort themselves out if you leave it a few hours (sometimes a bit longer if there are lots of things building).

---

### Post by psyke83 on 2009-10-03
> **chrisccoulson said:**
> The problems you're experiencing with "broken" packages are generally only because you're trying to upgrade packages before their dependencies have been built and/or published, so the packages aren't broken, as such. This is completely normal throughout the whole development cycle (pretty much right up to final freeze), and the problems will sort themselves out if you leave it a few hours (sometimes a bit longer if there are lots of things building).

Exactly.

manfer and others,

Testing the development release requires more care and attention than the final release. Please read the [sticky thread]("http://ubuntuforums.org/showthread.php?t=1280021") - it describes the issue clearly and succinctly. Also see [this]("http://ubuntuforums.org/showpost.php?p=8048061&postcount=5") post.

---

### Post by manfer on 2009-10-03
> **slakkie said:**
> Doing a dist-upgrade is not smart. Update (apt-get) or safe-upgrade (aptitude) are the safe choices. If you dist-upgrade (apt-get/aptitude) or full-upgrade (aptitude) you could get yourself into trouble. Read both the man-pages of apt-get and aptitude to understand why.

I did not have any problems with mysql-server packages during the whole karmic alpha/beta stage.

I dont understand what you mean with update for apt-get because update does "nothing" (nothing to the system just only to the packages index). You can update update update update update 1 million times and your system would be on same state. Of course that's totally safe. If your system has nothing broken it would remain the same.

Of course I always do an update before upgrade or dist-upgrade. Maybe I did wrong but as I have update manager inoperable I go to CLI and I do an apt update then apt upgrade and if it shows some packages are retained I try apt dist-upgrade to see its output. And if its output says it is going to update all, I do it instead of upgrade.

I don't know why my update manager is crashing every time. It is always when the window to set administrative password should appear. Update manager gets frozen and the window never appears.

And aptdaemon just crash on start.

Both have been upgraded recently and the problem persists.

And I was not who dropped mysql core and server 5.0 it was update manager (when it still was working) who did. One of those times it says it has to do a partial upgrade. It did and it dropped those packages without installing new versions, not me.

I will continue reading the man pages I still didnt see anything about the trouble you can get into if you do a wrong dist-upgrade.

---

### Post by manfer on 2009-10-03
> **chrisccoulson said:**
> The problems you're experiencing with "broken" packages are generally only because you're trying to upgrade packages before their dependencies have been built and/or published, so the packages aren't broken, as such. This is completely normal throughout the whole development cycle (pretty much right up to final freeze), and the problems will sort themselves out if you leave it a few hours (sometimes a bit longer if there are lots of things building).

I update very often so maybe this is what happened to me. Then there is nothing wrong if that happens and if you later do another upgrade would be corrected when all packages are builded.

Thanks then it is nothing to be alarmed with. I was just thinking I had a totally broken system if no one else was experimenting something like that.

Deal with the common problems sometimes happen when testing the beta is normal and I understand but I didn't understand that one about the wrong updates.

Anyway the problem I experimented with mysql 5.0 being dropped in a partial upgrade was very very strange. Because I think that wont be solved on the next upgrade, if the package is removed theres nothing to upgrade later. I dont think apt would select 5.1 versions to be installed by itself later.

But as I read in your recommended post it even can happen and the user has to solve it by itself. OK.

---

### Post by psyke83 on 2009-10-03
> **manfer said:**
> I update very often so maybe this is what happened to me. Then there is nothing wrong if that happens and if you later do another upgrade would be corrected when all packages are builded.

Wrong. If a package gets removed due to dependency problems, it usually won't get re-installed, even when the repository is updated and all dependencies are in place.

> Thanks then it is nothing to be alarmed with. I was just thinking I had a totally broken system if no one else was experimenting something like that.

It happens to plenty of people (who don't read the release notes or stickies).

> Deal with the common problems sometimes happen when testing the beta is normal and I understand but I didn't understand that one about the wrong updates.

That's not dealing with a problem - it's creating a problem due to a lack of patience to wait for the repository to become consistent.

> Anyway the problem I experimented with mysql 5.0 being dropped in a partial upgrade was very very strange. Because I think that wont be solved on the next upgrade, if the package is removed theres nothing to upgrade later. I dont think apt would select 5.1 versions to be installed by itself later.

I don't think so either. The repository has the -5.0 and -5.1 packages to give users the choice of which version to use.

The only reason that mysql 5.0 was dropped from your system was because you didn't wait for all the dependencies of the 5.0 packages to get built and released to the repository.

> But as I read in your recommended post it even can happen and the user has to solve it by itself. OK.

It is necessary to "solve" it only if the mistake has already been made. The real lesson to learn is to *stop performing partial upgrades, unless you are certain they are necessary*. To do that, you need to check the changelogs and/or confirm on the forums.

---

### Post by psyke83 on 2009-10-03
> **manfer said:**
> I dont understand what you mean with update for apt-get because update does "nothing" (nothing to the system just only to the packages index). You can update update update update update 1 million times and your system would be on same state. Of course that's totally safe. If your system has nothing broken it would remain the same.

slakkie made a small error, let me correct (in bold):

>  Originally Posted by slakkie:
Doing a dist-upgrade is not smart. **Upgrade** (apt-get) or safe-upgrade (aptitude) are the safe choices. If you dist-upgrade (apt-get/aptitude) or full-upgrade (aptitude) you could get yourself into trouble. Read both the man-pages of apt-get and aptitude to understand why.

> I don't know why my update manager is crashing every time. It is always when the window to set administrative password should appear. Update manager gets frozen and the window never appears.

And aptdaemon just crash on start.

Both have been upgraded recently and the problem persists.

Perhaps you previously ran a partial upgrade that removed packages essential to the Update Manager and/or aptdaemon, in the same way that you removed OpenOffice; it's hard to say. I don't have this problem.

I hope you spend some more time learning about the development process, and not to do partial upgrades. It'll save you a lot of headaches.

---

### Post by manfer on 2009-10-03
Ok, it is clarify.

I think with previous releases I had not those kind of problems and only on this karmic release I got into trouble. But maybe I was only lucky not having them earlier.

I didnt know update manager could be suggesting partial upgrades when they were no needed because the packages were being builded. Ok.

---

### Post by manfer on 2009-10-03
> **psyke83 said:**
> slakkie made a small error, let me correct (in bold):





Perhaps you previously ran a partial upgrade that removed packages essential to the Update Manager and/or aptdaemon, in the same way that you removed OpenOffice; it's hard to say. I don't have this problem.

I hope you spend some more time learning about the development process, and not to do partial upgrades. It'll save you a lot of headaches.

If any package needed (dependencies) by update manager or aptdaemon is not installed shouldnt it be shown in apt upgrade?

---

### Post by slakkie on 2009-10-04
> **manfer said:**
> I dont understand what you mean with update for apt-get because update does "nothing" (nothing to the system just only to the packages index). You can update update update update update 1 million times and your system would be on same state. Of course that's totally safe. If your system has nothing broken it would remain the same.


My bad, I ment upgrade like psyke83 already stated.

---

### Post by manfer on 2009-10-06
Finally todays aptdaemon upgrade solved that package problems on my system. Now it is not crashing anymore. Update manager is working again.

OK, with this post I learned not to trust update manager, or that is what you say. Well, that's really strange if I can not always trust what is supposed to be an automatic update system.

So I have myself to decide, in some situations if update manager shows correct output or not. Well, I would look carefully what it is doing when it suggest a partial upgrade.

Still are problems but with minor priority:

[LIST]
[*]a warning "BAR 6: no parent found of device that appears" on boot, that seems to be no important for what I read.
[*]no info dir entry: usr/share/info/menu.info usr/share/info/ispeel.info. That seems to be solved on debian so it is supposed to be solved soon in ubuntu.
[*]unknown media files: all/all, all/allfiles... that I read is normal too and related to kdelibs.
[/LIST]

I suppose soon or later these problems would be solved.

And a disgusting issue that probably ubuntu cant solve and is more an adobe job:
[LIST]
[*]Adobe player eats 100% CPU.
[/LIST]

---

### Post by philinux on 2009-10-06
> **manfer said:**
> Finally todays aptdaemon upgrade solved that package problems on my system. Now it is not crashing anymore. Update manager is working again.

OK, with this post I learned not to trust update manager, or that is what you say. Well, that's really strange if I can not always trust what is supposed to be an automatic update system.

So I have myself to decide, in some situations if update manager shows correct output or not. Well, I would look carefully what it is doing when it suggest a partial upgrade.

Never do a partial upgrade.

---

### Post by manfer on 2009-10-06
> **philinux said:**
> Never do a partial upgrade.

????? never never never ????

Today it did again. It was dropping libuniconf4.4 but it was installing libuniconf4.6. It is not secure in that case too?

---

### Post by philinux on 2009-10-06
> **manfer said:**
> ????? never never never ????

Today it did again. It was dropping libuniconf4.4 but it was installing libuniconf4.6. It is not secure in that case too?

When it offers a partial click cancel first then upgrade. Then wait a day or so and update again.

Read the stickies. They contain a wealth of info.
[http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)

---

### Post by manfer on 2009-10-06
> **philinux said:**
> When it offers a partial click cancel first then upgrade. Then wait a day or so and update again.

Read the stickies. They contain a wealth of info.
[http://ubuntuforums.org/showthread.php?t=1280021](http://ubuntuforums.org/showthread.php?t=1280021)

I read I read, you made me doubt I had did it. But I can't see a never there.

[LIST]
[*]Once you've started testing, do not upgrade your installation blindly - especially, avoid partial upgrades offered by Update Manager unless you know precisely why it's offering a partial upgrade. Regardless of which tool (APT, Update Manager, Synaptic, Aptitude) you're using to upgrade your packages, always check the list of packages to be removed, upgraded and installed before each upgrade. If in doubt, check the changelogs ("Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or at packages.ubuntu.com) to see why a package may be being removed.
[/LIST]

Anyway I have clear to have very very very special care and will wait every partial upgrade appears and try later.

---

