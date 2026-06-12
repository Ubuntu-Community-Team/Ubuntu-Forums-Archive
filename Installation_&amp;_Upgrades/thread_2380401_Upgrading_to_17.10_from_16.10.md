---
title: "Upgrading to 17.10 from 16.10"
date: 2017-12-16
forum: Installation &amp; Upgrades
---

### Post by Edward_Diener on 2017-12-16
I am running Ubuntiu 16.10. Software Updater is prompting me to upgrade to Ubuntu 17.04, yet I can see on the Ubuntu website that 17.10 is available. Why does the Software Updater program not ask me to upgrade to Ubuntu 17.10 ? 

When I did update to 17.04 from 16.10 previously through Software Updater, after backing up my Ubunti 16.10 system, the resultant Ubuntu was a failure, as it brought me to a 640 x 400 login screen which did not log me in to anything resembling ubuntu as the 640 x 400 login screen remained prompting me to login even after I did so, and nothing resembling a Ubuntu desktop appeared. After restoring my 16.10 system I was able to reboot successfully to Ubuntu 16.10.

---

### Post by deadflowr on 2017-12-17
> Why does the Software Updater program not ask me to upgrade to Ubuntu 17.10 ? 

16.10 is a dead release (no longer supported) so it never got any updates that would allow that.
(And it wouldn't have gotten that anyway even if 16.10 was still alive, standard non-lts releases only move up to the next release and never skip unless the next release is dead; which why if you run 16.04 (an lts) and look to upgrade to the next normal non-lts release, it would be 17.04, since that is the next still supported release. Come next month when 17.04 goes dead, then you would be able to upgrade to 17.10 from 16.04.
non-lts releases are only supported for 9 months so those can only be upgraded to the very next release, sort an opposite effect of the lts method, since those will never get the updates that any new release exist)

As if that makes sense
but I hope it does

---

### Post by Impavidus on 2017-12-17
Even if you somehow try to force an upgrade to 17.10, I expect that to be less reliable than the regular upgrade to 17.04. 16.10 reached end of life last July and shouldn't really have been used since. Your best course of action is probably a clean install of 17.10.

---

### Post by Edward_Diener on 2017-12-17
> **Impavidus said:**
> Even if you somehow try to force an upgrade to 17.10, I expect that to be less reliable than the regular upgrade to 17.04. 16.10 reached end of life last July and shouldn't really have been used since. Your best course of action is probably a clean install of 17.10.

Will not a clean install of 17.10 will wipe out everything I have with 16.10 ?

---

### Post by Edward_Diener on 2017-12-17
> **deadflowr said:**
> 16.10 is a dead release (no longer supported) so it never got any updates that would allow that.
(And it wouldn't have gotten that anyway even if 16.10 was still alive, standard non-lts releases only move up to the next release and never skip unless the next release is dead; which why if you run 16.04 (an lts) and look to upgrade to the next normal non-lts release, it would be 17.04, since that is the next still supported release. Come next month when 17.04 goes dead, then you would be able to upgrade to 17.10 from 16.04.
non-lts releases are only supported for 9 months so those can only be upgraded to the very next release, sort an opposite effect of the lts method, since those will never get the updates that any new release exist)

As if that makes sense
but I hope it does

So there is no way to upgrade using 16.10 because it is a dead release ? It did ask me to upgrade to 17.04, but the one time I tried that was a failure. The upgrade went "OK" but attempts to login to 17.04 brought me a 640 x 400 login screen and after giving my password, it never logged in but returned me to the login screen. Something was terribly wrong.

All I am trying to do is upgrade 16.10 to something usable since it gets no updates. This should not be so hard.

---

### Post by Impavidus on 2017-12-17
> **Edward_Diener said:**
> Will not a clean install of 17.10 will wipe out everything I have with 16.10 ?

Yes, it will. Well, no necessarily, and data you keep on a separate partition like a /home partition should be quite safe, but definitely assume that it may wipe everything, so make sure you've got backups.

It's best to upgrade before the release you upgrade from goes end of life, but you can still upgrade from 16.10 to 17.04. The upgrade was offered to you, you tried it and it failed. Unfortunately, release upgrades occasionally fail and when that happens, the easiest way out is a fresh install.

---

### Post by ian-weisser on 2017-12-17
> **Edward_Diener said:**
> The upgrade went "OK" but attempts to login to 17.04 brought me a 640 x 400 login screen and after giving my password, it never logged in but returned me to the login screen. Something was terribly wrong.

That is the problem you needed to solve months ago to make upgrading a worthwhile option.

Fix your video driver on an upgrade to 17.04, or backup your data and clean-install a supported release of Ubuntu.
Those are your two supported options. Choose one.

Upgrading directly to 17.10 is UNSUPPORTED. Don't count on much help from support when you do something unsupported. You can do it. There are threads here that tell you how. But if it fails, have a backup plan ready.

---

### Post by Edward_Diener on 2017-12-18
> **ian-weisser said:**
> That is the problem you needed to solve months ago to make upgrading a worthwhile option.

Fix your video driver on an upgrade to 17.04, or backup your data and clean-install a supported release of Ubuntu.
Those are your two supported options. Choose one.

Upgrading directly to 17.10 is UNSUPPORTED. Don't count on much help from support when you do something unsupported. You can do it. There are threads here that tell you how. But if it fails, have a backup plan ready.

How do I fix my video driver ? I have a GeForce GTX 960 Graphics Card and it seems to work fine in 16.10. I am supposed to install a particular driver for it, and if so how do I do that ?

---

### Post by QIII on 2017-12-18
Let's reset for a moment.

What release do you have installed right now?

---

### Post by Edward_Diener on 2017-12-18
> **QIII said:**
> Let's reset for a moment.

What release do you have installed right now?

My current release is 16.10. My previous upgrade to 17.04 failed and your comment suggested it might be because of my video driver. So my thought was to install the particular video driver I need ( if it is not already installed ) and then the upgrade to 17.04 might succeed.

---

### Post by QIII on 2017-12-18
No, I didn't suggest it might be due to your GPU driver.  But the appropriate answer was given.  There is no direct path to update from 16.10 to 17.10 without going through 17.04 - which would be an upgrade through a release that has nearly reached its End of Life as well.  

The chances that you will be successful in upgrading through that path are slim to none.  You are far more likely to encounter the same significant negative emotional event you already encountered.

Your best bet would be to do a fresh installation of a supported LTS release (16.04) and do a direct LTS to LTS upgrade to 18.04 when it is released.  You can do that without losing your important data in your /home directory, but back it up anyway.

I don't do release upgrades any longer.  I do fresh installations for newer realeases and stick to LTS releases for my daily use machines.  I keep up with interim releases in virtual machines.

---

### Post by Edward_Diener on 2017-12-19
I was able to successfully upgrade this time from 16.10 to 17.04 using the GUI upgrade manager triggered from the Software Updater application. One thing I realized before the upgrade is that I had Nemo set as the desktop handler and file manager. so I ran the appropriate commands to reset Nautilus as the desktop handler and file manager before I ran the upgrade this time. Perhaps having Nemo set as the desktop handler and file manager before running the upgrade the previous time, where it failed miserable upon reboot as I described in my initial post, caused the problem. But I am glad everything is now working properly. Thanks for the help of everyone in this thread who commented on my problem.

---

### Post by ian-weisser on 2017-12-19
That is wonderful news! 
Congratulations upon a successful release-upgrade.

One rather common tip around here is that you get the best chance of success at a release-upgrade when you return your packages to as close to stock condition as possible.

---

