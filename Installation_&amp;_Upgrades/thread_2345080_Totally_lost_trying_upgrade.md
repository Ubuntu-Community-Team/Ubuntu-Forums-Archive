---
title: "Totally lost trying upgrade"
date: 2016-11-30
forum: Installation &amp; Upgrades
---

### Post by russkyca on 2016-11-30
I am lost.   I went to IRC but their help was insufficient.  I was just given a link or links.   Maybe that's what will happen here, I'm not sure.

I need to be hand held, I guess.   I have never had this much trouble upgrading a system until now.   I waited too long.   I usually just give up and re-install but I don't want to do that.   Not yet.

Does anyone want to help?

I upgraded to 15.10 a while ago so I guess I need to upgrade to 16.04 and then 16.10 (after that upgrade is successful).

I am trying to find how-tos and instructions but everything is mostly a standard upgrade - not when you have waited too long and it's not supported any more.   

I am not sure about this LTS.   LTS editions were 14.04 and 16.04.   

Well, if you have good instructions or want to help, thank you (in advance).   Until then, I'm trying to figure out what to do.

---

### Post by QIII on 2016-11-30
Hello!

Honest opinion?  Re-install.  It is much more likely to succeed than trying to do an old-releases upgrade.  The latter is more likely to become a significant emotional event. Back up all of your important files.  Do you have a separate /home partition?

Sticking with 16.04 (an LTS) might not be such a bad idea.

---

### Post by russkyca on 2016-11-30
I tried the upgrade and finally, it worked without much trouble.   One error message at the end.   I followed this page:

[http://www.tecmint.com/upgrade-ubuntu-15-10-to-ubuntu-16-04/](http://www.tecmint.com/upgrade-ubuntu-15-10-to-ubuntu-16-04/)

The only other command I ran in addition to those steps is I decided to run $ sudo update-grub (just in case - I don't know if I needed to but I had no grub issues after the upgrade).

It might be after upgrades or installs of other distros - in which I need to run that command - not sure.

Anyway, the error message was:
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

I googled the message and I think I can just remove it (rm)?  I moved it to my /home directory just in case - but I believe I can just delete it (i.e. get rid of it).   The 'N' means notification and it's not needed?

So, should I just leave things now?   I was going to upgrade to 16.10 eventually but things seemed to go smoothly compared to be being really confused previously.

The other thing that I can see that is not configured properly is my graphics - as I remember seeing this before and that is the bottom tabs have 'highlighted' black text.   I think my graphics drivers need to be updated/upgraded or something.   I have a nvidia GTX 750 card and was planning on using gtx or binary drivers - so what's the best method?   Installing some ppa drivers in the repo or?   Geez, I always forget what to do and need to google/look it up. ;)

Any advice?

Edit:  I am not sure if it is supposed to look like that now.   It's highlighted but not blurry or overlapping (text doesn't overlap) which is maybe what I recall, I dunno.   But, it just looks odd.   It's hard for me to consider that it is supposed to look like that and not sure how to describe it.   'Hope someone knows what I'm talking about. :-)

---

### Post by oldfred on 2016-11-30
Since not a very new nVidia card, you can just use the most current version in Ubuntu's repository.
Only if you need the very newest driver, might you add the ppa first.

You can go to System Settings, Software & Updates icon, and then additional drivers tab.

You can also do the install from command line.
And if you install one nVidia driver, you must purge completely before installing another. It does not automatically purge with new version install. And if both installed you almost always have conflicts.

---

### Post by russkyca on 2016-11-30
NVIDIA Corporation:  GM107 (GeForce GTX 750)
 This device is using the recommended driver
 (*) Using NVIDIA binary driver &#8211; version 367.57 from nvidia-367 (proprietary, tested)

That means I'm using the latest, most current version in Ubuntu's repository, right?   

I just think the bottom screen - highlighted black font of the program (tabs) with the current one in use - for e.g. Firefox - is highlighted in grey with white font - not readable at all - looks strange.

---

### Post by oldfred on 2016-11-30
I do not understand "for Firefox"?
Never seen that related to nVidia driver.

---

### Post by russkyca on 2016-11-30
> **oldfred said:**
> I do not understand "for Firefox"?
Never seen that related to nVidia driver.I don't know what to  tell you.   To be honest, I don't like Ubuntu's graphical interface any  more.   It is not intuitive.   I guess I shouldn't say much more but I  don't like it, bottom line.

There's two horizontal grey bars - one at the top has Applications /  Places' on the left and the language/date/ LAN status/ sound/shut down  etc. options' on the far right.   On the bottom grey bar, whatever  programs/applications are open are displayed.  Are these task bars?

I can't configure anything with it.   But, the way it is displayed is  awful - whatever program I'm using, it is 'highlighted' in grey so I  can't read the text (the program name!!! or title - for e.g. if it's  Firefox, it is [UbuntuGnome] totally lost...etc.)   

I was going to ask on IRC but the IRC XChat program is unavailable and the Gnome version doesn't work for me.   

Very frustrated but at least the upgrade is okay but I have another  error now after trying apt-get update.   It doesn't show what the error  is or mention anything about it anywhere.   :sad:

Fetched 4,074 kB in 1min 7s (60.4 kB/s)                                        
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done

Tried a 2nd time, no errors.   :-{

---

### Post by oldfred on 2016-11-30
Yes, then those are the top & bottom task bars.
I install gnome-panel or fallback which uses those. I believe several other gui also are similar where Unity is the task bar on left. It just depends on which "flavor" of Ubuntu you have installed.
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
 [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

How are you updating. Maybe better to use command line to see all the errors.
sudo apt update
sudo apt upgrade

---

