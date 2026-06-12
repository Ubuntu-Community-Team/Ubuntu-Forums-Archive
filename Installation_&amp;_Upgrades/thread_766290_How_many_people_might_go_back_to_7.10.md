---
title: "How many people might go back to 7.10?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by wandalalakers on 2008-04-25
I realize this is only the 1st day after the official release of 8.04 but with soooo many problems, how many people might go back to 7.10?  I guess I'll keep 8.04.  I'll wait it out and see how well it goes.  My sound doesn't work anymore and I'm not sure how long I can live without that.  My text looks really weird at the top of all windows.  Firefox, thunderbird, etc.
I'm using the crystal window decoration under system settings.  The text looks like it's super bold. Trying to see if I can use the compiz desktop effects.

These are the problems that I'm having after upgrading from 7.10 to 8.04

1. no sound
2. can't use gl xscreensavers
3. text looks really weird at the top of all windows
4. some moodin splash screens are off center

---

### Post by iaculallad on 2008-04-25
Hardy's rocking my PC right now after installing the LTS version. Better performance I think than its Gutsy brother.

---

### Post by Holy Cheater on 2008-04-25
Well, I've upgraded to Hardy, now my supsend-to-ram works :)
Some weird things with configuring my SB Live (it doesn't react on bass/treble options in alsamixer)
Also something new to fonts, they're a bit big, but look more "clear". Text of playlist in Amarok - just like Mac fonts. The only thing that troubles me: some weird things with monospace fonts.

---

### Post by eye208 on 2008-04-25
> **pcdoctor said:**
> My sound doesn't work anymore and I'm not sure how long I can live without that.
Have you tried uninstalling Pulse Audio?

A few days ago there was a lengthy discussion in the dev forum about whether it was a good idea to include Pulse Audio with Hardy at this point in time. A quick look at the forums now tells me the question has just been answered.

---

### Post by wandalalakers on 2008-04-25
> **eye208 said:**
> Have you tried uninstalling Pulse Audio?

A few days ago there was a lengthy discussion in the dev forum about whether it was a good idea to include Pulse Audio with Hardy at this point in time. A quick look at the forums now tells me the question has just been answered.

I just went to add/remove, settings, pulse audio settings and it's not checked.  So I assume it's not enabled.  Is there any place I can check?  Thx.

---

### Post by gtdaqua on 2008-04-25
> **pcdoctor said:**
> I realize this is only the 1st day after the official release of 8.04 but with soooo many problems, how many people might go back to 7.10?  I guess I'll keep 8.04.  I'll wait it out and see how well it goes.  My sound doesn't work anymore and I'm not sure how long I can live without that.  My text looks really weird at the top of all windows.  Firefox, thunderbird, etc.
I'm using the crystal window decoration under system settings.  The text looks like it's super bold. Trying to see if I can use the compiz desktop effects.

These are the problems that I'm having after upgrading from 7.10 to 8.04

1. no sound
2. can't use gl xscreensavers
3. text looks really weird at the top of all windows
4. some moodin splash screens are off center

The soooo many problems are in majority due to simultaneous upgrades. Doing a distro-upgrade is going to take a lot of time and because of the network traffic your connection disrupts, the upgrade will break and you will run into problems.

Always wait for 1 day if doing a distro-upgrade or the best to do while others downloading a 0.1KB/sec is:

1. Locate the TORRENT (not the http download) of Ubuntu Alternate CD.
2. Download the ISO Image of Alternate CD via torrent (you will get in a couple of hours - more the people, more the speed in torrents)
3. Upgrade your distro.

Do not rely on http connections for a few days after a release is out. I am surprised to see many IT folks here rely on http rather than torrent. Torrent is extremely faster than other type downloads. Especially on D-Day like yesterday (and today!), those that take the expressway are the smart ones.

---

### Post by wandalalakers on 2008-04-25
> **gtdaqua said:**
> The soooo many problems are in majority due to simultaneous upgrades. Doing a distro-upgrade is going to take a lot of time and because of the network traffic your connection disrupts, the upgrade will break and you will run into problems.

Always wait for 1 day if doing a distro-upgrade or the best to do while others downloading a 0.1KB/sec is:

1. Locate the TORRENT (not the http download) of Ubuntu Alternate CD.
2. Download the ISO Image of Alternate CD via torrent (you will get in a couple of hours - more the people, more the speed in torrents)
3. Upgrade your distro.

Do not rely on http connections for a few days after a release is out. I am surprised to see many IT folks here rely on http rather than torrent. Torrent is extremely faster than other type downloads. Especially on D-Day like yesterday (and today!), those that take the expressway are the smart ones.

You don't think my problems are bugs?

---

### Post by Disparition on 2008-04-25
My RW drives aren't working and it seems to be only (major) problem.

---

### Post by gtdaqua on 2008-04-25
> **pcdoctor said:**
> You don't think my problems are bugs?

:) Easy, mate! 

