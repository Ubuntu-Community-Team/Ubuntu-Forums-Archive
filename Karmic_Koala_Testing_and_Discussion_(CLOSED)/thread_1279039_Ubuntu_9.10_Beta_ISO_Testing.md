---
title: "Ubuntu 9.10 Beta ISO Testing"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-09-30
**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A few days before each Ubuntu development milestone release (Alphas, the Beta and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. At the end of this period, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for the Karmic Beta release are now up at [the ISO Testing Tracker]("http://iso.qa.ubuntu.com/"). To find out how you can contribute by testing them, take a brief look at the links below:

[http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/](http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/)

[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

---

### Post by andrewabc on 2009-09-30
[https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)
Is release schedule. Please don't ask what time tomorrow the beta will be released. Just wait for the official announcement.

---

### Post by kansasnoob on 2009-09-30
Bug searching/filing frustrations :frown:

First of all, I'm reminded of trying to get something done about the Intrepid CD eject problem, well I obviously failed as anyone with an Intrepid Live Cd can attest to.

That aside, on to business: I've done several installs of Karmic today (used the testing iso) on a testing hard drive and discovered that if you choose "auto-login" during installation you just end up in an endless loop of brief display and then a blank screen.

If you Alt > Sys Req > B, upon reboot all is well, so it's hardly a fatal flaw, but I've been pulling my hair out to try and file a decent bug report (I did report my results on the iso tracker), but this seems inexcusable!

Bug searching/reporting should not be soooooooo difficult! Right now it's a nightmare!

---

### Post by 23meg on 2009-10-01
> **kansasnoob said:**
> but I've been pulling my hair out to try and file a decent bug report (I did report my results on the iso tracker), but this seems inexcusable!

Bug searching/reporting should not be soooooooo difficult! Right now it's a nightmare!

What exactly was the problem you ran into?

---

### Post by VMC on 2009-10-01
First time I came across "ISO Testing". The questions I have are:
(1) Do we have to download a complete ISO again or use the already installed and updated karmic OS.
(2) Can I use the testing ISO while I'm testing?!
(3) How long does it take - Do I leave my computer on for 24hrs or is this just several passes of testing.

I read through the material and maybe I just passed by the above answers. I don't have an account yet and would be willing if I knew more about what I'm getting into. 

Maybe if someone that has done this work before on previous releases can explain in more detail what's involved. 

The reason I'm asking is I don't want to say yes and then realize it's taking to much of my time and then someone assigned to that test is missing my assignment.

Thanks for your kind response.

---

### Post by 23meg on 2009-10-01
> **VMC](1) Do we have to download a complete ISO again or use the already installed and updated karmic OS.[/QUOTE]

You need to download the candidate ISO you want to test. [Using rsync]("https://help.ubuntu.com/community/RsyncCdImage") can make it easier.

[QUOTE=VMC](2) Can I use the testing ISO while I'm testing?![/QUOTE]

I don't understand this question said:**
> (3) How long does it take - Do I leave my computer on for 24hrs or is this just several passes of testing.

It depends on what tests you wish to perform; you can dedicate as much/little time as you want.

---

### Post by VMC on 2009-10-01
> **23meg said:**
> You need to download the candidate ISO you want to test. [Using rsync]("https://help.ubuntu.com/community/RsyncCdImage") can make it easier.



I don't understand this question; could you clarify?

I only have one computer to test and to do work on. Can I use the same computer. While testing I know I can't. But after a test, can I then stop and use the computer for other projects? I'm guessing the answer is yes from your previous answers..

Thanks for replies.

---

### Post by andrewabc on 2009-10-01
You can download the iso, burn to cd-rw, test it out without installing it. It won't affect your computer. You'd have to restart computer to test the cd, and then shutdown again when done testing and take the cd out.

If you are not sure I would not bother with testing the candidate. Just wait until official beta or later is released.

---

### Post by archiesteel on 2009-10-01
> **VMC said:**
> The reason I'm asking is I don't want to say yes and then realize it's taking to much of my time and then someone assigned to that test is missing my assignment.

I think I understand your concern: you're worried that you have to commit to a certain amount of work in order to contribute to the testing of the new ISO/development milestone. Is this correct?

You can stop worrying: the beauty of open-source testing is that you don't have to commit to anything. You install the new version, play around with it, and if you find any bugs you can enter bug reports - or not. You're not committed to anything, i.e. you contribute as much as you want to contribute.

Hope this answers your questions!

---

### Post by kansasnoob on 2009-10-01
> **23meg said:**
> What exactly was the problem you ran into?

Sorry to just disappear, but my grandson was somewhat seriously injured during football practice so I've spent nearly 24 hours at the hospital. 

Anyhoo, I installed a total of 7 times yesterday (3 test case scenarios - entire disc, auto-resize, and manual partitioning) to verify the problem and I'm quite sure it boils down to gdm.

If you select to "automatically login" during the installation procedure, then upon being prompted to restart & eject Live CD, when the machine restarts it justs goes into an endless loop where the screen (xsplash I think) blinks very briefly, then just black screen for several seconds, and it continues to repeat that behavior ad nauseam.

If you choose to "login using password" during installation all is fine.

I did report this in my test results yesterday (tester ID = Lance), so hopefully Henrik caught it.

Yesterday I had just figured out that what I need to do to report the bug is boot into one of the failed test cases (possibly by starting in recovery mode) and simply use "ubuntu-bug gdm" to collect info.

Sadly I'm just too exhausted at the moment to swap in my testing hard drive and complete it, must shower and get some rest.

If not "fixed" by the time the Beta is released, it probably should at least be reflected in "known bugs" in the Release Announcement. As I said if the default "login using password" is chosen all is fine, so it's hardly a fatal flaw (more of an annoyance).

---

### Post by 23meg on 2009-10-01
[QUOTE=kansasnoob]Sorry to just disappear, but my grandson was somewhat seriously injured during football practice so I've spent nearly 24 hours at the hospital. [/QUOTE]

Sad to hear that; I too had "disappeared" over a similar emergency a week or so ago. Hope he's doing fine.

I was actually referring to what problems you'd had in searching for and reporting bugs.

---

### Post by philinux on 2009-10-01
> **23meg said:**
> **[SIZE="3"]What Is ISO Testing?[/SIZE]**

A few days before each Ubuntu development milestone release (Alphas, the Beta and the RC), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. At the end of this period, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for the Karmic Beta release are now up at [the ISO Testing Tracker]("http://iso.qa.ubuntu.com/"). To find out how you can contribute by testing them, take a brief look at the links below:

[http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/](http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/)

[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)

I'll have a download and test tomorrow or over the weekend. Thanks for the links.

---

### Post by 23meg on 2009-10-01
> **philinux said:**
> I'll have a download and test tomorrow or over the weekend. Thanks for the links.

Thanks for your interest, but it's too late, since the beta is out now. I'm sorry to have been a bit late in posting the announcement on the forums; I'll make sure it happens in a more timely manner for the RC, which you can then help with.

---

### Post by philinux on 2009-10-01
> **23meg said:**
> Thanks for your interest, but it's too late, since the beta is out now. I'm sorry to have been a bit late in posting the announcement on the forums; I'll make sure it happens in a more timely manner for the RC, which you can then help with.

Oh righto no worries. Keep up the good work then!

---

### Post by kansasnoob on 2009-10-01
> **23meg said:**
> Sad to hear that; I too had "disappeared" over a similar emergency a week or so ago. Hope he's doing fine.

I was actually referring to what problems you'd had in searching for and reporting bugs.

Regarding the grandson it was a spinal injury requiring surgery, but he seems fine - no "cord" involvement - so I think it was more of a "fear factor" thing.

Regarding the bug searching/reporting issue I just never did find a truly related bug. I searched for bugs in ubiquity and gdm on Launchpad.

This will be the first time I've used the "ubuntu-bug packagename" feature. In the past I've always either been able to use apport or I've found a similar bug report to add info to.

Sometimes filing bug reports can be frustrating, but I suppose the more I do it the easier it will become.

---

### Post by kansasnoob on 2009-10-01
BTW the md5sum for the i386-desktop iso testing image is the same as the Beta so I may just do a reinstall on the drive I'm currently using and gather the needed info.

---

### Post by VMC on 2009-10-01
> **23meg said:**
> Thanks for your interest, but it's too late, since the beta is out now. I'm sorry to have been a bit late in posting the announcement on the forums; I'll make sure it happens in a more timely manner for the RC, which you can then help with.

I too will be ready then for testing at the RC level. Thanks, now that I know what to look for.

---

### Post by tsger on 2009-10-01
> **kansasnoob said:**
> 

If you select to "automatically login" during the installation procedure, then upon being prompted to restart & eject Live CD, when the machine restarts it justs goes into an endless loop where the screen (xsplash I think) blinks very briefly, then just black screen for several seconds, and it continues to repeat that behavior ad nauseam.

If you choose to "login using password" during installation all is fine.

I did report this in my test results yesterday (tester ID = Lance), so hopefully Henrik caught it.

Yesterday I had just figured out that what I need to do to report the bug is boot into one of the failed test cases (possibly by starting in recovery mode) and simply use "ubuntu-bug gdm" to collect info.

Sadly I'm just too exhausted at the moment to swap in my testing hard drive and complete it, must shower and get some rest.

If not "fixed" by the time the Beta is released, it probably should at least be reflected in "known bugs" in the Release Announcement. As I said if the default "login using password" is chosen all is fine, so it's hardly a fatal flaw (more of an annoyance).



Actually, I have this exact problem, with the weird flashing display after installing and upon reboot (which never happens...I have to do a hard reboot (press and hold power button...yikes!).  However, unlike kansasnoob, I chose the default "login using password" option.  I haven't tried it with the automatic login feature.

---

