---
title: "ATI X1250 - Jaunty (9.04)"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hblaw on 2009-04-12
Anyone got a working proprietary driver for the card? The xorg-driver-fglrx does not work for me. Thanks.

---

### Post by schmidtbag on 2009-04-13
only ati is allowed to work on proprietary drivers, and they simply will not make them for older cards.  if you can't find it on their website you won't ever find it, but that card should be new enough for you to get a good driver for it

---

### Post by hblaw on 2009-04-13
Yes. 8.10 has the proprietary driver. But 9.04 does not. I don't know what's the issue. Is it due to the X.org upgrade? Or kernel upgrade? Or anything else? Is it possible to hold back all packages affecting the driver at 8.10 and upgrade other components to 9.04? Thanks.

---

### Post by schmidtbag on 2009-04-13
i'm 90% sure its xorg, so just download the drivers from the site and maybe you'll be ok.  what you can do regarding your other question, is install 8.10 and download from the intrepid sources for updates.  i'm not entirely sure how safe that is but as far as i know its a smooth transition

---

### Post by hblaw on 2009-04-14
OK. If it is Xorg, then the development team should be able to fix it. I'll just wait, then. The free driver is not excellenet, but is tolerable for temporary use.

---

### Post by night-wing on 2009-04-14
I have the same problem.

But ati said, that they cancelled their support für this card. There will be no proprietary drivers for jaunty for this card!

---

### Post by baizon on 2009-04-14
> **night-wing said:**
> I have the same problem.

But ati said, that they cancelled their support für this card. There will be no proprietary drivers for jaunty for this card!

OMG! Why? I just made an upgrade to 9.04 and no proprietary drivers where detected :-( ... damn it.

Edit: Where did you read that they stopped supporting that card?

---

### Post by hblaw on 2009-04-14
ATI said they will discontinue support for older cards. But those "older" cards are really old, right? Not cards like X1250 I think. 

It probably is just a problem of compatibility between Xorg and the driver. The development team may be able to tweak their codes a little bit to solve this issue. There should not be architectural / fundamental change to Xorg for 9.04. Right?

I am wondering why the developers cannot design the driver framework to insulate the proprietary drivers. (I.e. is it possible to change other codes while keeping the proprietary drivers useable?) :)

---

### Post by markbuntu on 2009-04-14
Ati has dropped the RV200-RV500 cards from their linux and windows drivers starting with Catalyst 9.4. This is any card before the HD3xxx series. Drivers before 9.4 will not work with the new xserver in Jaunty.

Sooo, if you have a card before HD3xxx series there is no proprietary driver for you in Jaunty and never will be. But, the open source ati and radeon drivers work very well for those cards.

---

### Post by Woody1987 on 2009-04-14
no support for any card below the 2000 series in the proprietary driver. Use the open sauce ones. i recommend the radeonhd for you as it has both 2d and 3d accleration on your generation of card.

---

### Post by hblaw on 2009-04-15
What do you mean "Below 2000". Please be specific. Is ATI supporting X1250 or not?

---

### Post by benmoran on 2009-04-15
> **hblaw said:**
> What do you mean "Below 2000". Please be specific. Is ATI supporting X1250 or not?

The graphics card number and the graphics core numbers are different. Its kind of confusing. Like was said, anything below R5xx series cores has been dropped by ATI. I have an X1150 which has the RS480 core, so i'm out of luck too and my laptop is only 2 years old. 

Personally i'm going to just switch to Jaunty and use the open source drivers. It sucks because they aren't up to the performance levels of the proprietary one in 3D performance, but 2D performance is better. I'm just waiting for powerstate control, which is coming soon to the OS drivers.

---

### Post by barisurum on 2009-04-15
> Like was said, anything below R5xx series cores has been dropped by ATI

