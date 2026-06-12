---
title: "Could not calculate the upgrade...black listed"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by AlienAbduction on 2008-05-09
Hi very new user of Ubuntu.

Only tried 7.10 for a while. Was waiting for the 8.04 release to fix the Wireless driver for the Intel PRO/Wireless 4965 AG or AGN Network card.

Tried upgrading to 8.04, but get the "Could not calculate the upgrade" error. I don't think that I did any of those things: 1. upgrading to a pre-release version of Ubuntu; 2. Running the current release version of Ubuntu; or 3. unofficial software packages not provided by Ubuntu.

My laptop is a Dell XPS M1330. The last few lines in the Main.log attached:

2008-05-09 23:15:32,604 DEBUG Marking 'ubuntu-desktop' for upgrade
2008-05-09 23:15:32,671 DEBUG The package 'nvidia-glx-new' is marked for removal but it's in the removal blacklist
2008-05-09 23:20:57,478 ERROR Dist-upgrade failed: 'An essential package would have to be removed'

Looks like I'm on the black list...is there a bug/fix report for this?
(apt.log file was too big 134kb to upload as .txt)

---

### Post by dstew on 2008-05-09
Maybe that nvidia driver is operating your 7.10 desktop, so it can't be removed. You might try reconfiguring your display to use another driver, then try the upgrade again.

---

### Post by AlienAbduction on 2008-05-18
Thanks dstew, that did the trick. Though, this experience is not quite the 'just works' paradigm.

And, still no 'just works' WiFi for my wireless card. Oh well, I'll have to sort that out later...

---

