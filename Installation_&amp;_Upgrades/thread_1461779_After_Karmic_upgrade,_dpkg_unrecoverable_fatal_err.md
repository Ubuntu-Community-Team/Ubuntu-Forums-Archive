---
title: "After Karmic upgrade, dpkg: unrecoverable fatal error"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by indiepop on 2010-04-24
After upgrading to Karmic, I was having trouble with the fglrx driver.  Following instructions from the forum, I uninstalled the fglrx and reverted to the backup status for dpkg.  Now, dpkg fails completely.  I get the following error every time, no matter what I do:

```
dpkg: unrecoverable fatal error, aborting:
 conflicting diversions involving `/usr/lib/gnupg/gpgkeys_curl.non_curl' or `/gnupg-curl'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Can anyone assist with this?  I have Googled for hours with no success, and attempting to reinstall from the Ubuntu CD doesn't show any valid installs on my partition.  Thank you.

---

### Post by indiepop on 2010-04-24
I fixed the problem.  I reinstalled Ubuntu from the RC and the problem resolved itself, the fglrx drivers work, and nothing was lost.  All I did was manually select the root partition during the upgrade & it figured out what to do, even though it didn't find any profiles to migrate or upgrade.  It replaced the system files which didn't work with fresh copies that did.

---