I think its wrong. According to what I read in [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1") the support for cards ranging from r300 to r500 core series are dropped. They are r300/r400/r500 series. It means all the x1000 series of cards are put to legacy support category. 

The open source driver is currently behind of fglrx drivers performance-wise. But there is a high hope that the open source driver will be maturized and will match the performance of proprietary ones in the near future. This is because AMD (ati) has released documentations about these older cards that allows a fully featured open source driver possible according to [phoronix]("http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1") again. Nevertheless we will have to wait for some time to have full 3d and compositing.

---

### Post by benmoran on 2009-04-15
Your right, I worded that wrong.

---

### Post by hblaw on 2009-04-15
OK. Now I get it. ATI has *discontinued* support for X1250. It at the same time has released documentation to enable open source drivers. Currently no driver can match up with the proprietary drivers.

If this is the case, I think I will temporarily discontinue my use of Ubuntu, and wait until the open source driver to catch up. 

[Note to others with X1250 card: please make sure you also understand this - for 9.04, no state of art acceleration for ATI X1250 is available. Either you use an older version of Ubuntu (and probably sacrifice some of the new features), or you use 9.04 and sacrifice some performance.]

---

### Post by markbuntu on 2009-04-15
The open source drivers should be fully functional for all the RV200-500 cards in a few months.

---

### Post by bobnutfield on 2009-04-15
> **markbuntu said:**
> The open source drivers should be fully functional for all the RV200-500 cards in a few months.


Well, I am certainly glad I read this thread.  I was about to upgrade my Toshiba laptop to Jaunty from Intrepid.  This laptop is exactly one year old and has an integrated X1250 mobility radeon chipset.  If there is going to be no prop. drivers for it any more, I will stick with Intrepid.  This really bad news for those of us with this chipset.  And a bit of a ripoff from AMD as well since there are still NEW laptops being sold with this chipset.

---

### Post by Trespasser on 2009-04-15
I've got an Ati Radeon X1650 so I'm in the same boat. Hopefully this situation will improve in short order...but this truly does suck. Thumbs down to ATI for abandoning us.

Question to anyone who might know...can we down grade xorg so that we can use a recent Ati driver?

Later...

---

### Post by 0vermind on 2009-04-15
WTF?! My laptop has an ATI x1250 graphics card in it, and it's only a few months old. 

Well, I'm screwed now. I can't even get into Ubuntu and I have important data and settings on there (not just files). I tried force installing the ATI drivers the (X1300 series, because the X1200 series wasn't listed and I was told that X1300 supported X1250). So I force install these drivers by using the deb packages, and now my system won't boot. It boots fine then it goes to a black screen with colorful lines up at the top, and it freezes there. I have to hold down the power button to get it to turn off.

Any ideas on how to fix this?

Thanks!

Michael

---

### Post by crjackson on 2009-04-15
Okay, lets not get all upset over this. I have 3 machines I must run with Hardy because of ATI issues. If I were a windows guy, I would be stuck on XP because Vista / Windows 7 have no drivers for these video cards either. At least with the opensource drives, there is hope that I can run the latest/greatest Ubuntu OS at full speed in a few months.

Having said that. There's nothing wrong with Hardy. You can still update you software packages (MOST of them) to the same version level as Jaunty. I wish too that I could run jaunty with full speed video but it's no insult to run Hardy (which is still current and VERY stable) to get the performance I want.

---

### Post by hblaw on 2009-04-15
> **0vermind said:**
> 
Any ideas on how to fix this?


I tried exactly the same thing as you did (and with similar result). The way out is to boot in safe mode into the system and choose "Drop me to command line as root" when asked. Then "apt-get remove --purge xorg-driver-fglrx (or whatever other driver you installed)"

Thanks.

---

### Post by benmoran on 2009-04-15
You pretty much hit the nail on the head, crjackson. 

Intrepid works perfect for me with the 9.3 proprietary drivers, and does everything I want. There is no reason to switch to Jaunty right now, though just like most people I really want to. I can hold off with Intrepid until they open source drivers get powerstate support, then switch to Jaunty. It's being worked on. 

Windows users have it worse than Linux users right now. They will never have drivers for newer windows versions. We are&#12288;pretty much future-safe with the open source drivers. They aren't quite there now, but good on ATI for releasing docs.

---

### Post by 0vermind on 2009-04-15
> **hblaw said:**
> I tried exactly the same thing as you did (and with similar result). The way out is to boot in safe mode into the system and choose "Drop me to command line as root" when asked. Then "apt-get remove --purge xorg-driver-fglrx (or whatever other driver you installed)"

Thanks.

Okay that all worked, I'm back into Jaunty again. However, I am back to square one I was a few hours ago. I would be fine with the opensource radeon drivers except that my laptop screen flickers when ever I do something like Compiz, games, etc. It's really really annoying.

What do I do about this? Can I downgrade the xserver and xorg and keep the rest of Januty? I really would perfer not to reformat, it took me hours to configure Ubuntu the way I like it.

[I]Oh and on a side note, Windows Vista and Windows 7 both have ATI drivers that work perfectly with Radeon X1250 (X1200 and X1300 series both have Windows Vista/7 drivers). Just go to the ATI Website and download 'em.
[/I]



**EDIT:** Okay I guess I just don't understand. Up on the ATI Website there are drivers for ATI X1250, it's the xpress x1250 if that matters (I don't think it does), but there are 32-bit and 64-bit drivers. So if ATI has the drivers up, why won't they work on Janunty? [Here is the driver page.]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English")

Thanks!

-Michael

---

### Post by hblaw on 2009-04-15
They don't work because they (9.3 drivers) only work with the older version of Xorg (i.e. the version in Ubuntu 8.10). The programmers of Xorg could not hold the interface for proprietary drivers constant while they add other features. And the proprietary drivers don't work for new Xorg any more. Then ATI discontinued support which means they won't make new proprietary drivers for the new Xorg. That's what happened.

The question I asked above (on the first page) is on this point. Why could not the developers hold the interface constant. I guess this is technologically impossible (based on the current system structure). But I am not sure.

Thanks.

---

### Post by crjackson on 2009-04-15
> **0vermind said:**
> [I]Oh and on a side note, Windows Vista and Windows 7 both have ATI drivers that work perfectly with Radeon X1250 (X1200 and X1300 series both have Windows Vista/7 drivers). Just go to the ATI Website and download 'em.
[/I]

Overmind,

I think you are refering to my post where I said:
> I have 3 machines I must run with Hardy because of ATI issues. If I were a windows guy, I would be stuck on XP because Vista / Windows 7 have no drivers for these video cards either. At least with the opensource drives, there is hope that I can run the latest/greatest Ubuntu OS at full speed in a few months. 

If you WERE refering to that post, please re-read. I said that I have 3 machines with ATI cards that are unsupported beyond XP for microsoft OS's. I didn't say I have 3 machines with ATIX1250 video cards. I don't own that card at all. I own other unsupported ATI cards.

---

### Post by hblaw on 2009-04-15
> **0vermind said:**
> Okay that all worked, I'm back into Jaunty again. However, I am back to square one I was a few hours ago.

As mentioned above in an earlier post, you may try radeonhd driver. The package name is xorg-driver-radeonhd or something similar. For me it is a little better than the default driver. I use skype. The video flicks very often (every time my mouse is over a button, opens a menu, etc) under the default driver. But the radeonhd driver does not have this problem. You can enable *normal* visual effects without problem. If you want to continue using 9.04, this may be a compromise.

---

### Post by barisurum on 2009-04-16
> I've got an Ati Radeon X1650 so I'm in the same boat. Hopefully this situation will improve in short order...but this truly does suck. Thumbs down to ATI for abandoning us.

I have the same card and I'm dissapointed too. But if the driver will go open source and if they make it match the fglrx performance then I'll be more than happy. 

It is way much better than having a binary code (fglrx) incompatible with the kernel to screw up your system. "It works great!" but after a system update (kernel, xorg) "Ooooh I see a black screen of death". This is because ati doesn't have (and probably will never have) enough linux specialist computer scientists, who understand every corner of the linux kernel and who can make a decent driver work for every kernel and xorg update.

So ati says:

I will drop the support for x1000 series. Windows drivers are mature and will work with any game or application without errors anyway. And I release these documents to linux developers to help them help themselves and encourage them to build an open source driver based on these.

Recently I read an article in phoronix about a benchmark test between open source radeon drivers and fglrx proprietary ones:

[Here it is]("http://global.phoronix-test-suite.com/?k=profile&u=michael-1567-17468-20293")

Strange isn't it? Look at the unreal tournament test. Open source driver outperforms the fglrx one. So fglrx is not perfect and probably will never be. Will the open source driver take the place of fglrx? I don't know, we will wait and see.

---

### Post by TwiStEr55 on 2009-04-16
So ATI really has dropped support for the x1250 for linux ???

Sorry to be the first to say this out loud, BUT WTF?????

its a fairly new card, which is till being sold in new laptops ....... how in their right minds can they drop support for it????

Yeah they gave out the specifications, but there will be a long period until a working/stable open driver is out .... 


Im not a particular fan of closed source, but I want my hardware to run with advertised features and performance and not lose support for it after a year ....

Its like NVIDIA saying they wont support the 8000 series anymore .....

( I know, nobody HERE is to blame, but this really causes a little rage in me ... sry )

---

### Post by TwiStEr55 on 2009-04-16
Ok .. I want to soften my previous anweser a little.

I wanted to see formyself and downloaded the current alternate installer (04/14/09) and just installed it ... 

It doesnt detect any prop. drivers in Hardware Drivers. 

BUT .... compiz works fine :) .... everything works as of now flawlessly ...

so much for the long waiting period .... conclusion Open Source rulez! :P


Edit: And I might add its way smoother than before ... WOW ... jaunty rules!

---

### Post by zika on 2009-04-16
> **TwiStEr55 said:**
> Ok .. I want to soften my previous anweser a little.
I wanted to see formyself and downloaded the current alternate installer (04/14/09) and just installed it ... 
It doesnt detect any prop. drivers in Hardware Drivers. 
BUT .... compiz works fine :) .... everything works as of now flawlessly ...
so much for the long waiting period .... conclusion Open Source rulez! :P
Edit: And I might add its way smoother than before ... WOW ... jaunty rules!
I'm going on vacation and I hope when I come back (030509) I will be able to try compiz again after quite a time ... :) (HD3650 open-source driver) ... :)
keep the pressure on ... :)

