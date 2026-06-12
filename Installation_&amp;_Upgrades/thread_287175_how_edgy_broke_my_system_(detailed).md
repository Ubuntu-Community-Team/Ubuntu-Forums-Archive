---
title: "how edgy broke my system (detailed)"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by mnp5 on 2006-10-28
Ladies and Gentlemen --

I am proud to present a short narrative detailing how upgrading to edgy broke my system.  It goes a little something like this:

1) See that Edgy was released, get excited

2) Read installation documentation.  Check for peculiarities with respect to Kubuntu.  None seem to present themselves.

3) Follow instructions at [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades).  Run gksu "update-manager -c".

4) gksu chugs along nicely, downloading a bunch of files.  This takes about an hour -- I was getting 500kb/sec off of the mirrors.

5) All packages download successfully.  Unpacking/configuration process begins.

6) During the upgrade, update-manager mentions that /usr/X11R6/bin is going to be replaced with a symlink.  Unfortunately I'd installed opera-static, which left its own worthless symlink in /usr/X11R6/bin that update-manager wasn't aware of.  Since there's a file in the directory, update-manager refuses to remove and re-link /usr/X11R6/bin and borks out.  This is sensible enough.  I enter the dir, remove the symlink, purge the package and re-run update-manager.

7) update-manager says that my system is screwed (installation in incomplete state, no packages can be added/removed/whatever).

8) I start running aptitude in an attempt to get the remaining 500 downloaded but unconfigured packages installed.  I probably run aptitude and/or apt six to ten times before I'm able to get things sorted out.  This is because of a lot of stupid dependency issues.  Several useless packages are purged (by useless I mean things like python-html or whatever).

ps mr. author of the forum software: when someone writes the number eight and puts a closing parenthesis after it, it might just mean "number eight in a list" instead of "idiot smiley with sunglasses."  oh well.

9) Finally I get to the point where aptitude/apt isn't doing anything when dist-upgrade is requested.  I sigh a long sigh of relief and decide to reboot.

10) On reboot, kernel panic -- grub has somehow gotten the wrong idea about where my root filesystem is.  I use software RAID on my desktop machine, so grub really should be looking at root=/dev/md0 instead of root=UUID:some_bunch_of_incoherent_nonsense.  I edit the grub command-line and get past the panic, but the system stops booting after loading the ps/2 mouse driver.  Why? Possibly because I'm running a custom kernel and the whole damn init system has changed for some reason.

11) I screw with the grub boot parameters until I remember to specify root=/dev/md0 and init=/bin/bash and can at least get a shell -- on a read-only root filesystem, anyways.  This allows me to confirm that nothing worse than a grub screwup has taken place.

12) On my next reboot, I notice Edgy has installed 2.6.17.10-386, so I decide to forego booting my custom kernel (did I mention I don't like modules?  I don't like modules and build only the drivers I need -- statically) and hit 2.6.17.10-386 instead.  I have to specify that root=/dev/md0 instead of UUIDblahblah, but that's ok.  The system boots up fine.  The only problem is that Firefox 2.0 is buggy as hell, ie. crashes fairly frequently, and the system is now noticeably slower than it was before -- it used to take less than a tenth of a second to open an xterm; now the xterm opens, but I wait .5 for bash to give me a prompt.  And no, this system isn't THAT underpowered -- it's an xp3200 with two gigs of RAM.  It does now have over 100 modules loaded, however and I've noticed that doing a middle-click copy into nano takes like two seconds to complete.  Hurrah.

Now I'm a reasonably adept user, so this wasn't show-stopping for me.  Fixing my system after the upgrade did take a while, though, and that was irritating.  I don't know what I would have done if I didn't have substantial linux experience already (mind you, if I didn't have substantial linux experience I probably wouldn't be doing weird things like running custom monolithic kernels and software RAID on my desktop box).  I can definitely sympathize with the homies who have said "damn, edgy broke everything!"  My question is why when update-manager encounters the (predictable) /usr/X11R6/bin problem it halts instead of presenting the option to open a terminal, fix the problem, and then continue the upgrade.

Now I don't want to sound ungrateful or excessively sarcastic.  The people who do Ubuntu development have far more technical skill than I do and they produce a product that is more or less better than any other linux distribution.  That said, however, it'd be nice if someone would actually test the upgrade process exhaustively before releasing it to the public.  Similar nonsense happened to me when I went from hoary (or was it breezy? whatever came right before dapper, anyways) to dapper.  The reason why people don't use Linux is because it takes forever to do things that are simple in Windows XP, like get hardware to work or upgrade software on your computer.  Ubuntu goes a long way to closing that gap, but unfortunately not nearly long enough.

