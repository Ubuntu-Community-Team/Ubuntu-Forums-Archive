---
title: "[SOLVED] Dependency problem with unattended network install"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by pjrp on 2008-09-15
Hello

I'm trying to set up a system to do unattended Ubuntu 8.04 network installs.  I had this basically working, but after I recently updated my mirror I've run into problems.  The "Install the base system" step fails saying it cannot install he selected kernel.  On closer inspection the issue is installing linux-generic, which has some dependency issue as follows:

linux-generic: Depends linux-image-generic (=2.6.24.19.21) but 2.6.24.21.23 is to be installed

Any ideas how I can get around this?  Is there a boot parameter I can provide to make it chose a slightly older kernel that (hopefully) may have consistent dependencies?

Regards

Phil

---

### Post by pjrp on 2008-09-19
Ah, my mistake I think.  I'd forgotten I'd switched to the hardy-proposed branch a while ago to deal with another problem.  I just switched back and now everything works OK.  Thanks to anyone who was paying attention.

Phil

---