Its not unusual to see a lot of people reporting problems on the first few days of the release. What bugs are they?

---

### Post by wandalalakers on 2008-04-25
> **gtdaqua said:**
> :) Easy, mate! 

Its not unusual to see a lot of people reporting problems on the first few days of the release. What bugs are they?

These two:
text looks really weird at the top of all windows
some moodin splash screens are off center

I'll try to attach print screens for more info.
Maybe the weird text has to do with my nvidia driver.
I attached two print screen to show what the text is doing and three print screens to show what the moodin screen looks like.  One moodin splash screen is normal while the other two aren't.  By weird text I mean the text where the yellow border is at the top of two of the attachments.

---

### Post by gtdaqua on 2008-04-25
yeah, attach screenshots. they are more helpful. NVIDIA problems are really nothing. The driver needs to be recompiled (everytime the kernel is updated)

---

### Post by wandalalakers on 2008-04-25
This site is blocked at work so I'll have to respond when I get home this evening.  I attached five screenshots in my previous post.  Thx for responding!  I'm still enjoying kubuntu 100 times better than vista or xp!  I'm going to try the live cd on a laptop and see if the moodin off center splash screen problem still exists.

---

### Post by HunterThomson on 2008-04-25
I was using the Beta and got sick of it. I reinstalled 7.10 4 days ago. I am sticking to it for a long time. One major reason is a confirmed big in the kernel for the 64bit that makes my screen dim on boot/VLC/game... I am going to wait until I know that the problems I was having are fixed.

---

### Post by eye208 on 2008-04-25
> **gtdaqua said:**
> The soooo many problems are in majority due to simultaneous upgrades. Doing a distro-upgrade is going to take a lot of time and because of the network traffic your connection disrupts, the upgrade will break and you will run into problems.
You are wrong.

The upgrade process will first download all the packages and verify their integrity (digital signature, checksum) before even starting to apply any changes to the system. Nothing will be done until the last package has been downloaded successfully. You can interrupt the download any time and resume later.

If you blame broken upgrades on the package manager or network connection, you are barking up the wrong tree. For example, the issues regarding Pulse Audio were well-known, yet the developers decided to ship it.

---

### Post by wandalalakers on 2008-04-25
I fixed my text problem.
Now to see if I can fix my moodin problem.

---

### Post by Smudger on 2008-04-25
I updated to 8.4 and it refuses to recognise my monitor, so I have had to resort back to 7.10.

---

### Post by dawynn on 2008-04-25
My personal experience:

1) Feisty was a rock-solid version for me.
2) Gutsy was rocky from the get-go.  Lot's of problems.  Even glaring issues reported within a month after Gutsy's release, I was told, would just not be fixed in Gutsy.  I would just need to wait until Hardy.

My first install of Hardy was soon after it became available. I started using because Gutsy was not getting fixed.  Then Hardy crashed, and I've had to live with Gutsy.

Now, I've had about 2 days of Hardy with just a few issues I'm working through.  Since Hardy is supposed to allow for bug fixes (it is LTS), I'm here to stay.

---

### Post by wandalalakers on 2008-04-25
Umph.  It almost seems like 7.10 should be the LTS version.

---

### Post by rpage on 2008-04-25
I upgraded both an old dell laptop and my second desktop to 8.04 from 7.10 and have had only one issue so far. That is the sound on my desktop. And to be honest I have not had the time yet to even look at that issue more less resolve it. The laptop was super smooth and has not given me any issues yet. I will stick with 8.04 and see how it goes. I am new to Ubuntu and Linux (just a few months) and I must say, no matter what problems I run in to, I will NEVER go back to XP on either of my Ubuntu installs. Ubuntu is awesome!

---

### Post by wandalalakers on 2008-04-25
When opening openoffice, the menu bar doesn't look normal.  After uninstalling some programs using either adept or add/remove programs, menus now contains empty spaces.  some menus have items out of alphabetical order.

---

