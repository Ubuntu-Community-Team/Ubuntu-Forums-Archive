---
title: "how do i copy packages from one system to other"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by grray on 2006-06-24
I have one ubuntu dapper machine and another ubuntu breezy with dialup connection to internet.
How can i copy packages from dapper to breezy machine and then upgrade it to dapper? Is it possible?

---

### Post by jasutton on 2006-06-26
Doing that kind of an upgrade is not exactly recommended.  It might work,  but it will come with some strange side effects (as there were package naming changes from one version to the next, among other issues).

If you're set on doing it, and you still have your Dapper installation media, you might try inserting your Dapper CD into the Breezy machine and using 'sudo apt-cdrom add' on the command line.  Then you can do an 'sudo apt-get dist-upgrade' to try to do the upgrade from the CD.

Just a thought ;)

---

