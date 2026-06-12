---
title: "Alpha 4 Is Now Available!"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kevpan815 on 2009-08-13
Alpha 4 Is Now Available!

Already Finished Downloading It!

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

---

### Post by Revolutionary101 on 2009-08-13
That is awesome!!

---

### Post by MadsRH on 2009-08-13
And there's already a review: 

[http://news.softpedia.com/news/Ubuntu-9-10-Alpha-4-Has-Firefox-3-5-as-Default-Browser-119118.shtml](http://news.softpedia.com/news/Ubuntu-9-10-Alpha-4-Has-Firefox-3-5-as-Default-Browser-119118.shtml)

:)

---

### Post by AlanR8 on 2009-08-13
Running a fully patched Alpha 3, will it update to Alpha 4 with sudo apt-get dist-upgrade? Or will I have to download and reinstall?

---

### Post by slakkie on 2009-08-13
Not a lot of packages for me with the upgrade:

eog gnome-session gnome-session-bin libpango1.0-0 libpango1.0-0-dbg libpango1.0-common

---

### Post by wayne_cat on 2009-08-13
edit sorry ... double post

---

### Post by wayne_cat on 2009-08-13
> **AlanR8 said:**
> Running a fully patched Alpha 3, will it update to Alpha 4 with sudo apt-get dist-upgrade? Or will I have to download and reinstall?

alpha 3 + all update = alpha 4

---

### Post by kevpan815 on 2009-08-13
> **wayne_cat said:**
> alpha 3 + all update = alpha 4

Not True. If You Clean Install, You Will Get Mozilla Firefox 3.5.2 Instead Of The Current Mozilla Firefox 3.0.13, Just FYI.

---

### Post by wayne_cat on 2009-08-13
> **kevpan815 said:**
> Not True. If You Clean Install, You Will Get Mozilla Firefox 3.5.2 Instead Of The Current Mozilla Firefox 3.0.13, Just FYI.

wrong ... firefox 3.5.2+nobinonly-0ubuntu2 came with dist-upgrade this week

My system started as an Alpha 1

```
root@macbook:~# dpkg -l |grep firefox
ii  firefox                                        3.5.2+nobinonly-0ubuntu2                   meta package for the popular mozilla web bro
ii  firefox-3.5                                    3.5.2+nobinonly-0ubuntu2                   safe and easy web browser from Mozilla
ii  firefox-3.5-branding                           3.5.2+nobinonly-0ubuntu2                   Package that ships the firefox branding
ii  firefox-3.5-gnome-support                      3.5.2+nobinonly-0ubuntu2                   Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support                          3.5.2+nobinonly-0ubuntu2                   meta package pointing to the latest gnome-su
root@macbook:~# 
 
```

---

### Post by kevpan815 on 2009-08-13
The Fact That Your Machine Started Out As An Alpha 1 Means That You Are Missing Some Key New Features such As Grub Boot Loader 2.0, And The Ext 4 File System With Encryption, Just FYI.

---

### Post by psyke83 on 2009-08-13
> **kevpan815 said:**
> The Fact That Your Machine Started Out As An Alpha 1 Means That You Are Missing Some Key New Features such As Grub Boot Loader 2.0, And The Ext 4 File System With Encryption, Just FYI.

Not sure about encryption, but the transition to GRUB2 is pretty easy. If this process isn't automated, you can follow the steps on the [Grub2Testing wiki page]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing").

---

### Post by alphacrucis2 on 2009-08-13
Is this why today's updates were so boring?

---

### Post by wayne_cat on 2009-08-13
> **alphacrucis2 said:**
> Is this why today's updates were so boring?

There was a freeze .. you can see it in some bug reports:

```
the update has not been uploaded due to the alpha freeze being in effect

```at least there was a Tomboy update ... boring? ... yes ... but we could use it for another Mono rant :biggrin:

---

### Post by philinux on 2009-08-13
> **MadsRH said:**
> And there's already a review: 

[http://news.softpedia.com/news/Ubuntu-9-10-Alpha-4-Has-Firefox-3-5-as-Default-Browser-119118.shtml](http://news.softpedia.com/news/Ubuntu-9-10-Alpha-4-Has-Firefox-3-5-as-Default-Browser-119118.shtml)

:)

