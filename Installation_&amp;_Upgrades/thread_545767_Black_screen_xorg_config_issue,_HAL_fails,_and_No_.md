---
title: "Black screen xorg config issue, HAL fails, and No internet connection"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by UnrealMiniMe on 2007-09-08
Hiya guys,
In case you guys need more information, here is a metric ton of backstory and an explanation of what I've already tried - if you don't think you'll need it, skip right to the bottom!:
___________________________________________________________________
Since this post is exceedingly long anyway, here's a fun little story about my first Ubuntu/Linux experience, which I now consider "easy" compared to my current predicament:
Several months ago, I installed Ubuntu on my computer, and I only had one major issue:  I had no wired Internet connection, and my wireless card was a Buffalo card using a Broadcom chip.  In order to get my wireless working, I had to use my roommate's Windows machine to learn about ndiswrapper and bcm43xx-fwcutter.  Since I had no access to any Ubuntu repositories, I had to find compatible .deb's on Internet sites, copy them to my roommate's USB thumb drive, and copy them over to my Ubuntu box.  It didn't seem like bcm-43xx-fwcutter was working, so I spent several days downloading different versions of drivers to try to get ndiswrapper to work, only to find out a few days in that bcm43xx-fwcutter DID work...long story short, I eventually got my Internet connection up and running, and then, I was finally able to do things "by the book."

Now, I'm installing Ubuntu 7.04 (AMD64 version, since I have 4 gigs of RAM) onto my new computer at another house.  Potentially relevant specs are:
Acer AL2223W monitor
BFG 8800 GTS OC2
Intel Core 2 Quad Q6600
MSI PC60G wireless card (rt61 chip I think...)
I can provide the rest of the specs if need be, but these are the ones that are the most likely to relate to the issues.

Now, let me explain what makes my current problem so challenging:
Once again, I have no wired connection while in Ubuntu.  I bought the MSI card because I read that the drivers were GPL'ed and the card totally worked out of the box (I didn't want a repeat of last time...).  However, it does NOT work out of the box - what this means is, ***I CANNOT USE ANY SOLUTION THAT REQUIRES INTERNET ACCESS TO UBUNTU REPOSITORIES.***  It sucks, but, unless the wireless can be fixed first, that's just the way it is :(

So anyway, here's my current scenario, in depth:
- When I first tried installing Ubuntu, I got a completely black screen, regardless of whether I tried installing normally or using safe video mode (I think that's what it's called...I imagine you guys are following, though).  I tried another CD, and I had the same issue - eventually, I realized it was a video problem, so hitting F4 and changing the VGA mode fixed it.  After that, I'm able to install Ubuntu just fine.
- However, I cannot boot Ubuntu normally (I get a black screen again) - I have to use recovery mode.  Now, here's the really screwy thing:  Without even changing xorg.conf, I can immediately get a GUI by typing "sudo /etc/init.d/gdm start".  I can't get the GUI by loading Ubuntu normally, but it'll work if I start GNOME from the recovery console!  Sure, my resolution will be screwy, but at least I can get a GUI that way. :-/
- Once in Gnome, I get slammed with the whole "Failed to initialize HAL" error...this is a vanilla Feisty installation, so the whole "roll back to version 0.5.8.1-4ubuntu12" solution does not apply - I'm already using that version.  I've done some research on this, and a common suggestion I've seen is to run "/etc/init.d/hal restart" and "/etc/init.d/dbus restart" - unfortunately, neither seemed to help, and both spewed out a few messages about failing this and that :(  It was the recovery console where I tried those commands, by the way.  Now, this error may magically go away once I figure out how to get a GUI without first booting from the recovery console - then again, maybe it won't.
- No matter what I change in xorg.conf, I can't seem to boot normally into Ubuntu - I always have to use the recovery console and "/etc/init.d/gdm start" (and sometimes, the HAL error will keep my desktop from coming up after logging in - then, I need to return to the console with alt-f1).  I've tried adding the "1680x1050" resolution in the Screen section after "Modes" for each and every depth, I've tried putting that as the only resolution, and I've tried the modelines at [http://www.netsteps.ch/tutorials/acer_al2223w_linux](http://www.netsteps.ch/tutorials/acer_al2223w_linux) and another slightly different one that I'm now having trouble finding.  None have allowed me to avoid an eternal black screen after booting Ubuntu normally.
- Without the nVidia drivers, I can't get 1680x1050 resolution at all, but since HAL works with the LiveCD, I can copy the nVidia 100.14.11 drivers from my USB drive to my hard drive using the LiveCD.  After installing them using this guide, [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161), I can get 1680x1050 resolution (by setting it with nvidia-settings).  However, EVEN AFTER INSTALLING THE NVIDIA DRIVERS, nothing I put in xorg.conf has allowed me to boot Ubuntu normally!
___________________________________________________________________

So, in short, here are my issues (on a new install of Feisty AMD64, and I have NO internet access while in Ubuntu):
1.)   I have the nVidia 100.14.11 drivers, and the display runs at a beautiful 1680x1050 if I first boot into recovery mode and run "/etc/init.d/gdm start" - but I get the HAL error.  If I try to boot normally, I get an eternal black screen, and no modelines or HorizSync/VertRefresh settings in xorg.conf have helped me thus far.  Does anyone know how to fix this?
2.)  Assuming the HAL issue won't fix itself once I start booting normally, does anyone know how to fix it without an active Internet connection?  (I'm assuming I won't be able to get my wireless working until HAL is up and running anyway)  As a reminder, I'm already running version 0.5.8.1-4ubuntu12.
3.)  This is kind of a side issue, but I'm not really sure where to look for setting up my MSI PC60G card.  However, I definitely want to use network-manager (so I can automatically connect to my wireless, see my signal strength, etc.), and I'd rather not deal with ndiswrapper, because trying to get that to work reminds me of the time I visited the eighth circle of hell.  Odds are, I won't be able to use this card until I get the HAL issue fixed first, but...once I do, it'll be nice to know the best way to get this card running (such as with the native drivers, or something).

Um...help?
Thanks :popcorn:

---

### Post by K.Mandla on 2007-09-08
Wow. This is a tough one. I'm going to try a couple of guesstimations here, but I think, any way you look at it, you'll need some research to find out how these things will work.

First, I believe your network card should work, with or without HAL. I never install HAL, and the lack thereof never interferes with my hardware. I think the trick will be getting the right module and installing it. I looked over the MSI pages for a second, but I didn't see anything that suggested a Linux driver. If you can find one, get it installed and get net access first.

Second, check and see if there is a patch or anything else required to use those 100.14.11 drivers. [NvNews]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") is the place to look for that information, and really, you should ask your same question again there (be SURE you follow their instructions for posting questions; they'll snub you if you don't give them the proper reports from your card!). It could be something as simple as a one-line option somewhere in xorg.conf; if I don't tell the 96xx driver to use the DFP option, I get a dead screen too.

Worry about HAL last. HAL is cute and works nice, but you need a core level of operation before you can worry about things like automounting. If it continues to crash, let it. Get the important stuff -- network and video -- working first.

Sorry I can't be of more help with this stuff, but I didn't want your post to sit unanswered for much longer. I'm sorry to say it, but you'll need to spend a few hours online and probably ferry a few more drivers back to your rig before it will smile at you again. :D

---

