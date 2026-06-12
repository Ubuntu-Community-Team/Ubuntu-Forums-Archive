---
title: "Update from .iso?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by jjloupe on 2010-04-30
I burned and checked the image, but cannot install or upgrade ( I DL both the full and alternate image) Hangs on the Ubuntu screen with the scrolling dots.

After this, I tried mounting and running the install from the iso, but since all the files are either .inf or unknown, I don't know how.

Next, I tried  a trick from the ubuntu site using alt+F2 to run from the iso, and it seemed to work, but now it still tries to DL the updates from the internet instead of just getting them from the ISO. This also happens now if I try to upgrade from the update manager, it keeps asking for the install disk.

Is there any way to just use the ISO as though it were a disk??

I have been running 9.10 for months with no problems.

---

### Post by psusi on 2010-04-30
The alternate can be used as a source of packages to upgrade from, the desktop can not.

---

### Post by jjloupe on 2010-04-30
I logged in as root, went to /var/lib/apt/lists/ and deleted all references of lucid, and now the upgrade is going through. Wish me luck.

---