Not seen the Apps>system tools>disk utility

Very nice.

---

### Post by Luca_turicci on 2009-08-13
TLDR.
 
hey, yesterday installed Alpha 3, and now that Alpha 4 is out, i've been checking for updates every hour, but, do I need to do a clean installation of alpha 4?

---

### Post by andrewabc on 2009-08-13
> **Luca_turicci said:**
> TLDR.
 
hey, yesterday installed Alpha 3, and now that Alpha 4 is out, i've been checking for updates every hour, but, do I need to do a clean installation of alpha 4?

No. If you install alpha 1, 2, 3, 4, 5, 6, beta, RC, you will get updated to final (or whatever new development version before final) when it is out as long as you've kept up to date.

Just make sure to go to system->administration->update manager
And everything will be up to date and you have alpha 4.

We really need a sticky about this question. It seems to get asked daily.

---

### Post by ranch hand on 2009-08-13
> **Luca_turicci said:**
> TLDR.
 
hey, yesterday installed Alpha 3, and now that Alpha 4 is out, i've been checking for updates every hour, but, do I need to do a clean installation of alpha 4?
You will have it with your next update.

It is not completely true that if you update every day you are running the same thing as a new install of the latest.  You have notheng to worry about.

I have been trying to proveto my self that updatindg is a way to stay current.  I have, from clean installs, A1, A2, and A3.  All updated daily.  They do not get identical updates.  A1 is still using grub-legacy although every thing is in place except grub-pc.

I find it very interesting.  They all seem to run alike so I suspect that they will all come out at the same place.

---

### Post by VMC on 2009-08-13
> **philinux said:**
> Not seen the Apps>system tools>disk utility

Very nice.

Yes, very interesting. It test your hard drives. In fact Ferora 11 detected my external usb drive as having a defected sector. I ran the lists listed, but still errors. When I booted Karmic and using the new Disk Utility, It passed.

---

### Post by novafluxx on 2009-08-13
> **andrewabc said:**
> No. If you install alpha 1, 2, 3, 4, 5, 6, beta, RC, you will get updated to final (or whatever new development version before final) when it is out as long as you've kept up to date.

Just make sure to go to system->administration->update manager
And everything will be up to date and you have alpha 4.

We really need a sticky about this question. It seems to get asked daily.

I second this motion, and will co-sign the bill.

---

### Post by keypox on 2009-08-13
So i tried making a usb startup with this iso and it wont work on laptop... worked on all other though.

EDIT nevrmind i formatted and tried agina and it owrked.

---

### Post by running_rabbit07 on 2009-08-13
> **kevpan815 said:**
> Alpha 4 Is Now Available!

Already Finished Downloading It!