### Post by wandalalakers on 2008-04-25
> **rpage said:**
> I upgraded both an old dell laptop and my second desktop to 8.04 from 7.10 and have had only one issue so far. That is the sound on my desktop. And to be honest I have not had the time yet to even look at that issue more less resolve it. The laptop was super smooth and has not given me any issues yet. I will stick with 8.04 and see how it goes. I am new to Ubuntu and Linux (just a few months) and I must say, no matter what problems I run in to, I will NEVER go back to XP on either of my Ubuntu installs. Ubuntu is awesome!

Ditto.  I have no desire to go back to xp or vista.

---

### Post by Biggus on 2008-04-25
Comment Deleted

---

### Post by Nebutron on 2008-04-25
I have had no problems with my Hardy upgrade on my two home computers.  So far seems very stable.  Running 64 bit on one machine and 32 bit on the other. Both are AMD machines, one with a Biostart MB, the other ASUS.  Video on both is Nvidia.  From reading these posts, seems like I might be in the minority at the moment.  Still, I'm lovin the bird!  She is Hardy.

---

### Post by RJ Hythloday on 2008-04-25
keeping 7.10 xubuntu on the central pc, going to install 8.04 w/ kde4 on the media pc (soon) tried one of the beta's a while back and had some problems, haven't had time to get the media pc up and running.

---

### Post by dawynn on 2008-04-25
> **RJ Hythloday said:**
> ... going to install 8.04 w/ kde4 on the media pc (soon) ...

I also went the brave route -- jumping up to KDE4.  Now, its a matter of determining which bugs belong to 8.04 (having one boot-up issue) and which belong to KDE4 (warning: not for beginners).  So far, most of the issues I've seen are problems related to KDE4.

Cheers!

---

### Post by pholden on 2008-04-25
> **Holy Cheater said:**
> The only thing that troubles me: some weird things with monospace fonts.
This also bugged me after upgrading. In case nobody has linked the following threads, these helped me fix monospace fonts in the terminal:

