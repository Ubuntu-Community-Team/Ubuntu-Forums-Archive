---
title: "broadcom wireless (4315), network manager and 9.04, jaunty"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by digitalramble on 2009-04-11
tittle@anathema:~$ lsb_release -rd
Description:    Ubuntu jaunty (development branch)
Release:        9.04
tittle@anathema:~$ apt-cache policy network-manager
network-manager:
 Installed: 0.7.1~rc4.1.cf199a964-0ubuntu1
 Candidate: 0.7.1~rc4.1.cf199a964-0ubuntu1
 Version table:
 *** 0.7.1~rc4.1.cf199a964-0ubuntu1 0
       500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
       100 /var/lib/dpkg/status
tittle@anathema:~$ lspci | grep Broadcom
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xxtittle@anathema:~$ lspci -n | grep '14e4:43'
04:00.0 0280: 14e4:4315 (rev 01)

Here is what happened.  First I got a new laptop ;-)  HP dv4tse.  With relevent specs as above.

1) I installed 9.04 rc1 and the wireless worked out of the box, until it
dropped connection and reconnected.  At that point, it continually asked
for a WEP key and after that no matter how many times I verified it, it
came back and asked for WEP until eventually gave up.  After that, no
matter how i rebooted, etc, it would not recognize any available
wireless.

2) So I installed 8.10.  This never was able to use the wireless at all.
NM acted like there were never any wireless to detect, even tho the
various listings lspci, dmesg, etc all looked normal (and the
proprietary broadcom driver was available & activated).  In short, same
as above after a reboot.  So.

3) In desperation, I reinstalled 9.04...Same deal.  It worked for a
couple of hours, but then dropped & reconnected and went into WEP
PLZKTHX mode.  So I uninstalled NM and put in wicd.  Played with that,
but wasn't perfectly happy with it, and so reinstalled Network manager,
but this time went straight into NM and TURNED OFF THE AUTOCONNECT.
Since then, for several days, it has worked perfectly.  I just need to
take the additional step of telling it to, yes, connect to this wireless
router instead of letting the puppy think on its own.

WILD SPECULATION ON MY PART:  NM is ******* up one or more of its
configuration files, that are correct at the time of installing the
operating system, in some fashion when it is in autoconnect mode.    I
have tarballed my current configuration files in case it goes belly up
again and will compare, if this happens.  (These files can be found under ~/.gconf/system/networking -- i just tarballed that networking dir to  use as a comparison if the wireless suddenly stops working again.)

Hope this perhaps helps someone else...

One thing to note, with the 4315 chipset, the basic 43xx drivers do not support this particular variation, or I would have gone the fwcutter route.  Check which versions are supported before you try that (the lspci -n gives the additional detail, a plain lspci gives some other number.  Broadcom has a particularly non intutitive naming scheme.  However, under Systems->Administration->Hardware Drivers, it listed a "Broadcom STA Driver" which was activated for me on my clean install

Note also that ndiswrapper seems problematic -- I saw about equal numbers reported success and reported failures (probably in part due to getting particular versions mixed up?).

A few other links I picked up along the way that may also potentially be of use:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
undated description of various bcm43xx wireless and which ones the 43/43legacy drivers support (mine wasn't one of them, but it's a good overview of the issues & to find out for sure whether yours would work with fwcutter or not)

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)
this is outdated (the gconf files for jaunty look nothing like described here, nor was i using wpa, but it discusses how NM mangles the config files, and prompted me to try turning off autoconnect.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
a good deal of info about the bcm43xx wireless -- in general if you are going to purchase something new, stay away from broadcom, what a headache -- but anyway, some possibly useful stuff here

[http://ubuntuforums.org/showthread.php?t=571188&highlight=network+manager+config+files](http://ubuntuforums.org/showthread.php?t=571188&highlight=network+manager+config+files)
really old skool, but at one point i stripped out all wireless managers and configured manually (this confirmed that the sucker was working fine)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
general info about the bcm43xx and fwcutter stuff, getting dated (esp for jaunty)

---

### Post by Tommmyboy on 2009-04-13
:KS hi thank you for sharing your information. As there is no one surefire way that seems to consistently work, at least that's the conclusion I've gleaned from all of the Broadcom wireless card difficulties I've read about here, I'm fishing around the threads to find all the info I can that's pertinent to my 43xx card before it's time to install Jaunty release because everytime I install a new version of (k)ubuntu, I always end up so disappointed that wireless doesn't work and I can't get it to work. And what ends up finally after weeks of working in one iteration doesn't work in the another. This is on a Mac PPC G5.

The only reason I've stuck with Linux at all - I can't get wireless with any of the other 8 distros I've tried, the only way I've gotten it finally at all in Ubuntu is through the tremendous bounty of contributed experiences here in these particular forums - is because somehow through the grace of God, my Intel MacBook, with a Broadcom 43xx card, had wireless out of the box on Hardy! It didn't work on the live version but I installed onto my hard drive using the live disk and upon reboot, it was offering me the 15 different networks that are around me! You should have heard the hoots of victory go up in my apartment that late night.

thanks everyone for all your contributions and input.

-Tom

---

### Post by chicobo329 on 2009-04-14
I'm on a 4312 Broadcom and I've had very similar problems to you! One day, Network Manager just stopped working with Broadcom and wouldn't connect wirelessly after I updated the NVIDIA Graphics Driver. I went with 9.04 beta which worked perfectly until just today when there was a Network Manager update which made my wireless not work again! I never thought to think it was the config files that may be to blame. What a pain.

---