[http://cdimage.ubuntu.com/releases/karmic/alpha-4/](http://cdimage.ubuntu.com/releases/karmic/alpha-4/)

Getting that downloaded now.

---

### Post by ranch hand on 2009-08-13
Well out here in the sagebrush things are very slow.  Been at it for a couple hours and am being told thatt ist will be another 5 hours until it is done.

Right now I am getting a blazing 28Kb/s.

Stuff from the repos usually run about 300Kb/s and the A1,2 and 3 went at about 175Kb/s.

I assume this is an indication of trafic at the server level.

Is A4 when a lot of folks jump into the Alpha version?  As you can see from my join date (when I switched to Ubuntu as a complete linux noob) I have little prior experience to go on.

---

### Post by running_rabbit07 on 2009-08-13
> **ranch hand said:**
> Well out here in the sagebrush things are very slow.  Been at it for a couple hours and am being told thatt ist will be another 5 hours until it is done.

Right now I am getting a blazing 28Kb/s.

Stuff from the repos usually run about 300Kb/s and the A1,2 and 3 went at about 175Kb/s.

I assume this is an indication of trafic at the server level.

Is A4 when a lot of folks jump into the Alpha version?  As you can see from my join date (when I switched to Ubuntu as a complete linux noob) I have little prior experience to go on.

I'm getting it at about 170KBs. This is my first release cycle to follow. I am motivated to get KK running so I can get rid of Fedora.

---

### Post by andrewabc on 2009-08-13
> **ranch hand said:**
> Is A4 when a lot of folks jump into the Alpha version?  As you can see from my join date (when I switched to Ubuntu as a complete linux noob) I have little prior experience to go on.

Yes I think the later the release (alpha, beta, RC), the more downloads they would get.

Probably just the initial hammering of servers tonight.

---

### Post by ranch hand on 2009-08-13
> **running_rabbit07 said:**
> I'm getting it at about 170KBs. This is my first release cycle to follow. I am motivated to get KK running so I can get rid of Fedora.
I can see wanting to get out of Fedora.  I have had it on here 3 different times and it does not play nice.  You have to watch that installer like a hawk and be ready to abort when it is about to take over the HDD.  When I have it on I am not impressed, Just not worth it to me.

I wish I was getting that kind of speed.  It is hot here.  Maybe the ISPs air conditioning is not up to it (telephone co-op - only way to get a company here was to do it ourselves).  May have some servers there down.

---

### Post by wayne_cat on 2009-08-13
the Ubuntu servers are still fast as lightning ... 3:20 minutes to download the iso

```
rschmitt@extraseven:~$ which wget
/usr/bin/wget
rschmitt@extraseven:~$ wget http://cdimage.ubuntu.com/releases/karmic/alpha-4/karmic-desktop-i386.iso
--03:17:20--  http://cdimage.ubuntu.com/releases/karmic/alpha-4/karmic-desktop-i386.iso
           => `karmic-desktop-i386.iso'
Resolving cdimage.ubuntu.com... 91.189.88.39
Connecting to cdimage.ubuntu.com|91.189.88.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 730,206,208 (696M) [application/x-iso9660-image]

100%[=======================================================================================================================================>] 730,206,208    2.52M/s    ETA 00:00

03:20:20 (3.87 MB/s) - `karmic-desktop-i386.iso' saved [730206208/730206208]

rschmitt@extraseven:~$ 
```

---

### Post by ubudog on 2009-08-13
Are there any new themes? :P

---

### Post by ubudog on 2009-08-13
Where I am there is bad internet but once I get back to a place with faster internet I will download it.

---

### Post by running_rabbit07 on 2009-08-13
> **ranch hand said:**
> I can see wanting to get out of Fedora.  I have had it on here 3 different times and it does not play nice.  You have to watch that installer like a hawk and be ready to abort when it is about to take over the HDD.  When I have it on I am not impressed, Just not worth it to me.

I wish I was getting that kind of speed.  It is hot here.  Maybe the ISPs air conditioning is not up to it (telephone co-op - only way to get a company here was to do it ourselves).  May have some servers there down.

Fedora has been great to me and yeah I seen it wanted to eat Ubuntu when I started the install, but I like where Ubuntu is going. It is much easier to learn. I will save the rest for a testimonial thread later.

---

### Post by wayne_cat on 2009-08-13
> **ubudog said:**
> Are there any new themes? :P

no .... the new artwork will come on August 27th.

---

### Post by Slug71 on 2009-08-13
What Kernel does Alpha 4 have and is Radeon KMS enabled by default?

---

### Post by wayne_cat on 2009-08-13
> **Slug71 said:**
> What Kernel does Alpha 4 have and is Radeon KMS enabled by default?

kernel 2.6.31-5 and Radeon KMS is still disabled

---

### Post by ubudog on 2009-08-13
> **wayne_cat said:**
> kernel 2.6.31-5 and Radeon KMS is still disabled

Sweet!

---

### Post by Slug71 on 2009-08-13
> **wayne_cat said:**
> kernel 2.6.31-5 and Radeon KMS is still disabled

Thanks wayne-cat.

---

### Post by wayne_cat on 2009-08-13
> **ubudog said:**
> Sweet!

I'm happy about this ... Radeon KMS is still not usable ... it works only with some ATI
cards ... Gnome is really sluggish with active KMS on my ATI x1600

edit:

see this thread

[http://ubuntuforums.org/showthread.php?t=1181151&highlight=radeon](http://ubuntuforums.org/showthread.php?t=1181151&highlight=radeon)

---

### Post by running_rabbit07 on 2009-08-13
I just wanted to say that the Alpha 4 LiceCD acts a lot better than the Alpha 3, which I am sure everyone expected. Not going to install yet. Way too many files have to be backed up first.

---

### Post by running_rabbit07 on 2009-08-14
I went ahead and installed it, Other than few screen flickers, it runs great.

---

### Post by golusweet on 2009-08-14
> **kevpan815 said:**
> Not True. If You Clean Install, You Will Get Mozilla Firefox 3.5.2 Instead Of The Current Mozilla Firefox 3.0.13, Just FYI.


 Just keep updating. No need to do clean install.

I'm using Mozilla Firefox 3.5.2 :P

---

### Post by Luca_turicci on 2009-08-14
yeahp, i'm using FireFox 3.5 too, this is why i love ubuntu, no need to reinstall every time there's a new version, not like windows.... ¬¬

I'm having some problems with gdm, sometimes it doesn't load the theme or icons, etc. sometimes it does... i guess it's normal on an Alpha version. 

Plus, Inkscape finally fits perfect on my 10.1" screen.

I installed Alpha 3, and found out that Compiz wasn't there by default. Anyone knows why?

---

### Post by wayne_cat on 2009-08-14
> **Luca_turicci said:**
> yeahp, i'm using FireFox 3.5 too, this is why i love ubuntu, no need to reinstall every time there's a new version, not like windows.... ¬¬

I'm having some problems with gdm, sometimes it doesn't load the theme or icons, etc. sometimes it does... i guess it's normal on an Alpha version. 

Plus, Inkscape finally fits perfect on my 10.1" screen.

I installed Alpha 3, and found out that Compiz wasn't there by default. Anyone knows why?

Metacity is Karmic's default window manager (Compiz does not work with all graphic cards)

---

### Post by running_rabbit07 on 2009-08-14
> **Luca_turicci said:**
> I installed Alpha 3, and found out that Compiz wasn't there by default. Anyone knows why?
Don't know why but it started working on it's own when I installed A4.

---

### Post by marcopolo1981 on 2009-08-14
I have a problem.
Ive downloaded alpha 4 x64, live cd.
Ive checked the midsums and used the built in integrity checker to verify the disc is sound, but when starting the live cd, I only get as far as command line - "Ubuntu Login:"
I don't know what user name and password to use in order to run startx manually, though when I shut down, it does say stopping the gui.
Anybody got any suugestions?

TIA
Mark

---

### Post by cariboo on 2009-08-14
In Alpha3 there was a countdown timer on the login screen, I don't know if alpha 4 is the same, as I don't need to install it yet. Just wait for the countdown timer to get to zero, and it will continue on to the desktop.

---

### Post by jackhynes on 2009-08-14
Anyone got the new indicator applet working?

---

### Post by oboedad55 on 2009-08-14
Does Karmic use the same installer as 9.04?

Thanks!

---

### Post by ubudog on 2009-08-14
> **oboedad55 said:**
> Does Karmic use the same installer as 9.04?

Thanks!

I think. :P

---

### Post by ubudog on 2009-08-14
Anyone else know?  I'm also curious.

---

### Post by NCLI on 2009-08-14
So far, yes, at least in Ubuntu, I haven't tested X/Kubuntu.

---

### Post by wayne_cat on 2009-08-14
> **NCLI said:**
> So far, yes, at least in Ubuntu, I haven't tested X/Kubuntu.

Kubuntu comes with a new installer

[http://ubuntuforums.org/showthread.php?t=1240217](http://ubuntuforums.org/showthread.php?t=1240217)

---

### Post by ubudog on 2009-08-14
> **wayne_cat said:**
> Kubuntu comes with a new installer

[http://ubuntuforums.org/showthread.php?t=1240217](http://ubuntuforums.org/showthread.php?t=1240217)

Ok.  Thanks! :P

---

### Post by Marat89 on 2009-08-14
sry double post

---

### Post by running_rabbit07 on 2009-08-14
> **cariboo907 said:**
> In Alpha3 there was a countdown timer on the login screen, I don't know if alpha 4 is the same, as I don't need to install it yet. Just wait for the countdown timer to get to zero, and it will continue on to the desktop.

I haven't seen that yet. That would be cool.

---

### Post by ubudog on 2009-08-14
> **running_rabbit07 said:**
> I haven't seen that yet. That would be cool.

Yeah me neither, but it would be kinda cool.

---

### Post by Giwex on 2009-08-15
Hello everybody! 1st post :)

After having used Alpha 3 quite happily this morning I made a fresh install of Alpha 4. Everything seems ok except GRUB is 1.96 rather than 2. Anybody else has this issue?
Thanks

---

### Post by psyke83 on 2009-08-15
> **Giwex said:**
> Hello everybody! 1st post :)

After having used Alpha 3 quite happily this morning I made a fresh install of Alpha 4. Everything seems ok except GRUB is 1.96 rather than 2. Anybody else has this issue?
Thanks

That's normal. It's customary for developers to version pre-milestone software as x.9x to signify that it's stable enough to use (but not yet perfect).

---

### Post by Giwex on 2009-08-15
Thanks for answering. I was just confused because the new background is black rather than the previous blue

---

### Post by jerrylamos on 2009-08-15
A4 CD boots to black screen no cursor no keyboard nothing hung altogether.

Compaq Presario ati radeon Xpress 200.

Booted in recovery mode by replacing "quiet splash" with "single".

At recovery menu, found there was no /etc/X11/xorg.conf.  Boy the developers don't help us any.

Made a directory, mounted a karmic A2, copied /etc/X11/xorg.conf over.

Added 

Driver "vesa"

boots O.K. with vesa did not with the default xserver-xorg-video-radeon or whatever is the default; can't tell because it is hung. 

I could enter a launchpad bug which would involve 
booting in recovery mode, 
apt-get install openssh-server, 
giving root a password, 
logging in from another pc on the lan, 
resume to get the failure, 
if ssh is still working (a BIG if, does not on A4 intel i830 or i845)
copying over Xorg.0.log, dmesg, .xsession-errors, 
filling out a launchpad bug, ... 
or I could just wait to see if anyone else gets the bug too....:confused:

When it is hung during boot none of the handy apport or ubuntu-bug xorg other reporting tools work.  Everything has to be running in gdm mode before the tools work, if everything was running in gdm mode I wouldn't have a bug.

Oh, all of this started when the developers added in KMS mode which is off by default on ATI however the driver changes aren't done yet....here's hope.

Jerry

p.s. did an install from CD Live using "vesa" went O.K.  Couple problems it fixed by itself.  Manual partition worked O.K.

Install copied over the /etc/X11/xorg.conf with Driver "vesa" so it booted up just fine.  Thanks!

Updated the A4 install with the PPA [https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms](https://edge.launchpad.net/~ubuntu-x-swat/+archive/kms) for xserver-xorg-video-radeon.  Booted O.K. That's driver ati radeon 1:6.12.99+git20090805 so the one in the A4 CD must be different.

---

### Post by marcopolo1981 on 2009-08-17
Hi again.
I'm still not able to enter GUI mode - Live cd or installed.
I waited the default 10 seconds for autologin, didn't work.
I then waited a further 2 minutes and went and made a coffee, and still nothing.
I installed 9.04 again, configured the nVidia driver for this kernel, and all was ok.
I then did an upgrade using terminal "update-manager -d"
Booted into new kernel, entered my name and password, and ran "startx" It gave an error saying that nvidia drivers aren't available. I booted into it again in swapping "quiet splash" for "single" and tried to run the nVidia driver installer available from nVidia and it basically told me that these drivers aren't supported.
Wondering if I'm getting a similar problem to jerrylamos?
Going to try what he did and will post back

Edit:-
Yep, that fixed it. Thanks Jerrylamos!
Vesa drivers "work" but way to choppy on this lappy. But it got me closer to a smooth GUI.
I had to boot with enabled vesa diver before it would allow the nVidia driver install to complete. I don't know why?

---

### Post by ChiJoan on 2009-08-19
Hello,

I tested A4 and now it sees the on-board Intel NIC on the MS-6580 (v.1.X) 845G Max motherboard, but the MAC address reads all zeros...and yet Windows XP Pro uses the same NIC after the driver is installed.  I tried to update the BIOS, but so far have had no luck.

Anyone come across this before?  Oh, because of this BIOS, I had to push the F-Key #7 to install WinXP.  The Ami BIOS is 7.00.10 and dated 5/20/02.

Any pointers is appreciated for this MSI motherboard.

Thanks,
ChiJoan in Reno, NV, USA

---

### Post by ubudog on 2009-08-22
Downloading now.  Finally have a fast enough internet connection to do so.  Can't wait!

---

### Post by ubudog on 2009-08-22
Just 20 more minutes! :P :guitar:

---

### Post by Diggs808 on 2009-08-30
AHHHHH....

I downloaded the 9.10 and it will not boot to the live CD.  Whenever it starts I cannot log into it.  It says Authentication Failure.  I cannot find any login and passwords for the live cd.  Any help???  I get that message for the live cd or the just install ubuntu option.

---

### Post by andrewabc on 2009-08-30
> **Diggs808 said:**
> AHHHHH....

I downloaded the 9.10 and it will not boot to the live CD.  Whenever it starts I cannot log into it.  It says Authentication Failure.  I cannot find any login and passwords for the live cd.  Any help???  I get that message for the live cd or the just install ubuntu option.

There is no user or password for live cd. Just press enter when it pops up (or wait the 30 seconds and will auto login).

I presume you are doing this and still getting the error?

Maybe wait until this Thursday and download alpha5 to see if it is fixed. If not fixed, create thread in this forum about this to see if anyone has solutions, and if not file a bug. :)

---

### Post by Diggs808 on 2009-08-31
> **andrewabc said:**
> There is no user or password for live cd. Just press enter when it pops up (or wait the 30 seconds and will auto login).

I presume you are doing this and still getting the error?

Maybe wait until this Thursday and download alpha5 to see if it is fixed. If not fixed, create thread in this forum about this to see if anyone has solutions, and if not file a bug. :)

I am not getting past the login screen for the Live CD.  All I see is an authentication error and it fails to log in.  I have tried a couple of different ways in order to in to even see the Live CD.  Nothing.  Kinda frustrating, especially when I am trying to install.  Even the OEM installer doesn't work.

---

### Post by Seventh Reign on 2009-08-31
> **Diggs808 said:**
> I am not getting past the login screen for the Live CD.  All I see is an authentication error and it fails to log in.  I have tried a couple of different ways in order to in to even see the Live CD.  Nothing.  Kinda frustrating, especially when I am trying to install.  Even the OEM installer doesn't work.

Its probably not this, but I find its good to check 'everything'.  Make sure none of the keys on your KB are stuck.  I know on one of my older KB's, the 0(ins) Key on the Num-Pad sticks and causes issues when I boot.

---

### Post by Diggs808 on 2009-08-31
> **Seventh Reign said:**
> Its probably not this, but I find its good to check 'everything'.  Make sure none of the keys on your KB are stuck.  I know on one of my older KB's, the 0(ins) Key on the Num-Pad sticks and causes issues when I boot.

Nope.  Not that.  I checked EVERYTHING.  Including turning off my wireless hardware switch and making certain that I didn't have any USB type things plugged in.  Still no joy.

---

### Post by kevpan817 on 2009-09-15
> **kevpan815 said:**
> Not True. If You Clean Install, You Will Get Mozilla Firefox 3.5.2 Instead Of The Current Mozilla Firefox 3.0.13, Just FYI.
 
 
I Will Try Installing Firefox 3.0.13.  Just FYI.  I Will Do A Clean Install.  Just FYI.
 
Thank You.  Just FYI.  :)

---

### Post by andrewabc on 2009-09-15
> **kevpan817 said:**
> I Will Try Installing Firefox 3.0.13.  Just FYI.  I Will Do A Clean Install.  Just FYI.
 
Thank You.  Just FYI.  :)

Better off waiting until thursday and do fresh install of alpha 6, than say alpha 5. Some will say you can install daily build, but better off waiting until alpha 6 to make it easier to report bugs.

---

### Post by 23meg on 2009-09-15
Closed for milestone necromancy. Please use a recent daily build or milestone release for testing.

---

