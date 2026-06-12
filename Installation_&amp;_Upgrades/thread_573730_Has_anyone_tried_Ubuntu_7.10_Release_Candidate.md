---
title: "Has anyone tried Ubuntu 7.10 Release Candidate"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by wasim2050 on 2007-10-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/151817](https://bugs.launchpad.net/ubuntu/+bug/151817) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just download and installed Ubuntu 7.10 Release Candidate to try out if everything is working fine or not before the grand release of Ubuntu 7.10 as it says on the website "We consider this release candidate to be complete, stable, and suitable for testing by any user."

[HTML]http://www.ubuntu.com/news/ubuntu-7.10rc[/HTML]

So after installing the 7.10 rc the first thing I noticed was that during the loading of the system when we see the ubuntu logo at that time my monitor does not support the resolution and goes out of sync and after sometimes when the system comes to the login screen my monitor become ok and thats seems strange to me because this does not happens in ubuntu 7.10 beta. So I reboot it a couple of time to make sure and everytime my monitor goes blank until the system comes to the login screen.

I have reported it as a bug not sure if anyone has faced the same problem or not.

[HTML]https://bugs.launchpad.net/ubuntu/+bug/151817[/HTML]

---

### Post by dabl on 2007-10-11
Yep, I've been running Gutsy since Tribe 5.  It's currently running and the only issue I've had is the RT kernel doesn't run my sound system.  But the generic kernel seems quite stable and everything works fine.  :)

---

### Post by perlluver on 2007-10-11
Currently running Release Candidate, installed when it was tribe 5, only trouble I had was installing the Nvidia Drivers, other than that everything is good.

---

### Post by wasim2050 on 2007-10-12
So anyone else installed Ubuntu 7.10 rc if yes then please share ur experience about it.

---

### Post by forestpixie on 2007-10-12
I've been running gutsy since tribe 5, did the upgrade to beta and the many updates in between and since :) - and the only problem I had was on saturday when there was a problem with the kernel - as did many others from the threads I saw - repaired shortly afterwards

---

### Post by scawa on 2007-10-12
I just installed a dual boot system with Vista and 7.10 about an hour ago... My first Kbuntu install.   Love it, but trying to get the drivers for my hardware.   Having a hard time figuring out how to do that.  And trying to set up multiple monitors....

I'm using a GeForce 8500 GT video card.   Man, but the standard grapics are much nicer than that old Vista (I have to have it for work).

---

### Post by skompier on 2007-10-12
I installed 7.04 on a 10GB partition and have loved coming back to Linux. Since I still have XP for dual boot, I didn't mind playing around. I tried to upgrade to 7.10 using update -d and had some problems with missing packages and stuff, so I reinstalled 7.04.

Well..never being content and I decided I was going to repartition for 7.10 final anyway so I went ahead and d/l the RC and burned it last night. I deleted my partitions from my slave drive and installed 7.10RC from CD.

Everything has worked perfect. In fact, I have a 1440x900 LCD and 7.04 wouldn't run at that res. I tried ALL of the forum suggestions..nada..zip..zilch. 1280x1024 was ok and usable, so no biggy. Gutsy ran out of the at 1440x900...YIPPEE. I had to do nothing.

So in summation, installing RC from the CD has been wonderful.

---

### Post by amtnbiker16 on 2007-10-12
im running it on virtual pc right now and im planning to dual boot it when the official version comes out
7.04 has been working fine, but 7.1 seems to be organized better, so i figured why not try it

another thing is that 7.04 doesnt work on a lot of dells, which a friend of mine was lucky enough to discover (something to do with the hard drive), 7.1 booted right up

i guess i just wanted to throw in my two cents worth, not that it really does anyone any good, but i am looking forward to trying out compiz-fusion too, the videos on youtube were certainly impressive

well, good luck getting your monitor to work right

---

### Post by inportb on 2007-10-13
It's 7.10, not 7.1 :)

I've had a lot of fun with the RC. So far, it's done most things correctly and it's pretty stable. The first thing I thought when I booted up in Kubuntu Gutsy was: ooOOoo... smooooooth... :KS

I have a Toshiba A215-S4697, and this laptop has loads of issues running Linux. I couldn't even get a graphical interface with the Feisty LiveCD and ended up installing Feisty using the alternative disc and then tweaking the xorg.conf. Gutsy, surprisingly, booted right up using the VESA driver instead of the Radeon driver that didn't work. I then installed fglrx using the restricted driver manager. Smooth.

The sound subsystem was as flawed as in Feisty, but I just did what I did before and built myself the latest mercurial ALSA system and it worked perfectly. Now, there's something up with kmilo. That's the OSD that shows you the volume when you tweak the audio volume dial. It was fine (but ugly) in Feisty, but it does not respect my master channel setting in Gutsy, choosing instead to hook onto the first channel. The OSD is a lot prettier, though. I could disable kmilo and still tweak the volume the same way, but I lose the OSD, obviously.