[http://ubuntuforums.org/showthread.php?t=745094](http://ubuntuforums.org/showthread.php?t=745094)
[http://ubuntuforums.org/showthread.php?t=731136](http://ubuntuforums.org/showthread.php?t=731136)

---

### Post by dsiembab on 2008-04-25
what are all these bugs that need to be fixed? sure some minor inconveniences but I wouldn't call them bugs think of it as a learning experience. KDE is the buggiest. I'm using gnome and have no bugs. You can take any distro and put kde on it and you will see a big difference in error reporting gnome being a lot more slimmer than kde.

---

### Post by ROWDY!!! on 2008-04-25
On the bright side I've got sound, on the... not quite so bright side, it's very grainy. I assume this is another Pulse-Audio problem. 
Otherwise, in my humble opinion, Hardy has lived up to the hype! I'll definitely be sticking with it!

---

### Post by Pumalite on 2008-04-25
Best OS ever! Have 2 32 bit and 2 64 bit already rocking. Everything works. AND FAST.

---

### Post by Saya on 2008-04-25
Back on 7.10 for the sake of my sanity. I can't stand all the small annoyances. Hardy is Ubuntu's KDE4.

---

### Post by stymie61 on 2008-04-25
Upgraded my distro last night with no problems on my home computer. 
(AMD 64 3500+, 1GB ram, 30, 80, 2 -160GB HDD's w/ubuntu on its own drive). Got Flash and sound working in 5mins this morning before work. Haven't had much of a chance to play with it yet but seems to play well. 
   Only thing I still have to do is figure out how to stream hidef trailers (720p) without constant stopping to rebuffer. 
   will edit this post as I get to play around with it this weekend.

---

### Post by dfrandin on 2008-04-25
I'm not impressed with 8.04... Attempted a clean install on a new harddrive of 8.04 from alternate Cd. I find that the same problem seen in 7.10, ie: installer does not detect USB keyboard during initial setup (during install/verify disk/rescue menu), where a PS2 keyboard is needed to start install. Once the install continues, the USB keyboard is then able to be used.. Once install completes, and the system reboots, the splash screen is seen, xorg starts, the  spinning wheel cursor is seen, is able to be moved by the mouse, but is not spinning, and thats where the system stays.. The system in question is a Dell GX620, 4GB ram, Nvidia 8400GS/512mb video, and all this h/w worked swimmimgly under 7.04 on a different drive... Anybody else seeing these problems??

---

### Post by Perpetual on 2008-04-25
There should be an option on the poll for stick with 8.04, works great.  That's where my vote would go.

---

### Post by stymie61 on 2008-04-25
dfrandin, I have installed 8.04 beta release on my work computer using a usb wireless keyboard and mouse and it was detected with no problems. The beta version was kind of a problem on this computer with it constantly freezing on the splash screen. deleted everything and am going to try a clean install of 8.04 (which works good on my home pc)

---

### Post by bayonetblaha on 2008-04-25
I was doing fine, in fact it was absolutely wonderful except for no microphone, then I broke it :(

tried to install linux-backports-modules-hardy to get my microphone working, since the popular gutsy fix is to install linux-backports-modules-generic.

now my inspiron 1520 acts like there's no sound card (although it still shows up in lspci)

---

### Post by DrMega on 2008-04-25
> **Perpetual said:**
> There should be an option on the poll for stick with 8.04, works great.  That's where my vote would go.

There should also be an option for "haven't tried it yet, waiting to see what everyone else's experience has been".

I was going to wait a week or so anyway, to allow the server to recovering from the battering it will have inevitably taken over the last 24 hours or so.

The trouble is I'm waiting to rebuild my Media PC, and I don't want to install and configure twice. I reckon I'll give it Windows XP (which needs to be there for a piece of hardware I can't get working in Ubuntu), and leave it for a couple of weeks or so, and then give Hardy a go once it's teething problems have been ironed out a bit.

---

### Post by wadubois on 2008-04-25
pdoctor,

Based on your screenshots, I don't think it's a bug.  They've just got the text 'shadowed'.  It's in a setting somewhere (I can't recall off the top of my head as I'm @ work and haven't run KDE for awhile.)  But I can assure you it's a font setting somewhere that can be tweaked.

 - wayne

---

### Post by wkulecz on 2008-04-25
I voted other.    I installed 8.04 from the iso image to a spare partition.  I'll hang with it until its doing what I need, in the mean time, I dual boot into 6.06.

LTS releases only for me!

Can't really say anything yet about 8.04 as the repositories are timing out -- the bare install is utterly useless to me without even a command line C compiler!  (Edit:)  I spoke too soon, build-essentials seems to now be part of the base CD install it appears.  Progress.

But 6.06 has been solid and after the initial pain of using Synaptic to get what I really need, I've cloned half a dozen systems that are frequently used by others to run my software, maintainence has been pretty painless compared to my software that runs on Windows.

--wally.

---

### Post by FredB on 2008-04-25
Using Hardy since beta, no problems, will stay with it.

---

### Post by jedimasterk on 2008-04-25
Will skip this release since it won't install properly. I have allot of respect for Canonical and will continue to use Ubuntu. Just not this one!.

---

### Post by NR1224 on 2008-04-25
I have had no problems at all with 8.04 and plan to stick with it. There will always be inevitable bugs, but whatever. I trust that anyhting major will be fixed, and small random things cannot be blamed on the OS, but the hardware manufacturers without linux drivers

---

### Post by antemon on 2008-04-25
voted other.

will wait a couple of weeks (a month?)and dive back in. for some reason I get I/O errors when installing. :/

I'll prolly stick with 7.10 flavours or another distro before settling with 8.04 when I upgrade my PC. should be a little less buggy by then.

It's free, great support here and other places so I really can't btch about something I didn't pay for.

I like ubuntu and its derivatives :) no I'm not kissing ****.

---

### Post by sparky64 on 2008-04-25
I voted go back and will not.
My main production machine is never updated till at least 1 month-usually 2 after release. As It's production critical.
My laptop i upgraded but have had display problems - got nvidia loaded but still stuck at 800 x 600 (should be 1280x800) Also it flat out refuses to let me connect wirelessly. Have also had some probs with sound.

---

### Post by m61 on 2008-04-25
i chose other, did a fresh install of 8.04 onto my laptop and now have:
a) no wireless on laptop (centrino/intel wireless)
b) no audio in flash (had a similar issue in 7.10, fixed by reinstalling and not trying to mix pulseaudo and gstreamer)

i'm going to wait a bit to see if there are "fixes" available, after doing some browsing of the forums, found some fixes that might work, will try them when i get home

worst case, i'll downgrade to 7.10 as i had 0 problems out of the box and everything worked

---

### Post by QauNuckShin on 2008-04-25
I voted "keep with 8.04 and wait for fixes", but I'm currently leaning towards.. something else. Probably gonna try a clean install of 8.04 first, and if that doesn't help, I'm reinstalling 7.10.

---

### Post by pbpersson on 2008-04-25
I installed Hardy on my test machine.  This thing has an ATI Radeon 9550 card and this is the best Ubuntu/Mint experience I have had thus far.  Due to this stupid video card, the live CDs of some distros won't even display anything on the monitor.

I think I will be staying here

My main machine is still running Kubuntu Gutsy

Hey.....people.....the Hardy repositories are running really slow.  Can everyone else on the planet please stop downloading new Hardy packages for a few hours so I can get mine faster?  ;)

