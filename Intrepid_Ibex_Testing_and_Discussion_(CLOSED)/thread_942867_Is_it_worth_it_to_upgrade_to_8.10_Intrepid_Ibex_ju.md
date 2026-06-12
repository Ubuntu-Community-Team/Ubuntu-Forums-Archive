---
title: "Is it worth it to upgrade to 8.10 Intrepid Ibex just now?"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by milasch on 2008-10-09
Basically I'm having issues with VLC, and found out they refuse to give support to the version I have installed 0.8.6e (found on the main repositories). Looks like 8.10 ships with VLC 0.9.4 (latest).

I was trying to find an updated package for Hardy as I don't want to install from the source, and I can't seem to be successful.

So I'm wondering if it is worth it to upgrade my 8.04.1 Hardy Heron to the latest 8.10 beta... Anyone?

Also, since I migrated from openSuse to ubuntu on the 8.04 age, I was wondering whether I should waste my time upgrading it to find out the system is somehow broken, or I should go straight to a fresh installation.

Then, if I install 8.10 beta, and in 21 days they release 8.10, will I be able to upgrade again? Are the changes to screw my system up even bigger if I upgrade to beta then to the release version?

Thanks!

---

### Post by Yellow Pasque on 2008-10-09
[http://forum.videohelp.com/topic357107.html](http://forum.videohelp.com/topic357107.html)

---

### Post by milasch on 2008-10-09
Thanks, although this is not really the real point of the question. It's just that it feels like Canonical is allocating all its resources on the release of 8.10 now, and some packages like pidgin, vlc, among others, get outdated on 8.04.

---

### Post by mkvnmtr on 2008-10-09
You should only use 8.10 beta if you wish to help with the problems of putting together a new version. Then only if you don't depend on that OS. It is beta. Remember if you didn't buy support from Canonical the don't owe us support. As users of Ubuntu we support ourselves. If you have a problem bring it up in a thread of these support forums. There are some very good people that can help you get almost anything working.

---

### Post by caleb12 on 2008-10-09
I find it to be very stable... I just switched to Ubuntu from another linux distro about a month ago and went into Hardy for a short time, and then did the upgrade to Intrepid. 

There are definitely somethings to be aware of... like the 2.6.27 kernel, the current issues with the e1000 (supposedly patched)... Intrepid also uses the latest Xorg 7.4 and Xserver 1.5 - which means if you are using an ATI card with fglrx... that will stop working. Although, I've found the Open Source Radeon drivers to be just as good - there is a trade off; a decrease in performance, however an increase in stability. It hasn't affected my desktop experience, I still run compiz and all the goodies... 

IMHO, even though it's in beta... it's stable and I get a slew of updates every day so there is a lot of work going on behind the scenes and I like seeing that... 

But, if you are worried about upgrading you could always set up apt to do some pinning and then just force install the packages you want. 

Here's some info: 

[http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html](http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html)

---

### Post by milasch on 2008-10-09
> **caleb12 said:**
> I find it to be very stable... I just switched to Ubuntu from another linux distro about a month ago and went into Hardy for a short time, and then did the upgrade to Intrepid. 

There are definitely somethings to be aware of... like the 2.6.27 kernel, the current issues with the e1000 (supposedly patched)... Intrepid also uses the latest Xorg 7.4 and Xserver 1.5 - which means if you are using an ATI card with fglrx... that will stop working. Although, I've found the Open Source Radeon drivers to be just as good - there is a trade off; a decrease in performance, however an increase in stability. It hasn't affected my desktop experience, I still run compiz and all the goodies... 

IMHO, even though it's in beta... it's stable and I get a slew of updates every day so there is a lot of work going on behind the scenes and I like seeing that... 

But, if you are worried about upgrading you could always set up apt to do some pinning and then just force install the packages you want. 

Here's some info: 

[http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html](http://aldeby.org/blog/index.php/mixing-hardy-stable-and-intrepid-testing-repositories.html)

Thanks for your reply... So, when the release version is out, are you going to install it from again, or you're gonna upgrade it?

---

### Post by caleb12 on 2008-10-09
Im not completely familiar with how Ubuntu works, so if someone else chimes in that would be great. 

But, from my experience with other distros - as you go along the update process, i.e. continue installing upgrades as they are released - your distro will stay current. A freeze will be placed on certain packages while the official release is made, which once those packages are installed - your on the final release. No need to re-install... also hitting alt+F2, and typing update-manager -d will open the update manager - then click on "There's a new version available" button... will also do a system wide upgrade from Hardy to Intrepid. 

There's always a package or two that gets lost in the upgrade... so be prepared for the possibility that some issues may pop up but google is always a solid resource for figuring problems out. Personally, I didnt have one... (knock on wood)

---

### Post by carusoswi on 2008-10-09
If you are dual booting Ubuntu with any other OS on which you can fall back if you run into problems, then, I would not hesitate to go ahead an upgrade to Intrepid.  That's what I did (and I used the same approach from 7.10 to 8.04).

I highly doubt if an upgrade would fatally break your machine, but many of us have experienced some problems.  For me, the move to 8.10 caused a loss of sound while on the web.  Earlier this week, an 80 file upgrade caused me to lose internet connectivity altogether.

I could dual boot to XP and continue searching for solutions here and elsewhere, and continue my drunken indulgence in using the 'net for my work and pleasure.  I also have a blank 160 GB HD that I took from another old system, and I can swap that in place of my master HD to run whatever system of choice I choose to load onto that spare drive.  

I watched the presidential debacle . . . oops, debate live on the 'net using LinuxMint which is currently installed on that spare drive - I hate surfing from XP.

My bottom line advice to you would be to go ahead as long as you have some other route to the 'net available to you in case you lose that functionality during the upgrade process.

Ubuntu's (and Linux's) strength is its web integration.  But, if a system problem causes you to lose connectivity, you'll go nuts without some alternate route to the 'net.

Good luck.  Let us know what you decide and how it works out for you.

The earlier answer concerning upgrades was exactly correct.  If you load the beta now, upgrades will keep you up to speed so that you will not have to re-install when the LTS version is released.

Caruso

---

### Post by milasch on 2008-10-09
> **caleb12 said:**
> Im not completely familiar with how Ubuntu works, so if someone else chimes in that would be great. 

But, from my experience with other distros - as you go along the update process, i.e. continue installing upgrades as they are released - your distro will stay current. A freeze will be placed on certain packages while the official release is made, which once those packages are installed - your on the final release. No need to re-install... also hitting alt+F2, and typing update-manager -d will open the update manager - then click on "There's a new version available" button... will also do a system wide upgrade from Hardy to Intrepid. 

There's always a package or two that gets lost in the upgrade... so be prepared for the possibility that some issues may pop up but google is always a solid resource for figuring problems out. Personally, I didnt have one... (knock on wood)

I guess there is some sort of differentiation between the versions, since each Ubuntu release has its own repositories... I can think of 8.04 having kernel 2.25.19 as its latest distro and 8.10 having a later version available... I mean... Even Feisty/Edge users have different repositories, Canonical releasing 8.04 Hardy, didn't just give a set of new packages to users of previous distros so they would have their systems updated to a newer version.

I believe there is a lot more involved than just upgrading packages...

Well, I'll just try upgrading it myself tomorrow and post the results! :P If I find something really unstable I give the beta version a fresh installation. If I still find the 8.10 beta is unstable, I go back to 8.04 and wait for 8.10 to be finally released.

Hopefully when they do, I'll be able to suspend to ram on my desktop computer... I'd love to play with Wake On Lan over the internet.

Thanks!!!

---

### Post by flowingfire on 2008-10-09
Testimonial: It seems to work better than 8.04 for me. :)  No crashes, either, with exception to mistakes I made installing Compiz and Emerald.