Dolphin is the new default file manager tool for Kubuntu. It's pretty slick, but it does not respect system font and icon settings, but Konqueror still does.

Last thing... I just found out that I could not reboot my laptop normally. This was also the case in Feisty. The system goes down, but hangs on the way up. A cold reboot works though (shutting down fully first).

All-in-all, I think Kubuntu Gutsy is a very slick upgrade. Go for it if you feel you're ready!

---

### Post by EclipseAgent on 2007-10-13
I have installed Ubuntu and Kubuntu 7.10 RC's.. Pretty impressed with Ubuntu, although I am not a huge fan of Gnome.. Until their damn show desktop icon, and taskbar get fully transparent.. and they get comparible applications to Amarok / Akregator / Kmail / etc etc.. then.. well i'll just continue using KDE. 

I was very dissapointed with Kubuntu, it doesn't have all the same package versions as Ubuntu (mainly the 3945 driver for Intel wireless 3945 cards.. which was recently patched, and fixed with what I consider a critical issue).. Unfortunatly Kubuntu RC didn't include and Ubuntu did. 

Also dissapointed Kubuntu didn't have FF, and how it handled my monitors.. (very very poorly).

---

### Post by inportb on 2007-10-13
Hm... Kubuntu and Ubuntu pull their packages from the same repositories, so you should be able to get everything on Kubuntu that you can get on Ubuntu.

For the same reason, Firefox installation on Kubuntu is very straightforward (apt-get install firefox). What was wrong with the way monitors were handled?



Hm, I found why my usplash wasn't working correctly... it thought that my monitor was 1280x1024 when it's really 1280x800! So I fixed that in /etc/usplash.conf and ran mkinitramfs to commit it to the boot image... and it started working perfectly.

---

### Post by drphilngood on 2007-10-13
I really like it; it's faster, looks better and most of the bugs have been ironed out.:KS

---

### Post by techno-mole on 2007-10-13
im having trouble with mine, everything works fine apart from fusion (had it working perfectly on fiesty) i cant get any title bars on anything apart from firefox when its running with gutsy.
still trying to get it sorted.
apart from that it seems alot better in most respects than fiesty.
cheers

---

### Post by Pumalite on 2007-10-13
Check this:

[http://forlong.blogage.de/](http://forlong.blogage.de/)

---

### Post by iheartubuntu on 2007-10-13
I upgraded this morning and notice several 3rd party programs dont work anymore (gsopcast, easybuntu, automatix). Is there any way to uninstall the upgrade or somehow get back to feisty?

---

### Post by novaheat on 2007-10-13
I upgraded to the 7.10 RC last night with no real problems. All the hardware I was using worked fine after the upgrade. Some things seem a bit more sluggish -- that might be because I've got an older machine and Compiz Fusion is installed by default (though the settings are definitely more conservative than they could be -- good design choice there).

The only real "breakage" that I noticed was that the installation wiped out my /etc/fstab, which meant that the two NTFS-formatted Windows drives that I have in this computer became inaccessible. For me, this wasn't a huge problem to fix. For an "out-of-the-box" user who expects everything to work correctly, this would be alarming. 

To be fair, there were some fairly useful instructions that popped up when trying to get the drives back to working, but even more useful would've been the option to preserve the old fstab.

All in all, though, Gutsy is -- so far -- a modest improvement over Feisty. I haven't noticed anything mind-blowing. Then again, I haven't really been looking too hard. :) On the other hand, I see absolutely no reason to *not * upgrade, either. Aside from the fstab issue, everything else has worked just fine, and new-ish users who don't want to go through the hassle of installing/configuring Compiz will get it installed by default... and Compiz *is* pretty damned cool!

---

### Post by tgoff on 2007-10-13
I upgraded to the RC this morning.  It went pretty smoothly, except that the instructions were a little misleading.  once I added Gutsy to the metareleases file however, the process was awesome.  I have never tried a straight upgrade of a distro before, usually reinstalling from scratch, and I have to say that this was very nice compared to that.

I have noticed much difference yet.  It is nice how some comfiguration is consolidated.  

My one real issue is that upgrading broke compiz for me (ironic since 7.10 touts how it has compiz enabled by default).  I ended up with windows with no window decorations, and had to revert to metacity to get them back.  when compiz was running and I tried to run the window settings utility it said something like there was no registered config utility for compiz.   I noticed that the update applet in my task bar was saying that I had updates available, and they turned out to be compiz updates... I installed them and it still did not work.  Finally, I went into synaptic and installed mostly everything that had compiz in the name.  now it works.  The Ubuntu Devs should make sure that the upgrade process installs all of the packages that are required for compiz(or any other component) if it is going to be the default.  I am sure that had I done a clean install this issue would not have happened, but for users who have ubuntu as the primary OS on their primary system (like me), and less savvy users who dont know what to tinker with when things dont work, this is a huge nuisance.

---

