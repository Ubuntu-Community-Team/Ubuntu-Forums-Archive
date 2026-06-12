---
title: "How to check what's available before running apt-get update and upgrade?"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by underonesun on 2006-12-23
How to check what's available before running apt-get update and upgrade?
I'm trying to find a quick way to see what packages changed by looking at the date of the packages on a web page or repository. I want to see before I update and upgrade.  Can anyone tell me how to do this?  For edgy, for example.
Thanks.

---

### Post by Jussi Kukkonen on 2006-12-23
[https://lists.ubuntu.com/archives/edgy-changes/](https://lists.ubuntu.com/archives/edgy-changes/) (for other versions, change Edgy to something else)

You can also run *"apt-get upgrade --simulate"*.

---

### Post by studiesrule on 2006-12-23
you could just use synaptic/adept. But if you want to do it terminal wise, use the aptitude ncurses UI: sudo aptitude.
From there you should be able to check all your changes before installing, as well as browse the repos.

---

### Post by underonesun on 2006-12-23
> **Jussi Kukkonen said:**
> [https://lists.ubuntu.com/archives/edgy-changes/](https://lists.ubuntu.com/archives/edgy-changes/) (for other versions, change Edgy to something else)

You can also run *"apt-get upgrade --simulate"*.


The link is what I was looking for, thanks.  The potential problem to solve is the case where "someone" might try to subvert the update/upgrade process by playing with DNS, etc.  If there's a way to confirm, besides using local tools, like apt, etc., then there's an extra validation.  It could still happen, but if there are multiple confirmation sites the chances are reduced.  There may be better ways but this is one way.

---

### Post by underonesun on 2007-01-07
> **Jussi Kukkonen said:**
> [https://lists.ubuntu.com/archives/edgy-changes/](https://lists.ubuntu.com/archives/edgy-changes/) (for other versions, change Edgy to something else)

You can also run *"apt-get upgrade --simulate"*.


Is there another place to look?  That list hasn't been updated since Dec. 21
I had high hopes,  there must be a better way to do what I'm trying to do.
Anyone have any suggestions?

---

