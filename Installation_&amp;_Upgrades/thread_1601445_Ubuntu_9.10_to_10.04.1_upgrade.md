---
title: "Ubuntu 9.10 to 10.04.1 upgrade"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by wcorey on 2010-10-20
I had a functioning 9.10 system that I wanted to upgrade to 10.4.1. Nothing but problems. I could not get a functioning cd or thumb drive image to use. I tried upgrading in place but, somehow, my repository got whacked and I was in a persistent partial upgrade scenario. Essentially it said there were 1770 packages and when it went to fetch them it would, at max, retrieve only 1767. I was really trying to avoid a 'start from scratch'. Yesterday I backed up my home dir and usr/local and vmware and resigned myself to install from scratch off the live thumbdrive image. Right after it formated the partition the install died with an IO error. 

Fortunately I had the original 9.10 cd and did a fresh install from it. I next upgraded a clean 9.10 image to current in preparation for upgrade. All this worked fine.

Next I answered yes to upgrade to 10.4.1 on the update-manager app. This said there were 1330 packages to download and proceeded to download them.

It got as far as 1327 and stopped, just as it did before, 3 packages short of what it thought it needed. 

I realize there have been a barrage of issues upgrading to 10.4. I would greatly appreciate someone spelling out what precisely needs to be done to facilitate this. 

Thanks,
Walt

---

### Post by searchfgold6789 on 2010-10-20
Maybe Ubuntu is rounding off the packages to be installed to the nearest 10.
Finding out the three packages that don't install might help us. 
The i/o error you received is probably the result of a bad download or badly/quickly burnt or defective CD. (Or it might help to temporarily remove faulty RAM)
Did it just stop downloading, or did it only install most of the packages? You could try a ```
sudo apt-get update
``` before you upgrade.
Post back if anything starts working.
Good luck,
 - search

---

### Post by wcorey on 2010-10-20
Once I had a clean 9.10 image and I did, functionally, a 

sudo apt-get update
sudo apt-get dist-upgrade

I did it through the UI though, it worked perfectly.

I cut the CD's from a laptop running 10.4 which actually upgraded perfectly last Spring. I burned multiple cd's. I also, first try, successfully burned a 10.10 server image. The thing that really concerns me is the flash drive of 10.4.1 works fine booting up, no problems. When I tried a fresh, from bare metal, install it formatted the drive then through an IO exception. That's the first time I ever saw that. 

So now I am back to a fresh, up to date, 9.10 and I still can't get to 10.4.  I was wrong on the counts. I did get an updates available notice today that there were 4 more for 9.10. I installed them just fine but then tried, again, to upgrade to 10.04.1 from the update-manager app. Same precise problem, it said there were 1334 packages to download and it got stuck on 1331. So it appears to be a problem with 10.04.1. I upgraded 2 machines at home (32 bit laptop and 64bit Dell 720, to 10.4 with no issues. 

The upgrade does not do a sudo apt-get update, as that works with the current 9.10 repository. It, instead, points to the 10.4.1 repository or some such as when the upgrade to 10.4 fails it says it restores the prior sources.

The other thing that may be telling is yesterday, I tried the no internet upgrade by downloading the alternate image and mounting it to the loop driver and doing an cdromupgrade. It STILL went to the internet, even after I specitied NO (don't try to get the current uptodate packages. I was so surprised at that that I tried with the nic disconnected and the upgrade immediately failed. 

This is so completely bizarre. I am at a loss to explain this ordeal.

But if someone could say here is what you do, I would greatly appreciate it. I do not believe this has anything to do with the chip set as it doesn't even get that far.

I tried, the other day, to change software sources from  Main to something else and it made no difference. That is why I did not try it today. Turns out today it worked and I got those remaining three packages and it upgraded.

---