---

### Post by Lorenz on 2009-04-16
I was a bit panicky as well, BUT the open source drivers actually work like a charm and better than the ATI ones. At least for Compiz, video, scrolling - dunno about 3D stuff, don't use any luckily!

---

### Post by baizon on 2009-04-16
> **Lorenz said:**
> I was a bit panicky as well, BUT the open source drivers actually work like a charm and better than the ATI ones. At least for Compiz, video, scrolling - dunno about 3D stuff, don't use any luckily!

You're right. At the beginning I've overreacted a little bit. But after the last "update" the Xorg driver works well with my X1250.

---

### Post by 0vermind on 2009-04-16
Gosh dang it! Okay now I have a new problem. I just tried to boot into Ubuntu today and I keep getting these kinds of errors:

```

/usr/bin/startx: lind 168: Permission Denied.
/usr/bin/startx: line 170: cannot create temp file for here document: Read-only file system.

X:warning; process set to priority -1 instead of requested priority 0.

Fatal server error:
Could not create lock file in /tmp/.TX0-lock

xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/michael/.Xauthority

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or stat file could not be parsed or opened
```

This problem looks like something to do with permissions, possibly a read-only marked file system. However, last night I was able to boot in just fine. I hadn't changed anything since then. So I don't know how this happened, I think the drivers messed something up though.

