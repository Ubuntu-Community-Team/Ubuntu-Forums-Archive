---
title: "Could not calculate the upgrade (64-bit, 7.10 to 8.04)"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by factotum218 on 2008-04-27
I'm running 64-bit 7.10 and wanted to upgrade to 8.04. I opened the Update Manager and saw that there was one button at the top simply saying new version available (8.04) and to click it if I wanted to upgrade.

So I did.

Now, its telling me:

Could not calculate the upgrade
---------------------------------------------------------------------
A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
----------------------------------------------------------------------

There has in fact been a bug report filed and now am wondering what to do next. I removed a LOT of non ubuntu software and gave it another go. Same thing. I went ahead and disabled all restricted and non free repo's. Still the same thing.

Is this because I am running 64-bit or something? What should I attempt next?

---

### Post by martrn on 2008-04-27
> **factotum218 said:**
> 

Is this because I am running 64-bit or something? What should I attempt next?

From [https://wiki.ubuntu.com/PainlessUpgrade]("https://wiki.ubuntu.com/PainlessUpgrade") It says .."..Upgrading a fresh Ubuntu x to Ubuntu x+1 doesn't give you the same system as installing directly a fresh x+1. This lead to having systems that are, at each release, a bit more far from the current release, with unexpected bugs that cannot be reproduced easily..."...

Linux uses files to store its settings and a dependency will be expected to reside at a place on the current file system.  When your applications are running including low level library these dependencies will be expected to reside at a certain point of the file system. 

From that url I mentioned it states..".. Ironically, most advanced Ubuntu users now reinstall their system every 6 months. The re-installation procedure resolves dependency discrepancies and people who have been a distribution of linux will always re-install rather than upgrade their distribution and keeping all files in their /home directory.

So no is it not the fact you are running 64-bit or something, its the fact that apt can not resolve your dependencies.  Possibly because you either installed some software from another place or software that changed your system in apt-get.

From [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion") I would have thought you could either reinstall the original dependencies and fix any breakages, using libraries in your 7.10 cd then upgrade or follow the Clean Install Upgrade (not recommended) from there.

Its not recommended I think because your system may loose data or data loss is possible.

---

### Post by factotum218 on 2008-04-27
> **martrn said:**
> 
From that url I mentioned it states..".. Ironically, most advanced Ubuntu users now reinstall their system every 6 months. The re-installation procedure resolves dependency discrepancies and people who have been a distribution of linux will always re-install rather than upgrade their distribution and keeping all files in their /home directory.


I have read and digested all that you have provided and I thank you for taking the time to convey this information.
Sadly, what i have quoted above is the first time I have had to deal with doing things in this matter. I.e. a reinstall.
Again thank you very much! But I do not see why I should use something that recommends a complete reinstall. In the eight years that I have used *NIX variants I have never, ever, read a recommendation of a complete reinstall of an operating system (not even in windows, *BSD, or other distributions of GNU/Linux). Previous to my experiences with Ubuntu I have hardly ever found a reason to reboot a system outside of a kernel recompile or upgrade. Nothing against you or any user of Ubuntu, but I find this unacceptable.

Once again, nothing against you and your work to help provide and answer, but seriously... a reinstall? I can not take this seriously.
What of people who are using 6.06, the previous LTS release? From what I have heard they had planned on making the migration to the new LTS release painless. If that means paying for "tech support" to simply reinstall and save all data and setting...Ubuntu is a juvenile offering at best.

And, of course, you have been thanked. Cheers!

---

