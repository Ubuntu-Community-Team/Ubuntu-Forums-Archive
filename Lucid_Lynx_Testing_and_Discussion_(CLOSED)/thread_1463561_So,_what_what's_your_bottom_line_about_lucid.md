---
title: "So, what what's your bottom line about lucid?"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by moviemaniac on 2010-04-27
Hi fellow testers,

many of us have been using the illustrious lucid lynx for quite some time - even months now and for many of us it'll be time to say goodbye and hello maverick.
So I thought about starting a thread where everyone can tell us about his experiences with lucid - the good and the bad. This could become sort of a compilation of feedback that might be good for the devs too.

So I'll start:

**- The good:**
LL has been quite a great experience for me so far. It is stable (except for the problems below), snappy and most of the bugs that hit me during testing were fixed so far. It ran on all of the machines I popped the disc in (my iMac 8,1, a IBM T40, A Lenovo T500 and an MSI laptop). All in all, a very decent release - if it weren't for two more or less huge problems I'll talk about below - showbreakers I'd want to call them.

**- The bad:**

- KMS on ATI without PM:
As many of us know the code in Lucid's -32 kernel doesn't have support for power management on ATI cards with KMS (which is default). This is not a problem for desktop users, but laptop users with beefy cards may run into severe overheating issues. I expect the forums to flood with these problems once lucid is final. I have experienced this on two machines at home: GPU and CPU share a heatsink thus the CPU gets very hot too when idling. In one case this lead to the CPU (both are C2Ds) being stuck at 800 MHz a few minutes after booting, in the other case the CPU temps went up to 80° in idle even with the fans at full speed. Switching to fglrx OR a newer kernel and PM OR UMS and PM fixes this, but I feel KMS on ATI as a default is a bad decision right now. I hope this gets fixed with 10.10 as the PM code hits MMs kernel.

-KMS (on ATI) causing system freezes:
I have only experienced this on ATI, othe rcards might be affected too: The system freezes (up to multiple times a day) mostly when playing back video, using flash or playing games. It is only accessible via ssh so most people need a hard reset. I have so far encountered this (while helping people) on 10+ machines including three in my home so I guess it is a serious issue. Logfiles are unusable, there's no trace of the crashes being logged. What fixes the problem is updating to the currently in-development -34 kernel series so I guess it's a problem in LLs DRM code which was backported from -33. Again, as the issue above, a real showstopper for quite a few people - not all machines are affected (I haven't found a pattern yet) so many will run just fine, but also many machines are affected.

Well, those were the more serious bugs I encountered while testing (and which still exist in lucid as of the RC).

Some of the minor annoyances:
- Plymouth: It just looks goddamn ugly on machines not using KMS. It might speed up the boot process by 1-2 seconds and allows smoother transitions to GDM, but is this worth the ugliness many users now have? heck, it even looks funky with colors that look like they're on drugs on my T40 with KMS on a r100 (Mobility 7500) card.
- ancient ffmpeg: Lucid's ffmpeg is now over 1 year old. Development has moved on in many, many, many areas supporting many more codecs and features. I'm using my own, current svn builds and can't help but thinking wheter that wouldn't have been a better choice for lucid too? Even my requests to backport some of the major new codecs (Dolby TrueHD, Blu-Ray subtitles...) has not been fulfilled. We have to keep in mind lucid's a LTS release and I think we should keep at leas the multimedia side of it as up-to-date as possible to not risk it being completely outdated a year from now (it is already a bit outdated and it hasn't even been released yet...)
- Evolution 2.28: Evolution has always been a buggy bit of software throughout its history. 2.30 has brought many, many bugfixes upstream but it hasn't been included in lucid. Again, we're talking LTS here - many of these bugs which are fixed upstream are going to haunt the users for a few years now.
- oh, and who had the brilliant idea to move the minimize/maximize/close buttons to the left hand side? *srcasm on* A very newbie / switching-from-windows-user friendly decision! *sarcasm off*

Well, that's it from my side, I hope my criticism was constructive and a bit useful (it is, after all, only meant as feedback from a user's perspective). All in all I want to stress I really like lucid and think, y'all have done a superb job laying the base for a rather solid LTS release!

---

### Post by clhsharky on 2010-04-27
Hi

KMS PM is now in the kernel, 2.6.34.rc4 or newer. The ATI legacy chips that has to run OSS drivers, should certainly use the newest .34 kernel on laptops. The .34 kernel is way more laptop friendly than Ubuntu patched .32. Although the kernel PM is not as good as fglrx, reports claim to keep temp around 65c. Thats enough to keep core safe and away from temp crashes. I don't see a problem any more for me, but could be for the some. 

Sharky

---

### Post by moviemaniac on 2010-04-27
Hi Sharky, I've been using -34 for over a month now (due to the KMS freezes in -32) and I can only agree with you. However *some* cards don't work with KMS PM right now because they report the maximum clock speeds as the default ones in their AtomBIOS causing them to always run at full speed - my 2600XT is such a case but it doesn't get really hot anyway so I don't care. So each case needs to be evaluated separately whether -34 with PM or fglrx on -32 is the best option (for now).

---

### Post by demwz on 2010-04-27
Hi,

i've been using ubuntu for a couple of years now. from my point of view lucid is the best ubuntu release ever. even the best linux desktop distribution.

