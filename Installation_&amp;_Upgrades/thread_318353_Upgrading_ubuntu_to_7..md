---
title: "Upgrading *ubuntu to 7.*"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by wlamia on 2006-12-13
Please, please, PLEASE, everyone in the *ubuntu community. When 7.04, codenamed Feisty Fawn, is generally relased, PLEASE create, test, document, test, publish, and test a bullet-proof, newby-proof, expert-proof, reliable, simple to understand and perform, no mistakes, fool-proof UPGRADE process. 

No multiple posts to read, no lost X-servers, no disk reformatting, no reinstalls, no lost files, no lost usernames, no security holes, just a plain, simple, works-every-time one-step upgrade process. 

From 6.06 to 7.0x (whatever it turns out to be)
From 6.10 to 7.0x

Am I asking too much? I have tried unsuccessfully several times to upgrade, only to have to reinstall the whole OS. Fortunately, I did not have any significant work to lose, and a vanilla installation. No more. I now have real, valuable data to preserve, and lots of custom installations that I don't want to repeat installing. If I want to do that, I might as well install Vista.](*,) 

One last time, PLEASE, all you developers, make a simple, reliable, and fool-proof upgrade to 7.0x before you release anything else.

---

### Post by pay on 2006-12-13
> **wlamia said:**
> Am I asking too much?Yes. Considering the variations in hardware and configurations, something will inevitably go wrong for someone somewhere. But the normal way to do it would be to change your sources.list to an feisty sources.list and run sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by wpshooter on 2006-12-13
I will say it again, upgrading from one version of an O/S to another version of that same O/S (as opposed to a complete new install from scratch of the new version) generally did not work in M/S windows and generally I don't think it is going to work in Ubuntu/Linux.

If you want to have a stable/reliable O/S, install it from scratch.

---

### Post by wlamia on 2006-12-13
I'm sure there are myriad experiences with upgrades, but my own personal experience has been on various occasions to upgrade from W95 to W98 to WXP. IIR, I had to reinstall the apps from 95->98, but the 98->XP was straightforward (if time consuming) and did not even need apps reinstalls. 

I don't disparage anyone else's experience, but I still think that a simple, reliable upgrade process is essential. At the very least, it should warn me if there are hardware configuration situations that might be problematic, and let me abort the upgrade if there are any doubts.

---

### Post by pebo on 2006-12-13
> **wpshooter said:**
> 

If you want to have a stable/reliable O/S, install it from scratch.

Installing an o/s isn't a trivial matter - whenever you install a new kernel you can expect to have issues with drivers such as wireless, graphics cards etc. so a fresh install is the best option.

If you have a separate /home partition you can keep all your data - just don't format it during the new installation. (Back it up first of course:) )

---

### Post by xabbott on 2006-12-13
Yea, be it Linux or Windows. Upgrading from one version to another is not recommended.

I personally find it easier to upgrade on Linux because I keep a seperate data and /home partition. I highly recommend doing that.

---

### Post by wlamia on 2006-12-14
Saving and restoring /home is not the biggest problem (until I get to many Gb of files) - it's restoring all the optional components I installed. I am unaware of any way to automate this restoration. If there is one, it would make doing a clean re-install a lot easier.

---

### Post by darrenm on 2006-12-14
I've never had a problem with dist-upgrading. Whether from Dapper to Edgy or Edgy to Feisty.

That said, I have done my bit and filed a bug report for Feisty :) [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.19/+bug/73108](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.19/+bug/73108)

---

### Post by Tipo on 2006-12-14
I have yet to encounter a problem during upgrading.  All I really had to do was get update manager to recognize my Edgy CD (which was simple and done graphically) and click 'update' :/

---

