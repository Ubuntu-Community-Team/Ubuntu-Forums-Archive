---
title: "Unable to copy the user's Xauthorization file"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by 98cwitr on 2010-03-21
After update to 10.04 I am not longer asked to authenticate when attempting to run "root" priv. apps in System->Administration

Just get the error:

> 
Failed to run /usr/sbin/*whatever-application* as user root.

Unable to copy the user's Xauthorization file.

Google searches have been in vain. Any ideas? All apps still run if ran from terminal w/ sudo command.

---

### Post by 98cwitr on 2010-03-21
damnit, nevermind, upgrade took me out of the sudoers file

*sudo visudo* and added myself to the file, logged out and logged back in...working fine now :-?

---

