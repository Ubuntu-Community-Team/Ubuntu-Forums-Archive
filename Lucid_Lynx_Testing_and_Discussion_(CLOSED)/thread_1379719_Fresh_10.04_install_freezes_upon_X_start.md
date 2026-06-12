---
title: "Fresh 10.04 install freezes upon X start"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dangerp on 2010-01-12
I just installed 10.04 (lucid) via CD.  It was a fresh install, all the default options, and I let ubuntu wipe out and reformat/partition my drive the way that it saw fit.  In other words, nothing remarkable about the install.  No issues with the install, but when ubuntu tries to start X for the first time, it freezes after about 2 seconds.  I can see that it had started to render a message saying that my laptop battery is kaput (true, btw), but it just stopped, and nothing is responsive, the mouse won't even move.

I can only use the system if I boot into recovery mode, and drop to a root shell prompt.  No issues there.  I can do all of the usual command prompt stuff, but when I try "startx", it starts up X and then freezes in the exact same manner.

I am fairly comfortable with the command line, but I don't know what troubleshooting steps to take from here.  I have an IBM thinkpad T42.  I believe it has an ATI Mobility Radeon 7500.  I was previously running Jaunty (I think) without issues.

---

### Post by kansasnoob on 2010-01-12
Lucid is still in development and has it's own home here at the forums:

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

That said, did you use the Alpha 1 Live CD.

If so you might do better with the pre-Alpha 2 iso testing CD ........... or you might try updating and upgrading via command line by using the recovery mode at boot.

---

### Post by garvinrick4 on 2010-01-12
What did the screen say before going to splash. If it states "Cannot find plymouth"
then you have to install plymouth. Lucid is going to have a different splash I do believe
and I had to install do a "sudo apt-get clean && sudo apt-get install plymouth"
Without quotes. 
 All sorts of trouble with X on the latest dist-upgrade but that is expected when in Alpha 1
to have these problems. I have 54 files to do with splash installed we will see what happens. Hope this solves your boot problem.

---

### Post by dangerp on 2010-01-12
Thank you so much for your extremely quick replies!  I will direct any further questions to the lucid forum that you mentioned.  I would have done an update/upgrade at the beginning, but I was too damn lazy to truck my laptop over to the router (too lazy to try to get wireless working on the command line).  I did it, and everything seems to be working now.

Thanks!

---

### Post by dangerp on 2010-01-12
I posted this in the wrong forum, so I am reposting in order to reach the proper people :).  Original thread is here:

[http://ubuntuforums.org/showthread.php?t=1379652](http://ubuntuforums.org/showthread.php?t=1379652)

I just installed 10.04 (lucid) via CD. It was a fresh install, all the default options, and I let ubuntu wipe out and reformat/partition my drive the way that it saw fit. In other words, nothing remarkable about the install. No issues with the install, but when ubuntu tries to start X for the first time, it freezes after about 2 seconds. I can see that it had started to render a message saying that my laptop battery is kaput (true, btw), but it just stopped, and nothing is responsive, the mouse won't even move.

I can only use the system if I boot into recovery mode, and drop to a root shell prompt. No issues there. I can do all of the usual command prompt stuff, but when I try "startx", it starts up X and then freezes in the exact same manner.  To be clear, this is happening after I get to the desktop, the login screen and splash seem to work fine.  Maybe its a startup app?

I did an update/upgrade, and I thought it worked, but it only worked for an additional 20 seconds.  Any further troubleshooting tips would be awesome.

I am fairly comfortable with the command line, but I don't know what troubleshooting steps to take from here. I have an IBM thinkpad T42. I believe it has an ATI Mobility Radeon 7500. I was previously running Jaunty (I think) without issues.

---

### Post by dangerp on 2010-01-12
Argh, it's actually not working, it just lasted about 20 seconds longer.  I opened a new thread in the lucid forums, since that is where it actually belongs...

I also tried installing plymouth, but that didn't work.  It wasn't the splash anyways, it was after reaching the desktop that I had issues.  Thanks again for your suggestions!

[http://ubuntuforums.org/showthread.php?p=8655692](http://ubuntuforums.org/showthread.php?p=8655692)

---

### Post by ranch hand on 2010-01-12
Well one thing I would do is reboot in recovery and if you are getting to the menu I would run the "dpkg fix broken packages" option.  It may not do any good but it may.

If not some information on your box is needed.  Something along the line of what is in my sig would be a real good start.

What version that you used would also be good.  The alpha2 snap shot is coming up on thursday and it might just be a good idea to wait and try it again.  The installer has been buggy and acoupple of other problems have been bothering the LiveCD.  These seem to be fixed.

If you decide to go that route it would be good to put this (and any install you ever do) on 2 partitions, 1 for / and 1 for /home.

Until then continuing to run updates and try it is all anyone can say until we know more about your box.

We are getting x updates pretty regularly.

---

### Post by cariboo on 2010-01-12
Merged threads.

---

### Post by ranch hand on 2010-01-13
> **cariboo907 said:**
> Merged threads.
Good job.

---

### Post by jerrylamos on 2010-01-13
> **dangerp said:**
> I just installed 10.04 (lucid) via CD.  

I can only use the system if I boot into recovery mode, and drop to a root shell prompt.  

Hmmm.  I've a Thinkpad T40 with ATI Radeon Mobility M7 LW 7500 which may be similar to yours? Running with today's updates.  (My IBM tower is pretty dead with today's lucid but that's an intel video driver issue.)

The T40 is running latest update of Lucid O.K.

I don't know what level lucid CD you're using.  At the command prompt could you do a 
cat /proc/version
which might tell us?

In your spot I'd boot to recovery mode then either do:

fix broken packages

then reboot or else at command line:

dhclient
apt-get update
apt-get dist-upgrade
Y where asked for
reboot

Let us know...

Jerry

---

### Post by jerrylamos on 2010-01-13
> **jerrylamos said:**
> Hmmm.  I've a Thinkpad T40 with ATI Radeon Mobility M7 LW 7500 which may be similar to yours? Running with today's updates. 

Oops, spoke too soon, just locked up, screen frozen, Ctrl-Alt-F1 won't work.  I can't ssh into it from another pc either nor will Ctrl-Alt-Del. Power button time.

Alpha 2 is supposed to release tomorrow??

Jerry

---

### Post by ranch hand on 2010-01-13
Yes A2 tomorrow. Just downloading the ISO-testing image for today, yesterdays was a little buggy but the installer and partitioner worked real well.

---

### Post by DougieFresh4U on 2010-01-13
Did fresh install yesterday. When I rebooted this morning, I was presented with a lot of errors (gibberish). Some thing about  not finding home dev and  appamor or what ever that is. Then the can not find plymouth. But I waited a few minutes and was presented with 'desktop'. It's a little slow and 'jerky' (intel 810 graphics) but it's working

---

### Post by jerrylamos on 2010-01-13
> **ranch hand said:**
> Yes A2 tomorrow. Just downloading the ISO-testing image for today, yesterdays was a little buggy but the installer and partitioner worked real well.

On i845G video graphics on IBM tower, initial 20090113 CD boot screen is displayed.  Push enter and machine freezes tight.  No action ever.

Rather sluggishly came up on ati video.  Select scan CD for defects, get a splash like screen, no messages, CD light blinks forever.

Whoopee.

Jerry

---

### Post by ranch hand on 2010-01-13
Just to be a smartass;  Maybe you should try a 20100113 CD.

To be more supportive it may be better t owait for the release of A2.  Hopefully they will have it working better than it is now.

CD worked pretty well on my ATI setup.

---

### Post by jerrylamos on 2010-01-13
> **ranch hand said:**
> Just to be a smartass;  Maybe you should try a 20100113 CD.

Takes me about a year to get the year straight....

Jerry

---

### Post by ranch hand on 2010-01-13
I usually have to ask the date when writing a check.  Just too used to being where the date/time don't mean a thing.

I hope that you can get this going, at least well enough to file bugs.  I kept a "kinda" track on the people with serious problems with 9.10 when it was released and it seemed that their hardware had not been represented, in many cases, in testing.  We need a diverse bunch of hardware testing this to get it right.

Sure can be frustrating, remember to breath.

---

### Post by phillw on 2010-01-13
This is where I'm up to

[http://ubuntuforums.org/showthread.php?t=1380464](http://ubuntuforums.org/showthread.php?t=1380464)

If one of the mods want's to merge these .. the answer may lie in rolling back to karmic dirver, sorta like this [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Phill.

---

### Post by ranch hand on 2010-01-13
I just do not see the reason for going back to old drivers in a testing phase release.  Trying a newer driver or version of x like the edgers bunch put out I can see.

Our purpose here is to test 10.04. It works or it doesn't.  If it doesn't we let the devs know so the y can fix it.  How is this done with drivers from 9.10?

---

### Post by VMC on 2010-01-13
> **ranch hand said:**
> I just do not see the reason for going back to old drivers in a testing phase release.  Trying a newer driver or version of x like the edgers bunch put out I can see.

Our purpose here is to test 10.04. It works or it doesn't.  If it doesn't we let the devs know so the y can fix it.  How is this done with drivers from 9.10?

I agree. Going backwards is not the solution. I'm not sure I've seen a big report for the current wave of black screen or no X.




[SIZE="1"]BTW-I haven't written a check in years. Everything online now. :)[/SIZE]

---

### Post by Ibidem on 2010-01-13
There was one version of X that did not work at all; it was fixed within a day.
I see a number of reports of freezes when using modesetting, and a few reports that indicate success.
Of course, there is a negative skew: problems are posted more often than successes.
So the sum total is that X works (except a version or two), modesetting might be around equal parts success/failure and* really* speeds up boot when it does work (18 second boot reported), and the proprietary drivers (often) have some measure of functionality but may not *actually* enable compositing or (possibly) certain other hardware-accelerated stuff.
The question is whether drivers or Compiz are making trouble.
Ibidem

---

### Post by ranch hand on 2010-01-14
I may not be able to use desktop effects, which I do not like anyway, bot this box, for now is rocking on all 7 installs with x and plymouth working great.

I lost one install before A1.  Have replaced it with the same 9.04>9.10>10.04 upgrade.  It had too many hacks to survive the first time around but is actually doing better than the rest (slightly) right now.

I have had some trouble with x but they are updating that sucker twice a day some times.  Wait a while and it will work (I did have one that took 4 days - 9.10>10.04 upgrade).

---

### Post by jerrylamos on 2010-01-14
FYI, email today:

> Ubuntu-x Digest, Vol 29, Issue 10   

[http://webmail.aol.com/30361-111/aim-2/en-us/mail/DisplayMessage.aspx?ws_popup=true](http://webmail.aol.com/30361-111/aim-2/en-us/mail/DisplayMessage.aspx?ws_popup=true)

Hi everyone,

If you have an intel or an ati card and, you're running Lucid, and after a 
system upgrade and a reboot you get a black screen (with KMS i.e. by default) 
there is an easy fix for you.

Turn on your computer, press the "shift" key to enter the grub menu and select 
"recovery mode". This should drop you to the command line. At this point 
reinstall xserver-xorg-core with the following command:

apt-get install --reinstall xserver-xorg-core

Finally type "reboot" to restart your computer and boot as usual.

Things should work well again.

This shouldn't happen in dist-upgrades from Karmic to Lucid or in new 
installations but only in some cases after updating a Lucid system.

Note: revision ubuntu5 of xserver-xorg-core has a fix for the problem already 
but (for some unknown reason) it doesn't seem to work in 100% of cases.

Sorry for the inconvenience.

Regards,

-- 
Alberto Milone
Sustaining Engineer (system)
Foundations Team
Canonical OEM Services

This does NOT work for this IBM Thinkpad R31 i830 graphics.  I have to use nomodeset otherwise black screen just after hitting enter on the grub menu.

Good luck everyone.  Jerry

---

### Post by phillw on 2010-01-14
> **ranch hand said:**
> I just do not see the reason for going back to old drivers in a testing phase release.  Trying a newer driver or version of x like the edgers bunch put out I can see.

Our purpose here is to test 10.04. It works or it doesn't.  If it doesn't we let the devs know so the y can fix it.  How is this done with drivers from 9.10?

having the driver information and confirming it is that driver - would make it possible to file a bug-reoprt - a general "it doesn't work" is not a great help to the devs.

If the 'roll-back' works, I can ignore the update to the version that borked my system. and await the next one

Phill.

---

### Post by phillw on 2010-01-14
> **jerrylamos said:**
> FYI, email today:



This does NOT work for this IBM Thinkpad R31 i830 graphics.  I have to use nomodeset otherwise black screen just after hitting enter on the grub menu.

Good luck everyone.  Jerry

That arried a i waz popping a reply on - it worked - thank you !!

Phill.

---

### Post by VMC on 2010-01-14
There's another update today.Going from "1ubuntu5" to "1ubuntu6". Hopefully it will fix Jerry's kids. 

5 fixed mine, and I installed 6 in Kubuntu today, with no ill effects.

Using - Intel i865

---

### Post by jerrylamos on 2010-01-15
> **VMC said:**
> I agree. Going backwards is not the solution. I'm not sure I've seen a big report for the current wave of black screen or no X.

From the release notes pointed to in the sticky from 23meg,

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/506418](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/506418)

is a bug about black screen.  The bug in the report seems different than the one I get but sounds similar.

Basically, "Ubuntu xorg" seems to get screwed up on development levels for ATI, nvidia, intel, ... on Intrepid, Jaunty, Karmic, Lucid, and whatever's coming up next I assume.  It's probable that upstream Debian has the same or similar bugs but I don't have a development level Debian to compare to.

At the moment I can't get the A2 CD to boot at all on this intel i845G.  2.6.32-10 is running with "nomodeset" in the linux boot line and "vesa" in xorg.conf....

Vesa and nomodeset don't do much for development testing; I'll try default when/if the daily build CD will boot.  It's still at A2 level which doesn't as in the release notes.

Jerry

---

### Post by ranch hand on 2010-01-15
I am one of the folks on that bug.  I do not think it has anything to do with your problem.

It occures when you shut the Live session down.  You get the plymouth logo on black background and then it stops and hangs, no message to remove CD and hit enter, CD does not eject.

On mine the CD did eject but the rest was the same.  Had to do an Alt + sysRq +b to get out of it.

---

### Post by Ibidem on 2010-01-15
No, it doesn't look *anything* like an X bug, and it is not "black screen".
It almost sounds like the scripts are calling shutdown -H where the standard is closer to shutdown -P.
(Shutdown -P is standard and powers off the computer; shutdown -H halts Linux, but does not power off the system, kind of like Windows 95's "It is now safe to turn off your computer").

Jerry, I would think that your problem is that the i845 driver in xserver-xorg-video-intel is not working or that KMS support is incompatible with that card.  i915 is currently working, I can confirm.  So if you want to check, you might see about adding back the Intel driver, while keeping nomodeset, or even setting the system to boot to command line, logging in, and running "startx".  The latter method lets you know if the problem is related to X; if you get the black screen, power off, reboot, disable the Intel driver, start X, and finish cleaning up.

Ibidem

---

### Post by TKbuntu on 2010-01-16
Hi Jerry,  just a note to say I used the cmd line per your suggestions, and X now works again.  Thank you for such a good tip :)  Regards,  Tony

---

### Post by jerrylamos on 2010-01-17
A2 CD live won't boot on my i845G video graphics no way.

A1 updated to A2 level screen freezes quickly unless I specify "nomodeset" in the linux boot line and have an xorg.conf specifying "vesa".  That way it runs for a couple hours anyway.

Alternate A2 installed fine and runs for a good while.  Did freeze when I attempted to open a CD.

Hmmmm.

Jerry

---

### Post by Ibidem on 2010-01-17
What sort of CD drive? IDE, SATA, or SCSI?
Sounds like a trapper's box--catch the Lynx on anything.
If it's SCSI, that's no surprise...but still a bug.

Ibidem

---

### Post by stink on 2010-01-18
jerrylamos,

This bug is probably causing your X freezes:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/456902)

It's a problem in Karmic, too.  A fix is getting close.


> **jerrylamos said:**
> A2 CD live won't boot on my i845G video graphics no way.

A1 updated to A2 level screen freezes quickly unless I specify "nomodeset" in the linux boot line and have an xorg.conf specifying "vesa".  That way it runs for a couple hours anyway.

Alternate A2 installed fine and runs for a good while.  Did freeze when I attempted to open a CD.

Hmmmm.

Jerry

---