I tried to run fsck and it said that that system is marked as clean. :S

Any ideas anyone?

Thanks!!

Michael

**EDIT:** I just wiped the whole thing and started over.....

---

### Post by hblaw on 2009-04-16
> **baizon said:**
> You're right. At the beginning I've overreacted a little bit. But after the last "update" the Xorg driver works well with my X1250.

For me it is different. The open source driver works out of the box but there are a few issues (with Skype, especially). In addition, the screen would sometimes shake briefly (i.e. flick)(I don't know why). I am not sure whether you have the same problems before and the updated Xorg resolved this, or you just ignore this kind of glitches. :)

However, like I said, the radeonhd works and is a compromise good enough for the interim.

---

### Post by Lorenz on 2009-04-16
> **0vermind said:**
> Gosh dang it! Okay now I have a new problem. I just tried to boot into Ubuntu today and I keep getting these kinds of errors:

```

/usr/bin/startx: lind 168: Permission Denied.
/usr/bin/startx: line 170: cannot create temp file for here document: Read-only file system.

X:warning; process set to priority -1 instead of requested priority 0.

Fatal server error:
Could not create lock file in /tmp/.TX0-lock

xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/michael/.Xauthority

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or stat file could not be parsed or opened
```

This problem looks like something to do with permissions, possibly a read-only marked file system. However, last night I was able to boot in just fine. I hadn't changed anything since then. So I don't know how this happened, I think the drivers messed something up though.

I tried to run fsck and it said that that system is marked as clean. :S

Any ideas anyone?

Thanks!!

Michael

**EDIT:** Screw this. I'm outta here. Everytime I go back into Ubuntu or install it, thinking things have been fixed, problems arise. Now I've lost settings and data that I don't think I'll ever get back, because the bull s**t operating system keeps locking down the filesystem as read-only causing the stupid thing to drop me to the console. What kind operating system does stupid crap like that?

Sorry, but why do you use Beta software then??

---

### Post by 0vermind on 2009-04-16
Actually, I just wiped the entire thing and started over. Sorry for getting so upset.

Now I'm wondering if anyone  can  tell  me  how  to get  the  RadeonHD drivers on here that would be great!


-Mike

---

### Post by crjackson on 2009-04-16
> **0vermind said:**
> Sorry for getting so upset.-Mike

It happens Mike - We've all been there (with CP/M, OS/2, WIn (every version), and Linux. Errors and frustration are OS / Platform independent.

About the permissions thing - This usually happens when you run a program (that you shouldn't) with root permissions. Root steal's YOUR permissions. Also, because this is BETA software - It's more likely to self-destruct on it's own than a stable version.  Even though Jaunty is due to be released in a week and will be considered stable, it will be working out hundreds of bugs over the next few weeks. I don't normally switch my production machines until 8 weeks after a release.

For me... Intrepid is just NOW becoming stable, and only HARDY is acceptable for my laptops.

---

### Post by screaminj3sus on 2009-04-17
> **Woody1987 said:**
> no support for any card below the 2000 series in the proprietary driver. Use the open sauce ones. i recommend the radeonhd for you as it has both 2d and 3d accleration on your generation of card.

What about the mobility 2000 series, are those supported?

---

### Post by danwood76 on 2009-04-17
> **crjackson said:**
> 
For me... Intrepid is just NOW becoming stable, and only HARDY is acceptable for my laptops.

For me jaunty has been stable for months :)

The open source ATI drivers are better than fglrx in my opinion (at least for my X1950pro).

The reason that fglrx doesn't work with later xrorg versions than the one it was built on is the fact that the open source drivers can be recompiled for new xorg versions (normally with no changes as they have been written nicely) whereas fglrx has binary blobs for each xorg version so if a new version comes out bang go the drivers.

---

### Post by 0vermind on 2009-04-17
So can anyone point me in the right direction on how I can get those RadeonHD drivers on my Jaunty?


Thanks!

-Mike

---

### Post by markbuntu on 2009-04-17
radeonhd is in the repos.

---

### Post by krazyd on 2009-04-17
Just a note to those concerned about AMD "dropping" linux support for X1xxx cards and older - they haven't.

They are simply moving 'older' cards from a closed source driver to an open source driver, and providing all the documentation so that it's possible to bring full acceleration to linux. They employ at least one developer working full time on it, though it's open source so anyone can hack on it ;). Here's his blog: [http://www.botchco.com/agd5f/](http://www.botchco.com/agd5f/)

