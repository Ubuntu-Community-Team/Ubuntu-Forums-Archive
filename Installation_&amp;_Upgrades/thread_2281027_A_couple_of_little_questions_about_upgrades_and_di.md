---
title: "A couple of little questions about upgrades and distros"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by roy27 on 2015-06-03
1) Does upgrading Kubuntu 14.04 to 14.10 and then to 15.04 upgrade all the distros on my Linux (I am asking because it's called a distro upgrade and it specifically said "upgrade for Kubuntu" not "upgrade for Ubuntu").

2) When my system boots up I choose which OS to boot (Ubuntu) then I get some text on a black screen, then Xubuntu splash loads, then I get a black screen with some text popping up again (it disappears before I can read it), then some more text pops up ("loading version 219" or something) and then I get the KDE login screen. I am not sure if my system is working properly, is this supposed to happen? It didn't happen before I installed Kubuntu and then the two upgrades (yesterday). 

3) 15.04 seems to lack 25% of the features that 14.04 had (in terms of customizing the look and feel of things), like custom splashes, windows, etc... Why? Oh and applications crash constantly, and "half" the icons don't load. (While I was typing my Plasma desktop crashed :KS).Are those things coming back in updates _soon_? Otherwise, is there a way to revert back to the ***Trusty* Tahr**? 

4) Is updating my Windows 8.1 to Windows 10 on my dual boot machine affect my Linux machine? Should I do it? I am running a partitioned hard drive, with a different OS on each partition.

---

### Post by grahammechanical on 2015-06-03
I have several installs of Ubuntu and the family of Ubuntu distributions. They are all on their own partitions. I never experience what you describe in item 2.

As far as I can tell you have installed Ubuntu and then installed the Xubuntu and Kubuntu desktops. You have not really installed either Xubuntu or Kubuntu. And as you are finding out installing these alternative desktops does get messy. There are conflicts of interests. I would not recommend upgrading. And there are a couple of reasons for this.

1) 14.04 is a Long Term Support (5 years) release. Once you move off of it you would have to keep upgrading until you get to 16.04 and each of the releases that you will be upgrading to only has 9 months support. Keep on 14.04 and you can upgrade directly to 16.04 next year.

2) Upgrades to new releases work best if the OS is as close to a default install as possible. The more we modify the OS the more likely of an upgrading ending with some form of breakage. The risk of breakage increases with each upgrade.

From this other post of yours I see that you have removed Unity.

[http://ubuntuforums.org/showthread.php?t=2281030](http://ubuntuforums.org/showthread.php?t=2281030)

So, this install is far from default. When we load into one install of the Ubuntu family and upgrade to the next release it is only that install that is upgraded. Other installs of the Ubuntu family on other partitions are not affected. We would have to load each of those installations and run the upgrade.

Upgrading Windows 8 to Windows 10 should not affect the other operating systems on the hard disk but it may install the Windows boot loader and you will loose the ability to load Ubuntu. Someone has to be first and until someone tries this who can say what would actually happen. Wait until others have tried this and learn from their experience.

Regards.

---

### Post by roy27 on 2015-06-04
Too late I dun broke it, I already upgraded when I typed that message. At first nothing was crashing except an app from time to time, but then the whole desktop went (and five or more other apps at the same time xD), and it gives me a black screen on boot up 75% of the times I try to boot it (it first loads OS, shows me the Xubuntu splash, then goes black). *"Trusty Tahr* *is called Trusty for a reason." *That's my quote of the year.
Edit: My computer booted, and I'm just not going to turn it off at this point, because it doesn't know how to boot back up.

---