even if the design is disputed i love it. I hated the brown theme in the past.

Installation was pain in the as somehow in the past, at least on my hardware.  (Macbook pro, HP2133 Mini Notebook). I had always to pay attention on updates often they were destructive bcs of patched - self compiled/missing drivers

Installation of lucid worked like a charme.

the only thing i'm missing is the ability to replace windows to another desktop

---

### Post by Curtiss on 2010-04-27
Ubuntu has a keeper on this one. I had an old PC with XP on it and decided to give Ubuntu a try again, loaded up the beta 1 and I was so impressed I built a new machine just for Lucid Lynx.

Now on the RC and the install was flaw less and has been rock solid damm near perfect. I've been using the RC as my daily work horse pushing it to the limits and am still very impressed. My windows 7 box sets collecting dust now.

I am a photographer so will still keep windows 7 for photoshop and lightroom till I can port my work flow over to the Lynx and besides gimp, bibble and lightzone works great with Lucid Lynx RC 64 bit.

I don't post much in the fourms but read them daily you guys and gals have been a wealth of info my hat is off to you and Ubuntu for putting out rock solid OS.

Curtiss

---

### Post by moviemaniac on 2010-04-27
@Curtis: Photoshop works in Ubuntu using WINE - take a look at [http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17) for the details on the support of your specific Photoshop version. You could try it with a trial version first so you don't have to go through the activation process without knowing whether it'll really work.

---

### Post by Curtiss on 2010-04-27
Thanks will look into that !

---

### Post by aviramof on 2010-04-27
apart from all the ati and Plymouth problems i wish it would have a better nautilus then now and that empathy would have been better and had support for other client with today empathy
you can't even send files to any one excpet maybe google and google talk users because it support xpmm or something like this. 

and that working with samba would have been easier i have not checked it out recently but not long ago when i tried it was a mess and i was unable to remote control ubuntu 
and had all sort of permissions problems and etc i'm hopping that all this problems have already been fixed by now.

and of course network manager and pppoeconf problem ppoeconf worked pretty well until recently excpet the auto connect pppd option but network manager did not not until this 
week pretty much and the p2p problem i mentioned here that i am not sure if it has already been fixed or not.

and i still have one problem i am not entierly sure that grub 2 can install itself on my 
computer without my help i still needed to use this commands:

```
sudo mount /dev/sdb2 /mnt && sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

sudo grub-install /dev/sda

sudo grub-install /dev/sdb

exit

sudo umount /mnt/dev && sudo umount /mnt/proc && sudo  umount /mnt

```last night after i formated and grub 2 was not update during the install and the boot process was still looking for the number of the formated partition.
 
and that is pretty much all the problem i had with lucid that i can remeber for now and beside that everything is working fine now.

---

### Post by BrokeMahPC on 2010-04-27
The ATI, Plymouth and KMS issue has to be sorted out - expecting new users to edit boot strings, configure xorg and compile themselves a new kernel is just not right. I have used Ubuntu for a couple of years now and I'm only up to the stage where I would feel confident doing that now.
Any news on the final release? Will any of this be fixed?

---

### Post by timosha on 2010-04-27
I tested for six months Lucid on 5 machines and my bottom line is that Lucid is a bit like Windows Vista:

On some newer machines it works perfectly, on some older machines it works a little bit and on other machines it doesn't work at all. It has probably something to do with the video chips and the video drivers.

Most annoying for me is that indicator applet. Sometimes it appears after login, sometimes it doesn't appear and sometimes it appears twice. Takes two or three logout/login to get it right.

---

### Post by moviemaniac on 2010-04-27
> **BrokeMahPC said:**
> The ATI, Plymouth and KMS issue has to be sorted out - expecting new users to edit boot strings, configure xorg and compile themselves a new kernel is just not right. I have used Ubuntu for a couple of years now and I'm only up to the stage where I would feel confident doing that now.
Any news on the final release? Will any of this be fixed?
No, I don't think it'll be fixed until 2.6.34 hits 10.10 - certainly not for the final and I'm not even sure it'll be fixed in any of the point releases as it most likely would require a kernel update by 2 revisions and I don't think they're gonna do that... I could be wrong and it might just be a single patch that needs to be applied. The bugreport on the freezes has been in launchpad since Karmic (446421) - go figure...
I might do some bug-hunting trying to find the commit(s) which fixed this upstream but it's gonna be next week until I have some spare time to do just that.

---

