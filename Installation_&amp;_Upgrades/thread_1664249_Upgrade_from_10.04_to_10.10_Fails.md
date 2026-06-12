---
title: "Upgrade from 10.04 to 10.10 Fails"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by Rick B. on 2011-01-10
In trying to upgrade from 10.04 to 10.10, the installation fails when checking software channels. The error basically says that there are breaks, broken depends and unmet dependencies. Yet Package Manager shows that there are no broken packages and mostly everything is running OK except for the Suspend option which doesn't work in 10.04 on a good number of various laptops. I am using an IBM Thinkpad R51 laptop with 1.5 GHz and 512 MB RAM. I have never had a problem like this with any Ubuntu upgrade in the past. How can I get past this problem and upgrade to 10.10? Log files available upon request. If log files needed, please be specific about what file you want to look at. Someone on Launchpad said it's because I have third party software installed. But, this never happened before with previous Ubuntu upgrades. They all went smoothly. Thanks.

---

### Post by ajgreeny on 2011-01-10
Certainly if you have any ppa repos enabled, disable them first as they will probably cause difficulties.  Any manually installed applications can cause problems if the dependencies for them in the new OS do not meet the requirements of those manually installed apps, so it may be worth removing them and trying again.

Otherwise I have no more offerings; I always do clean installs, rather than updates, and have yet to have any major problems after nearly 6 years of Ubuntu.

---

### Post by Rick B. on 2011-01-10
OK. I'm, just curious why I didn't have this same failure in the past 3 Ubuntu upgrades since it upgraded fine with third party software installed? And doesn't the upgrade program automatically disable the third party PPAs when checking the system software anyways? OR is 10.10 Maverick that different from all previous Ubuntu versions? 

I am on my desktop now and will give it another shot in the morning on my laptop and report the results here in this thread. Thanks for responding!

---

### Post by Pumalite on 2011-01-10
I just upgraded from 10.04 in 3 computers without a problem, but I first removed all third parties from my sources list, had my 10.04 fully updated and had no programs installed by hand

---

### Post by Rick B. on 2011-01-11
Thanks for all those who replied about this problem. Manfred Hampl from Launchpad had the correct answer to this error, based on the following information:

"There is a known problem that the 10.04 to 10.10 upgrade fails with the error message
"Could not determine the upgrade
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu"

If that is your error message, and if you have the package xserver-xorg-video-nouveau installed, then removing that package can help (see bug 663158, bug 658458 and bug 658581)"

The third party software and PPAs had nothing to do with the problem. It was the bugs which Manfred described above. I removed the xserver-xorg-video-nouveau package which I noticed is "experimental". The upgrade ran OK on both my IBM laptop and Dell desktop this morning. No hitches. 

The suspend option for my IBM Thinkpad R51 laptop still doesn't work with 10.10. It did not with 10.04 but did work fine with 9.10. Is a fix for this coming down soon? 

It's really good to know that good support for Ubuntu can be found here at Launchpad and on the forums. Thanks again to everyone.

---

### Post by spek578 on 2011-02-06
great help guys, saved me some trouble by reading all your very helpful responses

---

### Post by Shamgar91 on 2011-02-09
I had the same problem and this helped out! Thanks guys

---

### Post by Guilden_NL on 2011-02-10
Thank you Rick B.!  Leave it to a fellow Michigander to have the right solution.

Strange for me. I started with Lucid Lynx, upgraded to Maverick Meerkat on this laptop, but last week I installed the Natty Narwhal Alpha and have been playing around with it.  But needed the laptop to be stable for some work, so went with a clean install from a Karmic Koala ISO CD I had (loaned the Lynx to someone). Went to upgrade this time, ran into this problem.

So thanks for posting this Rick. Seems that Ubuntu went a little wild with their Lynx upgrade process.

---

### Post by ostbahnx on 2011-02-11
Thanks for the solution.  Uninstalling that xserver-xorg-video-nouveau  solved my upgrade problems.

stephen

---

### Post by curig on 2011-02-15
I had the same problem and removing xserver-xorg-video-nouveau also seems to have solved it.

---

### Post by centec2b on 2011-02-16
Uninstalling that xserver-xorg-video-nouveau solved my upgrade problems

Thank you & respect to all the contributors 

I found this after many hours banging my head against a "brick wall".  If any moderator comes across this, it may be an idea to give it a higher profile

Regards

Centec2b

---

### Post by Jesper Ø. Jensen on 2011-02-28
Uninstalling that xserver-xorg-video-nouveau solved my upgrade problems

That helped me upgrading two computers as well.

Thank you so much for the tip

---

### Post by tomhay99 on 2011-10-16
I uninstalled xserver-xorg-video-nouveau but the upgrade still failed. After more investigation I found that the Adobe Flash package was causing problems.  When I removed that, the upgrade went fine.

---