Oh yeah, one more thing.. anyone have any clue as to wtf the new init binary is actually called and how I can manually call it from grub?  I'd like to get back to my non-crap kernel as soon as possible, I expect it might deal with some of the abysmal slowness problems I'm currently experiencing..



best,
mnp5
montreal

---

### Post by mr_fong on 2006-10-28
I was just smiling the whole way through reading your posting. I am using Debian (and Linux for that matter) since 1999, know my way around the system - although I also am no wizkid - but right now I feel like a *little* kid, not in command of my own toys anymore. Why do these grown-ups screw things up for me every time? --Hans

---

### Post by Koybe on 2006-10-28
Just one thing I can say : 8)
But I can't help you for the other things!

---

### Post by TheWizzard on 2006-10-28
mmm, upgrading is kind of tricky by definition. 
it should work painless on a box with standard hardware and very default configuration of ubuntu. but can be hard in other situations. 

i have to admit i'm very new to ubuntu. i made my switch just when ubuntu appeared. before ubuntu i used red hat / fedora and i did not upgrade every time because the backports were pretty good and ensured i had the latest packages. i only upgraded when my install was no longer supported. 
when i upgrade i always do a clean install to make sure the system is perfectly stable. 

because a clean install takes a few hours i'm sticking with dapper at least untill the next version of ubuntu is released and i'm curious to see how the backporting works in ubuntu. i hope it works fine, so that dapper is really a LTS!

---

### Post by cotcot on 2006-10-28
My upgrade from (a fairly buggy) dapper to edgy on an AMD64X2 was spotless just using the instructions of the ubuntu guide.

---

### Post by theosib on 2006-10-28
Re: Software RAID

Are you using RAID 1 or RAID 0? 

I had set up a software RAID 1 with Dapper, and when it was all installed, I did some investigating and testing, and I discovered that (a) grub was not installed on the secondary drive, and (b) menu.lst was not set up correctly to be able to boot from the second disk.  If I'd had a failure of the primary drive (without manually fixing the problems) I would have been up the creek.

Have you tried pulling power from your primary drive just to see if you could boot from your secondary?

Anyhow, this is just one of the many reasons why I don't think I'm EVER going to try to upgrade to Edgy.  I'm sure it's nice, but I have things working, and I'd like them to stay working.  I'd really LIKE to upgrade, but I'm 110% sure that it's going to be nothing but misery.

Here's a reference regarding software RAID:
[https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/68308](https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/68308)

---

### Post by mnp5 on 2006-10-28
To my friend the Belgian (cotcot):

Thanks so much for your helpful response! :P

To theosib:

It's raid 1 (raid 0 is asking for trouble -- substantially increases your risk of losing everything, as there's now two disks to fail and if one goes you're screwed).

Yeah, boot loaders are on both drives and all that good stuff.

I'm probably going to manually downgrade, even though that implies several hours of work.  My suggestion: don't upgrade.  This is NOT a stable release AT ALL; it's practically a frigging public beta.  Busted web browser, general slowness, etc. etc.

---

### Post by theosib on 2006-10-28
I'm thinking someone should write an article that summarizes all of the problems that people are having with the upgrade.  Just something generally informative, something that the developers can use as a reference, perhaps.  Perhaps if they have something more organized, it'll help them fix the problems quicker.

---

### Post by mnp5 on 2006-10-28
Fixed, partially.

In order for upstart to work you have to have "Inotify file change notification support" turned on in your kernel config.

Now I'm having ubuntu-related kernel compilation problems, whcih is another matter entirely.

---

### Post by hahafaha on 2006-10-29
I am running a Dell (Gasp!) C600 laptop. I upgraded to Edgy the day it came out. Here is what happened with me:

I was not running anything special -- default kernel, file system, etc. I did have a configured xorg.conf file, however. Upgrading took a while, the server I was using was swamped. Now, for those that don't know, the C600 series are known to occasionally overheat and crash, that is, a hardware crash, and the only way to get out of it is to press the power button and restart.

Now, because the server was swamped, upgrading took a long time and at some point, the hardware crashed. I had no choice but to reset it by hand. At this point, update-manager said that it can no longer proceed, since there were broken packages. I ran sudo aptitude dist-upgrade and it seemed to work. It said that I need to restart the system. I did.

The computer booted me into a strangely 2.14-ish GDM. I attempted to long into it, but it just displayed a blank screen. I restarted the computer again, and this time, it said that the X server crashed, because it was looking for /dev/wacom, and it was not there. Fortunately, I had a backup xorg.conf file, and after quite a bit of tweaking, I was able to manually fix it.

