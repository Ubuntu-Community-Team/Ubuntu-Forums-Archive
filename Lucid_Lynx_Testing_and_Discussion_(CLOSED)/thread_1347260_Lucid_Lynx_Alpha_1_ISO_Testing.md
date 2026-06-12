---
title: "Lucid Lynx Alpha 1 ISO Testing"
date: 2009-12-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-12-06
Alpha 1, which will be the first milestone release of the Lucid Lynx development cycle, will be out next Thursday. Like every milestone release, this one will benefit from good community testing coverage.

**[SIZE="3"]What Is ISO Testing?[/SIZE]**

A while before each Ubuntu development milestone release (alphas, betas and the release candidate), the package archive is frozen, and only bug fixes that help towards a high quality testing release are accepted. Towards the end of this period, usually on the first day of the week leading to the release, a set of daily images are designated as candidates for release, and are subject to an additional round of testing commonly referred to as "ISO testing", in order to ensure that they're reasonably free of showstopper bugs and ready to be tested by the broader testing audience that grows with each milestone.

**[SIZE="3"]How You Can Help[/SIZE]**

Candidate images for Lucid Lynx Alpha 1 can be expected to be available on [the ISO testing tracker]("http://iso.qa.ubuntu.com/") on Monday. You can test any number of test cases you'd like, and report bugs.

If you're unfamiliar with the procedures, there are two good places to start:

[list][*] [Ara Pulido's tutorial]("http://ubuntutesting.wordpress.com/2009/09/21/old-friend-iso-testing-tracker/") on how to use the ISO testing tracker 

[*] The [testing procedures page on the Ubuntu Wiki](https://wiki.ubuntu.com/Testing/ISO/Procedures)[/list]

You may want to download your daily images now, and [update with rsync]("https://help.ubuntu.com/community/RsyncCdImage") when testing begins, to avoid possible traffic congestion at the last minute. A good way to download a testing image and keep it up to date is the dl-ubuntu-test-iso script, which is part of the very handy ubuntu-qa-tools package ([click to install]("apt:ubuntu-qa-tools")).

If you need immediate help with testing, the best place to go is the #ubuntutesting IRC channel on irc.freenode.net. You can also follow [the #ubuntutesting tag on Twitter]("http://search.twitter.com/search.atom?q=%23ubuntutesting"), and feel free to ask any questions you may have on this thread.

---

### Post by MacUntu on 2009-12-06
Is it ok to use USB flash drives (via USB Startup Disk Creator) instead of CDs?

---

### Post by Gina on 2009-12-06
> **MacUntu said:**
> Is it ok to use USB flash drives (via USB Startup Disk Creator) instead of CDs?

Good question.  That's what I usually do - except for my laptop which only has USB 1 and slower than using DVDs and probably CDs as well.

---

### Post by ranch hand on 2009-12-06
I need to log in with the buggers because I am on a different installation.  Right now, my connection is fine, I can't get;

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

to load at all.

Just "waiting for ---".

Guess I will try later and in the morning.

---

### Post by 23meg on 2009-12-06
> **MacUntu said:**
> Is it ok to use USB flash drives (via USB Startup Disk Creator) instead of CDs?

It should be, since one of its intended purposes at the design stage was making ISO testing easier and less wasteful. It's still worth dropping a note in your reports that you used it, rather than burning a CD.

---

### Post by MacUntu on 2009-12-06
> **23meg said:**
> It's still worth dropping a note in your reports that you used it, rather than burning a CD.

Will do so, thanks.

---

### Post by Gina on 2009-12-06
I know I'm jumping the gun here but I found today's daily ISO won't install on my AMD64 (or at least the 64 bit Desktop and Alternate won't).  I needed to reinstall because my system crashed when updating and I couldn't recover completely.  I'll try again tomorrow and following days :)

---

### Post by MacUntu on 2009-12-07
Had time the whole morning, but [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/) didn't answer. Tracker down?

---

### Post by ranch hand on 2009-12-07
Yup, same problem I was having yesterday.  Just does not seem to be there at all, but FF just keeps "waiting".

EDIT;
As soon as I sent this, I got this on the tab trying to get to "http://iso.qa.ubuntu.com/";

**Proxy Error**

 The proxy server received an invalid response from an upstream server.
The proxy server could not handle the request *[GET /]("http://iso.qa.ubuntu.com/")*.
 Reason: **Error reading from remote server**

---

