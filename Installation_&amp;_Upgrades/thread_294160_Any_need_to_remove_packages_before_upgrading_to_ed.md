---
title: "Any need to remove packages before upgrading to edgy?"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by allanlewis on 2006-11-06
Hi,

Is there any need to remove any packages/remove any software before upgrading to Edgy? (assuming that I use the official method via update-manager)

Also, will I have to recompile any software (e.g. the latest beta of Gaim) after upgrading?

Thanks in advance.

(Yes, I have searched the forum to see if my question has been answered before posting this thread!)

---

### Post by babooka on 2006-11-06
Generally, no, packaging manager should figure most of the things out.

But it is a good idea to run "deborphan" to check for the unused packages.

---

### Post by allanlewis on 2006-11-06
> **babooka said:**
> Generally, no, packaging manager should figure most of the things out.

But it is a good idea to run "deborphan" to check for the unused packages.

Thanks babooka!

---

### Post by mazirian on 2006-11-06
Actually I was wondering about this myself.  It seems that much of the upgrade blues are the result of tracking third party repositories.  It is beneficial to remove packages installed (say form the plf repositories) before performing the upgrade?  Or will updating those repos to edgy along with all the rest allow things to go forward?

---