---

### Post by pancakelizard on 2008-04-25
well if i could get someone to look at the thread i made and help me out, i would use it

[http://ubuntuforums.org/showthread.php?t=765902](http://ubuntuforums.org/showthread.php?t=765902)

---

### Post by pancakelizard on 2008-04-25
double post

---

### Post by lefty_lou on 2008-04-25
Well i upgraded like an hour after the release by means of the system upgrade and must say not good..
lost my mouse config a 5 button one can't seem to get it back 
lost the emerald window borders can't apply any of them i only use the emerald studio one anyways but i want it back!!
also having problems with audio
and some weird things like for example have the normal Hdrive icon on desktop streched, after the upgrade it's all distorted and tried changing it to scalable but same thing happens and it's only that one 
the upgrade erased my cinepaint why???? and i know because i saw when it sayd it would do it with no options to stop it
FF3 b5 by default??? i only have 4 out of 23 addons working this should have been an option giving me the choice of what to do...
can't access my virtual drive since the new mount handler program changed the naming of the drives even my torrents got affected by this when i open azureus all my listed torrents have errors 
well God only knows what else i migth find but for something that's free can't say much only suggest forget about deadlines for a release do it when it's fully tested don't do the redmond mistake to push it out just because u said it would be done by x date. keep up the good work and hey we all have problems some wayyy more then others don't believe me look at vista LOL!

---

### Post by ashur@trogdor on 2008-04-25
I'm having zero problems. I didn't see the option for that in the poll...

---

### Post by chih on 2008-04-25
I upgraded to 8.04 and to be honest I haven't had full opportunity to explore it, but I'm easily thrilled and I have to say that the mouseover playback on audio files blows my mind, haha. I haven't run into any problems at all, except for a minor flash error that was easily fixed with terminal (literally using two commands).

---

### Post by mhenry35 on 2008-04-25
Hardy has been very good for me, only one issue which I list as an annoyance, and I think the culprit is actually Firefox 3, not Hardy.

Hardy worked out of the box for me with no edits!  I reformatted and installed the beta from scratch, then applied all updates throughout the process, and Hardy has been excellent, it's the first release that properly handles my wireless, widescreen laptop panel and large widescreen external monitor.

Gutsy, on the other hand was not usable for me.  I finally was able to get my monitor working by installing the old intel driver and applying my manual edits to xorg.conf and using a shell script I wrote to run 915resolution twice.  It never did work right with my wireless card, cutting me off the internet, and regularly losing connections.  I Downgraded back to Feisty and used that till the beta of Hardy came out.

You see reactions like this for each release, some people hate it, some love it, just depends on how it works for you.

---

### Post by tparker on 2008-04-25
> **pcdoctor said:**
> These two:
text looks really weird at the top of all windows

Sorry if this is a dumb suggestion, but are you sure that your video settings are correct for your monitor? Those screenshots look the same as my text looked when I had my screen resolution and refresh on settings that were not the same as the recommended ones for my monitor.

---

### Post by wandalalakers on 2008-04-25
> **wadubois said:**
> pdoctor,

Based on your screenshots, I don't think it's a bug.  They've just got the text 'shadowed'.  It's in a setting somewhere (I can't recall off the top of my head as I'm @ work and haven't run KDE for awhile.)  But I can assure you it's a font setting somewhere that can be tweaked.

 - wayne

I fixed my problem earlier this morning. (text problem) I still have no sound and when I ran compiz the window froze. I bit the bullet and did a 8.04 clean install.  I have sound now.  I hated to do a clean install since I had everything the way I liked it.

---

### Post by Fingers &amp; Thumbs on 2008-04-25
I came to linux with ubuntu 7.04 and upgrading to ubuntustudio 7.10 was pretty smooth. Upping it again to 8.04 has, for me gone flawlessly. Yes, there are certain things that I'm used to having, missing; Nvidia not correctly configured, various codecs, and some little extras such as the nautilus extentions that allow for opening terminal in arbtrary places from the context menu. But I was fully aware before upgrading, that most dissappointments would arrise from proprietary drivers and codecs, as well as some additional OSS.

Hardy Heron, as it is, for me, is superb. Already I have had a good opportunity to put the additional ubuntustudio packages through their paces and it works like a dream. With my past years experience with ubuntu, I am confidently happy that those missing elements will be along shortly. In the meantime I have plenty to play with.

---

### Post by dfrandin on 2008-04-25
> **stymie61 said:**
> dfrandin, I have installed 8.04 beta release on my work computer using a usb wireless keyboard and mouse and it was detected with no problems. The beta version was kind of a problem on this computer with it constantly freezing on the splash screen. deleted everything and am going to try a clean install of 8.04 (which works good on my home pc)

I'd think it was just my usb keyboard, but when I first saw the
problem during the install of 7.10, I tried several USB keyboards, none of which would allow me to select anything on the initial menu of the installer.. To get past that I had to put a PS2 keyboard on, which allowed me to select "verify cd" then "install os".. Once the installer actually started, the menus and places to name the machine etc. worked ok with the usb keyboard... I even tried different usb ports on the system... just does not like usb keyboards on this Dell system.. tho I never saw the problem when installing 7.04 on it last year...

---

### Post by stoneage on 2008-04-28
Remove Cinepaint, remove Yafaray? - I nearly didn't update! Decided to go for it anyway and compiled Yafaray from source, - now going after Cinepaint.
I'm happy with the update - as well as everything else I now have a more current Yafaray, and hopefully Cinepaint soon. 
I have nothing to complain about.(Actually, there is one thing - the Ubuntu Studio site still claims Cinepaint is bundled with Ubuntu Studio Video, but if it is I can't find it)

---

### Post by Nidding on 2008-04-28
As I can't even make my machine to install Hardy, I'm pretty convinced that I'll try to reinstall Gutsy.

---

### Post by yyyc186 on 2008-04-28
They are many.

1)  Any user of ATI, Nvidia, or Intel graphics chipsets are going to curse their own mothers for bringing them into this world when they try to upgrade.  8.04 is NOT an upgrade!  IT IS A WIPE AND RE-INSTALL.  The hardware detection software is broken badly.  If you have ANY of the restricted drivers running it will NOT detect your hardware.

2)  The "easy uninstal" option is non-existant once you upgrade.  I don't know why they are splashing such a thing on their main Web page.  It's as pointless as the "just works" slogan they used to use.

3)  Once again, the "final" release worshipped at the alter of the cave dwelling Gnome and shafted the users of the much more robust and user friendly KDE desktop.  Only Gnome is currently in the ISO you pull down.  When you run the upgrade it takes it upon itself to uninstall "obsolete" software such as KDevelop.