### Post by MacUntu on 2009-12-07
Now it's up but not yet ready for Alpha 1 testing.

---

### Post by Gina on 2009-12-07
I tried today's live ISO but it wouldn't install on my AMD64 - ubuquity crashed.  Try again tomorrow I guess.

---

### Post by juanJosepablos on 2009-12-07
¿where is the link for an old daily update? Alpha1 seem to be based on  
20091028

---

### Post by technicallygeek on 2009-12-07
I downloaded a lucid iso and the qa tools but can't seem to get the dl-ubuntu-test-iso script to update the iso. I followed [http://archives.free.net.ph/message/20091016.104741.368f4847.el.html](http://archives.free.net.ph/message/20091016.104741.368f4847.el.html) 

this is how I set thought the script was supposed to be setup 
```
# Sample .dl-ubuntu-test-iso.cfg file. The included settings are the
# default for the script
#
#    BASEURL The server from which to download. This is the cdimage
#    server that Canonical operates for Ubuntu development.
BASEURL="rsync://cdimage.ubuntu.com/cdimage"

#    RELEASES
#    Which releases of Ubuntu to target. Hardy and Karmic are the
#    only ones currently supported. Defaults to both.
RELEASES="lucid"

#    ARCHS
#        Which computer architectures to download. If you only have
#        one, you will want to set this variable to that. Default is
#        all the Ubuntu release architectures.
ARCHS="amd64"

#    FLAVORS
#        Which flavors of Ubuntu to download: Ubuntu, Kubuntu, etc.
#        The default is all of them.
FLAVORS="ubuntu"

#    VARIANTS
#        Which variants of each flavor to download: desktop cd, alternative
#        cd, server cd, dvd, etc. Default is all of them.
VARIANTS="desktop alternate"

#    EXCLUDE
#        Which flavors to NOT download. Sometimes it's easier to specify
#        "all, except..." and this allows you to do that. See also the
#        --exclude option above.
EXCLUDE=""

#    OPTS
#        What options to give rsync.
OPTS="-zthhP"

#    NO_ACT
#        If this is set to "yes", then the script won't run rsync, it will
#        just do everything else. See also to --no-act option above.
NO_ACT="no"

#    VERIFY
#        If this is set to "true", then the script will verify the iso's
#        md5sum against the downloaded MD5SUMS file.
VERIFY="false"

#    BUILD
#        Tell the script to download a specific build of the isos rather
#        than the current iso
#
# Examples
# BUILD="20080715"
# BUILD=$(date --date="yesterday" +%Y%m%d)
#
BUILD="current"
```

Maybe if someone could break it down into dummy terms on how Im supposed to update my lucid-desktop-amd64.iso that would help. Getting my image to update is the only thing haven't been able to figure out.

---

### Post by Gina on 2009-12-07
Yes, that's the configuration script.  I found the main bash script needed editing to use the latest development version.  I'll dig my edited version out.

Back shortly.

---

### Post by juanJosepablos on 2009-12-07
I personally use zsync. but my main problem is that I want an old version for the daily-live iso file. I have the feeling that the version from last week was working fine.

---

### Post by technicallygeek on 2009-12-07
I tried zsync and it gets to about 30% and stops

---

### Post by MacUntu on 2009-12-07
> **juanJosepablos said:**
> I personally use zsync. but my main problem is that I want an old version for the daily-live iso file. I have the feeling that the version from last week was working fine.