Also, initial 3D support for the latest cards, that is HD2xxx - HD4xxx was just pushed to the public repo. So I'm sure there'll be a PPA you can use soon to get binary-blob-free 3D on the latest ATI hardware! Certainly, 9.10 should have this support out-of-the-box. :D

---

### Post by hblaw on 2009-04-18
Dropping support is the current state. Full acceleration open source driver is months away. We must accept the reality. hihi

---

### Post by krazyd on 2009-04-18
> **hblaw said:**
> Dropping support is the current state. Full acceleration open source driver is months away. We must accept the reality. hihi

Full acceleration is available in open source for R5xx and older. For R6xx, R7xx, there is fglrx which works in Jaunty.

---

### Post by barisurum on 2009-04-18
> [COLOR="Red"]Full acceleration[/COLOR] is available in open source for R5xx and older. 

How can we confirm this? Can you provide a link?

---

### Post by danwood76 on 2009-04-18
I have full acceleration on my x1950.
Video playback is very smooth occasional vsync issue (fglrx had the same) and 3d games seem to work just fine (though some dont seem to like my screen setup) but I dont do much gaming.

Thing to do is install jaunty and have a play.

---

### Post by 0vermind on 2009-04-18
> **krazyd said:**
> Just a note to those concerned about AMD "dropping" linux support for X1xxx cards and older - they haven't.

