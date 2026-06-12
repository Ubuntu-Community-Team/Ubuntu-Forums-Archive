---
title: "Upgrading from Ubuntu 15.04 Server to latest version"
date: 2019-01-05
forum: Installation &amp; Upgrades
---

### Post by ndnd on 2019-01-05
Hello I have done an upgrade from an older version long time back and wanted to double check if this is the best way. I **_do not_** wish to install from scratch. 

My current installation is 

> 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 15.04
Release:        15.04
Codename:       vivid


After searching online briefly I wanted to confirm if this is the right line of action ? 

> 
Edit "/etc/apt/sources.list" (with root permissions) substituting all the links: "http://archive.ubuntu.com/..." for "http://old-releases.ubuntu.com/..."

Then do the 
$sudo apt-get update && sudo apt-get upgrade


If not can you please provide some details as I don't want to take any chances and am still a newbie :) 

Thank you in advance for your help :)

---

### Post by QIII on 2019-01-05
Hello!

If you don't want to take any chances, *don't try* an EOL upgrade, followed by another EOL upgrade, followed by an upgrade to a supported version.

If you try to upgrade from 15.04, you would have to first upgrade to 15.10 (also unsupported) and then to 16.04 LTS.  There is very little chance that this could be done with any hope at all of success.  There were substantive changes in 16.04.  I would estimate that your chances of success are very close to your chances of being hit by a meteor and living to tell the tale.

I would absolutely recommend against going the old-releases route, as you are almost certainly going to suffer through a significant emotional event when your OS is entirely non-operational and you will end up re-installing fresh in the end anyway.  Your best course of action is to back up all of your important files and install 16.04 or 18.04 fresh.

However, if you insist on entering a quagmire and taking your very slim chances on success, [this]("https://help.ubuntu.com/community/EOLUpgrades") is the process.  Again, your path must be 15.04 -> 15.10 -> 16.04.  A 15.04 -> 16.04 attempt is even more likely to end very badly.

***Strong warning:***  This is not likely to work.  Back up your data and install 16.04 fresh.  You have been warned.

---

### Post by Autodave on 2019-01-05
+1 with QIII: this is not going to work.  Do a clean install.  In fact, I would do a clean install of 18.04 and then you will be set for quite awhile.

                        Every 2 years, a long term service release is made.  18.04 was the last one: released during the 4th month of 2018, hence the name 18.04.  The next LTS release will be in 2020 during the 4th month.  In the meantime, a new, short term release will be issued every 6 months.  These short term releases are only supported until the next short term release. However, the LTS releases are supported for 5 years.  It is always best to stick with the LTS releases. When it comes time to upgrade one of those, I have always found it easier and quicker to just backup what I need to keep, wipe out what is there, and do a clean install.

The server LTS releases are supported even longer: I believe for 10 years, but not positive on that.

---

### Post by ndnd on 2019-01-06
I see your points QIII and Autodave. 

Thank you both for the replies. I will go for a clean install. However, I do have the following questions based on your answers 

Is this the norm every two years you do a clean install  or can you keep upgrading every few months.  I am not too worried about data as it is on a seperate disk however, there are lot of other installations (including licensed third party applications) which are a pain to configure etc. 

Can you explain if there are more efficient ways to transfer the applications ?

---

### Post by CatKiller on 2019-01-06
Your issue was that 15.04 was an interim release rather than an LTS release, so it only had 9 months support. LTS releases are supported for five years.

LTS releases are the ones to use. The interim releases are for testing. If you install a non-LTS version, you need to stay on the upgrade treadmill till you get to the next LTS.

Five years is long enough that you can skip the next LTS entirely before your fresh install, if you wish to, and still wait a year for the bugs to settle out before installing. You'll have security updates for all of that time.

Interim releases are only for masochists and idealistic enthusiasts.

---

### Post by Impavidus on 2019-01-06
Release upgrades a a bit of hit or miss. For some people (like me) they always work, for some people they sometimes work and for some people they never work. EOL upgrades are worse.

Count me with the idealistic enthusiasts. I used to stick with LTS releases, but since 13.10 I always use the interim releases. I never had any trouble. But for a server, the LTS releases are probably better.

---

### Post by jdeca57 on 2019-01-06
It may seem that there is little or no progress in development but for some features that is not the case. For the desktop recent versions of Gimp are very interesting (if you edit photo's) and if you draw with a Wacom tablet then the drivers are now included in the kernel. These are my reasons to stay with the latest version of the OS and yes, there may be issues but I accept them. For a server, the idea is to offer the greatest stability so the reasoning is of course different.

---

### Post by Topsiho on 2019-01-06
I agree with the above posts, and am glad that OP is listening, and doing a fresh install.
A fresh install is, provided you have fast internet, very easy and fast (for me the install process itself takes about 15 minutes). If you have a separate /home partition you'll only have to refresh your / partition, as it's the partition all the **system** files get into.
All your data (which you'll have to back up first if you don't want to loose them, as a precaution) and settings are in your /home partition, and **if you take care not to reformat that partition**, you'll find them unscathed after the next reboot.
After that however, you'll have to update your system (as you normally update it regularly), and eventually you'll have to reinstall any software that is not (re)installed during the install.
So that'll keep you busy somewhat :), giving you the chance to clean up your system a bit, not reinstalling any software you never use.

Topsiho

---

