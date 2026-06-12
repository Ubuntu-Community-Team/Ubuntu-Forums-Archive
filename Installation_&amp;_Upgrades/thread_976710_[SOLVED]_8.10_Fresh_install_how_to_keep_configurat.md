---
title: "[SOLVED] 8.10 Fresh install how to keep configuration"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by quikone8 on 2008-11-09
Hi,

I have heard that a fresh install corrects some of the sound issue.  If so, how could one do a fresh install on the same partition and keep all the desktop data?  If someone has a link or some detailed info please post, it would be useful for many of us that would like our sound back.

Ron

---

### Post by glennric on 2008-11-09
Do you have your home directories on a separate partition from root?  If so then just reinstall and use the manual disk setup to delete the root partition, create a new partition, and install there.  If you don't have your home partition separate then back up your files in your home directory to another disk or partition, and then do the same as above.  Then after the install copy your old home directory into the new.  I recommend putting your home directories into a separate partition in the future.

---

