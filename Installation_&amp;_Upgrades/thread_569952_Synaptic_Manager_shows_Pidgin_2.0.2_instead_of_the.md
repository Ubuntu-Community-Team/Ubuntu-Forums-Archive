---
title: "Synaptic Manager shows Pidgin 2.0.2 instead of the latest 2.2.1. Why?"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by LPMusicLJ on 2007-10-07
I'm sort of an advanced newbie.

I see that the latest version of Pidgin is version 2.2.1.  Why do the Ubuntu depositories only display the version 2.0.2?

I'm running version 2.0.2 for the last 2 months.  I've read that I have to uninstall Pidgin to upgrade Pidgin to the latest, but does that also mean that Synaptic Manager will show my current version instead of the latest version?  

Yes, I've run [FONT="Courier New"]sudo apt-get update[/FONT] and [FONT="Courier New"]upgrade[/FONT].

I've asked more advanced users about this problem, and they speculated something about that new version must be tested.  Could I get some "official" explanation on this?

---

### Post by ThrobbingBrain66 on 2007-10-07
One of Ubuntu's policies is "stability over cutting-edge."  Once a version becomes stable (on it's release date) updates only contain bug and security fixes.  If you want newer versions of packages, you can visit [www.getdeb.net](www.getdeb.net)

---

### Post by LPMusicLJ on 2007-10-07
So you're saying that the newer versions are considered stable yet?  Version 2.0.2 was the last stable version?

---

### Post by ThrobbingBrain66 on 2007-10-07
No, I'm saying that after a version of Ubuntu is released, the only updates it receives are for bug fixes and security updates.  Newer versions of packages (pidgin, gimp, openoffice, etc) aren't put into the repos.  But this isn't necessarily because the packages aren't considered stable.  

Whenever a new package version is brought into the repos (always during the developmental stage), extensive testing has been done to assure that no new bugs are introduced.  Frankly, the devs are busy enough with the development version, bug fixes and security updates...they don't have time to bring in new package versions as well.

This is one of the reasons [www.getdeb.net](www.getdeb.net) started.

---

