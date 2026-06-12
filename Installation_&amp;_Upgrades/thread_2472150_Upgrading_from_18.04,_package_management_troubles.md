---
title: "Upgrading from 18.04, package management troubles"
date: 2022-02-18
forum: Installation &amp; Upgrades
---

### Post by Fallen Guru on 2022-02-18
So I decided to finally get off my a— and upgrade my work machine [to 20.04], seeing as I'm currently between projects.

First try, the updater would close right after clicking the upgrade button. No error message. Apparently it doesn't like pinned-version packages, so I unpinned them and tried again.
Second try, it would hang when calculating dependencies. Nothing in the terminal output. Apparently it doesn't like the kisak-mesa PPA, so I ppa-purged that and tried again.

Third try, dependency resolution actually presented me with a result. But it wanted to remove gimp and vlc, and a bunch of other stuff I'd definitely prefer stayed. Not that many, I could just reinstall them after the upgrade. But it also declared a whole bunch of other packages no longer required, and the list was too long, had too much I still wanted. IIRC, earlier update-managers would just offer to remove auto packages with nothing depending on them for you, but this one included them in the count of packages to be removed, so it sounds like it might actually remove them. It's been a while, but It's not my first 18.04 &#8594; 20.04 upgrade, either. Something feels off. Abort and rollback.

1) Does it make sense to wait for 22.04 and upgrade straight to that, or would I have to go through 20.04 anyway?

2) Is there some version of / switch for the updater that makes it a bit less tight-lipped about what's going on and allows some manual intervention? I'd like to figure out why it thinks it needs to remove so much, then do a minimal upgrade and do the rest step by step, something like that.

---

### Post by Claus7 on 2022-02-18
Hello,

a quick response would be:
1) the latter,
2) you could initiate the upgrade via command line and see some more information.

Regards!

---

### Post by TheFu on 2022-02-18
The upgrade process is simple.
Before starting, do these things:
Fully, completely, patch the system. That includes moving to the HWE kernel line on 18.04. This should get you do the base 5.4 kernel used by 20.04. Reboot, be certain everything is clean. No problems.
Next, remove all PPAs (just rename the PPA files in /etc/apt/sources.list.d/ .  Go through a *full-upgrade* cycle. This should remove/replace all the packages that aren't currently compatible with 18.04. Some manually installed .deb files will likely remain, but you'll want to hunt those down and manually remove them. If you don't, expect problems.  Always keep track of any manually installed .deb files.
Run your normal clean up stuff to free some storage.  The upgrade process can use 2x the current storage, so beware. That's important in /boot/ and for the normal OS areas.  HOME directories for normal users don't matter.  You may want to clean old packages and old kernels completely from the system at this point.  **sudo apt autoremove --purge** and **sudo apt autoclean** are a start, but more effort may be needed to completely remove old kernels, modules, and headers.
Be certain that any non-OS scripting language version aren't being used by your sudo account.  I've been burned by having a personal perl and python versions installed which didn't match the OS perl and python versions. I'm stupid that way.
Next, make a backup of everything you can't afford to lose.  There seems to be a relationship to people who do this step and NOT having issues with the upgrade. I don't know why. It just works out that way.

Do the upgrade - that's **sudo do-release-upgrade**.
This can take 30 minutes to 5 hours.  Consider that a fresh install only takes 15 minutes when you choose the upgrade method. After the first 30 minutes, questions will start happening, so you'll need to be paying attention to answer. If you don't, the prompt will just sit there, waiting.

Good luck.

Should you attempt to upgrade from 18.04 to 22.04? No.  Just no.

And if the upgrade process fails, you have your backup to start over ... or just to a fresh, clean, install and use the backup to bring back the data and settings as a starting point on the new OS.

---

