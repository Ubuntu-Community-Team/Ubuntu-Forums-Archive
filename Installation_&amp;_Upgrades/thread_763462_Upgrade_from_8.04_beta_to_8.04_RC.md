---
title: "Upgrade from 8.04 beta to 8.04 RC?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Will B-R on 2008-04-23
How do I go about updating to the RC from the beta?

8.04 beta -> 8.04 RC?

---

### Post by forestpixie on 2008-04-23
If you've been updating as they come through then you already have.

---

### Post by Will B-R on 2008-04-23
Ok. It was just that I've been getting lots of updates. Some of which have been very large.

I wasn't sure if my update were subscribed to the beta server or something. And if that would mean I would automatically start getting the 8.10 beta updates.

---

### Post by martalli on 2008-04-23
As long as your repositories are all labelled "hardy", your updates will track along with hardy from alpha -> beta -> rc -> final.  AFAIK, you need to be doing "sudo apt-get update && sudo apt-get dist-upgrade" to be doing the upgrades.  If you are using synaptic or adept to upgrade, this is probably doing the "dist-upgrade" for you.  The "apt-get upgrade" command (or safe upgrade in adept and synaptic) is a less agressive upgrade, but probably not suitable for upgrading while using pre-released versions.

---

### Post by converted on 2008-04-23
Not that I've got any particular reason to avoid the command line, but does this mean that, using synaptic, hitting "reload" then, "Mark All Upgrades" may not be sufficient?

Thanks!

---

