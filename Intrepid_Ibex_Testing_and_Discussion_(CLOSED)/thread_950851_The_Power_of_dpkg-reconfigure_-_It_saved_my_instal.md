---
title: "The Power of dpkg-reconfigure - It saved my install!"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bobnutfield on 2008-10-17
Hello Everyone,

Just wanted to share last night's experience.  I got home from work to find 158 updates waiting requiring a 168mb download.  This was obviously going to be another dist-upgrade update, which I expect several of before Intrepid gets officially released.  It was a partial upgrade, but, this is a development version, so I went for it.

With just 10mb to go, my system hung while trying to download and install Flash for firefox.  I waited for several hours before deciding it was not going to continue, so, I felt the only thing to do is hit Ctrl-C and try to start the process over again.  It would not work, so I rebooted.  I knew what was coming:  A destroyed system.  I was right....no X, dozens of errors while booting, but finally booted to a command line.  I knew with the failed partial upgrade, I probably would never be able to restore the system without reinstalling.

So, I decided I was going to experiment trying different things just to see what I was able to do, knowing that a reinstall was ultimately the only way to fix.  Just for the heck of it, I tried:

```
sudo dpkg-reconfigure -phigh -a
```

As I watched, every single package was stopped, reconfigured, and restarted.  This process took the better part of an hour and a half, since it was effectively the same as re-installing but using packages that already existed.  It finally completed and dumped my back to a command line.  I rebooted into recovery mode, selected "try to fix X", rebooted, and, to my untter amazement, Ubuntu had repaired itself!  I was restored to a completely functioning desktop with the upgrade installed!

My point, is, if something gets broken during an upgrade, it looks like there is not too much that this command cannot fix.  So, before you give up and reinstall (like I was about to do), give it a shot!  It might work for you, too.

---

### Post by psyke83 on 2008-10-17
> It was a partial upgrade, but, this is a development version, so I went for it.

Don't. Do. Partial. Upgrades.

Yes, sometimes during the development release a dist-upgrade will intentionally elect to remove obsolete packages. 95% of the time, however, a partial upgrade is caused by a new package which has been uploaded, but it has dependencies that have not yet been uploaded.

If new users learned this prerequisite knowledge while testing the development release, they would save themselves a lot of headaches.

As for your problem, you may have had problems downloading the Flash tarball (the server can be quite erratic). If you cancel the installation, you may be able to fix things via: ```
$ sudo apt-get install -f
```

The method you used is also effective; just be sure to run the above command to finish installing the partially-installed packages.

---

### Post by bobnutfield on 2008-10-17
> If new users learned this prerequisite knowledge while testing the development release, they would save themselves a lot of headaches.

Thank you, that is a point well taken, but, I'm not a new user and I have learned to never do a partial upgrade on a stable release, but I have been required to do a number of times when testing a development release becuase the partial upgrade was not because of missing dependencies but my installed packages.  On two occassions while testing Intrepid, the missing dependencies never showed up, so I partial-upgraded and it worked out fine until now.

But I appreciate your point, and will certainly keep this mind.

---

### Post by mdurham on 2008-10-17
> With just 10mb to go, my system hung while trying to download and install Flash for firefox. I waited for several... 
How does this happen? It always appears to me that all the packages are downloaded first, then the install takes place.
Cheers, Mike

---

### Post by bobnutfield on 2008-10-17
> **mdurham said:**
> How does this happen? It always appears to me that all the packages are downloaded first, then the install takes place.
Cheers, Mike

Good point.  I have never seen it either.  The files were in the process of being installed, and as apart of the installation, the system connected to Adobe to download Flash 10.  This is where is hung up.  As the previous poster noted, this site does sometimes get a little flaky when downloading from it.  It connected, started the download, stopped and when never continue.  Since I wrote this post, I have discovered other things I could have done which may have helped me recover quicker.  I was just releived and pleased to save my installation.  Intrepid has worked so well for me on this laptop, that I had begun to save some important files.

---

### Post by MALEADt on 2008-10-17
> **mdurham said:**
> How does this happen? It always appears to me that all the packages are downloaded first, then the install takes place.
Cheers, Mike

I must say I came across a same error in here too. Did an update/safe-upgrade on a computer which was outdated for a full week. Download process started, but hung at 96% (process still was alive). Anyway, I terminated it, ran it again, it downloaded only the missing parts and installed them all. Weird case though.

---

### Post by kansasnoob on 2008-10-27
> **bobnutfield said:**
> Hello Everyone,

