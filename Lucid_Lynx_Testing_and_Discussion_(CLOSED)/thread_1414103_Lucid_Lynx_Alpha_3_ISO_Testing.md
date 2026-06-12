---
title: "Lucid Lynx Alpha 3 ISO Testing"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2010-02-23
Alpha 3, which will be the third milestone release of the Lucid Lynx development cycle, will be out this Thursday. Like every milestone release, this one will benefit from good community testing coverage.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the release candidate), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. Towards the end of this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for Lucid Lynx Alpha 3 are now available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/"). You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. And feel free to ask any questions you may have on this thread.

---

### Post by kansasnoob on 2010-02-23
Looking fairly good too! So far I've only done the Live Session test and the Entire Disc install but it went fairly well.

Running the Live CD did present the gdm (login screen) but just hitting enter several times without entering any username or password got me to the Live Desktop just fine. It does appear that the user must create a new username w/admin privileges in order to use persistence w/casper rw, but I think that may be a good idea.

The Entire Disc install went flawlessly choosing Install from the menu with one minor caveat, when the install was complete a warning popped up saying that the Migration Assistant couldn't migrate - of course there was nothing to migrate so I just clicked on continue and was prompted to restart, then to remove disc and press enter.

Oh the Check disc for errors still fails to produce any results so I'll have to dig up that old bug, and I'll have to think about the gdm thing, I know there was a prior bug report but then you actually had to create a user to get in.

I'll complete my other two tests and see if I can duplicate the same behavior but for the third and last alpha this looks great to me!

---

### Post by VMC on 2010-02-23
> **kansasnoob said:**
> ...when the install was complete a warning popped up saying that the Migration Assistant couldn't migrate - of course there was nothing to migrate so I just clicked on continue and was prompted to restart, then to remove disc and press enter....

It happened to me as well. Colin Watson fixed the original migration-assistant user login error. This is new. I'm going to try it again and capture the screen and the /var/log, and send it to the open bug.

Also the client-side decoration problem of "ghosting" has been fix or improved a lot. I don't see it in the games anymore.

Also Rhythmbox hogging the CPU has been fixed.

This all came from todays live-daily update.

---

### Post by andrewabc on 2010-02-23
Original post should change "released next thursday" to "released this thursday".

Safest bet would be "Thursday February 25".

Sorry I read post and first thought "next thursday" meant feb 2, even though I remember release schedule saying 25.
[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)

---

### Post by kansasnoob on 2010-02-23
Three bugs:

#1: CD integrity test still produces no results.

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/500198](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/500198)

#2: Lucid Alpha 3 Live CD boots to login screen  

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526545](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526545)

Note: logging in w/username "ubuntu" and NO password seems to work every time.

#3: ubi-migrationassistant fails w/exit code 141

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526581](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526581)

None that I'd consider show stoppers in an alpha :D

---

### Post by kansasnoob on 2010-02-23
Oh I also noticed that if you press F4 there's no longer a Safe Graphics Mode option.

I didn't need it but I wonder if that's a bug or just a design change :confused:

---

### Post by 23meg on 2010-02-23
> **andrewabc said:**
> Original post should change "released next thursday" to "released this thursday".

Safest bet would be "Thursday February 25".

Sorry I read post and first thought "next thursday" meant feb 2, even though I remember release schedule saying 25.
[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)

Fixed, thanks.

---

### Post by ranch hand on 2010-02-23
> **kansasnoob said:**
> Three bugs:

#1: CD integrity test still produces no results.

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/500198](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/500198)

#2: Lucid Alpha 3 Live CD boots to login screen  

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526545](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526545)

Note: logging in w/username "ubuntu" and NO password seems to work every time.

#3: ubi-migrationassistant fails w/exit code 141

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526581](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/526581)

None that I'd consider show stoppers in an alpha :D
Yes, while a little buggy, it does work.

I am using 64bit and had no login called for.

Only installed on "manual" but the migration assistant did come up with one possibility (there actually should have been more but I was happy to move on as I never use that).

Did have the same problem as last time of no message to remove the disk and hit enter.  Waited a minute and hit enter and nothing happened.  Alt+SysRq+b to reboot.

---

### Post by kansasnoob on 2010-02-23
> **kansasnoob said:**
> Oh I also noticed that if you press F4 there's no longer a Safe Graphics Mode option.

I didn't need it but I wonder if that's a bug or just a design change :confused:

I'm quoting myself because I'm very curious about this.