---

### Post by bodhi.zazen on 2008-10-09
> **mkvnmtr said:**
> You should only use 8.10 beta if you wish to help with the problems of putting together a new version. Then only if you don't depend on that OS. It is beta. Remember if you didn't buy support from Canonical the don't owe us support. As users of Ubuntu we support ourselves. If you have a problem bring it up in a thread of these support forums. There are some very good people that can help you get almost anything working.

+1 

The beta is for Testing and is not yet "ready" for prime time. 8.10 is due out soon and I would advise you update at that time.

Take care, just because it works for some does not mean it will work for you and there are some that have had problems with upgrading.

---

### Post by milasch on 2008-10-09
> **bodhi.zazen said:**
> +1 

The beta is for Testing and is not yet "ready" for prime time. 8.10 is due out soon and I would advise you update at that time.

Take care, just because it works for some does not mean it will work for you and there are some that have had problems with upgrading.

I'll give it a shot tomorrow... I figured the only thing that I have to save is my .conkyrc file and a bunch of scripts I wrote. Everything else is on my NTFS partition that I share with Vista.

If it does not come out ok, I just install 8.04 again until 8.10 gets released.

Thanks for sharing your opinion folks.

EDIT: Even better idea, I'll boot a 8.10 live, install partimage, create partition images for my root and home partitions, so it's easy to roll back.