[http://cdimage.ubuntu.com/cdimage/daily-live/](http://cdimage.ubuntu.com/cdimage/daily-live/)

Seems like there is only "today" and "yesterday" (IMO ok, since it's a _daily_ image). It's the same for Alpha versions: you either get the current one or nothing.

---

### Post by Gina on 2009-12-07
I've attached my edited script file.  NOTE I had to add **.txt** to get it to upload. 

This is my **iso.cfg** file :-
```
# Sample iso.cfg file. The included settings are the default for the
# script
#
#    BASEURL
#        The server from which to download. This is the cdimage server
#        that Canonical operates for Ubuntu development.
BASEURL="rsync://chromium.ubuntu.com/cdimage"

#    RELEASES
#        Which releases of Ubuntu to target. Hardy and Intrepid are the
#	only ones currently supported. Defaults to both.
RELEASES="lucid"

#    ARCHS
#        Which computer architectures to download. If you only have
#        one, you will want to set this variable to that. Default is
#        all the Ubuntu release architectures.
ARCHS="i386 amd64"

#    FLAVORS
#        Which flavors of Ubuntu to download: Ubuntu, Kubuntu, etc.
#        The default is all of them. -- ubuntustudio xubuntu
FLAVORS="ubuntu"

#    VARIANTS
#        Which variants of each flavor to download: desktop cd, alternative
#        cd, server cd, dvd, etc. Default is all of them. -- 
VARIANTS="desktop alternate"

#    EXCLUDE
#        Which flavors to NOT download. Sometimes it's easier to specify
#        "all, except..." and this allows you to do that. See also the
#        --exclude option above.
EXCLUDE=""

#    OPTS
#        What options to give rsync.
OPTS="-zthhP"

#    NO_ACT
#        If this is set to "yes", then the script won't run rsync, it will
#        just do everything else. See also to --no-act option above.
NO_ACT="no"

#    VERIFY
#        If this is set to "true", then the script will verify the iso's
#        md5sum against the downloaded MD5SUMS file.
VERIFY="true"

#    BUILD
#        Tell the script to download a specific build of the isos rather
#        than the current iso
#
# Examples
# BUILD="20080715"
# BUILD=$(date --date="yesterday" +%Y%m%d)
#
BUILD="current"
```
Note - I set verify to true so that it does md5sum checking automatically.

---

### Post by juanJosepablos on 2009-12-07
> **technicallygeek said:**
> I tried zsync and it gets to about 30% and stops

This is the command that I run:

```
zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso.zsync
```

works fine on my side. Is anyone able to install using latest daily-live?

---

### Post by technicallygeek on 2009-12-07
I tried the updated script with the boolean value for the md5sum it didnt work 
it tells me 
```
from: can't read /var/mail/which
```and the zsync command doesnt work either 
```
localhost: Success
failed on url http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zsync
could not read control file from URL http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zsync
```

maybe Im making some noob mistake or something. I have read over the rsync wiki doc and the iso testing wiki countless times and im cant seem to figure this out

---

### Post by lolren on 2009-12-07
it is worth to install  lynx alpha 1? to days ago xplash was still there.... no plymouth:(

---

### Post by 23meg on 2009-12-07
> **lolren said:**
> it is worth to install  lynx alpha 1? 

That completely depends on what your purpose in installing it would be.

---

### Post by juanJosepablos on 2009-12-07
could you try this command?

```
 wget http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zsync
```

---

### Post by technicallygeek on 2009-12-07
```
wget http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso.zsync 
```gives this error

```
Error parsing proxy URL http://localhost:4001 : Bad port number.
```

---

### Post by juanJosepablos on 2009-12-07
Seem like something is getting on your web traffic somehow. If you are able to run this command:

```
wget http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.iso
```

then you are allow to download iso images, if fail try:


```
wget http://www.google.com
```

If that works means that you are allow to have web traffic.

---

### Post by technicallygeek on 2009-12-08
I fixed it with

```
apt-get remove --purge anon-proxy
```

I was able to run

```
 rsync -zhhP rsync://cdimage.ubuntu.com/cdimage/daily-live/current/lucid-desktp-amd64.iso  . 
```

it updated about 600 some MB at first I thought it was a whole new image but when i looked in the pwd there was just the one image that I started with so I guess it updated.

---

### Post by Gina on 2009-12-08
I had another go at installing the AMD64 version using the Alt CD ISO.  First attempt stopped at 66% with an error about snmptbase (I think).  Since the option to download and install MIBS mentioned snmp, I decided to try without.  It went right through this time and I was able to boot to the menu and boot Lucid.  Again, it went to the command line login.  I left it for several minutes and it didn't time out this time so I logged in and got errors - tried startx and got more errors saying it couldn't load X etc. and dumped me back to the prompt.

Tomorrow is another day and another try.

---

### Post by kansasnoob on 2009-12-08
Would it not be best to just ask folks to sign up:

[http://iso.qa.ubuntu.com/user/register](http://iso.qa.ubuntu.com/user/register)

Then they'll get email notifications (if they choose to).

Sometimes they do seem to keep this "in house".

---

### Post by ranch hand on 2009-12-08
I found the live session to be GREAT.

Then I tried to install and realized I had 2 problems.

A>ubiquity crashed before the installer could open.
B>could not file a bug report because it could not connect to my DSL.

So I came over here to the Stoned Lizard and filed my "failed" report.

Bummer

---

### Post by Gina on 2009-12-09
I had the same problem.  The Alt CD installed (without MIBS) but wouldn't run - lots of errors.  I still have the 32 bit version working on my laptop but there are a large number of packages being held back and only a Partial Install available (which I don't do).  About to try today's live.

---

### Post by 23meg on 2009-12-09
The tracker has been updated with Alpha 1 candidates, which are now being built.

---

### Post by Gina on 2009-12-09
> **23meg said:**
> The tracker has been updated with Alpha 1 candidates, which are now being built.I presume then that it's no good trying until Alpha 1 is announced?

---

### Post by VMC on 2009-12-09
> **Gina said:**
> I presume then that it's no good trying until Alpha 1 is announced?

That's what I've decided to do. Wait until tomorrow or later and install Lucid on its own alpha. I have a lot of issues with this karmic to lucid upgrade.

---

### Post by 23meg on 2009-12-09
> **Gina said:**
> I presume then that it's no good trying until Alpha 1 is announced?

Not really; there's no harm in testing them *before* the release, which in fact is the very point of ISO testing.

---

### Post by juanJosepablos on 2009-12-09
Hi,
I have test the  20091209/lucid-desktop-i386.iso (Alpha1), 
One small issue:

When reboot the system  the text "Please remove CD ...and press enter" does not get displayed at the bottom of the screen, just the logo.

But if you press enter it actually works.

---

### Post by juanJosepablos on 2009-12-09
My Acer 1410 does not start up using lucid alpha iso. I am trying to boot up using recovery mode, but it get a black screen and i am not able to recover using another console (crtl+F1). Please advise about how to get more info and report back.

---

### Post by kansasnoob on 2009-12-09
> **juanJosepablos said:**
> My Acer 1410 does not start up using lucid alpha iso. I am trying to boot up using recovery mode, but it get a black screen and i am not able to recover using another console (crtl+F1). Please advise about how to get more info and report back.

Are you saying you did get it to install and now it won't boot?

What type of install is it? The only OS on the machine? A multi-boot?

I found it unusable:

[https://bugs.launchpad.net/ubuntu/+bug/494642](https://bugs.launchpad.net/ubuntu/+bug/494642)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/494608](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/494608)

---

### Post by juanJosepablos on 2009-12-09
It dual boot windows xp and ubuntu.
1) boot up the live cd ok
2) install works fine.
3) when reboot i can select ubuntu as OS
4) after initial boot up, I can see the some messages (last one [drm])
5) I get a black screen (ctrl+F1 does not work )