I don't like filing bug reports when the "bug" is actually a design change. I'm thinking maybe with the changes in etc/X11/xorg.conf.failsafe it's no longer needed :confused:

---

### Post by VMC on 2010-02-23
> **kansasnoob said:**
> I'm quoting myself because I'm very curious about this.

I don't like filing bug reports when the "bug" is actually a design change. I'm thinking maybe with the changes in etc/X11/xorg.conf.failsafe it's no longer needed :confused:

Reading from the ISO's "/isolinux/f4.txt":
```
There is no dedicated rescue mode on this disc. However, since the disc
provides a complete user environment, it is possible to use the
command-line and/or graphical tools provided to rescue a broken system,
and to use a web browser to search for help. Extensive advice is available
online for most kinds of problems that might cause your normal system to
fail to boot correctly.
```

I would think after reading that, its intentional.

---

### Post by k3lt01 on 2010-02-23
This may be the wrong place to ask this so please feel free to move or delete if need be, but, have they fixed the mini.iso yet? I don't want it to pull 670mb of Ubuntu desktop without my say so if I use it again.

---

### Post by VMC on 2010-02-23
> **k3lt01 said:**
> This may be the wrong place to ask this so please feel free to move or delete if need be, but, have they fixed the mini.iso yet? I don't want it to pull 670mb of Ubuntu desktop without my say so if I use it again.

I haven't used that in years. I downloaded the last one, karmic, but it took forever to retrieve the needed files. Maybe because its archived.

But on the main menu, item #6 - Download installer components. Isn't that what you want? Have you tried it?

---

### Post by kansasnoob on 2010-02-23
Just looked, we have a rebuild coming so keep those spare drives warmed up :P

---

### Post by k3lt01 on 2010-02-23
> **VMC said:**
> I haven't used that in years. I downloaded the last one, karmic, but it took forever to retrieve the needed files. Maybe because its archived.

But on the main menu, item #6 - Download installer components. Isn't that what you want? Have you tried it?I have used the mini.iso on my own machines since Hardy. Apparently Karmic had a similar problem, downloading and installing OOo without being asked to do so although this didn't happen to me, and it still isn't fixed from what I have been told. I haven't tried any other method on LiveCD or AlternateCD other than the default install method.

---

### Post by utUtu on 2010-02-24
> **k3lt01 said:**
> I have used the mini.iso on my own machines since Hardy. Apparently Karmic had a similar problem, downloading and installing OOo without being asked to do so although this didn't happen to me, and it still isn't fixed from what I have been told. I haven't tried any other method on LiveCD or AlternateCD other than the default install method.

At the very end when it ask for Software to install just select nothing to get a minimal set.  

But if you chose a desktop say Ubuntu it will pull in a lot of dependencies like OO and suggestions/recommends.

---

### Post by zeroandone on 2010-02-24
> **kansasnoob said:**
> Oh I also noticed that if you press F4 there's no longer a Safe Graphics Mode option.

I didn't need it but I wonder if that's a bug or just a design change :confused:
Man, this is bad news to me. I need Safe Graphics Mode option. I could only install Lucid Lynx with Safte Graphics Mode to get rid of the annoying, distorted window problem as described here: [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406). Unless the problem has been fixed in this new release.

[IMG]http://img15.imageshack.us/img15/6240/screenshotsystemmonitor.png[/IMG]

---

### Post by kansasnoob on 2010-02-24
> **zeroandone said:**
> Man, this is bad news to me. I need Safe Graphics Mode option. I could only install Lucid Lynx with Safte Graphics Mode to get rid of the annoying, distorted window problem as described here: [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406). Unless the problem has been fixed in this new release.

[IMG]http://img15.imageshack.us/img15/6240/screenshotsystemmonitor.png[/IMG]

From:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/525966/comments/1](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/525966/comments/1)

> I removed "Safe graphics mode" as the xforcevesa option no longer had any effect anyway, and wew're trying to simplify the main menu. You can add 'nomodeset' from the F6 "Other Options" menu at CD boot time, which may help you; that was the only remaining effective part of "Safe graphics mode".



---

### Post by zeroandone on 2010-02-24
Thanks. I will give it a try.

---