Before restarting GDM, however, I decided to run dist-upgrade again. Whoops, another good 500 packages to upgrade. I ended up running it again (several times), and finally got it to fully install.

The good news is that now I am running everything normally, and have no real complaints. I do not know if the reason the upgrade was troublesome was because of the crash or not, though.

---

### Post by mnp5 on 2006-10-29
What I find kind of surprising is just how much the stock Ubuntu kernels suck.  After getting my custom kernel back up again I saw a performance increase of about 50% everywhere -- on bootup, when opening applications, hell, even when redrawing the screen.

Sorry about cha laptop, pal -- good thing you knew what you were doing! :)  This is an experts-only upgrade, ha..

---

### Post by benmoreassynt on 2006-10-29
I reckon some of the slowness may have been a hangover from the problems you had upgrading, rather than a sucky kernal. I've got Edgy on a 500MB Compaq laptop with a bog standard P4M, so a quarter the RAM you have and an oldish CPU, and it's very quick - I'd say quicker than Dapper, although that's subjective. Quicker than my 1GB XP desktop anyway. None of the 2 second cut and pasting you mention either.

I suppose part of the reason that Linux never manages the smooth upgrades of Windows is because you are allowed to poke around with the kernal and do all sorts of wierd stuff. It's easier to upgrade a system that outlaws 95% of tinkering. I know the one bit of tinkering I have to do is get my wireless card going with ndiswrapper. Every upgrade breaks it, but I've got fixing it down to a fine art. Then again I'm using a wireless card that was almost 'deliberately' designed never to work with Linux, but works very well, so I can't complain.

---

### Post by TheWizzard on 2006-10-29
> **benmoreassynt said:**
> 
I suppose part of the reason that Linux never manages the smooth upgrades of Windows 

like upgrading from w98 to xp?!?

---

### Post by benmoreassynt on 2006-11-02
Shouldn't have said 'never'. However I was answering a comment about upgrades being a hindrance to people moving from Windows to Linux. All I was suggesting is that freedom comes at a price. If you customise your Linux PC a lot then you've got to expect to run into some problems. Personally I've never had major problems upgrading Ubuntu. Quite the opposite - I think it's miraculous just how smooth upgrading Ubuntu has been for me, and it seems to be one of the key reasons to use the distro.

---

### Post by myke on 2006-11-02
I have a crashed system as well and can't seem to find anyone here who has any suggestions.  I smoothly upgraded from breezy to dapper but dapper to edgy has really set me back.  Very frustrating especially considering I followed the suggested instructions for upgrading TO THE LETTER.   Now the Linux kernel won't even boot up properly and I'm left with this:

(initramfs)

I don't know what the hell that is but it won't let me put in command prompts to get upgraded or fixed via apt-get.   If I can't get this fixed I'll be forced to go back to XP which will suck as I've used Ubuntu for over a year successfully but can't stomach the thought of all the data I might be about to lose.  I know ... my fault for not backing it all up but who woulda thought and upgrade would prove so frightful??  XP isn't that problematic and I have to say ... ALOT of folks seem to be having problems from dapper to edgy.  There has to be a way to ensuring the upgrade process isn't so filled with problems before releasing a final candidate.

---

### Post by ronacc on 2006-11-02
Heck I was going to start another thread but I'll add my bitches here. My upgrade from dapper to edgy beta to edgy went ok(amd athalon64 and nvidia graphics ) the upgrade even picked up on the nvidia driver . my problems started when I tried to compile the pchdtv drivers after a couple of days of dead ends ( ok so Im slow) I started digging around and found several broken symlinks in (possibly) critical places , so I bit the bullet and wiped the drive (losing all my add ons and settings etc) and did a fresh install from cd ( release edgy amd64) ho boy things got worse in a hurry. 1 the broken symlinks are there right out of the box 2 edgy completely mis identified my monitor and video card dumped me in to generic crt (its a samsung lcd) and generic vesa driver. atleast that was easy to straighten out. still wont compile pchdtv drivers. also on another box same thing about the video (its a samsung crt and via chrome9 IGP) since I cant get that one straight the graphics are amost unusable even for text slow and jerky edgy also wont compile the via k8m890 drivers from via ( that may be via's fault the makefile is oriented tword redhat/suse) but why dosent Ubuntu atleaset have restricted packages for a very common graphics chipset.and their "vesa" driver is orders of magnitude slower than the vesa driver in puppy linux which I use to recover from the "blank screen" which edgy seems to drop you into at the drop of a sudo. I hope they get their act back together for feisty. I'm giving it about 2 more days and then I'll give this 40gig to my Suse install and the other box I'll play with some other distro.Dapper was pretty good  but if there is no path forward it's a dead end and right now edgy looks like more greif than I will put up with.
 My main reason for trying Ubuntu was to have something to recomend to my windows using friends when vista nukes their boxes, ( I,m a dedicated SuSe user but was looking for something to ease the microsucks users into the world of linux) and as much as I love SuSe, a 5 cd install and dependency hell is not the way to go , anyone that has used yast knows what I mean , apt/synaptic is way better.
 Like I said dapper was pretty good but it looks like they really stepped in it with edgy.