So i try to get some logs (boot in up from live-cd), but there is nothing on the /var/log of the boot process.


If the help i can install ubuntu alone. but I do not think that it matters.

---

### Post by ranch hand on 2009-12-09
The desktop worked fine and connected to the "net".

Installer failed in partitioner.

My bug was a duplicate for 494608.

I tried running on the option of "install ubuntu" and had the same grief.

Tried running fro m the desktop with "sudo ubiquity" second verse same as the first.

I did not try going it synaptic and reinstalling ubiquity.  This has worked a couple times for me but is hardly the type of thing the "average" user is going to do.

---

### Post by kansasnoob on 2009-12-09
> **ranch hand said:**
> The desktop worked fine and connected to the "net".

Installer failed in partitioner.

My bug was a duplicate for 494608.

I tried running on the option of "install ubuntu" and had the same grief.

Tried running fro m the desktop with "sudo ubiquity" second verse same as the first.

I did not try going it synaptic and reinstalling ubiquity.  This has worked a couple times for me but is hardly the type of thing the "average" user is going to do.

Be sure to create an account (if you haven't already) and also report that here:

[http://iso.qa.ubuntu.com/qatracker/test/3453](http://iso.qa.ubuntu.com/qatracker/test/3453)

I doubt they'll rebuild if I'm the only one squawking. I see there are now two duplicates to that, but no additional "fails" at the iso reporting site.

---

### Post by kansasnoob on 2009-12-09
> **juanJosepablos said:**
> It dual boot windows xp and ubuntu.
1) boot up the live cd ok
2) install works fine.
3) when reboot i can select ubuntu as OS
4) after initial boot up, I can see the some messages (last one [drm])
5) I get a black screen (ctrl+F1 does not work )

So i try to get some logs (boot in up from live-cd), but there is nothing on the /var/log of the boot process.


