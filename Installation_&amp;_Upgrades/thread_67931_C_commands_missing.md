---
title: "C commands missing"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by sameer_dash on 2005-09-21
i have installed ubuntu on my system but all C commands (including their man pages are missung from the installation).....how do I extract and install them??

---

### Post by banadushi on 2005-09-21
Install:

build-essential
manpages-dev

That should pull in most of the compiler stuff and the developer sections of man.

Have a good one!

Jason

---

### Post by invalid on 2005-09-21
sudo apt-get install <the two packages mentioned above>

---

### Post by sameer_dash on 2005-09-22
i tried:      sudo apt-get install manpages-dev              .....it says

Reading package lists... Done
Building dependency tree... Done
Package manpages-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package manpages-dev has no installation candidate




build-essential  had already solved the problem with gcc, but not with C commands.
it doesn't even recognise 'while' for unix shell  scripting!!

---