### Post by jppr on 2010-02-24
[http://cdimage.ubuntu.com/daily-live/20100224.1/](http://cdimage.ubuntu.com/daily-live/20100224.1/)  That works perfect = ) This is first time after 9.10 alpha 3 when live cd works me

---

### Post by jerrylamos on 2010-02-24
> 
Colin Watson  wrote on 2010-02-22:  	  #1

I removed "Safe graphics mode" as the xforcevesa option no longer had any effect anyway, and wew're trying to simplify the main menu. You can add 'nomodeset' from the F6 "Other Options" menu at CD boot time, which may help you; that was the only remaining effective part of "Safe graphics mode".

There are THREE critical parts of the old "Safe Graphics Mode" for two of my test machines:
1. nomodeset in the boot kernel line.  I have seen a late Lucid that had nomodeset as a CD boot option.
2. "vesa" video graphics driver.  I've had to laboriously key that into Lucid by putting "single" in the kernel boot line, then using nano since the default xorg driver doesn't work.
3. "compiz" apt-get remove - but it appears that compiz has been blacklisted for my machines that compiz fails on.

What's missing from Lucid is a method of choosing "vesa" other than remembering the syntax of xorg.conf....

Appreciate help in getting Lucid to boot more cleanly, i.e. black screen pretty useless.  I'm getting by with "nomodeset" and "vesa"....

Jerry

---

### Post by xebian on 2010-02-24
The ubiquity seems ok but going 'back' is always a problem.  Had to redo it 3 times because going 'forward' is what works.

You would think that the vertical tabs looks like you could go to each one directly and change/enter data there but it won't.

The skip button( bar?) at the bottom seems confusing.  Don't know  what it controls- the slide show or the activity on the top.  Found out later that it's the download but why would you skip in the first place?  It would be nice if instead of just <skip> add more text to what's skipping and place it close to what it controls.

It's ok to find and replace but does anyone even bother to proof read anything ever?

[HTML]Welcome
Thank you for choosing Kubuntu 10.04, the Karmic Koala!
Kubuntu is based on Ubuntu and features the K Desktop Environment (KDE).
Kubuntu is released biannually with at least 18 months of free security updates.
While Kubuntu is installing, we invite you to explore your new operating system.
Kubuntu is built to be safe. Feel free to explore!
[/HTML]

---

### Post by sim-value on 2010-02-25
No torrents ?!

---

### Post by Tikkyca on 2010-02-25
its a little buggy,but anyway i think final relase will be great :D

---

### Post by Harlekin33 on 2010-02-25
Alpha 3 released!

Throttles on maximum!

:D

---

### Post by Saghaulor on 2010-02-25
Technically the wrong thread, but I figured it's a good place to ask.

Is there any special procedure for upgrading from Alpha 2 to Alpha 3?

I have 10.04 server i386 Alpha 2 installed, and I don't really want to have to format and start all over. Will I be upgraded to Alpha 3 if I just do ```
sudo aptitude full-upgrade
```?

Would doing an upgrade cause me more problems than it is worth?

Please advise. Thank you.

---

### Post by ratcheer on 2010-02-25
Saghaulor, according to everything I have heard, doing a full-upgrade should give you everything that comes with alpha3.

Tim

---

### Post by jppr on 2010-02-25
When has been long period that has comes much new packages and updates, i do after that clean / fresh installation. i don´t care is that alpha 3 or what else. sometimes i do fresh installation almost every week, sometimes goes 2-3 weeks

---

### Post by Saghaulor on 2010-02-25
> **jppr said:**
> When has been long period that has comes much new packages and updates, i do after that clean / fresh installation. i don´t care is that alpha 3 or what else. sometimes i do fresh installation almost every week, sometimes goes 2-3 weeks

Yeah, from release to release I do a fresh install. I've never done any development testing, so I didn't know if it was buggy between the stages.

---

### Post by VMC on 2010-02-25
> **Saghaulor said:**
> 
Is there any special procedure for upgrading from Alpha 2 to Alpha 3?

I have 10.04 server i386 Alpha 2 installed, and I don't really want to have to format and start all over. Will I be upgraded to Alpha 3 if I just do ```
sudo aptitude full-upgrade
```?

Would doing an upgrade cause me more problems than it is worth?

Please advise. Thank you.Why full upgrade? You may be bringing in more than you want. There are packages that are held back. just a safe-upgrade is enough. It will bring up up to alpha 3.

---

### Post by RJARRRPCGP on 2010-02-25
Epic fail here, cannot even get the live CD desktop!: 

I'm puzzled of what has occurred. I'm gonna reinstall an actual release. 

It looks suspiciously like the ISO didn't even get generated correctly.

My ADSL is rock stable. Looks like a mirror problem at the least. :(

[http://ubuntuforums.org/showthread.php?t=1416192](http://ubuntuforums.org/showthread.php?t=1416192)

---

