---
title: "Flash vids won't play after 11.10 upgrade"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by morrna on 2011-10-28
Just a couple days ago I upgraded from 11.04 to 11.10 using the update software.  Everything went well for the most part.  There's just one little problem: before the upgrade, flash videos (like on Hulu and YouTube) played fine inside Chrome and Firefox, and now they play very jerkily, stopping and going.

Since the upgrade went mostly right I don't want to wipe the HD and do a clean install, I'd rather fix this one small issue.  Has anyone else encountered this problem?  Any ideas on how to fix it or where to look for clues?

---

### Post by morrna on 2011-10-28
I've tried a few things: I've used the software manager to install the versions of Adobe flash they show as available, and I've used the Flash-Aid extension in Firefox to install various versions and none of them seem to help or change the problem at all.  Any other ideas to try?

---

### Post by morrna on 2011-11-11
I could only resolve this issue by completely wiping and reverting to 11.04 .  Once I did that, everything worked fine.

---

### Post by nickpj on 2012-03-06
> **morrna said:**
> I could only resolve this issue by completely wiping and reverting to 11.04 .  Once I did that, everything worked fine.

I had the problems too with flash videos after upgrading from 11.04 to 11.10. After putting up with it for a while, today I found the "flash-aid" extension for Firefox, which fixes up broken flash for Ubuntu and Debian systems.

Installed the extension, restarted the browser, then went Tools -> Flash-Aid -> Wizard Mode, just went with all the defaults, it removed the old flash plugins (I had 2) and downloaded and installed the latest adobe one, and in 2 minutes it was as good as new and working flawlessly. It could not have been easier.

Give it a go, hopefully it helps you too!

---