### Post by manf0001 on 2007-10-17
I tried it last night.  and everything seemed to be working fine until I did the updates.

there were about 96 updates availiable and I did them all,  only  too find out afterwards that my sound stoped working and I am unable to move windows around.  When I try to grab them the menu bar for it won't highlight, unless I click on a menu and even then I can't move the window around.   Also the close, minimize and maximize buttons at the top of every window is now longer there.

Looks like I'll have to reinstall it and forget about the updates


Edit:  After reinstalling it looks like the reason for not being able to move the windows or lack of the buttons is from the Nvidia Drivers that I installed.  It was the NVIDIA-Linux-x86-96.43.01  Driver that I installed.

---

### Post by harambe on 2007-10-17
Bad news from my upgrade to 7.10

Two issues so far found, 

1 - I no longer have Internet access
     It recognises my BT Wireless connection and the network monitor says it is connected, but I can't access any WEB pages
     It repeatedly asks me for my WEP key, and I know I am entering it correctly

2 - My screen resolution is limited to 800
     I used to have up to 1024 and want it back.

This is one of the really frustrating things about Linux installs  and upgrades - they invariably need fixing.

---

### Post by lotv on 2007-10-17
problem with the upgrade from the very beginning, the process stopped from some error, pc was still bootable with an ubuntu 7.07 hybrid :p

i tried to upgrade again, and almoste everything seems to be working fine, apart from my sound blaster live soundcard which i haven't managed to make work, and those eye candies have big issues (the window title bar disappears instead of becoming transparent). i am in the middle of exams, i'll try a fresh install when i have time because i've been upgrading since dapper!

---

### Post by harambe on 2007-10-17
Well, OK - Got mine working now.

The Wireless Internet issue - for some reason I had to use the manual network configuration setup - just entering the WEP code via the window which pops up when you try the access the internet for some reason did not work.


As to the screen issue, I found my monitor listed using the System/Administration/Screens and Graphics option, and I selected it here. But, for some reason it did not allow me to set the resolution correctly - for this I had to go to System/Preferences/Screen Resolution.


Well - all OK now they - so far.

I must say it appears to be a much more bright/clean image than before,

---

### Post by cuby on 2007-10-17
Hello.
I upgraded to 7.10 while in beta.
I had some problems with the video drivers, but they were fixed in a later update :).
I have an asus p5b-v (with the dam jmicron thing), and I was unable to use PATA correctly with 7.04. Now IS FIXED (I think)!
Vmware and Virtualbox were broken in the upgrade... I will reinstall them later, after the official release (to many updates meanwhile). 
I am happy with 7.10.

---

### Post by maxseamus on 2007-10-17
I upgraded two days ago and so far so good. Everything seems to be working. I'm running it on a Dell D620 laptop and it's flying. I tried using Compiz, but it still needs some work i think. I kept getting black screens for my windows. I may just need to make some tweaks.

Another thing I noticed is that virtual box doesn't work quite the same in Seamless mode. When I went into seamless mode with XP I used to have my regular panel and the XP start menu right above it. Now the XP start menu sits right on top of my bottom panel and its a pain to switch between the two. 

Other than that I haven't run into any other issues. Has anyone else noticed the isswue with virtual box?

---

### Post by gjhicks on 2007-10-19
Hi,

Have installed Xubuntu 7.10rc to my hard disk. Installation went fine.  Seems to work as expected with one exeception.

If I try and open a terminal window, the xwindow closes and the login screen appears.

After logging in, if I try to open a terminal window, the xwindow closes and the login screen appears, 

After .......

Any ideas on how to fix this?

Geoff.

---

### Post by ldesilva on 2007-10-19
I was running 7.10 since its beta and did a fresh re-install this morning with the new code. I have not experience any dramas but the downloading package using synaptics today is very very slow.

---

### Post by wasim2050 on 2007-10-19
> **wasim2050 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/151817](https://bugs.launchpad.net/ubuntu/+bug/151817) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I just download and installed Ubuntu 7.10 Release Candidate to try out if everything is working fine or not before the grand release of Ubuntu 7.10 as it says on the website "We consider this release candidate to be complete, stable, and suitable for testing by any user."

[HTML]http://www.ubuntu.com/news/ubuntu-7.10rc[/HTML]

So after installing the 7.10 rc the first thing I noticed was that during the loading of the system when we see the ubuntu logo at that time my monitor does not support the resolution and goes out of sync and after sometimes when the system comes to the login screen my monitor become ok and thats seems strange to me because this does not happens in ubuntu 7.10 beta. So I reboot it a couple of time to make sure and everytime my monitor goes blank until the system comes to the login screen.

I have reported it as a bug not sure if anyone has faced the same problem or not.

[HTML]https://bugs.launchpad.net/ubuntu/+bug/151817[/HTML]

Even in the final release the problem remains :mad: I can't understand this because this problem was not in UBuntu Gutsy beta and this problem starts from Ubuntu Gutsy RC and it is still there for me in the final release as well.

---

