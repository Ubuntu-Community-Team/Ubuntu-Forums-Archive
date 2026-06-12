---
title: "Reliability of dist-upgrade/do-release-upgrade and best install strategy on new PC"
date: 2020-01-09
forum: Installation &amp; Upgrades
---

### Post by ofnuts on 2020-01-09
I got a new PC (Thinkpad P53). Nice machine, but not fully supported by 18.04 LTS (wifi chip not supported by that kernel). I can retrofit the wifi driver (there is a backport it seems). Ultimately I want to run Kubuntu 20.04LTS.

If I were patient I would keep the PC in its box until April and install 20.04, but that"s not an option.

Until know I have upgraded my Ubuntu version when changing machines or replacing the boot disk, so things were quite simple. But here I'll have to upgrade in-place and this is unknown territory to me.

Is the process (do-release-upgrade if I get it correctly) reliable (that will be on a LUKS-encrypted disk)? How long does it take (I'm on fiber...)?

What should I install in the mean time? 18.04? 19.10 (which should have the hardware support natively)? Is the upgrade to 20.04 easier from one or the other?

---

### Post by Dennis N on 2020-01-09
If your new computer has 18.04 or 18.04.1, the first thing I would try is to keep your current 18.04, upgrade to the HWE kernel, and try that before going to a newer Ubuntu release.

See this page for explanation of HWE and how to upgrade:

[https://itsfoss.com/ubuntu-hwe-kernel/](https://itsfoss.com/ubuntu-hwe-kernel/)

---

### Post by CatKiller on 2020-01-09
As Dennis N says, the Hardware Enablement Stack will give you a newer kernel (and graphics stack) on an 18.04 base. Install images from the 18.04.2 point release onwards use HWE by default; 18.04 and 18.04.1 install images would need HWE to be enabled manually. The current 18.04 kernel is the same one (5.0) that's used in 19.04; that will be updated to the one (5.3) that's used in 19.10 in February. There will probably be another point release then. 

> **ofnuts said:**
> Is the process (do-release-upgrade if I get it correctly) reliable (that will be on a LUKS-encrypted disk)? How long does it take (I'm on fiber...)?

In my ~15 years of using Ubuntu I've not had a problem with an upgrade in place. I generally do a fresh install with new hardware or an upgrade otherwise. Other people have had issues, though. Some upgrades change more fundamental things than others, and the more customised and further away from a default install - software from PPAs, proprietary drivers, weird configurations - the more likely it is that issues will arise. It generally takes a couple of hours; the delay isn't because of the download, but because every package has to be unpacked and configured in turn rather than just dumped onto the disc at once.

---

### Post by oldfred on 2020-01-09
Do you have 25GB available on drive?
If so you can also install 20.04 now and see how it works. You then can report any bugs to help make it better also.
Just recognize that it will have many updates before release and could have some issue that prevents it from booting. So you should not use it as your main working install.

I use 18.04 as main working install, but have 20.04 in another / (root) partition. When I built my Z170 system in early 2016, only 16.04 worked even though it was not yet released. I recognized that it my have issues, but thought it worthwhile.
I typically reinstall, if I do install the daily version, after final release. Just to houseclean all the extra logfiles and other cruft due to the many updates.

---

### Post by ofnuts on 2020-01-09
> **CatKiller said:**
> As Dennis N says, the Hardware Enablement Stack will give you a newer kernel (and graphics stack) on an 18.04 base. Install images from the 18.04.2 point release onwards use HWE by default; 18.04 and 18.04.1 install images would need HWE to be enabled manually. The current 18.04 kernel is the same one (5.0) that's used in 19.04; that will be updated to the one (5.3) that's used in 19.10 in February. There will probably be another point release then. 

Yes, on my freshly downloaded/installed 18/04 kernel is 5.0.  The kernel that supports my wifi is 5.1. is the 5.0 the HWE kernel or is there some hope that adding HWE would move to 5.1?

> **CatKiller said:**
> 
In my ~15 years of using Ubuntu I've not had a problem with an upgrade in place. I generally do a fresh install with new hardware or an upgrade otherwise. Other people have had issues, though. Some upgrades change more fundamental things than others, and the more customised and further away from a default install - software from PPAs, proprietary drivers, weird configurations - the more likely it is that issues will arise. It generally takes a couple of hours; the delay isn't because of the download, but because every package has to be unpacked and configured in turn rather than just dumped onto the disc at once.

OK so installing 19.10 remains a good option...

---

### Post by CatKiller on 2020-01-09
> **ofnuts said:**
> Yes, on my freshly downloaded/installed 18/04 kernel is 5.0.  The kernel that supports my wifi is 5.1. is the 5.0 the HWE kernel or is there some hope that adding HWE would move to 5.1? 

HWE will go to 5.3 in February. 

>  OK so installing 19.10 remains a good option...

Should be fine, as long as you remember to upgrade to 20.04 when that's released. Lots of people get stranded on the intermediate releases because they forget that they only get 9 months of support rather than the five years that LTS releases get.

---

### Post by cmcanulty on 2020-01-09
Realize you can update from 18.04 to 20.04 but if you go to 19.10 you have to do each incremental release ie- 18.04 to 18.10 to 19.04 to 19.10

---

### Post by TheFu on 2020-01-09
Whenever encryption is involved, excellent backups are mandatory.

---

### Post by SeijiSensei on 2020-01-09
I installed Kubuntu 19.04 then upgraded to 19.10 via do-release-upgrade without a hitch. When something went wrong with that installation, I opted to install the 20.04 development version. So far things are working fine.  This is an older HP laptop, but my experience with 19.04/19.10 on other machines I own suggests they wouldn't have problems with 20.04 either.

According to [https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html), support for that wifi chip exists in kernels 5.1/5.2 or later.

I suggest [downloading]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/") a copy of 20.04 and choosing Try Ubuntu after booting.  See if everything works or not.

---

### Post by ofnuts on 2020-01-09
Thanks all for the information. 19.10 it is, then.

Edit&PS: installed. Had to retry three times but all seems fine now and wifi works.

---

### Post by mörgæs on 2020-01-09
Good, please mark the thread solved.

---

