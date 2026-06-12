---
title: "Update Manager has turned my LAMP server into a frankenstein OS"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-11-19
I had a stable install of standard Ubuntu 6.10 with Apache, MySQL, and Perl added on top, and running an instance of phpBB3.  I tried to upgrade to 7.04 using the Alternate CD and it made it probably 90% of the way through before bombing-out with a message about Perl versions.  The system now thinks it's 7.04 even though it's still running largely the 6.10 versions of important apps.  So then I tried doing the online update from 7.04 to 7.10 (since that's what Update Manager thought was applicable) and hoping that the install 'logic' of the online Update Manager would be improved relative to the disc.  Similar problem -- it ran almost all the way through, then complained about wrong versions of dozens of apps (e.g. logon) and ultimately said it was cancelling, "Sorry but your system may have been left in an unusable state."  Fortunately, it all actually still seems to work (including phpBB) but my system now says it is 'running' 7.10 and won't allow me to update again.

How do I fix this?

How could I have avoided this?

And, if there's some predictable way to have avoided this, why doesn't Update Manager fix it or warn you ahead of time?

---

