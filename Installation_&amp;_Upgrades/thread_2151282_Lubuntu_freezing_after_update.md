---
title: "Lubuntu freezing after update"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by r3g on 2013-06-04
Hi,

I upgraded to 13.04 a few days ago and everything has been running fine, but I ran some recommended updates yesterday and now my netbook keeps freezing.

It always seems to freeze when I'm typing, but I can't say if that is the trigger or if it's just coincidence that it does it then. There doesn't seem to be any particular time frame on when it freezes and I can leave it for over an hour when it happens and it doesn't recover so I have to just power off.

I checked in the log files to see what was installed but I'm not proficient enough with linux to know whether I'm checking in the right place or how to revert any updates to see what's causing the problem.

I went to /var/log/apt/history.log and the contents look about right for what was installed;


> Start-Date: 2013-06-03  07:06:07
Commandline: aptdaemon role='role-commit-packages' sender=':1.40'
Install: linux-headers-3.8.0-23:i386 (3.8.0-23.34), 
  linux-image-extra-3.8.0-23-generic:i386 (3.8.0-23.34), 
  linux-headers-3.8.0-23-generic:i386 (3.8.0-23.34),
  linux-image-3.8.0-23-generic:i386 (3.8.0-23.34)
Upgrade: libfontembed1:i386 (1.0.34-0ubuntu1, 1.0.34-0ubuntu1.1), 
  libgnutlsxx27:i386 (2.12.23-1ubuntu1, 2.12.23-1ubuntu1.1),
  linux-headers-generic:i386 (3.8.0.22.38, 3.8.0.23.39), 
  cups-browsed:i386 (1.0.34-0ubuntu1, 1.0.34-0ubuntu1.1),
  linux-image-generic:i386 (3.8.0.22.38, 3.8.0.23.39),
  cups-filters:i386 (1.0.34-0ubuntu1, 1.0.34-0ubuntu1.1),
  libgnutls26:i386 (2.12.23-1ubuntu1, 2.12.23-1ubuntu1.1),
  linux-libc-dev:i386 (3.8.0-22.33, 3.8.0-23.34),
  libgnutls-dev:i386 (2.12.23-1ubuntu1, 2.12.23-1ubuntu1.1),
  libservlet3.0-java:i386 (7.0.35-1~exp2ubuntu1, 7.0.35-1~exp2ubuntu1.1),
  libgnutls-openssl27:i386 (2.12.23-1ubuntu1, 2.12.23-1ubuntu1.1),
  libcupsfilters1:i386 (1.0.34-0ubuntu1, 1.0.34-0ubuntu1.1),
  linux-generic:i386 (3.8.0.22.38, 3.8.0.23.39)
End-Date: 2013-06-03  07:11:31


Assuming that I'm in the right place to know what was installed, how do I go about removing these in some sort of structured order to see which one is cauising the freezing?

I'm not sure if any of the packages are dependent on each other and if I remove just one, I might break things further.

Any assistance would be much appreciated.

Thanks,

Richard

---

### Post by ohnonot on 2013-06-04
just a kernel upgrade,mostly?
could the problem have sth to do with screensaver/power-manager?
(not that i know what i'm talking about)

---

### Post by r3g on 2013-06-05
> **ohnonot said:**
> just a kernel upgrade,mostly?
could the problem have sth to do with screensaver/power-manager?
(not that i know what i'm talking about)

Hi,

Not sure, but I'll check it out.

If I switch off the screen saver and power saving features I would have thought that would do the trick if it is related, so I'll do that and post back the results.

Thanks.

---

### Post by r3g on 2013-06-05
OK, tired disabling the screensaver and switched of all power saving features and rebooted.

Looked OK at first, but then froze after about 7 minutes.

Does anyone know how to roll-back an update?

Thanks.

---

### Post by r3g on 2013-06-05
Just found this thread [http://ubuntuforums.org/showthread.php?t=1804985]("http://ubuntuforums.org/showthread.php?t=1804985") which mentions how to revert to a previous version of a package. dFlyer states that you can use;
> sudo dpkg -i "packagename" without the quotes to revert back to the old package. 
But it's going to be very hard to do when, A) I don't know which package is causing the problem and B) They system could freeze in the middle of the package update.

Is it possible to carry out maintenance like this on a system using a Live CD?

Thanks.

---

### Post by ohnonot on 2013-06-05
back to your first post. *from what* did you upgrade to 13.04?

your last post: i don't think this will work with a kernel upgrade.
however you should have multiple kernel entries in your grub, like "advanced options for lubuntu" --> chose the oldest kernel (smallest version number).
do you see the grub menu when you boot?

---

### Post by r3g on 2013-06-06
> **ohnonot said:**
> back to your first post. *from what* did you upgrade to 13.04?

your last post: i don't think this will work with a kernel upgrade.
however you should have multiple kernel entries in your grub, like "advanced options for lubuntu" --> chose the oldest kernel (smallest version number).
do you see the grub menu when you boot?

Hi,

I was on 12.04LTS previously.

I don't see a grub menu on boot, just a blank screen until the Ubuntu logo.

Also, I think this may now be a wild goose chase. I had a dig around on one of my old computers and found an image for 10.04 Netbook, so I installed that to an SD card and booted from there, but after a few minutes it froze again, so I don't think the issue is to do with the updates anymore, it seems to have just been a coincidence that it started to freeze immediately after an update.

It looks like I could have a more serious hardware issue, probably something overheating.

I'll strip it down and clean out the air vents and check the fans, but it may already be too late to save it.

Thanks for the assistance anyway.

Richard

---

### Post by ohnonot on 2013-06-07
sad. :-(

however, i'd try installing different distros *from scratch*, once you saved your data. distrowatch.com.

---