If the help i can install ubuntu alone. but I do not think that it matters.

I don't think reinstalling would matter.

Not sure what might be going on.

---

### Post by ranch hand on 2009-12-09
The ISO testing folks got my report just before I posted here.  Started ISO testing last cycle.  It is FUN.

---

### Post by kansasnoob on 2009-12-09
I hope they do a rebuild on this so we don't hear a gazillion complaints!

I managed to get my old Lucid going real well by removing ubuntu-desktop, then updating, then reinstalling ubuntu-desktop, and updating again. All in a chroot of course.

---

### Post by juanJosepablos on 2009-12-09
ok, 
Now I try a different route to get 10.04 on this laptop. 
Install 9.10 and upgrade.everything ok with version 9.10, So upgradte to 10.04, change sources aptitude update aptitude dist-upgrade
restart, same error: Black screen and unable to change console. 

Because I had a previous kernel (2.6.31-14-generic), I try to boot up with it. The system boots up without problems. Seem like the crupit is the 2.6.32 version of the kernel.

how can I debug this problem? As a test, i try to use the 2.6.32-7-386 version instead but it has same results as the 2.6.32-7-generic

---

### Post by Gina on 2009-12-10
They're still fixing bugs - there are probems with the X server that gives you a graphical display.  Alpha 1 is expected for later today - there are  likely to be problems until that is released.  I suggest waiting.

---

### Post by jerrylamos on 2009-12-10
> **juanJosepablos said:**
> ok, 
Now I try a different route to get 10.04 on this laptop. 
Install 9.10 and upgrade.everything ok with version 9.10, So upgradte to 10.04, change sources aptitude update aptitude dist-upgrade
restart, same error: Black screen and unable to change console. 

Because I had a previous kernel (2.6.31-14-generic), I try to boot up with it. The system boots up without problems. Seem like the crupit is the 2.6.32 version of the kernel.

how can I debug this problem? As a test, i try to use the 2.6.32-7-386 version instead but it has same results as the 2.6.32-7-generic

Juan, I've gotten black screen on various updates on two of my test pc's at various levels of update.

Lately the best solution in booting is to edit the boot line, and replace "quiet splash" with "nomodeset".

What "nomodeset" does is keep the kernel from setting graphics mode instead of text mode as it boots up.  Somehow this can result in the X drivers getting screwed up.  This problem has been going on for months.  Sometimes it's O.K. then the developers make a change and boom.  Black screen.

If "nomodeset" allows you to get a readable screen, then do
sudo gedit /etc/default/grub
then replace "quiet splash" with "nomodeset" and save.
Then do
sudo update-grub
Good luck....works for me sometimes.

Jerry

p.s. -7 is broken for a number of different functions for me.  I try it out, then when I want to do something useful like this post I boot a 9.04 karmic.

---

### Post by philinux on 2009-12-10
> **ranch hand said:**
> The desktop worked fine and connected to the "net".

Installer failed in partitioner.

My bug was a duplicate for 494608.

I tried running on the option of "install ubuntu" and had the same grief.

Tried running fro m the desktop with "sudo ubiquity" second verse same as the first.

I did not try going it synaptic and reinstalling ubiquity.  This has worked a couple times for me but is hardly the type of thing the "average" user is going to do.

Same here, ubiquity crashed on changing first partition. Install option takes you to the desktop so same crash.
No point me raising another dup.

Not sure if anyone else bugged this but usplash logo is mangled and it says ubuntu running in low res but desktop appears normal.

---

### Post by juanJosepablos on 2009-12-10
Thanks Jerry,
Tried your solution, but kernel 2.6.32-7 still fails on the acer 1410. A newer Acer laptop (5632z) does not seem to be affected by this problem.

I have try to install  bootchart to get some timing on the boot process, but for some reason it does not work for me. I wanted to see the different with previous chart using version 9.10. Should I open another thread for that?

---

### Post by VMC on 2009-12-10
> **philinux said:**
> Same here, ubiquity crashed on changing first partition. Install option takes you to the desktop so same crash.
No point me raising another dup.

Not sure if anyone else bugged this but usplash logo is mangled and it says ubuntu running in low res but desktop appears normal.

Ubiquity crashed a couple of times for me as well. When I selected  the partition I wanted and mount as "/" then checked format it crashed. What I then did, was to deleted that same partition first then did the previous soung & dance and it worked. Weird. Anyhoo, I'm up and running.

---