---

### Post by ivaarsen on 2008-10-10
I've been running 8.10b on a spare machine pretty much since it was released.  It's working well for the most part, but not quite as well as 8.04 - yet.

I've had a couple problems with the daily updates.  They've started coming up as 'partial distribution upgrades' and stop functioning during the cleanup phase.  After waiting for a few hours I just restart the machine.  First problem I had was with compiz.real - I had to turn off desktop effects. Then just this morning after another update (and similar stoppage on the update) I lost my keyboard and mouse input.  I'm still new to linux, and I had no idea how to fix that.  Based on that fact and that this is a spare machine I just decided to reload and try these updates from scratch.

I'll repeat what others have said:  if it's a spare machine or a multi-boot machine, go ahead and play with it, but you can't depend on it like you can previous releases - again, yet.  ;)

---

### Post by Yellow Pasque on 2008-10-10
> I've had a couple problems with the daily updates. They've started coming up as 'partial distribution upgrades' and stop functioning during the cleanup phase.

I've been playing with Intrepid on my spare disk and this is annoying. An update for the update-manager was released today, so maybe it's fixed. When I try to do the partial update, Intrepid tries to sneak a bunch of useless packages that I've removed back on my system like compiz, CUPS, Pulseaudio, input&video drivers that I don't use, etc. (basically anything that ubuntu-desktop depends on).

**BTW, anyone looking for a recent version of VLC packaged for Hardy should check [https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)**

---

### Post by thegner on 2008-10-10
I have not tested the theory, but you could consider downloading the .deb package from the intrepid repos, and installing it with "dpkg -i package.deb" on your hardy box...

As long as there aren't any/many dependencies, it should work OK. I have done that with other programs.

If there are dependencies, sometimes you can get it working by telling dpkg to ignore them. although I don't remember the exact command line option for that...

Travis

---

### Post by carolinason on 2008-10-10
Well I've been using Ibex for some time and it was great and now there is a horrible bug or feature depending on your point of view. In earlier Ubuntu releases, the Alphas worked very well and there was relatively few issues, but as off late it seems waiting is the best option.

The web site promotes downloading the Beta now, so you would assume system critical bugs where in the main channel. At this point, I'm unable to use my keyboard and mouse, due to what I ssume is a trackpad fix. IMHO keyboards and mice are more important, but I'm not sure of the payload distribution on the latest bug.

Still waiting for the fix to come.

---

### Post by victor9098 on 2008-10-10
Having the same problem too. I get the 'partial upgrade', it hangs at the end of 'cleaning up' and then after hitting the 'restart' icon I have no touchpad or keyboard functions.

Have gone through the install then update of the beta twice now today and has happened twice.

---

### Post by carolinason on 2008-10-10
Going through a second re-install and running into update dependacy issues.

gnome-power and gnome-panel

trying with defualt configuration

---

### Post by carolinason on 2008-10-11
without configuring the desktop I had no issues updating ibex beta. i lost my mouse and keyboard during the update until the update had finished, but i have a kvm and moved to this machine for a bit.

it appears that the earlier issue had to do with the power applet in the gnome panel. this is not a laptop however. and why bluetooth???? i don't have bluetooth.

---