4)  Once you upgrade the Gnome side, you have to reboot to your KDE session and do a partial upgrade.  There is no method other than doing this on-line.  If you have a satellite connection with 120-250Meg/day download limit, you will never be successful.  The powers that be have not included a throttle option.  They expect you to download 559+Meg in one shot.

5)  Even if you have OpenOffice Base running before you upgrade, it won't be there when you are done.  In order to save space, they nuke it.  You have to install it from scratch again.

That's all I've found so far.  I had to do a wipe of the notebook I tried to upgrade.  If I had my original Gutsy distro DVD here at this client site with me, I would be back to Gutsy in a heart beat.  8.04 should be pulled from release, only Microsoft ships software in this sad shape.

---

### Post by Stanley Krute on 2008-04-28
I used the Alt CD upgrade technique on a Toshiba Satellite.

The Toshiba ran well. No problems. 7.10. Graphics and sound and multimedia and networking and wireless networking all good.

After the upgrade, I have graphics issues and no sound.

Blecccch...

I don't think it's the network. It's the bugs.

-- stan

---

### Post by wandalalakers on 2008-04-28
> **yyyc186 said:**
> They are many.

1)  Any user of ATI, Nvidia, or Intel graphics chipsets are going to curse their own mothers for bringing them into this world when they try to upgrade.  8.04 is NOT an upgrade!  IT IS A WIPE AND RE-INSTALL.  The hardware detection software is broken badly.  If you have ANY of the restricted drivers running it will NOT detect your hardware.

5)  Even if you have OpenOffice Base running before you upgrade, it won't be there when you are done.  In order to save space, they nuke it.  You have to install it from scratch again.



I think openoffice math disappears after the upgrade also.  Yes, I agree about the part for users of nvidia.  I told a co-worker who wants to try linux to download 7.10.  My Dell laptop locked up twice with 8.04.