### Post by Samzon on 2010-04-27
[LIST=1]
[*]The bootsplash screen is horrible, but I think it can be changed. I liked the old one. =(
[*]The default theme is horrible, but can be changed.
[*]Random crashes which I have reported, even from fresh install.
[*]The sound won't work on my PC before I go to the audio settings and turn up all volumes. (Realtek inbuilt audio)
[*]Asus aspire one (mini) has some trouble sometimes connecting to a network, dunno if it's a problem with this or not.
[/LIST]
Otherwise really nice. :P

---

### Post by alligoodw on 2010-04-27
Using a HP Pavalion laptop with Nvidia graphics card = no video.  I can't install Lucid and I'm not going to use the alternative CD to salvage something as basic as video.  This hurdle should have been taken care of years ago.  Mouse, keyboard and video are the basic to any computer system and Ubuntu still struggles with these issues.  As long as this behavior exist, Ubuntu will NEVER be an alternative desktop for the masses.  Trust me, I know!

---

### Post by timosha on 2010-04-27
> **alligoodw said:**
> Using a HP Pavalion laptop with Nvidia graphics card = no video. 

Yep ! One of my five machines which doesn't work with Lucid is an HP Pavilion. I know, there are workarounds but it should work out of the box.

---

### Post by fedexnman on 2010-04-27
im sticking with ubuntustudio karmic,  reasons are nvidia and plymouth, nuff said there. that being said , i'll wait for 10.10 .:guitar:

---

### Post by kaibob on 2010-04-27
For me, lucid has more good than bad. The network upgrade went well without any major issues. I like simple scan--it's fast to load and does exactly what I like. I also like some of the new features in bash 4, which was present in karmic, but I skipped that after a tryout. The palimpsest disk utility will do a lot of the stuff that I used to do with WinXP or gparted. Lucid seems faster to shut down and possibly to load. 

On the other hand, the splash screen is unattractive, but I assume they'll fix that in time. I miss Totem Xine; I never have been able to get totem gstreamer to work as I want. Evince forgets view settings when reading new PDF's, which is a major usability issue for me.

Probably most important, I'll be getting a new computer soon with an i3 processor and  Intel graphics, and I understand that lucid works with the new Intel graphics chip.

---

### Post by clhsharky on 2010-04-27
HI moviemaniac

Your ATI 2600XT card was at the time AtomBIOS added PM to mobileHD chip, and you were left out. AFAIK all mobile chips from 3100 on should work with kernel/PM, except for evergreen. Some legacy mobile chips "r300/r500" are supported with AtomBIOS and work with KMS/KernelPM.

Sadly many users wouldn't know what to do if it doesn't work OoTB.

Ubuntu does make it easer to add packages than most distros.
Fresh OSS drivers and latest Kernels is not much more than copy/past to add PPAs and click to install deb.

I agree with you and hope 10.10 will bring it together for laptops.
I realy like Lucid for my desktop.


Sharky

---

### Post by moviemaniac on 2010-04-27
Thanks very much for the info! Lets hope the PM devs come up with a solution to manually set the PM mode - I have some settigns in my AtomBIOS table which request far lower clock speeds, but, as the highest one is default, they don't get used. I've already posted this issue on dri-devel and am hoping for a positive response. It's not a necessity for me, as I said, but it would be great to have it and if it's only for the lower power consuption and the resulting 10-15&#8364; savings per year on the electricity bill ;)

---

### Post by xhalarin on 2010-04-27
> **moviemaniac said:**
> - oh, and who had the brilliant idea to move the minimize/maximize/close buttons to the left hand side? *srcasm on* A very newbie / switching-from-windows-user friendly decision! *sarcasm off*


This is a deal breaker for me.  I would rather go through the pain of switching distros then have my OS behave like a Mac.

---

### Post by gnomeuser on 2010-04-27
I have been very impressed with Lucid all the way through the cycle. It has been very solid all the way and the list of improvements clearly make this the finest Ubuntu release to date.

Now I am waiting for Maverick to open so I can switch my desktop machine.

I am very impressed with the state of Nouveau, the new look and feel, the fact that Banshee is now kept up to date in the main repos (and hopefully will become the default media player in Maverick).

My bottom line is that Lucid is what convinced me not to leave Ubuntu. It leads in areas that I care about, it gives me a very solid desktop that is fun to use, beautiful to look at and easily inspires me to improve the system rather than fighting it.

All hail Lucid!

---

### Post by emarkay on 2010-04-27
I just do not understand and can not comprehend the choice to "advance" to Plymouth and it's ills for an LTS. Couldn't it have waited for the toolchain of 10.10?

The LTS should have been a "Rock Solid Karmic" with the kernel improvements and an emphasis on code efficiency, advanced application attention and bugfixes. Sure it could have had the "wrong-side buttons" and the other Lucid features, but I think there's now a "line in the sand" for older users and those who just want to stay productive that's going to haunt us for years.

As I said I am going to get this thing streamlined and pared down and stick with it for a long, long time - like most of those who have stuck with MS WinXP (myself included on those rare occasions I don't want to W(h)INE): we don't need no flashy hardware nor "New Improved" frills...

---

### Post by antenna on 2010-04-27
I have been using it for a few weeks and have had no real problems whatsoever, everything has been flawless.  I would say it is the best release of a distro I have used, so yeah very impressed (& perhaps lucky with my hardware).

---

### Post by cguy on 2010-04-27
It's crap.
I'm talking about Kubuntu.
- crashes all over
- installing Transmission doesn't install its icons => I get question marks in the right click menu (in the tray) - The same with Pidgin here and there...
- there's no decent music player:
----- Amarok can't shuffle and repeat at the same time, scanning a folder with a lot of mp3s hangs the UI, after a thousand releases they don't have a proper queue manager (ok, this is not Kubuntu's fault, but still ruins the experience)
----- Rhythmbox can't install some mp3 codecs without hitting the bucket, nor can it close correctly (it remains in the memory)
- how do you remove KBluetooth from starting automatically?
- although just a really small nuisance, why do they include the embarassing Konqueror instead of Firefox, by default?

I've had it with Kubuntu. There's something bugging me out every hour or so.
I'm gonna try the regular Ubuntu when the final version comes out, hopefully it will be solid. Too bad that it isn't as customizable... and fuglier, but I can live with that.

---

### Post by Eddie Wilson on 2010-04-27
> **cguy said:**
> It's crap.
I'm talking about Kubuntu.
- crashes all over
- installing Transmission doesn't install its icons => I get question marks in the right click menu (in the tray) - The same with Pidgin here and there...
- there's no decent music player:
----- Amarok can't shuffle and repeat at the same time, scanning a folder with a lot of mp3s hangs the UI, after a thousand releases they don't have a proper queue manager (ok, this is not Kubuntu's fault, but still ruins the experience)
----- Rhythmbox can't install some mp3 codecs without hitting the bucket, nor can it close correctly (it remains in the memory)
- how do you remove KBluetooth from starting automatically?
- although just a really small nuisance, why do they include the embarassing Konqueror instead of Firefox, by default?

I've had it with Kubuntu. There's something bugging me out every hour or so.
I'm gonna try the regular Ubuntu when the final version comes out, hopefully it will be solid. Too bad that it isn't as customizable... and fuglier, but I can live with that.

No it's not crap. Boy that was an easy rebuttal. It doesn't crash over everything with me. Amarok has never been any good. No problems with Rhythmbox. You can run Rhythmbox in Kubuntu even tho it's not made for KDE. Rhythmbox will remain in memory unless you close it correctly. (Don't use the little x)
I use Ubuntu and not Kubuntu. I don't like KDE but I haven't really found anything wrong with Kubuntu. The only problem I've had with Ubuntu is the shutdown hanging up on a 32 bit install. Other than that it has been solid.

---

### Post by tokyobadger on 2010-04-27
@emarkay: your frustrations around plymouth are more than likely valid; the connection between plymouth and the '10.10 toolchain' is misleading - please define what you mean by '10.19 toolchain'

---

### Post by cariboo on 2010-04-27
Overall Lucid has been a joy to use, I'm blessed with hardware that is well supported. Plymouth works as it should on both desktop systems, but not on my netbook, a clean install when the final is released should fix that.

I was surprised how well the UNE works, everything but wireless worked out of the box, and all I had to do was connect a network cable to download the restricted Broadcom drivers to make it work.

The one big problem I have is that the Live CD doesn't detect any hard drives on my pure SATA system. If I fall back to the alternate install iso, the drives are all detected properly. Another bug has been reported about this problem, as it has been going on for the last couple of releases

---

### Post by MacUntu on 2010-04-27
It's another fine release. I have to re-compile more packages, though (my GNOME-antipathy is growing).

---

### Post by cguy on 2010-04-27
> **Eddie Wilson said:**
> No it's not crap. Boy that was an easy rebuttal. It doesn't crash over everything with me.
It does here and I was presenting my opinion, not the general rule. The fact that its behavior is inconsistent makes it a bad release. KDE worked just fine (ie: didn't crash that often) on Fedora, so you can't place the blame on it.
> 
Amarok has never been any good.
Damn right when speaking about 2.x.
> 
No problems with Rhythmbox. You can run Rhythmbox in Kubuntu even tho it's not made for KDE. Rhythmbox will remain in memory unless you close it correctly. (Don't use the little x)
I know that!:lolflag:
It remains in memory after a proper closing.

---

### Post by RJQ on 2010-04-27
No fix for older Intel graphic cards (and others no so old) making the system to crash often, will have to wait until somebody make another sort or regression driver just like in the last releases. (not a Ubuntu problem  but such a influential distro could have gave a push to the fix, but I guess is time to say goodbye to old hardware) apart from that quite a nice distro, a little fix to the theme (see my screenshot desktop) and good to go some how.

would like a complete dark theme in ambiance (that would fix the openoffice display of the menu) and a way to log in once the gnome is complete loaded (specially if there is no other window manager installed) that would feel smother.:)

and (but not necessarily related) shouldn't be an option in shipit to select within the same page either Kubuntu or Ubuntu or both cds? :confused:

---

### Post by mörgæs on 2010-04-27
> **xhalarin said:**
> This is a deal breaker for me.  I would rather go through the pain of switching distros then have my OS behave like a Mac.

There is a solution to that:
[http://blog.daviey.com/blogroll/anything-but-the-buttons.html](http://blog.daviey.com/blogroll/anything-but-the-buttons.html)

- hoping that this will not turn the thread into just another left-or-right-button discussion.

---

### Post by andresmh on 2010-04-27
Lucid looks pretty but my webcam and my microphone still do not work (they used to work in 9.04). They didn't work in Karmic either, I opened bugs back in 2009, got confirmed but they never got fixed. 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/409819)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496266](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496266)

I would have expected that my hardware (Laptop thinkpad) was not that unusual, but maybe it is.

---

### Post by TrevT93 on 2010-04-27
My bottom line about Lucid so far is that I'm thinking of switching distros, unfortunately.  My laptop used to have great performance with Xubuntu Karmic, including a stunning 20 second boot time at max (that's 20 seconds from hitting enter at the grub menu to the GDM screen coming up).  Xubuntu was reliable and fast, and with a little customization I came to love it.

But then I started using Arch a little over the last few months and I love it.  It's the ultimate you-only-have-what-you-use distro, and its boot time is 19 seconds from grub screen to SLiM loading up.  I was wary of using Arch at first and that's why I kept Xubuntu, so that I could fall back on something familiar if I got too overwhelmed.

But now Xubuntu Lucid is using Plymouth (which doesn't agree with my Intel GMA 950 graphics) and takes 30 seconds to boot.  And it doesn't ever fsck - the one time it did, Plymouth actually loaded but wouldn't go away when fsck was done, and the system went unresponsive, so I had to reboot.  Those are little nuisances that go a long way.  I'm not generally one to care about graphics on startup, but if a distro has them installed from the get-go, they may as well work, you know what I'm saying?  And the system itself, after getting in to the Xfce environment, is generally more sluggish than it was on Xubuntu Karmic.

So I figure that if I don't really like it as much anymore and I don't really use it as much anymore, why keep it?  Kind of unfortunate though; I really liked Xubuntu.

Maybe it will bounce back in time for the release on Thursday?  I'll cross my fingers and hope.

---

### Post by nanog on 2010-04-27
I upgraded 5 of my production desktops to Lucid many weeks ago and will upgrade the rest next week. That should tell you something. My servers will wait for the point release. My personal computers are running 2.6.34 and edgers and will be  moved to Meerkat as soon as the toolchain is loaded!

The thing I like the least is the removal of the location bar toggle in nautilus but its really an upstream thing. Gnome has this habit of dumbing down the interface in ways that are maximally annoying to experienced users.

---

### Post by barney385 on 2010-04-27
I just installed the RC. I've added the Medibuntu repos and I'm now downloading and installing the proprietary driver for my Nvidia card.

It sure is taking a long time though.

---

### Post by NoVista on 2010-04-27
The bottom line is
SHOULD WE WAIT?

Been around long enough to know every release has new issues, and a swarm of also redundant questions get asked. 
But for a LTS coming out, well geez, seeing what seems like A LOT of people having REAL ISSUES with MANY DIFFERENT THINGS, I wonder if
the release date should be postponed a bit?

---

### Post by aysiu on 2010-04-27
> **Chauncellor said:**
> Maybe in a year the "knee-jerk conservatism" (as it has been so well labeled) will wear off >.> The only knee-jerk responses I saw were the ones defending the change, since there didn't appear to be any usability rationale for making it in the first place. The knee-jerk responses I saw to [rational](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/532633/comments/71) [arguments](https://wiki.ubuntu.com/LucidLynx/WindowControlIssues) against the change were "Just get used to it" or "It's not a big deal" or "You can change it back."

Fortunately, Mark finally listened to at least some reason and put the close button at the end of the window instead of in the middle.

---

### Post by xebian on 2010-04-27
It's pretty much golden ATM. Barring any showstopper, the cd images are pretty much set.

You can get it now and then just zsync if there is any changes (which I doubt) that can't wait for the day-after updates.  Otherwise, ride with the stampede on release day. :guitar:

Hello meerkat!!!

---

### Post by Bluesan on 2010-04-27
> **aysiu said:**
> The only knee-jerk responses I saw were the ones defending the change, since there didn't appear to be any usability rationale for making it in the first place. [B]The knee-jerk responses I saw to [rational]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/532633/comments/71") [arguments]("https://wiki.ubuntu.com/LucidLynx/WindowControlIssues") against the change were "Just get used to it" or "It's not a big deal" or "You can change it back."
[/B] 
Fortunately, Mark finally listened to at least some reason and put the close button at the end of the window instead of in the middle.

Having followed the conversations regarding button placement, etc. (including your poll, and Mark's response), personally, I've simply given up, and am no longer using Ubuntu as my primary operating system. In fact, my original persona here is gone, and I reopened an account primarily to follow the screenshot thread every month.

The last straw for me, with the direction of Ubuntu, was the decision to go with Yahoo as the default search engine. Not because it was Yahoo (they're fine), but, it's pretty obvious to me at least, that the decision to go with a purple theme in 10.04 was a complementary decision to Yahoo's purple theming. Now that Yahoo's out of the picture, I wonder how the design team feels now about all things purple?

Anyway, Asiyu, you always fight the good fight, and my hat's off to you. :)

---

### Post by rliegh on 2010-04-27
I'm pretty on-the-fence about Lucid. I like the idea of it being supported until 2013, but then again -centos 6 will be too (though it probably won't be out until august or sept).

I'm surprised at how easily I'm getting used to the button placement, actually my biggest esthetics gripe is the fact the volume meter is sideways instead of vertical.

gwibber is flaky for me, but it seems to be improving with each update, so I'll give it a chance. I'm not a social media person so it's not too hard to live without.

I **HATE** the default look, but it's easy enough to change.

I have had a number of problems with nvidia, but they seem to be getting better with each update -already they're at a point that I can live with them (I just have to fix my /etc/defaults/grub file on each install so the bootsplash looks decent).

So far sound works better than karmic for me. I'll probably stick with Lucid unless I have problems with doing 3d in virtualbox.

---

### Post by kevinatkins on 2010-04-27
I've been very pleased with Lucid on the whole. I've installed it on various machines, as below -

- Acer Aspire T180 - Athlon X2 4200 / 2GB RAM / nVidia 6200 gfx;
- IBM T60 - Intel Core 2 Duo T7200 / 2GB RAM / Intel graphics;
- IBM T30 - Intel mobile P4 1.8GHz / 768MB RAM / Radeon mobility 7500 gfx; (Lubuntu)... very very fast with Lubuntu!!!
- Generic Athlon XP 3000+ / 1GB RAM / nVidia 6200 gfx;
- Ancient HP Pavilion Celeron 1.2GHz / 512MB RAM (Xubuntu)

All work fine, although the bootsplash is ugly on the older machines (big deal..)

Lucid is a nice release - I've been using Ubuntu practically since its original release way back in 2004 and this release is a good one.. But I'm concerned to read of others' negative experiences with ATI graphics...

For me though, the one possible cloud is, er, the Ubuntu One cloud service, which I'm not sure is ready for prime time, and which could seriously annoy / alienate new users (particularly where money is involved with the 50GB paid service)... It's a great idea, but alternatives like Dropbox do it better. And the new music store - again a great idea, and I've used it a few times, but it's waaaay too slow to sync / download and I foresee angry customers. The cloud-based nature of the music store could be a real winner - it just needs more polish.

But overall, I'm liking 10.04 a lot - works great for me!!

---

### Post by Trapper on 2010-04-27
> **alligoodw said:**
> Using a HP Pavalion laptop with Nvidia graphics card = no video.  I can't install Lucid and I'm not going to use the alternative CD to salvage something as basic as video.  This hurdle should have been taken care of years ago.  Mouse, keyboard and video are the basic to any computer system and Ubuntu still struggles with these issues.  As long as this behavior exist, Ubuntu will NEVER be an alternative desktop for the masses.  Trust me, I know!

I won't go so far as to blame Ubuntu with the video difficulties, etc. All of linux struggles with this. Much of the blame goes right back to the hardware vendors catering to M$ though. In case you are not aware, M$ is doing all it can to destroy nix through both the software and hardware sectors, including arm twisting the hardware vendors.

I really don't think Ubuntu expects to be an alternative for the "masses" and probably doesn't want to be.

JMO

---

### Post by Orographic on 2010-04-27
Lucid hasn't  been so good on this same system that has run Karmic so well. The RC actually wont boot for me (Betas did) via the live CD unless I press any key, choose language, press F6 then select nomodeset. Once I have installed Lucid I can get to the desktop fine but it takes another 25 seconds for all of the menus to appear. The desktop just sits there with the background showing and no menus, for nearly half a minute. This happened in the Betas too and I reported it as a bug.


Karmic is rock solid though and I will be getting a new system some time this year (Core i3 most likely) so will stick with Karmic for now. Have also installed PCLOS 2010. 

Its a shame as I wanted to install the LTS on this three year old system so I could retire it to a once or twice weekly use for years without having to install another OS. When the same machine can't run the latest version of Ubuntu, its a bit of a worry.

My system:


Core Duo E4300 with 2G Ram with Gigabyte 945GZM-S2 mobo and intel onboard graphics.

---

### Post by ajgreeny on 2010-04-28
I have Lucid on a desktop with sempron 2400+, 2GB ram, and an ATI 9200SE graphics card, which seems to run fine, with no obvious problems.

My difficulties started however, when I put it on an old laptop, an Acer Travelmate 2200 with an ATI Mobility radeon 9000 card.  It seemed to run OK, but the fan never ever stopped, and if I had left it for too long, I'm convinced it would have melted or burst into flames; it was certainly too hot to leave running with any confidence at all.  I tried all of the workarounds I found in forums, which purport to overcome the hot running problem of ATI cards with the OS driver, but so far nothing has worked for me.

So to sum up:-
For my desktop it seems OK so far as I can make out, though I'll stick with Karmic for the moment until a few of the inevitable bugs have been sorted, and keep Lucid on my "testing" partition.

For my laptop, I'm afraid it's a non-starter; it just runs too hot, and so far I can't get it to run cooler, so that has gone back to Karmic, which is brilliant.

---

### Post by makitso on 2010-04-28
Been using Utuntu since the 7.04 days.  Its solid on my  desktop but that system has all the right hardware that is linux friendly.  My laptops have been problematic at best.  Wireless has improved 1000+.  But suspend/resume is still hit and miss.  With Lucid, the ATI driver bit me in the butt but now seems to have settled down.  

Bottom line:  On my netbook I dual boot WIN7 and Lucid.  But, mostly I use WIN7 since it work all the time.  My desktop dev system is all Ubuntu.

---

### Post by NCLI on 2010-04-28
> **Bluesan said:**
> Having followed the conversations regarding button placement, etc. (including your poll, and Mark's response), personally, I've simply given up, and am no longer using Ubuntu as my primary operating system. In fact, my original persona here is gone, and I reopened an account primarily to follow the screenshot thread every month.

The last straw for me, with the direction of Ubuntu, was the decision to go with Yahoo as the default search engine. Not because it was Yahoo (they're fine), but, it's pretty obvious to me at least, that the decision to go with a purple theme in 10.04 was a complementary decision to Yahoo's purple theming. Now that Yahoo's out of the picture, I wonder how the design team feels now about all things purple?

Anyway, Asiyu, you always fight the good fight, and my hat's off to you. :)

Uh, what? So you think they based the central color of the new design on a search deal with Yahoo, only to abandon the search deal when it encountered a bit of opposition? Riiiiight...

----------------------------------------------

My bottomline is very positive. My netbook has been happy with Lucid for the entire testing period, though I have had to mess a bit too much with the system, so I'll probably do a re-install to clean it up. My mediaserver has also been happy with Lucid since Beta 2, and hasn't had a single crash in its 21 days of uptime. 

I'm now looking forward to doing a fresh install of both Win7 and Lucid on my main desktop, and I don't expect to have any problems.

---

### Post by barney385 on 2010-04-28
Loads very quickly now! Firefox is twice as fast. Graphics are new and improved.

Excellent

---

### Post by The Cog on 2010-04-28
I am surprised that they choose to introduce  anything as flakey as plymouth into an LTS release. It hides the reason that your PC won't boot, leaving an un-responsive and un-helpful black or purple screen. It also seems to be actually responsible for failing to boot sometimes (I think). On this laptop, I have to reboot maybe one time in five because it doesn't reach the login dialog. 

And for what? This seems to make the boot process far more reliable:
> sudo chmod -x /bin/plymouth /sbin/plymouthd

---

### Post by wilee-nilee on 2010-04-28
I like Lucid Karmic had a bug that made my computer reboot randomly when using FF.

---

### Post by awi on 2010-04-28
Hate hate hate the window's button at the left. I really really hate them, so much for the "linux for human beings". Human beings are used to the buttons to the right, get used to it (whether you like it or not, people's first 5, 10, 15 years in front of a computer were with the button at the right), trying to denied is like going into a crusade, kind of Stallman's not using a cell phone style. 
Obviously people arguing that "it is better, you'll see it when you use it" had never deployed an application to average non technical users. Take THE most popular operative system as an example and see their results with Vista's popularity...
IMO, too many changes for the average LTS users. Think about some 8.04 LTS user which has to switch from the "old" desktop to the new one. 
Almost "Black and white" theme for tray icons is like traveling back in time to the atari era.
Anyway, most of my complains are about look and feel, I'm a technical user it would not take me too much time to personalize my desktop the way I want (even though I was a happy upgrader since 7.10 with no major changes to  desktop), but I was trying to bring more people from the dark side to linux machine, now thanks to the big l&f changes, I will think about it twice...

---

### Post by x-shaney-x on 2010-04-28
Bottom Line...

Good:
Fast.  Very fast from boot to desktop, opening applications etc.  Everything feels much zippier to me.

Bad:
Things feel unfinished and unready.
Plymouth.
The much touted "social from the start" is a bit of a joke.
Gwibber doesn't work properly with facebook or the new notifications.
Empathy doesn't work with non hotmail email accounts unless a package is manually removed (after searching to find out why it won't login).
Indicator session menu pretty much just mirrors messaging menu.
New messaging/notification/indicator doings as inconsistent as the inconsistent "systray" it is designed to replace.

If lucid was an application it would feel like a 0.8 release rather than a 1.0 final.

Having said all that, when these things ARE all sorted I think the end result will be pretty awesome.

---

### Post by wilee-nilee on 2010-04-28
> **awi said:**
> Hate hate hate the window's button at the left. I really really hate them, so much for the "linux for human beings". Human beings are used to the buttons to the right, get used to it (whether you like it or not, people's first 5, 10, 15 years in front of a computer were with the button at the right), trying to denied is like going into a crusade, kind of Stallman's not using a cell phone style. 
Obviously people arguing that "it is better, you'll see it when you use it" had never deployed an application to average non technical users. Take THE most popular operative system as an example and see their results with Vista's popularity...
IMO, too many changes for the average LTS users. Think about some 8.04 LTS user which has to switch from the "old" desktop to the new one. 
Almost "Black and white" theme for tray icons is like traveling back in time to the atari era.
Anyway, most of my complains are about look and feel, I'm a technical user it would not take me too much time to personalize my desktop the way I want (even though I was a happy upgrader since 7.10 with no major changes to  desktop), but I was trying to bring more people from the dark side to linux machine, now thanks to the big l&f changes, I will think about it twice...

Thanks for representing everybody else's opinion, always wondered what the masses thought.

---

### Post by emarkay on 2010-04-28
> **The Cog said:**
> And for what? This seems to make the boot process far more reliable:
sudo chmod -x /bin/plymouth /sbin/plymouthd 			 		

Educate the weary - what's this do; what about all the "internal" things Plymouth is now needed for?

---

### Post by emarkay on 2010-04-28
> **tokyobadger said:**
> @emarkay: your frustrations around plymouth are more than likely valid; the connection between plymouth and the '10.10 toolchain' is misleading - please define what you mean by '10.10 toolchain'


The toolchain is the "pre-Alpha" release - strictly a mishmash of templates, ideas, boilerplates and whatever can be "borrowed" from the prior relases; it's is the foundation for the Alpha/Beta/RC/Release of the next version.

While I have a few well running systems, there are a bunch of folks out there that have some serious problems - many Plymouth related, but others - well just look at all the (more than a hundred) unfixed "high" bugs, and maybe as many unassigned/wishing ones, too, and a few that are looking like they are going to stay around a bit...
[http://www.ubuntu.com/getubuntu/releasenotes/1004overview](http://www.ubuntu.com/getubuntu/releasenotes/1004overview)

I am sure this too shall pass, and no animals were hurt in filming, but maybe they will take the "LTS" concept more seriously now, for that "brand" implies stability, not "gee-whiz" applications of dogs and ponies dancing with frilly knickers for the easily amused...

---

### Post by cguy on 2010-04-29
Here's my opinion:
> MyUsername@MyHostname:/media$ sudo mount /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type
MyUsername@MyHostname:/media$ sudo mount -t iso9660 /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The CD-ROMs/DVD-ROMs will go the floppy way before they will work on Linux.

---

### Post by TerminX on 2010-04-29
Lucid is okay, but it's the release that finally pissed off my 8 year old install (was Debian before Ubuntu ever existed) to the point of having to scrap the whole thing.  At least my /etc doesn't have years of cruft in it anymore.

However, even with a clean install there were issues that should have been resolved before any final release came about.  Virtual terminals randomly not working, etc.  I'm inclined to blame plymouth for a large chunk of the issues people are facing and have faced... it just doesn't seem like a good idea to implement premature software which obscures valuable startup warnings/errors while simultaneously causing errors of its own.

All of this plymouth stuff should have been implemented on Karmic or it should have waited until Lucid + 1.  Playing games with the boot process for what is supposed to be a stable release with 5 years of support just doesn't seem like a great idea, especially when the only thing that comes out of it is a screen that most users will ideally see for less than 15 seconds.

---

### Post by amano on 2010-04-29
Lucid is the first release that will please beginners:

The good:
-Facebook chat via Empathy (BIG yeah!)
-Twitter integration.
-You can install new fonts just by double clicking them.
-Eye of gnome can now display animated gif files (embarrassing that all former Ubuntus couldn't)
-While the new look will not be the one to rule 'em all, but it certainly looks more professional than the cartoonish old one.
-DVD playback with Gstreamer and Totem seems to have matured. You can insert a DVD and in most cases Totem will play it flawlessly (if the secret Medibuntu decryption package is installed). That was totally broken with Jaunty.
-Pulseaudio seems to have finally matured. There have been much less complaints about sound cards stopping working with this release

The bad:
-Some parts look unfinished (e.g. the new F-Spot editing functions with one button being overlapped by the sidebar)
-The new plymouth didn't mature enough yet. The binary blobs cause a rather ugly boot, Nouveau KMS doesn't offer any 3D accerleration. And Radeon KMS lacks some power management functions and thus isn't a good option for portable usage

The ugly:
-With some graphic cards it can be hard to get Ubuntu booted at all.

If you can get it to boot it will be the best Linux ever.

---

### Post by BrokeMahPC on 2010-04-29
RE buttons on the left and new users - I tested them out on the biggest noob I know of: My technophobe Girlfriend.
She has trouble with the Microwave, TV, VCR and can break a PC just by breathing in the same room, whenever she is near it I worry like a 'fish guarding eggs'.

"Oh, buttons on the left?" she said, clicked at them and got minimise / maximise confused the first time but has not had a problem since.
If she gets it - anyone else shouldn't have a problem.

---

### Post by WishMaster on 2010-04-29
Worst release ever...

Been using ubuntu since warthog, but can't get 10.04 to boot.
On laptop: screen goes blank, nothing to do about it.
On desktop: monitor goes into sleep-mode. Ubuntu can't get DVI-cable to work (digital). Booting with analog cable does work, but I want my DVI cable !

---

### Post by breadlord on 2010-04-29
Buttons on the left > mac panderism. It made me very, very angry. I've modified everything to put them on the right (as in proper...) side. I will continue to do so.

If you want to tempt people away from windows, why make the transition more difficult by forcing people to spend three seconds remembering where the buttons that "should be on the right" are. This is the kind of thing that puts off casual users.

The notifier applet is awful. Utterly abhorrent. Forced spacing, removal of the standard volume control, doubling the functionality of the pidgin tray icon. Waste of everyone's time.

My main issue with it is that without delving into dev documentation (which I don't have time to do) I don't know how to stop it from consuming amarok. The notifier icon that comes with notifier-applet doesn't have the last.fm keyboard shortcuts that I use all the time on it. I can also no longer restore the application by double clicking the icon, which is also very, very annoying.

Well done on removing functionality I used all the time. Bravo

---

### Post by The Cog on 2010-04-29
> **emarkay said:**
> > And for what? This seems to make the boot process far more reliable:
sudo chmod -x /bin/plymouth /sbin/plymouthdEducate the weary - what's this do; what about all the "internal" things Plymouth is now needed for?
It stops at least part of plymouth running. I get an error message during boot that it can't start plymouth - that seems the only bad thing I have found. Considering the number of dependencies they've hung on plynmouth, it's rather odd that I can disable the executables with no detctable loss of functionality. The good things are:

* It doesn't seem to get stuck during boot occasionally any more - no more blank black screens

* I can see what it's doing while it boots and can see where it gets stuck, except it doesn't get stuck any more

* It seems to prevent an oddity that occasionally puts my login dialog box on a non-existent second display where I can't see it.

---

