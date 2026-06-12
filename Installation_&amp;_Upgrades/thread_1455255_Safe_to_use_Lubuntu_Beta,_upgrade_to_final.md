---
title: "Safe to use Lubuntu Beta, upgrade to final"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by jwmollman on 2010-04-15
I'm so excited to see how nicely Lubuntu 10.04 runs on my EeePC. I went ahead and installed it, knowing that it's just the second beta. Everything seems to be going nicely, but when I did a "sudo aptitude update && sudo aptitude safe-upgrade" it showed there were tons of updates (about 90MB worth). I saw updates for Chrome, the kernel, xserver-xorg, etc.

I understand this is just a beta operating system and is not recommended to be used as a primary OS, but I'm just so excited and can't wait. If I stay with this install, and keep updating, would I eventually make my way to the final release? Or would you recommend doing a reinstall with the final image?

---

### Post by ajgreeny on 2010-04-15
If you keep updating you will end up with the final release version.  There may be a lot of un-needed config files but they should not be a problem, and if you have a small SSD you may need to run sudo apt-get clean to get rid of GBs worth of update packages from the cache.

---

### Post by jwmollman on 2010-04-15
> **ajgreeny said:**
> If you keep updating you will end up with the final release version.  There may be a lot of un-needed config files but they should not be a problem, and if you have a small SSD you may need to run sudo apt-get clean to get rid of GBs worth of update packages from the cache.

Thank you. And I have the 1000HA which has a 160GB hard disk drive. After every update or install/uninstall of applications, I always run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

So are you saying with sudo apt-get clean, all those config files will be removed?

---

### Post by maddg3241 on 2010-04-15
ya there is only 14 days to go :):P :guitar:

---

### Post by ajgreeny on 2010-04-16
```
sudo apt-get clean
``` only removes all the old package files from cache, not the configuration files I spoke of, but they are only small in comparison with the packages so will not really cause any problem.

autoremove will get rid of any packages that are not needed as dependencies of applications that you have removed manually, and are not needed in themselves, or as dependencies of any other apps you have.

I don't know if synaptic is part of a standard lubuntu (LXDE) install, but that would be one possible way to get rid of un-needed residual configuration files, by clicking on the status button in the left hand panel, and choosing the next to bottom option, I think, which shows "residual configuration" or some similar description, which you can then "remove completely".   You can certainly install synaptic on lubuntu, and I would recommend it as the best package manager around for any deb based system.

---

### Post by Pierre16 on 2010-04-24
I installed Lubuntu Lucid Beta2.  How do I safely and properly upgrade to RC1 and the final version when they come out?

1) From the above, one correct and safe way would be:
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoclean 

Will that upgrade to only Lubuntu and not Ubuntu even though the commands are the same?

2) Beta2 has Synaptic installed.  Could it be used instead.  If so, what are exactly the steps?

3) Last week, I did a "Mark all Upgrades" with Synaptic.  There were dozens to be done according to the results.  How is this possible since RC1 was not released yet?

Thanks.

---