---

### Post by heffo_j on 2006-11-03
G'day all,

It is disapointing to see so many threads expressing grief and frustration over the Edgy upgrade. I hadn't done it yet because I've been stung before with a FC4-FC5 upgrade and also Breezy to Dapper. 

I have however installed it on my VMWare  partition and it seems okay there (but not my DLink wireless). I did have a problem with X when I changed over to Dapper from Breezy, but it was a common problem which was identified early after the upgrae and a solution was on the web pretty quickly. 

With Edgy, it seems the problems are everywhere. 

It is really annoying to try and convince others of the benefits of Linux when the (reputedly) best distro can't get it right. I think Ubuntu has been reading too much of its own PR and starting the believe it. It sadly reminds me of another popular OS starting with the letter W........

Best regards
a disappointed
John

---

### Post by TheWizzard on 2006-11-04
> **myke said:**
> 
ALOT of folks seem to be having problems from dapper to edgy.  There has to be a way to ensuring the upgrade process isn't so filled with problems before releasing a final candidate.

edgy is not suppost to be a stable version like dapper. edgy is suppost to be "edgy". 
if you want to have a stable os you should use dapper.

---

### Post by mojoman on 2006-11-04
> **TheWizzard said:**
> edgy is not suppost to be a stable version like dapper. edgy is suppost to be "edgy". 
if you want to have a stable os you should use dapper.

I do believe Edgy is (supposed to be) stable by now. ;)

---

### Post by ronacc on 2006-11-04
They considered Edgy "stable" enough for release . it acts more like alpha . I also discovered that it is throtling my Amd64 X2 back to 50% I can correct this with the gnome applets  cpu monitor configured to allow the user to adjust the cpu freq but it dont remember the setting and has to be done each boot. strangely  edgy dosent do this on my single core amd64 .(bios pwr management is OFF on both boxes ) gnome pwr management is set to do nothing and never. Anything this buggy should probably be late alpha not even beta and damn well not "release" . I dont mind testing software but I want to be warned .

---

### Post by TheWizzard on 2006-11-06
> **mojoman said:**
> I do believe Edgy is (supposed to be) stable by now. ;)

yes, but as far as i know it is an in between version and the project was started to try out some new things. dapper is a long-term support version. 
from the download site: 
> Ubuntu 6.10, the newest Ubuntu release: If you would like to benefit from the latest Ubuntu features, this is the release for you
Ubuntu 6.06 LTS, Ubuntu with long-term support: Choose this to benefit from the long support life-cycle of the 6.06 LTS release. This version is supported for 3 years on the desktop and 5 years on servers.

in other words: edgy if you want to play around and dapper if you need your computer for work.

---

### Post by Codefreeze on 2006-11-06
> **TheWizzard said:**
> in other words: edgy if you want to play around and dapper if you need your computer for work.
n00b here! I'm sorry but that advice wasn't warning enough for me, I went for the edgy option thinking this was the most up to date, stable release and the one to go for...

Just to give you of an idea of the decision a one-day newbie would make, based on the information on that front page - install the latest "edgy" release! There is nothing to suggest it isn't stable and is only for experts (isn't that what alpha/beta is for). hth

---

### Post by TheWizzard on 2006-11-07
> **Codefreeze said:**
> n00b here! I'm sorry but that advice wasn't warning enough for me, I went for the edgy option thinking this was the most up to date, stable release and the one to go for...

Just to give you of an idea of the decision a one-day newbie would make, based on the information on that front page - install the latest "edgy" release! There is nothing to suggest it isn't stable and is only for experts (isn't that what alpha/beta is for). hth

edgy is pretty stable, but i think dapper is more rock solid and thus better if people want to try out ubuntu. 

i agree with you that the text could be more clear.

---

### Post by ronacc on 2006-11-07
Perhaps stable isnt the right word mabye useable is a better one its not that edgy crashes alot ( although some people cant get it to even finish installing or run from cd ) it is that it does many things WRONG without crashing . misdetects video and throtles cpu come to mind strangely the fresh install screws up more stuff than an apt update (atleast on my system)

---