They are simply moving 'older' cards from a closed source driver to an open source driver, and providing all the documentation so that it's possible to bring full acceleration to linux. They employ at least one developer working full time on it, though it's open source so anyone can hack on it ;). Here's his blog: [http://www.botchco.com/agd5f/](http://www.botchco.com/agd5f/)

So wait... you're saying there is still hope? For those of us who have cards like the ATI X1250 still have hope with Jaunty? 


-Michael

---

### Post by minimec on 2009-04-18
Hi

Just saw that thread and gave it a try with the 9.04rc live ...

The OpenSource driver is not able to display 1680x1050 with my x1250. I will stay on Intrepid and Debian/Lenny until the OpenSource driver catches up.

---

### Post by danwood76 on 2009-04-18
I have a desktop area of 3200 x 1080 on the open source driver? (I do have a different card but its the same generation)
The problem with the live CD is that you cant change the virtual resolution for the driver so the desktop area is limited.

---

### Post by minimec on 2009-04-18
@danwood76

Hmmm... 

So you say that I would have the possibility to adjust screen resolution after install? With a GUI or with 'SubSection "Display"' in xorg.conf?

I have no idea of this xorg 1.6 thing ;)

greets minimec

---

### Post by 0vermind on 2009-04-18
> **markbuntu said:**
> radeonhd is in the repos.

I installed it and restarted my system and nothing changed. I have no idea if it is using the driver or not, but the screen still flickers a lot.

when I install the driver, do I have to tell the system to use it or something?



-Michael

---

### Post by inportb on 2009-04-18
> **hblaw said:**
> If this is the case, I think I will temporarily discontinue my use of Ubuntu, and wait until the open source driver to catch up.

Nice, so what distro will you use?

---

### Post by Spydr4590 on 2009-04-18
Here is the list of cards affected.

AMD has moved a number of DX9 ATI Radeon&#8482; graphics accelerators products to a legacy driver support structure.  This change impacts Windows XP, Windows Vista, and Linux distributions.  AMD has moved to a legacy software support structure for these graphics accelerator products in an effort to better focus development resources on future products.

The following products have been moved to the legacy software support structure (including Mobile and All-in-Wonder Variants):

ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series


AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.

Any customers using a combination of a ATI Radeon&#8482; HD 2000 Series, ATI Radeon&#8482; HD 3000 Series, or ATI Radeon&#8482; HD 4000 Series product with any of the legacy products listed above in a single PC system must use the ATI Catalyst 9.3 or earlier driver.   All future ATI Catalyst&#8482; releases made available past the ATI Catalyst&#8482; 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

---

### Post by danwood76 on 2009-04-18
> **minimec said:**
> @danwood76

Hmmm... 

So you say that I would have the possibility to adjust screen resolution after install? With a GUI or with 'SubSection "Display"' in xorg.conf?

I have no idea of this xorg 1.6 thing ;)

greets minimec

All that's needed is a larger virtual display, which is set in the xorg.conf.
Then you can adjust the resolution using the control panel.

---

### Post by krazyd on 2009-04-18
> **barisurum said:**
> How can we confirm this? Can you provide a link?> **0vermind said:**
> So wait... you're saying there is still hope? For those of us who have cards like the ATI X1250 still have hope with Jaunty?Well, my X1600 has had 3D out of the box with Kubuntu since Intrepid. See here: [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)
> **minimec said:**
> Hi

Just saw that thread and gave it a try with the 9.04rc live ...

The OpenSource driver is not able to display 1680x1050 with my x1250. I will stay on Intrepid and Debian/Lenny until the OpenSource driver catches up.
Please file a bug about this on launchpad (sounds like a packaging / configuration issue).

---

