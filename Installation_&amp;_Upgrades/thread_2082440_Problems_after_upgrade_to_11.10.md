---
title: "Problems after upgrade to 11.10"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by davejm73 on 2012-11-09
Hi

Im new to the forum, but have been working on Ubuntu for 2 years now and happily. Ive updated my system to 11.10 today and now my computer is slower than anything - even my internet connectivity keeps crashing to such an extent I cannot work anymore. 

Im not literate in computer language, but would appreciate it if someone can help me fix this issue. 

Thanks

---

### Post by Mr_JMM on 2012-11-09
If you back up your ~/home directory would you be willing to install 11.10 as a fresh install rather? I mean wipe the /root partition (if you created a separate home partition) and reinstall from scratch? That would be my personal choice. On older machines I've found this to be a better option.
If you backup home or have home on a separate partition it makes it a lot easier and you won't lose your data. You will have to install applications again though but settings are stored in home/.local so they're safe too.

---

### Post by darkod on 2012-11-09
1. Upgrades can often make issues, especially if you run many upgrades in a row without a clean install.

2. For a stable OS and without big risk of different issues, you might stick to LTS releases which have much longer support, you can upgrade from LTS to the next LTS. Clean install is of course always better.

You waited so long on 11.04 I don't see a reason to upgrade now to 11.10.

At this point of time I would also say to backup all your personal data and try a clean install of 12.04.1 LTS. You can try it in live mode from the cd first and see how it runs on the machine. Then do the clean install if you like it.

---

### Post by ibjsb4 on 2012-11-09
I too think 12o4 is worth a try.  It will be supported for five years, but an LTS comes out every two should you wish to upgrade.

12o4 also has the Unity desktop as default.  It can run in 2D if your system cannot support the 3D mode.  And if you want something that looks like your old gnome2 desktop you can install gnome-classic.

---

### Post by Slim Odds on 2012-11-09
I've been mentioning this more and more, but ***most*** people should really be sticking with the LTS releases.

---

### Post by snowpine on 2012-11-09
Recommend that you burn a few Live CDs or Live USBs and test-drive them to find the distro/release that gives best performance on your specific hardware (which you haven't mentioned what it is). Perhaps in this case trying 11.10 *before* clicking the Upgrade button would have exposed the incompatibility and saved you the hassle? Also recommend to use the forum Search feature for your specific computer model, to see if other users have had the same problem, and if so, were they able to fix it (and how)?

---

### Post by Inoki on 2012-11-09
The safest way to upgrade is always do a fresh install.

I have it set up the way, that I got my / partition on a separate drive than /home, so I never lose anything, similar to in Windows having your programs on C: and Documents and Settings on D:

At boot I always choose to format only / as my main partition for programs and mount the /home partition, that way only the previous install is erased, leaving my files intact and usable with the next version.

Hope this helps.

---