---

### Post by bingobingo on 2008-04-28
Any suggestions on the best way to downgrade? I do not have 7.10 cd, but if I did would I need to do a fresh install? Needless to say I forgot to backup to an external hd before the upgrade. The upgrade was a breeze going back is going to sting alittle.

---

### Post by Stik on 2008-04-28
I'm guessing the million other people who are having minimal to 0 issues
aren't venting in the forums or this place would be berzerk... Where is the
option for no issues????

---

### Post by aleuy on 2008-04-28
Since I have upgrade to 8.04 in my laptop I can't use the webcam, I can't hibernate or suspend and the power management is broken too!!! All this things were working on my 7.10 installation. The only new thing that now work is the wireless light.
I'm going to stay with 8.04 for some weeks and see what happens. If nothing change in few weeks I will have to go back to the great 7.10

---

### Post by vinsenjunior on 2008-04-29
I'm running HP 6910p laptop with Core2Duo Santa Rosa, intel 3945 wireless and ATI x2300.

I clean installed Hardy several days ago and here's what I've found going on in my system

Pros : 
[LIST]
[*]better ATI driver. It detects 1280x800 res right from the live CD
[*]I can now suspend/hibernate my system (I couldn't in Gutsy). This is probably related to updated kernel/graphic driver.
[/LIST]

Cons :
[LIST]
[*]Wireless not working. Major showstopper for me. 
[*]Slow boot
[*]Most Firefox plugins are not supported for FF3 beta
[/LIST]

So I came to a conclusion to reinstall Gutsy. The only problem is the suspend/hibernate.

It's only 5 days from the initial release and I think Hardy will be great after some improvements, but I'll stick with Gutsy for now.

---

### Post by robsic on 2008-04-29
I already downgraded to 7.10 (see earlier post here: [http://ubuntuforums.org/showthread.php?t=772002](http://ubuntuforums.org/showthread.php?t=772002)).
Since the problems that was introduced by the upgrade persists, possibly because the lacking support for downgrades, I'm going to do a fresh install of 7.10, might even consider switching to Debian Etch...

---

### Post by mtbsoft on 2008-04-29
> **yyyc186 said:**
> Any user of ATI ... graphics chipsets are going to curse ... when they try to upgrade.
Perhaps with an upgrade but not on a fresh install.

> **Stik said:**
> I'm guessing the million other people who are having minimal to 0 issues
aren't venting in the forums or this place would be berzerk... Where is the
option for no issues????

Amen to that.  I took the safe route of putting 8.04 onto a spare partition on my laptop (Inspiron 9400 with ATI X1400 graphics) and I'm happy as a pig in muck.

* For the first time I didn't have to use the ALT installer.
* The graphics came straight up at 1920x1200 with no problems.
* Installed the restricted ATI drivers and I have full compiz.
* Suspend works - didn't with Gutsy
* Hibernate works - didn't with Gutsy
* Touchpad works
* WiFi works (although the light doesn't come on [edit: and the keyboard switch doesn't work] but I don't really care)
* I use Opera so don't care about the FF issues.
* The fans appear to work without i8k
* It even has a sort of mouse trails in Compiz (which I wanted)
* SD card reader works

I haven't checked all my peripherals yet but it does all the stuff I **need**.  Basically, I'm thoroughly happy with this release which fixed many of the issues I lived with in Gutsy, particularly related to the ATI card, and improved other areas as well.  Just need to backup all my setting and so forth then blow away Gutsy for a fresh install.  Rock on Hardy!

---

### Post by arkangel on 2008-04-29
I had to tweak  7.04 a little bit more (xorg.conf  alsa, etc)  and it was solid like a rock    

8.04 works almost all, still working on it ,let see,  seems to react slower,   thinking in using another windows manager

---

### Post by jerrylamos on 2008-04-29
Not me.  I've got Hardy Ubuntu, Kubuntu, Xubuntu running on 2 PC's in several partitions, shared /homes.  For what I do it's just fine, best linux yet for me.  I do local lan folder sharing, Office, lan printer, internet videos on a number of sites, internet email, internet news & research, digital pictures, etc.  I'm into applications, not eye candy, so I don't do Compiz.  I don't do games either.  My occasional laptop use is Feisty 7.04 (if it isn't broken don't fix it).  By the way, I've been on PC's since 1982.  Now Hardy Alpha's & Beta's were as might be expected rough and busted so I had Gutsy in other partitiions to fall back on.
Jerry

---

### Post by wpshooter on 2008-04-29
I have tried it but do not like what I see.

Will try again once they come out with Hardy 8.04.**1**

Thanks.

---

### Post by rulorojo on 2008-04-29
I switched (through an internet upgrade) from 7.1 to 8.04 with almost no problems. The main nuisance was to make this version understand that my video card (nVidea mx4000)can process 1280 x 1024.Solution to it, came from Ubuntuforums. The system detected (without asking for specific drivers) my USB Wifi adapters, I tried 2 diferent adapters: Linksys WUSB11 v2.6 and a new EUSSO UGL2454-U2ZA (this has detachable antenna , more gain). This last device is shown as eth2 and not as a wlan.... as everything works, i will not try to convince the OS to change it's mind....
 
The first impressions are that programs open faster...? is this possible ? I will keep this version.

Ubuntu 8.04 is running on an Asus P4C800 deLuxe with 512 Mb RAM and a Pentium IV 2.6 Ghz.

---

### Post by Invader Amoto on 2008-04-29
I chose other.
Technically I am using 8.04 but only from the live disk.
I experienced this problem with the beta (and with the final release but i had to do something else to get it working (semi)properly. see here: [http://ubuntuforums.org/showthread.php?t=771115]("http://ubuntuforums.org/showthread.php?t=771115"))

---

### Post by tekguy on 2008-04-29
I'm rockin a clean install of 8.04 and it is running smooth. I haven't had any problems with it at all. All the nice compiz effects work now too. I couldn't get them working before.

---

### Post by bhold on 2008-04-29
I voted keep 8.04 and wait for patches. Only 2 problems so far.
1.) During installation from 8.04 Desktop Live CD, at the initial screen where I am asked to select a language, I had no mouse or keyboard control. After waiting for the timeout and default selection of US English, the installation proceded with no problems.
2.) I have hit the bug re: Nautilus inability to access folders shared from a Windows system, but the workaround with smbfs (just mount the share) is simple, not enough of a problem to go back to 7.10 for.

I do like the Mozilla Firefox 3 Beta feature that when a plugin is needed (e.g., to play flash files), I am notified of available alternatives for installation. I'm currently trying swfdec instead of adobe flash - so far, so good.

---

### Post by ezsit on 2008-04-29
I have Gutsy installed on three computers, two home-built and one Dell 2400. All older hardware (P4 single core 32bit cpu and Athlon 2500, 512mb-1gb RAM, PATA hard drives, Gforce 4 video cards, etc.) and Gutsy runs swimmingly on all, so did Feisty.

I tried the live cds of Kubuntu (3.5.9 and 4.0), Xubuntu, and Ubuntu. All cds boot but take a long time and the desktops are ugly. The fonts look bad and the screens are grainy.

The program versions do not add anything for me that justifies an upgrade at this point. Everyone seems to complain about Gutsy's bugs, but for me they just don't show up. I use Kubuntu 7.10 and will probably do so until 9.04 comes out.

---

### Post by mrand on 2008-04-30
> **robsic said:**
> I already downgraded to 7.10 (see earlier post here: [http://ubuntuforums.org/showthread.php?t=772002](http://ubuntuforums.org/showthread.php?t=772002)).
Since the problems that was introduced by the upgrade persists, possibly because the lacking support for downgrades, I'm going to do a fresh install of 7.10, might even consider switching to Debian Etch...If you're going to do a fresh install, I'd recommend at least trying 8.04.  Upgrades for even the most simple things can be quite tricky, especially when compared to fresh installs.  The last thing I would want to do is park myself on an old release unless the new one just flat out doesn't work (after a fresh install).

   Marc

---

### Post by arpanaut on 2008-04-30
Voted other: 
  
Not a chance I'm going back, I had so many issues with gutsy I installed Hardy alpha 4 and haven't looked back....

Did change out my ATI 9800 Pro for nVidia 7300 GT and couldn't be happier.

I've been on ubuntu since Warty and other than gutsy not working well for me I'm a dedicated convert....I about gag when I have to boot windows  LOL

My apologies to those of you having problems...

HARDY ROCKS!

---

### Post by Baconfatty on 2008-04-30
well once i got the NVIDIA drivers working its fricken sweet

---

### Post by FoxOne on 2008-04-30
I'm of the mindset if it works, and it's secure, why move forward. That being said my wife's computer is getting 8.04 treatment this coming weekend as I'm done dealing with 6.06 anymore.

---

