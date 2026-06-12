---
title: "Errors after upgrading from Ubuntu 12.04 to 14.04 LTS"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by skcgirl on 2014-09-26
I've been running Ubuntu 12.04 just fine without any issues and then I received some prompt a few weeks back to upgrade to 14.04. The upgrade itself was fairly uneventful however every time I log in to my system, I get "system error" after "system error". It doesn't say anything specific about what the issue is other than the fact it has a system error in a little pop up window and asks if I was to simply send a log to report the issue which I do every single time. On top of that I don't seem to be getting any available updates. I don't log in too often and usually when I do I have like 50-100 updates to install and there's nothing there which I know can't be the case. 

What options do I have? Should I just scrap the whole distro and start from scratch? How would I even do that on a dual boot system? 

Thank you so much, sorry to bug you guys.

---

### Post by T.J. on 2014-09-26
[Dup post]

---

### Post by T.J. on 2014-09-26
I'm sorry to sound gloomy, Skcgirl, but my experience has shown me consistantly that you should always install a clean copy, rather that do an upgrade of an existing system when working with Ubuntu.  Unless you are familiar with the insides of the system, and know how to fix broken packages, you are just asking for trouble.  I would use the install CD to boot Linux without installing it - run it in "Live" mode.  From there you should be able to backup anything you need to save.  Then I would just reinstall Ubuntu. I realize this is not what you want to hear or an ideal solution, but it is the easiest and most expedient way to get you back where you need to be.

On a dual boot, just reinstall over the existing Ubuntu, and leave Windows be.  As general word of caution, you should never install any OS on an existing computer without backing up your data first, in case you make a mistake and erase the wrong thing.

---

### Post by skcgirl on 2014-09-27
I'm actually taking a Linux Administration class right now so patience with us noobs is definitely appreciated. It's quite evident that something is definitely concerning about this last upgrade seeing the very high amount of posts related to this issue. The suggestion by "Bashing-om" in a related thread which was to make sure the package manager is happy definitely seemed to help. After rerunning those commands, I found where the update is actually failing and will resolve it accordingly. Thank you for your time.

---

### Post by T.J. on 2014-09-28
Awesome!  I hope your class goes well.  

Just as a parting comment, I'd like to say that "in place" upgrades on Linux are usually quite workable.  The reason I do not recommend them on Ubuntu is because Ubuntu is based on Debian Unstable or Debian Testing - rather than Debian Stable.  Canonical officially maintains only a small subset of Debian's huge package base - which means that bugs are sure to creep in when you are doing full upgrades from one version to the next.  Canonical tries, but reality being what it is, a lot of the packages in the Ubuntu "universe" repository do not see the patches that they should, and are just replaced with a new copy from the beta version of Debian when Ubuntu releases again - only to start the whole vicious cycle all over.

---