Just wanted to share last night's experience.  I got home from work to find 158 updates waiting requiring a 168mb download.  This was obviously going to be another dist-upgrade update, which I expect several of before Intrepid gets officially released.  It was a partial upgrade, but, this is a development version, so I went for it.

With just 10mb to go, my system hung while trying to download and install Flash for firefox.  I waited for several hours before deciding it was not going to continue, so, I felt the only thing to do is hit Ctrl-C and try to start the process over again.  It would not work, so I rebooted.  I knew what was coming:  A destroyed system.  I was right....no X, dozens of errors while booting, but finally booted to a command line.  I knew with the failed partial upgrade, I probably would never be able to restore the system without reinstalling.

So, I decided I was going to experiment trying different things just to see what I was able to do, knowing that a reinstall was ultimately the only way to fix.  Just for the heck of it, I tried:

```
sudo dpkg-reconfigure -phigh -a
```

As I watched, every single package was stopped, reconfigured, and restarted.  This process took the better part of an hour and a half, since it was effectively the same as re-installing but using packages that already existed.  It finally completed and dumped my back to a command line.  I rebooted into recovery mode, selected "try to fix X", rebooted, and, to my untter amazement, Ubuntu had repaired itself!  I was restored to a completely functioning desktop with the upgrade installed!

My point, is, if something gets broken during an upgrade, it looks like there is not too much that this command cannot fix.  So, before you give up and reinstall (like I was about to do), give it a shot!  It might work for you, too.

So OK I can't constrain myself any longer! What is -phigh?

---

### Post by skillllllz on 2008-10-27
> **kansasnoob said:**
> So OK I can't constrain myself any longer! What is -phigh?

From the dpkg-reconfigure man pages:
```
man dpkg-reconfigure
``` -pvalue, --priority=value
           Specify the minimum priority of question that will be displayed.
           dpkg-reconfigure normally shows low priority questions no matter
           what your default priority is.


.

---

### Post by cevans on 2008-10-27
> **psyke83 said:**
> Don't. Do. Partial. Upgrades.

Yes, sometimes during the development release a dist-upgrade will intentionally elect to remove obsolete packages. 95% of the time, however, a partial upgrade is caused by a new package which has been uploaded, but it has dependencies that have not yet been uploaded.

dist-upgrades can be quite important, and I've been using dist-upgrade for a decade or so without many ill effects. When using unstable repositories, however, it's important to check the details of what apt is actually planning to do before allowing it to change anything. If dist-upgrade is removing an unimportant package or two, or removing a package and installing a new package that has the same purpose, everything should be fine. If it wants to remove a few hundred packages, or remove a package like coreutils or libc6, allowing it to run is probably a bad idea. 

> **psyke83 said:**
>  If you cancel the installation, you may be able to fix things via: ```
$ sudo apt-get install -f
```

The method you used is also effective; just be sure to run the above command to finish installing the partially-installed packages.

In this particular case, since flash downloads in the configuration step, there probably weren't any partially-installed packages. In general, however, it is good advice.

> **bobnutfield said:**
> As I watched, every single package was stopped, reconfigured, and restarted.  This process took the better part of an hour and a half, since it was effectively the same as re-installing but using packages that already existed.

While dpkg-reconfigure can be very effective, one should note that it isn't the same as reinstalling, which is done by apt-get install --reinstall. dpkg-reconfigure just reruns the configuration scripts for the packages; I believe the reason you had problems was because your dist-upgrade failed during configuration, and thus dpkg-reconfigure configured the packages that had been upgrade but hadn't been configured.

> My point, is, if something gets broken during an upgrade, it looks like there is not too much that this command cannot fix.  So, before you give up and reinstall (like I was about to do), give it a shot!  It might work for you, too.

I can assure you that I've done many apt dist-upgrades and dpkg installs that have broken things dpkg-reconfigure hasn't been able to fix.

> **bobnutfield said:**
> Good point.  I have never seen it either.  The files were in the process of being installed, and as apart of the installation, the system connected to Adobe to download Flash 10.  This is where is hung up.

This is done by a few packages where the contents are such that they can't be stored in Ubuntu repositories at all; ttf-mscorefonts-installer is another one, or at least used to be, if I recall correctly.

> **kansasnoob said:**
> So OK I can't constrain myself any longer! What is -phigh?

As skillllllz noted, it pertains to the level of configuration questions that dpkg asks while installing. I believe most of the frontends in Ubuntu automatically select high. Low can ask a terribly large number of questions, and can be quite annoying; I don't think many people actually use it these days, but I can remember dreading the questions.

---

