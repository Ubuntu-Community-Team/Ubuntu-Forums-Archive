---
title: "verifying file consistency with packages"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-01-31
I'm looking for a command or option that will verify, for each package that is installed, that the files it would install are present and correct (matching checksum, perhaps).  I recall seeing this capability somewhere, but cannot seem to find it.

I have a machine which ended up with some missing files.  I managed to get it restored runnable by rsyncing some files from another machine in /bin and /lib and /usr.  But these machines did not have exactly the same package versions, and while it runs, it may not be right.  If there is a way to get the package system to verify that each package has all its files and has them correct, that's what want to do right now.

---

