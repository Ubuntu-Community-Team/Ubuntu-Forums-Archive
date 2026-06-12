---
title: "Gutsy Gibbon Crash Installation Guide"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by mike1947 on 2007-11-06
This concerns how to recover from a Gutsy Gibbon Crash installation.   For the record I have a an AMD Athelon dual process computer with 2GB memory a a Tyan Guiness Motherboard.   I also have an Intel 2.4GB Computer with onboard control of ethernet and Graphics.   Both were running Gutsy, both failed in the middle of installation.   The first I ran apt-get autoclean and autoremove first.   A bad move as upgrade records were wiped out and I eventually had to reformat my main drive and replace all.   Fortunately this computer was experimental and no serious data was lost.  My work computer containg student wiki's and my personal web pages was another story.   

There were numerous problems with the the upgrade.  The two main texlive-base-bin and texlive-base installed before other texlive installations spawining a hugh number of processes.   With load numbers returned greater than 25 or more my system eventually killed the offending job by itself. I had to run a sequence of dpkg --configure -a, apt-get -f install, apt-get upgrade, apt-get dist-upgrade repeatedly.   This however did not suffice. :lolflag:  I needed to remove the texlive-base-bin and texlive-base postrm installation files, to force the installation of the latex distribution.   Later when all was installed I reinstalled them.   Also ubuntu-desktop failed to install because acpid a dependent module  could not start the relevant file needed being locked by hald.   Compiz-extra had to be removed to get the latest and greatest of compiz.   I had an additional problem with apache2-torrus. The installation script is problematic because the packages ask for responses in the middle of installation making it necessary to stay and watch the scripts.  All the necessary questions need to come at the beginning:mad:

The good news is that the six or seven times repetition of scripts involved in the installation did not break much.   The bad news is that there was no thorough posting to explain details like this in the spot.   While there may have been a better way than to force installation and fix later I haven't been able to find it in the dpkg installation guide.   My suggestion is the Ubuntu developers force a crash in the middle of the installation and write a guide as to how to deal with it.   It is inevitable given the network installation structure.   Down load a global apt-get install and final clean up that such problems will inevitably arise at least for some users.

---

