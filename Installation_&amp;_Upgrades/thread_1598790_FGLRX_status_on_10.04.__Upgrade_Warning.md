---
title: "FGLRX status on 10.04.  Upgrade Warning"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by hell_rider on 2010-10-17
Hello all,

I am a bit behind the rest of you guys who are already onto to 10.10.

I am running 8.04 on a Toshiba Satellite A100 laptop. (My Toshiba model is unfortunately the one with the Phoenux BIOS)

I have been happy with 8.04 LTS for quite some time now and was thinking of upgrading to 10.04 LTS, which the Update Manager says is available.  I normally choose to upgrade a few months after release once things have stabilised a bit.  I figured it was now time for 10.04.

I accordingly have first taken all the updates for 8.04 and brought it up-to-date.  

Then when I click on Upgrade, I get the following message

[INDENT][I]Upgrading may reduce desktop effects and performance in games and other graphically intensive programs.

This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware
in Ubuntu 10.04 LTS.

Do you want to continue ?[/I][/INDENT]

Since I wasn't sure of the exact entire implications, I said NO and exit the upgrade at that point.

I then googled a bit and found this to be a pretty serious installation issue with a number of people who unfortunately have ATI display cards.

But then I came across this page:
[http://www.webupd8.org/2010/09/fglrx-finally-works-with-ubuntu-1010.html](http://www.webupd8.org/2010/09/fglrx-finally-works-with-ubuntu-1010.html)

Does the above link mean that this problem is now solved with respect to 10.04 as well ?

Also, if not, what are the implications for me ?  
[LIST=1]
[*]Does this mean I have to be stuck on 8.04 only ?  
[*]If I choose to upgrade anyway, what display functionality will I lose ?
[*]I don't need Desktop Effects or other toys.  But I do use GIMP quite a bit and also watch videos in multiple formats.  Will I not be able to do these ?
[/LIST]

Kindly advise.

Thanks and Regards.

---

### Post by mörgæs on 2010-10-17
Good to see that you are investigating the new version before installing. If only more people would do that...

8.04 is supported half a year more, so you are not in a hurry to do anything. 

There is no development in 10.04 and 10.10, 'only' bug fixes, so there will not be FGLRX support added to 10.04. The development version is 11.04. 

I would wait a month or two and then go for a clean install of 10.10.

---

### Post by hell_rider on 2010-10-17
Morgaes,

Many thanks for your response.

I also wanted to know what exactly will stop working if I go for the upgrade.  

As it is, in my current setup with 8.04, compiz, desktop effects etc. does not work.  I also don't do any gaming on my laptop that requires me to be concerned with blazing fast frame rates etc.

The only video/graphic intensive tasks I perform on my laptop are working on GIMP and watching videos in different formats using VLC player.

Will I not be able to do even these two tasks if I upgrade to 10.04 ??  I just need to know what are the implications of going in for 10.04 with respect to graphics problems.

If GIMP and video will work fine, then I am happy as I am not really big on compiz, Desktop effects etc (they anyway don't work now)

Kindly advise.

Thanks and Regards.

---

### Post by mörgæs on 2010-10-17
It is hard to answer these questions exactly. I can not say whether or not the videos will stutter or run smoothly, for example. GIMP is light on the graphics card because one is only dealing with still pictures (not video), so no problem here.

 A brief googling indicates that the Satellite 100 has 512 MB memory from birth. If this is still the case for your machine, you will not get Compiz running in any release (but this does not seem to bother you, so no harm there).

It does not sound like you have any problems with 8.04 except support running out next year, so I can not give other advice than before: I would wait a month or two and then go for a clean install of 10.10.

---

### Post by Mark Phelps on 2010-10-17
Didn't notice what ATI card you have, but the warning implies that it is no longer supported with fglrx drivers.

If you upgrade in place, with the current fglrx drivers installed, you will likely lose desktop graphics entirely and be relegated to a command line.  You probably do NOT want that result.

So, the best thing to do is to remove the fglrx drivers BEFORE the upgrade, that way, you will still get a graphical desktop after upgrade.

Also, AMD dropped fglrx support for your card a long time ago.  There are no fglrx drivers for it ... and there are not going to be any in the future.

---

### Post by hell_rider on 2010-10-17
Morgaes and Mark,

Thanks for your responses.

Morgaes.  I have upgraded my laptop to 1GB of RAM.  Insufficient RAM is possibly not the reason why compiz is not working on my laptop. In any case, like I mentioned before that is not a primary concern.

Mark,
I checked the Xorg.log
It reports:
[INDENT][B]ATI Technologies Inc M52 [Mobility Radeon X1300] rev 0
fglrx(0): Chipset: "ATI Mobility Radeon X1300" (Chipset = 0x7149)[/B][/INDENT]

Your summation of the situation is a bit scary.  My laptop is *relatively* new.  It is a Centrino Duo.  That it would already be outdated / obsolete with respect to hardware support seems a bit scary, especially considering that one of the much touted features of Linux as per its proponents seems to be great support for older hardware.

In any case, coming to the options you have outlined:
[LIST=1]
[*]If I disable the fglrx drivers before I upgrade, would I not lose the graphics capability immediately ??  Or will I still have rudimentary graphical desktop facilities ?
[*]And when you say I "will still get a graphical desktop after upgrade" (after uninstalling the fglrx drivers before the upgrade) will this be a functional desktop in terms of what I am having now ??? Will Gnome / KDE, GIMP, VLC media player etc work ???
[/LIST]

Also, purely out of curiosity, I am not having compiz, Desktop effects etc. any way now.  What happens if I uninstall fglrx at this point ?? Will my Gnome desktop work ??

Would appreciate some advise on the above queries.

Thanks once again.

Best Regards.

---

### Post by mörgæs on 2010-10-17
> **Mark Phelps said:**
> and there are not going to be any in the future.

Now I don't get it. Didn't the link in the first post indicate that FGLRX works in 10.10 (or am I misunderstanding something here)?

---

### Post by hell_rider on 2010-10-18
Yeah,

That threw me too.  

Also, I checked out the latest PCLinuxOS website.  They clearly state they have the fglrx driver working for ATI.

So it looks like wait n watch at the moment.

---

### Post by Mark Phelps on 2010-10-18
> **mörgæs said:**
> Now I don't get it. Didn't the link in the first post indicate that FGLRX works in 10.10 (or am I misunderstanding something here)?

The fglrx driver does NOT work in any Ubuntu release newer than 8.10 for what AMD/ATI term "legacy" cards -- of which the op's card is one.

In stark contrast, the existing fglrx drivers DID work in Ubuntu 8.04 -- which is why the op was able to install and use them.

AMD/ATI completely dropped fglrx support for their "legacy" cards a long time ago.  The new drivers will NOT work with those cards.

---

### Post by Mark Phelps on 2010-10-18
> **hell_rider said:**
> Also, I checked out the latest PCLinuxOS website.  They clearly state they have the fglrx driver working for ATI.

There have been a LOT of reported problems using 10.10 and fglrx drivers.  Some folks have been able to work around those by installing patched drivers from a ppa.

But these drivers still only work for the "newer" ATI cards.  They do NOT work for the "legacy" cards.

Perhaps what PC Linux OS is referring to is a patched version of the new AMD fglrx drivers that work properly now -- without having to incorporate the drivers from the ppa.

Also, your Centrino chipset has nothing to do with the video; it's the "legacy" ATI chipset that is the problem.

---

### Post by hell_rider on 2010-10-19
Thanks Mark.

Things are a little clearer now. 

Though I am a bit pissed off with my combination of Toshiba and ATI, both causing their own set of issues.  (My Toshiba happens to be one with the unfortunate Phoenix BIOS).

Well, lesson learned.

I will be doing some more googling and coming up with a new set of questions though :-)

Thanks all once again for your responses.

---

### Post by hell_rider on 2010-10-20
Just to update you guys.

I provided you incorrect information in my earlier post(s).

Compiz / Desktop Effects work perfectly on my laptop :-)

I was just curious and was looking around the Help in the forums and found this page :
[https://help.ubuntu.com/community/RadeonXpress](https://help.ubuntu.com/community/RadeonXpress)

I just followed the instructions at the end of that page (i.e. using fglrx) and one instruction from earlier in the page i.e.
```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

Following this all the Desktop Effects functionality works fine.  

But I've actually kept it turned off.  Not too impressed to be honest.  I'm happy with my simple and sober Gnome Desktop.  But its nice to know that it works.

Thanks all once again.

---