### Post by hblaw on 2009-04-19
> **krazyd said:**
> Full acceleration is available in open source for R5xx and older. For R6xx, R7xx, there is fglrx which works in Jaunty.

Full acceleration is NOT available in open source for X1250. There is NO fglrx for X1250 which works in Jaunty. That's the current state. 

If you have solution to either, please post the steps. Thanks.

---

### Post by krazyd on 2009-04-19
X1250 (RS690) should have open source acceleration: [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

If not, please file bugs and post links to them so others can add info.

---

### Post by minimec on 2009-04-19
> **danwood76 said:**
> The problem with the live CD is that you cant change the virtual resolution for the driver so the desktop area is limited.

I cannot confirm that. It is possible to modify and restart the X-Server while running the Live CD

> **danwood76 said:**
> All that's needed is a larger virtual display, which is set in the xorg.conf.
Then you can adjust the resolution using the control panel.

I was indeed able to get a 1680x1050 screen (including 3D acceleration) with the OpenSource driver, but the screen gets somehow 'nervous'. It's not a flickering... it's a 'nervous' screen. I don't know how to say that. 

Modifications in xorg.conf (Section "screen")

# I added the fallowing...

[INDENT]Subsection "Display"[/INDENT]
[INDENT][INDENT]Modes   "1680x1050"[/INDENT][/INDENT]
[INDENT][INDENT]Virtual 1680 1050[/INDENT][/INDENT]
[INDENT]EndSubSection[/INDENT]


> **krazyd said:**
> Please file a bug about this on launchpad (sounds like a packaging / configuration issue).

I don't know if this is a software bug. I'd rather say that the ATI X1250 itself is a bug(!!!), and all Linux ATI users are Zen masters.

---

### Post by hblaw on 2009-04-19
> **krazyd said:**
> X1250 (RS690) should have open source acceleration: [http://wiki.x.org/wiki/RadeonFeature](http://wiki.x.org/wiki/RadeonFeature)

If not, please file bugs and post links to them so others can add info.

Please note, "have acceleration" and "matching the speed of proprietary driver" are two different things. Yes there is a useable open source driver, but no, it is way slower.

---

### Post by danwood76 on 2009-04-19
The speed isnt that different on my card.
You get less fps but the fps is still way higher than my eyes could notice.

---

### Post by barisurum on 2009-04-20
> The speed isnt that different on my card.
You get less fps but the fps is still way higher than my eyes could notice.

Now that I've been testing jaunty for some time, I will confirm this. Compiz works like charm. Direct rendering is available if I don't use compiz and glxgears give me about 4500 fps which is half of the fglrx but not that bad. When using compiz glxinfo says direct rendering: no but glxgears gives about 3200 fps which is still acceptable.

edit: is there a way to fix this direct rendering no problem with compiz? glxinfo says direct rendering: No (LIBGL_ALWAYS_INDIRECT set). When I disable compiz it says yes. 

my specs:

AMD K8 dual core 2.8 ghz
4gb of 800 mhz ram
Ati X1650XT with 256mb ddr3 ram

---

### Post by hblaw on 2009-04-20
On mine, it is in the per second 300 range.

The screen flicks here and there. Rolling the screen in firefox is slow (lagging sometimes). I have turned off the visual effects.

In addition, if all the specs are disclosed to the community, what a "full speed" driver means is one that makes the card as fast as it is in Windows (i.e. working without glitch), not just comparable to fglrx (which I doubt the ATI people have spent much time on). [I am fine if it is at least comparable to fglrx, though.]

---

### Post by benmoran on 2009-04-20
Personally I never expected the free drivers to reach their current level so fast. I first started using Linux exclusively at Ubuntu 7.10, and fglrx was buggy and SLOOOOW as hell on my Radeon Xpress x1150. It took until 8.04 for them to become stable, and 8.10 for them to become really usable for games. I would say that the current free drivers are already better than my first experience with fglrx. I'm really hyped, and hope that the current development speed keeps up.

---

### Post by neekz on 2009-04-22
Well the open source driver has been more functional for me then flgrx in 8.10 I couldn't get most games to work, it would just a black screen with weird blocks all over the place while the game ran in the background. 

  I get a little flicker is there any way to tweak something to fix that?? Acer Extensa 4420 with a X1250.

---

